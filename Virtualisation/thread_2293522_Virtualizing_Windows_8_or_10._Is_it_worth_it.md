---
title: "Virtualizing Windows 8 or 10. Is it worth it?"
date: 2015-09-05
forum: Virtualisation
---

### Post by jason_gibson2 on 2015-09-05
I much prefer Linux as my main os, however I need Quickbooks. Seems a pain to virtualize an entire Windows just for that but I need the software regardless. I currently am running a laptop with an i7 4500U, 8gb of ram, gpu is intel hd4400 on the i7, 120gb Samsung 840 EVO ssd. I have tried virtualizing Windows before but it wasn't very fluid. If I'm going to virtualize it I have to be able to depend on it, no freezes or forced resets losing data in the process. Is my laptop up to the task enough to rely on a virtualbox vm or do I just not have enough power for it to be dependable?

If not then I will stick with Windows on the laptop. As said though I'd rather be running Linux as the host if possible.

---

### Post by J_Me on 2015-09-05
Have you looked to see if Quickbooks will run under wine [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by jason_gibson2 on 2015-09-05
2009-2013 are all rated garbage on winehq. Is why I know I'm gonna need to virtualize if I want to run Linux as the main :/

---

### Post by SeijiSensei on 2015-09-05
Your computer has more than enough horsepower to virtualize Windows.  My experience only extends through Win7, but I doubt there would be much difference with Win10.  Give Windows at least 2 GB of memory, preferably four.  On my Linux machines with Win7 virtualized, the minimum memory size I use is 1,536 MB.  

Check the BIOS to make sure VT-x is enabled.  Make sure to install the "Extension Pack" as it will improve video performance.

I use virtualized Windows for things like tax preparation.  For games, I use native Windows for performance reasons.

---

### Post by ajgreeny on 2015-09-05
Have you considered trying gnucash instead of quickbooks?

I've never needed quickbooks but I did use quicken a long time ago in my Windows days, and I missed it at first but have since found a native application, kmymoney2 which does everything I used quicken for; the same may be true for you as well with gnucash.  I think it can also import files from quicken or quickbooks , but have not done so myself.

---

### Post by jason_gibson2 on 2015-09-06
I use kmymoney for personal stuff, but gnucash or kmymoney can't compare with QuickBooks for my business.

After some reading I found that win 10 is still a little questionable in Virtualbox. Is why I've had those freezes and instability. I've since gone back to kubuntu and have kept windows on 8.1. It's running beautifully. I'll do 10 when its fully supported.

---

### Post by Morbius1 on 2015-09-06
More of an FYI:

I'm running Win10 as a Vbox guest on a Xubuntu 14.04 host and it seems to be running just fine. 

I originally had it running with VBox 4.x.y but couldn't quite get the resolution where I wanted it. Using Vbox 5.0.0 fixed all that.

---

