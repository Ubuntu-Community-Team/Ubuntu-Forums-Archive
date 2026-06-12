---
title: "Ubuntu 11.10 x64 +ssd ocz vertex 2"
date: 2011-10-17
forum: Server Platforms
---

### Post by jedan83 on 2011-10-17
How to enable trim support  in fstab conf? tanks:(

---

### Post by VirtualFido on 2011-10-17
Change:
```
errors=remount-ro
```
to
```
noatime,discard,errors=remount-ro
```

In other words, add **discard** to mount options. The **noatime** is also useful for SSDs to minimize writes.

---

### Post by jedan83 on 2011-10-17
nano /etc/fstab

 ext4  /      noatime,discard,errors=remount-ro  0  1

 but boot  defaults or    noatime,discard 0  2

 tanks!:confused:
 ext4  /boot  defaults -- (noatime,discard )   0  2

---

### Post by VirtualFido on 2011-10-17
```
ext4  /      noatime,discard,errors=remount-ro  0  1
```Atleast, thats what I have for my SSD.

This is the content of my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=000000-52f0-46de-8615-9c240ee7c364 /               ext4   **noatime**,**discard**,errors=remount-ro 0       1
# Storage drives.
/dev/sdb1    /storage/hdd1    ext4    defaults,noatime 0 0
/dev/sdc1    /storage/hdd2    ext4    defaults,noatime 0 0
# Directories with lots of write is mounted as tmpfs (ram).
none    /tmp        tmpfs    defaults,noatime,mode=1777 0 0

```

---

### Post by jedan83 on 2011-10-18
ok tanks!
what is   ?
# none    /tmp        tmpfs    defaults,noatime,mode=1777 0 0

---

### Post by VirtualFido on 2011-10-18
> **jedan83 said:**
> ok tanks!
what is   ?
# none    /tmp        tmpfs    defaults,noatime,mode=1777 0 0
It mounts the /tmp folder in RAM to prevent excessive writes on the SSD. Since its a temporary folder, it doesn't matter if the content is lost on reboot :)

---

### Post by jedan83 on 2011-10-18
add line  fstab
#none /tmp tmpfs defaults,noatime,mode=1777 0 0


:popcorn:ok -tanks!

---

