---
title: "srm hardlinked files"
date: 2009-01-01
forum: Security
---

### Post by NeoDevin on 2009-01-01
I'm having a little trouble with the secure-delete package (and I'm new to linux/ubuntu).  I have an external USB hard drive (formatted NTFS), and am trying to use srm to securely delete some files off of it.

Problem is, for many of the files, it gives me the error message:

Error: File Social01-pic2.JPG - file is hardlinked 1 time(s), skipping!

How do I go about making this work?  Am I better off to just use shred (which does seem to work properly)?

Thanks,
Devin

---

### Post by Tubes6al4v on 2009-01-01
If shred is working, I'd just use that. Someone here may be able to give a more definitive answer, or perhaps know how to overwrite the newly freed space with random data to secure the deletion.

---

### Post by memoria on 2010-07-07
I am also trying to figure out secure-delete tools.

I used this command

srm -r "/media/DRV4_VOL1/danny/R"

and I as well was told "file is hardlinked 1 time(s), skipping!" for every file in that folder. 

I too am a newbie and dont even know what hardlinked files are or how to change them. 

Any suggestions would be appreciated.

---

### Post by Lemo85 on 2010-11-04
I've had the same issues with srm and trying to securely clean work hard drives.

What I usually do is run srm as sudo and sometimes run it a few times (even after it completes the first time). Then if there are still files that wont srm I do a normal delete (send them to the trash), show hidden files and then srm the trash folder on the drive.

I don't know how secure this is, but it's currently working for me.

I'd be keen to hear anyone else's thoughts.

---

