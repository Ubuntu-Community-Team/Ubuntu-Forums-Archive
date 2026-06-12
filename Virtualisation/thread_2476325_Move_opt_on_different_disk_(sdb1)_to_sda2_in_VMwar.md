---
title: "Move /opt on different disk (sdb1) to sda2 in VMware Workstation Pro."
date: 2022-06-23
forum: Virtualisation
---

### Post by whizzkid-raj5 on 2022-06-23
Hello all,

I have GNS3 VM in VMware Workstation Pro. 
GNS3 provides ready-made VMs and we can directly import them in VMware Workstation Pro and start working with it.
The current GNS3 VM is running on Ubuntu 20.04.4 LTS as you can see from the output below.

I have also taken outputs of some important commands so that you can see the structure of all the drives and directories.

The /opt directory is on different disk i.e. sdb1 and / is on different disk i.e. sda2

So I want to move entire sdb1 to sda2 without losing any data in sdb1 or sda2. And if I copy any data to /opt which is now in sdb1, but after the transfer of /opt to sda2, any data that I copy to /opt should go to sda2.

And after all this is successfully completed, I hope I can remove the second hard disk in VMware which contains /opt now, right?

Please help. I have also attached the VMware disks screenshot to this thread.

```
[COLOR=#008000]**root@gns3vm:~#**[/COLOR] [COLOR=#EE82EE]**lsb_release -a**[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    [COLOR=#FF0000]**Ubuntu 20.04.4 LTS**[/COLOR]
Release:        20.04
Codename:       focal
```
```
[COLOR=#008000]**root@gns3vm:~#**[/COLOR] [COLOR=#EE82EE]**df -h**[/COLOR]
**Filesystem      Size  Used Avail Use% Mounted on**
udev             16G     0   16G   0% /dev
tmpfs           3.2G  1.5M  3.2G   1% /run
[COLOR=#FF0000]**/dev/sda2        20G  6.3G   12G  35% /**[/COLOR]
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/loop0       62M   62M     0 100% /snap/core20/1494
[COLOR=#FF0000]**/dev/sdb1       1.5T  7.0G  1.4T   1% /opt**[/COLOR]
/dev/loop1       62M   62M     0 100% /snap/core20/1518
/dev/loop2       68M   68M     0 100% /snap/lxd/21835
/dev/loop3       47M   47M     0 100% /snap/snapd/16010
/dev/loop4       45M   45M     0 100% /snap/snapd/15904
/dev/loop5       68M   68M     0 100% /snap/lxd/22753
tmpfs           3.2G     0  3.2G   0% /run/user/1000
```
```
[COLOR=#008000]**root@gns3vm:~#**[/COLOR] [COLOR=#EE82EE]**lsblk**[/COLOR] 
**NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT**
loop0    7:0    0 61.9M  1 loop /snap/core20/1494
loop1    7:1    0 61.9M  1 loop /snap/core20/1518
loop2    7:2    0 67.2M  1 loop /snap/lxd/21835
loop3    7:3    0   47M  1 loop /snap/snapd/16010
loop4    7:4    0 44.7M  1 loop /snap/snapd/15904
loop5    7:5    0 67.8M  1 loop /snap/lxd/22753
**sda      8:0    0 19.5G  0 disk** 
&#9500;&#9472;sda1   8:1    0    1M  0 part 
&#9492;&#9472;[COLOR=#FF0000]**sda2   8:2    0 19.5G  0 part /**[/COLOR]
**sdb      8:16   0  1.5T  0 disk** 
&#9492;&#9472;[COLOR=#FF0000]**sdb1   8:17   0  1.5T  0 part /opt**[/COLOR]
```
```
[COLOR=#008000]**root@gns3vm:~#**[/COLOR] [COLOR=#EE82EE]**fdisk -l**[/COLOR]
Disk /dev/loop0: 61.94 MiB, 64925696 bytes, 126808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 61.95 MiB, 64933888 bytes, 126824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 67.25 MiB, 70508544 bytes, 137712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 46.98 MiB, 49233920 bytes, 96160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 44.72 MiB, 46870528 bytes, 91544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 67.83 MiB, 71106560 bytes, 138880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

**Disk /dev/sda: 19.54 GiB, 20971520000 bytes, 40960000 sectors**
[B]Disk model: VMware Virtual S
[/B]Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: BFA768D8-7456-4147-A732-1F8B08825581

[B]Device     Start      End  Sectors  Size Type
/dev/sda1   2048     4095     2048    1M BIOS boot
[COLOR=#FF0000]/dev/sda2   4096 40957951 40953856 19.5G Linux filesystem[/COLOR][/B]

[B]Disk /dev/sdb: 1.48 TiB, 1610612736000 bytes, 3145728000 sectors
[/B][B]Disk model: VMware Virtual S
[/B]Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x083b1967

[B]Device     Boot Start        End    Sectors  Size Id Type
[/B][COLOR=#FF0000]**/dev/sdb1        2048 3145727966 3145725919  1.5T 83 Linux**[/COLOR]
```

---

### Post by howefield on 2022-06-23
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2022-06-23
This is more of a system question than a Virtualization question, but who cares... LOL

Two different option approaches...

Option 1- Create a new partition on whatever disk you want to move it to. Create/format a filesystem onto that new partition. Copy the contents of your old /opt mount to the new partition. Update the /etc/fstab file to point it to the new location. Test it. Clean up the old location after success.

Option 2- Create a new /opt directory under /, where your root system is located. Copy over the contents of your old /opt mount to that new directory. Comment out the mount line of /opt in your /etc/fstab file. Test.  Clean up the old location after success.

---

### Post by whizzkid-raj5 on 2022-06-24
Thanks a lot, @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547").

I backed up my /opt folder data and then edited the /etc/fstab file with nano editor as root and added a comment on the line of /opt mount and saved it and shutdown the VM.
Then I removed the 2nd HDD which was 1.5 TB and contained /opt. And I expanded the 1st HDD size from 19.5 GB to 2 TB.
Then I started the VM and check with df -h and lsblk and /opt mount drive was gone i.e. sdb1. Now sda2 was there with size of 19.5 GB i.e. resize to 2 TB not yet reflecting.
So I opened fdisk /dev/sda and then print with p command then delete partition number 2 i.e. sda2 with d command.
Then create new partition number 2 with n command and accept default first and last sector values and preserve the signature of drive with No option.
Then I changed ID of created partition number 2 to Linux LVM by typing the t option in fdisk and then selecting the value as 31
And then write the changes with w command
Then inputting below commands.
pvresize /dev/sda2 (install pvresize by command "apt install lvm2 -y", if pvresize command not found error comes)
growpart /dev/sda 2
resize2fs /dev/sda2

And then I verified that sda2 was resized to 2 TB by entering the commands df -h and lsblk.

Only 1 thing that I think is not needed from above steps is:
pvresize /dev/sda2 (this command might give an error)

Thanks a lot for your help again, @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547").

I wish there was a like button or some way to show my appreciation for your help.

---

### Post by MAFoElffen on 2022-06-26
I am happy that worked for you. That it it helped and marked as "Solved" also helps others later, when they search for what might solve their own problems... 

Appreciation? That I can share my experience to help others makes me happy.

---

