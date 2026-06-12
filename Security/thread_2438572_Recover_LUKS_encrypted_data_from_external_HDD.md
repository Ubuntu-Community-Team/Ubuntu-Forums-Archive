---
title: "Recover LUKS encrypted data from external HDD"
date: 2020-03-14
forum: Security
---

### Post by kaky951357 on 2020-03-14
Hello folks,
My computer won't boot probably due to a hardware problem, fortunately my HDD is still running, so i put it in a hard drive enclosure to read its content via usb, the system that i used in my laptop is ubuntu and during the installation i chose to have a separate and encrypted partition for the home folder.
Now when i try to access the home partition it won't ...
when run : ```
sudo ecryptfs-recover-private
```
I get : ```
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/1000/doc’: Permission denied
find: ‘/run/user/1000/gvfs’: Permission denied
find: ‘/proc/2999/task/2999/net’: Invalid argument
find: ‘/proc/2999/net’: Invalid argument
find: ‘/proc/3120/task/3120/net’: Invalid argument
find: ‘/proc/3120/net’: Invalid argument

```
and when i run : ```
sudo cryptsetup luksDump /dev/sda7 -v
```
i get : ```
Command failed with code -1 (wrong or missing parameters).
```
what should i do to access my files please ...?
Thanks for trying to help.
Have a great day.

---

### Post by TheFu on 2020-03-14
This might help: [https://ubuntuforums.org/showthread.php?t=2438311](https://ubuntuforums.org/showthread.php?t=2438311)

---

### Post by EuclideanCoffee on 2020-03-14
You created a new installation with the external drive mounted as a partition?

Of course your home user won't have permission to open /proc because the permission belongs to root.

If you take one computer partitioned for Linux separately and try to mount it as a home directory, there will be directories included in the lvm block that are not compatible.

You can use the partition as a /home partition, but it will include everything from root, including /proc, which is typically in your root directory.

Your tree would look like this:

/root/home/proc/

Instead of mounting it as your home directory, I would move your home directory to a new drive and repartition your drive.

---

### Post by kaky951357 on 2020-03-15
Hello,
Thank you for your answers.
So what you are saying is that : it's not possible to access data on the encrypted home folder of my previous system with an other ubuntu system like i would if it wasn't encrypted.
i just want to access the data not boot a system using the home folder of an other.
What is PV ? and how can i get it ?```
PV=c7205467
```
have a great day.

---

### Post by TheFu on 2020-03-15
What we are saying is there are 2 very different types of encryption.  in 14.04, HOME directory encryption was per-userid and had metadata leak problems in addition to being slow.  That method was deprecated around 16.04 (i don't recall exactly when).    i used this method for about a month before determining it broke my backups and wasn't something i could easily fix.

The other method is shown as "whole drive encryption with LVM" during Ubuntu installations.  it uses a much more efficient method that doesn't leak metadata and encrypts an entire device.  A device can mean anything - as is normal for all Unix systems.

Here's an example layout wth whole dsk encrypton:
```
$ lsblk (plus a bunch of options)
NAME                        SIZE RO TYPE  MOUNTPOINT
sda                       465.8G  0 disk  
+-sda2                      732M  0 part  /boot
+-sda3                    464.6G  0 part  
| +-sda3_crypt            464.6G  0 crypt 
|   +-ubuntu--vg-root        25G  0 lvm   /
|   +-ubuntu--vg-home--lv    75G  0 lvm   /home
|   +-ubuntu--vg-stuff      100G  0 lvm   /stuff
|   +-ubuntu--vg-swap_1     4.5G  0 lvm   [SWAP]
+-sda1                        0   512M  0 part  /boot/efi
```
See how all of sda3 is used for the LUKS "container"?  That "container becomes the PV, Physical Volume, for the LVM2 needs. The PV is entirely used by the VG, then parsed out to LVs as needed.  As you can see, The partition, sda3, is 464G, but the LVs only use about 204G of that storage.  BTW, is a 500G SSD.
The /boot/ (ext2) and /boot/efi/ (fat32) partitions are external to the LUKS "container."  Part of the boot stages contained inside the /boot/initrd file understands how to deal with LUKS encryption and LVM PV, VG, and LVs.   Unrapping the different logical containers from the outside in has to be handled.

  The PV setting in my notes is purely for convenience to save a little typing.  I’m lazy.  Use it or don't. Completely up to you.

My LUKS notes above steps are only for LUKS, not encryptfs or encfs. Sorry.  To access those HOME directory encryption methods, someone else will need to help.

---

### Post by EuclideanCoffee on 2020-03-15
You should be able to mount the drive on your root partition. I thought in your original post you mentioned you had done this already.

As an example the desktop comes with a file explorer called nautilus that gives you the ability to mount drives and decrypt them.

---

