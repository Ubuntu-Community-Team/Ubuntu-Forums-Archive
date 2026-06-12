---
title: "Dealing with storage on KVM"
date: 2016-05-30
forum: Virtualisation
---

### Post by kcallis on 2016-05-30
I have created a logical drive to hold all of my images (which I created a brtfs filesystem), I also created a logical drive for data. I thought that I could create that drive as a block device, but I don't have the slightest idea to have the image make use of the block device. For instance, if I were to create a Windows 7 virtual machine, and I wanted to allocate 40G, how do I tell KVM that I want to create that 50G on my data drive which is a block device? Or would it just be better to just make the logical drive a filesystem. I wanted to play with block devices (since I wanted to also use container on the block device as well), but I don't want to be twiddling my thumbs waiting for a solution when I could just make a file system and call it a day!

Any pointers would be appeciated!

---

### Post by houstonbofh on 2016-05-30
A "block device" is a hard drive.  Not a partition on a hard drive. So, /dev/sda is your block device, not /dev/sda3.  And it is hard to install many systems in a partition without touching the boot block...  My advice is to stick with files unless you have a few spare hard drives.

---

### Post by MAFoElffen on 2016-06-01
As for dealing with storage while using KVM, I do it two different ways. (and when I discuss this, I am talking about the host environment the host server of the KVM Server Service.)

My first KVM host server, I have setup on LVM, that way when I need more storage, I can add on the fly. Of the two, this has the best performance, and the most reliable connection to my images.

My second is indirectly (physically) on LVM, but is not physically located on the same server. It is a managed storage pool (a network share) located elsewhere on my network. Not the best performance (commumications between has a very slight cost, but really not that noticeable), but is lots more flexible, and the most reliability (as related to my disaster recovery plan).

My recommendation, K.I.S.S. Personally, I use what I have experience with. If I'm going to do pools, then I use LVM or ZFS. I had ZFS experience from Solaris ... But native support for ZFS in Ubuntu only came around within the last year.

---

