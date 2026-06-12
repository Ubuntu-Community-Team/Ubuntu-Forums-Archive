---
title: "Confusing resolution"
date: 2015-07-08
forum: Server Platforms
---

### Post by zkab on 2015-07-08
I have some Ubuntu servers (14.04.2 LTS) with Intel 2nd Generation Core Processor Family Integrated Graphics Controller on mobo.
I don't use any GUI for the servers - only ssh login.
The servers was recently connected via VGA to a KVM switch (Aten 8-ports ACS1208A).
After that it sometimes complains when rebooting ... the console shows following message: 'The current timing is not supported by the monitor display. Please change your input timing to 1920x1080@60 Hz or any other monitor listed timing as per the monitor specifications.'

The console is locked with that message and I can't ssh login to the servers - only hw reset which feels uncomfortable - very annoying.
The display shows with its menu system that the resolution is 720 x 400 @ 70 Hz ... hmmm ... so why is it complaining - that resolution is specified as an display option ... confusing
How can I set all the resolutions that my display can handle or is there another solution.
There is no /etc/X11/xorg.conf

Preset Display Modes (Dell U2212HM) from the manual.

VESA, 720 x 400 31.5 70.0 28.3 -/+
VESA, 640 x 480 31.5 60.0 25.2 -/-
VESA, 640 x 480 37.5 75.0 31.5 -/-
VESA, 800 x 600 37.9 60.3 40.0 +/+
VESA, 800 x 600 46.9 75.0 49.5 +/+

VESA, 1024 x 768 48.4 60.0 65.0 -/-
VESA, 1024 x 768 60.0 75.0 78.8 +/+
VESA, 1152 x 864 67.5 75.0 108.0 +/+
VESA, 1280 x 1024 64.0 60.0 108.0 +/+
VESA, 1280 x 1024 80.0 75.0 135.0 +/+
VESA, 1600 x 1200 75.0 60.0 162.0 +/+
VESA, 1920 x 1080 67.5 60.0 148.5 +/+

---

### Post by zkab on 2015-07-20
Anyone ?

Right now I don't know where to start searching for the error ...
Is the problem with:

1) KVM switch (Aten 8-ports ACS1208A)
2) The monitor (Dell U2212HM)
3) Ubuntu X-software

or a combination ?

---

### Post by howefield on 2015-07-20
Let's start by moving your thread here to the "*Server Platforms*" forum seeing as you have not had any luck in General Help..

---

