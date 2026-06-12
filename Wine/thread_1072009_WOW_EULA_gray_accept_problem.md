---
title: "WOW EULA gray accept problem"
date: 2009-02-17
forum: Wine
---

### Post by pdonovan821 on 2009-02-17
Wow Eula gray accept
I'm sure this is a question that's popped up quite a bit, but i can't seem to solve it, and honestly, im almost at the point of just wiping my hard drive completely and going back to windows (which i really dont wanna do).

So here's the deal. I'm trying to install wow, via the installer ( i dont have my original discs, still have the BC and the WOTLK ones ) and I'm having the gray accept problem. I've been trying now for four days to figure this out and I'm literally about to scream. Basically, It loads up (quite beautifully I might add) but when I get to the EULA, it shows gray. I've tried the original, BC, and Wrath installer, all of em give me the same thing. I really am at a loss here.

I've tried older versions of Wine, all the way back to 1.1.8 i believe it is (currently have wine 1.1.15 in), Im using Ubuntu 8.10, on a dell with a 2.4 ghz processor, 768 mb Ram, um...yeah, i think that's about the most on my specs that I can come up with off the top of my head. Regardless, I've researched about every possible thing to do and I've had no luck.

Someone help me figure this out, pretty please. I'm really really not wanting to go back to windows...because well..its the devil.

---

### Post by amritmatharu on 2009-02-17
I can't remember where I saw the solution for it, but basically, I had to download Internet Explorer, and it somehow solved the problem for me. Sorry about the short reply, but it's honestly all I remember. I'll have a look around for what I downloaded.

---

### Post by kenaro on 2009-02-17
Can I ask how you accessed the older versions of Wine? I can't find anywhere to install them, nor can I install them through deb files.

---

### Post by Pikestaff on 2009-02-18
I solved this problem on my latest reinstall by downloading the very latest Wine actually.

If that's not working for you try out this method I posted on my own blog, which worked for me when I installed WotLK Beta this past autumn: [http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html](http://www.aspectofthehare.net/2008/09/linux-users-do-it-with-wine.html)

---

### Post by pdonovan821 on 2009-02-18
> **kenaro said:**
> Can I ask how you accessed the older versions of Wine? I can't find anywhere to install them, nor can I install them through deb files.

If memory serves me, i just went to wine's download site and they had pretty much every version under the sun there.

---

### Post by NewNewb on 2009-03-04
[http://winehq.org/download/deb](http://winehq.org/download/deb)

follow the all the steps.  the new wine takes care of business.

chee-eeez.

---

### Post by jlhines on 2009-06-20
I'm having this problem right now, and have tried all the solutions posted in this thread and others.  I'm having the problem with both the downloaded installers and the CDs (both from the disk, and downloaded to my hard drive).  I've got the newest version of wine and MS fonts installed.  I've also downloaded Internet Explorer and it didn't magically fix it :-(

A question for Pikestaff:  You said in your blog "An attempt to run the installer via IEs4Linux’s Wine told me I needed to have Burning Crusade installed".  How did you "run the installer via IEs4Linux's Wine"?  I don't really understand what that means or how to do it.

If anyone has any other possible solutions, I'm willing to try just about anything now.  

Stupid 'accept' button!

---

### Post by mvidberg on 2009-08-23
I am having this "can't click on the Accept button" of the EULA problem myself after just purchased the World Of Warcraft Battle Chest set.  Newest wine, msfonts installed, but still greyed out Accept button.  Lame.

---

### Post by mbuehl on 2009-08-23
Same issue with diablo II. Can't install, grayed out accept.

---

### Post by Bios Element on 2009-08-23
> **mvidberg said:**
> I am having this "can't click on the Accept button" of the EULA problem myself after just purchased the World Of Warcraft Battle Chest set.  Newest wine, msfonts installed, but still greyed out Accept button.  Lame.

Newest wine isn't 1.0.0. Use the dev version. I just checked and on my system it's still working fine.

---

### Post by hikaricore on 2009-08-23
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)  << figure it out folks

---

### Post by mbuehl on 2009-08-23
actually, after having this issue I followed one of the above posters advice...

sh winetricks -v ie6

fixed my issue.

---

### Post by 5zerocool on 2009-08-24
Great solution, I updated wine! Works perfectly. Thanks.

---

### Post by blackmail on 2010-05-28
just go to winehq.org and install the new wine, don't forget to SUDO APT-GET REMOVE WINE before you install the new wine, cuz the problem will persiste, and also, if it still doesn't go away, please check for a new installer, and copy that from a friend or from somewhere...
Good luck and have fun
after the installation is off, which goes much faster under linux, might I add, i only tremble to see if the patches will be so docile and install...

---

### Post by blackmail on 2010-05-28
WINE can xseem somewhat complicated at first and since it yelds such a great entropy some explanaitons are always welcome

---

### Post by TristanCharles on 2011-01-25
> **mbuehl said:**
> actually, after having this issue I followed one of the above posters advice...

sh winetricks -v ie6

fixed my issue.

Worked PERFECTLY! I've been looking almost all day to figure this out! Thank you!

---

