---
title: "Two hours with Oneiric: a total disaster"
date: 2011-10-14
forum: Testimonials &amp; Experiences
---

### Post by 08gr10 on 2011-10-14
Over the last 15 years I tried every now and then a Linux distro to see if it was mature enough to replace Windows. It wasn't for me, until I tried Ubuntu 11.04 last summer. I was highly impressed by it's stability, clean interface and effectiveness. So I was looking forward to 11.10. What a disappointment! It is just not workable! 
There seem to have been several alpha and beta releases before the final release. What did those testers do when I &#8211; a simple novice user &#8211; see crashes all over the place? Below is the list of issues I encountered the first two hours using Oneiric; note that these issues are **not **present in Natty!

What makes it a disaster:
[LIST]
[*]Installation of Ubuntu with wireless update enabled did **freeze** (at least I perceived it as a freeze since 10 minutes later it still didn't proceed to the next menu).
[*]After installation without auto-update a Broadcom propriety driver was found. Installation (i.e. activation) **failed**.
[*]I downloaded Chrome. When I double-clicked on the .deb file SW Center reports: **Failed **to open chrome.deb. Wth? Finally I got it installed by right-clicking and select 'open with SW center'.
[*]The cooling fan of my HP Probook runs on high speed all the time; annoying and likely decreasing battery life.
[*]Some external SW **failed **to install. Eg. Syspeek. 
[*]Cut/paste a file from desktop to a network share **crashed **Nautilus.
[*]Running Windows applications with wine is **totally messed up**. Windows menu's aren't working, sometimes menu's are visible at the upper left corner of the desktop, clicking on a tab moves the app to the other side of my desktop, etc.
[*]Installing Autokey did **freeze **most of the desktop. After some struggling I managed to logout and login again after which I ended up in a **corrupt **LibreOffice document.
[*]LO recognized that the document was corrupt. However, Recovery **failed**. Great! The 'Press next for error report system' failed to show any reporting system (not sure if this would work in Natty since I never had corrupted files in Natty).
[*]Nautilus **crashed **all over the time, it doesn't survive browsing with approx. more than 3 clicks. Starting another instance crashes it too.
[*]I lost even more LO documents that got **corrupted **when I was forced to logout and logon.
[/LIST]

What is annoying:
[LIST]
[*]The Microsoft way of converting a quote+character into a special character is enabled by default. I just want to insert a quote (') with a single keypress!
[*]It takes 4 attempts to connect to my Windows share before it actually connects (note: it needs to be waked up by the network from standby). Natty did it consequently in 2 times.
[*]System settings: where are all the advanced settings?
[*]For some reason, the left mouse button gets occasionally disabled and the right button gets partly the functionality of the left button. A bit hard to explain, but highly annoying, it makes Ubuntu totally unworkable which I only get repaired by logout and login again. To be honest I also have this occasionally in Natty, it's just a pity it's not solved in Oneiric. I also do not know yet what event/action does cause this 'mode'.
[/LIST]

What I liked:
[LIST]
[*]Fast
[*]Alt-Tab functionality.
[*]Bookmarks in Nautilus (also for network shares).
[/LIST]

Maybe Natty was as buggy as Oneiric when it was released in April. Maybe I was lucky to start using Natty a few months later when most bugs were fixed. 
I know one thing for sure: when I tried Natty and it would have been as buggy as Oneiric is now, I would have laughed pityingly and returned to Windows within a few minutes. Since I have good experiences with Natty I might try Oneiric again in a few months.
What I don't understand is why Canonical is provoking its user base with such a buggy release. The move to Unity was already controversial so I'd be more caring about my user base before they move to another distro or, in my case, even back to Windows.

---

### Post by beew on 2011-10-14
> Maybe Natty was as buggy as Oneiric when it was released in April.Actually it was much, much worse. Will take a month or so for the bugs to clean up,--and Natty took longer too,-- but this is definitely a more solid release than Natty was when it came out.

---

### Post by egkeat on 2011-10-14
This always seems happen. I started out using 8.10 and ever since has been a sort of love/hate experience. Now I'm using 11.10 + Gnome 3 and love it (dual boot Windows). If it holds up, I might just stick with Ubuntu from here on.

---

### Post by 3rdalbum on 2011-10-15
> **08gr10 said:**
> 
There seem to have been several alpha and beta releases before the final release. What did those testers do when I &#8211; a simple novice user &#8211; see crashes all over the place?

What makes it a disaster:
[LIST]
[*]Installation of Ubuntu with wireless update enabled did **freeze** (at least I perceived it as a freeze since 10 minutes later it still didn't proceed to the next menu).

I'll answer you question of "what did those testers do". First bug: Didn't observe it.

> [*]After installation without auto-update a Broadcom propriety driver was found. Installation (i.e. activation) **failed**.

I don't use Broadcom devices so there's no way I could discover this problem.

> [*]I downloaded Chrome. When I double-clicked on the .deb file SW Center reports: **Failed **to open chrome.deb. Wth? Finally I got it installed by right-clicking and select 'open with SW center'.

Didn't run into this one either; in fact I think all my offline Debian package installs worked fine by double-clicking them. There's no way I can report a bug I had no knowledge of.

> [*]The cooling fan of my HP Probook runs on high speed all the time; annoying and likely decreasing battery life.
[*]Some external SW **failed **to install. Eg. Syspeek. 

I don't have one and I don't use this software. Sounds interesting though, I might check out Syspeek.

> [*]Cut/paste a file from desktop to a network share **crashed **Nautilus.

Not observed here. I don't generally CUT files, especially across a network. It always makes me paranoid that the original file will disappear before it's been fully pasted to the network location.

> [*]Running Windows applications with wine is **totally messed up**. Windows menu's aren't working, sometimes menu's are visible at the upper left corner of the desktop, clicking on a tab moves the app to the other side of my desktop, etc.
[*]Installing Autokey did **freeze **most of the desktop. After some struggling I managed to logout and login again after which I ended up in a **corrupt **LibreOffice document.

Don't use either of these software.

> 
[*]Nautilus **crashed **all over the time, it doesn't survive browsing with approx. more than 3 clicks. Starting another instance crashes it too.

Sounds like what is a known bug, that should have been fixed already. If you have installed nautilus-open-terminal, try removing it. I observed it and "me too"'ed the bug report.

> [*]It takes 4 attempts to connect to my Windows share before it actually connects (note: it needs to be waked up by the network from standby). Natty did it consequently in 2 times.

I don't use Wake On Lan for my server, so I didn't observe this.

> [*]System settings: where are all the advanced settings?

Gnome 3's developers have simplified the settings panels. The non-Ubuntu-specific ones are missing some features, presumably by design. This isn't Ubuntu's fault. If you ask on here about specific features, there might be some that have merely moved or are replaceable with other software.

> [*]For some reason, the left mouse button gets occasionally disabled and the right button gets partly the functionality of the left button. A bit hard to explain, but highly annoying, it makes Ubuntu totally unworkable which I only get repaired by logout and login again.

Not observed here. Never even heard of it, actually.

> To be honest I also have this occasionally in Natty, it's just a pity it's not solved in Oneiric.

It might have been helpful if you had filed a bug report in Natty, but then sometimes it's difficult to do when it's an intermittant fault, so I understand why you didn't. Since it happens more frequently on Oneiric for you, try reporting it. While this problem is happening, go to the terminal and type:

```
ps aux | grep "unity"
```

The four/five-digit number in the second column is the "process ID". You want to put it into the next command:

```
ubuntu-bug (process-id)

For example:
ubuntu-bug 4571
```

This allows you to describe your bug, search whether it's been filed already, and if not you can fill out a bug report. It will automatically attach relevant information to the bug report.

If you can, I'd appreciate it if you could install 12.04 when it reaches Alpha 3. Report all the bugs you can, especially the ones that have affected you in 11.10. It's only through the efforts of you and me that we stamp out bugs in Ubuntu; without us, the developers only see the bugs that personally affect them.

---

### Post by 1roxtar on 2011-10-15
"Total Disaster"  is such an exaggeration.  I have 11.1.0 installed on five of my computers, from a 4 yr old IBM Thinkpad, two Toshiba Satellites (single core cpu), an Alienware desktop (dual core), and a Dell Inspiron desktop (dual core).  Each are running flawlesly with no crashes and I for one LOVE Unity.  My IBM thinkpad fell back to the Unity 2D mode, but even that is making my older laptop run very snappy.

I have been using 11.10 since the Alpha versions and of course during the development I filed many bugs, but since it's final landing it has proven to be very stable. It's ridiculous to state that just because it didn't work well with YOUR hardware, it was a total failure.

---

### Post by dniMretsaM on 2011-10-15
OP, you need to take a chill pill. Just because it didn't work for you, doesn't mean it was a "total disaster." And no offense, but it's kind of your fault for upgrading off the bat. If you're not willing to deal with problems, stay with an LTS release or at least wait a few months for the a lot of the bugs in the new release to be ironed out.

> **1roxtar said:**
> It's ridiculous to state that just because it didn't work well with YOUR hardware, it was a total failure.

Wow! Someone with sense! Very refreshing.

---

### Post by slooksterpsv on 2011-10-15
08gr10 - I just wanted to say thank you for your feedback. It helps to know what issues others are experiencing. If you need complete stability, I would recommend 10.04, as the next LTS is going to be released in April (3 years for LTS I believe, 5 for server LTS).

With 11.10 I have music apps crashing all the time such as Banshee and Exaile - Exaile has been stable when started from Gnome Terminal, but otherwise it's not functioning when ran from Unity.

Software Center has been crashing a lot too. If you find an issue is constant crashing, I would suggest either filing a bug or checking to see if there's one that's already been reported. Remember, there will be patches and updates for 11.10 for the next 6 months at least (not sure if it goes past that) so there are some stability issues there.

---

### Post by lancest on 2011-10-15
Operating systems when first introduced are liable to need some tweaking. 

Music apps- Google Music for me. 

Windows 7 used to crash certain applications alot when first introduced.
Still does. 
(Try Adobe X- in note edit mode)

---

### Post by Gatemaze on 2011-10-16
> **08gr10 said:**
> Over the last 15 years I tried every now and then a Linux distro to see if it was mature enough to replace Windows. It wasn't for me, until I tried Ubuntu 11.04 last summer. I was highly impressed by it's stability, clean interface and effectiveness. So I was looking forward to 11.10. What a disappointment! It is just not workable! 
There seem to have been several alpha and beta releases before the final release. What did those testers do when I &#8211; a simple novice user &#8211; see crashes all over the place? Below is the list of issues I encountered the first two hours using Oneiric; note that these issues are **not **present in Natty!

Use 10.04 which is a long term release and much more stable and tested. And yes unless you are willing to live with few bugs better wait a month or two before upgrading to a new release. At least it is a month or two and not a whole new operating system, referring to millenium->xp, vista->7

---

### Post by xx58 on 2011-10-16
> **08gr10 said:**
> Over the last 15 years I tried every now and then a Linux distro to see if it was mature enough to replace Windows. It wasn't for me, until I tried Ubuntu 11.04 last summer. I was highly impressed by it's stability, clean interface and effectiveness. So I was looking forward to 11.10. What a disappointment! It is just not workable! 
There seem to have been several alpha and beta releases before the final release. What did those testers do when I &#8211; a simple novice user &#8211; see crashes all over the place? Below is the list of issues I encountered the first two hours using Oneiric; note that these issues are **not **present in Natty!

What makes it a disaster:
[LIST]
[*]Installation of Ubuntu with wireless update enabled did **freeze** (at least I perceived it as a freeze since 10 minutes later it still didn't proceed to the next menu).
[*]After installation without auto-update a Broadcom propriety driver was found. Installation (i.e. activation) **failed**.
[*]I downloaded Chrome. When I double-clicked on the .deb file SW Center reports: **Failed **to open chrome.deb. Wth? Finally I got it installed by right-clicking and select 'open with SW center'.
[*]The cooling fan of my HP Probook runs on high speed all the time; annoying and likely decreasing battery life.
[*]Some external SW **failed **to install. Eg. Syspeek.
[*]Cut/paste a file from desktop to a network share **crashed **Nautilus.
[*]Running Windows applications with wine is **totally messed up**. Windows menu's aren't working, sometimes menu's are visible at the upper left corner of the desktop, clicking on a tab moves the app to the other side of my desktop, etc.
[*]Installing Autokey did **freeze **most of the desktop. After some struggling I managed to logout and login again after which I ended up in a **corrupt **LibreOffice document.
[*]LO recognized that the document was corrupt. However, Recovery **failed**. Great! The 'Press next for error report system' failed to show any reporting system (not sure if this would work in Natty since I never had corrupted files in Natty).
[*]Nautilus **crashed **all over the time, it doesn't survive browsing with approx. more than 3 clicks. Starting another instance crashes it too.
[*]I lost even more LO documents that got **corrupted **when I was forced to logout and logon.
[/LIST]

What is annoying:
[LIST]
[*]The Microsoft way of converting a quote+character into a special character is enabled by default. I just want to insert a quote (') with a single keypress!
[*]It takes 4 attempts to connect to my Windows share before it actually connects (note: it needs to be waked up by the network from standby). Natty did it consequently in 2 times.
[*]System settings: where are all the advanced settings?
[*]For some reason, the left mouse button gets occasionally disabled and the right button gets partly the functionality of the left button. A bit hard to explain, but highly annoying, it makes Ubuntu totally unworkable which I only get repaired by logout and login again. To be honest I also have this occasionally in Natty, it's just a pity it's not solved in Oneiric. I also do not know yet what event/action does cause this 'mode'.
[/LIST]

What I liked:
[LIST]
[*]Fast
[*]Alt-Tab functionality.
[*]Bookmarks in Nautilus (also for network shares).
[/LIST]

Maybe Natty was as buggy as Oneiric when it was released in April. Maybe I was lucky to start using Natty a few months later when most bugs were fixed. 
I know one thing for sure: when I tried Natty and it would have been as buggy as Oneiric is now, I would have laughed pityingly and returned to Windows within a few minutes. Since I have good experiences with Natty I might try Oneiric again in a few months.
What I don't understand is why Canonical is provoking its user base with such a buggy release. The move to Unity was already controversial so I'd be more caring about my user base before they move to another distro or, in my case, even back to Windows.

Bye and good luck with Microsoft Windows.

---

### Post by armandh on 2011-10-16
Ubuntu's release date is [IMHO] the release to a wider pool of testers.
my first try of 7.04 was a slam dunk in JULY
early adopters [AKA lab rats] be ware
you may be lucky, or not

good luck, best wishes 

and a big THANK-YOU

---

### Post by DeMus on 2011-10-16
> **lancest said:**
> Operating systems when first introduced are liable to need some tweaking. 

Music apps- Google Music for me. 

Windows 7 used to crash certain applications alot when first introduced.
Still does. 
(Try Adobe X- in note edit mode)

Some tweaking you say? The whole thing has to be re-written.

---

### Post by kwildman on 2011-10-16
Google can be your friend...

This was the first update since Intrepid that didnt go 100% smoothly for me.  Chrome wouldnt install from the software center using the .deb file downloaded from the webpage.  Tried to intall using dpkg and it showed several missing dependicies.  Installed them from apt-get repositories and then installed chrome using dpkg.

The fact that Chrome hadnt updated their installer to work smoothly with 11.10 isnt a reflection of Ubuntu since 11.10 ships with firefox by defualt.

---

