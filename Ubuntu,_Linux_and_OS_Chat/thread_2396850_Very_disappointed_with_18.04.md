---
title: "Very disappointed with 18.04"
date: 2018-07-21
forum: Ubuntu, Linux and OS Chat
---

### Post by ship22 on 2018-07-21
I don't know if ubuntu designers or developers even peruse these forums but I just want to say that I've used Ubuntu since it's earliest release days. This release has been by far the most problematic that I have experienced. I migrated a system that was running 16.04 and loaded 18.04 from scratch (wiped and formatted everything except for /home)

The system was working ok on 16, but I wanted to bring it up to date. Now:

- It takes minutes to boot, where previously it was about a minute or less.
- It hangs on reboot. Must be hard-reset to reboot.
- mounts.. i used to have like 4. Now I have 34 loop devices? 
- Can't get bluetooth to work as of the last update.

Granted, I'm sure there is a fix. I'm sure I'll resolve them eventually, just don't have the time to screw with it right now.  I use linux because I like that it *can* be fixed and I enjoy tinkering, but tinkering with stuff that works. Not so with 18.04. Searches for these problems yeild pages of other people having the same issues and the few rabbit holes I've gone down to try and fix with posted suggestions are as ineffective for me as the OPs.

This release just seems thrown together.. sloppy. I don't know if they lost some good leadership over at Ubuntu or gained some very bad design leadership, but something has changed.. and not for the better. This posting is not a cry for support. It's a comment on the product.

---

### Post by QIII on 2018-07-21
Every release since I started with Warty has been called "the worst ever".  It is often tempting to generalize everyone else's experience based on yours.

I have several machines, desktop and server, running 18.04 without issue.  Everyone's mileage varies.

Please take the opportunity here to get support.

By the way:  No, Canonical's developers don't hang out here.  Just us volunteer end-users.

---

### Post by bodhin2 on 2018-07-21
and i have been very impressed. it has come a long way since the first release...  i had way too many issues getting a few major things working.

---

### Post by ajgreeny on 2018-07-21
Bear in mind that the default DE of Ubuntu has changed between 16.04 and 18.04 from unity to gnome so a lot of things work differently; this may well be part of your new dislike of 18.04.

Can you also show us the output of ```
uname -a
``` in terminal as there was a problem with kernel 4.15.0-24, now withdrawn from the repos, which caused a very slow boot. An update of the kernel to 4.15.0-29 which arrived today for me might help overcome your slow boot problem.

---

### Post by VMC on 2018-07-21
```
systemd-analyze blame --order
``` for starters, concerning the boot times. But since we're in chat does it matter...

---

### Post by ship22 on 2018-07-21
yes I am running 4.15.0-24, downloading the update now. Thank you!

---

### Post by coffeefiend on 2018-07-24
I don't really have much to base my opinions on because I have only used 17.10 and 18.04, but I haven't found much to be disappointed about. Especially considering before giving Linux a try, I have been a Windows baby my whole life. The only real issue I have had so far is that I had to use a wifi dongle with my HP laptop to get connectivity. But that is because my onboard NIC is Realtek, and they, for whatever reason, do not support Linux. Get with the program, Realtek!

---

