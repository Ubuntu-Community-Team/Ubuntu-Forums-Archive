---
title: "benchmarking for n0obs"
date: 2009-09-03
forum: The Cafe
---

### Post by joey-elijah on 2009-09-03
I want to do some simple benchmarking for applications on Ubuntu

how long they take to start/open
cpu usage
ram usage

and well, that's it!

I installed the Phoronix suite (after wrestling with error after error) but it doesn't seem to be much help/seem to work.

Are they any simple CLI tools that would work better?

Fankooo's

---

### Post by gnomeuser on 2009-09-03
benchmark isn't what you want, benchmark is the pseudo science of boiling a whole system with wildly varying bottlenecks and performance that is dependent on the task and what else the system is doing at the time.. in other words impossible.

Generally data extraction is easy which is what you describe you want, top e.g. gives you an overview of cpu and memory usage over time, it's not reliable as there are underlying designs that factor in (so it might be lying about how much RAM is actually being used but not how much is allocated for that process e.g.).

Startup time for applications can be done with time, but it requires the application to quit immediately after having fully loaded. This however is not a useful thing for an application to do so your metric will be screwed provided this option isn't available or you are unable to modify the code to do so.

---

### Post by joey-elijah on 2009-09-03
> **gnomeuser said:**
> benchmark isn't what you want, benchmark is the pseudo science of boiling a whole system with wildly varying bottlenecks and performance that is dependent on the task and what else the system is doing at the time.. in other words impossible.

Generally data extraction is easy which is what you describe you want, top e.g. gives you an overview of cpu and memory usage over time, it's not reliable as there are underlying designs that factor in (so it might be lying about how much RAM is actually being used but not how much is allocated for that process e.g.).

Startup time for applications can be done with time, but it requires the application to quit immediately after having fully loaded. This however is not a useful thing for an application to do so your metric will be screwed provided this option isn't available or you are unable to modify the code to do so.

So i'd be better off just casting my eye over system monitor and seeing the "general" usage of ram and CPU to get a gist of resources usage for applications? 

The start up thing - i was just curious to see how much quicker Chrome starts on my system than firefox - cos firefox takes forever and a day...

---

### Post by gnomeuser on 2009-09-03
> **joey-elijah said:**
> So i'd be better off just casting my eye over system monitor and seeing the "general" usage of ram and CPU to get a gist of resources usage for applications? 


There are means of doing it more precisely but as a general rule as a user you are probably better off just glancing at top or g-s-m every once in a while to examine the usage over time.

> 
The start up thing - i was just curious to see how much quicker Chrome starts on my system than firefox - cos firefox takes forever and a day...

The best possible option is to insert an handy exit in the code right after it finishes to load everything. Then time <application> will give you a result that is reproducable and reliable. You can also use use some handy insertions like that and get timings for strace to see what takes how long during startup.. these are technics that require a bit of knowledge though.

---

### Post by tgalati4 on 2009-09-03
man time

Also, use a stopwatch and physically measure the time it takes to open applications.  It will vary depending on what else is loaded on the system.  You'll find the second time that you load a program, it will load faster because most of it is already in cache.

If you want faster performance, add RAM.  You can also preload/prefetch applications at boot.

---

### Post by joey-elijah on 2009-09-03
> **tgalati4 said:**
> man time

Also, use a stopwatch and physically measure the time it takes to open applications.  It will vary depending on what else is loaded on the system.  You'll find the second time that you load a program, it will load faster because most of it is already in cache.

If you want faster performance, add RAM.  You can also preload/prefetch applications at boot.

I have been meaning to upgrade my RAM... it's painful how slow Firefox is on my mere 4GB's...

---

### Post by blur xc on 2009-09-03
> **joey-elijah said:**
> I have been meaning to upgrade my RAM... it's painful how slow Firefox is on my mere 4GB's...


How many extensions and add-ons do you have running?  That can slow things down dramatically.

BM

---

### Post by joey-elijah on 2009-09-04
> **blur xc said:**
> How many extensions and add-ons do you have running?  That can slow things down dramatically.

BM

I may have over egged the slowness - it takes 30 secs or so to start from a cold boot, which is more noticeable since Chrome/ium takes about 2 seconds from a cold boot.

I have to be honest - i rarely use Firefox these days since Opera 10 got QT4 and thus GTK integration and Chrome hit "usable" thanks to font rendering, plugins and extensions.

---

### Post by tgalati4 on 2009-09-04
With 4 GB, you should be running Firefox in a ramdisk.  Makes sqlite3 stores much faster:

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

---

### Post by MikeTheC on 2009-09-04
I'm thinking we should benchmark the n00bs themselves. It would prove far more fun and entertaining.

We could, for instance, have a n00b 10 mile sprint to see who crosses the finish line.

Or, if you just want to judge out-and-out performance, we could possibly have pizza-and-Mountain-Dew races to see who can consume the most in the shortest amount of time.

If you wanted to judge qualitatively, you could have them line up, roll up their sleeves, and analyze their skin under a spectrometer to see which ones had been exposed to the least sunshine.

Yes, I think n00b benchmarking would be a lot of fun. Heck, maybe we could even sell tickets and help to raise money to support our favorite Linux distro, Ubuntu!

---

