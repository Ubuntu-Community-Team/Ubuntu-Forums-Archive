---
title: "Zenmap (NMAP GUI) becomes unresponsive during scan"
date: 2008-06-29
forum: Security
---

### Post by shmoe010 on 2008-06-29
I am trying to map out a network with Zenmap, the GUI interface for nmap, and everytime I start a scan it becomes unresponsive within a few seconds. I don't know if I'm asking too much of it or what. Is it more likely my hardware or is the network doing something to mess with my connection? I'm part of this network and still have 'net access, so it hasn't blacklisted my MAC or anything (i haven't changed it recently.)

---

### Post by The Tronyx on 2008-06-29
> **shmoe010 said:**
> I am trying to map out a network with Zenmap, the GUI interface for nmap, and everytime I start a scan it becomes unresponsive within a few seconds. I don't know if I'm asking too much of it or what. Is it more likely my hardware or is the network doing something to mess with my connection? I'm part of this network and still have 'net access, so it hasn't blacklisted my MAC or anything (i haven't changed it recently.)

IMHO, zenmap is a nice UI, but a bit buggy and not too comfortable in my experience.  If you insist on using a front end for nmap, i would go with nmapfe.  I believe that a lot of tools are best used graphically but nmap is not one of them.  If you run nmap from the command line, you can press 'any key' and it will show you how far along your scan is, i.e. 20% remaining, ETA 17 minutes.

Without any kind of program output, it would be pretty hard to say just why the Zenmap FE becomes unresponsive but that is just my 2 cents.

---

