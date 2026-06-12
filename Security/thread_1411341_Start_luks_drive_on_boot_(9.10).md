---
title: "Start luks drive on boot (9.10)"
date: 2010-02-19
forum: Security
---

### Post by ztripez on 2010-02-19
I'm trying to add a crypted drive to my system (/dev/sdb1)

I've created the Luks header with:
```
sudo cryptsetup --verify-passphrase luksFormat /dev/sdb1 -c aes -s 256 -h sha256

```

And added it to my crypttab:

```
sdb1_crypted UUID=c10aa478-756b-4035-b433-cba491e166aa	none luks
```

I've also added the modules to /etc/modules
```
dm-crypt
aes-i586
dm-crypt
dm-mod
sha256_generic

```

I can open the drive manualy with cryptsetup luksOpen..

[COLOR="Red"]but,[/COLOR]
when I restart the computer the crypted drive doesn't open.
The only error message I've seen is just after i typed "sudo reboot", gnome dies and the bootlog blinks for 1 second.
It says something about that /dev/sdb1 isn't a luks-drive.

I can't find the error in either dmesg or syslog :|

I think I'm getting crasy, I've read every forum-bloggpost-email list about luks on ubuntu for serveal days, nothing.

So please help me before I throw the computer and it's drive out of the window (I live on the 4th floor), retrain myself to become a blacksmith in northern Scandinavia, and never ever touch a computer again.

I'm using Ubuntu 9.10 x64

---

### Post by tucemiux on 2010-02-20
I attempted the fix below and it did not work.  Using UUID with an encrypted partition makes ubuntustudio hang while attempting to load the hard drive while booting.  It looks like what needs to be used in the named in /dev/mapper.  So basically if you attempt to use UUID in your /etc/fstab file your machine will not boot up.  I had to boot up my machine to my USB thumb drive and edit my fstab.  Luckily my "/" directory is not encrypted.
______________________________________________________________________________________

It looks like we both have the same problem.

You are using the hard drive's UUID to add it to your crypttab.

The last step you havent done is the step that lets you mount the drive on boot.  You have to add a line into your "/etc/fstab" file.  This is how youre supposed to add the line into your "fstab" file according to [http://www.debian-administration.org/articles/469](http://www.debian-administration.org/articles/469)

/dev/mapper/[nameUsed_in_crypttab] /mnt/[mount_point_in_HD] ext3 defaults 0 2

nameUsed_in_crypttab: it's supposed the name you added in crypttab, since you used UUID I suppose you have to use something else.

mount_point_in_HD:  in ubuntu we dont really use "/mnt", we create a folder in "/media" then we chown the folder to ourselves.

 -->sudo mkdir /media/mount_point_for_hd
-->sudo chown username:username /media/mount_point_for_hd

Last step would be to update ramdisk:  
   sudo update-initramfs -u -k all

I dont know if it'll work or not.  When adding a hard drive to your "fstab" file using UUID this is the way youre supposed to do it:

UUID=[the_uid_of_the_hd] /media/[mount_folder] ext3 relatime 0 2

I'm going to try it and post my results

---

