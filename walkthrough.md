# PakePlus-Android Setup Walkthrough

> [!NOTE]
> I have migrated this folder to the **PakePlus-Android** codebase. All required Android files (`package.json`, `app`, `build.gradle`, `scripts/ppconfig.json`, etc.) are intact and correctly set up. 

## 1. Project Configuration

The main configuration for your Android app is located in `scripts/ppconfig.json`. 
- Open `scripts/ppconfig.json` to customize your app's display name, bundle ID, target website URL, and screen orientation inside the `"android"` section.

## 2. GitHub Token Configuration

You already have the `.env` file with your GitHub token (`ghp_...`). 
This token is used by scripts and the GitHub API to automate your workflow.

## 3. Local Development & Building

> [!TIP]
> Before building locally, make sure you have **Node.js** (v16+), **Java JDK 17**, and the **Android SDK** installed.

1. **Install Dependencies**:
   ```bash
   npm install
   ```

2. **Apply Configurations**:
   ```bash
   npm run pp:worker
   ```
   This script reads your `ppconfig.json` and automatically updates the Android Manifest, Gradle files, and Icon files. *(Note: On Windows, the icon generation might fail if ImageMagick is not installed. Use the GitHub Actions cloud build instead!)*

3. **Build the APK**:
   ```bash
   ./gradlew assembleDebug --no-daemon
   ```

## 4. Cloud Building (Recommended)

Since you've pushed this code to GitHub, the included **GitHub Actions workflow** (`.github/workflows/build.yml`) will automatically run `npm run pp:worker` and build the Android `.apk` file for you in the cloud! 

You can download your ready `.apk` from your repository's Releases page.
