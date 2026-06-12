---
title: "Installing Ubuntu CE 3.2 on Fujitsu Lifebook &quot;A&quot; Series"
date: 2007-07-23
forum: Ubuntu Christian Edition
---

### Post by setxdxer on 2007-07-23
I've been trying and trying (without success) to do a complete install of Ubuntu CE 3.2 on a Fujitsu "A" Series Lifebook.  The Windows label on the keyboard says "Designed for Microsoft Windows XP" but the Microsoft certificate of authenticity on the bottom of the notebook says "Microsoft Windows 2000 Professional."

I'm using a distribution CD of CE 3.2 that I purchased, not one that I burned myself.  The Ubuntu CE spash screen appears, then the diagnostic messages begin to scroll up the screen.  After that, I get the cursor positioned in the middle of the screen, and nothing else.  I've waited for as long as 45 minutes, but nothing (except a pretty warm CD!).

I've even gone into the BIOS and changed it to use "Boot from CD" as 1st priority, but no joy.

Is there something wrong with the laptop?  I mean, it says "XP" _and _"Windows 2000 Professional" - could someone have done a "mix & match" number to the unit before/after it was excessed and then donated to me?

Just trying to boot the laptop without the CE 3.2 CD in, I get this weird logon screen asking me for a user name and password, but it's _not _the typical Windows login screen.

I really would like to get this laptop working with CE.  Do I need to obtain a version of CE older than 3.2?

Any help would be **greatly **appreciated!

Thanks!

---

### Post by mysticrider92 on 2007-07-24
Since you get to the Ubuntu login screen and nothing else, my guess is that the laptop might not have enough ram. If you boot into Windows and press the "Start" key + Pause Break, a window should pop up that will list the os version and some information about the computer (I am not completely sure if it works this way in Win 2000 or not). Check the part that says "Computer" (near the bottom) and there will be a part that says ram. 

If this is less than about 256mb, it might not be enough. In this case, you can download and burn a regular Ubuntu alternate install cd and use the Ubuntu CE convert_me script to convert it to CE.

Also, if you can post any error messages you get with the live cd, someone might be able to help you install using that. It could just be a system specific problem, I have heard of those with some IBM/Lenovo laptops and others.

---

### Post by setxdxer on 2007-07-28
mysticrider92,

Thanks for your help!  I'm researching now on how to burn a "regular Ubuntu alternate install" cd.

setxdxer

---

