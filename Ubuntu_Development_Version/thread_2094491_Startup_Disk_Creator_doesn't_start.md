---
title: "Startup Disk Creator doesn't start"
date: 2012-12-13
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-12-13
This is the error message that pop-ups in dialog box.

```
An error occurred while talking to the udisks service.
```

```
apt-cache policy usb-creator-gtk udisks
usb-creator-gtk:
  Installed: 0.2.42
  Candidate: 0.2.42
  Version table:
 *** 0.2.42 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
udisks:
  Installed: 1.0.4-7
  Candidate: 1.0.4-7
  Version table:
 *** 1.0.4-7 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
```

Update: already reported [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1090212]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1090212")

---

### Post by ventrical on 2012-12-14
Yup .. same here.

<I clicked "affects me too"> +1

---

### Post by konas on 2012-12-14
+1

Worked well around three weeks ago....

---

### Post by ronacc on 2012-12-14
hasn't worked for me since just after the start of quantal .

---

### Post by mc4man on 2012-12-14
The message just reflects a crash in usb-creator-helper, been happening for quite some time. (& likely well known as reports would go to whoopsie/whatever or filed directly on crash here weeks ago
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1078810](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1078810)

Usually here sdc never works well or at all during dev, generally does near or at release

---

### Post by mc4man on 2012-12-31
With usb-creator 0.2.41 & 0.2.42 dead on landing & still so, -  one can use 0.2.40ubuntu1 (python2.7) in 13.04
To do so - 
get both .debs from here, under "Builds" pick arch.
[https://launchpad.net/ubuntu/+source/usb-creator/0.2.40ubuntu1](https://launchpad.net/ubuntu/+source/usb-creator/0.2.40ubuntu1)
 Put them in a folder, cd to that folder & sudo dpkg -i *.deb to downgrade.

Then before using - 
```
sudo gedit /usr/lib/python2.7/dist-packages/usbcreator/misc.py
```

replace lines 39 & 40 - screen 1
    > from IN import INT_MAX
    MAX_DBUS_TIMEOUT = INT_MAX / 1000.0

with - screen 2 (keep indent as shown
```
MAX_DBUS_TIMEOUT = 2147483
```

---

### Post by ventrical on 2012-12-31
Iv'e used maveric (10.10) to do all my start-up-disks and I also zsync from that install.Never fails.

---

### Post by pressureman on 2013-01-01
... or you could just install grub to a suitably large (2GB+) USB stick, copy the ISO file directly to the stick, and set up the necessary grub menu entries.

I've done this on an old USB stick, and I have semi-latest raring ISO on it, plus 12.10 ISO as a fall back.

If the stick has enough spare space on it, you could even use zsync to update the ISO file directly on the stick, and save yourself another unnecessary step. Keep the .zs-old file as a rollback plan if the new image doesn't work for any reason.

Treat yourself to a decent-sized USB stick, and copy a whole bunch of Linux ISOs to it... much more convenient.

---

### Post by MacUntu on 2013-01-01
```
dd if=ubuntu.iso of=/dev/sdX bs=1M
```

---

### Post by konas on 2013-01-10
Today's update fixed it for me.

---

### Post by mc4man on 2013-01-10
> **konas said:**
> Today's update fixed it for me.

Did you try it yet?
(atm here it works but is going to take a Very long time, normal is about 3 min.

Edit: not the sdc package, something else..

---

### Post by ventrical on 2013-01-10
I'm still zsyncing my isos with a  maveric install and using SDC from there. I'll update and see if i can emulate.

---

### Post by mc4man on 2013-01-10
Probably worth waiting till SDC leaves proposed. The extreme slowdown seen here was due to recent udev source updates.
With *udev* downgraded the python2.7 SDC was normal - 3 min to complete, the new SDC was slow, around 20 min., still nothing like the new SDC with new udev, 8-10 hrs.

---

### Post by ventrical on 2013-01-10
It is working on retrograde time as the percentage increases. Slower than a snail trying to climb a dehydrated cactus. :)

ouch!

---

### Post by cecilpierce on 2013-01-10
No go here on Raring or Quantal.

---

### Post by mc4man on 2013-01-10
Well it doesn't appear in proposed anymore so as is the performance s***s
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1098260](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1098260)

---

### Post by mc4man on 2013-01-10
> **cecilpierce said:**
> No go here on Raring or Quantal.

It seems that on some hardware  SDC never works?? 
Was ok here in quantal release, on raring never worked unless I used the older version with edit to misc.py as in post 6

---

### Post by ventrical on 2013-01-10
> **mc4man said:**
> Well it doesn't appear in proposed anymore so as is the performance s***s
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1098260](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1098260)

