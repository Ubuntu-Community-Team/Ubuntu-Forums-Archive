---
title: "Which Unity Bugs bother you most?"
date: 2011-05-08
forum: The Cafe
---

### Post by Bazon on 2011-05-08
(**Disclaimer**: I started [a thread with the same title](http://ubuntuforums.org/showthread.php?t=1724571) before, but it is now closed as the natty development section in the forum is inactive now. So here is a new one.)

[**intro from the previous thread:**]
As the classic gnome-panel desktop will be dropped in 11.10, it becomes increasing important to give the developers feedback where the community suffers most under unity.
I know, the forum here is not the place for feedback, but launchpad is! ("affects me", comments, fixes...) So maybe, this thread can be some kind of runway to link to the different issues that are still left.
(or maybe it dies soon or maybe it gets fused into the unity mega thread.... )

[b]Update:
List of things which are less efficient compared to previous versions or not even possible any more in Unity:[/b]

_* Grouping windows in contexts by using workspaces_
Although workspaces are still there in Unity, they lost their function: Every window on every workspace is represented in the launcher. The launcher even lets you switch the workspace without intending it. You don't even have a glue on which workspace you are on now, as this is not shown any more.
[https://bugs.launchpad.net/unity/+bug/683170](https://bugs.launchpad.net/unity/+bug/683170)
[https://bugs.launchpad.net/unity/+bug/689733](https://bugs.launchpad.net/unity/+bug/689733)

_* Starting a window in e.g. 80% screen size_
Before, a new window launched exactly the size you closed it last time. Now, when it was bigger than 75% Screen Size last time, the window is forced to open maximized. Whether you want it or not.
[https://bugs.launchpad.net/unity/+bug/754214](https://bugs.launchpad.net/unity/+bug/754214)
[https://bugs.launchpad.net/bugs/769085](https://bugs.launchpad.net/bugs/769085)

_* Using menus in different windows_
Requires one click more each time you change the window: FIRST click to focus the window, second to get to the menu. Before, focusing the window and accessing the menu was just one click.
(don't know whether there is a launchpad bug about this)

_* Selecting windows containing text documents_
is now very difficult, because in the shiny exposé-like view you can't read the content and the window title:
[https://bugs.launchpad.net/unity/+bug/734253](https://bugs.launchpad.net/unity/+bug/734253)

_* Pasting in Alt+F2_
worked before with middleclick paste, Ctrl+v or context menu and was very useful following tips from the internet. Doesn't work any more:
[https://bugs.launchpad.net/unity/+bug/736222](https://bugs.launchpad.net/unity/+bug/736222)

_* Quick look in a window and then minimize it again_
Worked before with pressing the window switcher two times (show - minimize) and was very useful and a very common practices. Doesn't work any more with the Unity launcher:
[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)

_* Minimizing a background maximized window_
Is more difficult than before, because that window has no controls: Normally, the window controls are in the top panel for maximized windows. But the top panel is now occupied by the window having focus. (Which is confusing by the way, as it looks like the menu belongs to the background maximized window)
[https://bugs.launchpad.net/unity/+bug/762277](https://bugs.launchpad.net/unity/+bug/762277)


Also, I'm really confused some things don't work with netbooks: I thought Unity was developed for netbooks?
So Evolution mail is the default mail application in Ubuntu. Did anyone try to use the initial configuration Dialogue with a netbook? I recently did on my girlfriends netbook, and the Dialogue window was bigger than screen size, not really resizeable (maximizing made the window jump on click, so click goes into the void.) and so I had to use TAB to access the "next" buttons BLIND. I mean, come on, setting up the email configuration is one of the first things a new user does, and that goes so horribly wrong? On the second release designed for netbooks? I can hardly believe this...
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/488244](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/488244)

*[Will also be posted on Marks page](http://www.markshuttleworth.com/archives/671/comment-page-4#comment-352713).*

---

### Post by leviathan8 on 2011-05-08
There is a bug, when I start ccsm and change any setting, the top panel transforms into a distorted purple picture and nothing else is visible on it. Logging out and back in solves the bug.

---

### Post by Shmantiv_Radio on 2011-05-08
The aero snap>maximize>no window buttons/global menu bug.

Disappearing windows borders. This is a *really, really* old Compiz bug.

Apps showing up in the File & Folders part of Dash search.

Random xserver crashes that send me back to the  login screen. Had this in the Beta, but it started again yesterday after updating.

WIFI can take 5 or 6 attempts to connect.

Even though I've set the dock to only show when I push into the left hand corner, it sometimes shows up if I press to the left.

Can't install DEBs through USC as it just crashes. Even after 3 reinstalls with 3 different ISOs it still does this.

The Plymouth boot screen doesn't work, all I see is solid purple, no logo.

The Dash sometimes closes itself when searching. 

That's all I can think of ATM.

---

### Post by BigSilly on 2011-05-08
It not working at all with my nVidia card! It just won't boot up consistently, and I end up with it either hanging at boot, or the old Gnome desktop, or nothing!

---

### Post by BlacqWolf on 2011-05-08
I have no issues except an occasional issue with the titlebar disappearing when snapping windows. Other than that, the only issues I get are with Unity 2D, and that it just with the launcher appearing behind other windows or being active on the left side of the screen however I cannot see it.

---

### Post by Oxwivi on 2011-05-08
[Drag and drop between maximized windows]("https://bugs.launchpad.net/unity/+bug/738636").

---

### Post by Oxwivi on 2011-05-08
And the [dash being restricted to search with only titles]("https://bugs.launchpad.net/unity/+bug/779429").

---

### Post by Hyporeal on 2011-05-08
What does the evolution bug have to do with Unity? And why does it have so much useless whining in its text? It's inconsistent with the rest of the list, which is concise (if somewhat petty).

I'm most bothered by indicator-weather routinely having a segfault.

---

### Post by Bazon on 2011-05-08
Yes, it is inconsistent, that's why I started that paragraph with "also" outside the list.


An "petty"? 
I didn't search for these things, they just annoy me in my daily experience.
And Ubuntu is my virtual "home", so I want it of course to be comfortable and therefore change for the better... :-)

---

