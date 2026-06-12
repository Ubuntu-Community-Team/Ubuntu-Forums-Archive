---
title: "dd_rescue nightmare --- help please"
date: 2008-09-06
forum: Security
---

### Post by trevorhughdavis on 2008-09-06
Okay, I was using dd_rescue to recover a partition from damaged disc ('/dev/sda2').  It was approximately 50 GB

I setup dd_rescue to write to /dev/sdb1 

**dd_rescue /dev/sda2 /dev/sdb1**

Problem was, /dev/sdb1 had all sorts of important stuff on it.  (it's a FAT partition)



I intended to write to /dev/sdb2!  

**dd_rescue /dev/sda2 /dev/sdb1**

I let the damn thing run for almost half an hour before I discovered it. 

I need to recover as much as possible -  the filenames if at all possible.....

argh

---

### Post by niteshifter on 2008-09-06
Hi,

Google up Testdisk / PhotoRec. But after an hour run of dd_rescue for certain sure the FAT table(s) are overwritten - data that was at the root of the FAT filesystem is gone. Testdisk / PhotoRec may retreive some files / folders from the "end" of the disk - worth a try.

---

### Post by hyper_ch on 2008-09-06
DD will write sector for sector... I think you'll have bad luck... if the data is valuable you might want to contact a specialized lab for that.

---

### Post by dannyboy1121 on 2008-09-06
I guess there were no tape backups to restore the data from? I feel really sorry for you dude .. I know I've made similar mistakes in the past.

---

