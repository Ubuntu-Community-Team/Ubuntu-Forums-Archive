---
title: "Saving Ubuntu Server installation"
date: 2009-06-22
forum: Server Platforms
---

### Post by trillex on 2009-06-22
Heya,

The other day I heard my system drive make loud "clonk" noises and decided it was well about time to back it all up and replace the damn. The problem is, that I don't really have a means of "cloning" the drivers other than I got a Windoze machine about, where I can back up my ubuntu drive to.

How is this best done?

My server layout is like this:

500 GB system disk, like 5 GB used.
3x1 TB storage disks, mostly full. 

I don't have an image server handy and I'm having problems understand just how dd works. 

I'm new in general, so it might need to be cut out in cardboard. A newbie in training.

---

### Post by Cheesemill on 2009-06-22
For the system drive I suggest using [CloneZilla]("http://clonezilla.org/"), you'll probably be able to fit the entire backup onto one DVD.
For the data drives you can just do a simple copy onto external media, although having 3x1TB drives without a backup in place is asking for trouble. One of these days your drives **will** fail.

---

### Post by HermanAB on 2009-06-22
Howdy,

See this: [http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

---

### Post by trillex on 2009-06-27
Welp, thanks for the help. :) My system drive took a dive for it already before being able to back it up. Hopefully it should be relatively easy to get back up.

---

