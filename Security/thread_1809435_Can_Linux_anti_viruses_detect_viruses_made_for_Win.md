---
title: "Can Linux anti viruses detect viruses made for Windos?"
date: 2011-07-21
forum: Security
---

### Post by TobiasRipper on 2011-07-21
Here is the system. My laptop has Ubuntu and my Desktop has Win 7. I do not even dare to connect my PC to internet because it;s just too risky so what I want to do is to have Ubuntu with internet make all my downloads and then scan then with some kind of anti virus for ubuntu and only then transfer it to Windows machine if the files are clean.

So mainly i'm not worried about my ubuntu station but the PC station. I wont be installing linux on desktop.

But my main question would be, can Linux Anti virus detect viruses made for Win 7?

---

### Post by haqking on 2011-07-21
> **TobiasRipper said:**
> Here is the system. My laptop has Ubuntu and my Desktop has Win 7. I do not even dare to connect my PC to internet because it;s just too risky so what I want to do is to have Ubuntu with internet make all my downloads and then scan then with some kind of anti virus for ubuntu and only then transfer it to Windows machine if the files are clean.

So mainly i'm not worried about my ubuntu station but the PC station. I wont be installing linux on desktop.

But my main question would be, can Linux Anti virus detect viruses made for Win 7?


YES.

Linux is not prone to viruses like windows but all AV siftware available for linux can scan windows files and partitions for windows based viruses, really to prevent you fomr spreading viruses in a windows based network even though you are running linux.

peace

---

### Post by uRock on 2011-07-21
ClamAV in the ubuntu repos scans mostly for Windows viruses.

I have been running Windows 7 with MS Security Essentials for more than two years now and have not had any problems with viruses.

---

### Post by sneakyimp on 2011-07-21
The way most virus scanners work is to look for a virus 'signature'.  I'm not entirely sure about the process, but I believe it involves checking files for a series of bytes that can by reliably and uniquely attributable to a virus.  AV programs keep a big database of these byte signatures and scan for them without any regard as to which platform they might target.

---

