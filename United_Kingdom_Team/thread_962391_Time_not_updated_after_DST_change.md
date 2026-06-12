---
title: "Time not updated after DST change"
date: 2008-10-29
forum: United Kingdom Team
---

### Post by Mark224 on 2008-10-29
Hi,

My system time has not changed since we moved from BST to GMT last weekend (i.e. it is now an hour ahead).  What do I have to do to fix this?  I am using Hardy Heron 8.04 LTS.

TIA, Mark.

---

### Post by freesitebuilder on 2008-10-30
System > Admin > time and date brings up the box - you'll need to click "unlock" and enter your password. 

Mine has updated - it had no time zone selected, and was set to manual, so I don't know why it updated! :)

---

### Post by Mark224 on 2008-10-30
I've looked at this.  The timezone is still set to "Europe/London" as I set it when I installed the OS.  I can change the time but surely this will break again when DST starts again next year?

---

### Post by ianhaycox on 2008-10-30
Are you dual booting windows ?

I vaguely remember a problem I had from a while ago that Windows and Linux treated the BIOS clock differently and depending which system booted would mess with the clock somehow and affect the other OS.

This isn't much help, but I changed a config file (/etc/default/rcS I think) to modify the interpretation of the BIOS clock to UTC/GMT and it fixed my problem.

Bizarre and vague I know but it might help point you in the right direction.

---

### Post by Mark224 on 2008-10-31
Thanks.  I'm not dual booting windows, although Ubuntu may think I am since I have two HDDs and one used to have windows on it.  I have used gparted to put an ext3 filesystem on it.

I know that windows expects the BIOS to store localtime and Linux expects UTC.

I will have a look at that file and see if I can figure it out.

---

