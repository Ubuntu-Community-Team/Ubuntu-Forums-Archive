---
title: "No Space left on device"
date: 2016-01-21
forum: Server Platforms
---

### Post by joelbarnard on 2016-01-21
Please help, my system has locked up and I can't even cd or move around within he console, the error given is "do-bash: cannot create temp file for here-document: No space left on device", but I can't figure out how to free up this space. 

The output of "df -h" is

```
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/ZION--vg-root  149G  149G  8.0K 100% /
none                       4.0K     0  4.0K   0% /sys/fs/cgroup
udev                       986M  4.0K  986M   1% /dev
tmpfs                      200M  760K  199M   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                       996M     0  996M   0% /run/shm
none                       100M     0  100M   0% /run/user
/dev/sda1                  236M  109M  115M  49% /boot
/dev/sdc                   3.6T  1.7T  1.8T  48% /media/backups
/dev/sdb                   1.8T  1.6T  107G  94% /media/data
```

"ls /boot" shows

```
abi-3.16.0-37-generic         lost+found
abi-3.16.0-38-generic         memtest86+.bin
abi-3.16.0-39-generic         memtest86+.elf
abi-3.16.0-41-generic         memtest86+_multiboot.bin
config-3.16.0-37-generic      System.map-3.16.0-37-generic
config-3.16.0-38-generic      System.map-3.16.0-38-generic
config-3.16.0-39-generic      System.map-3.16.0-39-generic
config-3.16.0-41-generic      System.map-3.16.0-41-generic
grub                          vmlinuz-3.16.0-37-generic
initrd.img-3.16.0-37-generic  vmlinuz-3.16.0-38-generic
initrd.img-3.16.0-38-generic  vmlinuz-3.16.0-39-generic
initrd.img-3.16.0-39-generic  vmlinuz-3.16.0-41-generic
```



Please advise, thank you gurus!

---

### Post by deadflowr on 2016-01-21
boot's not the problem in this case.
You have no space on the main root file system
```
/dev/mapper/ZION--vg-root  149G  149G  8.0K 100% /
```

The two places I'd look into would be the /var directory and the /home directory.
Specifically the /var/log directory.
Log files can get enormous if unchecked problems run amuck.

---

### Post by darkod on 2016-01-22
You can check each folder size with something like this (if it works since you are low on free space):
```
sudo -i
cd /
du -sh *
```

That will make you root, go to the / location and check each folder. If you see any big ones, you can cd into them and run the same command, etc... Of course, it also depends whether relevant data has filled in your root or something you can get rid of. When you find folder sizes you will have a better idea is it something you can remove or not.

---

### Post by joelbarnard on 2016-01-23
@darkod and @deadflowr Thank you so much, I just got home and will take a look at that now!

---

