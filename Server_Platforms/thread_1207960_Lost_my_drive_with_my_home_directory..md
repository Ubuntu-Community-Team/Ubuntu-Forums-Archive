---
title: "Lost my drive with my home directory."
date: 2009-07-08
forum: Server Platforms
---

### Post by irv on 2009-07-08
I did an update this morning on my server, and now it wont boot up. I found the problem to be a faulty hard drive I was using for a home directory. I replaced the hard drive and booted with gparted and setup a partition for my home directory. The problem I ran into was not being able to mount it as /home/username. Is there a command to do this from the shell. The drive that I want to use as my home is sdb. Any help would be great. I would love to get my server back on line as soon as I can.
Thanks
Irv

---

### Post by swerdna on 2009-07-08
> **irv said:**
> I did an update this morning on my server, and now it wont boot up. I found the problem to be a faulty hard drive I was using for a home directory. I replaced the hard drive and booted with gparted and setup a partition for my home directory. The problem I ran into was not being able to mount it as /home/username. Is there a command to do this from the shell. The drive that I want to use as my home is sdb. Any help would be great. I would love to get my server back on line as soon as I can.
Thanks
Irv
You can boot up the install CD and then access/mount sda1. Edit the file /etc/fstab on sda1 and wherever the line for the old home is, replace the address of the partition with sdb1 (eg /dev/sdb1), modify sdb1 to whatever is correct if the new home is not on the first partition of sdb.

If in doubt, type  here the line in fstab for the mount of the old /home.

---

### Post by irv on 2009-07-08
> **swerdna said:**
> You can boot up the install CD and then access/mount sda1. Edit the file /etc/fstab on sda1 and wherever the line for the old home is, replace the address of the partition with sdb1 (eg /dev/sdb1), modify sdb1 to whatever is correct if the new home is not on the first partition of sdb.

If in doubt, type  here the line in fstab for the mount of the old /home.
Ok I did this and here is the fstab file.
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 / was on /dev/sda1 during installation
UUID=2a3defd4-ed77-4cff-bd25-b5a126e134bb /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=[COLOR="Red"]542cf967-62c9-4165-8524-a080612d1e0d[/COLOR] /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=bdcc5204-aa31-42d7-91b3-931de5229275 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[COLOR="Red"]In Red:[/COLOR] I changed the UUID number to the Number of the drive I replaced the old drive that failed with. It still don't boot, it comes up with the error can find /home/username directory. The reason is I do not have the mount point set to /home/ and my username directory does not exist yet.
Even though the fstab home is set, the drive is not setup to mount as home. That's what I need to know how to do. I don't want to have to re-install the whole OS just to setup a new home/user again.

---

### Post by Wim Sturkenboom on 2009-07-09
If you have the root account enabled, login as root and fix the system. The root user's home directory is not in /home and therefore it will work.
If you have not enabled it, you have just proven that it's a **BIG** disadvantage not to have root enabled.

I don't have a Ubuntu box at hand, but you might be able to boot into single user mode (recovery mode) and create the user's home directory.

If that does not work, you might be able to enable the root account on your system from a live CD by editing /etc/passwd/ or /etc/shadow, but I'm not sure how. Some instructions that may work can be found [here](http://www.developertutorials.com/tutorials/linux/lost-linux-root-password-060413/page1.html); read the whole article but below is, what I think, the relevant part
> 
Or just edit /etc/shadow to remove the password field: move to just beyond the first ":" and remove everything up to the next ":". With vi, that would be "/:" to move to the first ":", space bar once, then "d/:" and ENTER. You'll get a warning about changing a read-only file; that's normal. Before you do this, /etc/shadow might look like:

root:$1$8NFmV6tr$rT.INHxDBWn1VvU5gjGzi/:12209:0:99999:7:-1:-1:1074970543
bin:*:12187:0:99999:7:::
daemon:*:12187:0:99999:7:::
adm:*:12187:0:99999:7:::

and after, the first few lines should be:

root::12209:0:99999:7:-1:-1:1074970543
bin:*:12187:0:99999:7:::
daemon:*:12187:0:99999:7:::
adm:*:12187:0:99999:7:::


---

### Post by irv on 2009-07-09
I guess we can put this thread to rest. After trying everything here and much more, I thought it would just be faster and easier to just reinstall Ubuntu, and setup LAMP and restore my backup files. And that is what I am doing this morning. I am 71% done with the install and should have it up and running within an hour or so.
Thanks for all the help I learn something the long way is sometimes the easiest way to fix things.
I know there might be a easy fix for this, but I was not knowledgeable enough to do it. So thanks again for the input. 
Irv

---

### Post by irv on 2009-07-09
There is one area where Ubuntu 9.04 is lagging. The post above was posted about 5 hours ago. I said in the post that I was 71% done with the install and the rest of the install was almost done before I posted the above, but it took about a half hour to do the updates and install LAMP. But the slow down was the file copy. I have all my backup on a 250gig USB HD. I just finished restoring my web files, and I have about an hour to go with my home files. 
The point I wanted to make is the file transfer rate was under a 1MB/sec. It was around 995kb/sec. This is really unacceptable for Ubuntu. I never ran that slow with other distros or even windows. My server does have USB 2.0 on it so it should transfer much faster that 1MB/sec.
I believe there is a bug report on this problem.

---

