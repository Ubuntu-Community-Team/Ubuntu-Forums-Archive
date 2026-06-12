---
title: "Hardware Clock"
date: 2008-11-04
forum: Server Platforms
---

### Post by cjwallace on 2008-11-04
Guys.

When my system boots up, you know when you see the OK down the right hand side as its going through all the boot up stuff , for a brief moment i see something along the lines of

Cannot access hardware clock.....something something something.

Is there a log i can view to see what this message says in full?

I know what i have put here is brief but any ideas?

Craig

---

### Post by MJN on 2008-11-04
Try running **hwclock --show** (or even **--debug** for extra detail) - this will attempt to read from the clock and hence test kernel access to it.

Mathew

---

### Post by cjwallace on 2008-11-05
Thank you very much for passing the info along.

Ok so i have run both commands and below is the output

Any ideas?

root@LNMON01:~# hwclock --show
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
root@LNMON01:~# hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.

---

### Post by MJN on 2008-11-05
(From a Google search)
 
Try enabling the rtc-cmos module with **sudo modprobe rtc-cmos** and retrying hwclock. If this works then make it permanent by adding **rtc-cmos** to the **/etc/modules** file.
 
Mathew

---

### Post by cjwallace on 2008-11-05
Thanks for the reply mate.

I have tried the command and get the following

root@LNMON01:~# modprobe rtc-cmos
FATAL: Module rtc_cmos not found.

Any ideas?

Cheers

Craig

---

### Post by forger on 2008-11-05
*edited*

what distribution are you using? Did you upgrade from hardy 8.04.1 to intrepid 8.10?

---

### Post by cjwallace on 2008-11-05
Hi mate.

Yes i upgraded from 8.04 server to 8.10 server

Craig


***edit

Please note this was a fresh install of 8.04 and then 8.10. At the moment the server is not doing anything and nothing has been installed on it.

---

### Post by forger on 2008-11-05
What's your hardware specification?
Post a reply with ```
sudo lshw -short
```

If you're using a macintosh, check this: [http://ubuntuforums.org/showthread.php?t=229678](http://ubuntuforums.org/showthread.php?t=229678)

---

### Post by cjwallace on 2008-11-05
> **forger said:**
> What's your hardware specification?
Post a reply with ```
sudo lshw -short
```

If you're using a macintosh, check this: [http://ubuntuforums.org/showthread.php?t=229678](http://ubuntuforums.org/showthread.php?t=229678)


Hi mate please find as requested. Thanks for your help so far.

```

root@LNMON01:~# lshw -short
H/W path           Device      Class      Description
=====================================================
                               system     ProLiant DL360 G4p
/0                             bus        Motherboard
/0/0                           memory     64KiB BIOS
/0/400                         processor  Intel(R) Xeon(TM) CPU 3.00GHz
/0/400/710                     memory     16KiB L1 cache
/0/400/720                     memory     2MiB L2 cache
/0/400/730                     memory     L3 cache
/0/400/0.1                     processor  Logical CPU
/0/400/0.2                     processor  Logical CPU
/0/406                         processor  Intel(R) Xeon(TM) CPU 3.00GHz
/0/406/716                     memory     16KiB L1 cache
/0/406/726                     memory     1MiB L2 cache
/0/406/736                     memory     L3 cache
/0/406/0.1                     processor  Logical CPU
/0/406/0.2                     processor  Logical CPU
/0/1000                        memory     9GiB System Memory
/0/1000/0                      memory     2GiB DIMM DDR Synchronous 400 MHz (2.5
/0/1000/1                      memory     2GiB DIMM DDR Synchronous 400 MHz (2.5
/0/1000/2                      memory     2GiB DIMM DDR Synchronous 400 MHz (2.5
/0/1000/3                      memory     2GiB DIMM DDR Synchronous 400 MHz (2.5
/0/1000/4                      memory     512MiB DIMM DDR Synchronous 400 MHz (2
/0/1000/5                      memory     512MiB DIMM DDR Synchronous 400 MHz (2
/0/100                         bridge     E7520 Memory Controller Hub
/0/100/2                       bridge     E7525/E7520/E7320 PCI Express Port A
/0/100/4                       bridge     E7525/E7520 PCI Express Port B
/0/100/4/0                     bridge     6700PXH PCI Express-to-PCI Bridge A
/0/100/4/0.2                   bridge     6700PXH PCI Express-to-PCI Bridge B
/0/100/6                       bridge     E7520 PCI Express Port C
/0/100/1c                      bridge     6300ESB 64-bit PCI-X Bridge
/0/100/1c/1                    storage    Smart Array 64xx
/0/100/1c/2        eth0        network    NetXtreme BCM5704 Gigabit Ethernet
/0/100/1c/2.1      eth1        network    NetXtreme BCM5704 Gigabit Ethernet
/0/100/1d                      bus        6300ESB USB Universal Host Controller
/0/100/1d.1                    bus        6300ESB USB Universal Host Controller
/0/100/1d.4                    system     6300ESB Watchdog Timer
/0/100/1d.5                    system     6300ESB I/O Advanced Programmable Inte
/0/100/1d.7                    bus        6300ESB USB2 Enhanced Host Controller
/0/100/1e                      bridge     82801 PCI Bridge
/0/100/1e/3                    display    Rage XL
/0/100/1e/4                    system     Integrated Lights Out Controller
/0/100/1e/4.2                  system     Integrated Lights Out  Processor
/0/100/1f                      bridge     6300ESB LPC Interface Controller
/0/100/1f.1        scsi0       storage    6300ESB PATA Storage Controller
/0/100/1f.1/0.0.0  /dev/cdrom  disk       DVD-ROM GDR8084N
root@LNMON01:~#

```

