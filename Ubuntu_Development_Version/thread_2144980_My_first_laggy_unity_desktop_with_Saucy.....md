---
title: "My first laggy unity desktop with Saucy...."
date: 2013-05-14
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-05-14
I did the upgrade from latest update(saucy-proposed enabled) and reboot. After login, open facebook and gmail on firefox and unity start to lag. Switch to console and below is the fbgrab from htop:

[IMG]http://i.imgur.com/nyIdTzc.png[/IMG]

---

### Post by 2F4U on 2013-05-14
Not sure what your question is. From the screenshot it is pretty obvious that the system is pretty much saturated with running Unity desktop and load averages are quite high. What are your hardware specs? If this is an older machine I would probably use a desktop environment which places less demand on the machine, such as, for example, XFCE or LXDE.

---

### Post by ventrical on 2013-05-14
Check 'about this computer'  (details) and see if llvmpipe is running.

---

### Post by serdotlinecho on 2013-05-14
I'm sorry if this too confusing. No I mean, Unity is running fine on my  netbook before i did the upgrades yesterday. But after reboot and login, I open  facebook on firefox, and gnome control center online accounts launched  asking for integration with the desktop. Then after that it started to  lag. Luckily, I can  switch to tty1 console and login. Fire up htop to see what is hogging my resources, using fbgrab to take screenshot. As you can see the above post, HUD, unity panel, bamfdaemon and dbus-daemon was hogging my cpu resources.

For Ventrical:

[IMG]http://i.imgur.com/B1BVDzI.png[/IMG]


I don't want to open gnome control center cause i'm afraid it will start to hogging my cpu and unity become laggy again ;)
And when I open gnome terminal profile preferences, gnome terminal crashed. Eye of Gnome also crashed when I open it. Can't take screenshot using gnome-screenshot too. Nevermind, i have i3 wm as a backup when Unity is unusable :)

So, after today's update and upgrade, still having problem with Unity become laggy when i open facebook, gmail and google plus on firefox. I've discovered that unity-desktop-integration, ubuntu-online-accounts and unity-websites-integration firefox extensions was causing the lagginess issue. When I disabled those extensions, no more lagginess when i'm using Unity and Firefox.

---

