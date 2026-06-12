---
title: "aptitude - apt-get/cache: What's the difference?"
date: 2008-07-01
forum: The Cafe
---

### Post by KenBW2 on 2008-07-01
See title

---

### Post by Raven_Oscar on 2008-07-02
Well after brief looking on debian  [wiki]("http://wiki.debian.org/Aptitude") it seems that aptitude is no more than frontend to apt.

---

### Post by forger on 2008-07-02
aptitude is made to handle the dependencies better (The recommended are installed as well I think, whereas apt-get installs only the recommended ones)
It's more or less the same thing, depends on how you're used to it.

Aptitude has command-line support to "freeze" packages (lock their version and don't update them using upgrade)

apt-cache has several things aptitude doesn't have, like "apt-cache policy package"
> 
aptitude --help
apt-get --help
apt-cache --help

---

### Post by KenBW2 on 2008-07-02
So it's not as simple as aptitude being a newer version of apt-get? Oh... So which am I best using?

---

### Post by Raven_Oscar on 2008-07-02
KenBW2
As for me I use aptitude. But some times I have to use apt (especially apt-cache) mostly because I like output of apt-cache search more than aptitude search.
For example in debian aptitude supposed to be primary package management tool and apt is a secondary tool for specialized tasks ([prooflink]("http://wiki.debian.org/Apt")).
As for ubuntu it seems there is no grate difference.

---

### Post by erginemr on 2008-07-02
-deleted-

See below...

---

### Post by erginemr on 2008-07-02
One vote for aptitude here, too. It handles dependencies better than apt-get, in that, if you install and then remove a program with aptitude, it will remove all unused dependencies along with.

Aptitude sports other functionalities as well: "aptitude search", "aptitude show" are but a few of these. There is also an interface to aptitude which you can activate by "sudo aptitude".

---

### Post by mashcaster on 2008-07-02
> **erginemr said:**
> One vote for aptitude here, too. It handles dependencies better than apt-get, in that, if you install and then remove a program with aptitude, it will remove all unused dependencies along with.

Does the following command not do the same thing?

> sudo apt-get remove program && sudo apt-get autoremove program


---

### Post by erginemr on 2008-07-02
I remember to have tried "sudo apt-get autoremove program" before, but all the command did was to remove the original package only (no dependencies). 

Maybe, I should do another try and report back. What are your findings?

---

### Post by mashcaster on 2008-07-02
> **erginemr said:**
> I remember to have tried "sudo apt-get autoremove program" before, but all the command did was to remove the original package only (no dependencies). 

Maybe, I should do another try and report back. What are your findings?

How about sudo apt-get autoremove?  I do that every now and again and it seems to remove a lot of redundant stuff.  I've never really looked deeply into it though.

---

### Post by erginemr on 2008-07-02
Regarding "autoremove", the man page of apt-get looks promising:
[http://www.annodex.net/cgi-bin/man/man2html?8+apt-get](http://www.annodex.net/cgi-bin/man/man2html?8+apt-get)

I was rather using "deborphan" and a corresponding custom filter in Synaptic to remove orphaned packages. Yet, if "autoremove" works as promised, "apt-get" is more than welcome as a worthy alternative to "aptitude".

---

### Post by erginemr on 2008-07-02
Reporting for duty... :)

1. "sudo apt-get install pingus" installed the game and its dependencies.

2. "sudo apt-get autoremove pingus" successfully uninstalled all of them.

So, I owe an apology to "apt-get" and a big thanks to @mashcaster, for pointing out this feature.

---

### Post by mashcaster on 2008-07-02
> **erginemr said:**
> Reporting for duty... :)

1. "sudo apt-get install pingus" installed the game and its dependencies.

2. "sudo apt-get autoremove pingus" successfully uninstalled all of them.

So, I owe an apology to "apt-get" and a big thanks to @mashcaster, for pointing out this feature.

Thanks for taking the time to look into this.

---

### Post by forger on 2008-07-02
if you want to purge the unused dependencies:
> sudo apt-get autoremove --purge

---

