---
title: "Cant run binary app"
date: 2015-08-02
forum: Ubuntu Phone and Tablet
---

### Post by neochapay on 2015-08-02
I create simple binary application, but wher i run it on sdk i get this error:
```

[COLOR=#31363b][FONT=Monospace]Sdk-Launcher> Application installed successfully[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> AppId:                   chebfmchat.neochapay_chat_0.4.7[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Architecture:            armhf[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Application confined:    True[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Communication directory: /home/phablet/.local/share/chebfmchat.neochapay/[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Application started: 5071[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Debug-helper> Setting up environment[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Debug-helper> TmpDir:      /home/phablet/.local/share/chebfmchat.neochapay/[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Debug-helper> AppId:       chebfmchat.neochapay_chat_0.4.7[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Debug-helper> Environment: confined[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Debug-helper> Executable was not found in the PATH[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Received a failed event[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> The Application exited, cleaning up[/FONT][/COLOR]
[COLOR=#31363b][FONT=Monospace]
Sdk-Launcher> Finished[/FONT][/COLOR]


```

My desctop file is:
```

[COLOR=#808000][Desktop[/COLOR][COLOR=#808000]Entry]
[/COLOR][COLOR=#800080]
Version[/COLOR]=1.0

[COLOR=#800080]Name[/COLOR]=ChebFMChat

[COLOR=#800080]Exec[/COLOR]=chat

[COLOR=#800080]Icon[/COLOR]=chat/chat.png

[COLOR=#800080]Terminal[/COLOR]=false

[COLOR=#800080]Type[/COLOR]=Application

[COLOR=#800080]X-Ubuntu-Touch[/COLOR]=true

[COLOR=#800080]X-Ubuntu-Splash-Color[/COLOR]=#F5F5F5

[COLOR=#800080]X-Ubuntu-Supported-Orientations[/COLOR]=portrait

```[FONT=Verdana]

My app .pro file is:
[/FONT]```

[COLOR=#800080]TARGET[/COLOR][COLOR=#c0c0c0] [/COLOR]=[COLOR=#c0c0c0] [/COLOR]chat[FONT=Verdana]
folder_01.source[/FONT][COLOR=#C0C0C0][FONT=Verdana] [/FONT][/COLOR][FONT=Verdana]=[/FONT][COLOR=#C0C0C0][FONT=Verdana] [/FONT][/COLOR][FONT=Verdana]qml/chat[/FONT]
folder_01.target[COLOR=#c0c0c0] [/COLOR]=[COLOR=#c0c0c0] [/COLOR]qml
DEPLOYMENTFOLDERS[COLOR=#c0c0c0] [/COLOR]=[COLOR=#c0c0c0] [/COLOR]folder_01
[COLOR=#008000]#[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]Additional[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]import[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]path[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]used[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]to[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]resolve[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]QML[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]modules[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]in[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]Creator's[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]code[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]model[/COLOR]QML_IMPORT_PATH[COLOR=#c0c0c0] [/COLOR]=
[COLOR=#800080]QT[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]multimedia
android[COLOR=#c0c0c0] [/COLOR]{[COLOR=#c0c0c0]
    [/COLOR][COLOR=#800080]QT[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]androidextras
}
else
{[COLOR=#c0c0c0]
    [/COLOR][COLOR=#800080]QT[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]widgets}
[COLOR=#008000]#[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]The[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000].cpp[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]file[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]which[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]was[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]generated[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]for[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]your[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]project.[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]Feel[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]free[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]to[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]hack[/COLOR][COLOR=#c0c0c0] [/COLOR][COLOR=#008000]it.[/COLOR][COLOR=#800080]
SOURCES[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]main.cpp[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/connecter.cpp[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/suiteadapter.cpp[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/notificationclient.cpp

[COLOR=#808000][FONT=Verdana]include[/FONT][/COLOR][FONT=Verdana](qtquick2applicationviewer/qtquick2applicationviewer.pri)[/FONT]
qtcAddDeployment()
[COLOR=#800080]HEADERS[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]    [/COLOR]src/connecter.h[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/suiteadapter.h[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/config.h[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]src/notificationclient.h
ANDROID_PACKAGE_SOURCE_DIR[COLOR=#c0c0c0] [/COLOR]=[COLOR=#c0c0c0] [/COLOR]$$[COLOR=#800080]PWD[/COLOR]/android
[COLOR=#800080]OTHER_FILES[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]    [/COLOR]android/AndroidManifest.xml[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]qml/chat/pages/SplashScreenPage.qml[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]qml/chat/js/Global.js[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]qml/chat/pages/MessageFeedPage.qml[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]qml/chat/pages/LoginPage.qml
[COLOR=#800080]DISTFILES[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]    [/COLOR]chat200.png[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]chat80.png[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]chat64.png[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]chat.svg
[COLOR=#800080]RESOURCES[/COLOR][COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
    [/COLOR]resources.qrc
CONF_FILES[COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0]  [/COLOR]chat.apparmor[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
               [/COLOR]chat.desktop[COLOR=#c0c0c0] [/COLOR]\[COLOR=#c0c0c0]
               [/COLOR]chat.png
config_files.path[COLOR=#c0c0c0] [/COLOR]=[COLOR=#c0c0c0] [/COLOR]/chat
config_files.files[COLOR=#c0c0c0] [/COLOR]+=[COLOR=#c0c0c0] [/COLOR]$${CONF_FILES}
[COLOR=#800080]INSTALLS[/COLOR]+=config_files[FONT=Verdana]
```[/FONT]
My package .pro is:
```

[COLOR=#800080][FONT=Verdana]TEMPLATE[/FONT][/COLOR][FONT=Verdana]=[/FONT][FONT=Verdana]subdirs[/FONT][FONT=Verdana]
load(ubuntu-click)[/FONT]
[COLOR=#800080]SUBDIRS[/COLOR]+=chat
[FONT=Verdana]UBUNTU_MANIFEST_FILE=manifest.json.in[/FONT][FONT=Verdana]
UBUNTU_TRANSLATION_DOMAIN="chebfmchat.neochapay"[/FONT][FONT=Verdana]
UBUNTU_TRANSLATION_SOURCES+=[/FONT][FONT=Verdana]\[/FONT]$$files(app/*.qml,true)\$$files(app/*.js,true)[FONT=Verdana]
UBUNTU_PO_FILES+=$$files(po/*.po)[/FONT]
aptest.target=autopilot
aptest.commands=bash$$[COLOR=#800080]PWD[/COLOR]/app/tests/autopilot/run
aptest.depends=sub-app
unittest.target=check
unittest.commands=/usr/bin/qmltestrunner-input$$[COLOR=#800080]PWD[/COLOR]/app/tests/unit
unittest.depends=sub-app
[COLOR=#800080]QMAKE_EXTRA_TARGETS[/COLOR]+=aptestunittest
```
where I'm wrong?

---

