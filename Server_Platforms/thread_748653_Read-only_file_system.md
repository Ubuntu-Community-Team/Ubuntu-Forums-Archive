---
title: "Read-only file system"
date: 2008-04-07
forum: Server Platforms
---

### Post by stevejacobsen on 2008-04-07
My file system says it's read only. I've rebooted a couple of times. I'm currently trying to run fsck in rescue mode but it says the drive is mounted. I've tried umount and umount -f  but it still gives me the warning that it's mounted. What should I do?

/steve

---

### Post by ajgreeny on 2008-04-07
You can't unmount the file system you are using.  To do a forced fsck on the file system of your ubuntu install, use the live disk or before you shutdown or restart the system use ```
sudo touch /forcefsck
```Next boot it will do the fsck that it normally does every 30th boot, at least I think it is 30 by default, though you can change that with **tune2fs.**

---

### Post by stevejacobsen on 2008-04-07
I can't touch the file because it's read only. And I'm not sure about the live CD. I installed using the text based server install. I found the rescue part of it but nothing for fsck. Do I need to download a different CD?

/steve

---

### Post by stevejacobsen on 2008-04-07
Okay, I got the live CD thing figured out and ran:

sudo fsck /dev/sda1
sudo fsck /dev/sdb1

The both came back clean.

I did notice that during the boot there's an error message that says:

'sysfs' is not supported. skipping mount.

I googled that and did find much. any ideas?

---

### Post by stevejacobsen on 2008-04-08
Anyone got anything on this? I've got several web sites down that I'd rather not rebuild on a new server. I've got the live disk running and getting ready to copy the data off but would much prefer finding a fix.

/steve

---

### Post by koenn on 2008-04-08
the easies way to run fsck on your / partition is by having it fsck'ed during startup, you do that by giving the  -F option with shutdown, something like
```
sudo shutdown -F -r now
```

for your sysfs problem : possibly you have something in /etc/fstab that tells the system to mount a filesystem of type 'sysfs'. do
```
cat /etc/fstab
``` to have a look (& post the output)

sysfs is apparently used to represent kernel memory - drivers mostly, so it shouldn't be used on hard disks. if you have it on a partition (re fstab) thats most likely wrong. 
If your operating system somehow is told to do something with sysfs (other than mounting a partition) and then finds out it doesn't support it, you probably messed something up big time and it would be good to give that info if you want help fixing it. 

On the other hand, I don't see how this relates to your fs coming up readonly, so in any case try that reboot with fsck first

---

### Post by stevejacobsen on 2008-04-08
The last things I had done before it broke was to fix a problem with sendmail. It was complaining about not having a FQDN and then I was getting emails about some crontabs that were not working (generating sitemaps etc.) I fixed those and there was one crontab I hadn't got to look at yet. It was doing something with cron-msp and sendmail if I remember right

I tried the cat command but got a segmentation fault so here is a print screen of the fstab.

Here's something I found tonight. If I log in using a regular user all I get is:

-bash: /dev/null: Permission denied. 

I did a ls -l on /dev and most of the folders have this:

crw-rw----

/steve

---

