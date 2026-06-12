---
title: "Hardware Virus? or simply a sticky key?"
date: 2009-03-12
forum: Security
---

### Post by Thorzilla on 2009-03-12
I dual boot Vista and Ubuntu Intrepid on a Sony Vaio VGN Fw235j.
It has 4GB RAM, 250GB HDD and a 2.0GHz Intel Core 2 Duo.
The vid card is an Intel GMA chipset.

I got a virus yesterday while I was torrenting an episode of a TV show. I was on Vista with a sandbox. I could find the link to the torrent if you need it. The virus evaded UAC, shut down my computer, restarted, and now my capslock turns on when my computer powers up. I've tried booting linux, but ubuntu drops to the (initramfs) prompt with lots of "[^" that never end.

I've tried using live cd's but they all drop to (initramfs)
I've even tried DBAN (Dariks boot and nuke), but it fails saying there are bad sectors on the drive.
As far as I can tell, the virus loads to ram the moment the laptop powers up, but I could be wrong.

The computer is about a month old, which is why I dismissed a sticky key as the reason

Does anyone know a way for me to nuke my hard drive without booting up (I can use a friend's computer as a host...but I'm not sure how)? Or any other solution?
Please help.

Thanks

---

### Post by hyper_ch on 2009-03-12
shouldn't you rather ask this on a windows forum?

---

### Post by bodhi.zazen on 2009-03-12
I think you need to start by identifying the virus.

Could be a hard ware problem and it could be you are jumping to conclusions.

And this is the problem with antiviurs, the do not protect you against zero day exploits.

---

### Post by Thorzilla on 2009-03-12
Re: Hardware Virus? or simply a sticky key?
I think you need to start by identifying the virus.

Could be a hard ware problem and it could be you are jumping to conclusions.

And this is the problem with antiviurs, the do not protect you against zero day exploits. 

-----

Well, I ran symantec on my windows system and while it was scanning registry entries I noticed weird entries like [www.kaspersky.com](www.kaspersky.com) [www.sophos-antivirus.com](www.sophos-antivirus.com) and a few other IP's.

I guess that would mean a virus.

Although, yes, it could also be a hardware problem.
I'll try and get more info after I get home today.

Thanks!

---

### Post by Hobgoblin on 2009-03-12
> **Thorzilla said:**
> 
I've tried using live cd's but they all drop to (initramfs)


A virus which affects live CDs, that would have to have infected (and altered) the BIOS, which is pretty unlikely.

---

### Post by hacker07.gbh on 2009-03-12
It might just be your keyboard. Try rebooting.

---

### Post by hacker07.gbh on 2009-03-12
Can you boot into any os. If so just get a live cd partition editor.

---

### Post by Thorzilla on 2009-03-13
> **hacker07.gbh said:**
> Can you boot into any os. If so just get a live cd partition editor.

So it turns out this is a result of multiple issues.
1. My keyboard was faulty
2. Vista had a virus, but it was not the cause of these problems, it seems to be a keylogger.
3. Ubuntu drops to (initramfs) because it has some sort of issue with the address of the HDD on my computer -> more information/a solution here:[http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html](http://www200.pair.com/mecham/spam/waiting_for_root_file_system.html)
This fix simply switches it back to initrd from initramfs, not the most desirable.

I still need to find a solution to that

4. My HDD has some bad sectors in it, need to have it replaced.


I found all this out because it was only Puppy Linux that managed to boot onto the computer with the pfix=toram option.


Thanks for all the help everyone. Glad to be using OSS :D

---

### Post by bodhi.zazen on 2009-03-13
I am going to close this thread now.

As I indicated previous let's not assume any and all problems are due to a viurs.

Pleas post any ongoing issues in "General Help".

---

