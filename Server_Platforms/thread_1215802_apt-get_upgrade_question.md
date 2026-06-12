---
title: "apt-get upgrade question"
date: 2009-07-17
forum: Server Platforms
---

### Post by dragos2 on 2009-07-17
I am a little confused:

```

root@deb02:/home/dragos# apt-get update
..
root@deb02:/home/dragos# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Why are there 2 not upgraded packages ?

I thought I am up to date with
Linux name 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux


but by curiosity I had a look in synaptic and it was showing that I have to
upgrade to a new kernel.

How can I upgrade those 2 not upgraded packages using apt-get ?

---

### Post by peekaboo on 2009-07-17
what happens when you type "aptitude" instead of "apt-get"?

*I'm a clueless newbie so I shouldn't be making any suggestions...

---

### Post by dragos2 on 2009-07-17
> **peekaboo said:**
> what happens when you type "aptitude" instead of "apt-get"?

*I'm a clueless newbie so I shouldn't be making any suggestions...

Na, aptitude is just another supposed intelligent wrapper around apt-get which is a wrapper
over dpkg.

---

### Post by Cheesemill on 2009-07-17
```
 
sudo apt-get dist-upgrade

```or
```
 
sudo aptitude full-upgrade

```

---

