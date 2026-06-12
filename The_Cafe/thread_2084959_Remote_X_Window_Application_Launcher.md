---
title: "Remote X Window Application Launcher"
date: 2012-11-16
forum: The Cafe
---

### Post by fatpenguin on 2012-11-16
Hi All - 

I have a Ubuntu 12.10 server in my basement, and I use a Windows (I know, I know) machine as my primary desktop.  I typically do all of my access through XMing, launching any needed X Windows app through a remote gnome-terminal window.

Instead of launching everything through the command line, I thought it might be kind of cool to run a simple X based application launcher off to the side so I can quickly launch applications I typically use, such as a terminal, or any X based programs I want to launch (a small GUI similar to the Unity app launcher would be nice).  Does anyone have any recommendations that I could try?  

As a note, I couldn't seem to find a way to launch the unity style launcher and have it work through XMing, so I'm looking for something simpler.  Docky seemed to require too much as well, since the dbus-launch seemed to create an entire desktop instead of just the simple launcher.

Thanks for any tips you all may have!
Adam

---

### Post by leekd on 2012-12-10
Hi Adam,

Did you find a solution to this?

My server is running Ubuntu 12.04.  I use Cygwin-X because the free version of Xming did not allow re-sizing of child/sub-windows such as Properties or Configuration windows.

I am able to use docky over Cygwin-X.  

This is how I start docky on the Windows side:

dbus-launch --exit-with-session docky > /dev/null 2>&1

I had to configure docky, that is, add the launchers from the Ubuntu machine.  I use 2 monitors with Windows.  I have the Windows 7 toolbar on one and docky on the other. I uploaded a picture, docky.jpg.

In docky over Cygwin-X, you lose the dock animation and transparency.  Also, the icon images for 'Terminal', 'System Settings' and 'Trash' are not correct.

Please let me know if you found a more elegant solution.

Thanks.

Lee

---

### Post by fatpenguin on 2012-12-12
Hi Lee - 

Unfortunately I did not find a good solution for this.  After seeing your screenshot, I'm inclined to give Docky another shot, although that requires me to run more services than I'm really willing to.  I'm not surprised that you lose transparency, this does not work well under XMing either as the background is assumed to be blank on X, and not the background application running on Windows.

I am tempted to see how much of an effort it would be to put together a simple X based application launcher.  The trouble is always finding the time... :)

Adam

---

