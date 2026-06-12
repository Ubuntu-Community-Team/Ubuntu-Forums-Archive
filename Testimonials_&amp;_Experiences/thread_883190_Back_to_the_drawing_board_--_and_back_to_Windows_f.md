---
title: "Back to the drawing board -- and back to Windows for a while :("
date: 2008-08-07
forum: Testimonials &amp; Experiences
---

### Post by MountainX on 2008-08-07
I built a new server and installed Ubuntu 8.4.1 amd64. It is meant to replace an older file server running Windows 2003. I spent several weeks (spare time) setting up the new server and I put it online (apparently after too little testing). Very soon, the performance problems became so apparent that I went into troubleshooting mode. Not finding a solution, I had to go back to the Windows file server. I want my Ubuntu! :)

Main problem:
Very slow disk performance (from hardware that should perform well).

Secondary problem:
Need a backup solution, but I'll deal with that after I fix all the problems.

I have seen these errors in the log:

[ 3642.345984] gvfsd-smb[8256] general protection rip:7ff3f099e2fc rsp:423ef5b0 error:0

and a multitude of these on the (hardware controller) RAID-0 device:

[104070.269918] EXT3-fs error (device dm-6): ext3_new_block: Allocating block in system zone - blocks from 78249984, length 1

and, this mtrr error (which I think is video card-related, and therefore not of immediate concern:
mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining

I have asked about each issue separately (both here and at another forum). I'm being persistent only because I am determined to move from the Windows file server to Ubuntu.

Actually, now that I write this I realize I posted [almost the exact same plea for help]("http://ubuntuforums.org/showthread.php?t=882088") yesterday.

So, do I post this or not? I'm going to post it because I don't know what else to do.

---

### Post by windependence on 2008-08-08
How is your box partitioned? What size is your swap file, and what file system are you using? Also, how much RAM do you have in this box? I'm hoping you aren't running a GUI but I think I know what the answer is. :)

-Tim

---

### Post by MountainX on 2008-08-08
Thanks for your interest.

I have 6 GB of ECC RAM.

Swap file is 6GB and it is essentially never touched.

File system is Ext3 with only noatime attribute.

I am running a GUI because I have hardware capacity to spare. This whole file server serves only one family, not hundreds of users.

Other details can be found in the attachments to my other post:
[http://ubuntuforums.org/showthread.php?t=882088](http://ubuntuforums.org/showthread.php?t=882088)

or I'll be glad to reply with any other details requested here. I'm motivated to solve this.

---

### Post by dmizer on 2008-08-08
> **MountainX said:**
> Actually, now that I write this I realize I posted [almost the exact same plea for help]("http://ubuntuforums.org/showthread.php?t=882088") yesterday.

So, do I post this or not? I'm going to post it because I don't know what else to do.

Actually, since this would be a double post otherwise, I'm going to keep this thread open, but move it to testimonials.

Edit:
I wish I had enough experience to help you out, but frankly solving your problem will take someone with a great deal more skill than me.

---

