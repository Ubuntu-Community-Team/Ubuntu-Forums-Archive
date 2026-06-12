---
title: "[SOLVED] RAID 1 and RAID 5"
date: 2008-02-24
forum: Server Platforms
---

### Post by CyberDean on 2008-02-24
New to Linux and I am getting ready to build a Ubuntu 6.06 or 7.10 server with two drives as RAID1 and four drives as RAID5.

First question, Ubuntu 6.06 or 7.10 software, which would be the best at this time?

Second, I am going to use the RAID1 partitioned for the OS, SWAP and an area for myself to store files, backups, play around with Linux, etc. etc. etc.  I understand the concept of the directory tree in Linux, but when I add the RAID5 will it require a mount point?  And would this mount point continue the directory tree even though it is on additional drives in a different configuration?

I don't need specifics at this time, still working on concepts.

Thanks.

---

### Post by mrsteveman1 on 2008-02-24
Unless I'm mistaken, the kernel in 6.06 is quite old at this point, and I can't recommend using it for something like this. It's unfortunate that there is even a question as to which version of Ubuntu to use, you should be able to just use the newest version etc, but i know people have had serious problems with 7.10.

I use the x64 version of 7.10-server on my server and have seen no problems at all.

If you install Linux on the RAID-1 array, and then later on create a RAID-5 array, that array will become a new single device on which you can create partitions and filesystems. Those partitions can then be mounted anywhere you want.

I keep my storage array mounted at /storage for instance.

---

### Post by CyberDean on 2008-02-24
Thanks Steve.  Only been into Linux for about 3 weeks, but felt I was on the correct path.  Did not know about the kenal in 6.06 and the problems some have had with 7.10.  I am leaning heavily towards 7.10, especially considering what I have learned lately.

In Linux, is it best to partition large drives or leave it as one?

Thanks again.

---

### Post by mrsteveman1 on 2008-02-24
For a RAID5 array that will be used for long term storage it is probably best to just make one large filesystem on the device.

Unless you have a really good reason to split a drive/device its usually best to just leave it as one partition.

It's not that there is anything wrong with the 6.06 kernel, it's just 2 years old at this point, and there have been massive improvements since then, particularly with drivers for new hardware.

---

### Post by CyberDean on 2008-02-24
Thanks Steve

---

### Post by astrotech226 on 2008-02-24
I didn't see how you were building the raid. Are these hardware or software raids?

They are considerably different as far as architecting them.  With a hardware raid, you are pretty much stuck with each drive being part of a raid.  When you use a software raid, you have to partition the drives first and then create the raid.

Example:  In a hardware raid, you have two drives set up as raid 1.  That's it.  You have exactly one half the capacity of the two drives.

With a software raid, those two drives can have three partitions on each drives.  The first partition being a raid 0, and the other two each having a raid 1.  So as you can see, you can get pretty flexible with the software raid.

---

### Post by CyberDean on 2008-02-25
Hi Mark.  Thanks for your comments, you helped in confirmming what I have learned in the last few weeks, and yes, I will be using software RAIDs.

I did not go into the first set of RAID drives at all due to them not being really part of my questions.  Yes, the first two drives will be partitioned into three partitions for SWAP, ROOT and HOME, RAID0, RAID1 and RAID1 respectfully.

The next four drives will each have one partition all brought together as one RAID5.

Thanks again Mark.

---

### Post by Brazen on 2008-02-25
I'm amazed that there is any question as to what distro to use, too.  Maybe Ubuntu needs to make this information more prominent.  If you want a stable and reliable server, you stick with the LTS releases which would be 6.06.2 at this point.  The other releases are intended to be more experimental and push development of new and interesting features, which does not bode well for a stable production server, but great for other things.

Also, when 8.04 comes out, you will be able to upgrade directly to it, and even though 6.06 is two years old, it still gets security and bugfix updates.

---

### Post by CyberDean on 2008-02-25
What about driver upgrades, for currently supported hardware in 6.06 and new hardware since 6.06 was released?

And Thanks, I appreciate all comments and recommendations,and I am open to change and better ways of doing things.

Dean

---

