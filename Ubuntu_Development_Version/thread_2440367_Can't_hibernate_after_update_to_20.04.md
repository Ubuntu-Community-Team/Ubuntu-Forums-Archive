---
title: "Can't hibernate after update to 20.04"
date: 2020-04-09
forum: Ubuntu Development Version
---

### Post by evvdcaec on 2020-04-09
Hibernation worked for me on 19.10. I updated to 20.04 with [FONT=courier new]do-release-upgrade -d[/FONT] and now hibernation is borked. When I [FONT=courier new]systemctl hibernate[/FONT] the system appears to suspend to disk. Upon booting the system again it's as if I did a regular boot. 

I'm using GNOME. I had an issue with Nvidia where after a regular suspend it would kill the GNOME session and force me to log back in. I stopped using the Nvidia card and stuck with the iGPU and that issue went away. This feels similar but I'm not using the Nvidia card anymore, as far as I can tell, and I'm not having that suspend issue anymore. 

```
cat /sys/power/state
   freeze mem disk
```

```
cat /sys/power/disk
   [platform] shutdown reboot suspend test_resume

```

[inxi -F]("https://pastebin.com/qwyvPy9N")

[/etc/fstab]("https://pastebin.com/X6WMYGCm")

[/etc/default/grub]("https://pastebin.com/WcaW1kvi")

[/var/log/sylog]("https://pastebin.com/7059wMei")

[/var/log/kern.log]("https://pastebin.com/Df9xELRG")

[dmsg]("https://pastebin.com/Ssd3PsQ3")

[/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla]("https://pastebin.com/b3xjv3xt")

Does anyone see anything obvious that I'm missing?

---

### Post by knossos456 on 2020-04-09
Was your Ubuntu 19.10 a upgrade version to ? And if yes from witch version?
If not i presume you had setup it manually?
The thing I can say is Ubuntu 16.04 made it from fresh install, Ubuntu 18.04 and 20.04 not. Shame, it is mandatory for laptops on battery working.
Debian 10 does it at install stage as Ubuntu 16.04.

---

### Post by evvdcaec on 2020-04-11
The 19.10 was a fresh install.

---

### Post by knossos456 on 2020-04-11
ok. please provide return of :
```
swapon -s
```and please provide size of RAM memory

---

### Post by dbergst on 2020-04-13
Please post the output from sudo blkid.  There should be a matching entry in your /etc/fstab.

---

### Post by evvdcaec on 2020-04-17
swapon -s gives me:

```
Filename                Type        Size    Used    Priority
/dev/nvme0n1p6                             partition    15999996    0    -2

```

The UUID from blkid matches the UUID in fstab. 

My swap partition appears to be working according to htop. 

I have 16GB of RAM and a little over 15GB swap. I usually float under 3GB usage.

---

### Post by dino99 on 2020-04-17
Have had that issue too (ubuntu session and swap file which is the default now); but since a weeek or so, the problem is gone by itself (proposed archive is activated)

---

### Post by evvdcaec on 2020-04-18
> **dino99 said:**
> Have had that issue too (ubuntu session and swap file which is the default now); but since a weeek or so, the problem is gone by itself (proposed archive is activated)

Well, don't I feel sheepish. I just tried it again and now it works. 

Thanks, dino99!

---

