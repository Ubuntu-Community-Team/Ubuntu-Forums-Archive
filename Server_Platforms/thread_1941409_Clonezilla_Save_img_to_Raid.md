---
title: "Clonezilla Save img to Raid"
date: 2012-03-15
forum: Server Platforms
---

### Post by ptmuldoon on 2012-03-15
I followed this post here to install Clonezilla onto headless Ubuntu Server with no GUI

[http://ubuntuforums.org/showthread.php?t=1216081](http://ubuntuforums.org/showthread.php?t=1216081)

But when I run clonezilla, and follow the prompts to save to disk, clonezilla lists each disk in my Raid5 - 4 1TB array, and does not show me md0 to save the iso too.

For background.  I have my OS installed on a 4GB compact flash card, with the Raid array as separate drives.   I think I should be able to save to that location?  

Any help is appreciated.

Thanks
PT

---

### Post by trundlenut on 2012-03-15
I presume you are running clonezilla from a live cd, in which case it either doesn't have mdadm included on the live cd or it isn't running so clonezilla doesn't understand your software raid setup.

IIRC the more recent versions of clonezilla are based on debian/ubuntu so you should be able to either install mdadm or role your own live cd incorporating it.

Once you have it on the live cd you need to run mdadm to recognise the raid array and then mount it to allow you to save your image onto the array.

---

### Post by ptmuldoon on 2012-03-15
Well, I'm not running the live CD so that could be part of the problem.  But fro the link posted earlier, there's a way to actually install clonezilla on to your system and run it from there.   I'm trying to experiment with a way of backing up my Ubuntu server OS without having to shut it down.  I tried remastersys, but does not seem to work the best without a GUI installed.

Clonezilla appears to run fine, and I am shown options to mount to a local disk, samba server or ssh server.  Now as Ubuntu server also has both samba and ssh running, I'm trying to back up that way as well, but haven't gotten the parameters correct yet.

---

### Post by trundlenut on 2012-03-16
Are you trying to run clonezilla on the machine your trying to create the image of?

Depending how your raid array is mounted, clonezilla may see it as part of the file system and want to back it up hence why it is not offered as an option.

If you want to back up the running machine you may be better off with something like BackupPC.

---

