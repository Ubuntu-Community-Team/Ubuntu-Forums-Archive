---
title: "Salvation of a problematic machine"
date: 2007-01-12
forum: Testimonials &amp; Experiences
---

### Post by zerhacke on 2007-01-12
I've been a Ubuntu user for some time now, but I have a new story I want to share.

I had been using a custom build machine for some time.  My kids were stuck with an old Dell Optiplex GX110 machine.  Pretty old and didn't play any games they wanted to (mostly emulators) due to the crappy i810 graphics chipset on it.  The machine also regularly gave a BSOD or a stop error to the point the machine couldn't run for more than 1 hour before dying.

So I switched the kids my machine for theirs.  They got a fully customized Edgy machine and I took on the problem child machine.  Everything I read on the net told me the RAM was bad, but no memtest on earth could find the problem.  I just knew the problem was that Windows XP SUCKED.

I was right.  This little Ubuntu box has only been rebooted once, and that was because I got a new kernel.  BSOD this, Windows!

I'm happy with this little machine.  Sure, I took a step down in almost all directions in trading my kids a computer, but I can still compile, surf the net, and play games so I'm happy.

---

### Post by weresheep on 2007-01-14
My Mothers work used to have Dell GX110 machines and they had no end of trouble with them. They ran WIndows NT 4.0 with a whole lot of other sortware and only had 64MB of RAM. When I heard they were throwing them out for new machines I got a couple for free. My main machine is now one of those Dell GX110s with a Pentium III 733MHz processor and (upgraded from 64MB) 512MB of RAM.

It runs Ubuntu Dapper and works very well. The i810e integrated graphics aren't great and it does mean I lose 8MB of system memory for the shared graphics RAM but on the whole everything works fine and the performance is perfectly acceptable.

Long live the GX110 :mrgreen: 

-weresheep

---

### Post by Dragineez on 2007-01-22
How did you get it to install? I've likewise "inherited" a bunch of these from work and the installer fails when trying to mount the CD.

And before you ask, the CD is good. Two days of googling, and I'm not the only person having this problem on these machines. All CDs have been burned with verify, the MD5 of the download matches. The verify matches. Copying of all files from the burned CDs works flawlessly. That is not the problem.

Did you do anything special to get the install to work?

---

### Post by weresheep on 2007-01-23
Hello,

I installed Ubuntu on my GX110 a while ago but I don't remember having to do anything special.

What version of Ubuntu are you installing? I have Dapper Drake LTS 6.06 on my GX110. I installed it from the normal LiveCD before they released the 6.06.1 version. If I remember correctly it took a couple of attempts as the install hung when transfering files but apart from that it installed okay.

Perhaps Edgy introduced an incompatibility with the Optiplex GX110. Maybe Dapper would be worth a try?

-weresheep

---

### Post by Dragineez on 2007-02-06
> **weresheep said:**
> Hello,

I installed Ubuntu on my GX110 a while ago but I don't remember having to do anything special.

What version of Ubuntu are you installing? I have Dapper Drake LTS 6.06 on my GX110. I installed it from the normal LiveCD before they released the 6.06.1 version. If I remember correctly it took a couple of attempts as the install hung when transfering files but apart from that it installed okay.

Perhaps Edgy introduced an incompatibility with the Optiplex GX110. Maybe Dapper would be worth a try?

-weresheepAgreed, I've given up on Edgy. Can't get it to work on anything. Had much the same problem with Dapper. After much research, I got this to work. Now, I'm not exactly sure which of these parameters was critical - but:

```
boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false
```

Yeah, I know - I have noacpi in there twice. Never hurts to be sure!

Now if I could only get the damn nVidia GeForce FX 5500 to work on this bloody thing!

---

