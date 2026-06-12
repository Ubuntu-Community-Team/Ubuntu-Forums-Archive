---
title: "Dell Keyboard not working with 20130209 Nightly Build."
date: 2013-02-09
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-02-09
Just FYI.

---

### Post by kevpan815 on 2013-02-09
P.S. I am running 13.04 on my Secondary PC which does NOT have the necessary WIFI Access Build-in in order to BOTH Connect to the Internet AND file the necessary Bug Report. Just FYI.

---

### Post by bobipod on 2013-02-09
I was about to post about my keyboard only partly working.

I'm on Ubuntu 12.10 latest update and using a dell inspiron 1520.  In the last couple of days my arrow keys have stopped working and now so too have the following:

home, pg up, pg dn, end, and the arrows.

Any ideas or fixes?

---

### Post by kevpan815 on 2013-02-09
> **bobipod said:**
> I was about to post about my keyboard only partly working.

I'm on Ubuntu 12.10 latest update and using a dell inspiron 1520.  In the last couple of days my arrow keys have stopped working and now so too have the following:

home, pg up, pg dn, end, and the arrows.

Any ideas or fixes?

My keyboard problem is even worse because none of my keys are working with Ubuntu 13.04 AMD64 Nightly Build 20130209, so NOT only am I unable to install the Build, I am also unable to Type anything in while running the DVD in Live CD Mode! :-(

So far I am NOT sure exactly what to do about the problem other than try the disk out on my primary computer (which is a Net Book PC instead of a Desktop PC and see if I have the same problem or NOT), knowing that eventually I will have to return my Net Book back to Windows in order to update my IPhone 5 to the next Build of Apple IOS 6.1.1 Beta (the NDA Beta that I was referring to before) Just FYI.

---

### Post by cariboo on 2013-02-09
Have you tried the onscreen keyboard go to System Settings>Universal Access>Typing, and turn on the onscreen keyboard. See the screen shot.

---

### Post by kevpan815 on 2013-02-09
Even if I tried the on screen keyboard, i would still be unable to file a Bug Report on my Secondary PC as this particular PC does NOT have the neccesary 80211.a.b.g.n WIFI Built in to receieve the Internet Connection from my Sprint Apple IPhone 5's 4G LTE Personal Hotspot to connect to the Internet. I decided that I am going to remove Windows Temporarily from my Primary Computer and see if the disk has the same problem on my primary computer or NOT, and that I am going to try the 12.04.2 AMD64 Alternate Installer on my secondary computer and see if problem also occurs on it as well or NOT. Thanks for the help, however.

By the way, I did try the Check Disk for Errors Option on Boot Up and it Passed the Disk Integrity Check without any Problems.

---

### Post by kevpan815 on 2013-02-10
> **cariboo907 said:**
> Have you tried the onscreen keyboard go to System Settings>Universal Access>Typing, and turn on the onscreen keyboard. See the screen shot.

Cariboo907, the issue that occurred on my Dell Inspiron Zino 400 HD (my Secondary Computer) which has a 64 Bit AMD Processor and an ATI Graphics Card by the way (I am mentioning this because I have had a couple of weird MSDOS Like Screens showing up on Boot Up on this Machine while running 13.04 Nightly that do NOT show up when running 12.04.2 Nightly) did NOT reproduce itself on my Dell Inspiron 1012 Mini Net Book PC while running 13.04 (my Primary Computer), and the issue did NOT reproduce itself on 12.04.2 on my Secondary PC (the one with the problem with 13.04 Nightly) either.

---

### Post by cariboo on 2013-02-10
My suggestion to use the on-screen keyboard was to help you diagnose the problem without having to just wonder what created the problem. With the on-screen keybaord, you should be able to open a terminal and check the output of dmesg at the least.

---

### Post by kevpan815 on 2013-02-11
> **cariboo907 said:**
> My suggestion to use the on-screen keyboard was to help you diagnose the problem without having to just wonder what created the problem. With the on-screen keybaord, you should be able to open a terminal and check the output of dmesg at the least.

Cariboo907, I figured out the problem: Broken USB Connector on the Keyboard itself (that's the reason why the Keyboard sometimes works and Othertimes does NOT work at all), Solution: Use a different Keyboard, just FYI.

---

