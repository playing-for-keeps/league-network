# The League Network — Version 2

A free static website starter for your Sleeper fantasy football league, with a Google Sheets editorial workflow.

## What this version does
- Loads public league details, roster names, current-week matchups, and roster points from the Sleeper API.
- Loads **approved/published** stories from a Google Sheets CSV feed.
- Keeps the workflow editorial: put drafts in the private `Drafts` tab; only move approved items into `Published`.
- Supports `story`, `recap`, `award`, and `lines` content types.
- Keeps the website free to host on GitHub Pages.

## Important limitations
- This version does not automatically write AI-generated recaps. It provides the content pipeline and starter website. True AI draft generation needs an AI service or a manual workflow; calling a paid AI API directly from a public web page would expose your API key and should not be done.
- The current Power Rankings page is a simple points-scored baseline, not a sophisticated model.
- Sleeper API data has not been verified from this environment. Test it after publishing.
- A Google Sheet's Published tab must be published to the web as CSV for the public website to read it. Do not put private notes, personal information, or unapproved content in that published tab. Keep drafts and notes in a separate, unpublished tab.

## 1. Make your Google Sheet
1. Upload `league_network_content_template.xlsx` to Google Drive.
2. Open it with Google Sheets (File → Save as Google Sheets if prompted).
3. Use the `Drafts` tab for unpublished content and notes.
4. When you approve an item, copy its row into `Published`. Set `status` to `published`.
5. In Google Sheets, select **File → Share → Publish to web** (the exact menu wording may vary).
6. Choose only the `Published` sheet/tab and choose **Comma-separated values (.csv)**, then publish.
7. Copy the published CSV URL.

**Privacy note:** the Published tab becomes publicly readable. Do not publish the Drafts tab.

## 2. Connect the site to your sheet
Open `index.html` in a text editor (Notepad is fine). Find this line near the top of the script:

`publishedCsvUrl: ""`

Paste your published CSV URL between the quotes. Save the file.

## 3. Create your free GitHub account
1. Go to https://github.com/signup
2. Enter your email, create a password, and choose a username.
3. Complete GitHub's verification steps and confirm your email.
4. Save your password in a password manager. Do not share it with me or put it in the website files.

## 4. Publish the website
1. Sign in at https://github.com.
2. Click the **+** menu near the top-right and choose **New repository**.
3. Name it `league-network`, set it to **Public**, and select **Add a README file** if shown.
4. Click **Create repository**.
5. On the repository page, click **Add file → Upload files**.
6. Upload `index.html` from this folder. You may also upload this README if you like.
7. Click **Commit changes**.
8. Open **Settings → Pages**.
9. Under **Build and deployment**, choose **Deploy from a branch**.
10. Select branch `main` and folder `/(root)`, then click **Save**.
11. Wait a few minutes and refresh the Pages settings. Click **Visit site** when the URL appears. It will look like `https://YOUR-USERNAME.github.io/league-network/`.

GitHub Pages on GitHub Free requires a public repository, and the published website is public. GitHub says publishing can take up to about 10 minutes.

## Weekly workflow
1. Copy/edit weekly ideas in the private `Drafts` tab.
2. Review all facts, jokes, awards, rankings, and odds.
3. Copy only approved rows to the `Published` tab.
4. The website will display the approved rows after its CSV feed refreshes.

## CSV column format
The website expects these columns in the Published tab:
- `type`: `story`, `recap`, `award`, or `lines`
- `title`: headline
- `subtitle`: optional deck/subheadline
- `body`: article, award explanation, or odds text
- `category`: optional label
- `week`: optional week number
- `status`: use `published` for items that should appear
- `date`: optional date

The supplied workbook has example rows to show the format. Replace them before publishing your content.
