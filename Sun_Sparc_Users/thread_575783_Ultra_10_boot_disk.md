---
title: "Ultra 10 boot disk ?"
date: 2007-10-14
forum: Sun Sparc Users
---

### Post by AgentZ86 on 2007-10-14
Hi all.

I created a sparc 7.04 ubuntu cd on my linux box, 

I go over to the ultra 10 sparc system with 440 MHZ sparc processor and hit the stop+a key to get the ok prompt.

Then type boot cdrom, and I get a message like can't find volume label or something and can't find something else check cables or something.

Anyhow I was not sure I it was ok to burn the CD from my linux box shouldn't I still be able to use this to boot up the ultra 10 system.

The CD files look ok, folders etc.  and seems to read ok.

Did I do somethin wrong on the burn ?

Please advise.

---

### Post by zanderred on 2007-10-16
Hi, I'll take-it that youre ultra 10 is ok, all wired up?, when the u10 is booted it go's into initializing. (initialising) press stop A befor this stops! boot cdrom. (it wiil continue to initiate) and then boot the cd. if you do not stop at the initializing stage the computer starts to boot loads a bit of code. if that happens, at the OK type reset and start again.(still-no cold boot )
hope this helps

---

### Post by AgentZ86 on 2007-10-20
Yup, thanks, but as I indicated in the post, I've done the stop+A and got the OK prompt, then typed boot cdrom but still no effect I get some volume message.

I'm not sure I burned the CD correctly, but let me ask ??

Is is ok to burn the CD on a Ubuntu PC system cause thats what I did ? 

Just burned the ISO image to the CD and it's all there on the CD, files etc. not just an ISO so I assume it's ok.

But since I'm not familiar with the Sparc systems I was basically wanting to confirm that it should work. ??

I'll try again on another Sun system perhaps the CD drive itself is not working properly.

Thanks

---

### Post by Moulton on 2007-10-20
I've generally had poor luck booting Sparc machines off of custom-burned CDs.  

Try to find a professionally pressed CD to boot your machine.

The first thing you want to prove is that you can at least boot into *some* OS from a known good CD.

There are other solutions for booting Sparc machines, especially if you have a spare external drive that you can prepare on another machine.

---

### Post by pwyll on 2007-10-23
I've not had problems booting a Sun Ultra 10 from a burned cd...I've burned a couple of Debian distros, Solaris 10 and FreeBSD (besides Ubuntu) from both winblow$ and linux boxen and never had a problem with the cd's.  On the other hand, I've *always* had to cold-boot/power-cycle to boot from cd.  Just hitting stop-a while the box is running will allow a boot from disk, but not from cdrom.  I've always had to turn the power off and hit stop-a as the memory is initializing from a powered-down state.

---

### Post by AgentZ86 on 2007-10-23
> **pwyll said:**
> I've not had problems booting a Sun Ultra 10 from a burned cd...I've burned a couple of Debian distros, Solaris 10 and FreeBSD (besides Ubuntu) from both winblow$ and linux boxen and never had a problem with the cd's.  On the other hand, I've *always* had to cold-boot/power-cycle to boot from cd.  Just hitting stop-a while the box is running will allow a boot from disk, but not from cdrom.  I've always had to turn the power off and hit stop-a as the memory is initializing from a powered-down state.

Thanks I'll try that

---

