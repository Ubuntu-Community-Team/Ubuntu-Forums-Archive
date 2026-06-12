---
title: "Linux Desktop Responsiveness Patches"
date: 2010-08-07
forum: The Cafe
---

### Post by ibuclaw on 2010-08-07
Original post in phoronix: [http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ)

Someone seems to claim a fix for a long standing issue in desktop responsiveness in Linux.

Upstream Patches:
[Here in 2.6.35]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff_plain;h=5f53e76299ceebd68bdf9495e8ff80db77711236") and [Here in zen-kernel]("http://git.zen-kernel.org/?p=kernel/zen.git;a=commitdiff_plain;h=6d1a3963a64325da2bc5d975c8df2807fc826af5;hp=9fe6206f400646a2322096b56c59891d530e8d51").

It basically ensures that high cost allocations don't thwart the resposiveness of low cost allocations. So you can copy a large file from a Hard disk to a Pendrive, and rest assured your system won't lock up (ymmv).

So I'm curious if anyone has tried it out? Do you notice any improvements?

Attaching a combined patch for 2.6.32 kernels. Applies cleanly to the linux-2.6.32.orig.tar.gz tarball in Debian's repository.


Regards

---

### Post by gnomeuser on 2010-08-07
All the patches have been ACKed, I suspect they will go into .36 soon, then testing will reveal if they cause any regressions and if they really do improve the situation.

I am actually surprised nobody put up a ppa yet.

---

### Post by blueturtl on 2010-08-07
I thought this was precisely the advantage Linux has always held... that running multiple applications simultaneously wouldn't make the system unresponsive.

Sometimes I might be completely oblivious to the fact that a process has gone haywire because even though the CPU usage is capped I can't tell if I am not running a another intensive process that displays a progress bar.

My audio player will never ever skip even if the system is dying.

Which DE does this bug supposedly affect or all?

edit: read the link, I guess I must be running an older kernel than affected...

---

### Post by ibuclaw on 2010-08-07
> **blueturtl said:**
> I thought this was precisely the advantage Linux has always held... that running multiple applications simultaneously wouldn't make the system unresponsive.

Sometimes I might be completely oblivious to the fact that a process has gone haywire because even though the CPU usage is capped I can't tell if I am not running a another intensive process that displays a progress bar.

My audio player will never ever skip even if the system is dying.

Which DE does this bug supposedly affect or all?

edit: read the link, I guess I must be running an older kernel than affected...

When I say YMMV, I honestly do mean exactly that. Some people swear that copying a large file from A to B will cause all light processes to be put "on hold" whilst the copying is undergoing. Others perhaps suffer from system jitters when running two or three tasks at once when suddenly all the system cache is expended and memory is now being juggled about to and from swap, causing heavy delays when performing light desktop activities - clicking on a menu, changing directory in the file browser, refreshing a webpage.

If you don't suffer from these sorts of symptoms, great! If you do, salvation may be on the way to tend to your heavy desktop needs...

---

### Post by phrostbyte on 2010-08-07
I don't remember ever having this problem. Is there a reproducible way to trigger it?

---

### Post by ibuclaw on 2010-08-07
> **phrostbyte said:**
> I don't remember ever having this problem. Is there a reproducible way to trigger it?

