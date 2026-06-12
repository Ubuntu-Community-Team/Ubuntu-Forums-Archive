---
title: "Deciding bare metal or virtual, suggestions please"
date: 2012-09-18
forum: Server Platforms
---

### Post by hitime on 2012-09-18
Hey all,

I'm trying to figure out what the best setup would be for the server setup I want.  

Machine: Quad core Q6600 with 4gb or ram
Storage: 250 Sata boot, 750GB USB storage

Services wanted: 
Apache w/ php & python support (OwnCloud)
Want to use Handbrake and video crunching over ssh (could setup tigervnc)
may have an IRC bot

want to do some python dev so will use it for playing with that


Questions:
Is setting up kvm and its graphical setup overkill?
Would virtualbox be better
Should I just go bare metal and try securing it

I would say I have intermediate skills when it comes to cli and have been doing more and more as I go along

I do have 2x desktops running kubuntu currently, can kvm instances be managed remotely (have not looked at management software, I would think so)

Other question is if the host crashes is there a way to automatically spin up the instances on reboot  (again I really am not super familiar with virtualization, I've only done desktop software for very specific tasks) 



I may add stuff as I go along, just to play with or as I need more services.

Thoughts, suggestions, anything would be appreciated.....\

hitime

---

### Post by sandyd on 2012-09-18
You probably want Proxmox VE.

Looking over your requirements, it has everything you need.

---

### Post by HermanAB on 2012-09-19
Howdy,

You should never run a server bare metal, since it presents a maintenance problem.  It is much less long term schlepp to run servers as VMs, since you can easily provision and move the VMs to new machines.

---

