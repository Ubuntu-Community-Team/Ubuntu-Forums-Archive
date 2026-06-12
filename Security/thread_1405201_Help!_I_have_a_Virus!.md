---
title: "Help! I have a Virus!"
date: 2010-02-12
forum: Security
---

### Post by Celestika6 on 2010-02-12
Okay... So KlamAV found a virus...

It has officially ***ked up my entire computer and because I can't seem to get rid of it with KlamAV I tried to install AVG for linux. That just messed things up even worse. My terminal says it can't allocate the memory to install it. I really do NOT have that many files on my computer, I have it all on an external HD.

Can someone either tell me how I delete with KlamAV or burn AVG for linux onto a bootable CD?

I run Karmic Koala.

---

### Post by Grenage on 2010-02-12
The virus won't affect your Linux machine, it will be a Windows virus (apologies if I'm stating the obvious).  Did ClamAV delete files, was it run as root?

What problems are you having?

---

### Post by running_rabbit07 on 2010-02-12
Please give us a screenshot or copy of the text output of the scan showing the name and type of file infected. Clam is known for false positives. In your case, there may be a Windows virus or just a bad cookie. Either way, we need to know what your are dealing with in order to help you.

---

### Post by mhgsys on 2010-02-12
run clamav with
```
sudo clamscan -r /
```

to check all files on the computer, displaying the name of each file

---

