---
title: "Ram problems after 9.10 upgrade"
date: 2009-11-22
forum: System76 Support
---

### Post by jdayrutherord on 2009-11-22
I have a daru laptop, 4gb of ram, and recently upgraded to
9.10, installed system76 drivers 2.4.0

After a reboot, pulseaudio will grow to about 900MB within an
hour, and continue to eat more ram. Other processes seem to grow as
well but not like pulseaudio. Eventually all 4gb of ram will be
in use and swap takes over, and of course performance takes a big
dive. Reboot time. I have not yet removed pulse but expect I will
soon. Has anyone else seen this in 9.10? It seemed to work ok prior
to the 9.10 upgrade.

---

### Post by thomasaaron on 2009-11-23
We've not been able to duplicate this in the shop, so it may have something to do with the actual upgrade. However, there is a know pulseaudio memory leak that I've seen one other report on.

See...
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)
...and...
[http://ubuntuforums.org/showthread.php?p=8327736](http://ubuntuforums.org/showthread.php?p=8327736)

You might try running from a 9.10 live CD (freshly downloaded) and see if the problem occurs there. If not, a fresh install may be less hassle.

---

### Post by jdayrutherord on 2009-11-26
I did a fresh 9.10 install from cd and installed the 2.4 system
76 driver.

But it seems that pulseaudio is still eating a lot of ram.
This is a 4GB Daru3 laptop, and after about 12 hours of uptime
pulseaudio is using 2.3GB of ram. Most of that 12 hours is without
any real use of the system. Would any specific diagnostic information
be of use in tracking this down?

---

### Post by jdb on 2009-11-26
> **jdayrutherord said:**
> I did a fresh 9.10 install from cd and installed the 2.4 system
76 driver.

But it seems that pulseaudio is still eating a lot of ram.
This is a 4GB Daru3 laptop, and after about 12 hours of uptime
pulseaudio is using 2.3GB of ram. Most of that 12 hours is without
any real use of the system. Would any specific diagnostic information
be of use in tracking this down?

That's the classic symptom of a memory leak.
They generally don't leave a trail & are very hard to troubleshoot.
Memory leaks are caused by faults in the application.

If that's what it is you shouldn't be the only one experiencing it.
If googling doesn't get any hits there must be something really unique
about your setup that triggers the bug.

jdb

---

### Post by thomasaaron on 2009-11-27
How old was the CD you installed from?
Are you fully updated?

Does...

killall pulseaudio

...halt the leakage?

---

### Post by jdayrutherord on 2009-11-28
I did poke around a bit. It seems it is not all that unique, and has
definitely been reported by others.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)
It seems to point to udev. It might also be related to intel
sound chips, which maybe why its not as widely encountered.
It was reported that after a fresh install the problem was not there until
the recommended updates were installed.
It seems likely there will be updates available soon.

---

### Post by gpstar on 2009-11-28
you have to revert back to version 147~6.0 of udev to stop the leak currently, but you may loose automounting features. This happened to me on a system76 bonobo. On a fresh install of 9.10 64bit everything was fine except automounting of external drives and usb flash memory. A updated udev 147~6.1 came out and upgrading to that caused the pulse audio memory leak. Downgrading back to 147~6.0 udev stopped the leak.

the actual culprit was

```
closedir(dir);
``` line in udev-node.c in the updated udev. still waiting for a fix for it.

---

### Post by adonis827 on 2009-12-01
> **gpstar said:**
> you have to revert back to version 147~6.0 of udev to stop the leak currently, but you may loose automounting features. This happened to me on a system76 bonobo. On a fresh install of 9.10 64bit everything was fine except automounting of external drives and usb flash memory. A updated udev 147~6.1 came out and upgrading to that caused the pulse audio memory leak. Downgrading back to 147~6.0 udev stopped the leak.

the actual culprit was

```
closedir(dir);
``` line in udev-node.c in the updated udev. still waiting for a fix for it.

i am having this problem too. may laptop has 3gb ram and 4gb swap. there was a time pulseaudio took up almost all of that ram and swap.

so from a new install- your flash drive will not be automounting. if you upgrade udev to 147~6.1 your flash drive will again automount but you will have pulseaudio leaking quite often. 

so which poison will you choose. 

[http://greatwebhost.com.ph/blog/2009/11/07/your-flash-drive-not-auto-mounting-in-ubuntu-kubuntu-maybe-xubuntu-too-9-10-32-or-64-bit/](http://greatwebhost.com.ph/blog/2009/11/07/your-flash-drive-not-auto-mounting-in-ubuntu-kubuntu-maybe-xubuntu-too-9-10-32-or-64-bit/)

---

### Post by gpstar on 2009-12-01
if you use the older version of udev, 147~6.0, you can temporary solve the automounting issue by just opening a terminal and restarting udev by typing

```
sudo stop udev
sudo start udev
```

then everything will automount fine. Just you have to do that everytime you reboot the computer.

---

### Post by michaelzap on 2009-12-02
I've also begun to notice this problem. My computer gets sluggish and then I notice that pulseaudio is using two or three gigs of RAM. killall pulseaudio frees the memory up, but it just keeps growing again afterwards.

This is a fresh install of 64-bit vanilla Ubuntu on a Lenovo Y530 with Intel sound and video.

Yet another Karmic drag...:(

---

### Post by abulluck on 2009-12-03
I have it too on my panp4 running a fresh install of 9.10.  Currently I just killall pulseaudio if it gets too high.  But would love a solution that doesn't break automounting.

---

### Post by Fazelki on 2009-12-03
For me it generally goes up continually at a rate of about 2MB every 5s, then sometimes levels out or simply slows down to a near unnoticeable rate at some amount less than 300MB, such as around 250MB right now.
Otherwise it starts heading up towards 1.3GB or so.
I've just been killing pulseaudio every once in a while for now.

---

### Post by shaviro on 2009-12-17
I seem to be having the same problems. I will wait until I hear of a better solution.

---

### Post by salemboot on 2009-12-29
apt-get remove pulseaudio


There are also race conditions with kernels past 2.6.31.14.  Stick with that one.

---

### Post by jdayrutherord on 2010-02-01
Not sure if this is on any use, but kubuntu 9.10 64 does
not seem to have the pulse audio memory leak problem. I have had it running for a couple of days now and now memory issues or udev issues that I can see.

---

### Post by thomasaaron on 2010-02-02
Another tech told me a few days ago that the pulseaudio memory leak in gnome has been fixed by a recent update.

---

