---
title: "Has anyone been able to write HTML5/Phonegap apps with Ubuntu SDK?"
date: 2014-01-02
forum: Ubuntu Application Development
---

### Post by lesilvestre on 2014-01-02
I use Ubuntu 13.10. I tried this in two different computers already with identical results.

I installed Ubuntu SDK following the instructions on the official website
[http://developer.ubuntu.com/apps/create/get-the-sdk/](http://developer.ubuntu.com/apps/create/get-the-sdk/)

I tried to follow this tutorial to write Cordova apps
[http://developer.ubuntu.com/apps/cordova/creating-cordova-ubuntu-qr-code-scanner-html5-app/](http://developer.ubuntu.com/apps/cordova/creating-cordova-ubuntu-qr-code-scanner-html5-app/)
but I immediately run into trouble since "[COLOR=#333333][FONT=Ubuntu]Cordova Ubuntu HTML5 Touch UI" is not a type of project offered in Qt Creator/Ubuntu SDK.

Then I go for one of the projects available there. I thought I would try "HTML5 Tabbed Touch UI".
Some sample html5 project gets created in Qt Creator. When I try to run it I get the following error message.
[/FONT][/COLOR][COLOR=#9d9d9d][FONT=Monospace]Starting ubuntu-html5-app-launcher --www=/home/luis/projects/ubuntu-tabbed-test[/FONT][/COLOR]
[COLOR=#9d9d9d][FONT=Monospace]Failed to start program. Path or permissions wrong?[/FONT][/COLOR]
[COLOR=#9d9d9d][FONT=Monospace]ubuntu-html5-app-launcher exited with code -1

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]I can solve this one installing the package [/FONT][/COLOR]ubuntu-html5-container, but I thought it would be worth reporting it, since it might be useful to some people.

After installing that package, I try to run my sample html5 project again and I get the following error message.

[COLOR=#1414be][FONT=Monospace]Starting ubuntu-html5-app-launcher --www=/home/luis/projects/ubuntu-tabbed-test[/FONT][/COLOR]
[COLOR=#be1414][FONT=Monospace]/usr/bin/ubuntu-html5-app-launcher: error while loading shared libraries: libQt5Core.so.5: cannot open shared object file: No such file or directory[/FONT][/COLOR]
[COLOR=#be1414][FONT=Monospace]ubuntu-html5-app-launcher exited with code 127


[/FONT][/COLOR]I don't know how to solve this one. Like I said before, the same procedure gave me identical results in two different computers. I am following the official instructions from the Ubuntu website, so I was expecting this would work without severe glitches. The QML projects on Ubuntu SDK seem to work fine.

The package libqt5core5 is installed with version 5.0.2+dfsg1-7ubuntu11.1 and it certainly contains the file [COLOR=#BE1414][FONT=monospace]libQt5Core.so.5.[/FONT][/COLOR]

My questions are:
1. How do I make Cordova apps with Ubuntu SDK? Is there a tutorial that fits the current reality?
2. How do I fix the error above?

---

### Post by athletesrun on 2014-01-05
I have the same problem and I have not been able to find a solution.  :(

---

### Post by stefan_03 on 2014-02-24
Same here. I've tried a few things, but none of them work. And I think that it's not an optimal solution to add JavaScripts into the head, which do not exist at all
[COLOR=#808000]<script[/COLOR][COLOR=#c0c0c0] [/COLOR]src=[COLOR=#aa0000]"/usr/share/ubuntu-html5-ui-toolkit/0.1/ambiance/js/fast-buttons.js"[/COLOR][COLOR=#808000]></script>

[/COLOR][FONT=Verdana]I have to install them on my own, and I just figured it out accidentally. How can I build WebApps/Html5Apps for Ubuntu? :/[/FONT]

---

### Post by adrian89 on 2014-03-07
> **stefan_03 said:**
> Same here. I've tried a few things, but none of them work. And I think that it's not an optimal solution to add JavaScripts into the head, which do not exist at all
[COLOR=#808000]<script[/COLOR]src=[COLOR=#aa0000]"/usr/share/ubuntu-html5-ui-toolkit/0.1/ambiance/js/fast-buttons.js"[/COLOR][COLOR=#808000]></script>

[/COLOR][FONT=Verdana]I have to install them on my own, and I just figured it out accidentally. How can I build WebApps/Html5Apps for Ubuntu? :/[/FONT]

Open Ubuntu SDK, New Project->Ubuntu(project)->HTML5 TOUCH UI

---

