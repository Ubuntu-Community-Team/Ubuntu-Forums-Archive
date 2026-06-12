---
title: "No DVD In Ubuntu Guest OS"
date: 2008-12-05
forum: Virtualisation
---

### Post by wah fun on 2008-12-05
Hi,

I am trying out ubuntu 8.04 as a possible fit for a small business. So I have an XP host with ubuntu 8.04 guest os installed. Linux guest additions have also been installed. Everything works great except the dvd. I cannot view movies or burn a cd when logged into the XP system as a restricted user (this does not prevent a user from using the dvd in xp). However, when logged in as administrator on xp, the ubuntu guest system works fine. Now, since I want to let restricted users actually use the ubuntu VM to see if they like it, I don't want the xp system exposed.

If anyone has a solution to get the dvd to work for this test environment, I would appreciate it.

Thx

---

### Post by Dedoimedo on 2008-12-05
Hello,

Try SuRun in Windows XP. Run as limited user and elevate privileges as necessary - similar to sudo.
[http://kay-bruns.de/wp/software/surun/](http://kay-bruns.de/wp/software/surun/)

A healthy explanation on this on Wilder's forums:
[http://www.wilderssecurity.com/showthread.php?t=196737](http://www.wilderssecurity.com/showthread.php?t=196737)

Cheers,
Dedoimedo

---

### Post by wah fun on 2008-12-05
Thx. That worked!

---

### Post by Dedoimedo on 2008-12-06
Cheers! You can mark the thread as solved.
Dedoimedo

---

### Post by stinger30au on 2008-12-06
thanks

---

