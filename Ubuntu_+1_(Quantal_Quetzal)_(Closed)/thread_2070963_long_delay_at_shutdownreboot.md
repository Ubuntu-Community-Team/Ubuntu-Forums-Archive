---
title: "long delay at shutdown/reboot"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lucazade on 2012-10-14
there is a long delay when shutting down or restarting the system.
it looks like the network-manager service hangs when stopping in init6.

* Asking all remaining processes to terminate... [OK]
* Killing all remaining processes... [fail]
nmdispatcher.action caught signal 15 shutting down ...

If I manually stop the network-manager service before shutdown/restart then everything works fine

this bug is probably related to this old one (solved in 12.04):
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)

new bug reported:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484)

---

### Post by sammiev on 2012-10-14
I was shutting down in 3 seconds with 12.10 until a week a go. Now it's about 15 seconds. With 12.04 my 4 laptops all stopped shutting down a few months after it was released. I hope 12.10 doesn’t follow 12.04. It's does seem to be with Network Manager.

---

### Post by dino99 on 2012-10-14
same thing here too: stop a few seconds at "remaining services" and have also some initctl unknown jobs (K20plymouth K20networking).

using bum, i've uncheck them (K20...) so now its cleaner, but still not perfect.

---

### Post by techvish81 on 2012-10-15
> **sammiev said:**
> i was shutting down in 3 seconds with 12.10 until a week a go. Now it's about 15 seconds. With 12.04 my 4 laptops all stopped shutting down a few months after it was released. I hope 12.10 doesn’t follow 12.04. It's does seem to be with network manager.


+1

---

### Post by VinDSL on 2012-10-15
A couple of thoughts...

Yes, shutdown/reboot is V slow on 12.10!  I don't know why this is, however, I've noticed there is a torrent of HDD activity during shutdown.  Sometimes, my HDD activity light is lit-up solid for several minutes.  And, it's particularly slow and lumbering if I've been using Banshee (a Mono app).

I've also noticed that the length of time it takes to shutdown/reboot, and the amount of HDD activity that takes place seems to be directly related to how much time I've spent in a session.  If I've only been in a session for a few minutes, shutdown/reboot is very quick.  If I've been in a session for (say) 12 hours, it takes a considerably longer amount of time to shutdown.  Sometimes, I leave the room, and come back later, to make sure my PC shutdown -- that's how long it takes.

As an aside, I booted into Ubu 10.10 last night, to make sure my new Conky script worked on Gnome 2/Linux 2.6.  I was shocked at how fast it shutdown when I was done! So, it is not hardware related.

---

### Post by philinux on 2012-10-15
This network manager thing hanging is a pain shutting down. It gets fixed only to creep back in again and again.

I've added myself to the new bug.

---

### Post by lucazade on 2012-10-15
> **philinux said:**
> This network manager thing hanging is a pain shutting down. It gets fixed only to creep back in again and again.

I've added myself to the new bug.

:) A never ending story ...

---

### Post by DogMatix on 2012-10-15
I get a similar problem trying to restart (ie. after an update requiring so). I have to shutdown completely and reboot. Selecting 'restart now' ends in a black screen hang. Unless I disconnect network before doing so. I have added 'me too' to a bug report.

---

### Post by baizon on 2012-10-16
Affects me too. Hope it will be fixed soon.

---

### Post by lisati on 2012-10-16
Seeing this thread stirred recollections of another thread: [http://ubuntuforums.org/showthread.php?t=1134201](http://ubuntuforums.org/showthread.php?t=1134201)

---

### Post by nairias on 2012-10-16
+1, despite having vertex4 ssd on sata3, noticeably longer than 12.04

---

