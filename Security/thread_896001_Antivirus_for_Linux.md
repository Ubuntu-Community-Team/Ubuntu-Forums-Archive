---
title: "Antivirus for Linux"
date: 2008-08-20
forum: Security
---

### Post by lisadi on 2008-08-20
What is a good anti virus program so when I download windows programs with Linux that I can check for viruses before I write a CD for a windows app?

---

### Post by tamoneya on 2008-08-20
use clam AV. 

Here is the site: [http://www.clamav.net/](http://www.clamav.net/) however it is in the repositories so that is the easiest way to get it.

---

### Post by ggaaron on 2008-08-21
ClamAV is underrated because it has no on-exec scan - you must scan files manually. Still I think it is the best option.

---

### Post by tamoneya on 2008-08-21
why would it need a on-execute functionality.  It searches for windows virii and windows virii wont be executing themselves on a linux machine.  Even if they did they wouldnt be able to do any damage.

---

### Post by jerome1232 on 2008-08-21
Not to mention you can just make a small easy script that scans files once every day and moves infected files to an "infected" directory and clean ones to a "clean" directory. I love it.

---

### Post by aysiu on 2008-08-21
Do you mean *overrated*?

---

### Post by ggaaron on 2008-08-22
I mean that people tend to say that ClamAV is bad because it doesn't use auto-scanner so I think underrated - people tell it is worse that it really is? (actually there is dazuko, but I've tried it - slow and unstable...). Why would you need auto-scan anyway? 1. you can infect wine (not a big problem=P) 2. being lazy I would prefer that *.exe files I download be scanned automatically=)

---

