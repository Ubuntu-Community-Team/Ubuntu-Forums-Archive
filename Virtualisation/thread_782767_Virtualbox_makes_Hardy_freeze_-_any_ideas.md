---
title: "Virtualbox makes Hardy freeze - any ideas?"
date: 2008-05-05
forum: Virtualisation
---

### Post by ACMarina on 2008-05-05
Hardy is, without a doubt, stable in any other circumstance.  I installed Virtualbox to use a guest installation of Windows XP, as I send a lot of screenshots to show people how to do things and that would make the whole process a lot easier.  

Well, whenever I start the virtual machine, it's a ticking time bomb.  Sooner or later, something seems to happen that freezes the entire system.  I'm not even sure what's happening, but it's a full lockup - no keyboard or mouse action, and the only way out is to power down the whole system.

I've googled and searched here, but the only things I've found relate to dual core processors (which I don't have) and some sort of general freezing with Hardy (which I also don't have, it's quite specific to the virtualbox program)

Any ideas??

---

### Post by ACMarina on 2008-05-06
Come on, folks - anything?  Any ideas at all??

---

### Post by Lord_Phoenix on 2008-05-06
You asked for it...

I am not currently home so I can't "see it" and properly tell it...

Are you using the Personal VirtualBox ? I really do recomend you do, it works slightly better.

Anyway, there's a setting for the VMs that has to do with your Processor hability, or lack thereof, to deal with virtualization. It's a checkbox that reads something like 'VT-???/AMD??', it should be right on the first settings screen. Is it checked ? Try unchecking it, it worked for me on a laptop I setup yesterday, I don't think it was ever checked on my desktop pc.

---

### Post by ACMarina on 2008-05-06
Not checked at all.  I'm running a test right now, as it appears that this might be some sort of networking issue.  I've "disconnected" the network adapter in my virtualbox settings, and I have yet to freeze.  I'm going to run through the day and see what happens, but it looks like I might be on the right track..

---

### Post by ACMarina on 2008-05-06
Well, I was just kidding :)

I installed the guest additions and had an immediate freeze.  Maybe something else is to blame here..

---

### Post by Joeb454 on 2008-05-06
Perhaps it's the guest additions? What happens if you don't run them?

---

### Post by ACMarina on 2008-05-06
Nope, it freezes before the virtual machine can even start loading the operating system..

---

### Post by ACMarina on 2008-05-06
I've disabled the ACPI in virtualbox and things are going smoothly for now - I'm "reformatting" and starting over, so we'll see what happens!

---

### Post by ACMarina on 2008-05-07
Well, it's been about 24 hours and still no freezes - I'm still testing, but it looks like a possible fix..

---

### Post by ACMarina on 2008-05-07
Back to square one - still freezing..

---

### Post by ACMarina on 2008-05-08
I just don't understand it - I'll go for 12 hours with no trouble, then it will freeze for (apparently) no reason..

Any thoughts on possabilities or anything? Anyone?

---

### Post by ACMarina on 2008-05-09
Don't feel bad - nobody at Virtualbox seems to know either :)

---

### Post by maestrobwh1 on 2008-08-20
Yeah, same thing started happening to be about a week ago running an XP Guest.  I tried my best, upgraded, downgraded, purged, reinstalled, removed guest additions: the works.  It only happens on one machine as far as I can tell.  I have it on my one laptop running hardy, and my desktop running hardy, but this one particular laptop... the one I use the most, the guest boots but within a few minutes, the drive locks with a red led.  It isn't the drive seemingly b/c nothing else makes the machine freeze.  I can open ff3, dolphin, amarok all at once and everything is fine.  I can't even get VB to run without a lock even using fluxbox as my desktop.

Even using the command line with tools, like 

$VBoxManage clonevdi from / to

Command line things will complete (at times), but will lock before the command prompt returns.

Same machine runs Xandros, and a more or less clone of the VDI in another folder and I have no issues with it.

It seems to be a particular Ubuntu issue perhaps, but only with certain hardware?  

I have minimum options checked, I don't even have any shares set up.

---

