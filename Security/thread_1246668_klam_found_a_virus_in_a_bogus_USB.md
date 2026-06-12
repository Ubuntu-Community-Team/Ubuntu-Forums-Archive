---
title: "klam found a virus in a bogus USB"
date: 2009-08-22
forum: Security
---

### Post by winst0n on 2009-08-22
I was trying to set up a flash drive to boot so it may be some kind of buffer,
but why is it still there? 
Should I erase it?
Should I be suspicious of the windows distribution it is associated with?

Anyway here's the post:

Anyone try any tools to examine / verify boot sectors with some translation from machine to human readable?

I won't be trying windows for a while ...

21265 was the final virus count from Klam.
I went and erased whole directories of HTML files.
Klam Anti-Virus has found 3 "broken executables" in the Linux File System that I am inclined to leave.
(it's libfglrx_ip.a.GCC4 that was updated twice).
Before I attempt another Windows distribution I would like to obtain BOOT SECTOR confidence.
I'm still a ways away from looking at raw Hex dumps.
I've been fiddling with partitions a little and some unexpected things have been happening.
I've been getting Physical/Logical discrepancies.

Something that was infected is making me think a different win distro may be necessary:

Has anyone ever heard of a reason for a "USB" folder that does not correspond to an actual flash drive?
What I have COULD be legitimate but I am concerned that virus activity either independently, or packaged with my Windows distribution may be the cause.

winston@ubuntu-9-04:/media$ ls
cdrom disk floppy ntfsdisk USB\040DISK
cdrom0 disk-1 floppy0 RED\0402GB WHITE-DT-8G

winston@ubuntu-9-04:/media$ cd USB\ DISK
bash: cd: USB DISK: No such file or directory
winston@ubuntu-9-04:/media$ cd USB*
winston@ubuntu-9-04:/media/USB\040DISK$ ls
boot.bin DOCS $OEM$ syslinux.cfg VALUEADD WIN51IP
boot.catalog I386 README.HTM ubnfilel.txt vesamenu.c32 win51ip.SP3
cmpnents OEM SUPPORT ubnpathl.txt WIN51
winston@ubuntu-9-04:/media/USB\040DISK$ cd \$OEM\$
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$$ ls
$$ $Docs
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$$ cd \$\$
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$/$$$ ls
OEMDIR Resources system32 Web
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$/$$$

At one point I was trying to make a bootable Flash from the distro so it may be some kind of buffer folder that I can erase.
I will cross-post in a Linux Forum. 

I'd like to get my machine clean.
Klam seems to have found most of the critters.
Still need a way to know my boot sectors are ok.

---

### Post by bodhi.zazen on 2009-08-22
> **winst0n said:**
> 21265 was the final virus count from Klam.

That is a huge number. You were either severely infected, quoting the number of files scanned, or are looking at false positives.

The raw output of klam would help.

At any rate, it sounds as if you have already started deleting things.

As such my advice is to simply re-format the partition(s) and start over.

In the future, FYI, Linux antivirus scanners are notorious for false positives and you really need to investigate further before you assume that just because you get a warning or a positive "infected" file and start deleting things, especially if you are deleting things in a Linux native partition.

---

