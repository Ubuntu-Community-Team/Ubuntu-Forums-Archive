---
title: "Online anti-virus scanner compatible with linux?"
date: 2009-01-10
forum: The Cafe
---

### Post by mr.propre on 2009-01-10
Hi,

Is there an online virus scanner (that can scan a single file or more) and that runs on Linux? It's for a windows exe, I want to scan it first before coping to a windows machine. Google didn't really help finding one ;-)

Thank you.

---

### Post by sydbat on 2009-01-10
Trend Micro has an online scanner ([Housecall]("http://housecall.trendmicro.com/")) that works with Linux (it is actually browser based so works anywhere). Not sure if it can scan only one file though...

---

### Post by jrusso2 on 2009-01-10
I know Trend Housecall does it has two plugins one for Java which is for Linux and one for active x for Windows

---

### Post by 2hot6ft2 on 2009-01-10
> **mr.propre said:**
> Hi,

Is there an online virus scanner (that can scan a single file or more) and that runs on Linux? It's for a windows exe, I want to scan it first before coping to a windows machine. Google didn't really help finding one ;-)

Thank you.
If you just want to scan a single file you can upload it to here. [http://www.virustotal.com/](http://www.virustotal.com/) and have it scanned by about 20 anti virus programs all at once.

If you want to scan a bunch you already have clamav installed and you can install the gui for it with.
```
sudo apt-get install clamtk
```
In a terminal
Applications>Accessories>Terminal

Then it will be in
Applications>System Tools>Virus Scanner

---

### Post by abn91c on 2009-01-10
AVG has a free linux version here: [http://free.avg.com/download?prd=afl]("http://free.avg.com/download?prd=afl")

---

### Post by 2hot6ft2 on 2009-01-10
> **abn91c said:**
> AVG has a free linux version here: [http://free.avg.com/download?prd=afl]("http://free.avg.com/download?prd=afl")
That too IF you're running the x86 32 bit OS and also avast will work on the x86 32 bit system. Unfortunately neither one has a 64 bit version unless they've added it in the last few weeks. Both and more info can be found here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by mr.propre on 2009-01-11
Thanks for the replies, I don't really want to install an anti-virus scanner because normally i don't need one except for this one time occasion.

I tied housecall of trendmicro but for some reason my java crashes in firefox and Opera seems to have trouble selecting files.
I'm about to try virus total.

I you see "solved" it means it worked.

---

### Post by binbash on 2009-01-11
virustotal is great for that purposes, i am using it for a long time

---

