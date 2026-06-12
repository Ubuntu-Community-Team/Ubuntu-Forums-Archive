---
title: "My Windows2003 Server install exaperience"
date: 2008-01-25
forum: The Cafe
---

### Post by PryGuy on 2008-01-25
Hey people! I'm going to tell you about my Windows2003 Server installation experience. Yes, I know, there's a lot of posts about the fact how bad/good Windows is but this is the first case in my practice that shown me the true unfrendliness of the Microsoft products. 

I'm an (Ubuntu) Linux IT engineer, working for a small company. We've got a tricky server and we had to install Windows2003 Server on it. Yes, people, it's legal if you care. Finally it lay on my shoulders of course.;) The problem was it has an Adaptec SCSI RAID controller and three 10000 RPM SCSI drives (two are mirorred). Another problem was that the company server belonged to lost the driver CDs that shipped with the server, It happens quite frequently, So I finally found the Adaptec driver and... well, I had to press F6 and insert a *diskette* with the driver on when it's needed. I've seen U1 server cases that do not have a room for a floppy drive, so using a diskette is generally a strange move.

Was it the system's fault or not but I noticed it, the system refused to see the diskette if you booted with it inserted, so you had to boot without a diskette. But the real bug was when I booted, pressed F6, inserted a diskette on a request, got my drivers loaded, agreed with a user agreement and partitioned a disk Windows installer asked me for the driver diskette again (yes, it was still in) saying the inserted disk is probably wrong or broken (do not remember the exact phrase). The only solution for me was to make an unattended install CD with the driver integrated. 

BTW, Ubuntu LiveCD booted fine and recognized the SCSI controller hands down. ;)

---

### Post by HermanAB on 2008-01-25
Well, Windows 2003 is 5 years old already.  For a system that old, it is pretty damn good actually.  Let's see if you can install Ubuntu from 5 years ago on that machine...

Cheers,

Herman

---

### Post by PryGuy on 2008-01-25
Forgot to say it was Windows 2003 Server *RC2*.

---

### Post by HermanAB on 2008-01-25
Cool - I use whatever gets the job done and oftentimes that includes some sort of Windoze, but I usually run it inside a VM - much less trouble that way.

Cheers,

H.

---

### Post by sulusulu on 2008-01-25
> **HermanAB said:**
> Well, Windows 2003 is 5 years old already.  For a system that old, it is pretty damn good actually.  Let's see if you can install Ubuntu from 5 years ago on that machine...

Cheers,

Herman

I think that the problem here wasn't that Windows didn't already have a driver for the SCSI adapter but that it had a problem with the floppy. I can understand that Microsoft can't put every driver on their installation disk but there is no excuse for not being able to accept a driver that is on CD even if they had to cache it in memory.

---

### Post by KThrace on 2008-01-25
Win 2003 is actually pretty decent for a server OS. Funny how Vista's supposedly built off its codebase.

---

