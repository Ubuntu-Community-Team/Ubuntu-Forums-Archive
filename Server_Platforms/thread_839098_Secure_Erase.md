---
title: "Secure Erase"
date: 2008-06-24
forum: Server Platforms
---

### Post by AlienCollective on 2008-06-24
I have a dedicated server hosted remotely. The server's hosting is about to expire, and as it contains some rather sensitive data, I would like to completely wipe the drive first. The catch is that obviously I don't have physical access to the server, so the format would have to be conducted while the server is running on the partition to be erased.

Is this possible?

(I know about shred/srm from my searches, but I haven't seen my question addressed, possibly because it's a pipe dream.)

---

### Post by windependence on 2008-06-24
Well obviously, you can't wipe the OS drive, but you CAN wipe the other partitions and there are tools to do this. If the data was really sensitive, I would recommend no less than 4 passes overwriting the data. I would think you could get a pretty good job done by using dd to overwrite the partition with zeros. 

[http://howto.wikia.com/wiki/Howto_wipe_a_hard_drive_clean_in_Linux](http://howto.wikia.com/wiki/Howto_wipe_a_hard_drive_clean_in_Linux)

Be careful though, we affectionately call dd "disk destroyer" because if you don't get the parameters correct, you can do some damage. Of course, in this case, that is the intent. :)

-Tim

---

### Post by AlienCollective on 2008-06-24
Well, that's the problem. I've only got the one partition, and I have no means of booting to anything but. I guess I'll content myself with deleting my home folder, all backups, and the MySQL database. I just have to figure out where MySQL keeps the thing, which I ought to be able to discover with a couple of minutes on Google. I'm going to bed now, though, so I'll find out tomorrow and if somebody beats me to it, so much the better. ;)

My host has a system that lets you install OSes (including a couple of versions of Ubuntu) from ghosted images they've set up with no intervention on their part. Once I've got the most sensitive stuff dealt with, I'll make a fresh install over top of what's left, disconnect the server, and leave it that way until my host brings it down for good.

By the way, I'm using srm rather than dd. The latter is a [_little too confusing_](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/) for me. :?

---

### Post by windependence on 2008-06-24
Yes, that tutorial you posted is the best dd tutorial ever, but it is geared to someone who has physical access to the box. Please check out the one I posted because you only need one command and it's quite easy. Keep in mind that one overwrite is not enough to make the data irretrievable.

-Tim

---

### Post by AlienCollective on 2008-06-24
Well, srm uses the Gutmann method by default (or something approximating it) so it's definitely not *one* overwrite.

Anyway, as you say, the link you provided is designed to be read by someone with physical access to the box. For those that do not, and don't have another partition to boot to, it really doesn't apply. From what I can see, none of the commands would work on the boot disk, which is what I'm trying to do.

The lion and the tiger battled, each consuming the other, until there was nothing left of either one.

---

### Post by gtdaqua on 2008-06-24
[DBAN]("http://dban.sourceforge.net/") is open-source and can run standards-based formats - DoD, Guttman, RCMP or even a Quick Erase. But you need physical access to the machine. CD and Floppy images are available.

---

### Post by cdenley on 2008-06-24
If you can't erase the entire drive, you should still be able to erase sensitive data. You can srm or shred any sensitive files, and if you're worried about files that have already been deleted, use sfill.

---

### Post by hyper_ch on 2008-06-24
I'd

(1) create a seperate boot
(2) create an own initrd into which I can ssh and which has DD in it (or some other tool
(3) reboot with that initrd
(4) login by ssh
(5) unmount (if necessary) the other partition
(6) dd (or whatever tool) the other partition

---

### Post by AlienCollective on 2008-06-24
> **gtdaqua said:**
> [DBAN]("http://dban.sourceforge.net/") is open-source and can run standards-based formats - DoD, Guttman, RCMP or even a Quick Erase. **But you need physical access to the machine.** CD and Floppy images are available.

Doesn't help, then.

> **cdenley said:**
> If you can't erase the entire drive, you should still be able to erase sensitive data. You can srm or shred any sensitive files, and if you're worried about files that have already been deleted, use sfill.

Yeah, srm seems to be getting the job done. Thanks for the suggestion about sfill; I'll be sure to use that.

> **hyper_ch said:**
> I'd

**(1) create a seperate boot**
(2) create an own initrd into which I can ssh and which has DD in it (or some other tool
(3) reboot with that initrd
(4) login by ssh
(5) unmount (if necessary) the other partition
(6) dd (or whatever tool) the other partition

Also not an option, unless this is something you can do on the boot drive.

---

### Post by hyper_ch on 2008-06-24
> **AlienCollective said:**
> Also not an option, unless this is something you can do on the boot drive.

Yes, you can ;)

Have a look at this:  [http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)

It's not exactely what you need BUT it shows you how to create an initrd on your own, it shows you how to start it (there's also a grub option that will only boot for the next reboot into a specific initrd) and it shows you how to add programs (like dd) to it.

All you need to do is to skip that crypto part of it and add "dd"

---

### Post by AlienCollective on 2008-06-24
Cool! I'll be sure to give that a go when I get home.

*Okay, your tutorial isn't making any sense to me. :oops: Could you be a little more specific? Can I really delete everything on the drive (old partition) just using that? Wouldn't you have to install at least a bare-bones bootable partition?*

---

### Post by hyper_ch on 2008-06-24
well, you do have to have a bootable partition /boot... except from that you can then completely wipe the rest of the harddisk... so it's about max. 100mb that you cannot completely wipe...

---

### Post by AlienCollective on 2008-06-24
But I can repartition the drive/install on the new partition while booted from the same drive and running the server via ssh?

(Sorry if I'm coming across as a little slow here.)

---

### Post by hyper_ch on 2008-06-24
do you have a swap partition?

---

### Post by AlienCollective on 2008-06-24
Nope.

---

### Post by hyper_ch on 2008-06-24
are you sure?

post the output of
```

sudo fdisk -l

```

---

### Post by HermanAB on 2008-06-24
All modern disk drives have a self erase function built in.  I believe that you can activate it with 'hdparm'.  All you need to do is activate it, then reboot the machine and it will self destruct.  Unfortunately these features are not well documented, but some Googling and man page reading may be enlightening.

---

### Post by cdenley on 2008-06-24
I used that once. If I remember correctly, hdparm didn't finish running until the erase function finished. I'm not sure what would happen if you run it on a disk with a mounted filesystem and a running OS (don't really want to try).

---

### Post by AlienCollective on 2008-06-26
Okay, this still isn't making much sense to me and the hosting expires tomorrow, so I'm just going to content myself with using srm, blanking free space, then using my host's format function. It's not "secure", but it'll have to do in a pinch.

Thank you all for your input.

---

### Post by Metal Slug on 2010-04-12
But isn't there some program that only sweeps the free space of the HD? I.e. you delete the regular way first, then sweep.

---

