---
title: "Dissapointment...."
date: 2008-08-11
forum: The Cafe
---

### Post by Cariboo1938 on 2008-08-11
Hello all,
I don't know in what category to put my issue...so I start here, hoping somebody will lead me in the right direction.
I run Ubuntu 8.04-amd64 and I want to use 'Remastersys' for backup and liveCD purposes. Unfortunately remastersys runs into a problem, 
giving me the message:> -----------------------------------------------
Command-line options = dist
------------------------------------------------------
File /home/remastersys/remastersys/ISOTMP/casper/filesystem.squashfs is larger than 4GiB-1.
-allow-limited-size was not specified. There is no way do represent this file size. Aborting. I contacted the developer, Fragadelic, [HERE]("http://loscompanion.com/forums/index.php?topic=4586.msg66956#msg66956") and there he expresses his disappointment, that obviously nobody in the Ubuntu community wants to talk to him about the issue. He says:> I'd love to get the chance to talk one-on-one with the casper and ubiquity devs about it.  I believe it would be mutually beneficial.  Ubuntu would have an official backup solution and I'd be able to get the info upfront without having to always dig for it in the scripts.
I cannot agree more and maybe some other people are interested to use remastersys too and help me to direct the issue to the right place...
Thanks
Cariboo

---

### Post by Cariboo1938 on 2008-08-11
Hello 
I wonder, is this the wrong place to discuss the issue:confused:

---

### Post by DouglasAWh on 2008-08-12
maybe the official mailing list rather than the forum?  My understanding is the forum isn't officially tied to ubuntu.

---

### Post by Cariboo1938 on 2008-08-12
> **DouglasAWh said:**
> maybe the official mailing list rather than the forum?  My understanding is the forum isn't officially tied to ubuntu.
Thanks DouglasAWh,
please, can you give me more info how to get the 'official mailing list'
Thanks

---

### Post by Cariboo1938 on 2008-08-15
Hi all,
can somebody help me, please, to bring this issue 

Quote (see also [HERE]("http://loscompanion.com/forums/index.php?topic=4586.15")):
I'd love to get the chance to talk one-on-one with the casper and ubiquity devs about it. I believe it would be mutually beneficial. Ubuntu would have an official backup solution and I'd be able to get the info upfront without having to always dig for it in the scripts.  
EndQuote 

to the casper/ubiquity developers attention?
Thanks

---

### Post by Cariboo1938 on 2008-08-15
:guitar:I wonder....How can I keep this thread alive....:popcorn:

---

### Post by Bachstelze on 2008-08-15
The ubuntu-devel-discuss mailing-list seems to be the right place to talk about this.

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by LeoSolaris on 2008-08-15
This would be a nice addition to Ubuntu's repertoire. I hope the Dev's listen!

---

### Post by chris4585 on 2008-08-16
> **Cariboo1938 said:**
> Hello all,
I don't know in what category to put my issue...so I start here, hoping somebody will lead me in the right direction.
I run Ubuntu 8.04-amd64 and I want to use 'Remastersys' for backup and liveCD purposes. Unfortunately remastersys runs into a problem, 
giving me the message: I contacted the developer, Fragadelic, [HERE]("http://loscompanion.com/forums/index.php?topic=4586.msg66956#msg66956") and there he expresses his disappointment, that obviously nobody in the Ubuntu community wants to talk to him about the issue. He says:
I cannot agree more and maybe some other people are interested to use remastersys too and help me to direct the issue to the right place...
Thanks
Cariboo

I've made a few livecds, and it seems that the problem is that when trying to squashfs your filesystem (compress your filesystem) its larger then 4GB, a regular ubuntu installation (default) would squash to about 690mbs.  Try moving some personal files to a external drive.  This is just a theory, you might be able to talk to capink in this thread: [http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")

---

### Post by Cariboo1938 on 2008-08-17
> **chris4585 said:**
> I've made a few livecds, and it seems that the problem is that when trying to squashfs your filesystem (compress your filesystem) its larger then 4GB, a regular ubuntu installation (default) would squash to about 690mbs.  Try moving some personal files to a external drive.  This is just a theory, you might be able to talk to capink in this thread: [http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")
Thanks for the reply...
Did you make live CDs from Ubuntu -amd64?
From the developer of remastersys I quote his opinion on that issue:> I need to take a look at 8.04 amd64 version as it appears some changes may have been made to casper there.  Mint uses normal x86 and this may be the difference and the key to your issue.
BTW "http://ubuntuforums.org/showthread.php?t=688872" is far beyond my capabilities:(

---

### Post by LaRoza on 2008-08-17
> **DouglasAWh said:**
> maybe the official mailing list rather than the forum?  My understanding is the forum isn't officially tied to ubuntu.

This is the official Ubuntu forum (servers and licenses owned by Canonical) but it isn't the best way to contact developers.

---

### Post by Cariboo1938 on 2008-08-17
> **LaRoza said:**
> This is the official Ubuntu forum (servers and licenses owned by Canonical) but it isn't the best way to contact developers.

@LaRoza:
Thanks...
What would you recommend to do?

---

### Post by chris4585 on 2008-08-17
> **Cariboo1938 said:**
> Thanks for the reply...
Did you make live CDs from Ubuntu -amd64?
From the developer of remastersys I quote his opinion on that issue:
BTW "http://ubuntuforums.org/showthread.php?t=688872" is far beyond my capabilities:(

I'm using Ubuntu 32bit version, the thread i pointed to you more than likely would be able to help, the script remastersys and the howto i showed you are nearly the same, remastersys is just automated, this is probably your best option, hope it works!

---

### Post by Cariboo1938 on 2008-08-17
> **chris4585 said:**
> I'm using Ubuntu 32bit version, .......this is probably your best option, hope it works!
I moved all my /home files and I choose the option "dist" which also eliminates the personal data but it didn't help. There must be something different for the 64bit version! Thanks anyway. I try to bring the Ubuntu developers and Fragadelic, the developer of remastersys, together!

---

### Post by DouglasAWh on 2008-08-19
> **LaRoza said:**
> This is the official Ubuntu forum (servers and licenses owned by Canonical) but it isn't the best way to contact developers.

So the info in this thread is old or incorrect?  [http://ubuntuforums.org/showthread.php?t=176622](http://ubuntuforums.org/showthread.php?t=176622)

It says 

> Ubuntuforums is not being run by canonical. It was started by ubuntu-geek using his own money.

---

### Post by Cariboo1938 on 2008-09-01
I still have to struggle with the backup issue of my Ubuntu 8.04-amd64 installation.
It seems to me that Remastersys is a very useful script but I'm not expert enough to figure out why it's not working. 
I was told it must have something to do with "casper".:confused:

---

### Post by Fragadelic on 2008-10-06
The issue has to do with the iso9660 file size limit of 4 Gig and isn't an issue with casper or ubiquity or even genisoimage.

When too much data is backup up, the filesystem.squashfs file grows beyond the 4 Gig limit and the iso file cannot be created.  Only fix is to reduce the amount of data you are including.

I've already explained this on my forum but just thought I'd put some info here in case anyone was wondering the outcome of this.

---

