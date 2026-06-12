---
title: "2nd opinion, drive share security issue"
date: 2006-08-17
forum: Server Platforms
---

### Post by grimmson on 2006-08-17
Hello all. I wanted to get fancy. I installed fedora core 5 (so wife and I can study for rhct.) That gives me a tripple boot ubuntu fc5 and doze 2000. Fedora is up and running, updated etc... so now I'm tuning. A have two drives, hda (1,2,3&4) and sda1. I hold all my stuff on sda1 (not home for either). I wanted to mount sda1 in fc5 and thats where the fun began. I can mount it in root w/ read only (and thats as far as I can take it.) Started a thread [http://forums.fedoraforum.org/showthread.php?t=121016](http://forums.fedoraforum.org/showthread.php?t=121016) and got a probable solution, that led me to a question. Ubuntu is my primary dist. In ub my groupid is *. The advice on ff thread says edit etc/passwd, match users group and owners in BOTH os's and I probably can see sda1. What dist should I change? group * (from what I've read is system). System groups are not advised. Should I dummy down my group in ub for security/safty or add a system groupid * in fc5? I think I can do either. I don't know what is best for both worlds. Please give me your two cents (if your sure you know what your talking about, no offence.) Thanks for your time.

---

### Post by Ride Jib on 2006-08-17
Why not manually create a new, unique group under both systems (ensuring they have the same gid like 1345 or something unused) and then just chgrp on the folder?

---

### Post by grimmson on 2006-08-18
I'm starting to think my error is I'm using a admin account daily in ubuntu. Thats why my group is * (system). I'm almost sure I need to make a normal user account for normal usage. If I made a groupid over 500 would I want to include that user in visudo?

---

