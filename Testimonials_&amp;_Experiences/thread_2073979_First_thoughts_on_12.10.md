---
title: "First thoughts on 12.10"
date: 2012-10-20
forum: Testimonials &amp; Experiences
---

### Post by thany on 2012-10-20
Installation was a long process, even on an SSD. That aside, no errors. I did an in-place upgrade via the update manager - no installation disks involved.

My thoughts so far:
1) The windows-key still doesn't work.
2) Still unable to create desktop shortcuts.
3) Still unable to move the taskbar anywhere.
4) Still not able to reorder icons on the taskbar by dragging them vertically. Have to drag horizontically first. Vertical dragging drags the entire set of icons which doesn't do squat.
5) Maximized windows still have the icons on the top-left, while non-maximized windows have them on the top-right. Confusing.
6) The software center is still a joke. It's just horrible to work with when uninstalling a bunch of things.
7) Why is there Amazon on my pc?! I don't mind, but ASK first. Uninstall.
8.) Ubuntu seems unable to remember my screen resolution. At semi-random points WHILE running, it reverts to whatever it thinks is my monitor's native resolution, which it isn't.
9) For non-maximized windows, their menu is at the very top of the screen in the bar that has notification icons. It's confusing because that isn't where the application is. It's the same as OSX, but that's not neccesarily good.
10) VirtualBox 4.2.0 videodriver no longer works. Could have tested that, yea?

10 fails for a .10 release. Nice!

The interface loogs good though, although but not much has really changed as far as a normal user is concerned. Sorry, no compliments, only problems.

---

### Post by uRock on 2012-10-20
1) Works fine on my system.
2) The purpose of Unity is to do away with desktop shortcuts, though I have been able to create them with no problems.
6) I have never had any problems with uninstalling packages via the USC, but I usually use Synaptic anyways.
7) If you had read the release notes, then you would have known about this.
10) Did you file a bug report?

It sounds as if you need to start some threads asking for help. Since this thread isn't asking for help it is being moved to the Testimonial & Experiences sub-forum.

---

### Post by 3rdalbum on 2012-10-21
> **thany said:**
> 
1) The windows-key still doesn't work.

Submit a bug report. Or check that your keyboard works.

> 2) Still unable to create desktop shortcuts.
3) Still unable to move the taskbar anywhere.
4) Still not able to reorder icons on the taskbar by dragging them vertically. Have to drag horizontically first. Vertical dragging drags the entire set of icons which doesn't do squat.

By design. If these were things that were going to be changed in 12.10 I'd agree with you, but they were never going to be changed, so you can't really complain "It still doesn't work how I think it should work".

> 5) Maximized windows still have the icons on the top-left, while non-maximized windows have them on the top-right. Confusing.

This is not the default behaviour. If it confuses you, then change the window buttons back to the left.

> 7) Why is there Amazon on my pc?! I don't mind, but ASK first. Uninstall.

It's a change to the default software set. They don't have to ask your permission at upgrade-time to update your software - you've already given permission by running the upgrade. As noted for the last few months, it's almost trivial to remove the Amazon shopping lens or disable all network-touching lenses. Also as noted, you've had shopping links on many previous versions of Ubuntu...

> 8.) Ubuntu seems unable to remember my screen resolution. At semi-random points WHILE running, it reverts to whatever it thinks is my monitor's native resolution, which it isn't.

File a bug report.

> 9) For non-maximized windows, their menu is at the very top of the screen in the bar that has notification icons. It's confusing because that isn't where the application is. It's the same as OSX, but that's not neccesarily good.

It's been this way for the last 18 months, where have you been? Also, it's still trivially-easy to remove the global menu and get back to menu-in-window.

> 10) VirtualBox 4.2.0 videodriver no longer works. Could have tested that, yea?

Did you test it before release? And did you submit a bug report?

---

### Post by Pilot6 on 2012-10-21
Oracle already released a new version, that supports Quantal.
But still, e.g a flash boot drive is impossible to create.

---

### Post by maverick555 on 2012-10-22
1.Ubuntu is becoming more like windows 8 now.It says itself a desktop operating system and didn't even know that, in a desktop there is a keyboard which has num lock function which should be enabled by default.

2.Windows is more customizable : i can change icons,move taskbar anywhere,change login screen and even boot screen.
In ubuntu change in icons and theme nothing else.

This is just for ubuntu i know kde is more customizable.

3.    The worst case is my printer worked in ubuntu 10.10 and not in any releases after 11.10.
Now i have a new computer and i can't install ubuntu 10.10 because hd2000 graphics does not support it.
Conclusion windows supports more hardware.Cause everything you purchase they will give you the driver cd.

4.If you don't have a internet ubuntu is useless.While in windows you can back up the software and install them any time you want.

Please ubuntu (canonical) sort this things out somehow.:popcorn:

---

### Post by JRV on 2012-10-22
9) This "feature" is called global menus.
To put the menus back in the window run the following command:
```

sudo apt-get remove indicator-appmenu

```

---

### Post by uRock on 2012-10-22
> **maverick555 said:**
> 1.Ubuntu is becoming more like windows 8 now.It says itself a desktop operating system and didn't even know that, in a desktop there is a keyboard which has num lock function which should be enabled by default.

2.Windows is more customizable : i can change icons,move taskbar anywhere,change login screen and even boot screen.
In ubuntu change in icons and theme nothing else.

This is just for ubuntu i know kde is more customizable.

3.    The worst case is my printer worked in ubuntu 10.10 and not in any releases after 11.10.
Now i have a new computer and i can't install ubuntu 10.10 because hd2000 graphics does not support it.
Conclusion windows supports more hardware.Cause everything you purchase they will give you the driver cd.

4.If you don't have a internet ubuntu is useless.While in windows you can back up the software and install them any time you want.

Please ubuntu (canonical) sort this things out somehow.:popcorn:

1) Num lock has never been enabled by default in ubuntu. At least not in the many installs I remember.

2) I have been able to do just about any customization I have needed with ubuntu. Unity itself is not very customizable, but there are many other gnome based solutions.

3) Create a thread on your printer problems, if you haven't already. All of my printers are HP and work perfectly. Which graphics card are we talking about? Google tells me Intel and ATI have HD 3000 series cards. I install my graphics drivers manually and have had no problems with doing so. I have to install these drivers manually in Windows as well. If you need help finding and installing, then feel free to start a thread asking how to do these things, as I am sure one of the community members will be able to help you. Compatibility is a requirement of the hardware manufacturer, not the OS.

4) Not sure what you mean. I did a clean install of Windows 7 Pro yesterday and had to use another machine to get the NIC drivers, as Windows couldn't use the cards.

Ubuntu has AptOnCD, which can be used for copying software as well as the ability to download Debs from the ubuntu repositories and install packages from Sourceforge and other sites. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) [http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/](http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/)

---

