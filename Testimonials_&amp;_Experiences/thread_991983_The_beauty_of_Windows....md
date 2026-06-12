---
title: "The beauty of Windows..."
date: 2008-11-24
forum: Testimonials &amp; Experiences
---

### Post by Silent Warrior on 2008-11-24
:popcorn: Brace yourselves - this is hilarious, in a dark and, admittedly, not very funny way.

I'm presently writing from my mother's laptop. What can I say - I'm not even on the same continental-plate as my own desktop-monster(s), and I don't own a laptop. Anyway, my mother is a kind, caring, and, above all, law-abiding citizen. She "acquired" this laptop because of some government-initiative to spread computer-competence to one and all - some might need it in their work. (You should really label this as a lease, though. I won't bother to explain it in-depth - if you're a Swede, you know; if not, you don't need to.)
This laptop is a HP Pavilion dv1000, with WinXP Home (32) preinstalled. Now, my mother would much rather poke around in the garden instead of sitting at the computer, and as such rarely even runs Windows Update. No, what she uses this computer for is e-mail, occasional information-gathering on the internet, word-processing, storing her digital pictures, all protected by Norton Internet Security 2003 - exactly what Microsoft wants you to do. No monkey-business.
(Hey, don't worry, I replaced that with Avast and Comodo and gained nearly a minute on a cold boot. That, and much prettier UIs.)
Now comes the fun part. Me being... a bit more into pushing random buttons than mummy is, I ended up installing SP3, .Net-SPs, droves of security-fixes and whatnot, but met my nemesis with... IE7.
:guitar:
This is a really effin' spooky problem. IE6 came with the OS, and I just felt sorry for this little laptop. I mean, it even has a pretty nice soundcard - once you plug something in that can actually produce something more than the acrid hisses the built-in speakers provide, that is. It shouldn't have to suffer IE6, right?
The problem with installing IE7 appears to be that it can't update the registry properly - error 1013, the log says. (%windir%\ie7_main.log)

What do we have here, gents (and fine wenches?)? An OEM-computer, no monkey-business, built with Windows in mind from day one (I hope...) and powered accordingly, I don't think she ever updated the graphics-drivers*, and a freak error occurs that I've never seen before, myself or otherwise reported, halting installation of a MICROSOFT product on a MICROSOFT OS.

A virus-scan turns up nothing (sweeping with Avast at the time of writing, though), there doesn't seem to be any malware worse than NIS (I just want to say that I have no ill feelings to that software at all - it just bogs down the boot something fierce) or Outlook, no eccentricities discovered that might be related to failing hardware.
Having bounced this issue back and forth with HP, I've discovered two ways to scan the registry - one SubinAcl.exe and some other built-in scanner - and found 13 reported errors, though I never received an output as to which actual entries weren't right.
I've tried installing with and without SP3, admin or failsafe mode, with and without AV and firewall, with and without net-current - nothing. I even tried manually hacking the registry, deleting anything that looked like it belonged to IE - and found one that was vital for internet-connectivity. Back-ups are nice, aren't they?

Conclusion: LINUX, I LOVE YOU! (And Firefox 3 rules!)

That said, if anyone knows how to actually get IE7 installed on my mother's machine, I'm all ears. It just kinda sucks that my internet-bank only works on IE... If they move beyond IE6-compatibility any time soon, I'm screwed left, right and centre.

* All I know for sure is that the outdated driver on Intel's site (for Intel 915GM) is a notable jump in version-numbering ahead of the older driver, and works much better...

---

### Post by oilchangeguy on 2008-11-24
you might have better luck here:
[http://www.microsoft.com/windowsxp/expertzone/default.mspx](http://www.microsoft.com/windowsxp/expertzone/default.mspx)

---

### Post by CatKiller on 2008-11-24
> **Silent Warrior said:**
> That said, if anyone knows how to actually get IE7 installed on my mother's machine, I'm all ears. It just kinda sucks that my internet-bank only works on IE... If they move beyond IE6-compatibility any time soon, I'm screwed left, right and centre.

There is a script that installs IE in Wine. It seemed to work fine when my other half installed it quite some time ago for an IE-only site. She stopped visiting the site fairly shortly afterwards for other reasons, and she's on a new computer now and never uses IE, but for the short time she was using it, it worked.

Perhaps it would work for your needs, and perhaps your mum would be just as fine with Xubuntu. I know mine is :)

---

### Post by Silent Warrior on 2008-11-25
oilchangeguy: Thanks, I never knew that place existed. Now to see if I get something useful out of it.

CatKiller: I like the sound of that! But I think I'll try it on my own computer first.

Another thing about MS... I don't suppose anyone here has noticed that they charge you about $100 just to ASK? Open-Source r teh win.

---

### Post by scouser73 on 2008-11-25
>  Brace yourselves - this is hilarious, in a dark and, admittedly, not very funny way.

I'm presently writing from my mother's laptop. What can I say - I'm not even on the same continental-plate as my own desktop-monster(s), and I don't own a laptop. Anyway, my mother is a kind, caring, and, above all, law-abiding citizen. She "acquired" this laptop because of some government-initiative to spread computer-competence to one and all - some might need it in their work. (You should really label this as a lease, though. I won't bother to explain it in-depth - if you're a Swede, you know; if not, you don't need to.)
This laptop is a HP Pavilion dv1000, with WinXP Home (32) preinstalled. Now, my mother would much rather poke around in the garden instead of sitting at the computer, and as such rarely even runs Windows Update. No, what she uses this computer for is e-mail, occasional information-gathering on the internet, word-processing, storing her digital pictures, all protected by Norton Internet Security 2003 - exactly what Microsoft wants you to do. No monkey-business.
(Hey, don't worry, I replaced that with Avast and Comodo and gained nearly a minute on a cold boot. That, and much prettier UIs.)
Now comes the fun part. Me being... a bit more into pushing random buttons than mummy is, I ended up installing SP3, .Net-SPs, droves of security-fixes and whatnot, but met my nemesis with... IE7.

This is a really effin' spooky problem. IE6 came with the OS, and I just felt sorry for this little laptop. I mean, it even has a pretty nice soundcard - once you plug something in that can actually produce something more than the acrid hisses the built-in speakers provide, that is. It shouldn't have to suffer IE6, right?
The problem with installing IE7 appears to be that it can't update the registry properly - error 1013, the log says. (%windir%\ie7_main.log)

What do we have here, gents (and fine wenches?)? An OEM-computer, no monkey-business, built with Windows in mind from day one (I hope...) and powered accordingly, I don't think she ever updated the graphics-drivers*, and a freak error occurs that I've never seen before, myself or otherwise reported, halting installation of a MICROSOFT product on a MICROSOFT OS.

A virus-scan turns up nothing (sweeping with Avast at the time of writing, though), there doesn't seem to be any malware worse than NIS (I just want to say that I have no ill feelings to that software at all - it just bogs down the boot something fierce) or Outlook, no eccentricities discovered that might be related to failing hardware.
Having bounced this issue back and forth with HP, I've discovered two ways to scan the registry - one SubinAcl.exe and some other built-in scanner - and found 13 reported errors, though I never received an output as to which actual entries weren't right.
I've tried installing with and without SP3, admin or failsafe mode, with and without AV and firewall, with and without net-current - nothing. I even tried manually hacking the registry, deleting anything that looked like it belonged to IE - and found one that was vital for internet-connectivity. Back-ups are nice, aren't they?

Conclusion: LINUX, I LOVE YOU! (And Firefox 3 rules!)

That said, if anyone knows how to actually get IE7 installed on my mother's machine, I'm all ears. It just kinda sucks that my internet-bank only works on IE... If they move beyond IE6-compatibility any time soon, I'm screwed left, right and centre.

* All I know for sure is that the outdated driver on Intel's site (for Intel 915GM) is a notable jump in version-numbering ahead of the older driver, and works much better...


That speaks an awful lot about why people are making the transition from Microsoft and why people should be aware of their choices in relation to different operating systems and browsers alike. 

As for Microsoft charging $100 for a solution, that in itself is abysmal, and yet I would like to bet that if a similar problem had been found on an Ubuntu machine the user would know about the forums such as these where help and a quick answer is just a few words away.

Thank god for the open source community, Mark Shuttleworth, Canonical and the people that run this forum, and people posting answers because I for one wouldn't know what to do if this resource wasn't here. Also I'm glad there is Ubuntu.

---

### Post by kostkon on 2008-11-25
> **Silent Warrior said:**
> CatKiller: I like the sound of that! But I think I'll try it on my own computer first.
Yes, it's the [*ies4linux*]("http://www.tatanka.com.br/ies4linux/page/Main_Page") script. And [here a nice how-to]("http://www.psychocats.net/ubuntu/ies4linux") in case you need it.

---

### Post by sandy8925 on 2008-11-25
I find Ubuntu to be more user friendly than Windows.

---

### Post by Silent Warrior on 2008-11-26
I dunno, Ubuntu IS significantly more difficult to bring irreparable harm to... :)

---

### Post by Geekkit on 2008-11-26
> **sandy8925 said:**
> I find Ubuntu to be more user friendly than Windows.

+1, these forums also help tremendously.

---

### Post by wolfen69 on 2008-11-26
> **Silent Warrior said:**
> I dunno, Ubuntu IS significantly more difficult to bring irreparable harm to... :)

not just ubuntu, but many distros. ;)

---

### Post by ComputerHermit on 2008-11-26
> **sandy8925 said:**
> I find Ubuntu to be more user friendly than Windows.

me 2 I went through two dv1000's nice laptop in fact I'm useing the wifi card out of one of them in my new shiny toshiba j/k its like the dv1000 but the wifi cardin the dv is very good ipw2200 my 2 dv1000 pooped out ho well any way Linux ubuntu and mint ran great out of the box and the new kernel seems better ;p

---

### Post by Wally_dog on 2008-11-26
Yeap... I love when Windows decided it doesn't want to update itself anymore and refuses to validate itself, even when it is an install that was installed by Dell, haha. One of the main reasons I switched to ubuntu... it never refuses updates, doesn't cost you a fortune to contact support for something the OS did to itself, and it doesn't become decrepit after a few weeks. I installed Windows XP in a dual-boot. The first day, Windows booted ridiculously fast. I was on the internet within about 15 seconds of pressing power. A week or two later, 45 seconds passes and I'm just getting on. Wanna know why Windows got slower? I would too, because it doesn't have anything installed, and all it is used for is Xbox LIVE. If only it was easy to use Xbox LIVE with Ubuntu, then I could become Microsoft-independent.

---

### Post by Izek on 2008-11-26
> **scouser73 said:**
> As for Microsoft charging $100 for a solution, that in itself is abysmal, and yet I would like to bet that if a similar problem had been found on an Ubuntu machine the user would know about the forums such as these where help and a quick answer is just a few words away.

That depends on how you convey your data. Sometimes I have luck on these forums, sometimes I don't. Anyway, you're right about that charging for support, outrageous!

---

### Post by seanlano on 2008-11-26
> **Wally_dog said:**
> Wanna know why Windows got slower? I would too, because it doesn't have anything installed, and all it is used for is Xbox LIVE. If only it was easy to use Xbox LIVE with Ubuntu, then I could become Microsoft-independent.

:lolflag: you realise that Microsoft make Xbox's? 

I have one also, the only reason was because MS trapped Bungie into only releasing the Halo trilogy on Xbox. Bastards. Otherwise I would have gone PS3, they actually make it easy to install linux on it! I haven't tried it, but Microsoft would certainly never do it. I'm thinking of changing, but I **really** like Halo 3. 

You know what would be awesome? WINE for Xbox games! Yeah, dream on...

---