### Post by astrotech226 on 2008-02-25
> **CyberDean said:**
> What about driver upgrades, for currently supported hardware in 6.06 and new hardware since 6.06 was released?
Dean

I've always used the latest and greatest.  But I also will typically compile my own kernel.  In all the years I've been doing this, I've only been bit once by using a cutting edge OS.  It was Gentoo when it was using a 2.6.18 kernel.  There was some bug in one of the network drivers that plagued me for a period of time.  Once I figured it out and swapped out the kernel for a different one, it was smooth sailing.

I'm relatively new to Ubuntu, but using other distros, I've had near 1,000 day uptimes on many of my servers.  And none of those ran the equivalent of LTS.

---

### Post by CyberDean on 2008-02-25
Hi Mark, Thanks again for your comments.  Nothing on the software side is cut in stone and I don't mind existing on the edge at times if there appears to be success on the other end.  This is not my first server experience, that was back in the late 1980's, but my first Linux and personal server.  Once I decide, put the hardware together and install software, will be when I know for sure what I'm going to do.  When I have my first problem and need assistance, I'll include my hardware and software configurations.  

I THANK everyone for their comments.  Back to the community forums, HowTo's etc. etc. etc.  CLI's don't scare me, I used to program down to microcode and machine language code back in the 1970's and 80's before everyone knew how to spell PC.

---

### Post by Brazen on 2008-02-25
> **CyberDean said:**
> What about driver upgrades, for currently supported hardware in 6.06 and new hardware since 6.06 was released?

And Thanks, I appreciate all comments and recommendations,and I am open to change and better ways of doing things.

Dean

Are you having a driver problem with your hardware on Ubuntu 6.06.2?  If not, then it's not an issue.  If you are, then personally, for a production server, I would replace the hardware or wait for the next LTS release in April, but that is just something you will have to take into consideration.

---

### Post by Brazen on 2008-02-25
> **astrotech226 said:**
> 

I'm relatively new to Ubuntu, but using other distros, I've had near 1,000 day uptimes on many of my servers.  And none of those ran the equivalent of LTS.

Until Fedora and Ubuntu came around, pretty much ALL distros were the equivalent of the LTS releases.  If you have a server with 1000 days uptime, then I would like to know what distro you were using 3 years ago that had a 6-month release cycle.  If it is a popular mainstream distro such as Debian, RedHat, or Gentoo, then they were ALL the equivalent of LTS.

If you are telling the truth and used something with a 6-month release cycle such as Fedora or Ubuntu from back then, then your server is seriously out of date on security patches.

---

### Post by CyberDean on 2008-02-25
> **Brazen said:**
> Are you having a driver problem with your hardware on Ubuntu 6.06.2?  If not, then it's not an issue.  If you are, then personally, for a production server, I would replace the hardware or wait for the next LTS release in April, but that is just something you will have to take into consideration.

Hi Brazen, First personal Linux server, all I'm trying to do is stay out of problems from the start before the server is built and software installed.

My first Linux install went very well on an older computer till I got hit by
a power brownout that blew the neutral in my meter box that blew the power supplies in two of my computers that were turned off.  Got the window's machine back up and running but the Linux machine is still waiting for a replacement power supply.  Did not have problems installing the Linux software or operating the Linux machine.

Catch you all later, Thanks.

---

### Post by astrotech226 on 2008-02-25
> **Brazen said:**
> 
If you are telling the truth and used something with a 6-month release cycle such as Fedora or Ubuntu from back then, then your server is seriously out of date on security patches.

These uptimes were done with RH 9.0 and FC1.  At this time RH was spitting out distros like crazy.  There were releases between RH 9.0 and FC1.  I can't remember if it was called 9.9 or 10.0, but RH desktop had a goofy yellow flower on it.  And you could tell they were making the migration to Fedora.

And I didn't really need to update the security patches on those particular servers.  Even the one's on the internet were firewalled and ran particular services like sendmail and apache and noone had shell access.  And I usually compiled my own versions of those so the updates weren't too big a deal to me.

The equivalent of LTS back then would have been RHEL3 if I remember correctly.

---

