---
title: "GParted &amp; Ownership Permissions"
date: 2013-08-04
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2013-08-04
I bought a new hard drive and it had to be formatted. I pulled up GParted and formatted and partitioned it.

But when I mounted it, the ownership permissions are all: / or root.

To the developers: If GParted offered a second stage of setting permissions, that would make ease of use. Even if the second stage were only a readme to pop up on screen, saying:

sudo mkdir /mnt/name-a-device

cd /mnt

ls

see the device by the name you have given it.

To change the ownership permissions of each partition you have created:

sudo chown -R user:user /path/to/device

Now, I'm a non-geek guy and don't really know if the above is correct. I've spent a few days fooling around, which isn't relevant to this post, but is about changing external drive ownership.

Thanks for reading.

---

### Post by TheFu on 2013-08-04
This isn't a **gparted** thing.

When you create the directory where the partition was mounted, did you make the owner non-root? 
I'm pretty certain that is what controls the top level mount-point permissions.  You can always use **sudo chown** to make a new owner later.  

If the driver were being mounted as /, having root.root ownership is critical to system security.  As an end-user, that might not seem clear, but it is true. Linux is a multi-user OS from the ground up.  Know it, learn it, love it.

Allowing an end-user to mount anything is a relatively new idea.  For years, only root could (and should) mount file systems. There are many reasons why an average user shouldn't be allowed to mount drives under a multi-user OS ... well, at least not with the default options.  Perhaps if the file system were NTFS or FAT32, then it would be fine.

Perhaps a better workflow could be helpful.  I rarely use gparted to format anything. Just don't think that way.  I use **mkfs** for that.  As a UNIX user, I prefer small tools that do 1 thing well, not the huge-ass monster apps that do everything + have a kitchen sink.  Call it a cultural difference.  Since Linux is like UNIX, it has inherited much of that culture. I prefer it, but clearly other people might disagree.

---

### Post by oldfred on 2013-08-05
You can manually mount the partition, but if an internal drive better to permanently mount with fstab.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

More info:

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by TheFu on 2013-08-05
Has **fdisk** been fixed or does it still have issues with GPT, sector alignments on 4K disks and 2+TB disks?
To avoid those issues, I've switched to using **parted** for anything where fdisk would have been used 2 yrs ago.

Seems safer to always use parted - not fdisk going forward.

---

### Post by coffeecat on 2013-08-05
> **TheFu said:**
> When you create the directory where the partition was mounted, did you make the owner non-root? 
I'm pretty certain that is what controls the top level mount-point permissions.  You can always use **sudo chown** to make a new owner later.  

If the driver were being mounted as /, having root.root ownership is critical to system security.  As an end-user, that might not seem clear, but it is true. Linux is a multi-user OS from the ground up.  Know it, learn it, love it.

In fact, you don't make the mount partition owner non-root, you chown the actual filesystem itself by chowning the mountpoint. This is a subtle point that doesn't seem to be widely understood, and I think the OP has a very good point. If I had £10 for every time I advised someone in this forum how to take ownership of an ext2/3/4 filesystem they'd just created, I'd.... well I'd have more money than I do at the moment! :)

Try this as an experiment:

1 - create new ext4 filesystem in a spare partition or external drive, using Gparted.

2 - Don't automount it from the GUI - you don't want a dynamic mount point for this experiment - but create the mountpoint from the terminal, say /mnt/experiment.

3 - Mount the filesystem to /mnt/experiment from the terminal.

4 - Run ls -l /mnt. /mnt/experiment is owned by root. Agreed?

5 - Run sudo chown yourusername: /mnt/experiment .

6 - Run ls -l /mnt again. /mnt/experiment is now owned by you. Agreed? But is that the mountpoint or the filesystem?

7 - Unmount the filesystem from the terminal.

8 - Now run ls -l /mnt again. You'll find it's owned by root again.

The filesystem has been owned, and the mountpoint only displays the non-root owner of the filesystem while the filesystem is mounted. If you chown the mountpoint before mounting the filesystem, I'm fairly sure the filesystem remains root-owned.

