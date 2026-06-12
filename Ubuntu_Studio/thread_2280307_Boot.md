---
title: "Boot"
date: 2015-05-29
forum: Ubuntu Studio
---

### Post by Miykel on 2015-05-29
Hi; Just lately, when I boot I get a strange screen with the rotating icon for studio and at the bottom  "s for skip or M for manual mount" or words to that effect, has anyone else experienced this and how do I get rid of it
Many Thanks M

---

### Post by sudodus on 2015-05-29
I think your system has found a problem with the file system in your root partition (or maybe home partition if it is separate). It is trying to fix the errors with ***e2fsck*** running automatically under the hood. "S for skip or M for manual mount" means that you can interrupt the checking and fixing process. You should start it when you need not use the computer, and let the checking and fixing process scan the whole file system and finish. I can take hours if the drive is big and/or there are many file system errors. If successful, the strange look should disappear.

If not successful, you can try to fix it manually in a more advanced way. If still no luck, maybe it is time to suspect problems with the hardware. You can start looking at the S.M.A.R.T. information of the hard disk drive.

---

### Post by Miykel on 2015-05-29
Thank you sudodus for your help, I'll let it run later when I don't need the pc and see what happens, this all started when i installed 15.04 on another partition but stupidly moved the mbr to a different partition and all went to hell after that, finally got grub fixed but now this problem, will see how I go

---

