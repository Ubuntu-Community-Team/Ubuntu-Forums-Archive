---
title: "ubuntu-html5-app-launcher click bug"
date: 2015-02-11
forum: Ubuntu Application Development
---

### Post by deekaybee0 on 2015-02-11
Hi.

I have a problem with the ubuntu-html5-app-launcher, clicks dont work.
Did install qtcreator & ubuntu-sdk on my Linux Mint and start a html5 project.
If i click on a link or a button, nothing happens.

Can someone help me pls? Thanks 8-[

EDIT:
I get that application output:

 [COLOR=#0000aa][FONT=Monospace]Debugging starts[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]&"warning: GDB: Failed to set controlling terminal: Inappropriate ioctl for device\n"[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Setting import path to:  /home/dee/untitled/www/../lib/x86_64-linux-gnu [/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]WARNING: This project is using the experimental QML API extensions for QtWebKit and is therefore tied to a specific QtWebKit release.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]WARNING: The experimental API will change from version to version, or even be removed. You have been warned![/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]unity::action::ActionManager::ActionManager(QObject*):[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]	Could not determine application identifier. HUD will not work properly.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]	Provide your application identifier in $APP_ID environment variable.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Cannot create CordovaView object.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Falling back on the plain Webview backend.[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Inspector server started successfully. Try pointing a WebKit browser to [http://192.168.2.101:9221](http://192.168.2.101:9221)[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Injecting webapps script[0] : file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/UnityWebApps/unity-webapps-api.js[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Invalid message received: {"event":"newtab","url":"http://developer.ubuntu.com/apps/html-5/"}[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Invalid message received: {"event":"newtab","url":"http://developer.ubuntu.com/api/html5/current/"}[/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace]Invalid message received: {"event":"newtab","url":"http://developer.ubuntu.com/apps/html-5/"}[/FONT][/COLOR]

---

### Post by pablo180 on 2015-02-15
Same problem here. I have spent the past few days trying to get an HTML5 app to run, but none do, not even the tutorial ones from the developer site. Frankly I have given up, I have tried everything and if even the tutorials ones don't work in the SDK then I am never going to know whether an HTML5 app that I have written will work or not, and if it doesn't whether it is something that I have done (or not done) or a bug in the SDK. Which makes the whole thing kind of pointless.

---

