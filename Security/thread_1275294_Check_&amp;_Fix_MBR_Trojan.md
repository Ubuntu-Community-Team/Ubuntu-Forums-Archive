---
title: "Check &amp; Fix MBR Trojan?"
date: 2009-09-25
forum: Security
---

### Post by sandman3838 on 2009-09-25
Hello
I have a dual boot system with XP & Linux Ubuntu both on there own HD.

I just got done getting rid of one hell of a Trojan virus form Windows.  So I thought?

From the Windows side I flashed the Bios & Updated it and I reinstalled XP.  All of my important material is off on another HD so there wasn't a loss of too much material.

However, before discovering my "ISSUE", from the Grub menu selecting Winxp for the first time I would receive "NTFL is missing please reboot" which I would and I could proceed into Windows. 

That reboot issue is back.  And, from the Winxp Stand point with all the Malware and Virus checking it's OK for right now?

My question is this could it be starting up again due to Ubuntu?  I have not done and checking there as I thought the issue was in Winxp?  Is there something I can run and Is there something that can check the Linux MBR?

Suggestions Anyone?

Thank you.

---

### Post by bodhi.zazen on 2009-09-25
What makes you think this is a Trojan ?

It is windows being windows

[http://lmgtfy.com/?q=NTFL+is+missing+please+reboot](http://lmgtfy.com/?q=NTFL+is+missing+please+reboot)

which leads to

[http://support.microsoft.com/kb/153973](http://support.microsoft.com/kb/153973)

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)

I would also encourage you to seek assistance for windows problems on a windows forum.

---

### Post by sandman3838 on 2009-09-25
Ok!
But sorry, Winxp is fine now my issue is with the GRUB Menu.

Try this.
Does Linux have an MBR or something like it?

Can the MBR or it's Ubuntu equivalent be checked and or reinstalled without too much damage?

Is there a way to check for Trojans in Linux/Ubuntu?

Thank you.

---

### Post by bodhi.zazen on 2009-09-25
Ubuntu uses GRUB. There are no known Trojans for Gurb.

Ubuntu is not Windows and not every problem in Windows is a virus or Trojan.

I have not idea what your problem is as you are assuming you have a Trojan and have not provided sufficient technical information or a description of your problem.

So ...

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
> A **master boot record** (**MBR**), or **partition sector**, is the 512-[byte]("http://en.wikipedia.org/wiki/Byte") [boot sector]("http://en.wikipedia.org/wiki/Boot_sector") that is the first [sector]("http://en.wikipedia.org/wiki/Disk_sector") ("[LBA]("http://en.wikipedia.org/wiki/Logical_block_addressing") Sector 0") of a [partitioned]("http://en.wikipedia.org/wiki/Disk_partitioning") [data storage device]("http://en.wikipedia.org/wiki/Data_storage_device") such as a [hard disk]("http://en.wikipedia.org/wiki/Hard_disk").

This is a hard drive thing and not an Operating system thing.

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

Grub is used to boot yoru computer and the first stage is in the MBR.

To configure GRUB see :

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

If you have a more specific question or would care to giv emore details perhapsy we could be of further assistance.

---

### Post by sandman3838 on 2010-01-02
I used another Trojan scanner in windows and it found the issue.  It's been working fine.

---

### Post by bodhi.zazen on 2010-01-03
> **sandman3838 said:**
> I used another Trojan scanner in windows and it found the issue.  It's been working fine.

May I ask, what did you find ? Was it a problem with the BIOS, Grub, or the Windows boot files ?

---

### Post by sandman3838 on 2010-01-04
Hello
I remember correctly is was tucked away in one my HD partitions....

1001 apologies!  I can't find my notes on it.

I generally, keep track on my editing as I go when something like happens.

---

