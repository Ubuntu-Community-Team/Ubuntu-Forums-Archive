---
title: "What's oneconf-service and where did it come from?"
date: 2011-10-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2011-10-14
And why is it using as many resources as Xorg?

This is in a new OO installation - shortly to become PP

It doesn't show in my everyday OO install.

---

### Post by cariboo on 2011-10-14
The oneconf-service is supposed to allow you to setup one system, then use that configuration file to setup other systems over a network. I haven't looked for any documentation on how to use it yet though. It is installed on my Oneiric system. 

With a little more looking, oneconf work with the Software Center.

---

### Post by Quackers on 2011-10-14
Thanks cariboo907, I understand that it will come in handy in the future.
I was, however, somewhat surprised to see it using up to 4% CPU for approximately half an hour after installation.
Maybe it's just the first time it runs that uses so many resources for so long.
A sort of initialisation period, maybe. 
Future reboots should make things clearer.

---

### Post by cariboo on 2011-10-14
There is some additional info here:

[https://wiki.ubuntu.com/OneConf](https://wiki.ubuntu.com/OneConf)

---

### Post by Quackers on 2011-10-14
Thanks for the further info cariboo907.
It's going to have a few uses in the future, assuming all those settings are transferrable between the two systems concerned.

I will mark this as solved as it hasn't shown its head again in subsequent restarts.

---

### Post by jfernyhough on 2011-11-29
I thought I'd search and find out what this was and found this thread. Nice.

It's pretty noticeable when oneconf is running on my 311c (slow processor, after all). It looks like it also runs whenever you add or remove software - which makes sense looking at the wiki page it talks about easily reinstalling software after an install.

---

### Post by jerrylamos on 2011-11-29
> **jfernyhough said:**
> I thought I'd search and find out what this was and found this thread. Nice.

It's pretty noticeable when oneconf is running on my 311c (slow processor, after all). It looks like it also runs whenever you add or remove software - which makes sense looking at the wiki page it talks about easily reinstalling software after an install.

How do I tell if it is installed and running here?

How do I get rid of it?

Thanks, Jerry

---

### Post by cariboo on 2011-11-29
From the looks of it, you can just remove that package, check synaptic package properties to see what else may be removed. 

Oneconf doesn't run all the time, so it shouldn't be a problem, as it only runs when installing new packages, to check, open a terminal and start top, then install a package.

---

