---
title: "Virus?"
date: 2009-01-21
forum: Security
---

### Post by Celestika6 on 2009-01-21
I think I may have a virus... the signs are there. Random files disappearing on me, CD drawer won't close. What is a good, free virus scanner program for ubuntu 8.10 (intrepid)?

---

### Post by Dr Small on 2009-01-21
It's possible I guess, but highly unlikely. Are you sure that some application is not still "holding" on to your CD-ROM drive and that the files were deleted by accident, or your hard-drive is losing files?

---

### Post by hyper_ch on 2009-01-22
it's not a virus.

---

### Post by The Cog on 2009-01-22
clamav is a good free virus scanner. It's in the repos. But I very much doubt that you have a virus. Look for other explanations for the problems too.

---

### Post by theotherphil on 2009-01-23
> **The Cog said:**
> clamav is a good free virus scanner. It's in the repos. But I very much doubt that you have a virus. Look for other explanations for the problems too.


I thought ClamAV was for virus checking emails, not for routine scanning of a filesystem?

---

### Post by |{urse on 2009-01-23
LOTS of things to troubleshoot here, so here they are in no specific order.

Does the same thing happen with the cdrom when you are using the livecd version? You should try that first. 
command to eject cdrom is eject or sometimes eject /dev/sr0 or sometimes eject cdrom
If it does happen you have a defective cdrom.

Back up your files immediately. Try a fresh install opn a different hard drive. This is the only way you will know for sure. I've seen *nix/win/mac running on degraded hard drives do all manner of odd things that seemed "virusish" and while there are virii that target linux (you have better chances of winning the lottery than getting one) I doubt any of them would stop your cd-rom from closing.

If you have a stick of compatible ram laying around (not everyone does) I'd give that a go as well. 

there is also a good possibility that the ide (or sata) controller on your system is taking a dump. That would really suck because unless you are a soldering god then you need to get a new motherboard. 


If you try all this and you are still experiencing the same problems then the next possibility is that you have been hacked, not infected. try issuing the "who" command to see if there is anyone other than you logged into your system. Reset your router. Change your passwords. Alert your isp etc etc etc. there are a lot of things you can do to harden security but i doubt any of this is software related, sounds like hardware to me.

BUT before you do anything posting the output of the

dmesg | tail

command will be useful.

---

### Post by Celestika6 on 2009-01-25
I downloaded ClamAV and scanned all my files using the following:

> sudo clamscan -r --bell -i /

It came up saying it had found 2 infected files. Here's the thing... adding the -r to the command is supposed to remove the infected files. I scanned again to be sure it had zapped them and it came up saying there were still 2 infected files. How do I delete them myself from the terminal?

---

### Post by Zip247 on 2009-01-25
What are the infected files???

---

### Post by nubdora on 2009-01-26
Most likely false positives. 

Personally, I'd rather have files disappearing from my HDD than endless CPU cycles and gigabytes of free space disappearing with no interation from the legitimate user. *sigh*

---

### Post by The Cog on 2009-01-26
I still think a virus is unlikely. Can you post the name of the files and the md5sum results for them?

---

