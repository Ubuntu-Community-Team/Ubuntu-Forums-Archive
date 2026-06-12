---
title: "Increase root disk space without loosing data"
date: 2016-11-15
forum: Virtualisation
---

### Post by khalifanizar on 2016-11-15
Hi all,

I'm running a virtual machine with Ubuntu 14.04.1 LTS.
And i want to increase my disk space without loosing data. 

I tried many same solution on the net but i cant really understand if i will loose my data.
I tried this command:
[I][B]
sudo resize2fs /dev/sda1 100G
[/B][/I]
*resize2fs 1.42.9 (4-Feb-2014)*
*The containing partition (or device) is only 15728384 (4k) blocks.*
*You requested a new size of 26214400 blocks.*



I can't run a live CD i'm on remote mode and here is informaion about my machine.

```
df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on[/I]
*/dev/sda1      ext4       59G   35G   21G  63% /*
*none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup*
*udev           devtmpfs  7.9G  4.0K  7.9G   1% /dev*
*tmpfs          tmpfs     1.6G  504K  1.6G   1% /run*
*none           tmpfs     5.0M     0  5.0M   0% /run/lock*
*none           tmpfs     7.9G     0  7.9G   0% /run/shm*
[I]none           tmpfs     100M     0  100M   0% /run/user
```
```
fdisk -l
*Disk /dev/sda: 161.1 GB, 161061273600 bytes*
*255 heads, 63 sectors/track, 19581 cylinders, total 314572800 sectors*
*Units = sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*
*Disk identifier: 0x000f290d*

*   Device Boot      Start         End      Blocks   Id  System*
*/dev/sda1   *        2048   125829119    62913536   83  Linux*
*/dev/sda2       125831166   134215679     4192257    5  Extended*
*/dev/sda5       125831168   134215679     4192256   82  Linux swap / Solaris*
```



```
lsblk

[/I]*NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT*
*sda      8:0    0   150G  0 disk*
*&#9500;&#9472;sda1   8:1    0    60G  0 part /*
*&#9500;&#9472;sda2   8:2    0     1K  0 part*
*&#9492;&#9472;sda5   8:5    0     4G  0 part [SWAP]*
*sr0     11:0    1  1024M  0 rom*

```

Best regards,
Nizar

---

### Post by howefield on 2016-11-15
Thread moved to the "*Virtualisation*" forum.

---

### Post by ajgreeny on 2016-11-15
I assume it is your virtual disk that you wish to enlarge; am I correct?
What is the host OS as I know only Ubuntu Linux as host? If you use Windows of any version as host I can't help you further.

What virtualisation application are you using, as I know only VirtualBox?

I had to increase the virtual disk I had made originally for Windows-XP from 10GB to 20GB which I did with command ```
sudo VBoxManage modifyhd "/home/*username*/VirtualBox VMs/WinXP/WinXP.vdi" --resize 20000
```
After doing that I had to attach an iso file of gparted and hold shift at boot of the VM to change the virtual device to the gparted live OS which I used to expand the XP partition to fill the space that was now unallocated in the virtual disk.

If you originally created a fixed size virtual disk for your VM in VBox you will first have to clone it but this time use a dynamically allocated disk size as you can not enlarge a fixed size virtual disk.

It may sound complicated but is actually easier to do than describe; all went without a problem and I ended with a working 20GB XP installation with no data loss.

---

### Post by khalifanizar on 2016-11-16
[COLOR=#000000]
[/COLOR]No, the virtual disk is already enlarged. It was 60G and now 150G.
Like the *[COLOR=#ff0000]**lsblk **[/COLOR]*[COLOR=#000000]show, there are about 90G unused so i want to add them to the sda1.
[/COLOR]
[COLOR=#000000]What is the host OS as I know only Ubuntu Linux as host? If you use Windows of any version as host I can't help you further.

[/COLOR]Im running [COLOR=#000000]Ubuntu 14.04.1 LTS on a virtual machine and the access is with VMware Sphere client or with ssh mode.
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by ajgreeny on 2016-11-16
OK, I see what you mean.

You will not be able to edit any partitions from your running ubuntu system as it is impossible to edit on mounted partitions, which they will be if running, so a live system is, I'm afraid, essential.

Your free space does not appear to be next to the partition you wish to enlarge, but right at the end of the disk so you will have to delete the swap partition sda5 and then the sda2 extended partition, then enlarge sda1 into the free space but leave the final 4GB (I think) free for a new swap partition.  However, as I say, this will have to be done using a live system, and I am in no position to say how that might be possible for you.

---

