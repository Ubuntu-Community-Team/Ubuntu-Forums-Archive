---
title: "[SOLVED] Low Disk Space on 750G HD"
date: 2008-03-01
forum: System76 Support
---

### Post by natibo on 2008-03-01
I keep getting an error when I boot up that I have low disk space and 100% of it is being used.  Yet disk usage analyzer tells me I am only using 4% of my disk.

This problem is so bad that sometimes the X window system will not start because it says the disk is full.  Is there some max size for my home folder?

This is a major error and I can use some help.

---

### Post by jdb on 2008-03-01
On the command line type in:

df -h

This will show the usage of each partition.
You may have a number of partitions with one of them being very small & full.

John

---

### Post by natibo on 2008-03-01
here is the output.

If I have a problem, how do I change the size?

natibo@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.6G  5.6G     0 100% /
varrun                2.0G  152K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  116K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             675G   22G  620G   4% /home
overflow              1.0M  108K  916K  11% /tmp
natibo@ubuntu:~$

---

### Post by gaussian on 2008-03-01
> **natibo said:**
> here is the output.

If I have a problem, how do I change the size?

natibo@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.6G  5.6G     0 100% /
varrun                2.0G  152K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  116K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
lrm                   2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             675G   22G  620G   4% /home
overflow              1.0M  108K  916K  11% /tmp
natibo@ubuntu:~$

Your root partition (/dev/sda1) is full. If I were you I would:
1) Backup your root and home to an external drive (using live cd, so your root is not "alive")
2) Try a live disk with parted (e.g. your ubuntu installation disk):
-Reduce the size of your home by about 30G
-Create a new partition (sda4)
-Copy the content (with parted) of sda3 to sda4
-delete sda3
-resize your root to at least 15G (with a drive of that size you certainly can afford it)
-recreate partition 3 to the empty space between 1 and 4
-copy stuff back from 4 to 3
-remove partition 4
-resize partition 3 back to recapture part taken by partition 4
3) reboot and pray. If things are not good you have an extra backup. If things are bad, you need that backup.

Others might have more straightforward advise.

---

### Post by jdb on 2008-03-01
The advice gaussian gave is good but there is one more thing you need to check.

At the command line type in mount.
Check what type sda1 & sda3 are.
If they are ext3 you are good to go.

If you have a LVM partition you may not be able to resize it.
Someone might have some good advice on managing LVM partitions.
I don't.
I don't even know how to mount the things from a liveCD.
That makes backing up very hard if your system is in trouble.


John

---

### Post by compholio on 2008-03-02
> **jdb said:**
> ...
I don't even know how to mount the things from a liveCD.
...

Open a terminal, then:
```
sudo su
mkdir /media/sda1
mkdir /media/sda3
mount /dev/sda1 /media/sda1
mount /dev/sda3 /media/sda3
```

That's all there is to it.  Personally, I think the CD should do that automagically but it doesn't (at least, not yet).

---

### Post by gaussian on 2008-03-03
> **compholio said:**
> Open a terminal, then:
```
sudo su
mkdir /media/sda1
mkdir /media/sda3
mount /dev/sda1 /media/sda1
mount /dev/sda3 /media/sda3
```

That's all there is to it.  Personally, I think the CD should do that automagically but it doesn't (at least, not yet).

I think you might have missed the part about LVM, since your advice does not seem to work with Gutsy 64-bit live cd. I tested this, since I have been contemplating a reinstall (to 64-bit, but that is worth another thread some day) and being able to run a backup with a live-cd would be worthwhile. I would be really excited if someone would give directions on how to resize the LVM.

Here is what you need to do to access LVM with Ubuntu live-cd (steps I took with my Darter):

1) Activate your network
2) apt-get update 
3) apt-get install lvm2
4) modprobe dm-mod
5) vgchange -ay
6) mkdir /media/ubunturoot
7) mount /dev/ubuntu/root /media/ubunturoot

---

### Post by compholio on 2008-03-03
Opps, sorry about that - apparently I'm not conscious this evening.

---

### Post by jdb on 2008-03-03
gaussian

Thanks for the info on mounting LVM partitions.

If you want to reinstall to 64 bit this is a excellent opportunity to reformat to ext3.

You can even make a couple of spare partitions for things like trying Hardy Heron.

