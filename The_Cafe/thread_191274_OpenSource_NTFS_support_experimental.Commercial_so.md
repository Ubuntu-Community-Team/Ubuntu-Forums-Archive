---
title: "OpenSource NTFS support experimental.Commercial software already ahead?How can it be?"
date: 2006-06-07
forum: The Cafe
---

### Post by zugu on 2006-06-07
As we know, there are open source programs/platforms/layers/scripts/hacks etc. that provide full NTFS partitions access from within Linux (as in read AND write).

The problem is this is experimental and hence very unstable, so it's not recommended to the casual user.

However, I have found some commercial, closed source applications that can claim to provide painless NTFS writing support from within Linux. Actually, I know someone that payed for a program like this and says that he never experienced HDD/partition damage or corruption, not even the slightest data loss.
The developers claim that their application does not inclue Microsoft code and is perfectly legal to use (of course, after paying for a license).

How can this possible? How can a company developing closed software (so with less people looking into the code, or designing the app) be ahead of the open source movement? Is it because they have more money? Is it because they have more skilled programmers? Why?

I know, this is just a dilemma of mine and this is not a general Linux forum, but I think it would be interesting to know the answer.

---

### Post by glotz on 2006-06-07
Well, the private outfit can have many people working on the issue full time. Also, Microsoft might have revealed them something that they haven't released in public. I personally think that NTFS support isn't a very interesting issue. Pure Linux, all the way.

---

### Post by IYY on 2006-06-07
Who knows. It's possible that they had some ex-Microsoft employee working on this and telling them how to do this.

---

### Post by dvarsam on 2006-06-07
[QUOTE=glotz]Well, the private outfit can have many people working on the issue full time.
Also, Microsoft might have revealed them something that they haven't released in public.[/quote]

Do you know what is the Program called out there?

> I personally think that NTFS support isn't a very interesting issue.
Pure Linux, all the way.

On the contrary!
I disagree!
If FAT can _only_ go up to 30GB maximum, NTFS is a _must_!!!

We NEED some _limitless_ format that can work with Windows with NO problem!

FAT has a size limit!
If it did NOT, then there would be NO problem...
Since it does, I consider the NTFS write possibility of great importance!!!

P.S.> If you know the program's name, please post it...

---

### Post by Wolki on 2006-06-07
[QUOTE=dvarsam]
If FAT can _only_ go up to 30GB maximum, NTFS is a _must_!!!
[/quote]

Tell that to my FAT 80GB external drive. :)

> P.S.> If you know the program's name, please post it...

Paragon NTFS for Linux: [http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)

---

### Post by aysiu on 2006-06-07
[QUOTE=dvarsam]
On the contrary!
I disagree!
If FAT can _only_ go up to 30GB maximum, NTFS is a _must_!!!

We NEED some _limitless_ format that can work with Windows with NO problem![/QUOTE] It's called Ext3

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by sup on 2006-06-07
> It's called Ext3

[http://www.fs-driver.org](http://www.fs-driver.org)
Well, it is working but not painlessly - to my knowledge, fs-driver does not properly support different encodings and when a disk with ext3 is not properly unmounted before connecting to windows machine, it refuses to mount on windows.

---

### Post by varunus on 2006-06-07
If you have a windows license, you can use the Captive NTFS Drivers on Linux for full read-write support.  Captive was recently updated to use the new FUSE kernel interface, too.  No paragon required.  NTFS write support is being worked out by the open source guys; give it time...they already have it experimentally.

---

### Post by dvarsam on 2006-06-07
Dear "Wolki",

Thanks for your reply!

> Tell that to my FAT 80GB external drive.

Sorry to ask, but how did you format an 80GB drive into FAT32?

Basically, when I do that from Windows, it is NOT permittable!!!

Were you just joking (else how did you do this)?:-k 

And this 80GB FAT32 drive can be Read/Write in a Windows System?

> Paragon NTFS for Linux

I wonder: Does this work with 100% success?
(if it does, then why did the PC Magazine gave it a rating 4.5/5.0 instead of 5.0/5.0?)

---

### Post by glotz on 2006-06-07
You've got too old a BIOS, that's your limit. (Maybe) You probably can upgrade (flash) it. Be careful though! See [http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html](http://www.tldp.org/HOWTO/Large-Disk-HOWTO-4.html)


Or maybe it's just the tools you use, see [http://en.wikipedia.org/wiki/Comparison_of_file_systems#fn_7](http://en.wikipedia.org/wiki/Comparison_of_file_systems#fn_7)
and [http://en.wikipedia.org/wiki/Comparison_of_file_systems#fn_7_back](http://en.wikipedia.org/wiki/Comparison_of_file_systems#fn_7_back)

---

### Post by wthanna on 2006-06-07
Hmm.. In dapper, using gparted, I created a 40GB FAT32 Partition.  I booted back into XP and backed up several GB worth of data to it from a mixed network environment (ext3, NTFS, FAT32).  I have been able to successfully access (read and write) to this partition from both windows and linux with no problems.

---

### Post by glotz on 2006-06-07
wthanna, read the last 2 links in my previous post. Mystery solved.

---

### Post by jdong on 2006-06-07
Windows XP does not format FAT32 partitions larger than 30GB or so, but will gladly accept 100+GB FAT32 partitions formatting with Linux or windows 2000, etc.

The real limitation of FAT32 is the maximum file size limit.


As far as the NTFS support, they likely signed a nondisclosure agreement with Microsoft that allowed them access to NTFS details but restricts them from ever making it open source.

---

### Post by G Morgan on 2006-06-07
[QUOTE=jdong]The real limitation of FAT32 is the maximum file size limit.[/QUOTE]

As somebody who used a variable sized HDD image with VMware and found himself out of room all of a sudden (was a while ago now) I can attest to this. Always tend to just mount extra blocks as and when they are needed these days to get around the 4GB problem.

---

