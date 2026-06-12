---
title: "Can a virus infect my linux partition if my XP partition is infected?"
date: 2008-07-23
forum: Windows
---

### Post by AOZ on 2008-07-23
If windows can't recognize the ext3 partition will it not be able to write to it aswell or have hackers found a way around that?

---

### Post by hessiess on 2008-07-23
if you have the windows ext3 driver installed then yes, as it complely ignores linux,s scuraty. the same thing is true with wubi while win is running.

---

### Post by tamoneya on 2008-07-23
it makes little sense for a virus writer to waste time on ext3 since only people running linux use it and there are currently no linux virii in the wild and definitely no cross OS virii.  Even if a windows virus did migrate into an ext3 partition through fsdriver(ext3 on windows) it still wouldnt be able to take control of the OS because it would not have the correct permissions to control the computer. (it could delete stuff if it wanted to but that isnt a very good virus if it cant replicate itself).

---

### Post by Frak on 2008-07-23
Ummm... No? I'd like to shake the hand of anybody who could create a virus that could infect Windows AND Linux.

---

### Post by Canis familiaris on 2008-07-24
> **AOZ said:**
> If windows can't recognize the ext3 partition will it not be able to write to it aswell or have hackers found a way around that?
No. Because Windows cannot access Linux partitions and Windows viruses do not affect Linux.

---

### Post by hellion0 on 2008-07-24
Assuming you've r/w access to the ext3 partition while under Windows... it can't *infect* it, but it certainly has the capability to *damage* it. If there's no write access, then the point's completely moot.

---

### Post by lisati on 2008-07-24
> **Anurag_panda said:**
> No. Because Windows cannot access Linux partitions and Windows viruses do not affect Linux.
Qualification: **by default** Windows can't access Linux partitions (ssssh...don't tell my desktop, it has drivers installed on its XP partition that let it access the Linux partitions)

Best bet: protect yourself within Windows from nasty stuff (antivirus, antispyware, etc), all the other usual Windows precautions...... (plus using "common senses" about potentially unsafe sites)

---

### Post by eldragon on 2008-07-24
actually, this poses as a security threat.
imagine a windows vulnerability. and a virus tailoerd to search for ext3 partitions or wubi installs.

its the equivalent of giving root access to your linux os.
they can modify any system file they want. even add users, add small daemons to the init script..or what not. and then, when runnning on linux, start spamming the world...

they would take advantage of the insecurity of the windows os and the stability of the linux world. :(

this seems quite possible. :(

---

### Post by hyper_ch on 2008-07-24
malware on windows could still delete/wipe the linux partitions...

---

### Post by Canis familiaris on 2008-07-24
> **hyper_ch said:**
> malware on windows could still delete/wipe the linux partitions...

I didnt think that. This is scary.

---

### Post by insane_alien on 2008-07-24
viruses can(depending on the skill of the developer) write to the disk independantly of the filesystem. if it generates and writes random data to random parts of the disk then it will affect your linux partitions as well.

best to keep the two seperate. although most viruses will not affect it.

---

### Post by Archmage on 2008-07-24
Don't forget that a bootblock virus will still infect everything (and most of the time they will kill grub).

---

### Post by loell on 2008-07-24
i would love to be wrong, but

yes it can, virus writers will just have to bundle ext2fsd into their software.

---

### Post by seanc7 on 2008-07-26
You can put Windows-virus infected files on a Linux ext3 partition but it's not going to affect Linux as it's a Windows virus. BUT if you put the virus back on a Windows system it WILL start messing with Windows again.

---

### Post by ariscanete on 2009-01-09
Based on my experience as a WILD Desktop technical support for both Windows and Linux computers, Viruses like malware / Rootkit can't infect a Linux box using an ext3 partition format. 

As a matter of fact, I even use my Linux Ubuntu Live CD or any Linux Live CD to troubleshoot on a Windows partition Hard Disk and remove viruses manually or a Linux box with a Windows hard disk installed as 2nd Master drive.

---

### Post by hyper_ch on 2009-01-09
A virus could also just delete or format another partition... so it can affect your linux partition.

---

