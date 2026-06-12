---
title: "Sensor Applet"
date: 2005-08-01
forum: Requests
---

### Post by Omnios on 2005-08-01
When I first started with Ubuntu I could not get any of the dock app cpu sensors to work with my hardware P4 1.6ghz so I looked for one on the net. Anyways I came accross an dock app that worked like a charm and was easy to install with only lmsensors as a dependancy. I don't think there is a deb package yet but not shure as its a very small program. Im including a link to the website.

[http://freshmeat.net/projects/sensors-applet/](http://freshmeat.net/projects/sensors-applet/)






 This sensor works where other don't and works well!

---

### Post by Sam on 2005-08-02
Yes, and it's cute too ! :razz:

[img]http://img182.imageshack.us/img182/993/sensorsapplet7rg.png[/img]

---

### Post by Skel on 2005-08-02
Would be awesome to get one workign on my pc my bios reads the temp but no program on linux has been able to hmmm :-#  hopefully this will

---

### Post by Sam on 2005-08-02
[QUOTE=Skel]Would be awesome to get one workign on my pc my bios reads the temp but no program on linux has been able to hmmm :-#  hopefully this will[/QUOTE]
Did you tried lm-sensors ?

There is an [howto](http://ubuntuforums.org/showthread.php?t=2780) for Warty, but it works well on Hoary.

---

### Post by Omnios on 2005-10-20
Hi aperently this applet is in Debian as sensors-applet as a debian package.

---

### Post by Omnios on 2006-01-12
APerently this is now available from snaptic

---

### Post by yabbadabbadont on 2006-03-21
I don't suppose it would be possible to get the 1.6 version into backports?  I'm going to download the source and see if I can build it myself to be sure that it will work with the existing breezy libraries.  This version adds some features and also additional hardware support.  Here is the changelog from the author's site:```
Version:	1.6
ChangeLog
(1.5.2 -> 1.6) :	Added support for icons for each sensor, 
with intelligent default selections for each sensor interface.
Added support for ibm-acpi kernel module (#1386478).
Added a help manual, accessible via the panel applet menu.
Fixed memory leak (#1394943).
Backported code to handle therm_adt746x prior to 2.6.12 as well as current
 therm_adt746x device
Display temperatures without any decimal places as almost all interfaces only use integers,
 and the only one that doesn't is i2c-sys which only uses half degrees at most.
NOTE: The upgrade to 1.6 will break current configurations - please remove
 GNOME Sensors Applet from the panel and then re-add it after upgrading.

```

EDIT: It compiles, installs (checkinstall of course), and works fine under breezy.

---

