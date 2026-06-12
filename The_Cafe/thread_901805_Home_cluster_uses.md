---
title: "Home cluster uses?"
date: 2008-08-26
forum: The Cafe
---

### Post by dhysk on 2008-08-26
I have 3 very old computers P3's few MB of ram yes MB, and maybe 20-30 GB of hard drive space all together.  Basically my question is this.  If I were to spend the time to make them into a cluster what could I use it for?  Would it be worth it?

And please no, you could do #insert comment here# with them instead.  I'm just wondering if I could do anything useful/fun with a cluster of 3 possibly 4 old computers.  Given the age/specs of these computers I'm not even sure if they could do anything my dual core laptop couldn't.  But I've never seen/used/built a cluster before so I figured I would ask you fine individuals before trying.

Computers 

P3 600MHz with 384MB ram(3x pc133 128MB sticks)

P3 500MHz with 64 MB ram @100MHz

Intel Celeron 533MHz with 64 MB ram @100MHz

possibly an: AMD xp2600+ OC'ed 2.4GHz with 1GB ram

---

### Post by zmjjmz on 2008-08-26
I have quite a few more computers of greater age, and I was considering using the CHAOS Linux distribution in combination with ClusterKnoppix.
Of course, I have no clue how to do this.

---

### Post by happyhamster on 2008-08-26
> **dhysk said:**
> I have 3 very old computers P3's few MB of ram yes MB, and maybe 20-30 GB of hard drive space all together.  Basically my question is this.  If I were to spend the time to make them into a cluster what could I use it for?
For fun, I would say.

> Would it be worth it?
If having fun is enough, then yes :)

> 
And please no, you could do #insert comment here# with them instead.  I'm just wondering if I could do anything useful/fun with a cluster of 3 possibly 4 old computers.  Given the age/specs of these computers I'm not even sure if they could do anything my dual core laptop couldn't.
A modern dual core would very likely out-perform a cluster of those by a wide margin (and it would be cooler, quieter and in need of less power). 


> Computers 

P3 600MHz with 384MB ram(3x pc133 128MB sticks)

P3 500MHz with 64 MB ram @100MHz

Intel Celeron 533MHz with 64 MB ram @100MHz

possibly an: AMD xp2600+ OC'ed 2.4GHz with 1GB ram
A cluster of those four would behave more or less like the single AMD I think (I'm assuming it is the fastest of the bunch). Basically, in a cluster you want equal: cpu power/RAM per cpu core/io-bandwith. And of course multi-threaded stuff to run on it.

Here's an interesting page on clusters:
[http://www.clustermonkey.net//content/view/211/1/](http://www.clustermonkey.net//content/view/211/1/)

---

### Post by LateNiteTV on 2008-08-26
if i were you id do it just for the hell of it.

---

### Post by Erdaron on 2008-08-27
[IMG]http://imgs.xkcd.com/comics/network.png[/IMG]

You could donate their uptime to a distributed project, something from BOINC.

---

### Post by r+9 on 2009-10-01
(it's too bad this thread is so old, but I want to dig it up)

I'm all set to put together a cluster but I can't figure out why, like what problems would I solve.  I'm not really into graphics or video, and I intend to build my cluster using a tuple-space model so integrating with other cluster projects (SETI@HOME) would be awkward at least at first.

It is true, lots of newer systems are way more powerful than clusters of old systems.  I'm mostly interested in the learning involved in building it.  But I'd like to do something useful(or exciting or both) too.

So to restate my question: What sort of problems are clusters being used to solve, and how might I go looking for a problem I could solve with a cluster.

---

### Post by Firestem4 on 2009-10-01
> **r+9 said:**
> 

So to restate my question: What sort of problems are clusters being used to solve, and how might I go looking for a problem I could solve with a cluster.

Clustering can be used for anything that you can/want to get to run. I've seen a cluster of linux servers powering Quake 4 running on 24 monitors lol.

If you like distributed computational programs like Folding@Home, clustering is a great way to improve performance by leveraging all 3 computers at once. But this is semantic. You can have 3 computers run 3 different projects and have them complete equally, or have 3 computers finish 1 project theoretically faster. It depends on what you want to do.

Plus, you are tripling your effective processors and memory so that application you just don't have enough ram for on a single station, now you do!

I personally want to test out clustering as a personal project to try and devise a high-availability system where if 1 goes down the other two immediately recover the lost share so I can no downtime. Server farms are just this, Highly redundant and replicated.

---

### Post by openfly on 2009-10-01
Uhm don't look for a use for equipment.

DO SOMETHING then use equipment to do it better after that.

or in short,

YOU ARE DOING IT WRONG.

---

### Post by chrisjsmith on 2009-10-01
Throw the kit away and go out :)

---

