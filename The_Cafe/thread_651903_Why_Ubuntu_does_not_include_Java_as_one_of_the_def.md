---
title: "Why Ubuntu does not include Java as one of the default package in its distribution"
date: 2007-12-28
forum: The Cafe
---

### Post by tunyawat on 2007-12-28
I'm wondering why Ubuntu and other major Linux distro does not include Java as one of the default package in their distribution. Has Java been opensourced? Does Ubuntu has plan to include Java in its future distribution?

---

### Post by LaRoza on 2007-12-28
Why doesn't Windows?

It is easy to install, kind of large, and isn't free speech so it makes sense it isn't an an operating install disk.

---

### Post by Majorix on 2007-12-28
> It is easy to install, kind of large, and isn't free beer so it makes sense it isn't an an operating install disk.

Its not large. Its only like 20mbs, while OpenOffice which made it into the Ubuntu disk is like 150mbs.

And it IS free as in beer, just not free as in speech.

At OP, I believe the main reason is just what I said above this line,

---

### Post by BreathEasy on 2007-12-28
Probably legal reasons. Ever noticed when installing Java you have to accept a license agreement - if installed manually it's presented in a terminal, if installed using apt-get or Synaptic it's with a GUI where you have to click accept. The EULA is seperate from Ubuntu and hence what Canonical can support.

---

### Post by DjBones on 2007-12-28
they could include the open-source java (ie 'IcedTea') which is in the repo's at the moment..
i'm sure theres a good reason why its not though.

maybe the dev's didn't think java was essential?

---

### Post by LaRoza on 2007-12-28
> **Majorix said:**
> 
And it IS free as in beer, just not free as in speech.


That is what I meant, post fixed.

---

### Post by LaRoza on 2007-12-28
> **DjBones said:**
> 
maybe the dev's didn't think java was essential?

It isn't. It is only missed if you are on the internet, in which case, you can download it anyway.

The real missing package complain lies with build-essential, which should be installed by default.

---

### Post by BreathEasy on 2007-12-28
> **LaRoza said:**
> It isn't. It is only missed if you are on the internet, in which case, you can download it anyway.

The real missing package complain lies with build-essential, which should be installed by default.

I agree 100% with all of this. Even though my 64-bit Ubuntu doesn't have a proper Sun Java plugin, I don't care cos it's rarely required for anything these days, and build-essential is kinda... essential in a lot more cases.

---

### Post by LaRoza on 2007-12-28
> **BreathEasy said:**
> I agree 100% with all of this. Even though my 64-bit Ubuntu doesn't have a proper Sun Java plugin, I don't care cos it's rarely required for anything these days, and build-essential is kinda... essential in a lot more cases.

It is on the CD, that is very handy, but I can't figure out why it isn't installed.

(You can install it without the net)

---

### Post by tunyawat on 2007-12-28
OK, I got it. Since Java is not a proper opensourced project, that's why it never been included by default.

---

### Post by Majorix on 2007-12-28
Not too many people are programmers.

There is a popularity contest feature with Ubuntu, and the packages on the cd and packages installed by default are selected according to this.

We need more programmers to send their usage data to Canonical :D

---

### Post by LaRoza on 2007-12-28
> **Majorix said:**
> Not too many people are programmers.

There is a popularity contest feature with Ubuntu, and the packages on the cd and packages installed by default are selected according to this.

We need more programmers to send their usage data to Canonical :D

Considering that almost all Linux software is distributed (or can be) with source, including Linux itself, the C compiler and libraries are needed. 

You don't have to be a programmer.

---

### Post by Majorix on 2007-12-28
However you don't immediately need it. You should be fine with just the "apt-get install" feature.

Don't get me wrong, I also want this package to be added, mainly because I program in C under Ubuntu from time to time.

---

### Post by LaRoza on 2007-12-28
> **Majorix said:**
> However you don't immediately need it. You should be fine with just the "apt-get install" feature.

Don't get me wrong, I also want this package to be added, mainly because I program in C under Ubuntu from time to time.

They main problem I find is that other distros install it, except a few. And I am surprised Ubuntu is one of them.

---

### Post by Majorix on 2007-12-28
Like I said, with the popularity feature of Ubuntu, obviously not enough people send their usage data about build-essential to the servers. I for one do send mine, so if any of you wants some package (be it build-essential or anything) just send your usage data (I believe it is set to off by default, you have to enable it in Software Sources) and hope for the best.

OT, I believe it's impossible to get Java RE on the default install, even if every single user uses it, because of legal reasons explained before.

---

