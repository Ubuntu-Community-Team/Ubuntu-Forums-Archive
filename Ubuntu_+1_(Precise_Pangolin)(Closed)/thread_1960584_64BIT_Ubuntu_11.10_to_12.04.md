---
title: "64BIT Ubuntu 11.10 to 12.04"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by N64Cam on 2012-04-17
I installed ubuntu ver 12.04 I cant move my cursor , i can only log in the desktop is bugged no graphics the icons are messed up and i dont no what to do now,please help

---

### Post by mörgæs on 2012-04-17
Have you searched the forum thoroughly before posting? 

If you have Nvidia and use closed-source drivers, this could explain your graphics problem:
[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

---

### Post by swissinvestor on 2012-04-17
I upgraded 4 computers from 11.10 to 12.04 and had serious problems on one of them. 
What did it for me was
apt-get -f install

This fixed the problem.

---

### Post by N64Cam on 2012-04-17
> **mörgæs said:**
> Have you searched the forum thoroughly before posting? 

If you have Nvidia and use closed-source drivers, this could explain your graphics problem:
[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

i went to ubuntu.com i saw the 12.04 lts download

---

### Post by N64Cam on 2012-04-17
the terminal is bugged

---

### Post by mörgæs on 2012-04-17
Moved to Absolute Beginner Talk. 

Installing beta software like 12.04 is not recommended unless you are experienced in troubleshooting.

---

### Post by Iowan on 2012-04-17
:oops: Oops, this thread is gonna get dizzy from all the moves...
Moved to Ubuntu +1 (Precise Pangolin)

---

### Post by swissinvestor on 2012-04-18
> **N64Cam said:**
> the terminal is bugged

I am not sure if your problem is that you cannot access the terminal.

That was the problem I had too, I had no access to the terminal and lost mouse control also.

I solved the problem by starting directly in terminal mode but not sure anymore how exactly I did that:

maybe it was  Alt-Ctl-F2

beside apt-get -f install

I also did 
apt-get autoremove (because the installation process was somehow broken)

apt-get update
apt-get dist-upgrade

This did the trick for me, I had a working system - still with some minor problems but most of those seem to have gone by now through normal updates

---

