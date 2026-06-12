---
title: "Initramfs pausing boot and flagging different disks as mdadm spares"
date: 2014-03-29
forum: Server Platforms
---

### Post by Erk1209 on 2014-03-29
Hello, I could really use a hand with this problem so thank you in advance!

I just added two disks to my MD array and grew the file system to match the new array. However, each time I reboot Initramfs pops up and asks if I want to boot the array in a degraded state and cites /proc/mdstat to show one or two disks as spares as the source of my problem. However, if I log in, neither /proc/mdstat or mdadm -D /dev/md0 show any hint of an issue and the array mounts correctly and all data appears to be accessible. I have tried updating my mdadm.conf file as well as update-initramfs -u a few times with no changes. An interesting note: initramfs seems to flag different disks as spares each time.

Can anyone help me solve this problem? Please let me know if you need additional information

---

