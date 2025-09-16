FocusTime - Android (Jetpack Compose)
====================================

What's included:
- Minimal Android Studio project structure for the FocusTime app (Jetpack Compose).
- UI components: MainScreen, TimerCard, StatsSection (pie chart + legend + reset today).
- TimerViewModel with per-day logs and start/stop/resetToday logic.

How to build a DEBUG APK (quick):
1. Open the project folder in Android Studio.
2. Let Android Studio sync and download Gradle and dependencies.
3. Run: Build > Build Bundle(s) / APK(s) > Build APK(s).
4. The APK will be at: app/build/outputs/apk/debug/app-debug.apk

How to build a SIGNED RELEASE APK (Play Store):
1. Create a keystore (if you don't have one):
   keytool -genkeypair -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias

2. Add your keystore to app/build.gradle signingConfigs (example):
   signingConfigs {
       release {
           storeFile file("/absolute/path/to/my-release-key.jks")
           storePassword "your-store-password"
           keyAlias "my-key-alias"
           keyPassword "your-key-password"
       }
   }
   buildTypes {
       release {
           signingConfig signingConfigs.release
           minifyEnabled false
       }
   }

3. Build > Build Bundle(s) / APK(s) > Build > Generate Signed Bundle / APK...
   Follow the dialog, choose your keystore, and select "release" build type.

Notes:
- For Play Store distribution prefer an Android App Bundle (.aab).
- This project is minimal and intended as a starting point. Consider adding persistence (Room/DataStore) for real usage.
