---
title: "help removing Microsoft .net framework SP2"
date: 2010-03-12
forum: The Cafe
---

### Post by sudoer541 on 2010-03-12
OK!
I am on Windows xp and I am cleaning my PC.
Here is something weird, on my control panel:




Microsoft .net **2.0** framework SP2
Microsoft .net **3.0** framework SP2

I am trying to remove the old one but its not allowing me, any ideas?

---

### Post by themarker0 on 2010-03-12
What error does it give?

---

### Post by AllRadioisDead on 2010-03-12
You can't remove it. .Net framework installs in layers. The .Net framework 2.0 is Dependant on 1.0, and 3.0 is dependent on 2.0. They are all updates.

---

### Post by Post Monkeh on 2010-03-12
> **sudoer541 said:**
> OK!
I am on Windows xp and I am cleaning my PC.
Here is something weird, on my control panel:




Microsoft .net **2.0** framework SP2
Microsoft .net **3.0** framework SP2

I am trying to remove the old one but its not allowing me, any ideas?

you shouldn't remove it - different programs depend on different versions of .NET

---

### Post by sudoer541 on 2010-03-12
> **themarker0 said:**
> What error does it give?


wow! thanks for the quick reply!:)
here is the error:

---

### Post by Post Monkeh on 2010-03-12
> **ihermit said:**
> You can't remove it. .Net framework installs in layers. The .Net framework 2.0 is Dependant on 1.0, and 3.0 is dependent on 2.0. They are all updates.

not true i don't think

i had to reinstall XP the other day and although i had .NET 3 installed, there was a program i couldn't get to work becuase it needed .NET 1, so i had to install it from the microsoft website.

---

### Post by AllRadioisDead on 2010-03-12
> **Post Monkeh said:**
> not true i don't think