According to [https://bugzilla.kernel.org/show_bug.cgi?id=12309](https://bugzilla.kernel.org/show_bug.cgi?id=12309)

```
dd if=/dev/zero of=/tmp/test bs=1M count=1M
```

---

### Post by Kubunteando on 2010-08-10
It helps a great deal.
Now during KDE startup still the system is responsive.
The same when there is heavy Hard disk reading.

Before with the original Ubuntu kernel I could notice severe slowdown when there was heavy hard disk input/out.

So it seems the patch works well.
I had to apply the patch manually.

I have an AMD system with a 785G chipset.

---

### Post by alanwalterthomas on 2010-10-19
I have an Acer Aspire One netbook with the absolutely pathetic 16 GB SSD. The interface grinds to a halt with any disk usage, so I'm very interested in these patches. Even light browsing gives me ~30 second waits.

I want to install UNR 10.10 - with these patches. How do I apply them? What do I do about normal kernel updates?

Thanks,

---

### Post by NightwishFan on 2010-10-20
To be honest, SSDs have great read speed and terrible write speed, so they choke on writes. I think you would be better off running using the deadline scheduler so reads have higher priority, and find ways to reduce writes such as mounting using noatime. I can help you with that if interested, you should probably start a new thread and link me to it.

As for patching, I am not quite sure I could walk you through it so I will leave that to someone else since a few experienced folks are subscribed to this thread. I would ask them if they drop by; did it land in .36? I believe you can use a mainline build of .36 for Ubuntu if it is included.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by ibuclaw on 2010-10-20
As far as I'm aware, it did land in the mainline for the 10.10 release.

I'll have a quick dig about though just to be sure...

---

### Post by alanwalterthomas on 2010-10-21
wow, thanks. I'll be very glad if I can overcome this netbook's ssd problem. I've tried every possible combination of filesystem & scheduler to get this thing to work properly - with very modest results. Any disk activity will "bring the gui to its knees" & the only improvement is that the period of non-responsiveness may be a little shorter. The truth is that this ssd should never have been put into a personal computer; maybe some kind of embedded media device would tolerate it. I think I'll need a bit of help to apply the patches though -

[http://www.phoronix.com/scan.php?page=news_item&px=ODQ3Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODQ3Mw)
   says it's hopeful the patches will make it into .36, but it's too late for 10.10

[http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ3OQ)
   says the patches may work their way back to earlier kernels

[http://www.phoronix.com/scan.php?page=news_item&px=ODU0OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODU0OQ)
   says the patches will probably only make it into .37

I want to run UNR 10.10 with these patches (all of them, from all the sources mentioned in the above articles), but how? (& what do I do about the normal kernel point updates?)

edit: [http://www.phoronix.com/scan.php?page=news_item&px=ODY5NA](http://www.phoronix.com/scan.php?page=news_item&px=ODY5NA)
says the desktop responsiveness patches will go into .37

---

### Post by alanwalterthomas on 2010-10-26
bump

please, any help on getting these patches into 10.10's kernel would be much appreciated.
Thanks

---

### Post by del_diablo on 2010-10-27
Use xorg edgers instead.

---

### Post by alanwalterthomas on 2010-10-28
Use xorg edgers instead?

Why?
What does xorg have to do with patches that deal with disk i/o?

& I'm a noob, so how?

---

### Post by alanwalterthomas on 2010-11-01
bump.

plz, what does xorg edgers have to do with this, how would I use it, & how can I patch the kernel?

thx

---

### Post by Half-Left on 2010-11-01
Well Ubuntu uses a rather conservative setting in that regard. It's a balancing act really. You can set 1000hz in the kernel and enable preemptive desktop.

From what I can see, Ubuntu enables 100hz, which isn't good for responsiveness but good for power management. I'm not sure why it's set so low for a desktop but good for laptops.

---

### Post by ibuclaw on 2010-11-04
> **Half-Left said:**
> Well Ubuntu uses a rather conservative setting in that regard. It's a balancing act really. You can set 1000hz in the kernel and enable preemptive desktop.

From what I can see, Ubuntu enables 100hz, which isn't good for responsiveness but good for power management. I'm not sure why it's set so low for a desktop but good for laptops.

I remember a rant from the main pulseaudio developer about that setting too; which addressed all bug reports related to pulseaudio being slow (pulseaudio is most optimal when the kernel time resolution for processes and threads is set to 1000Hz).

---

### Post by NightwishFan on 2010-11-04
I find pulseaudio to be a bit iffy no matter what the setting is. Though when it works it works great, and is flexible.

Personally I use 1000hz/preempt simply because I it makes up for the terrible via alsa drivers. Perhaps they should review the conf? 1000hz and voluntary preemption is what my custom kernel uses.

I think the biggest issue with performance is disk/memory IO. When memory gets full things get slow. (er than they need to be)

---

### Post by unimatrix on 2010-11-17
Interesting, I've changed it to 1000Hz/preemptive and now pulseaudio network streaming doesn't work anymore.

---

### Post by NightwishFan on 2010-11-17
You might be using full preemption which is said to be iffy with some drivers.

---

### Post by grahammechanical on 2010-11-17
Is it system memory or graphic card memory that is being affected. I had music playing stutter (files on hard disc) when viewing a large PDF document that was actually scanned pages of a lexicon (long "page loading" waits). I now have a new graphic card with 1meg memory and things are a lot faster. 

Regards

---

### Post by weblordpepe on 2010-11-18
zomg i have been suffering this for years! since version 7.04 came out. cant wait to try this to see if it helps me

---

