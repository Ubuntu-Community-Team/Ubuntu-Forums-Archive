---
title: "Latest update screwed up flashback"
date: 2013-09-11
forum: Ubuntu Development Version
---

### Post by Smask on 2013-09-11
When I logged in after reboot I had no gnome-panel. When I tried  ctrl-alt-delete and ctrl-alt-t they did nothing. I started gnome-panel manually via nautilus. 

This is probably what screwed my computers:
```
Changes for gnome-session-flashback versions:
Installed version: 1:3.6.2-0ubuntu13
Available version: 1:3.6.2-0ubuntu14

Version 1:3.6.2-0ubuntu14: 

  * debian/patches/50_ubuntu_sessions.patch:
    - Set DesktopName and X-LightDM-DesktopName to Unity instead of GNOME
      since Flashback uses indicators and the same "fallback" components
      Unity does. This will also allow for a more consistent experience
      for Edubuntu which offers both Unity and Flashback.      

```

---

### Post by mc4man on 2013-09-11
That change doesn't seem to be working out here very well either. I removed the various added lines, (DesktopName= and X-LightDM-DesktopName=) in the session .desktops & then the 2 gnome-panel sessions  load fine.
You'd hope this is fixed in the near future...

---

### Post by Cavsfan on 2013-09-12
I was wondering if any one else had this same problem. My panels are also gone both top and bottom in flashback session.
Luckily I have Cairo Dock or I would not be able to do anything.
Hopefully this will be fixed shortly. Meanwhile I guess Unity it is. :(

---

### Post by mc4man on 2013-09-12
here's a report - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217)

As a **temp workaround** one can edit the altered files, 
for no effects
/usr/share/xsessions/gnome-fallback.desktop
/usr/share/gnome-session/sessions/gnome-fallback.session

For effects(compiz
/usr/share/xsessions/gnome-fallback-compiz.desktop
/usr/share/gnome-session/sessions/gnome-fallback-compiz.session

---

### Post by Cavsfan on 2013-09-13
> **mc4man said:**
> here's a report - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1224217)

As a **temp workaround** one can edit the altered files, 
for no effects
/usr/share/xsessions/gnome-fallback.desktop
/usr/share/gnome-session/sessions/gnome-fallback.session

For effects(compiz
/usr/share/xsessions/gnome-fallback-compiz.desktop
/usr/share/gnome-session/sessions/gnome-fallback-compiz.session

I think it is fixed now. I have top and bottom panels. :) Wonder if anything else was fixed.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-session-flashback
gnome-session-flashback:
  Installed: 1:3.6.2-0ubuntu15
  Candidate: 1:3.6.2-0ubuntu15
  Version table:
 *** 1:3.6.2-0ubuntu15 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by VMC on 2013-09-13
Are you kidding me! I thought it was my video causing this.
Installing Ubuntu-Saucy I couldn't get a usable panel so I installed gnome-panel. No panels.  I managed, after creating a empty directory, to drop down to "/usr/share/applications" and from there click on "panel" which worked, but on re-boot again no-panels. So I then tried Cinnamon. Again no panels. Using cinnamon-settings, I got nowhere. Found "panel" again, but this time nothing.
Tried all the "--replace" from compiz, to cinnamon, to you-name-it. They all did what they suppose to do, but all I was left with, was a beautiful, empty background.

I thought I would try UbuntyGNOME 13.10. It works very well. Some glitches but all and all, its a treat. I was very surprised how well it works.

I'm also and have been using Kubuntu 13.10. It is almost flawless. And has been for several weeks. Once I figured out how to control my nvidia chip.
I have installed Kubuntu for a long time, and Saucy is so far the most polished.

If I had found this tread yesterday, I wouldn't have given UbuntuGNOME a try. Glad I did. More options.

---

### Post by Smask on 2013-09-14
```
Changes for gnome-panel versions:
Installed version: 1:3.6.2-0ubuntu14
Available version: 1:3.6.2-0ubuntu15

Version 1:3.6.2-0ubuntu15: 

  * Identify as GNOME; identifying as Unity is buggy (LP: #1224217)
```

---

