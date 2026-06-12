---
title: "new install bind will not stop or start - it was installed"
date: 2008-07-06
forum: Server Platforms
---

### Post by mspIggy on 2008-07-06
failing miserably setting up new server - bind seems to be the latest problem that is prefenting me from being able to plug into the www

------------------------

i have been trying non-stop since thursday th 4th to load ubuntu with raid 1 on my dl360... sleeping for 3 and 4 hours here and there until i get this to work

following this [http://www.howtoforge.com/perfect-se...ntu8.04-lts-p4](http://www.howtoforge.com/perfect-se...ntu8.04-lts-p4) added raid 1 (cannot install grub in drive 2)

one reason or another all installs have failed... this one - i wiped clean drives and started fresh....

i think i am actually close...

for some reason bind is not loading...

no way to start...

if i try to stop i get this

127.0.0.0.1 # 953 connection refused

thoughts?

---

### Post by mspIggy on 2008-07-06
fixed it gateway ip was wrong

but bind will not start...

---

### Post by cariboo on 2008-07-06
is the 127.0.0.0.1 a typo? it should be 127.0.0.1

Jim

---

### Post by mspIggy on 2008-07-06
sorry this is a typo..

the correct ip in there - i made goof in post to forum...
 grub to disk 2 on raid 1
i guess i will erase drives and try again...

geeze   4 days...

cannot get grub to drive 2 80gb sata drives...

spent all day yesterday on that alone...

---

### Post by windependence on 2008-07-06
You probably don't even need bind. I don't know who is telling everyone they need a full DNS server on their server but in most cases you don't, especially if you are just running a web server.

-Tim

---

