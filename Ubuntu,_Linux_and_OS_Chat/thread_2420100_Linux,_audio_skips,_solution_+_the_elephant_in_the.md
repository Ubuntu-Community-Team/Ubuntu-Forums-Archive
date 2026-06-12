---
title: "Linux, audio skips, solution + the elephant in the room"
date: 2019-05-30
forum: Ubuntu, Linux and OS Chat
---

### Post by charlieg on 2019-05-30
I just bought a new PC, the fastest I have ever owned by a mile (an i9, 16gb RAM, SSD etc). The only thing it lacks is a dedicated graphics card; it's for software development so I don't need one. I bought it with 18.04 installed (since upgraded to 19.04).

I fire it up, start some YouTube videos in the background, and get to doing some programming (Eclipse). The audio periodically skips. FML.

Long story short, I remember something I used to follow more closely - [Con Kolivas' work on process and IO scheduling](http://ck-hack.blogspot.com/). After some investigating I install the [Liquorix kernel](https://liquorix.net/).

Magic, no more audio skips. :p ;)

I'm pretty sure that if you have a dedicated graphics card then you'll probably not suffer this problem, but the fact it is still a problem on such modern hardware with integrated graphics is galling. Why is this still a problem with modern Linux? Why is the default kernel so poorly set up for such an average/typical system? Ubuntu surely targets the average user as a desktop experience, right? It's frankly ludicrous that this is still a problem.

When Con Kolivas took his solutions to the Linux developers, he was pilloried. Almost immediately somebody wrote up an alternative scheduler that was [promptly promoted](https://linux.slashdot.org/story/07/07/28/1836247/torvalds-explains-scheduler-decision) to the main scheduler despite largely failing to address the problems that Con Kolivas' work actually solved.

It would be nice for a power player (like Ubuntu) to investigate Con Kolivas' patches and even use them.

---

### Post by DuckHook on 2019-05-30
Who does one cater to? The corporate/SOHO/general user who wants reliability and stability, or the gamer/multimedia user who wants minimal lag and low-latency response?

It's the question that every distro has to answer. Apparently, one cannot have both because the low-latency kernel build necessarily sacrifices redundancies and memory overhead that are used to safeguard and segment important parts of kernel space. This is all hearsay; I'm not a dev of any sort much less a kernel dev. If memory serves, Con Kolivas' work was rejected because it did not address these concerns to the kernel maintainers' satisfaction. I can't find it now, but I recall this being reported briefly some time ago in diff-u on Linux Journal.

Moreover, Ubuntu already has a [low-latency kernel]("https://packages.ubuntu.com/bionic/linux-image-lowlatency") that can easily be installed in lieu of the standard kernel. No need to install Kolivas's (though you are free to do so for reasons of your own). However, installing the official low-latency kernel would preserve ongoing official support.

---

### Post by CatKiller on 2019-05-31
Prioritising low-latency deprioritises things like power-saving, speed, and predictability. It's not a good fit for every, or even the general, use case. It's trivially simple to install the low-latency kernel if your use case is one that would benefit from it. 

With adequate and appropriately-configured hardware audio doesn't skip when using the generic kernel.

---

### Post by charlieg on 2019-05-31
[QUOTE=CatKiller]With adequate and appropriately-configured hardware audio doesn't skip when using the generic kernel.[/QUOTE]

Ok Cersei. Sip your wine then. I literally just told you it skips audio (not just on YouTube, on any audio application it seems, I got skips on music and movies) on a very modern i9 PC.

How should I "appropriately configure" it? What is "adequate" to you?

[QUOTE=DuckHook]Who does one cater to? [/QUOTE]

A sensible question. Well I think the answer is easy, for Ubuntu.

Ubuntu Desktop should produce a system that doesn't perform so badly out of the box. As I request here.

Ubuntu Server, stick with the generic kernel configured to be great on the kinds of PCs kernel developers get to use (idiotically beefy ones).

[QUOTE=DuckHook]Moreover, Ubuntu already has a low-latency kernel that can easily be installed in lieu of the standard kernel. [/QUOTE]

That's not exactly an obvious thing to come across.

Moreover, that just shouldn't be required by desktop users. I don't recall ever having to install a low latency kernel on Windows just so I can play music or watch YouTube without my audio skipping like a kangaroo.

---

### Post by CatKiller on 2019-05-31
> **charlieg said:**
> Ok Cersei. Sip your wine then. I literally just told you it skips audio (not just on YouTube, on any audio application it seems, I got skips on music and movies) on a very modern i9 PC.

How should I "appropriately configure" it? What is "adequate" to you?
So that it doesn't skip :rolleyes:

This isn't an "I'd like help with my skipping audio" thread, this is an "I want to whinge about the default kernel configuration" thread, but in your case you could have tried not resampling audio in software at the same time as running non-hardware-accelerated video, at the same time as you're running some other variable-workload task. If you'd wanted. 

Or you could continue to pretend that **every** Ubuntu user for the past 15 years has had their audio skip because of malice, and no one's ever said anything until you bravely stepped forward, if you prefer.

---

### Post by QIII on 2019-05-31
Civility is appreciated.

Hasty generalizations and sarcastic responses to them are not.

Please avoid causing the Staff to close this thread.

---

