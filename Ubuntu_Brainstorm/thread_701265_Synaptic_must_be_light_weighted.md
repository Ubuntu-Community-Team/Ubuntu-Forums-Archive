---
title: "Synaptic must be light weighted"
date: 2008-02-19
forum: Ubuntu Brainstorm
---

### Post by adi_das on 2008-02-19
the Synaptic must be light weighted, it consumes a lot of resource when installing

---

### Post by smartboyathome on 2008-02-19
Talk to the synaptic guys. I am on SAM Linux right now, and I definately like the Smart Package Manager over Synaptic when it works, as synaptic can take a while to search.

---

### Post by insane_alien on 2008-02-19
of course it uses a lot when installing, its either install it as fast as possible or take for ever. 

if you install something manually it will also hog resources.

---

### Post by kerry_s on 2008-02-19
> **adi_das said:**
> the Synaptic must be light weighted, it consumes a lot of resource when installing

i agree it could use some trimming, i use it on 450mhz 256mb ram, so i really get to see the speed. :lolflag:

i like synaptic though, it gets the job done, i know it like the back of my hand. even on my slow rig at least it works, i can't stand anything else.

if it's really that bad for you using the console and apt-get is just as effective, you can skip the complicated gui wrappers and use it pure.

try looking at "wajig" it's in the repos and has a gnome gui front end "gjig"
also look at gnome-apt, if your using gnome.

---

### Post by CarpKing on 2008-02-20
I think a major improvement would be some sort of search as you type function.  It's reasonable to take a lot of resources while installing something, but the way Synaptic goes unresponsive for several seconds when searching seems unnecessary, especially when before you start searching the entire list it searches through is already displayed.

---

### Post by kerry_s on 2008-02-20
> **CarpKing said:**
> I think a major improvement would be some sort of search as you type function.  It's reasonable to take a lot of resources while installing something, but the way Synaptic goes unresponsive for several seconds when searching seems unnecessary, especially when before you start searching the entire list it searches through is already displayed.

it does have that, just click on a line, any line, then just start typing what your looking for.

---

### Post by Whiffle on 2008-02-20
If you're looking for more speed ... aptitude on the command line is pretty fast.  I could uninstall synaptic if i wanted to, I havn't used it in ages. 

But honestly, when you're downloading and uncompressing large amounts of data, its going to be slow, no way around it.

---

### Post by 23meg on 2008-02-21
1) There's a good chance that Synaptic will be removed from the default install in 8.10, since there are plans to introduce PackageKit.

2) Is Synaptic itself really the bottleneck, or is it the underlying system? Have people who find it heavy measured its performance against APT alone? Any benchmarks?

---

### Post by jpittack on 2008-02-21
The best measurement I have found is my internet download speeds.  This is a huge variable, but aptitude will give me up to 700 kb/s, where as synaptic won't top 300.  Not that reliable as a benchmark, but I see it as some sort of proof that aptitude is doing something faster.

---

### Post by 23meg on 2008-02-21
The download speed can't be different as long as they're using the same sources, and they should be. It's almost certainly due to some kind of misconfiguration on your end, or one of the apps isn't reporting the actual speed correctly.

---

