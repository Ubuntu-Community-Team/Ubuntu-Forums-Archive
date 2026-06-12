---
title: "Wine won't work with Ubuntu 10.04, and Psychonauts? HELP!!!"
date: 2010-07-25
forum: Wine
---

### Post by Kurtless on 2010-07-25
So I have Ubuntu 10.04 (lucid), and I hear that the newest Wine doesn't work with much of anything with Ubuntu 10.04, I tried doing something, but it didn't work. I couldn't open any exe files.

So I heard if you use a earlier version of Wine, it would work, so I tried, and it worked, sort of. It loaded the Psychonauts installer, and everything was working until it asked for Disc 2, I put the Disc in, and it said there was no disc in the drive, even though there was one. The disc drive is not faulty, and I'm not good with Ubuntu yet.

Can anyone help me? :D

---

### Post by collinp on 2010-07-25
I haven't heard much of anything about Wine not working right in Lucid Lynx (it works just peachy for me).

From my knowledge, it's rare for anything to work right off a CD with Wine. 

Here's a guide to installing the game that you're trying to run that I found: [http://www.wine-reviews.net/games/psychonauts-on-linux-with-wine.html](http://www.wine-reviews.net/games/psychonauts-on-linux-with-wine.html)

---

### Post by Kurtless on 2010-07-28
That seems like the only tutorial online, but the wording confused me, and everything, something about "cd to dvd" and I lost it from there, I tried putting the codes but the installation still didn't work, I know it can work, so how can I make it?

---

### Post by Kurtless on 2010-08-04
Hey! So I tried to do this installation thing another way.I put the discs on my hard rive, and when it asked for Disc 2, I lined it up with the disc 2 on my hard drive, and it worked! It didn't ask for the other 3 discs, but i put those in the same folder, it said the installation was complete, but when I tried to make it work it came up with the message of a crash, null, and that I didn't have the VS.net or something installed, debugger something or other, anybody know whats going on?

---

### Post by cogadh on 2010-08-04
You need to slow down a bit, pay close attention to the errors you are getting and tell us *precisely* what they say. We are not sitting in front of your machine, so you need to be our eyes, otherwise we can't help you.

---

### Post by Kurtless on 2010-08-23
Sorry, well here is what it says after I try running psychonauts.

Encountered Error:

(null), line 1
Crash: 0x0000005
If you have VS.NET installed, you can try to attach the debugger

Otherwise click ok


Know whats wrong everyone?

---

### Post by Ross Abraham on 2010-12-15
> **Kurtless said:**
> So I have Ubuntu 10.04 (lucid), and I hear that the newest Wine doesn't work with much of anything with Ubuntu 10.04, I tried doing something, but it didn't work. I couldn't open any exe files.

So I heard if you use a earlier version of Wine, it would work, so I tried, and it worked, sort of. It loaded the Psychonauts installer, and everything was working until it asked for Disc 2, I put the Disc in, and it said there was no disc in the drive, even though there was one. The disc drive is not faulty, and I'm not good with Ubuntu yet.

Can anyone help me? :D

> **Kurtless said:**
> Sorry, well here is what it says after I try running psychonauts.

Encountered Error:

(null), line 1
Crash: 0x0000005
If you have VS.NET installed, you can try to attach the debugger

Otherwise click ok


Know whats wrong everyone?
Guys,
My questions is similar but different. Wine works perfectly on some programs but not others. I have an Asus laptop which dual booted Windows XP and Ubuntu 10.04. I had Wine 1.2 running and it ran every .exe program I wished. I have now re-installed Ubuntu 10.04 on the same machine and only some .exe programs will run. This is the same computer and same software, the only difference is Windows XP has gone. 
I am also using a netbook which had Windows XP loaded. I installed Ubuntu 10.04 and Wine runs every .exe. file I wish with no problem.
I am baffled. Why will Wine now only run some .exe files and not others? Has anyone any clues please?
Ross

---

### Post by SuperXDE on 2010-12-16
Did you install the perquisites by winetricks? it is necessary for programs to run on Wine to have some certain programs ( like .NET framework , Visual C , etc... )

---

### Post by @TAN on 2011-01-08
Well there seems to be an issue working with the new wine version in GUI. If you use the Terminal it will work fine. Just go to your directory where the .exe file is located using the terminal and type wine <file name you want to execute>. For those using GUI, wait for the wine developers to find a solution.

---

