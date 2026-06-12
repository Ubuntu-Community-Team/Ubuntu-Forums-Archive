---
title: "Trying to fix up a friend's computer, having an odd IE problem."
date: 2007-05-09
forum: Windows
---

### Post by sunexplodes on 2007-05-09
I'm trying to rid my friend's computer of spyware and get it running the stuff she wants, but I've run into a wall. She wants to keep using Windows, and I've convinced her of the value of Firefox over IE, which should minimize the spyware problem. BUT

Internet Explorer 7 will not allow me to download any software. It browses just fine, but as soon as I click a download link, the download dialog appears, hangs, and eventually aborts with a "cannot connect" error. Similarly, it will not allow me to install Adobe Flash. 

Any suggestions?

---

### Post by steven8 on 2007-05-09
Download Firefox on your computer, burn it to a disk, and install it on her computer.  I had to do that with a fella's computer once, because I couldn't get rid of the nasty BHO that was goofing up IE.

---

### Post by Sef on 2007-05-09
It could be in the permission settings.   I think it is under Tools > Options.  It may be set so high that you can't download anything.  I have had the same problem with Windows before and that is how I resolved it.

---

### Post by sunexplodes on 2007-05-09
> **steven8 said:**
> Download Firefox on your computer, burn it to a disk, and install it on her computer.  I had to do that with a fella's computer once, because I couldn't get rid of the nasty BHO that was goofing up IE.

That is definitely on the agenda, but I'd like to figure out how to fix the problem with IE, because she uses outlook express for her email, and the two are tied together. 

> **Sef said:**
> It could be in the permission settings.   I think it is under Tools > Options.  It may be set so high that you can't download anything.  I have had the same problem with Windows before and that is how I resolved it.

I had a look in there, and found some stuff that seemed a little too tight, but it didn't seem to do the trick. The weird thing is, I don't think anything is DISABLED, per se, because IE *tries* to download things, but fails, as opposed to just prohibiting those downloads.

---

### Post by bikeboy on 2007-05-09
Hmm, maybe you could try the ftp download of Firefox on there.

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest-2.0/win32/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest-2.0/win32/)

Obviously doesn't help with normal downloads, but would be interesting to see if it works with ftp but not http.

---

### Post by fourthdimension on 2007-05-09
Never underestimate the obvious malware scans with multiple scanners (Ad-aware SE Personal Edition and Spybot S&D are two free ones that work very well together).
You could also reinstall the browser from the sys disk.

---

### Post by hobieone on 2007-05-09
are we talking ei 7 and is it on xp or vista? i encountered a similar issue on a vista machine and it would give that same error if trying to dowload a program that vista deems as possible harmfull or if the program was not approved by ms  to pass it content protection scheme  onaccount it can't tell if it actually spyware or comming from a place it should n't be. and the whole thing tends to be over jealous about it. 
if it with xp  thaen probly something infecting ie. i read something not long ago about a malware that would  infect ie  and preventit from doing normal tasks

---

### Post by aysiu on 2007-05-09
> **sunexplodes said:**
> That is definitely on the agenda, but I'd like to figure out how to fix the problem with IE, because she uses outlook express for her email, and the two are tied together.  No chance of switching her to Thunderbird? It'd be an easy sell: "See? Outlook Express... doesn't work. Thunderbird... works!"

---

### Post by sunexplodes on 2007-05-10
Yeah, she's pretty set in her ways. 

Anyway, in answer to the above inquiries:

- spybot search & destroy found next to nothing, i'm going to take ad-aware over next time i go to her house, so we'll give that a shot.

- the default firefox download from getfirefox.com is an ftp server, so that's a no-go

- it's IE7 on XP, it's not a security thing, the downloads are failing on an error connecting. 

I'm pretty sure it's a spyware thing. I'll try ad-aware next time i'm there, but if anyone has additional advice, i'm all ears. thanks.

---

### Post by Tyrax on 2007-05-11
Try running internet explorer in No Add-ons mode. Its similar to the 'Safe Mode' in Fx so absolutely no bhos, toolbars, or ActiveX controls like java and flash will load. It's in Programs->Accesories->System Tools.

Does this occur with all downloads or just one particular program.

---

