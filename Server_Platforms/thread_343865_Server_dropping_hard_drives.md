---
title: "Server dropping hard drives"
date: 2007-01-22
forum: Server Platforms
---

### Post by Crummy_Gummy on 2007-01-22
Hi all

I'm running a Tyan server with Seagate hard drives on ubuntu. The server has four SATA drives running in parallel using RAID 1 with mdadm. At the moment we are dropping almost one hard drive a week with SMART errors and bad blocks -> mostly smart errors though. Has anyone here seen something like this before? Is there any possibility that is could be an Ubuntu/kernel issue? The SATA uses a Nvidia chipset.

---

### Post by fnjordy on 2007-01-22
SMART errors are reported from the HDD, so that would indicate serious issues.

MDADM drops disks on reported errors, but you seemed to have already found out where they are coming from.  The next step is to ask Seagate whether the SMART values from those particular models you are using are reliable.

---

### Post by MJN on 2007-01-22
What *exactly *do you mean by SMART errors? (post the output, e.g. a **smartctl -a <device>** if that's what you're using)

Mathew

---

### Post by Crummy_Gummy on 2007-01-23
I wish I knew. I've sent in all those hard drives forgetting about smartctl. If it happens again I'll use it. When I say smart flag set I mean that using seatools the diagnosis was "smart flag set".

---

### Post by MJN on 2007-01-23
Oh, okay.
 
You really need to see the severity of the SMART errors - the SMART protocol is extremely comprehensive (perhaps often too much so!) hence you can't necessarilly determine a drive is about to fail (or already has done) on just *any* error. You'd really need to see what it actually was.
 
Don't get me wrong - I'm not ruling out the possibility of you having multiple drive failures as a result of some exterior cause (or sheer bad luck!) but more just trying to warn against jumping to any conclusions as to what the problem might be.
 
Give SmartCTL a go on your replacement drives - indeed I'd recommend running the Smartmontools daemon constantly so you ought to get a >90% chance of being warned of likely failure within 24 hours of it potentially happening. For a belt and braces approach I would also suggest scheduling regular full drive tests - my drives undergo a short test every morning and extended test at the weekends.
 
Mathew

---

### Post by Crummy_Gummy on 2007-01-23
Thanks I'll do that. Is it possible that SMART errors could be caused by software?

---

### Post by MJN on 2007-01-23
Unlikely given that the SMART attributes are created by the drive itself. Of course, the monitoring software could misinterpret the attributes and falsely imply a failure however I would expect this unlikely using the manufacturer's SMART package.
 
SMART, like many so-called 'standards', is implemented slightly differently by different vendors hence why some 3rd party SMART software might erroneously interpret the results. However, as mentioned I would not expect this with the vendor's own toolset.
 
Mathew

---

### Post by Crummy_Gummy on 2007-01-24
Thanks for the input :)

---

