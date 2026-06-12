---
title: "isw raid won't mount at boot"
date: 2010-03-03
forum: Server Platforms
---

### Post by sherl0k on 2010-03-03
Hey all,

I'm having some trouble getting an intel software RAID to mount at boot and I'm really confused as to why. I run dmraid -y and it shows the RAID is activated, but it's not until I run gparted that the partition is available.

```

root@zangetsu:~# dmraid -r
isw: untested metadata version 1.3.00 found on /dev/sdf
isw: untested metadata version 1.3.00 found on /dev/sde
isw: untested metadata version 1.3.00 found on /dev/sdd
isw: untested metadata version 1.3.00 found on /dev/sdc
isw: untested metadata version 1.3.00 found on /dev/sda
/dev/sdf: isw, "isw_caeigfjbga", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sde: isw, "isw_caeigfjbga", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdd: isw, "isw_caeigfjbga", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdc: isw, "isw_caeigfjbga", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sda: isw, "isw_caeigfjbga", GROUP, ok, 2930277166 sectors, data@ 0

```

```

root@zangetsu:~# dmraid -ay
isw: untested metadata version 1.3.00 found on /dev/sdf
isw: untested metadata version 1.3.00 found on /dev/sde
isw: untested metadata version 1.3.00 found on /dev/sdd
isw: untested metadata version 1.3.00 found on /dev/sdc
isw: untested metadata version 1.3.00 found on /dev/sda
RAID set "isw_caeigfjbga_Images" already active

```

in /dev/mapper there's isw_caeigfjbga_Images, but I can't mount that. When I run gparted, isw_caeigfjbga_Images1 shows up and gets mounted. What is gparted doing to make the partition visible? I can't figure it out for the life of me. I just want to be able to put the command in /etc/rc.local so it shows up at boot...

---

### Post by sherl0k on 2010-03-03
okay, I solved my own problem.

the following makes the partition visible to be mounted:

```

kpartx -a /dev/mapper/isw_caeigfjbga_Images

```

putting that in /etc/rc.local, follow by a mount -a, will mount the drive on boot. the partition shows up at /dev/mapper/isw_caeigfjbga_Images1.

---