Extra partitions are also good places to boot to when you want to back up your main partition, much faster than a liveCD.

I have a really big non-bootable partition I mount as /data, that's were all my stuff goes.

I have a bunch of 10 G partitions I run different operating systems on & experiment with.

I put mount points & entries for them in fstab, that makes them easy to play with.

to back one up:
cd /some_mount_point
sudo tar czf /data/some_name.tgz .

to restore one I usually unmount it & reformat the partition, it's faster than removing stuff & gives me a nice fresh unfragmented partition.
After remounting the partition:
cd /some_mount_point
sudo tar xf /data/some_name.tgz

If you do  lot of reformatting it's easier to use /dev/sda type entries instead of UUID type  in fstab & menu.lst.
It saves finding the new UUIDs with dumpe2fs & editing fstab & menu.lst.

I created /data/boot/grub/menu.list & that is the one I use.
I always let a new installation install it's own, but after I boot to it & take a look at what its done, I just edit my menu.lst if needed & then run grub.

sudo grub
# The following will then find all the grub folders,
#The one for my data partition is on hd0,7
find /boot/grub/stage1
# Next I tell grub were to look for my menu.lst
root (hd0,7)
#  Finally Il write the MBR
setup (hd0)
# I'm done
quit

If things get really hosed up you can always boot to a liveCD & run grub.

With this setup I can try some really crazy stuff & it's easy to recover when I toast things.

John

---

### Post by thomasaaron on 2008-03-03
Did you try emptying your trash?

---

### Post by gaussian on 2008-03-03
> **jdb said:**
> gaussian

Thanks for the info on mounting LVM partitions.

If you want to reinstall to 64 bit this is a excellent opportunity to reformat to ext3.

You can even make a couple of spare partitions for things like trying Hardy Heron.

Extra partitions are also good places to boot to when you want to back up your main partition, much faster than a liveCD.

I have a really big non-bootable partition I mount as /data, that's were all my stuff goes.

I have a bunch of 10 G partitions I run different operating systems on & experiment with.

I put mount points & entries for them in fstab, that makes them easy to play with.

to back one up:
cd /some_mount_point
sudo tar czf /data/some_name.tgz .

to restore one I usually unmount it & reformat the partition, it's faster than removing stuff & gives me a nice fresh unfragmented partition.
After remounting the partition:
cd /some_mount_point
sudo tar xf /data/some_name.tgz

If you do  lot of reformatting it's easier to use /dev/sda type entries instead of UUID type  in fstab & menu.lst.
It saves finding the new UUIDs with dumpe2fs & editing fstab & menu.lst.

I created /data/boot/grub/menu.list & that is the one I use.
I always let a new installation install it's own, but after I boot to it & take a look at what its done, I just edit my menu.lst if needed & then run grub.

sudo grub
# The following will then find all the grub folders,
#The one for my data partition is on hd0,7
find /boot/grub/stage1
# Next I tell grub were to look for my menu.lst
root (hd0,7)
#  Finally Il write the MBR
setup (hd0)
# I'm done
quit

If things get really hosed up you can always boot to a liveCD & run grub.

With this setup I can try some really crazy stuff & it's easy to recover when I toast things.

John

John,

Thanks for the info. That is pretty much my plan, with the exception that I would for the moment hang on to the original 32-bit install as an option, since I don't want anything to interrupt the mission critical services (and by that I mean mostly Webkinz, which seemed to work fine with 64-bit Gutsy live-cd after flash install) and I'd like to hold on to all the customizations.

And the LVM is making that hard. I think when I have spare time I will backup everything, reformat the drive to several partitions (including the separate data partition like you suggest) and copy back the initial 32-bit installation to one of the partitions (I know I have to play with fstab, menu.lst and grub's device.map after that).  And have couple spare partitions where I can install 64-bit Hardy and Gutsy etc to check when things are in good enough shape to get completely rid of the 32-bit.

I like your idea of using /dev/sdaX type entries, I will certainly follow that. As for GRUB, I have been fan of chainloading: let each system install its own grub at its partition (in Ubuntu you need alternative install disk do this when installing) and then chainload to different partitions. This way kernel updates will be automatically added to menu.lst and available without any manual interventions.

---

### Post by natibo on 2008-03-06
Re-installed ubuntu using the all available disk space or something like that.

---

