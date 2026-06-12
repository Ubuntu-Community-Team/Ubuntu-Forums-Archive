---
title: "server load"
date: 2020-02-05
forum: Server Platforms
---

### Post by mikelhayes on 2020-02-05
howdy,
my first install (18.004LTS) went straight forward until I updated the server; then it ran out of room?
238GB raid1, no way. So I'm thinking the default partition sizing is small. Is terminal gparted the only way to address this?
Thank you

---

### Post by TheFu on 2020-02-06
Please prove the statements using commands posted with output wrapped in "*code tags*".  

These commands would be helpful:
```
lsblk
df -Th
```

---

### Post by mikelhayes on 2020-02-11
```
Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-55-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

  System information as of Tue Feb 11 17:23:38 UTC 2020

  System load:  0.0               Processes:           295
  Usage of /:   99.6% of 3.87GB   Users logged in:     1
  Memory usage: 0%                IP address for eno1: 
  Swap usage:   0%

  => / is using 99.6% of 3.87GB


8 packages can be updated.
8 updates are security updates.

99%
```

```
lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0  88.5M  1 loop /snap/core/7270
sda                         8:0    0 278.9G  0 disk
&#9500;&#9472;sda1                      8:1    0     1M  0 part
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 277.9G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0     4G  0 lvm  /
sdb                         8:16   0 557.8G  0 disk
sr0                        11:0    1  1024M  0 rom
```
```
toor@clicalc1:/etc$ df -Th
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs   32G     0   32G   0% /dev
tmpfs                             tmpfs     6.3G   18M  6.3G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.9G     0 100% /
tmpfs                             tmpfs      32G     0   32G   0% /dev/shm
tmpfs                             tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                             tmpfs      32G     0   32G   0% /sys/fs/cgroup
/dev/loop0                        squashfs   89M   89M     0 100% /snap/core/7270
/dev/sda2                         ext4      976M   78M  832M   9% /boot
tmpfs                             tmpfs     6.3G     0  6.3G   0% /run/user/1000
```

---

### Post by TheFu on 2020-02-11
The interesting parts are here:
```
$ df -Th
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.9G     0 100% /
/dev/sda2                         ext4      976M   78M  832M   9% /boot
```
All the other crap is just there to confuse stuff.

For this:
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 278.9G  0 disk
&#9500;&#9472;sda1                      8:1    0     1M  0 part
&#9500;&#9472;sda2                      8:2    0     **1G**  0 part **/boot**
&#9492;&#9472;sda3                      8:3    0 277.9G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0     **4G**  0 lvm  **/**
sdb                         8:16   0 557.8G  0 disk
```
Those are the useful parts.  Plus, we see you have sdb. A slightly more useful version of that command is:
```
\lsblk -o fstype,name,size,type,mountpoint
```

The / LV (ubuntu--vg-ubuntu--lv) is full.  There is good news.
a) The disk appears to have 278G total storage, but the current setup is using about 5G.
b) You selected to use LVM during the install.  **BRILLIANT!**  This makes adding storage easy, probably. Just need to check a few things.

Please post the commands + output from
```
sudo pvs
sudo vgs
sudo lvs

```
If those show 278+ GB in each, then 1 command can make the / LV (currently 4GB), to be 25GB.
And another command can create a separate /home/ LV of whatever size you want.  I'd start with 25G there too.
And if this is a desktop system, you'll want a 4.1G swap LV.  That needs 3 changes to setup.

LVM makes adding a little more storage 5 seconds.  The real power comes from not over allocating and just adding enough space for about 3 months at a time.  Leaving 20% unused leaves space for better backups using LVM snapshots and will drastically increase SSD lifespans.

If the vgs/lvs commands above look good, which I expect, 
To expand the LV for / and increase the file system, do this:
```
sudo lvextend       -L +21G      --resizefs       /dev/mapper/ubuntu--vg-ubuntu--lv
```
That should work on the running system and immediately, the storage should be about 25G in size. The last parameter needs to be a path - you can grep to get it from the fstab.  Should look something like:  **/dev/mapper/ubuntu--vg-ubuntu--lv**  Check YOUR fstab.

To create a 4.1G swap LV, is a few more steps, but still easy. Same for making an LV for /home/.
If you web search for "lvm tutorial", the top three should be from reputable sources and provide concepts with simple commands.

When it comes to Unix storage, there are 4 major ideas.
[LIST=1]
[*] The disk
[*] The partition - GPT allows 100+ primary partitions.  MBR allows 4 primary partitions. Use GPT. 
[*] The file system - a file system must be put onto the partition (or LV in your case).  mkfs is the command. mkswap is used for swap.
[*] The mount - generally, it is best to mount via the /etc/fstab configuration. Avoid any GUI.
[/LIST]

When using LVM, an LV - logical volume can almost always be thought of as the same as a partition.  There's time to learn that stuff later.

---

### Post by mikelhayes on 2020-02-11
PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3  ubuntu-vg lvm2 a--  277.87g 273.87g
toor@clicalc1:~$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- 277.87g 273.87g
toor@clicalc1:~$ sudo lvs
  LV        VG        Attr       LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 4.00g

---

### Post by mikelhayes on 2020-02-11
sudo lvextend -L +21G --resizefs ubuntu--vg-ubuntu--lv           Please specify a logical volume path.

---

### Post by TheFu on 2020-02-11
**Code tags** please. Too hard to read otherwse.

Took me about 10 min to get the post right. Ignore the email verson. Read the post above.

---

### Post by mikelhayes on 2020-02-11
sorry I don't see an above.
Thanks so far.

---

