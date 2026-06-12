---
title: "Stupid: Renamed /etc"
date: 2009-02-08
forum: Server Platforms
---

### Post by Jeztastic on 2009-02-08
Whoops. 

Was trying to backup and replace /etc using Webmin. So I dropped /etcbackup in / and then renamed /etc > /etcbackup2. Went to restore /etcbackup to /etc but couldn't. Everything broken now!!! 

How do I sort this? Please be kind.

---

### Post by jimv on 2009-02-08
This is where the livecd will help you.  You need to go to that machine, put the cd in, and use the terminal on the cd to rename your /etc folder.

---

### Post by Jeztastic on 2009-02-08
yup, that sorted it... Phew!

---

### Post by skunkbad on 2009-02-09
So why is it that he could rename /etc, but could only rename it back to /etc through the Live CD environment?

---

### Post by jimv on 2009-02-09
Good question.  Seems like mv should still have worked.

---

### Post by Jeztastic on 2009-02-09
It may well have been because I was using Webmin at the time. When I tried to log into the shell via SSH it wouldn't let me... I assume because it couldn't find /etc. Maybe I could have plugged a moniter in and done it directly, but by then the whole thing was having a fit and I couldn't get it to boot.

---

### Post by Dr Small on 2009-02-09
> **jimv said:**
> Good question.  Seems like mv should still have worked.
Probably because the sudoers file was missing, but if he was already logged into root, that wouldn't have mattered.

---

