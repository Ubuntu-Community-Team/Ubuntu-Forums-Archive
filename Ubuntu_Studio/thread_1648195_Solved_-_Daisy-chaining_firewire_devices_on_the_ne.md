---
title: "Solved - Daisy-chaining firewire devices on the new stack!"
date: 2010-12-18
forum: Ubuntu Studio
---

### Post by trulan on 2010-12-18
Finally cracked this one today.

Since the new JuJu firewire stack is enabled by default in Ubuntu 10.10 and will be the only option in 11.04, I've been testing it extensively.  The last remaining hurdle was daisy-chaining, or using more than one firewire audio device at a time.  And I can finally report success on getting this to work in both Ubuntu 10.10 and 11.04.  This is written assuming you already have one device working on the new firewire stack.

Basically, we need to upgrade libraw1394.  But first, you'll need a kernel 2.6.36 or newer, and kernel headers to match.  I am currently using liquorix:
[http://techpatterns.com/forums/about1212.html](http://techpatterns.com/forums/about1212.html)
but anything 2.6.36 or newer should work.

After you've got your new kernel up and running, download the libraw1394 2.0.6 source:
[https://ieee1394.wiki.kernel.org/index.php/Release_Notes_-_Libraries](https://ieee1394.wiki.kernel.org/index.php/Release_Notes_-_Libraries)

Then, extract it, and in a terminal go to its directory.  Configure it like this:
```
./configure --prefix=/usr --with-fw-dir=/usr/src/linux-headers-$(uname -r)/include/
```**Important:** For this to work, you must be running a 2.6.36 kernel and have the accompanying headers installed.

Then, run
```
make
``````
sudo make install
``````
sudo ldconfig
```And that should be it!  Merry Christmas!

---

### Post by AutoStatic on 2010-12-18
Nice!!! And good to know also that these Liquorix kernels have this cgroup stuff disabled apparently: [http://jackaudio.org/linux_group_sched](http://jackaudio.org/linux_group_sched)

Best,

Jeremy

---

### Post by trulan on 2010-12-18
Liquorix did have some cgroup stuff enabled for a bit, but it has been removed again due to some quirky bugs.  Even when it was implemented there it didn't break anything for me.

Edit:  Wait, that was sched_autogroup, not cgroups.  I'm not exactly a kernel hacker.  :wink:

I won't pretend to understand what cgroups are or what they do.  And another thing I don't understand - while this has not to my knowledge caused an issue in Maverick, it sure is a pain in Natty.  Hopefully somebody comes up with a solution before 2011-04 or anybody who wants to use Jack in Natty is going to need to install a non-standard kernel.

---

### Post by AutoStatic on 2010-12-18
I don't grok that stuff either, but I do keep an eye on it through the jack-devel mailinglist. Hefty discussions but also some fruitful results, there's already a patch available that allows JACK to work with cgroups.

---

### Post by cchhrriiss121212 on 2010-12-18
off-topic: 
Hey Trulan,
Can I ask how you are getting on with the Liquorix kernel? I have been using it for the past few weeks with good performance, but it has iffy stability (occasional freeze ups every few days).
I just upgraded to 2.6.36-2 the other day and have had no freezing so far, so maybe it was just a temporary thing? It performs just as good as the rt kernel for audio work on my machine, but I'd like to know whether I can count on it or not.

---

### Post by trulan on 2010-12-18
The only real problem I've had with the liquorix kernels has been with my wireless card - a broadcom 4312lp-phy (or 4315) which I've learned is probably worth more as a guitar pick than as a wireless card.  But even that I've gotten to where it's working most of the time.

Liquorix tends to change a lot from day to day, and there was a recent release (2.6.36-2.dmz.2 I believe) that was a real dud for anything 64 bit.  So far 2.6.36-2.dmz.5 looks nice and solid.  I've been rebooting a lot lately - doing a lot of testing - and I haven't had anything running for more than a few hours at a shot, so I can't realy comment on long-term stability.  I agree it is comparable to the rt kernel in perfomance, and when combined with the new firewire stack it easily outperforms my older setup.  I haven't had any other problems with it.

---

