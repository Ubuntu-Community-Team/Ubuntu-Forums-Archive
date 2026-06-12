---
title: "Wheres the AV software?"
date: 2008-04-24
forum: Security
---

### Post by AJB2K3 on 2008-04-24
Silly question really but with copying files from multiple MS pc's I would like to scan all the files on my ubuntu system before finial sorage.

Where do I find the AV software?
Does it check and clean MS OS made files?

---

### Post by Monicker on 2008-04-24
> **AJB2K3 said:**
> Silly question really but with copying files from multiple MS pc's I would like to scan all the files on my ubuntu system before finial sorage.

Where do I find the AV software?
Does it check and clean MS OS made files?


sudo apt-get install clamav

sudo freshclam - in order to update the virus definitions


Then use clamscan to check your files.

---

### Post by Chayak on 2008-04-25
ClamAV isn't exactly the best antivirus out there.  If you want to scan a file you can use [http://www.virustotal.com]("http://www.virustotal.com") it does multiple scanners and if you look at the stats ClamAV is one of the worst.

---

### Post by juan@forum on 2008-04-25
> **Chayak said:**
> ClamAV isn't exactly the best antivirus out there.  If you want to scan a file you can use [http://www.virustotal.com]("http://www.virustotal.com") it does multiple scanners and if you look at the stats ClamAV is one of the worst.

it is not the right way to describe an antivirus...

clamav is better suit to be used on mailservers

---

