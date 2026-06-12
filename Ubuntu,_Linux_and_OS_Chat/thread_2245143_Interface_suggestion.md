---
title: "Interface suggestion"
date: 2014-09-21
forum: Ubuntu, Linux and OS Chat
---

### Post by GuiHarrison on 2014-09-21
Please correct me if I'm posting this on the wrong side of the forum, but I need to put this minor frustration somewhere.

I'm a interface designer and I'm trying to build my first theme for ubuntu, but there is a consistency gap (when something looks or behaves differently than a similar thing elsewhere) is really bugging me.

I don't think I'm the only only one to think that context menu from unity launcher is quite sexy! It visually has everything to do with the OS's identity and its beautiful beyond comparison. So why isn't the whole system's interface like that? I mean, when I right click on Nautilus I get the normal looking list that, grant it, has the ability to be stylized by my theme, but never gets close to the beauty of the launcher's.

Let's talk about it!

---

### Post by grahammechanical on 2014-09-21
Every Linux distribution is made up of components from other free and open source software projects whose developers have their own design ideas. Ubuntu just happens to come with a User Interface (Unity) that has been written by the employees of Canonical, the main supporter and developer of Ubuntu .

Yes, because everything is open source, it is possible to modify what is called Upstream Code. And that is sometimes done. In fact I think it has been done a little bit with Nautilus. It is also possible to "fork" the code. And that was done with 14.04 getting a Ubuntu settings application derived from Gnome's control centre.

I guess it is a case of how far do they go? Do they want to make major re-writes of upstream code? Would it not be a distraction from the main purpose of producing the Ubuntu distribution?

I think that it is good that there are "gaps" in Ubuntu that developers, like yourself, can fill. Not everything has to be done by Canonical developers.

Regards.

---

### Post by tgalati4 on 2014-09-21
Linux is based on frameworks.  You could remove all software that does not conform to Unity's style guidelines--and that might make for a small software universe.  Or you can allow older and newer software to run on the same Desktop Environment (DE) with a compatibility mode for the Window Manager (WM) to allow newer and older window styles to function correctly.  The result is a hodge-podge.  

Funny there is no distro named Hodge Podge Linux.

To get a consistent look-and-feel, you would need complete control over the graphics-rendering framework, the desktop environment framework, the Window Management framework, and then each application that you choose to run.  Unity is certainly moving in the direction of a consistent interface across devices, but the older frameworks are still in place.

If you want a more consistent graphical environment, then Apple's OS X might be more suitable.

As you dig into the details, there is a reason for these "gaps".  It's not easy to rip apart a working framework just to make it look "pretty".

---

### Post by mastablasta on 2014-09-22
let's not even start with GTK apps in KDE or qt apps in Gnome...

anyway Ubuntu needs you help. if you know how to fix nautilus to look the same as in Unity menu, then do it! and put the proposal for review on Launchpad. if it works ok, it will be accepted and you will see a piece of your work in next iteration of the OS.

---

