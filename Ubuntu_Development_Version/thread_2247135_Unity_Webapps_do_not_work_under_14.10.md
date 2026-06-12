---
title: "Unity Webapps do not work under 14.10"
date: 2014-10-05
forum: Ubuntu Development Version
---

### Post by gutigen on 2014-10-05
I have pretty fresh installation of Ubuntu 14.10 (not upgrade, wiped the drive first) and I can't get Unity WebApps to work. Ubuntu Browser works without issues, loads same pages WebApps are suppose to load, yet WebApps do not work (results in blank page).

Any ideas?

---

### Post by aleolivat on 2014-10-06
I have the same problem.   Should we file a bug?

I was just about to reinstall, because I thought there was something wrong with my installation.   Did you do your installation when the final beta came out or before?

---

### Post by gutigen on 2014-10-06
Yes, I did fresh install from daily image like two weeks ago, so not sure if it was final beta or not.

Filed a bug report for unity-webapps-livemail as an example (though it affects all webapps) with terminal output attached:
[https://bugs.launchpad.net/ubuntu/+source/unity-webapps-livemail/+bug/1377942](https://bugs.launchpad.net/ubuntu/+source/unity-webapps-livemail/+bug/1377942)

---

### Post by aleolivat on 2014-10-07
I marked the bug as affecting me too.   Hopefully it can be fixed soon.   Thanks for filing the bug.

---

### Post by Frogs Hair on 2014-10-15
I found the same with launchpad integration.Using the icon in dash opens webbrowser-app to a blank page and using the following command works but displays errors.  ```
webbrowser-app %u https://launchpad.net/
```

---

### Post by mc4man on 2014-10-15
Might try running from terminal to see if anything relevant about failure to run (whether it's an  unity-webapps-runner/libunity-webapps or webbrowser-app issue
Couple of ways, using mentioned as example, launchpad. (both are really the same
```
unity-webapps-runner -n 'TGF1bmNocGFk' -d 'launchpad.net'
```
or 
```
gtk-launch Launchpadlaunchpadnet
```

---

### Post by Frogs Hair on 2014-10-16
My problem was solved by Unity updates on 10-16. The main error was pointing to Unity-Schemas which was updated.

---

### Post by gutigen on 2014-10-18
Still not fixed here, terminal output results in:

```
The schema com.canonical.Unity.Thumbnailer is missing
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon/webapp-properties.json"
Invalid webapp webapp definition: homepage not found or fails predicate isString
Could not open manifest file:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon/manifest.json"
Invalid webapps manifest found in:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon"
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-livemail/webapp-properties.json"
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-youtube/webapp-properties.json"
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon/webapp-properties.json"
Invalid webapp webapp definition: homepage not found or fails predicate isString
Could not open manifest file:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon/manifest.json"
Invalid webapps manifest found in:  "/usr/share/unity-webapps/userscripts/unity-webapps-amazon"
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-livemail/webapp-properties.json"
Skipping "webapp-properties.json" as a webapp definition search:  "/usr/share/unity-webapps/userscripts/unity-webapps-youtube/webapp-properties.json"
Using Oxide as the web engine backend
Empty path in webapps model search path update request
QQmlExpression: Expression file:///usr/share/webbrowser-app/webcontainer/WebApp.qml:179:25 depends on non-NOTIFYable properties:
    unity::action::qml::ActionManager::globalContext
Empty path in webapps model search path update request
file:///usr/share/webbrowser-app/webcontainer/Chrome.qml:85: TypeError: Cannot read property 'icon' of null
file:///usr/share/webbrowser-app/webcontainer/Chrome.qml:97: TypeError: Cannot read property 'title' of null
[1018/120031:WARNING:proxy_service.cc(909)] PAC support disabled because there is no system implementation
[1018/120031:WARNING:gpu_control_list.cc(760)] Entry with unknown fields 0
[1018/120031:WARNING:gpu_control_list.cc(746)] Malformed exceptions entry 24
qml: Loaded 2 UA override(s) from file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Web/ua-overrides-desktop.js
file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/UnityWebApps/bindings/content-hub/backend/content-hub.js:31: ReferenceError: ContentHubBridge is not defined
file:///usr/share/webbrowser-app/FilePickerDialog.qml:26:9: Type FileDialog unavailable
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:46:1: module "QtQuick.Layouts" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:48:1: module "Qt.labs.folderlistmodel" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:49:1: module "Qt.labs.settings" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:42:1: module "QtQuick.Controls" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:43:1: module "QtQuick.Controls.Private" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:46:1: module "QtQuick.Layouts" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:48:1: module "Qt.labs.folderlistmodel" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:49:1: module "Qt.labs.settings" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:42:1: module "QtQuick.Controls" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:43:1: module "QtQuick.Controls.Private" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:46:1: module "QtQuick.Layouts" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:48:1: module "Qt.labs.folderlistmodel" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:49:1: module "Qt.labs.settings" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:42:1: module "QtQuick.Controls" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:43:1: module "QtQuick.Controls.Private" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:46:1: module "QtQuick.Layouts" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:48:1: module "Qt.labs.folderlistmodel" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:49:1: module "Qt.labs.settings" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:42:1: module "QtQuick.Controls" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:43:1: module "QtQuick.Controls.Private" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:46:1: module "QtQuick.Layouts" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:48:1: module "Qt.labs.folderlistmodel" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:49:1: module "Qt.labs.settings" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:42:1: module "QtQuick.Controls" is not installed
qrc:/QtQuick/Dialogs/DefaultFileDialog.qml:43:1: module "QtQuick.Controls.Private" is not installed

```

---

### Post by aleolivat on 2014-10-24
It has also not been fixed for me, even with a clean install (Oct -20).

---

### Post by ervindine-al on 2014-10-24
Same here.

---

### Post by Elfy on 2014-10-24
If you have issues with 14.04 Trusty please start support threads in one of the support forums, we've moved on to 15.04 in here now.

[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

Closed

---