i had to reinstall XP the other day and although i had .NET 3 installed, there was a program i couldn't get to work becuase it needed .NET 1, so i had to install it from the microsoft website.
The error is not letting him remove it because .Net Framework 3.0 is dependent on .Net Framework 2.0.
Not sure why OP ignored my post, but here it is.
[http://support.microsoft.com/kb/829019](http://support.microsoft.com/kb/829019)

---

### Post by Post Monkeh on 2010-03-12
> **ihermit said:**
> The error is not letting him remove it because .Net Framework 3.0 is dependent on .Net Framework 2.0.
Not sure why OP ignored my post, but here it is.
[http://support.microsoft.com/kb/829019](http://support.microsoft.com/kb/829019)

yeah, i think i had 2 & 3 (my disk is xp & sp2), but i had to install 1.

---

### Post by sudoer541 on 2010-03-12
> **ihermit said:**
> The error is not letting him remove it because .Net Framework 3.0 is dependent on .Net Framework 2.0.
Not sure why OP ignored my post, but here it is.
[http://support.microsoft.com/kb/829019](http://support.microsoft.com/kb/829019)

I just realized that I am running an outdated version of .net framework.
The new one is 3.5 and I have 3.0. So now if I install the latest version Can I remove version 2.0 or possibly 3.0? I doubt it. :D

---

### Post by sudoer541 on 2010-03-12
Ok, now this is weird. I d/l  the latest .net framework 3.5 and I run the installer at the end I got a blank error. Can someone explain this to me?

---

### Post by pricetech on 2010-03-12
> **sudoer541 said:**
> wow! thanks for the quick reply!:)
here is the error:

Try following the link in the error message.

You might be able to remove some of the dot net stuff that's been installed, but I don't advise it.  You'll probably break something.

A typical winders reinstall here involves 11 dot net packages of some kind.  I could do it with less, but I prefer to install them locally before visiting MS Update.

Easiest way is to point IE to [http://update.microsoft.com](http://update.microsoft.com) and install the updates from there.  Expect to make more than one trip.

---

### Post by Post Monkeh on 2010-03-12
> **sudoer541 said:**
> I just realized that I am running an outdated version of .net framework.
The new one is 3.5 and I have 3.0. So now if I install the latest version Can I remove version 2.0 or possibly 3.0? I doubt it. :D

no, you need to keep them all.

---

### Post by sudoer541 on 2010-03-12
> **Post Monkeh said:**
> no, you need to keep them all.

aha! I see. I thought I was running an outdated and obsolete version of .net framework and to save some space, I wanted to remove it. 
I guess ill leave it alone cuz I dont want to mess my xp. 


btw I want to do the same thing with quicktime but its not possible to remove quicktime without breaking iTunes 9.0.2.5 right?
I never use quicktime and it takes about 77MB on my hard drive.

EDIT!!: I want to remove internet explorer 6 as well. I have tried to remove it many times but it keeps coming back when someone tries to go to a webpage by typing in the  address bar of explorer.exe  ( in my documents, my computer etc)

---

### Post by pricetech on 2010-03-12
> **sudoer541 said:**
> btw I want to do the same thing with quicktime but its not possible to remove quicktime without breaking iTunes 9.0.2.5 right?
I never use quicktime and it takes about 77MB on my hard drive.

I'm pretty sure you can remove QT and leave itunes in place.  If nothing else I think apple offers itunes without QT if you check the right box, so worst case scenario should be reinstalling itunes.

> **sudoer541 said:**
> EDIT!!: I want to remove internet explorer 6 as well. I have tried to remove it many times but it keeps coming back when someone tries to go to a webpage by typing in the  address bar of explorer.exe  ( in my documents, my computer etc)

Good luck.  IE is part of the winders OS.  Just update it.

---

### Post by Meep3D on 2010-03-12
> **sudoer541 said:**
> aha! I see. I thought I was running an outdated and obsolete version of .net framework and to save some space, I wanted to remove it. 
I guess ill leave it alone cuz I dont want to mess my xp. 


btw I want to do the same thing with quicktime but its not possible to remove quicktime without breaking iTunes 9.0.2.5 right?
I never use quicktime and it takes about 77MB on my hard drive
Dude, buy a larger hard drive.  If 77mb is non-negligible, I hate to think what you're running.

---

### Post by jrothwell97 on 2010-03-12
> **sudoer541 said:**
> EDIT!!: I want to remove internet explorer 6 as well.

Install IE8. Job done.

> **pricetech said:**
> I'm pretty sure you can remove QT and leave itunes in place.  If nothing else I think apple offers itunes without QT if you check the right box, so worst case scenario should be reinstalling itunes.

Not quite. iTunes depends on QuickTime, not the other way round, so it's possible to install QuickTime without iTunes, but you need QuickTime if you want iTunes.

---

### Post by sudoer541 on 2010-03-12
> **Meep3D said:**
> Dude, buy a larger hard drive.  If 77mb is non-negligible, I hate to think what you're running.

LOL!!! I already have a 80GB hard disk, but I like to get rid of the things I dont use so that xp performs a bit faster. Ok I know a bit weird lol!

---

### Post by koleoptero on 2010-03-12
I recently removed all the .net stuff from my xp install. Can't remember exactly how I did it but it is possible, and it didn't require hocus pocus.

---

### Post by Post Monkeh on 2010-03-12
> **jrothwell97 said:**
> Install IE8. Job done.



Not quite. iTunes depends on QuickTime, not the other way round, so it's **possible** to install QuickTime without iTunes, but you need QuickTime if you want iTunes.

fixed that.

---

### Post by jrothwell97 on 2010-03-12
> **Post Monkeh said:**
> fixed that.

Whoops! Fixed.

Thanks!

---

### Post by pricetech on 2010-03-15
> **jrothwell97 said:**
> Not quite. iTunes depends on QuickTime, not the other way round, so it's possible to install QuickTime without iTunes, but you need QuickTime if you want iTunes.

You are correct.  I was remembering it backward I guess.  It happens when you get old.

---

