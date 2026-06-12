---
title: "New Users"
date: 2006-06-17
forum: Testimonials &amp; Experiences
---

### Post by tedboy021052 on 2006-06-17
Hi just like to say that I am running Ubuntu for the first time and is does a great deal for me. It runs all my hardware apart from seing my NTFS Drive and Old Tablet Wacom. I have a wallpaper which shows my feeling to ward 'MS'. I find the OS very fast and the users interface easy to set up. In Short Its GREAT sorry about Shouting.

If you have some ideas about using my Tablet Wacom pen or view NTSF Drive please help it will not stop me using this great software there are many ways to skin the 'Cat'

Bye

---

### Post by RRS on 2006-06-17
Follow [these directions]("http://easylinux.info/wiki/Ubuntu#Windows") to access your NTFS drive.

Sorry, can't help with your Tablet Wacom pen though, you might search the hardware section of the forums.

Welcome aboard :)

---

### Post by IYY on 2006-06-17
Is your tablet in the following list?:

```
UD and UD II
PenPartner
Graphire 1 & 2
Intuos 1 & 2
Cintiq & TabletPC
Graphire 1, 2, 3 & 4
Cintiq & CintiqPartner
Intuos 1, 2, & 3
Volito 1 & 2
PenPartner 1 & 2
DTF 521
```

If it is, you can try the following site:

[http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)

---

### Post by graigsmith on 2006-06-18
you should be able to get your wacom tablet working. 

install this package   wacom-tools

& simple edit of your etc/X11/xorg.conf file should get it working.

this can go under the mouse device section.

```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"

  
EndSection
```

If that doesn't work after a reboot, you should check this howto out.  your device setting might be wrong.  since you have a serial tablet, i am not sure if the ubuntu-tools package will create a dev/input/wacom device.  if it doesn't you might have to directly use the serial port that your tablet is on (the howto details finding the port it is on)

here is the howto,  if you have any problems setting up your wacom tablet. send me a message.  or feel free to contact me on AIM, user name graigrsmith.  you can also contact me on jabber.  [email]graig@jabber.org[/email]

[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+howto](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom+howto)

---

