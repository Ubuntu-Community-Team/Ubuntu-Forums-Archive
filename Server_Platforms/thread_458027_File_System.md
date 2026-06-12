---
title: "File System"
date: 2007-05-29
forum: Server Platforms
---

### Post by twinax on 2007-05-29
Hello,

I have two sata drives for data, they have been partitioned and raid 1(md0) added (the OS is on another drive).  Couple questions:
Which file system?  (code?)
Do I need to edit the /etc/fstab to auto mount? Code?
Thanks

---

### Post by kalisto on 2007-05-31
From: [http://wiki.debianhelp.org/pmwiki.php/DebianHelpPages/RaidWithMdadm]("http://wiki.debianhelp.org/pmwiki.php/DebianHelpPages/RaidWithMdadm")

Make the Array

I used the mdadm tool to make the array. It's command line and doesn't require a config file. You can get it as a debian package like so:

   1. apt-get install mdadm 

You'll also need a multi-disk device created in your /dev file system.

These can probably be created with mknod, but I don't know how to do it since my system came with ten of them: /dev/md0 ... /dev/md10

Here's how I created my array with mdadm:

   1. mdadm --create /dev/md0 -level LINEAR -raid-disks=2 /dev/hda3 /dev/hdc1 

And that's it. mdadm should give you a nice message if the array was created properly. The --level option tells what type of array you want to build. It looks like all you need to do to create different types of arrays is make sure that the type is compiled into the kernel, and change this option.

You can check out the status of your array with

   1. cat /proc/mdstat 

Format the Array

The array needs a file system. Now I can treat /dev/md0 as an unitialized disk.

   1. mkfs -t ext2 /dev/md0 

This puts a fresh ext2 filesystem on the array.
Mount the Array

Now it should be mountable. I created a mountpoint, /usr/backup, for my array:

   1. mount /dev/md0 /usr/backup 

Now I'm in business!
Make Array Mount at Boot with /etc/fstab

Now the array is working, but I want it to be mounted the next time the system has to boot. I do this by editing /etc/fstab. This is where changing the partion types pays off.

In /etc/fstab, I add the line

/dev/md0 /usr/backup ext2 rw,user 0 0

to the bottom.

First, you give the device you want to mount, then the mountpoint, then the file system type.

After that, there are some mounting options, which I'm not totally clear about. The rw option, sets it to both read and write, and user sets it for data storage and not much else. You will undoubtedly want to set different options on your arrays.

The first 0 has to do with the dump command, and I'm not familiar with that. The second 0 tells the order to run fsck on the file system at boot up. If you put a 0 here, fsck won't be run on that file system.

Now, I reboot, run

   1. cat /proc/mdstat 

to see if the array is still running, and run

   1. mount 

to see if the array is still mounted where I want it. 

good luck ;D

---

