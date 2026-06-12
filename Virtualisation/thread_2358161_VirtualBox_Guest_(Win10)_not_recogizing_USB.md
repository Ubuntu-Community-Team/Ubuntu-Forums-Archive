---
title: "VirtualBox Guest (Win10) not recogizing USB"
date: 2017-04-10
forum: Virtualisation
---

### Post by jackmetal on 2017-04-10
I moved back to Ubuntu (from Debian) a couple months ago, but I have one problem I haven't been able to resolve.  I'm running Ubuntu 16.10 and have the latest version of VirtualBox installed, along with the extensions and the latest guest utilities in the guest, but USB devices aren't recognized in the Win10 guest (I've tried enabling the different versions of USB (v2, v3, etc) - but so far, none have worked to allow any usb devices to show up in the Windows guest.  It all worked great in Debian, so I'm hoping someone has run across this and knows of a solution since that's the only thing standing in the way of my complete move back to Ubuntu.

Thanks in advance for your help!!!

---

### Post by ajgreeny on 2017-04-10
Are the guest additions you have installed exactly the same version as VBox itself; it can cause problems if they are not?

Have you gone to the Devices menu of the VBox window (or the management bar at top or bottom of the screen) and checked the correct USB items in the listed USB hardware attached?

---

### Post by &amp;KyT$0P# on 2017-04-10
Also, please run this command in Terminal on your host machine -
```
id
```
Does it list the [FONT=Courier New]vboxusers[/FONT] group?

---

### Post by jackmetal on 2017-04-10
Thank-You guys very much!!

I checked everything except that it had put me into the vboxusers group during install (some distro's do, some don't - and it had been a few years since I've used Ubuntu since I've been on mostly debian for the past 8 or 9 years)....and after using VirtualBox for 'years' on all different distributions, I should have known better.  :-)

Thanks again for the help, it's much appreciated!

JM

---

### Post by slickymaster on 2017-04-10
*Thread moved to **Virtualisation**.*

---

