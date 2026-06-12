---
title: "import Ubuntu.Components 1.1 Problem"
date: 2015-02-19
forum: Ubuntu Application Development
---

### Post by Grim_Gent on 2015-02-19
I'm running Ubuntu 14.10 64bit.
I've install ubuntu-sdk. My problem is this import line is underlined in red in my Qml project
```

import Ubuntu.Components 1.1

```
I'm getting this output from Qt Creators General Messages
```

 [02:15:04] ii click-reviewers-tools 0.21-0~356~ubuntu14.10.1
 

 Warnings while parsing QML type information of /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components:
 Failed to parse '/usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes'.
 Error: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes:632:19: Expected string literal to contain 'Package/Name major.minor' or 'Name major.minor'.
 /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes:633:36: Expected array literal with only number literal members.
 

 Warnings while parsing QML type information of /usr/lib/x86_64-linux-gnu/unity8/qml/Dash:
 Failed to parse '/usr/lib/x86_64-linux-gnu/unity8/qml/Dash/Dash.qmltypes'.
 Error: /usr/lib/x86_64-linux-gnu/unity8/qml/Dash/Dash.qmltypes:83:19: Expected string literal to contain 'Package/Name major.minor' or 'Name major.minor'.
 /usr/lib/x86_64-linux-gnu/unity8/qml/Dash/Dash.qmltypes:84:36: Expected array literal with only number literal members.
 

 Warnings while parsing QML type information of /usr/lib/x86_64-linux-gnu/qt5/qml/QtMultimedia:
 Failed to parse '/usr/lib/x86_64-linux-gnu/qt5/qml/QtMultimedia/plugins.qmltypes'.
 Error: /usr/lib/x86_64-linux-gnu/qt5/qml/QtMultimedia/plugins.qmltypes:0:0: Expected a single import.
 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Settings/Menus
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Settings/Menus
 QQmlComponent: Component is not ready
 

 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/CordovaUbuntu.2.8
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/CordovaUbuntu.2.8
 QQmlComponent: Component is not ready
 

 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Extras/Browser
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Extras/Browser
 QQmlComponent: Component is not ready
 

 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Content
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Content
 QQmlComponent: Component is not ready
 

 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Telephony/PhoneNumber
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Telephony/PhoneNumber
 QQmlComponent: Component is not ready
 

 

 QML module does not contain information about components contained in plugins.
 

 Module path: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Web
 See "Using QML Modules with Plugins" in the documentation.
 

 Automatic type dump of QML module failed.
 Errors:
 "/usr/lib/x86_64-linux-gnu/qt5/bin/qmlplugindump" returned exit code 3.
 Arguments: --path /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Web
 QQmlComponent: Component is not ready
 

 
```

---

### Post by sarujanai on 2015-03-13
I have the same problem. Did you find a solution?

---

### Post by mkamenjak on 2015-04-03
Have you guys installed all the plugins for the sdk?

---

### Post by balcy on 2015-04-12
> **Grim_Gent said:**
> 
```

Warnings while parsing QML type information of /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components:  
Failed to parse '/usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes'. 
Error: /usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes:632:19: Expected string literal to contain 'Package/Name major.minor' or 'Name major.minor'. 
/usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes:633:36: Expected array literal with only number literal members. 

```  

Hi, I've just made a fresh install of Ubuntu 14.10 (32 bit) + the SDK in VirtualBox today, and I am seeing the same problem. 
 After creating a new QML project, the line "Ubuntu.Components 1.1" was underlined red and showing the error message above. 

 I believe the source of this problem lies in the file /usr/lib/i386-linux-gnu/qt5/qml/Ubuntu/Components/plugins.qmltypes  

Here are the lines 629 to 633 of it that I found:
 ```
     
Component {
         prototype: "QObject"
         name: "UbuntuColors" 
         exports: ["UbuntuColors -1.-1"]
         exportMetaObjectRevisions: [-1]
...

```  

I replaced those numbers by non-negative numbers, e.g. 

```
     
Component {
         prototype: "QObject"
         name: "UbuntuColors" 
         exports: ["UbuntuColors 1.0"]
         exportMetaObjectRevisions: [1] 
...

``` 

 NOTE: I'm not sure what the actual version numbers are supposed to be here, 1.1 or whatever. Nevertheless after my change the Ubuntu Components do properly appear in my QML project within the Ubuntu SDK

---