> **TheFu said:**
> Allowing an end-user to mount anything is a relatively new idea. For years, only root could (and should) mount file systems. There are many reasons why an average user shouldn't be allowed to mount drives under a multi-user OS ... well, at least not with the default options. Perhaps if the file system were NTFS or FAT32, then it would be fine.

Relatively new? Well, perhaps if we're talking about PCs rather than server installations. And if we're talking about PCs, what about a data partition formatted ext4 for your personal files on a sole user system? Something I use on my main PC and something I certainly don't want owned by root.

---

### Post by oldfred on 2013-08-05
I still post commands with fdisk, but often now use parted. Fdisk is only for MBR(msdos) partitioned systems and you need parted or gdisk for gpt drives.

I think TheFu was discussing the actual mount not the ownership of a drive. The newest Ubuntus mount external devices within the user like /media/fred/MC4GB (my flash drive) where before you only mounted at /media/MC4GB which is within the system and controlled by root.

---

### Post by coffeecat on 2013-08-05
> **oldfred said:**
> 
I think TheFu was discussing the actual mount not the ownership of a drive. The newest Ubuntus mount external devices within the user like /media/fred/MC4GB (my flash drive) where before you only mounted at /media/MC4GB which is within the system and controlled by root.


Oh sure, but even with automounting on /media/username/mountpoint one still has a problem with the filesystem being owned by root as default until one chowns it. Which is why I agree with the OP - as far as relatively inexperienced users are concerned. 

I've just formatted an external USB stick ext4 and mounted it through Nautilus after which it mounted on /media/myusername/37c691ec-063f-4c05-891f-f2a2e65dc8b0. Trying to drag and drop stuff into the drive via Nautilus failed - with the 13.04 version of Nautilus not even giving me a helpful error message, simply sliding the file back to where I had tried to drag it from. Once I'd chown'd it from the terminal - no problem.

The version of Disk Utility that came in Ubuntu 12.10 (or was it 12.04?) allowed you to "own" a Linux filesystem when creating it. The new "Disks" in 13.04 doesn't even do that - as far as I can tell. A pity, imo. Root owned Linux filesystems in such places as external drives or internal data partitions which have no need to be owed by root confuse and aggravate new users unused to Unix filesystems.

---

### Post by Morbius1 on 2013-08-05
The /media/fred/MC4GB mount point brings up another frustration that will induce a help request to the forums depending on why you are changing permissions.

Change permissions to 777 on MC4GB.
Now lets say you have a process - like samba for example - that wants to add something to that folder as someone other that fred.

No can do. Regardless of the permissions on MC4GB the only user getting to the MC4GB directory is fred:
getfacl -t /media/fred
> USER   root      rwx     
user   fred     r-x     
GROUP  root      ---     
mask             r-x     
other            ---

---

### Post by Mark_in_Hollywood on 2013-08-05
Flexibility with one's software is the real strength of Linux. An inability, such as mine, to understand how to make the drive do what I want isn't. I looked at half a dozen to a dozen ideas (post, how-to's, tutorials) about "mounting" an external hard drive with user:user permissions. In my way of thinking of this, I'm not mounting an OS. I'm mounting a storage device. GParted or "Parted" should say: "Would you like to change the permissions from root? Well, see this . . .". Thanks all for reviewing my idea. And yes, if I had to pay 10 bob every time I asked for/looked for help on this one, I'ld have made the techies a big night out on the town.

---

### Post by Cheesemill on 2013-08-05
Just to add that the new versions of fdisk now support GPT partitioned drives, I'm not sure when they'll make it into Ubuntu though.

```
root@arch:~# fdisk -v
fdisk from util-linux 2.23.1
root@arch:~# 
root@arch:~# fdisk -l /dev/sda
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

Disk /dev/sda: 64.0 GB, 64023257088 bytes, 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: gpt


#         Start          End    Size  Type            Name
 1         2048         6143      2M  BIOS boot parti grub-bios
 2         6144    125045390   59.6G  Linux LVM       lvm-ssd

```

---

