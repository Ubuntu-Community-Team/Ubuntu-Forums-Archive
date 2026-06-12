---
title: "Adding squashfs support"
date: 2012-01-16
forum: Server Platforms
---

### Post by fcoury on 2012-01-16
I am using the Ubuntu 10.04 64-bit ec2 official AMI and it doesn't come with squashfs support. 

Is there a straightforward way of adding support for squashfs?

---

### Post by Cheesemill on 2012-01-16
```
apt-get install squashfs-tools
```

---

### Post by fcoury on 2012-01-16
Unfortunately that allows me to create new SquashFS files, but not mount them.

---

### Post by Cheesemill on 2012-01-16
This has always worked for me:
```
sudo mount /path/to/squash_image /mnt/mountpoint -t squashfs -o loop
```What happens if you try this?

---

### Post by fcoury on 2012-01-16
It gives me that unknown filesystem error. The squashfs entry is not in /proc/filesystems and modprobe squashfs doesn't work as well :-(

---

### Post by Cheesemill on 2012-01-16
You may need to install the kernel modules:
```
apt-get install squashfs-modules-`uname -r`-generic-di
```

---

### Post by fcoury on 2012-01-16
I will try that and report back - thanks a lot!

---

