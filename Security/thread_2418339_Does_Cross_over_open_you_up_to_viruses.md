---
title: "Does Cross over open you up to viruses?"
date: 2019-05-05
forum: Security
---

### Post by jam7755 on 2019-05-05
I was thinking of getting cross over to run on my Ubuntu system because I still have a need to run Windows software.  Not much but enough to warrant this.  I am wondering if Cross over would allow a virus to run natively on Linux since it does allow windows software to run natively.  My main need to is for a garmin watch I use to track my activity and Garmin Express only runs on Windows or Mac.

---

### Post by Frogs Hair on 2019-05-05
Moved to *Security*.

---

### Post by yetimon_64 on 2019-05-05
Check out the [[COLOR=#0000ff]--Ubuntu security sticky-- [/COLOR]]("https://ubuntuforums.org/showthread.php?t=510812") under the section "A few comments on wine" for information regarding viruses affecting wine (crossover is based on wine). 

One important thing to remember: DO NOT run wine/crossover as root. A wine/crossover virus may be able to run but can only affect the users home directory if run with user privileges. There are quite a few more important notes on wine and viruses in the link in blue text above.

Regards, yeti.

---

### Post by maglin2 on 2019-05-06
I empathise. I also need Garmin Express for my car sat nav. 
Possible different approach. I bought a refurbished Windows 10 laptop to run it for twice the cost of a 1 year Crossover licence.
Also means if I come across anything else that really needs Windows I'm ready.

---

### Post by TheFu on 2019-05-06
> **maglin2 said:**
> I empathise. I also need Garmin Express for my car sat nav. 
Possible different approach. I bought a refurbished Windows 10 laptop to run it for twice the cost of a 1 year Crossover licence.
Also means if I come across anything else that really needs Windows I'm ready.

THIS!!!

WINE isn't 100% - more like 20%.  I fought for months to get about 65% of Quicken working, but wasn't able to get the other 35% to work, ever.  For me, it is easier to run a Windows7 instance inside a VM to run those 3 programs I need that don't have any acceptable alternative in Linux.  Virtualization is really excellent these days, but you'll need a legal license from MSFT.  Also, I don't use Windows on the internet, ever, so I'm not worried about getting viruses.  One of my 3 Windows programs will stop working when MSFT ends support. When that happens, I have another, less good, Linux option for it. It will not work under WINE.

For virtual machines to be an option, you only need a Core2 Duo or better CPU with 4GB of RAM - 8 would be better, but 4 is sufficient for a small 2G Windows install. Plus, by using a VM, you don't have to reboot from Linux into Windows.  You start up the Windows VM just when you need it, a few times a year for something like GPS map updates or weekly like I need it to enter/update Quicken data.

---