---

### Post by forger on 2008-11-05
Try this:
**[COLOR="Red"]WARNING[/COLOR]: Use it at your own risk!** (never tried it with servers)

while you're logged in as root:
```
aptitude download udev util-linux
dpkg -i --force-overwrite util-linux*.deb udev*.deb

```

It will download two packages in current folder and reinstall them with forced overwrite, hopefully will work.

You need to reboot after this!

After you reboot, check if it's working (again as root)
```
hwclock --debug
```

If it doesn't, reply with the output of: 
```
grep -ri "rtc" /etc/udev/
ls -ld /dev/rtc*
```

---

### Post by cjwallace on 2008-11-05
> **forger said:**
> Try this:
**[COLOR="Red"]WARNING[/COLOR]: Use it at your own risk!** (never tried it with servers)

while you're logged in as root:
```
aptitude download udev util-linux
dpkg -i --force-overwrite util-linux*.deb udev*.deb

```

It will download two packages in current folder and reinstall them with forced overwrite, hopefully will work.

You need to reboot after this!

After you reboot, check if it's working (again as root)
```
hwclock --debug
```

If it doesn't, reply with the output of: 
```
grep -ri "rtc" /etc/udev/
ls -ld /dev/rtc*
```

Thanks mate. When i run the command i get 

aptitude: unrecognized option '--force-overwrite'

Craig

---

### Post by forger on 2008-11-05
they're two different commands:
```
aptitude download udev util-linux
```
```

dpkg -i --force-overwrite util-linux*.deb udev*.deb

```

---

### Post by cjwallace on 2008-11-05
> **forger said:**
> they're two different commands:
```
aptitude download udev util-linux
```
```

dpkg -i --force-overwrite util-linux*.deb udev*.deb

```

Doh!

Sorry mate still learning Linux at the moment.

I have run the command and rebooted and still the same mate.

i have run

grep -ri "rtc" /etc/udev/
ls -ld /dev/rtc*

and i have run hwclock --debug

Below is the results

```

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Wed Nov  5 13:26:46 2008
root@LNMON01:~# hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.
root@LNMON01:~# grep -ri "rtc" /etc/udev/
/etc/udev/rules.d/60-symlinks.rules:# Compatibility symlink for the CMOS RTC
/etc/udev/rules.d/60-symlinks.rules:SUBSYSTEM=="rtc", DRIVERS=="rtc_cmos", SYMLINK+="rtc"
/etc/udev/rules.d/40-permissions.rules:KERNEL=="rtc",                          GROUP="audio"
/etc/udev/rules.d/85-hwclock.rules:# This file causes the hardware clock to be set when /dev/rtc is available.
/etc/udev/rules.d/85-hwclock.rules:KERNEL=="rtc", ACTION=="add", RUN+="set_hwclock"
root@LNMON01:~# ls -ld /dev/rtc*

```

---

### Post by cjwallace on 2008-11-05
Just Bumping this back up the list

---

### Post by forger on 2008-11-05
you might want to file a bug report about it at [http://bugs.launchpad.net/ubuntu/+filebug](http://bugs.launchpad.net/ubuntu/+filebug)

try a subject such as: "hwclock: Open of /dev/rtc failed, errno=2: No such file or directory"

---

### Post by cjwallace on 2008-11-05
> **forger said:**
> you might want to file a bug report about it at [http://bugs.launchpad.net/ubuntu/+filebug](http://bugs.launchpad.net/ubuntu/+filebug)

try a subject such as: "hwclock: Open of /dev/rtc failed, errno=2: No such file or directory"

Ok mate thanks for your help on this issue.

Out of interest what is not having the hardware clock not working going to do to my system?

I was going to sync the time with ntp anyway?

My main issue is that my server will be used for Zabbix and time needs to be perfect.

Any advice welcome

Craig

---

### Post by forger on 2008-11-07
I believe the problem is that the file /dev/rtc doesn't exist at all, but it is used for checking the cmos hardware clock (correct me if I'm wrong).

I use /etc/crontab and the ntpdate command to keep my time synchronised:
```
/usr/sbin/ntpdate time.nist.gov
```

---

