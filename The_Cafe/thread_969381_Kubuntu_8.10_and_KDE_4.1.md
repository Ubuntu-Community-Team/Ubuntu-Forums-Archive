---
title: "Kubuntu 8.10 and KDE 4.1"
date: 2008-11-03
forum: The Cafe
---

### Post by Rhapsody on 2008-11-03
I'm looking at upgrading from Kubuntu 8.04 (using KDE 3.5.10) to Kubuntu 8.10, but I'm unsure whether KDE 4.1 can do what I want yet. The [KDE Techbase](http://techbase.kde.org/Schedules/Is_KDE_4.1_for_you%3F) article helped somewhat, but also noted that some distros may have workarounds, so I want to ask specifically about what Kubuntu 8.10 can do.

First off, is the GPU performance problem really as bad as it's made out to be? I've got a GeForce 8800GT here (using the nvidia driver) and it works pretty well with KDE 3. What's the likelihood of me getting significant performance problems under KDE 4, and how easy are these problems to solve?

The panels are another issue. I have a rather complicated setup under KDE 3 with two normal-sized panels at the top and bottom, both 80% width, autohiding after 1 second. The top panel has my K Menu, System Menu, and Quick Launcher. The bottom panel has my Taskbar, Desktop Preview & Pager, System Tray, Wastebin, and Clock. Both panels are normally locked. How much of this arrangement can be carried over to KDE 4.1 without being changed?

I usually use the different backgrounds on my desktops to identify them (I have six virtual desktops). Is it really impossible to have different backgrounds on virtual desktops under KDE 4.1? Icons are no problem fortunately as I've never used them.

Some KDE applications (the most notable for me being Amarok and K3b) haven't been updated for KDE 4 yet. How will they work under Kubuntu 8.10? I gather that the KDE 3 versions will still be usable for now, but are there any things I should know about using them on a KDE 4 desktop? Also, while K3b 1.1 is in pre-alpha, Amarok 2 is in beta now. How would I go about installing the Amarok beta in Kubuntu 8.10 if I wanted to try it?

---

### Post by mips on 2008-11-03
> **Rhapsody said:**
> 
First off, is the GPU performance problem really as bad as it's made out to be? I've got a GeForce 8800GT here (using the nvidia driver) and it works pretty well with KDE 3. What's the likelihood of me getting significant performance problems under KDE 4, and how easy are these problems to solve?

The panels are another issue. I have a rather complicated setup under KDE 3 with two normal-sized panels at the top and bottom, both 80% width, autohiding after 1 second. The top panel has my K Menu, System Menu, and Quick Launcher. The bottom panel has my Taskbar, Desktop Preview & Pager, System Tray, Wastebin, and Clock. Both panels are normally locked. How much of this arrangement can be carried over to KDE 4.1 without being changed?

I usually use the different backgrounds on my desktops to identify them (I have six virtual desktops). Is it really impossible to have different backgrounds on virtual desktops under KDE 4.1? Icons are no problem fortunately as I've never used them.

Some KDE applications (the most notable for me being Amarok and K3b) haven't been updated for KDE 4 yet. How will they work under Kubuntu 8.10? I gather that the KDE 3 versions will still be usable for now, but are there any things I should know about using them on a KDE 4 desktop? Also, while K3b 1.1 is in pre-alpha, Amarok 2 is in beta now. How would I go about installing the Amarok beta in Kubuntu 8.10 if I wanted to try it?

First I use Arch and KDEmod but thought I would comment anyway.

I have a 9600GT and I have not noticed lag. There are some fixes out there for those that experience it. The latest nvidia beta drivers are also an option to try.

As for your panels the only thing I'm not sure of is the System Menu and the 1 second Auto Hide. Auto hide is there but there is no timer option I know of. The rest seem doable.

If Amarok & K3b are not up to scratch you could try the older kde3 versions or try compiling newer versions from source.

Hopefully a current Kubuntu user can answer your questions more to the point.

---

### Post by stimpack on 2008-11-03
I have an 8800GT and Kubuntu8.10. It is slower than than 8.04, noticeably, but it is not so bad that I have gone and done anything about it.

Amarok and K3b work fine, as do all kde3 apps I have tried.

Panels are fine top and bottom, but I dont see how to auto-hide in the quick glance i gave while writing this.

I dont see anyway to have different backgrounds on each desktop.

8.10 is very interesting, and I am sticking with it, but KDE4 is still *far* from finished.

---

### Post by kef_kf on 2008-11-03
you should use the nvidia 177.80 beta driver with the optimizations listed [_here_]("http://www.nvnews.net/vbulletin/showthread.php?t=118088"). you can use the neon project to install amarok 2 beta but it is far from feature complete.

---

### Post by mips on 2008-11-03
> **stimpack said:**
> 
Panels are fine top and bottom, but I dont see how to auto-hide in the quick glance i gave while writing this.


Try Panel Settings->More Settings->Auto hide if available in Kubuntu.

---

