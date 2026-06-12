---
title: "How to resize a partion/filesystem after adding more storage in a VM"
date: 2021-01-12
forum: Ubuntu/Debian BASED
---

### Post by basse00 on 2021-01-12
Hey!

I recently had to extend my virtual disk on one of my VM in proxmox becuase it was full. And i search the web for how to resize it, but none of the guides worked for me, so i'm gonna look for help here.

So the problem:

I have run the "lsblk" to see what's going on and this is how it looks:

loop0                       7:0    0   55M  1 loop /snap/core18/1880
loop1                       7:1    0 55.4M  1 loop /snap/core18/1944
loop2                       7:2    0 71.3M  1 loop /snap/lxd/16099
loop3                       7:3    0 67.8M  1 loop /snap/lxd/18150
loop4                       7:4    0 31.1M  1 loop /snap/snapd/10492
loop5                       7:5    0 31.1M  1 loop /snap/snapd/10707
sda                         8:0    0   60G  0 disk
&#9500;&#9472;sda1                      8:1    0    1M  0 part
&#9500;&#9472;sda2                      8:2    0    1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0   49G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   20G  0 lvm  /

As u can see i managed to extend the sda3 partition, but i dont get it to extend to the os &#9472;ubuntu--vg-ubuntu--lv 253:0    0   20G  0 lvm  /

It only says 20G while it should be 50G. How can i get the filesystem to read that it has gained more space?

btw i'am totally new to linux and how it works so i don't even know if what i have written is correct, so feel free to correct me! I trying to get better at Linux but i have used Windows my whole life soo yeah... Don't know to much.


Any help would be greatly appreciated!

---

### Post by Dennis N on 2021-01-12
When you resize the logical volume **ubuntu-lv** with the **lvextend** command, you need to use the **--resizefs** option to make the file system fill the bigger LV space.

If you didn't use that option, then to make the file system fill the LV space afterwards, you can run **sudo resize2fs /dev/ubuntu-vg/ubuntu-lv**

---

