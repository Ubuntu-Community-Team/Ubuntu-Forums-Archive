---
title: "Still No Updates on 13.04 Yet?"
date: 2013-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2013-05-06
Well, i did get one (a kernel update) a few days after installing 13.04 (I installed about a day or two after it was released)....but since then, have not seen any...My updater seems to be checking every morning, but whether it checks automatically or i run it manually, it seems to check but just says that i am up to date...

I know it can be a bit quiet for a while after a release, but just curious...anyone been getting updates?   I am running the standard ubuntu with unity desktop...
Just wanted to be sure there wasn't anything wrong on my side, here...

Thanks :)

---

### Post by monkeybrain2012 on 2013-05-06
Nope, not for me either, only an upgrade for Skype last week which fixed the Skype not starting problem which was all over the places a little while back. Haven't got anything before or since except for the kernel upgrade you mentioned.

EDITED: I am sure it is not a problem on my end because I have added the Compiz enhanced performance experimental ppa and for that I get almost daily updates (so one day it is going to break my system. :))

---

### Post by lovebluesky2009 on 2013-05-06
not for me yet,

---

### Post by craig10x on 2013-05-06
That is a relief to hear (LOL) :)

I had been running 13.04 while it was in development (and re-installed after the final was released)...i guess i was so accustomed to getting daily updates there (in fact, if i checked there was even updates in the afternoon too)...that it seemed a bit strange not to get any for a while...of course, development is a whole different "bag"...;)

---

### Post by pqwoerituytrueiwoq on 2013-05-06
@craig10x
it is time to test ubuntu 13.10 saucy salamander out
```
sudo sed -i 's/raring/saucy/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get dist-upgrade
```

---

### Post by craig10x on 2013-05-06
Trying to tempt me back there, eh? ;) :D

---

### Post by craig10x on 2013-05-07
Quick follow up:  Update Manager brought up updates this morning...first ones after about a week of quiet...

---

### Post by slickymaster on 2013-05-07
> **craig10x said:**
> Trying to tempt me back there, eh? ;) :D

Do feel tempted. I've been using it for almost two weeks now. And it keeps running completely smoothly, besides a hick-up here and there.
```
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.9.0-030900rc3-generic
```

---

### Post by craig10x on 2013-05-07
@slickymaster:  sounds like it's going mostly as smooth as 13.04 development did...
I had actually tried to get my sources switched over when 13.04 finalized but things got kind of all messed up and i ended up re-installing from 13.04 final....

I wish they had that easier way in place to have it automatically "point" to the next version, but i know they haven't implemented that yet...and i am kind of "gun shy" about trying the terminal commands method of switching the sources again...and i am told that trying to do the upgrade via the update manager can be problematic...

---

### Post by monkeybrain2012 on 2013-05-07
> **craig10x said:**
> 
I wish they had that easier way in place to have it automatically "point" to the next version, but i know they haven't implemented that yet...and i am kind of "gun shy" about trying the terminal commands method of switching the sources again...and i am told that trying to do the upgrade via the update manager can be problematic...

It would be nice if you can choose which repo (unstable, testing, stable etc) to point to by setting priorities in  /etc/apt/preferences like in Debian. : ) It may be a thing to consider as Ubuntu seems to be moving to a similar release structure (13.10 is like "experimental" )

---

### Post by craig10x on 2013-05-07
Yes, that would be very nice...i guess i will have to "keep an eye" on 13.10 development...perhaps they will add something in it, or offer a new simpler option to "roll" with it (as they mentioned they were working on) before 13.10 goes final...If they do, i could then consider installing a 13.10 daily build before it goes final and "roll" into 14.04....

---

### Post by slickymaster on 2013-05-07
> **craig10x said:**
> @slickymaster:  sounds like it's going mostly as smooth as 13.04 development did...

So far everything points in that direction. Apart from a few problems with the update-manager and software-properties-gtk packages, promptly solved with the upgrade to the 3.9rc3 kernel, haven't had any problems so far.

---

### Post by castrojo on 2013-05-07
It's because things go into -proposed first for a while before they roll out: 

- [http://askubuntu.com/questions/288177/why-am-i-not-receiving-any-updates](http://askubuntu.com/questions/288177/why-am-i-not-receiving-any-updates)

---

