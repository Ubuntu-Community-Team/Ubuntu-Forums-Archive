---
title: "Installation/Boot parameters?"
date: 2008-08-05
forum: Slackware and derivatives
---

### Post by IIMarckus on 2008-08-05
Hi guys, I've never run Linux before. I've been slowly getting into it with some liveCDs like Slax and Knoppix, and today I installed Slackware on my system. The box is an older machine with an AMD-K6 processor.

When I first put in the Slackware install disk, it gave a message saying
```
This kernel requires the following features not present on the CPU:
0:15
Unable to boot - please use a kernel appropriate for your CPU.
```

I then booted the CD with the parameter "huge.s," and it ran fine. I then installed Slackware, as well as LILO. When LILO asked for default boot parameters, I put in "huge.s", assuming it would require the same parameter as before. Then I continued with the rest of the installation. Everything seemed to go fine, but now the computer doesn't work.

When the computer is turned on, a Slackware screen pops up asking to choose an OS, Windows or Linux. (The computer has two hard drives; hda has Windows 2000 and hdb has Linux.) Windows works fine. When I try Linux, this displays:
```
Loading Linux......................................
BIOS data check successful
This kernel requires the following features not present on the CPU:
0:15
Unable to boot - please use a kernel appropriate for your CPU.
```

I hear first-time Linux users frequently have problems, but I didn't expect something this early. Any insights? :D

---

### Post by saulgoode on 2008-08-05
> **IIMarckus said:**
> I then booted the CD with the parameter "huge.s," and it ran fine. I then installed Slackware, as well as LILO. When LILO asked for default boot parameters, I put in "huge.s", assuming it would require the same parameter as before.
You probably don't need to enter any boot parameters here, and it is certainly not necessary to type "huge.s" (that is the name of the kernel image to be loaded, it is not a parameter). 

You should reboot into your system using the install CD. At the LILO menu, type in the following command:

***huge.s root=/dev/hda1 noinitrd ro ***

After you have logged in as root, go to the /boot directory and do an "***ls -l***". You should see something similar to (ignore the "tesla" files, which are my custom kernels):

```
lrwxrwxrwx 1 root root      37 2008-04-21 22:34 README.initrd -> /usr/doc/mkinitrd-1.3.2/README.initrd
lrwxrwxrwx 1 root root      25 2008-05-05 06:17 System.map -> System.map-2.6.24.5-tesla
-rw-r--r-- 1 root root  902376 2008-05-05 08:23 System.map-2.6.24.5-tesla
-rw-r--r-- 1 root root  844024 2008-04-30 15:02 System.map-generic-2.6.24.5
-rw-r--r-- 1 root root  880187 2008-04-30 14:19 System.map-generic-smp-2.6.24.5-smp
-rw-r--r-- 1 root root 1282875 2008-04-30 15:15 System.map-huge-2.6.24.5
-rw-r--r-- 1 root root 1320655 2008-04-30 14:42 System.map-huge-smp-2.6.24.5-smp
-rw-r--r-- 1 root root     512 2008-04-12 03:08 boot.0300
-rw-r--r-- 1 root root     512 2008-04-11 03:03 boot.0301
-rw-r--r-- 1 root root     199 2008-04-12 03:08 boot_message.txt
lrwxrwxrwx 1 root root      21 2008-05-05 06:17 config -> config-2.6.24.5-tesla
-rw-r--r-- 1 root root   82657 2008-05-05 06:07 config-2.6.24.5-tesla
-rw-r--r-- 1 root root   82369 2008-04-30 15:02 config-generic-2.6.24.5
-rw-r--r-- 1 root root   82657 2008-04-30 14:19 config-generic-smp-2.6.24.5-smp
-rw-r--r-- 1 root root   82208 2008-04-30 15:15 config-huge-2.6.24.5
-rw-r--r-- 1 root root   82536 2008-04-30 14:42 config-huge-smp-2.6.24.5-smp
-rw-r--r-- 1 root root    5040 2008-04-01 03:39 diag1.img
-rw------- 1 root root   98816 2008-05-05 08:23 map
-rw-r--r-- 1 root root   15754 2008-02-21 19:08 slack.bmp
lrwxrwxrwx 1 root root      22 2008-05-05 06:17 vmlinuz -> vmlinuz-2.6.24.5-tesla
-rw-r--r-- 1 root root 2326072 2008-05-05 08:22 vmlinuz-2.6.24.5-tesla
-rw-r--r-- 1 root root 2055544 2008-04-30 15:02 vmlinuz-generic-2.6.24.5
-rw-r--r-- 1 root root 2167384 2008-04-30 14:19 vmlinuz-generic-smp-2.6.24.5-smp
-rw-r--r-- 1 root root 4205208 2008-04-30 15:15 vmlinuz-huge-2.6.24.5
-rw-r--r-- 1 root root 4369880 2008-04-30 14:42 vmlinuz-huge-smp-2.6.24.5-smp
```

The main items of interest are the symbolic links (i.e., the lines that begin with a lowercase L). You want to change the 'vmlinuz' link so that it points to the 'vmlinuz-huge-2.6.24.5' kernel:

***rm vmlinuz && ln -s vmlinuz-huge-2.6.24.5 vmlinuz***

You will likewise want to change the 'System.map'

***rm System.map && ln -s System.map-huge-2.6.24.5 System.map***

And 'config':

***rm config && ln -s config-huge-2.6.24.5 config***

After making these changes, run LILO:

***lilo***

And reboot. If this does not work, please post the contents of '/etc/lilo.conf' and the listing of your '/boot' directory (long format).

---

