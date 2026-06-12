---
title: "boot/startup time"
date: 2020-07-10
forum: The Cafe
---

### Post by T6&amp;sfpER35% on 2020-07-10
so after seeing a couple of posts about people moaning about slow startup / boot times ,i decided to time mine with a stopwatch.
from a completely off pc to a workable pc (after i logged in) ,it took 1 min 51 sec.
should i moan ? how can i shed a second or maybe two ?
:lolflag:

---

### Post by TheFu on 2020-07-10
```
systemd-analyze blame
systemd-analyze  critical-chain
```

---

### Post by GhX6GZMB on 2020-07-12
That's about right for a HDD boot. SDD will be around 25% of that.

---

### Post by TheFu on 2020-07-12
> **ml9104 said:**
> That's about right for a HDD boot. SDD will be around 25% of that.

It is possible to get boot down to less than 20 seconds on spinning HDDs if all the extra crap the DEs load "to be easy" are prevented.  There are lots of threads here where people are able to reduce their boot times by 50% just by disabling stuff they never use.  For example, if you don't use ZFS, BTRFS, Bluetooth, snaps, autofs, samba, LVM, lpd and a bunch of other daemons, why have them run at startup, before the login screen is displayed?

As I look through a system and see a number 1sec "loop" device times, I know these are all for snaps that I seldom use.  The apt-daily-upgrade.service needs to be stopped here too. I patch weekly and don't need any automatic stuff related to that.

```
sudo systemctl stop apt-daily-upgrade.service
sudo systemctl disable apt-daily-upgrade.service
sudo systemctl mask apt-daily-upgrade.service
```

Done. [B]People who like to be nagged about available updates or have them installed automatically wouldn't want to do that.
[/B]
On another system, these are killers:
```
         36.925s systemd-udev-settle.service
         20.171s systemd-fsck@dev-istar\x2d8TB-istar\x2dback3\x2da.service
         19.684s systemd-fsck@dev-istar\x2d8TB\x2dB-lv4_back.service
```

Those are waiting for slow, huge, USB storage devices that go to sleep when not used recently.  I need to prevent that if I want faster startups.
Even wasting 56 seconds, 
```
$ systemd-analyze
Startup finished in 8.060s (kernel) + 1min 1.735s (userspace) = 1min 9.796s
```

That's a no-SSD, dual-core pentium, system with 30+TB of storage connected.  I'll be swapping some of the USB storage to eSATA on that system soon. That will make those times drop or go away.

---

### Post by zebra2 on 2020-07-12
systemd-analyze
Startup finished in 3.652s (kernel) + 47.630s (userspace) = 51.282s 
graphical.target reached after 47.601s in userspac 


Ubuntu 20.10 Gnome 3.36 Wayland
1T HD. 2 x 1.1ghz cores 12G RAM Legacy boot. 

I find this result to be very acceptable.

---

### Post by Chanath on 2020-07-13
> **3nd said:**
> so after seeing a couple of posts about people moaning about slow startup / boot times ,i decided to time mine with a stopwatch.
from a completely off pc to a workable pc (after i logged in) ,it took 1 min 51 sec.
should i moan ? how can i shed a second or maybe two ?
:lolflag:

Check whether the UUID of your swap is correct in /etc/fstab and in /boot/grub/grub.cfg
If it is wrong, it'd take 1 min and 30 sec checking.

---

### Post by P-I H on 2020-07-13
On development version of Ubuntu 20.04.1
```
p-i@asus-b450-f:~$ systemd-analyze
Startup finished in 21.569s (firmware) + 2.216s (loader) + 3.686s (kernel) + 8.068s (userspace) = 35.541s 
graphical.target reached after 8.055s in userspace
p-i@asus-b450-f:~$
```

---

### Post by GhX6GZMB on 2020-07-13
This is mine:
```
macro@macro-pc:~$ systemd-analyze
Startup finished in 3.591s (kernel) + 12.753s (userspace) = 16.344s 
graphical.target reached after 12.721s in userspace
```
12 year old HP/Compaq with 4 GB RAM, 2 GHz CPU and new SSD. Total boot time is 26 seconds, so power-up and BIOS take ~10 seconds. I don't see much room for improvement...

---

### Post by mastablasta on 2020-07-14
hdd should be 45sec -1min, however, with snapd in 20.04 it could take longer.

others already demonstrated the difference when using SSD.

---

