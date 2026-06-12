---
title: "Microsoft Office 2010 in WINE"
date: 2011-03-18
forum: Wine
---

### Post by TriBlox6432 on 2011-03-18
Has anyone gotten this to work flawlessly?  On winehq is says that it's garbage, but has anyone gotten it to work for them?

---

### Post by seawolf167 on 2011-03-18
I haven't tried it - but see if PlayOnLinux has an entry for Office 2010

---

### Post by Old *ix Geek on 2011-03-18
Is there a reason you want to use M$ products instead of their native Linux counterparts? I don't get this, so help me out please! :confused:

---

### Post by sydbat on 2011-03-18
> **Old *ix Geek said:**
> Is there a reason you want to use MS products **in WINE** instead of their native Linux counterparts? I don't get this, so help me out please! :confused:1) This - after FTFY.

2) Windows stuff works better on Windows. You could dual boot or run Windows in a VM if you want / need to run Windows programs.

---

### Post by dmn_clown on 2011-03-18
> **Old *ix Geek said:**
> Is there a reason you want to use M$ products instead of their native Linux counterparts? I don't get this, so help me out please! :confused:

Maybe when OpenOffice.org or LibreOffice or BrOffice or Lotus Symphony or whatever clone/fork pops up next month offer full compatibility with MS Office document formats and macros, this argument would be valid.  

The reality is that the majority need compatibility for one reason or other, none of the free applications provide that compatibility.

---

### Post by Old *ix Geek on 2011-03-18
> **sydbat said:**
> 1) This - after FTFY.Thanks, but it didn't need fixing. ;) My question is if there's a reason the OP wants to *USE* Micro$oft products instead of their native Linux counterparts.
> 2) Windows stuff works better on Windows. You could dual boot or run Windows in a VM if you want / need to run Windows programs.For apps that have native Linux counterparts...why do this? :confused:

---

### Post by Mark Phelps on 2011-03-18
> **TriBlox6432 said:**
> Has anyone gotten this to work flawlessly?  On winehq is says that it's garbage, but has anyone gotten it to work for them?

Apparently not ...

My own experience with Wine (and it's extensions) is that it takes the duration of a full version of MS Office to get the latest one working.  Office 2007 finally worked (with some exceptions) about the time Office 2010 came out.

So, keeping with the same timeline -- it will be 2-3 years before you can expect the same for Office 2010.

---

### Post by beew on 2011-03-18
> **dmn_clown said:**
> Maybe when OpenOffice.org or LibreOffice or BrOffice or Lotus Symphony or whatever clone/fork pops up next month offer full compatibility with MS Office document formats and macros, this argument would be valid.  

The reality is that the majority need compatibility for one reason or other, none of the free applications provide that compatibility.


Most places still use M$ Office 2003 or 2007 so if you want compatibility there is no need for Office2010. There is nothing with perfect compatibility with MS Office formats including different versions of Office. Whose fault is it that other office suits are not compatible with MS?  The compatibility issue is entirely created by MS by design so that it can keep it stranglehold on the market. The problem will disappear if more people switch to other alternatives.

---

### Post by Lateralis on 2011-03-18
For work-related reasons I have a couple of M$ products that I need to use that don't have particularly good Linux counterparts (that I do what I need) or versions of the software for Linux.  For these programmes I use CrossOver as opposed to Wine.  You do have to pay for Crossover, but I don't think it is that expensive to be honest.  Anyway, I run Office 2007 in that nearly flawlessly.  (I have to say though that I am trying to find a way of not using Office 2007 at all, as I actually *hate* that software with such a passion.  I can't think of a worse office suite that has ever been conceived, designed or implemented.)

@ Sydbat

I'm normally doing a lot of different things at once.  Or, better put, when analysing data I'm using a variety of different programmes which each do different things.  I've also written Perl code to help me with this analysis.  Whilst I do have a dual boot it is entirely impractical to switch between the two when I need to make use of a piece of M$ software.  Of course I could VM a Windows desktop, but I don't actually have a copy of Windows... The OP may be in a similar situation.

---

### Post by Vaphell on 2011-03-18
either way VM is the best solution to the problem of 'running linux yet requiring native windows apps' - increased productivity and peace of mind are worth those few bucks you pay for windows copy if you want to be legit.

---

### Post by sandyd on 2011-03-18
office 2010 will not work.

I play around with WINE a lot, so I installed office 2010 in a virtualbox VM, then stuck it back in WINE (from git).

Well, it ran... but huge major blockers came up. Just stick with 2007, and it will work properly.

---

### Post by stmiller on 2011-03-18
Some general info here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

If you get crossover, it helps to install Office 2007 (pre-SP1).

---

### Post by Lateralis on 2011-03-20
@Vaphell

Windows isn't just worth "a few bucks" for a "legit" copy.  And for the amount that I use Windows these days those "few buks" aren't worth it.

---

### Post by brawnypandora0 on 2011-03-23
Why is it that different versions of the same product work differently under Wine? I hear XP Office runs well.

---

### Post by Isaacgallegos on 2011-03-24
Fact: Windows Office 2007 under wine is more stable than Open Office. 
I don't know why, but that's the way it is. All this means is I had to keep saving every few minutes when working in any Open Office app. I don't know about Libre Office, but since I've gotten MS Office 2007 working I have no interest in anything else. 

Crash rate for Open office was about once for every hour. 

Windows Office 2007 under wine has yet to crash on me, and I've already done a research paper and some heavy excel use... 

I have the best OS with the best office suite. Life is good.

---

### Post by velt on 2011-05-07
Office 2007 works fine under wine, but as far as i have seen no way to make office 2010 work as good as 2007 on wine. I think there is not a lot of interest to make it work under wine.
Is a shame.

---

### Post by krapp on 2011-05-07
> **Isaacgallegos said:**
> Fact: Windows Office 2007 under wine is more stable than Open Office. 
I don't know why, but that's the way it is. All this means is I had to keep saving every few minutes when working in any Open Office app. I don't know about Libre Office, but since I've gotten MS Office 2007 working I have no interest in anything else. 

Crash rate for Open office was about once for every hour. 

Windows Office 2007 under wine has yet to crash on me, and I've already done a research paper and some heavy excel use... 

I have the best OS with the best office suite. Life is good.

Good stuff! I know Vista was a disaster despite the billions put into it, but Office has that many more years and $$$ going for it, so you kinda expect it to be the best.

(Patiently waiting for a better FLOSS alternative.)

---

