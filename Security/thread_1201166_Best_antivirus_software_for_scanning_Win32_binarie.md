---
title: "Best antivirus software for scanning Win32 binaries ?"
date: 2009-06-30
forum: Security
---

### Post by credobyte on 2009-06-30
Which is the most powerful ( detection rate ) antivirus sofware, available on Ubuntu ? I constantly need to verify various Win32 binaries ( .exe, .msi ) and Clam doesn't do it's job ( trojan detected by AVG, Kaspersky, Avast and NOD32 - Clam stays silent .. tested with 3 different infected applications ).

Suggestions always appreciated :)

---

### Post by sangaya on 2009-06-30
Not sure on the volume of binaries you need to scan, but I've found that uploading them to [www.virustotal.com](www.virustotal.com) does the trick.  I believe it's currently scanning with 40 different engines.

Also, check out [www.sunbeltsecurity.com](www.sunbeltsecurity.com) and submit it to the CWSandbox (located at the bottom).  They'll run an analysis on the WinPE32 executable and inform you of changes it makes to the file system, registry, network activity, etc.

---

### Post by credobyte on 2009-06-30
> **sangaya said:**
> Not sure on the volume of binaries you need to scan, but I've found that uploading them to [www.virustotal.com]("http://www.virustotal.com") does the trick.  I believe it's currently scanning with 40 different engines.

Also, check out [www.sunbeltsecurity.com]("http://www.sunbeltsecurity.com") and submit it to the CWSandbox (located at the bottom).  They'll run an analysis on the WinPE32 executable and inform you of changes it makes to the file system, registry, network activity, etc.

Usually I've ~ 100-150 files in queue ( once in 3-5 days ). Uploading each and every file to virustotal would be insane ( 5-10 minutes for every file ) !
Tough, thanks for trying to help .. let's see if I can create a macros ( start, sleep, collect results :D ).

---

### Post by bodhi.zazen on 2009-06-30
IMO Linux antivirus is not so great and most of what is discovered (depending on your source of course) is false positives.

So my advise is rather then looking for a better scanner you should track down and confirm the positives.

From my windows days years ago I recall there is no single fool proof scanner, I used to employ 2 antivirus scanners and 3 anti-spyware. Positives need to be confirmed before you go deleting some such just because it gives you an alert.

---

### Post by credobyte on 2009-07-01
> **bodhi.zazen said:**
> IMO Linux antivirus is not so great and most of what is discovered (depending on your source of course) is false positives.

So my advise is rather then looking for a better scanner you should track down and confirm the positives.

From my windows days years ago I recall there is no single fool proof scanner, I used to employ 2 antivirus scanners and 3 anti-spyware. Positives need to be confirmed before you go deleting some such just because it gives you an alert.

I'm running a private server and rules are very straightforward - virus detected, file deleted. Even if it's false-positive, I'm not going to guess if it true or I can leave it.
So far the one and only solution seems to be VirtualBox :(

---

### Post by bodhi.zazen on 2009-07-01
:lolflag:

I run private servers as well.

The rules are very simple

No Windows No Problem

Not knowing exactly what you are doing it is hard to know if your strategy is going to be of any benefit. Probably a good strategy if you are running a mail server and wish to protect windows clients and are willing to accept a number of false positives.

Not so good if the data you are removing is of any potential value , such as system files (ie scanning and deleting things  in /etc /usr or just about anywhere outside of $HOME or /tmp is going to get you into trouble) or files you (or someone else) spent several hours on only to see his or her work deleted as a false positive.

---

### Post by jrusso2 on 2009-07-01
Avira Antivir probably has the best detection rate for Windows as I have seen in tests and it has a Linux version.

---

### Post by lisati on 2009-07-01
> **bodhi.zazen said:**
> Positives need to be confirmed before you go deleting some such just because it gives you an alert.
I concur: I've had false positives and botched repairs happen on Windows system files, which does wonders for the functionality of the system!

---

### Post by colau on 2009-07-01
[http://it.dennyhalim.com/2009/01/antivirus-for-grml-debian-ubuntu-linux.html](http://it.dennyhalim.com/2009/01/antivirus-for-grml-debian-ubuntu-linux.html)

---

### Post by scorp123 on 2009-07-01
> **bodhi.zazen said:**
> The rules are very simple: No Windows No Problem Exactly. :guitar:

---

### Post by colau on 2009-07-01
> **scorp123 said:**
> Exactly. :guitar:
I do agree too.

---

### Post by credobyte on 2009-07-01
> **bodhi.zazen said:**
> 
The rules are very simple

No Windows No Problem

Um, yeah, however .. not everyone understands it ! New slogan for Ubuntu's promotion on YouTube ? :D

> **colau said:**
> [http://it.dennyhalim.com/2009/01/antivirus-for-grml-debian-ubuntu-linux.html](http://it.dennyhalim.com/2009/01/antivirus-for-grml-debian-ubuntu-linux.html)

Excellent ! Suggestions and list of *all* available antivirus applications received - problem solved ( I hope so :roll: ).

---

