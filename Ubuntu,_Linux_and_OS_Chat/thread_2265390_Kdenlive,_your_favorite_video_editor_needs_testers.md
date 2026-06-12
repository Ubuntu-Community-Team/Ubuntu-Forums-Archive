---
title: "Kdenlive, your favorite video editor needs testers!"
date: 2015-02-14
forum: Ubuntu, Linux and OS Chat
---

### Post by amgeddis on 2015-02-14
So just getting the word out but Kdenlive has been under very active development recently and they need testers to help shake out the bugs for their Qt5/KDE Frameworks 5 port of Kdenlive.  Kdenlive is officially becoming a KDE app and they want to quickly iron out the bugs and get it stable so that it can be released as part of the KDE Applications 15.04 release!  

In their git is a "15.04" branch you need to download and compile for testing here: [https://projects.kde.org/projects/extragear/multimedia/kdenlive/repository/show?rev=15.04](https://projects.kde.org/projects/extragear/multimedia/kdenlive/repository/show?rev=15.04)

And here are the build instructions:  [https://community.kde.org/Kdenlive/Development/KF5](https://community.kde.org/Kdenlive/Development/KF5)
*"Please notice you need a KF5 install to do this.  One possible solution is to use a virtual machine with Kubuntu 15.04 preview for testing."*

They do not use Mantis for the KF5 version so report bugs with the KDE bug tracker here:  [https://bugs.kde.org/describecomponents.cgi?product=kdenlive](https://bugs.kde.org/describecomponents.cgi?product=kdenlive)

After the porting is complete and stable the Kdenlive developers plan to finish the refactoring work they started years ago:

> [COLOR=#000000][FONT=arial]Refactoring branch (called frameworks)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]The refactoring has been split into 3 major steps:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]A - clip handling and project bin[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]B - porting monitors to copy Shotcut - brings back opengl & movit[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]C - timeline refactoring[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]The idea is that once a step has been finished, Kdenlive is usable.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Step A is almost finished, mostly needs some cleanup (about 2 more weeks)[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]Step B should be the easier, not started yet[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]Step C wil be a long story, we might want to make several short steps. VPinon started some preliminary work[/FONT][/COLOR]

---

