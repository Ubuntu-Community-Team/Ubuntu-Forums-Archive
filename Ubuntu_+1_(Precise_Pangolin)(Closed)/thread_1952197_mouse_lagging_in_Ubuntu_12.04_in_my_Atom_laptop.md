---
title: "mouse lagging in Ubuntu 12.04 in my Atom laptop"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by DaviesX on 2012-04-03
I have a Netbook with an Atom N450 CPU and 1 GB memory. 
When I currently upgraded to Ubuntu 11.10 from Ubuntu 10.04, I have found that the new unity desktop is so sticky Especially when I open the libre office, almost everything sticked including the cursor !

So I made a decision to upgrade to Ubuntu 12.04 although it haven't been released yet. However, it is much faster running on my Atom netbook, I think that is probably because hardware acceleration is supported. 

Nevertheless, that problem still exists: when I switching a tabs to another in Google Chrome, for example, My hard disk is reading continuously for a while, and the CPU usage is extremely high ( almost 100 % ).

Despite the usage of CPU, a cursor shouldn't have been sticked on the screen any way when I was using Ubuntu 10.04 and Windows Xp. It isn't a great matter, I was annoying, though. Is that anyone can explain this problem, or is that possible to solve it ?

Thank you

---

### Post by uRock on 2012-04-03
Hello and welcome to the forums.

I have moved the thread to the ubuntu+1 sub-forum where folks testing 12.04 beta may be able to help you.

---

### Post by DaviesX on 2012-04-04
Thanks

---

### Post by meborc on 2012-04-04
if things are slow, they might be for several reasons. try checking what process is using the CPU the most and also see if you are using large amounts of swap.

you can do it with "top" in the terminal or just using the system monitor from the dash

as always - 12.04 is still not ready so upgrading from an older system can actually result in some different issues compared to fresh install. If I was you, I would back up all data and install 12.04 from an daily image

---

### Post by sudodus on 2012-04-04
I think that 'vanilla' Ubuntu is slow because it has too much 'eye candy'.

Either you tweak the desktop environment, so that it will demand less horsepower, or you try other flavours of Ubuntu

- Xubuntu with XFCE has a small foot-print
- Lubuntu with LXDE has an ultra-small foot-print.

- as suggested by *meborc*: install a fresh 'vanilla' Ubuntu 12.04.

Anyway, download iso files for these flavours and try them live before installing.

---

### Post by DaviesX on 2012-04-04
Thanks.

I saw someone in the forum posted such a solution about how to solve this problem, I would like to try it first.

> 
[COLOR=#000000][FONT=Times New Roman]Adding the following line in /etc/modprobe.d/local.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]options drm_kms_helper poll=N [/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]Then restart. [/FONT][/COLOR]


---

### Post by DaviesX on 2012-04-04
:-)

Actually I have used Ubuntu only for several months, But I find it pretty good. Especially that is because I only have a slow netbook, it can't work sensitive enough with Windows Xp. So I try switching to a free Linux-kernel Ubuntu 10.04 and everything is good except the Ralink wireless hasn't supported yet, I have to install myself.

---

### Post by DaviesX on 2012-04-05
It still doesn't work, Perhaps I should make up a fresh install to see if that help.
And I wonder if it is related to the upgrade of Linux kernel. Does the new kernel use another strategy in dispatching CPU time on tasks so that the user interface does not get enough resources computing while some other tasks are busy ?

---

### Post by DaviesX on 2012-04-14
That problem finally solved using a fresh installation, I think it is better to use a fresh installation than an upgrade :-)

---

### Post by jerrylamos on 2012-04-15
> **DaviesX said:**
> That problem finally solved using a fresh installation, I think it is better to use a fresh installation than an upgrade :-)
Verily.  Once install is working (ubiquity install bugs are legion in launchpad!)  I install as soon as something significant is taking place.

This is a Intel(R) Atom(TM) CPU N455   @ 1.66GHz with no problem with mouse speed.

Early in pangolin I couldn't install because the ubiquity required screen size was greater than 1024x600 with key choices falling off the botton.  That's been fixed, and through the forums found out how to move the screen.  I just didn't know what the problem was until I installed on a 1024x768 screen and saw the options at the bottom.

That said, pangolin won't install on my Thinkpad R31 failing during the copy step - every day's zsync does the same.  Yes launchpad bug written.

I've lubuntu 12.04 running on it because Alpha would install and have been updating since oink oink on disk space with accumulated garbage despite my efforts with synaptic and apt-get clean, autoclean, autoremove ...

Test partitions!  Install often!  Backup!

Jerry

---

### Post by DaviesX on 2012-04-19
> **sudodus said:**
> I think that 'vanilla' Ubuntu is slow because it has too much 'eye candy'.

Either you tweak the desktop environment, so that it will demand less horsepower, or you try other flavours of Ubuntu

- Xubuntu with XFCE has a small foot-print
- Lubuntu with LXDE has an ultra-small foot-print.

- as suggested by *meborc*: install a fresh 'vanilla' Ubuntu 12.04.

Anyway, download iso files for these flavours and try them live before installing.

I have tried Lxde on Ubuntu 12.04. And I felt in love with it at once due to its high efficiency ! Thanks for your suggestion !:)

---

### Post by sudodus on 2012-04-20
> **DaviesX said:**
> I have tried Lxde on Ubuntu 12.04. And I felt in love with it at once due to its high efficiency ! Thanks for your suggestion !:)
You are welcome :-)
I'm glad you like it.

---