<click>

---

### Post by ventrical on 2013-01-11
Still no change after today's updates.

---

### Post by konas on 2013-01-12
> **mc4man said:**
> Did you try it yet?
(atm here it works but is going to take a Very long time, normal is about 3 min.


Indeed, it says it will take 30 min ...

---

### Post by kuvanito on 2013-01-12
i never use startup disk creator 
i always use unetbootin
sudo apt-get install unetbootin
never been happier :)
have of all ubuntu apps are useless,yes useless and that includes Brasero

1-brasero=nero
2-empathy=pidgin
3-libreoffice=microsoft office or google docs(online)
4-remmina=teamviewer
5-rythmbox=totem(deafult)
6-startup disk creator=unetbootin

note:after a clean installation of a daily builds this is my first executed command:
sudo apt-get purge aisleriot* baobab* empathy* gnome-contacts* gnome-games-data* gnome-disk-utility* gnome-online-accounts* gwibber* deja-dup* landscape* libreoffice* onboard* overlay-scrollbar* gnome-orca* remmina* rhythmbox* shotwell* usb-creator* ubuntuone* software-center* xul-ext-ubufox* unity-lens-shopping* unity-webapps* xdiagnose* xterm*
sudo apt-get autoremove
sudo apt-get autoclean 

and if i need anything i go here: [https://apps.ubuntu.com/cat/](https://apps.ubuntu.com/cat/)

---

### Post by cariboo on 2013-01-12
> **kuvanito said:**
> i never use startup disk creator 
i always use unetbootin
sudo apt-get install unetbootin
never been happier :)
have of all ubuntu apps are useless,yes useless and that includes Brasero

1-brasero=nero
2-empathy=pidgin
3-libreoffice=microsoft office or google docs(online)
4-remmina=teamviewer
5-rythmbox=totem(deafult)
6-startup disk creator=unetbootin

note:after a clean installation of a daily builds this is my first executed command:
sudo apt-get purge aisleriot* baobab* empathy* gnome-contacts* gnome-games-data* gnome-disk-utility* gnome-online-accounts* gwibber* deja-dup* landscape* libreoffice* onboard* overlay-scrollbar* gnome-orca* remmina* rhythmbox* shotwell* usb-creator* ubuntuone* software-center* xul-ext-ubufox* unity-lens-shopping* unity-webapps* xdiagnose* xterm*
sudo apt-get autoremove
sudo apt-get autoclean 

and if i need anything i go here: [https://apps.ubuntu.com/cat/](https://apps.ubuntu.com/cat/)

If you feel this way, why even use Ubuntu. I'd suggest instead of removing packages, why not use the mini.iso, and only install the packages you want?

---

### Post by mc4man on 2013-01-29
> **mc4man said:**
> Probably worth waiting till SDC leaves proposed. The extreme slowdown seen here was due to recent udev source updates.
With *udev* downgraded the python2.7 SDC was normal - 3 min to complete, the new SDC was slow, around 20 min., still nothing like the new SDC with new udev, 8-10 hrs.

speed was fixed in latest SDC, currently  0.2.45.1

---

