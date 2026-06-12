---
title: "How to autofix disk errors on startup"
date: 2011-06-22
forum: Server Platforms
---

### Post by icedown on 2011-06-22
I have a server that, due to the amount of data it's moving, tends to trash up the hard drive when I have a power outage or crash.  It doesn't have a keyboard or monitor attached to it normally so it's a real pain when I have to boot it back up.  I have to hook one up just to hit F to have it fix all the errors.  Is there a way to have it do this automatically on boot rather then having to confirm it?

---

### Post by brettg on 2011-06-22
I can't help with your direct question, but I would recommend that you get yourself a UPS if you are having that many power outages. 

As for "crashing", your server shouldn't be doing that. If it is you need to figure out why and fix it.

Just having it press "F" automatically for you is a bandaid fix, and a poor one at that.

---

### Post by icedown on 2011-06-22
I do have a UPS, but it can't hold through the long outages.  And as far as the crashes, I'm asking a bit much from the computer.  I'm surprised it holds out as well as it does.  

If I had the money to fix it the correct way, I would have done it already. I already have it so that every time it boots it cleans out the spool area's, checks and fixes errors, and remounts everything prior to restarting the data feed.  It's just getting to that point that is the issue.

---

### Post by Eteif 1 on 2012-08-27
if someone still interrested 

set in file: /etc/default/rcS

FSCKFIX=yes

---

### Post by Gompa on 2012-08-27
are you using the ups as a graceful shutdown method ?
or are you using the ups as backup power supply until the power is back ?

---

