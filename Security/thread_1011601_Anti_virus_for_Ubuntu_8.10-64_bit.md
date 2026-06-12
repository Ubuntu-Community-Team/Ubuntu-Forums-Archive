---
title: "Anti virus for Ubuntu 8.10-64 bit"
date: 2008-12-14
forum: Security
---

### Post by Orvile on 2008-12-14
I use ubuntu 8.10/64 bit. I have read much about anti-virus software for Linux. Form what I have read, It doesn't seem to be a big concern and I understand all the reasons. I am not new to computers or viruses for that matter but it would give me the "Warm & Fuzzys" if I could find an anti-virus that works with 64 bit. I use the ClamTk that is in the add/remove section of the software but I would prefer something that works automatically. The ClamTk is strictly Manual! All the popular ones: Avast, AVG.....etc only have the 32 bit versions. Any ideas out there in internet-land??    

:confused:

---

### Post by HermanAB on 2008-12-15
This one should work on any system type.  It is a bit slow, but it works really well:

#! /bin/bash
echo "Linux virus scanner, Copyright reserved FSF, GPL 2008"
sleep 10
echo "Scanning..."
echo sleep 30
echo "Still scanning..."
sleep 10
echo "Wait for it!"
sleep 20
echo "Drum roll..."
sleep 5
echo "No viruses found!"
sleep 10
echo "Have a nice day."
exit 0

---

### Post by hyper_ch on 2008-12-15
no anti-virus needed on linux.

---

### Post by Liviu-Theodor on 2008-12-15
Apparently, ClamTK detects Windows viruses, so if you receive such thing, you could thing better before resending it to an Windows user.

---

### Post by Vantrax on 2008-12-15
Avast has an AV that is good if:

Your running wine (some viruses can work under wine)
Your working with dualboot systems and want to scan windows from linux.
You want to be able to run scans on attached storage.

---

### Post by Orvile on 2008-12-15
THX. I will try avast.I have used it on Windows machines and it seems to works fine but if it gives me troubles, I guess I will go back to clamtk.  I have tried windows programs under Wine and some are a little finicky.

AVG sells an anti-virus for Linux that they claim works on all linux platforms. Does anyone know if it's a TRUE linux anti virus or just another windows/wine scanner???

:confused:

---

### Post by cariboo on 2008-12-15
I'm not sure about any of the commercial versions, it would be best to go to their home pages and read what viruses they scan for. Clamav does scan for Linux viruses, even though their non in the wild.

Have a look [here]("http://librenix.com/?inode=21"), for reasons why it is so hard  for a virus to take hold in Lunx.

Jim

---

### Post by Nepherte on 2008-12-15
> **hyper_ch said:**
> no anti-virus needed on linux.
Exactly, Just forget about the whole anti-virus thing. If you really insist on securing your system more, read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

