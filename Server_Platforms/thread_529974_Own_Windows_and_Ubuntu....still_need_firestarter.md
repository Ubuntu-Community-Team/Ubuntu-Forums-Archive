---
title: "Own Windows and Ubuntu....still need firestarter?"
date: 2007-08-19
forum: Server Platforms
---

### Post by working_night_owl on 2007-08-19
I bought a computer with Windows XP already installed on it for years. Then I decided to have ubuntu installed because I wanted to run my computer with a Linux OS. So my question is, should I have firestarter installed on my computer since I still have Windows XP installed on my computer? Can any of the viruses that can attack Windows ever cross over into my Linux OS? I kept both on my computer in case I needed to ever use Windows too.

---

### Post by Motoxrdude on 2007-08-19
A firewall is a good idea but no, a windows virus can not execute in linux and effect your windows partition (in theory).
A firewall is still recommended though.

---

### Post by bodhi.zazen on 2007-08-19
Firestarter is an easy to user firewall.

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

In general, you do not *need* a firewall with a default install because there are no open ports.

If you run a server (or server software on a desktop), however, you should look into a firewall.

---

### Post by codmate on 2007-08-20
> **bodhi.zazen said:**
> Firestarter is an easy to user firewall.

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

In general, you do not *need* a firewall with a default install because there are no open ports.

If you run a server (or server software on a desktop), however, you should look into a firewall.

Weird - in my Ubuntu installation (Feisty - 7.04) iptables was switched on by default, but with no rules and an 'allow everything' policy on all chains  :confused:

Maybe you mean there are no vulnerable services started by deault?

---

### Post by bodhi.zazen on 2007-08-20
> **codmate said:**
> Weird - in my Ubuntu installation (Feisty - 7.04) iptables was switched on by default, but with no rules and an 'allow everything' policy on all chains  :confused:

Yes, those are the default settings for iptables

> Maybe you mean there are no vulnerable services started by deault?

Yes, I think ...

There are no open ports with a default install. The problem is that some software that a user may then install will open ports. Sometimes this is obvious (apt-get install openssh-server) and sometimes not (VoIP software).

open port = listening server

---

### Post by Mach1US on 2007-08-20
Generally if you are connected directly the internet it is a good idea to run a firewall and Firestarter is simple to get up and running yet offers plenty to customize if you want to tweak it.

---

