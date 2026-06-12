---
title: "EXT3-fs errors from External Harddrive"
date: 2011-03-29
forum: Server Platforms
---

### Post by chrislynch8 on 2011-03-29
HI,

I have External Harddrives that I use for backing up onto at night. A couple of them all the same Make,Model, Storage are starting to cause issues. Some morning when I come in and go to check the backups the following message is on the screen over and over again.

**EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset0**

Then when I log into the server and try to umount the device I receive the following error before it umounts.

**EXT3-fs error (device sdb1): ext3_put_super: Couldn't clean up the Journal**

Is this an indication that the Harddrive are failing, they are not that old - I'd be susprised if there where 1 year old.

This happened before and I ran the **sudo e2fsck -y /dev/sdb1** and backup worked away for a while then I get this above issues again. 

Is there something I can do or is it a case of getting new Drives?

Rgds
Chris

---

### Post by Vegan on 2011-03-29
It looks like only 1 of the disks is a problem.

download smartmontools

and use it to run tests on the disk to be sure its OK

[http://www.windows-it.tk/papers/disk-reliability.php](http://www.windows-it.tk/papers/disk-reliability.php)

---

### Post by chrislynch8 on 2011-03-30
Its a couple of disks , I only have one mounted at a time but IU get the above errors for multiple disks


I will try the link.

Rgds
Chris

---

