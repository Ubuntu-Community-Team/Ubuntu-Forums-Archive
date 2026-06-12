---
title: "RAM usage at near max"
date: 2009-03-27
forum: Server Platforms
---

### Post by shizakapayou on 2009-03-27
I have a Poweredge 2950 III, eight core Xeon with 8GB RAM, running Server 8.04.2 64-bit.  It does OpenLDAP, Samba, DNS, internal Apache page, Bacula, NTP, and probably probably one or two I'm forgetting.  At any rate, the hardware is serious overkill, as this is an office of 30 people and 50 computers.

Today while I was looking at SNMP reports in Zenoss (which is on a different server), I noticed the 2950 was reporting almost all RAM used.  Logged on and ran top, which confirmed about 50mb free, and minimal/no swap in use.  I then checked htop, which said about 3GB of RAM was used.  CPU usage is at zero according to everything.

What's the best way to approach this?  I'll admit I'm not sure exactly how to read each column in top, but I can provide whatever additional information is needed.

---

### Post by windependence on 2009-03-28
This is due to Linux memory management and is probably perfectly normal. Even though it appears to be "using" all the RAM, Linux does not manage memory like Windoze at all ( this is a GOOD thing). Linux will appear to use whatever memory you give it because it will cache as many programs in memory as it can for fast access. Memory is paged in and out as necessary when a process is called to be run, but any additional RAM is "used" to load processes into memory that will likely be recalled. If you search google for "Linux memory model" or "Linux memory management" you will find many articles on this.

-Tim

---

### Post by hyper_ch on 2009-03-28
run:

```

free -mem

```

it will give detailed view of how much ram is really in use and how much is just "filled" with previous data.

---

### Post by schettj on 2009-03-28
There really should be some kind of message about this in linux ;)

Free memory is wasted memory. You're not burning electricity to have a bank of ram with nothing in it, right?

Be happy your box is correctly caching about 7gb of disk, as it should!

---

### Post by shizakapayou on 2009-03-28
```
administrator@mercury:~$ free mem
             total       used       free     shared    buffers     cached
Mem:       8186412    8139540      46872          0      23760    7870352
-/+ buffers/cache:     245428    7940984
Swap:      7812492        444    7812048
```

Looks like most of it is in fact cached.  Good to know, I'll just remember not to worry until the swap is going crazy.  Thanks all.

---

### Post by tubezninja on 2009-03-28
Yeah, if your swap remains untouched, then your memory usage is fine.  Linux and unix-like OSes tend to be good at making the max use of the RAM you have, and having loads of free RAM actually isn't optimal.

---

