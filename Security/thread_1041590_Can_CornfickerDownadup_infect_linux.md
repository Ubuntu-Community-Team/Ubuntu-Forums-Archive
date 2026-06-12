---
title: "Can Cornficker/Downadup infect linux?"
date: 2009-01-16
forum: Security
---

### Post by joey-elijah on 2009-01-16
I know it's a somewhat dumb question to ask, but with a Windows partition it's something i need to make sure of! 

Also, I've been using IE4Linux in Ubuntu. Is it possible to catch this worm and for it to effect Linux by going through Wine etc?

My virus scans haven't thrown up anything, but i just want to make sure.

***NB: Cornficker/downadup is a current worm that has infected up to 10 million PCs - over a million in the last day or two.***

---

### Post by jgoguen on 2009-01-19
Short answer: I highly doubt it'd work "correctly" if even at all.

Long answer: I haven't seen anyone try this one in WINE, but based on some testing done a while ago with other viruses in WINE I would say it's highly unlikely that this one will work "correctly", if it works at all.  You'd need to make sure infected files don't get copied to the Windows partition, but if you mount them read-only that's not a problem.  Worst-case, you're using IE6 and this worm downloads and it happens to download itself to your Windows partition, but that's incredibly unlikely, since the worm is expecting Windows paths and will thus end up copying itself somewhere into your WINE prefix.  So the chance of it getting onto your Windows partition is pretty slim.

---

### Post by PocketDog on 2009-01-20
Even if it does silently download, it can't download to anywhere outside your home folder. And it certainly can't execute, even if it is partially coded to run in a Linux environment.  It doesn't matter what browser you're using - damage can only be done if the browser is running as root or with sudo privileges, and nobody's stupid enough to do that, are they? ;-)

---

### Post by jgoguen on 2009-01-21
> **PocketDog said:**
> damage can only be done if the browser is running as root or with sudo privileges, and nobody's stupid enough to do that, are they? ;-)
Are you sure?  Tell me something, what would you consider to be more important?  The system files that you can recover with a reinstall and updates, or those family photos that haven't yet been backed up (cause not everyone does backups on a daily basis, or even ever until they have to reinstall...) and those documents that you've been working on for months?  Personally, I'd rather suddenly lose /usr/ than have to deal with recovering even half of a day's work.

---

### Post by Sorivenul on 2009-01-21
I've already read some reports from folks trying to run it on Wine. All point to it being an unsuccessful attempt. I highly doubt there is much, if any, risk for Linux.

---

### Post by hyper_ch on 2009-01-22
> **jgoguen said:**
> or those family photos that haven't yet been backed up (cause not everyone does backups on a daily basis, or even ever until they have to reinstall...) and those documents that you've been working on for months?
Well, if they don't backup then they should blame no one but themselves... a harddisk may fail from one day to another and teh data is gone. If they don't backup then they have no grounds to complain.

---

### Post by jgoguen on 2009-01-22
> **hyper_ch said:**
> Well, if they don't backup then they should blame no one but themselves
Oh I fully agree.  Backup, backup, backup, and if it's important make a second copy somewhere else.  All I'm saying is, what data is more important.  IMO (clearly) the user's data is much more important than system files. System files can be easily restored with a reinstall/update, but for the average user who doesn't make regular backups losing personal files could be devastating.  I've seen it happen, I work tech support for my university and one time a Computer Science grad student came up to us asking if we could recover his thesis from a USB key, the one and only place he'd saved his thesis and all his research.  I'm willing to bet he makes backups now though ;)

---

### Post by hyper_ch on 2009-01-22
> **jgoguen said:**
> IMO (clearly) the user's data is much more important than system files.

It depends, you seem to think of linux as single-user OS only where each user uses the same account. If you alter your perspective and treat it like a real multi-user OS then you would see, that one's home data is less important than the overall system. If you get root access you get access to everyone's data.

---

### Post by PocketDog on 2009-01-24
I may be wrong here, but won't the user have to manually run Conficker (edit: *any* malicious program) to have it affect the home folder (or anywhere), or make it executable? No downloaded files can possibly run without user intervention, can they?

---

### Post by ZarathustraDK on 2009-02-04
> **jgoguen said:**
> I haven't seen anyone try this one in WINE, but based on some testing done a while ago with other viruses in WINE I would say it's highly unlikely that this one will work "correctly", if it works at all.

So, Wine-devs, when can we expect Wine to support Downadup/Cornficker? :D

---

### Post by unoodles on 2009-02-04
I tried it in WINE. There was a thread in the Community Cafe. The problem is that it runs as a dll, so you have to use the rundll32.exe tool. This does not work.
I had to go with a virtual machine. Infected it nicely :D.

P.S. You can get it from offensivecomputing.net

---

