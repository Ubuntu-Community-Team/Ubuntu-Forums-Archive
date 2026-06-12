---
title: "dist-upgrade or fresh?"
date: 2005-10-07
forum: The Cafe
---

### Post by hardwarder on 2005-10-07
I'm having a slight conflict with myself about this lately.
What are the pros and cons of each? A bit hard to decide for me :P

---

### Post by Geekboy on 2005-10-07
I thought the biggest benefit of Ubuntu (and other Debian distros) was being able to just dist-upgrade rather than reinstall.

---

### Post by aysiu on 2005-10-07
That is a big benefit, but sometimes people just like things "clean." Maybe you have too much residual crud that you don't feel like cleaning out and you also want to see the new installer in Breezy. As long as you have a separate /home partition, a clean install isn't so bad. In fact, it may take less time than a dist-upgrade (sure, it takes time to download the Breezy ISO, but once you have it downloaded, you can use it many times--even use it for friends--the dist-upgrade you can use only on your computer).

---

### Post by Cirkus on 2005-10-07
If you can afford to do a fresh backup, do so. It's almost always better (apt-get dist-upgrade is wonderful, but not perfect).

---

### Post by Zelut on 2005-10-08
I originally did the dist-upgrade and things worked fine but had a few bugs.  I did a fresh install and things worked a bit more smoothly.  I agree with aysui, its smart to have /home as a seperate partition so you can update everything and and keep your personal files.

---

### Post by hardwarder on 2005-10-08
Heh, good that i have it on a separate partition then:) Thanks for the suggestions.

---

### Post by Goober on 2005-10-08
I say fresh.  Although, I just made another 40 Gig partition on my 160 Gig HD for 5.10, and put it on there, and still have Hoary floating around.  I have noticed that Breezy has run a lot faster and smoother with a fresh install then my Hoary install, and that I dist-upgraded from Warty.  I definitely reccomend a fresh instal.  

Also, for me, at least, Breezy automatically mounts my Hoary partition, which is extremely convenient.

---

### Post by agger on 2005-10-08
I'll do a dist-upgrade, since I think it ought to work and a fresh install should be unnecessary. Also, I don't have my /home on a separate partition (but I could always burn it to a DVD, of course).

My plan is to do a dist-upgrade and see how it goes, and if something goes awry report it on the Ubuntu Users list to provide feedback.

---

### Post by heimo on 2005-10-08
To add my obvious observation: Backup is smart idea before any major upgrade (and periodically in any case). I would suggest to use dist-upgrade, but to prepare for clean install if anything goes wrong (if you have the bandwidth, burn a CD first, it's good idea to have it available anyway). dist-upgrades work generally fine and the most common problems can be quite easily solved using dpkg and apt -tools.

The best tool to keep available (if possible) during dist-upgrade is another computer with working internet connection. If anyone encounters problems with dist-upgrade it's very good idea to do as agger says - share your experience so that bugs can be fixed and others learn and can prepare / use work-arounds.

---

### Post by Leif on 2005-10-08
I'm guessing I'm in the minority here, but after messing up my computer, I tried installing breezy preview, which did not recognize my audio hardware correctly. so I reinstalled using hoary, dist-upgraded, and everything works nice & smooth.

---

