---
title: "Windows documentation, wow. Just, wow."
date: 2011-10-23
forum: The Cafe
---

### Post by hwttdz on 2011-10-23
So I was looking for which format I might want to make my new external drive such that it will play nice with any computer I might interact with (i.e. as many systems as possible) and hoping to get the advice of people wiser than I, I googled
[http://www.google.com/search?hl=en&q=windows+linux+hard+drive+format](http://www.google.com/search?hl=en&q=windows+linux+hard+drive+format)
hoping to find the advantages of filesystem formats readable by both windows and linux, and was somehow inspired to click on the windows documentation:
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

The summary is reproduced here:
> This article explains how to remove the Linux operating system from your computer and install Windows XP. This article assumes that Linux is already installed on your computer's hard disk, that Linux native and Linux swap partitions are in use (which are incompatible with Windows XP), and that there is no free space left on the hard disk.

NOTE: Windows XP and Linux can coexist on the same computer. For additional information, refer to your Linux documentation. 

1) Linux native and swap are incompatible with windows xp? I don't know if it's possible to put root on an ntfs or fat32 (or if it's a good idea), but it probably is possible with home (still possibly not a good idea), but that seems to sort of steamroll the issue.
2) We're just going to assume there's no hard disk space left, so you don't want another operating system, you want windows, trust us. 
3) If you aren't intimidated enough by tech support documentation (which probably gets its bad name from the windows support pages) to realize we're trying to pull a fast one, we're not going to tell you how to dual boot, you better hope it's out there somewhere.  

And the #1 complaint I hear about linux is "well sure maybe it's more stable and faster, but it's not user friendly".  Seriously?  That's your documentation, and you're going to sit there and tell me with a straight face, that's more user friendly? </rant>

But if anyone does have any input about which format to make my external (possibly multiple partitions? maybe have a bootable system on there?, I have 250 gigs to work with) let me know.

---

### Post by Flymo on 2011-10-23
So true, so true.   Lies and FUD are all you can expect. <sigh>

There's a biography of Microsoft's Glorious Leader [here]("http://knol.google.com/k/david-blomstrom/bill-gates/1i6e04re3w2kp/4#Biography")

---

### Post by ubu_dynamite on 2011-10-23
If you want to use the external drive with windows use "ntfs".
Unix like systems can read and write to it using "ntfs-3g"

---

### Post by sffvba[e0rt on 2011-10-23
> **ubu_dynamite said:**
> If you want to use the external drive with windows use "ntfs".
Unix like systems can read and write to it using "ntfs-3g"

+1 for NTFS


404

---

### Post by kurt18947 on 2011-10-23
Playing well with others is not one of Microsoft's strong suites.  Linux reads and writes NTFS files quite reliably so it's possible to use an NTFS  partition on an external drive as a data repository readable by both Windows and Linux.  There are also add-ons for Windows that enable Windows to use EXT 2 & 3 partitions; I'm not sure about EXT 4 .  If you google something like "windows reading ext3 drive" you should find some information.  I've had pretty good luck either creating a partition on an internal hard drive that both operating systems can see or creating a partition on a removable device.  As far as running an OS on an external drive I think USB2 would be kinda slow. eSATA or USB3 might work pretty well though.  If you set the BIOS to boot first from any USB drives,  I don't think you'd have any problems with GRUB on the internal hard disk but I'm no expert so take this for what it's worth.

---

### Post by Merk42 on 2011-10-23
I really don't see what the problem is with the article.

