---
title: "System 76 Lemur automatically upgraded to 11.04?"
date: 2010-12-18
forum: System76 Support
---

### Post by marksandler on 2010-12-18
hey guys, it is a weird question, but mu wife's laptop now proudly displays 11.04 as its operating system (yep, released in April 2011, as it says). It was never manually upgraded, (my wife is the primary and only user and no way she would do a dist upgrade, without remembering it) and all the updates are received in automatic mode. 

I presume it is way too early for automatic push to 11.04, so i was wondering, how this could have possibly happen and has anyone else experienced this?  If it helps, the laptop is about 2 month old.


Thanks!

---

### Post by Noah0504 on 2010-12-18
I honestly have no idea how this could have happened without user intervention.  To upgrade to a normal release, permission needs to be given by the user with their password... I don't want to point any fingers, but maybe she did it?  :P

---

### Post by 3Miro on 2010-12-19
You would have to enable unstable updates and then do a dist-upgrade. The download is about the size of a CD (700MB) and it will take quite some time to install. Furthermore, 11.04 comes with the new Unity interface for all versions and it would look very different.

Logout the see if you can select "Unity". Also try:
```
uname -a
```
to see if you are running kernel 2.6.35 or 2.6.37. It is possible that something it only thinks it is 11.04 and not actually being 11.04.

---

### Post by Dave_L on 2010-12-19
Also check the output from this shell command:

```
lsb_release -a
```

---

### Post by Eldera on 2010-12-19
There is some information on this in other parts of the forum. Apparently it is some kind of bug.

[post]10254636[/post]

[thread]1648262[/thread]

Now you and your wife can relax and have a great day.

---

