---
title: "if windows applications can run on linux why not mac ?"
date: 2009-05-27
forum: The Cafe
---

### Post by ctrlmd on 2009-05-27
Wine made windows application possible to run under linux environment why can't MAC 
application run on linux ?  

i mean windows is a different environment and mac is closer to linux environment why can't their applications run on linux

---

### Post by ricardofilipemoreira on 2009-05-27
basically no one has made it possible. wine didn't just appear as a miracle. people made it. maybe someone will soon make some software to run mac applications on linux too. but for now we'll all have to wait.;)

---

### Post by ctrlmd on 2009-05-27
> **ricardofilipemoreira said:**
> basically no one has made it possible._ [COLOR=Blue]**wine didn't just appear as a miracle. people made it**[/COLOR]_[COLOR=Blue]**.**[/COLOR] maybe someone will soon make some software to run mac applications on linux too. but for now we'll all have to wait.;)

OMG really someone made wine ? :shock:

i thought i came out from the sky #-o

anyway 

what i mean is that mac has a decent applications out there. wish some alien i mean wish someone could design some application to allow mac app to work on linux 

thx 4 sharing your thoughts :-\"

---

### Post by jonian_g on 2009-05-27
I've read somewhere that making mac apps run on linux is as dificult as making windows apps.

Everything that is proprietary is dificult to make it run on linux cause it has to be done through reverse engineering.

---

### Post by suitedaces on 2009-05-27
I would imagine it's a fairly simple case of demand. There's a bigger demand to run Windows programs, so more resources dedicated to it.

---

### Post by aeiah on 2009-05-27
there's less market for it. there simply aren't many mac only applications that would be useful to most people, and the ones that are are likely to be massive audio or video suites and such that need to work perfectly.

plus apple would send the lawyers in far quicker than microsoft because apple only software is usually software owned by apple themselves.

---

### Post by kamitsukai on 2009-05-27
> **aeiah said:**
> there's less market for it. there simply aren't many mac only applications that would be useful to most people, and the ones that are are likely to be massive audio or video suites and such that need to work perfectly.

plus apple would send the lawyers in far quicker than microsoft because apple only software is usually software owned by apple themselves.

What would they sure for? the current wine isn't illegal so why would one for mac applications be?

---

### Post by jespdj on 2009-05-27
> **kamitsukai said:**
> What would they sure for? the current wine isn't illegal so why would one for mac applications be?
For now, Microsoft has not taken any action against WINE, but it remains to be seen whether there are legal issues with it or not.

Microsoft does not allow reverse engineering Windows, so if they could prove that WINE was made by using knowledge gained through reverse engineering Windows, they could have a legal case against WINE. But proving that would be really hard.

---

### Post by Skripka on 2009-05-27
Because it is illegal.

The OSX API is proprietary and strictly locked down, and they have no qualms of suing tiny operations.  It will NEVER happen.

PS-OSX is FAR from being Linux, they are barely 2nd cousins.

---

### Post by happysmileman on 2009-05-27
The way i see it, it would take the same amount of effort to get Mac apps to run as it would to get Windows apps to run, and no-one wants Mac apps enough. There's very few applications that are Mac-only, and not enough to merit the effort.

---

### Post by Skripka on 2009-05-27
> **happysmileman said:**
> The way i see it, it would take the same amount of effort to get Mac apps to run as it would to get Windows apps to run, and no-one wants Mac apps enough. There's very few applications that are Mac-only, and not enough to merit the effort.

The Cocoa and Carbon libraries are not open source.  It will never happen-effort is irrelevant.


There is also no point.  How many apps are written for OSX only, and not Windows?

---

### Post by jelle_ on 2009-05-27
I think making a clone of the few mac-applications people need is a much better idea than an emulator.

---

### Post by praveesh on 2009-05-27
Windows' applications requires windows api for their functionality . What the wine developers does is recreating such api s . Also calls to some windows APIs are redirected to linux API . If some one wants to create emulator for osx, they will need to recreate the osx APIs which is as difficult as creating wine.

---

### Post by mamamia88 on 2009-05-27
my bad

---

### Post by aeiah on 2009-05-27
> **kamitsukai said:**
> What would they sure for? the current wine isn't illegal so why would one for mac applications be?

exclusive mac applications are usually exclusive because they are owned by a subsidiary of apple. a lot of the pro media software that's mac only is that way because apple bought the company that made it to block it from being multiplatform. i suspect in the EULAs and such that the software says 'for use only on os x' etc. they seem much more likely to bring charges against people than other big software vendors. apple is a fairly protective and restrictive company even by microsoft's standards.

---

### Post by mamamia88 on 2009-05-27
no offense but is there any partiticular mac software that you want to run that you can't find a equal or better equivelent for windows or linux?  seriously windows has 90% marketshare or so i'm sure there are at least 2 applications that can do the job as good as mac software for every one on mac

---

### Post by Xbehave on 2009-05-27
> **praveesh said:**
> Windows' applications requires windows api for their functionality . What the wine developers does is recreating such api s . Also calls to some windows APIs are redirected to linux API .
AFAIK almost all API  calls are redirected to the relevent linux API thats why you don't get the preformance hit of emulating when you run wine, just the hit of an extra api call per api call.
>  If some one wants to create emulator for osx, they will need to recreate the osx APIs which is as difficult as creating wine.
Mac os X has 4 Api's "These APIs have some overlapping and some exclusive capabilities; as the functionality of Mac OS X changes they have not been kept in sync."
POSIX & java (both usable in Linux)
cocoa ( GNUstep & cocotron both implement much of this API)
Carbon (no other implementation AFAIK, but it is under maintained by apple so hopefully used less)
AFAIK programs using only java/posix calls can run in linux with no recompilation necessary, but those using cocoa will need a recompilation.
So while creating "[Apfelwein]("http://en.wikipedia.org/wiki/Apfelwein")" would be hard, it would be much easier than wine.

> For now, Microsoft has not taken any action against WINE, but it remains to be seen whether there are legal issues with it or not.No it doesn't Reverse enginiering is protected by [legal president]("http://en.wikipedia.org/wiki/Clean_room_design#Case_law"), Microsoft could at worse use [software patents]("http://en.wikipedia.org/wiki/Software_patents"), however much of the world is exempt from software patents and so wine could still be developed and used most places outside the us

---

### Post by aysiu on 2009-05-27
I'm confused about what the question is.

If the question is why doesn't Wine exist on Mac to run Windows programs, the answer is "It actually does." I tried to use Wine on a Mac to install IEs4Linux once, and it failed. Worked fine on Linux, though. Maybe the Wine version for the Mac is older?

If the question is why isn't there something like Wine to run Mac-native programs on Linux, the answer is "No one has made it." The fact that no one has made it means there probably is very little interest in it.

If you want to try to make it, go for it... or pay someone else to do it.

---

### Post by Xbehave on 2009-05-27
> **aeiah said:**
> I suspect in the EULAs and such that the software says 'for use only on os x' etc. they seem much more likely to bring charges against people than other big software vendors. Fortunately a way of running apple software on linux would only enable users to break the EULA, but as there would be legit use due to many non-apple products (e.g [camino]("http://en.wikipedia.org/wiki/Camino")) and it doesn't apply to apples big 2 (itunes & safari) anyway. While users would be open to litigation EULAs are often not [legally binding]("http://en.wikipedia.org/wiki/EULA#Enforceability").

---