Let's look at the summary again:
> 
This article explains how to remove the Linux operating system from your computer and install Windows XP.Fine, if you have a problem with such an article existing, then you should have a problem with this [this help article too](https://help.ubuntu.com/community/HowToRemoveWindows)

>  This article assumes that Linux is already installed on your computer's hard disk,If it weren't then the user wouldn't need the article how to **remove Linux**

> that Linux native and Linux swap partitions are in use (which are incompatible with Windows XP),By default most Linux distros would install those as ext, which is incompaible by default, with Windows

> and that there is no free space left on the hard disk.So we have a FULL harddrive, and the user wants to install Windows, how would you propose they get it on there without removing Linux? Repartition?  Good thing there's this last quote 

> NOTE: Windows XP and Linux can coexist on the same computer. For additional information, refer to your Linux documentation.


---

### Post by hwttdz on 2011-10-23
But this article more closely corresponds to the collection of links linked to from here: 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

As there's nothing significant about reformatting the hard disks and starting from scratch in any case.  And, yes, I would be annoyed if the only link from that page were "do this if you want to wipe everything on all your disks and start fresh with a shiny new copy of ubuntu which won't read data from any other partitions/drives that you might previously have had, if this isn't what you want you can look somewhere else".

There's even the, "so you have windows and now you want both" documentation:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows#Dual-Boot](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows#Dual-Boot)

My issue is that they make a lot of bad assumptions about what the user wants to do and except for one sentence which is more or less "we're not going to tell you how to do that", they attempt to present the material in such a way to minimize choices.

---

### Post by hwttdz on 2011-10-23
Using ext3 from windows is non-viable as the machines I will be attaching this to will not be my personal machine.

---

### Post by Tibuda on 2011-10-23
> **hwttdz said:**
> 1) Linux native and swap are incompatible with windows xp? I don't know if it's possible to put root on an ntfs or fat32 (or if it's a good idea), but it probably is possible with home (still possibly not a good idea), but that seems to sort of steamroll the issue.
What it says it that Windows XP can't read any Linux native filesystem like ext*. It does not say Linux can't read Windows file system like FAT* or NTFS.

> 2) We're just going to assume there's no hard disk space left, so you don't want another operating system, you want windows, trust us. 
It does not say it.

> 3) If you aren't intimidated enough by tech support documentation (which probably gets its bad name from the windows support pages) to realize we're trying to pull a fast one, we're not going to tell you how to dual boot, you better hope it's out there somewhere.  
That documentation is not about dual boot, but about installing Windows in a machine with Linux preinstalled.

> But if anyone does have any input about which format to make my external (possibly multiple partitions? maybe have a bootable system on there?, I have 250 gigs to work with) let me know.
NTFS is the best that could be read by both Linux and Windows, but I don't know if you can boot from NTFS.

---

### Post by hwttdz on 2011-10-23
It's not bad documentation if that's actually what you want to do.

It is bad documentation if/when you consider that there is no documentation for dual booting, and that it's documentation that's silly to have (because other than using linux to remove the partitions, it does the same thing as removing all partitions during a windows install).  Then suddenly it's quite bad documentation.  

And there is also no documentation for "if you have extra space and want to install windows alongside another operating system).

Also, I believe the various FAT's qualify as native linux filesystems (as in native kernel support), so in that case it's just wort of, wrong.

---

### Post by Merk42 on 2011-10-23
> **hwttdz said:**
> It's not bad documentation if that's actually what you want to do.

It is bad documentation if/when you consider that there is no documentation for dual booting, and that it's documentation that's silly to have (because other than using linux to remove the partitions, it does the same thing as removing all partitions during a windows install).  Then suddenly it's quite bad documentation.  

And there is also no documentation for "if you have extra space and want to install windows alongside another operating system).Doesn't dual booting depend on the Linux distro though? Do you want Microsoft to mention how to do it for every one of the hundreds of distros out there? Wouldn't it make more sense to do what they've done and say, yes you can do it, but look up the documentation for whatever distro you're using.

> **hwttdz said:**
> Also, I believe the various FAT's qualify as native linux filesystems (as in native kernel support), so in that case it's just wort of, wrong.
I'm guessing because the situation of a person who only has Linux installed yet formatted their drives at FAT is such an incredibly minute use case that it's just assumed they didn't do it.

---

### Post by Tibuda on 2011-10-23
> **hwttdz said:**
> It's not bad documentation if that's actually what you want to do.

It is bad documentation if/when you consider that there is no documentation for dual booting, and that it's documentation that's silly to have (because other than using linux to remove the partitions, it does the same thing as removing all partitions during a windows install).  Then suddenly it's quite bad documentation.  

And there is also no documentation for "if you have extra space and want to install windows alongside another operating system).
It makes no sense for MS to have such documentation. And they can't have liability if a user follows a documentation on dual boot and then void the hardware warranty or something.

> Also, I believe the various FAT's qualify as native linux filesystems (as in native kernel support), so in that case it's just wort of, wrong.

not, because they were not made by linux devs.


EDIT: Or what megaman said.

---

### Post by ViperChief on 2011-10-23
> NOTE: Windows XP and Linux can coexist on the same computer. For additional information, refer to your Linux documentation.

Y'all are right. They're spreading nothing but FUD. How dare they tell people that their system actually can work with Linux?

/sarcasm

---

