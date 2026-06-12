---
title: "panp6 lost sound and Sys76 driver install odd"
date: 2010-11-13
forum: System76 Support
---

### Post by jpv on 2010-11-13
I just fully updated a panp6 and rebooted, and now I've lost sound.

Stock Sys76 panp6 Lucid install:

$ uname -a
Linux perry 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

$ aplay -l
aplay: device_list:223: no soundcards found...

$ last reboot
reboot   system boot  2.6.32-25-generi Sat Nov 13 14:17 - 14:55  (00:38)    
reboot   system boot  2.6.32-25-generi Sat Nov 13 01:36 - 14:16  (12:40)

$ cat /etc/apt/sources.list.d/system76.list 
## System76 Driver - Ubuntu Repository
## Please report any bug on [https://bugs.launchpad.net/system76/](https://bugs.launchpad.net/system76/)
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./


So after each (warm) reboot I tried System > Administration > System76 Driver.  I am connected to the 'Net (I'm typing this on the affected machine), and the driver sort-of seems to install.  But...  I get a dialog box with the title "Install Complete" but an *empty* body.  No buttons and clicking the title bar "X" does not close the box.

I'm suspecting the problems are related, but I'm not finding anything in the forums or in Google.

Any clues?

---

### Post by jpv on 2010-11-13
Did a cold boot, removed the battery, cleaned out the fan, etc.

$ sudo aptitude purge system76-driver
$ sudo mv /opt/system76/ /opt/system76.old
$ sudo aptitude install system76-driver
$ system76-driver 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(Reading database ... 242642 files and directories currently installed.)
Preparing to replace libfprint0 20081125git-2 (using libfprint0_20081125git-2_amd64.deb) ...
Unpacking replacement libfprint0 ...
Setting up libfprint0 (20081125git-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fprint-demo is already the newest version.
libpam-fprint is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by jpv on 2010-11-14
I'm starting to suspect hardware problems.  Yesterday Logcheck started emailing me hundreds of USB errors from the kernel, but the *only* USB thing connected is a mouse, which is working fine.  (Is the panp6 optical drive USB?)  I'd figured all the reboots yesterday would fix it, and they did for a while.  But starting around 4am I'm getting them again:

Nov 14 03:50:54 perry kernel: [44842.150068] usb 8-2: device descriptor read/64, error -71
Nov 14 03:50:54 perry kernel: [44842.390048] usb 8-2: device descriptor read/64, error -71
Nov 14 03:50:54 perry kernel: [44842.750020] usb 8-2: device descriptor read/64, error -71
Nov 14 03:50:55 perry kernel: [44842.990186] usb 8-2: device descriptor read/64, error -71
Nov 14 03:50:55 perry kernel: [44843.640038] usb 8-2: device not accepting address 4, error -71
Nov 14 03:50:56 perry kernel: [44844.180038] usb 8-2: device not accepting address 5, error -71
Nov 14 03:50:56 perry kernel: [44844.180059] hub 8-0:1.0: unable to enumerate USB device on port 2


When I look at the errors for just today I see:
$ cut -c45- /tmp/usb.errors | perl -pe 's/address \d+/address */;' | sort | uniq -c | sort -rn 
  10070  usb 8-2: device descriptor read/64, error -71
   4825  hub 8-0:1.0: unable to enumerate USB device on port 2
   3353  usb 8-2: device not accepting address *, error -71
   1836  hub 2-0:1.0: unable to enumerate USB device on port 6
     11  hub 2-0:1.0: connect-debounce failed, port 6 disabled
      8  hub 2-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
      1  __ratelimit: 18 callbacks suppressed


The logs themselves:

# ll kern*
-rw-r----- 1 syslog adm 1.6M 2010-11-14 12:44 kern.log
-rw-r----- 1 syslog adm 2.1M 2010-11-14 07:48 kern.log.1
-rw-r----- 1 syslog adm 5.4K 2010-11-06 08:28 kern.log.2.gz
-rw-r----- 1 syslog adm  832 2010-10-29 19:38 kern.log.3.gz
-rw-r----- 1 syslog adm 1.8K 2010-10-23 09:56 kern.log.4.gz

# zgrep -ci 'usb' kern*
kern.log:16432
kern.log.1:15036
kern.log.2.gz:0
kern.log.3.gz:10
kern.log.4.gz:35

# tail kern.log 
Nov 14 12:42:47 perry kernel: [76755.300027] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:42:51 perry kernel: [76759.392540] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:42:51 perry kernel: [76759.670060] hub 8-0:1.0: unable to enumerate USB device on port 2
Nov 14 12:42:52 perry kernel: [76760.070049] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:42:52 perry kernel: [76760.660046] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:43:05 perry kernel: [76773.010064] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:43:06 perry kernel: [76774.210066] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:43:07 perry kernel: [76775.070081] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:43:07 perry kernel: [76775.440073] hub 2-0:1.0: unable to enumerate USB device on port 6
Nov 14 12:44:04 perry kernel: [76832.440057] hub 2-0:1.0: unable to enumerate USB device on port 6

---

### Post by isantop on 2010-11-15
Does it work from a LiveCD? Or if you install another Ubuntu on a separate partition?

Also, did this happen only after a regular update or a distribution upgrade?

---

### Post by jpv on 2010-11-16
It looks like the USB problem was caused by the very rarely used optical drive.  Various reboots didn't help, but opening and closing the empty drive *seems* to have stopped the log message flood.

This happened after a regular update, as I noted it was/is a stock Sys76 Ubuntu 10.04 install.

After having to tweak the poorly chosen Lucid defaults in /etc/default/grub so I could actually see a grub menu, I tried all the installed kernels:

2.6.32-25-generic < Current, no sound devices
2.6.32-24-generic < no sound devices
2.6.32-23-generic < no sound devices
2.6.32-22-generic < no sound devices
2.6.31-21-generic < Failed to load the NVIDIA driver

Ubuntu 9.10 factory Live-CD = no sound devices

---

### Post by isantop on 2010-11-16
This almost sounds like a hardware problem. Could you send us an email at support...at...system76...dot...com?

---

### Post by jpv on 2010-12-14
This was a hardware problem, just got the machine back and it works fine again.

---

