

# Metabase Google Sheets Integration Script

This Google Apps Script integrates Google Sheets with Metabase to enable seamless data import from Metabase questions into Google Sheets. Users can import individual questions or automate imports for all questions associated with specific sheet names.

---

## Features
1. **Import a Specific Metabase Question:** Replace the content of the current sheet with data from a specified Metabase question.
2. **Import All Questions:** Automate data import for all sheets following a naming convention `(metabase/QUESTION_NUMBER)`.
3. **Refresh Active Sheet:** Automatically refresh the data for the active sheet based on its associated Metabase question number.
4. **Automatic Token Management:** Handles session token retrieval and renewal for Metabase API authentication.

---

## Script Installation and Setup

1. **Add Script to Google Sheets:**
   - Open a Google Sheet.
   - Navigate to `Extensions > Apps Script`.
   - Copy and paste this script into the script editor.

2. **Set Script Properties:**
   Configure the following properties in the **Apps Script Project Settings**:
   - `BASE_URL`: The base URL of your Metabase instance (e.g., `https://your-metabase-url.com/`).
   - `USERNAME`: Your Metabase username.
   - `PASSWORD`: Your Metabase password.
   - `TOKEN`: (Optional) A valid Metabase session token, if already available.

3. **Run `onInstall` Function:**
   - Execute the `onInstall` function in the Apps Script editor to add the **Metabase** menu to your Google Sheets interface.

---

## How to Use

### 1. Metabase Menu
Once installed, a new **Metabase** menu will appear in the Google Sheet with the following options:

#### **Import Question**
- Prompts for a Metabase question number.
- Replaces the content of the current sheet with the result from Metabase.

#### **Import All Questions in Sheets**
- Scans all sheets named in the format `(metabase/QUESTION_NUMBER)`.
- Automatically imports data for all identified question numbers.

### 2. Refresh Active Sheet
- Refreshes data for the active sheet based on its question number derived from the sheet name.

### 3. Automatic Refresh
To automate data imports at scheduled intervals:
- Create a trigger in `Extensions > Apps Script > Triggers`.
- Set up the `runautomatically` function to execute at your desired frequency.

---

## Sheet Naming Convention

- To import data for multiple Metabase questions automatically, name sheets in the format `(metabase/QUESTION_NUMBER)` where `QUESTION_NUMBER` is the Metabase question ID.

Example:
- `Sheet1` → `(metabase/152)`: Links the sheet to Metabase question 152.

---

## Functions Overview

### Core Functions
- **`importQuestion`:** Imports data for a specific Metabase question.
- **`importAllQuestions`:** Automates data import for all linked sheets.
- **`refreshactivesheet`:** Refreshes data for the active sheet.
- **`getToken`:** Manages Metabase API session tokens.
- **`getQuestionAsCSV`:** Fetches Metabase question data in CSV format.
- **`fillSheet`:** Fills the specified sheet with imported data.

### Utility Functions
- **`onOpen`:** Adds the Metabase menu to the UI.
- **`onInstall`:** Runs `onOpen` during script installation.
- **`getSheetNumbers`:** Extracts linked Metabase question numbers from sheet names.

---

## Error Handling
- Displays alerts and logs errors for failed imports or authentication issues.
- Automatically attempts token renewal if the session token is invalid.

---

## Notes
- Ensure the Metabase API is enabled for your account.
- Use strong credentials for Metabase to ensure data security.

--- 

Feel free to customize the file based on additional details or specific user instructions!
