---
title: "Nautilus 3.30 and desktop icons"
date: 2018-12-18
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-12-18
Nautilus 3.30 in proposed```
corrado@corrado-p13-dd-1107-x:~$ inxi -SCx
System:    Host: corrado-p13-dd-1107-x Kernel: 4.20.0-042000rc7-generic x86_64 bits: 64 
           compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.1 Distro: Ubuntu 19.04 (Disco Dingo) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake 
           rev: 9 L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
corrado@corrado-p13-dd-1107-x:~$ apt policy nautilus
nautilus:
  Installed: 1:3.30.4-1ubuntu1
  Candidate: 1:3.30.4-1ubuntu1
  Version table:
 *** 1:3.30.4-1ubuntu1 100
        100 /var/lib/dpkg/status
     1:3.26.4-0ubuntu9 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
corrado@corrado-p13-dd-1107-x:~$ 
```

---

### Post by mc4man on 2018-12-19
I gather the thought is neutered is better than nothing. Quick glance shows,
No DnD
No execute on files (links, launchers, ect.
Reduced context menu

---

### Post by corradoventu on 2018-12-19
Once the icons have been placed on the desktop, they can not be removed with gnome tweaks. Only personal folder and trash icon can be removed.

---

### Post by corradoventu on 2019-01-12
Nautilus 3.30 arrived today WITH desktop icons. Application icons on desktop must be allowed to run - click on icon and allow run.
Appication icons works fine, .jpg and .png pictures appear as miniature, .ods files opens correctly but .txt files does not open.

---

### Post by jbicha on 2019-01-12
Do you have a Snap or Flatpak version of gedit installed? Opening text files works fine here.

---

### Post by corradoventu on 2019-01-12
My gedit is standard, no Snap or Flatpak```
corrado@corrado-p6-dd-1227:~$ snap list
Name                  Version         Rev   Tracking  Publisher   Notes
core                  16-2.36.3       6130  stable    canonical&#10003;  core
gnome-3-26-1604       3.26.0          74    stable/&#8230;  canonical&#10003;  -
gnome-calculator      3.30.1          260   stable/&#8230;  canonical&#10003;  -
gnome-characters      3.30.0          139   stable/&#8230;  canonical&#10003;  -
gnome-logs            3.30.0          45    stable/&#8230;  canonical&#10003;  -
gnome-system-monitor  3.30.0          57    stable/&#8230;  canonical&#10003;  -
gtk-common-themes     0.1-4-g88bc1b2  818   stable/&#8230;  canonical&#10003;  -
corrado@corrado-p6-dd-1227:~$ apt policy gedit
gedit:
  Installed: 3.30.2-2
  Candidate: 3.30.2-2
  Version table:
 *** 3.30.2-2 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p6-dd-1227:~$ 
```

edit: text files are correctly opened from /Home/Desktop but not from desktop

Sorry: problem occurs only with Wayland session ... false ... also x11
may be because text file was flagged as 'executable'

edit:can confirm: being executable does not cause problem if i click on the icon in the nautilus window /Home/Desktop wile i have the problem if i click the icon on the desktop so the same text file is edited from /Home/Desktop but not from desktop.

---

### Post by Chazall1 on 2019-01-12
No I do not have access files from the desktop. I am also using Nemo as my default. Nautilus Desktop Icons show all the time after update. After update I have both icons on my desktop. Nemo and Nautilus. I have not figured out yet how to just show nemo icons only.

---

### Post by mc4man on 2019-01-13
> **corradoventu said:**
> Nautilus 3.30 arrived today WITH desktop icons. Application icons on desktop must be allowed to run - click on icon and allow run.
Appication icons works fine, .jpg and .png pictures appear as miniature, .ods files opens correctly but .txt files does not open.

Try a fresh install using latest image, you'll see current behavior

---

### Post by corradoventu on 2019-01-14
As I explained editing my previous post the problem occurred because the text file was flagged as 'executable' removed the flag now text file is correctly edited.
You suggest to use latest image, i'm using an image dated 20181227 always updated, do You think make a difference?
Thanks

---

### Post by corradoventu on 2019-01-14
Using nautilus 3.30 with icons on desktop:
Changing Dock Icon size (Settings-Dock-Icon size) the icons on desktop disappear, they reappear creating a file or a folder in desktop or in /Home/Desktop
Sometimes they reappear also changing icon size again.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717)

---

### Post by PaulW2U on 2019-01-15
> **corradoventu said:**
> Using nautilus 3.30 with icons on desktop:
Changing Dock Icon size (Settings-Dock-Icon size) the icons on desktop disappear, they reappear creating a file or a folder in desktop or in /Home/Desktop
Sometimes they reappear also changing icon size again.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717/+attachment/5229291/+files/Screencast%20from%2001-15-19%2011%3A55%3A52.webm](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717/+attachment/5229291/+files/Screencast%20from%2001-15-19%2011%3A55%3A52.webm) is how I 'm seeing this issue. The screencast has been added to the bug report and the issue noted on the ISO Testing Tracker.

Repeatedly changing the icon size sometimes results in a crash but that's not something that I can reproduce at will.

---

### Post by mc4man on 2019-01-15
> **corradoventu said:**
> Using nautilus 3.30 with icons on desktop:
Changing Dock Icon size (Settings-Dock-Icon size) the icons on desktop disappear, they reappear creating a file or a folder in desktop or in /Home/Desktop
Sometimes they reappear also changing icon size again.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1811717)
Seems fixed in the latest git of desktop icons, if I use git-d1027f8 (20190114) here the issue doesn't occur.

---

### Post by corradoventu on 2019-01-17
After last updates desktop icons works properly
```
corrado@corrado-p5-dd-0115:~$ apt policy gnome-shell-extension-desktop-icons
gnome-shell-extension-desktop-icons:
  Installed: 19.01-1
  Candidate: 19.01-1
  Version table:
 *** 19.01-1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu disco/main i386 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p5-dd-0115:~$ apt policy nautilus
nautilus:
  Installed: 1:3.30.4-1ubuntu1
  Candidate: 1:3.30.4-1ubuntu1
  Version table:
 *** 1:3.30.4-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p5-dd-0115:~$ 
```

---

