---
title: "VISTA ERRORS (that figures...)"
date: 2008-10-12
forum: Windows
---

### Post by Sponzenbroekske on 2008-10-12
Every time I open any program I get the error in the picture.
It says that C:/..... is not for windows or it contains an error. Try reinstalling the program....(unimportant jibberish)

Google wasnt really a help to me, normall it is...

Even when I start up vista I get that error like 7times, REALLY ENOYING!!!

I thaught it was the lexmark driver, but I uninstalled it and yet no result.
I'm no hero in back ups (a)
And I don't like te reinstall my OS every time it gets some weird **** like this.

Its windows vista home premium SP1

---

### Post by fiddledd on 2008-10-12
> **Sponzenbroekske said:**
> Every time I open any program I get the error in the picture.
It says that C:/..... is not for windows or it contains an error. Try reinstalling the program....(unimportant jibberish)

Google wasnt really a help to me, normall it is...

Even when I start up vista I get that error like 7times, REALLY ENOYING!!!

I thaught it was the lexmark driver, but I uninstalled it and yet no result.
I'm no hero in back ups (a)
And I don't like te reinstall my OS every time it gets some weird **** like this.

Its windows vista home premium SP1

I've no idea what "vifirid.dll" is, and you are right, google gives no hits for it.

I would run Windows Defender to see what programs are running at start up, and disable them one at a time and reboot. When you stop getting the error you'll know what was causing it.

BTW, you can disable/enable start up programs from Defender's Tools link.

---

### Post by Sponzenbroekske on 2008-10-12
> **fiddledd said:**
> I've no idea what "vifirid.dll" is, and you are right, google gives no hits for it.

I would run Windows Defender to see what programs are running at start up, and disable them one at a time and reboot. When you stop getting the error you'll know what was causing it.

BTW, you can disable/enable start up programs from Defender's Tools link.

I solved it, must be when you were typing this :)

Hijackthis told me that it had a extreem early startuptime, not many programs use that, but especially TROJANS :s
So I installed killbox but that wasn't the right tool, though Hijackthis told me to do so.

I just went in the register and deleted an entry, poef! solved :D

What entry you must asked yourself

computer/hkey_local_machine/software/microsoft/windows NY/currentversion/windows
and there I deleted APPS_init   vifiride.dll


And thx to Linux I learned to work with windows, else I would have never know the register :D

edit: typos.................

---

### Post by fiddledd on 2008-10-12
> **Sponzenbroekske said:**
> I solved it, must be when you were typing this :)

Hijackthis told me that it had a extreem early startuptime, not many programs use that, but especially TROJANS :s
So I installed killbox but that wasn't the right tool, though Hijackthis told me to do so.

I just went in the register and deleted an entry, poef! solved :D

What entry you must asked yourself

computer/hkey_local_machine/software/microsoft/windows NY/currentversion/windows
and there I deleted APPS_init   vifiride.dll


And thx to Linux I learned to work with windows, else I would have never know the register :D

edit: typos.................

Glad you sorted it.

---

### Post by Giant Speck on 2008-10-13
Windows 7 has a public beta?

---

### Post by Sponzenbroekske on 2008-10-14
> **Giant Speck said:**
> Windows 7 has a public beta?

no not a BETA but you could find some builds, though there not public, but if you look hard enough you will find one, and can I suggest to not use build 6519 cuz that similar to vista and therefor not an awesome expirience.

So look for a build higher then 6519. :)

And also, you could post that in an own thread cuz this one taken ;)

---

### Post by Giant Speck on 2008-10-14
> **Sponzenbroekske said:**
> no not a BETA but you could find some builds, though there not public, but if you look hard enough you will find one, and can I suggest to not use build 6519 cuz that similar to vista and therefor not an awesome expirience.

So look for a build higher then 6519. :)

And also, you could post that in an own thread cuz this one taken ;)

Nah, I wasn't trying to hijack.  I just noticed it in your screenshot and was curious.

---

### Post by Sponzenbroekske on 2008-10-14
> **Giant Speck said:**
> Nah, I wasn't trying to hijack.  I just noticed it in your screenshot and was curious.

cuz u asked for windows 7 and im talking about vista, but oke no problem :D

---

### Post by Giant Speck on 2008-10-14
> **Sponzenbroekske said:**
> cuz u asked for windows 7 and im talking about vista, but oke no problem :D

No.  Look at your screenshot.  I mentioned Windows 7 because I saw the Vuze torrent download bar near the top of your screen.  I didn't think you were actually running Windows 7.

---

### Post by Sponzenbroekske on 2008-10-14
> **Giant Speck said:**
> No.  Look at your screenshot.  I mentioned Windows 7 because I saw the Vuze torrent download bar near the top of your screen.  I didn't think you were actually running Windows 7.

ah yeah, I didn't realize it, but your right I was downloading windows 7 at that moment :)
Now I understand why you picked in.

You're totally right, I'm sorry. :)

---

