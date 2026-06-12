---
title: "Software sources fixed yet?"
date: 2012-12-05
forum: Ubuntu Development Version
---

### Post by bird1500 on 2012-12-05
Hi,
Starting with Quantal "Software sources" is (much) slower to startup and a lot more CPU intensive (so that I can hear the fan spinning like crazy) for like 2-5 seconds until the window shows  up.

Raring doesn't install for me, so I'm asking if this has been fixed in Raring.

---

### Post by VinDSL on 2012-12-05
Kind of a tricky question!

I suppose it depends on how many repos/PPAs you've got plugged in.

Here's a screenie of Synaptic reloading the package info, on my machine...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-5-dec-2012-1(659x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-dec-2012-1.png")[/INDENT]


It's reloading "355" sources, I guess, and it takes a while.

If I open the repo list, all it does is call up "Software Sources".  And, yes, it takes forever to open -- 1-2 minutes, going by my clock, in Conky (right-side of display).  

I would judge "Software Sources" to be hideously slow, and getting slower.  But, I keep adding sources, sooo...

But, then again, I suppose testers provide extreme examples of slowness and inefficiency, when it comes to such things. 

Anyway, Ubu Raring certainly doesn't offer any relief over Quantal.

Every time I open "Software Sources", it pegs my processors at 100% for a certain length of time, and takes forever to open up the window.  Sorry!  ;)

---

### Post by ventrical on 2012-12-05
23 seconds here .. but with only 1 ppa.

---

### Post by fjgaude on 2012-12-05
About 3 seconds here, without any PPAs.

---

### Post by mc4man on 2012-12-05
A couple of ppa's or so doesn't make any or much difference here, the bulk of the increased time comes from additional drivers being added to SS.
The time to open is likely more dependent on cpu & drive type, a newish cpu & SSD will be much faster than older cpu & or HDD

If there is a bug I'd guess that when SS is opened directly or from software-center there is no indication anything is going on 
(synaptic will show a spinning cursor while cursor is in synaptic window

---

### Post by zika on 2012-12-05
It is difficult (in most of the cases) to differentiate part in difference in time due to network access from the one due to actual disk/data access...

---

### Post by cariboo on 2012-12-05
This method isn't that accurate, but I used the following command to start software-sources:

```
time software-properties-gtk
```

and got the following results:

```
time software-properties-gtk
gpg: /tmp/tmpsmw2p7/trustdb.gpg: trustdb created

real	0m19.423s
user	0m9.833s
sys	0m0.316s
```

some of the total time, is a result of my reation time to close the window once it opens.

Running the command a second time, because of caching, the time drops about 7 seconds.

---

### Post by fjgaude on 2012-12-05
Here's mine using 'time':

```
frank@cutie:~$ time software-properties-gtk
gpg: /tmp/tmpal7mxn/trustdb.gpg: trustdb created

real	0m4.312s
user	0m2.972s
sys	0m0.144s

```

Running the command several times dropped the time by maybe one second. Notice my signature.

---

### Post by VinDSL on 2012-12-06
Ooh... nice one, cariboo! :D

```

vindsl@Zuul:~$ time software-properties-gtk
gpg: /tmp/tmpcv1ope/trustdb.gpg: trustdb created

real	0m55.640s
user	0m27.032s
sys	0m1.164s

```

Anyone got that beat?!?!?

---

### Post by zika on 2012-12-06
```
:~$ time software-properties-gtk
gpg: /tmp/tmpq9bbyi/trustdb.gpg: trustdb created

real    0m21.281s
user    0m12.717s
sys     0m0.351s
```(/tmp is not od disk, it is in memory (tmpfs)...)

---

### Post by mc4man on 2012-12-09
bug on
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1073728](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1073728)

---

### Post by bird1500 on 2012-12-09
Thanks for the bug report, someone had to step up, otherwise the devs are playing ostrich politics it seems.
I'd also like Canonical to tell more of its devs to use native languages, it pushes a lot of scripted code even for sophisticated stuff like the software center. Imo Steve Jobs would have used the word "lazy" in this regard, as he did about the devs from Adobe (for a different reason though).

---

### Post by VinDSL on 2012-12-09
> **mc4man said:**
> bug on
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1073728](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1073728)
Added "me too" and comment.

Thanks!

---

### Post by serdotlinecho on 2012-12-10
```
Netbook 1.6ghz 
2gig of RAM
Hard disk 5400 RPM
Unity 6.12.0daily12.12.05-0ubuntu1
Software Sources 0.92.13

```

```
~$ date -R ; time software-properties-gtk
Mon, 10 Dec 2012 17:01:17 +0800
gpg: /tmp/tmp3d6zsq/trustdb.gpg: trustdb created

real	0m18.634s
user	0m14.112s
sys	0m0.672s
```

---

### Post by pqwoerituytrueiwoq on 2012-12-12
The added time is because of the last tab, They put "Addition Drivers" aka jocky in the software sources window

the best way to make everyone happy would be this i think:
The software sources tab should not search for drivers until the additional drivers tab is selected and it should have a loading bar in it for that process

---

### Post by bird1500 on 2012-12-13
> **pqwoerituytrueiwoq said:**
> 
The software sources tab should not search for drivers until the additional drivers tab is selected and it should have a loading bar in it for that process

It's a painkiller rather than a cure, but still, doing it is much better than nothing.

Imo, the Canonical devs should ask themselves how to detect drivers much more efficiently and when fixed do the detection in the background, because even then it could take up to a second or so.

To seriously compete with Apple they need to be better, not just build patches on top of good-enough (or mildly bad) open source solutions.

---

