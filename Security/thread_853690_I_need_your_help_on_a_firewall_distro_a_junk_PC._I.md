---
title: "I need your help on a firewall distro a junk PC. IPCOP/Pfsense, etc"
date: 2008-07-08
forum: Security
---

### Post by mechanicalmetal on 2008-07-08
Hey guys,


I am a HUGE Fan of IPCOP and have used it flawlessly for a few months now. I actually talked to one of my buddies at my corporate office that managaes the whole entire US network for my company. He recommends Pfsense. He states that it will run circles around IPCOP. I Love my linux IPCOP and I do not want to get rid of it! I installed Pfsense BSD. I havent configured anything on Pfsense, and removed IPCOP from my box for Pfsense, but I feel like its not for me. The gui is too simple, but highly complex. I want what is BEST and can provide me with the highest level of security possible. Please give me your recommendations and pros/cons vs IPCOP/Pfsense

And please inform me if there is any distro's that are better than the 2 I stated above. I want top of the line secuirty for my stand alone box.

---

### Post by dannyboy1121 on 2008-08-29
Dude ... if you've used IPCOP flawlessly then it sounds like it's done the job you intended it to do. Unless your friend can pull up some stats or metrics to prove why x is better than y ... I wouldn't switch.

With most of these distributions it probably comes down to two things - ease of use and what extra functionality they bundle with the app.

I've always liked the fact that the IPCOP guys bundles squid with it.

Some alternatives (which you probably know about) are: m0n0wall, Untangle and Smoothwall. 

I bet there are plenty of others out there I've not heard about.

---

### Post by cariboo on 2008-08-29
I agree with the previous poster, if it works for you stick with it.

Jim

---

### Post by veloce on 2008-09-10
Overall: IPCop is ideal for a home setup but can be too limited for a corporate environment. Pfsense is more secure but less useable.

e.g. IPCop is limited to 1 each of red, orange, blue & green interfaces.

PFSense by default blocks outgoing traffic as well as incoming, you have to specifically allow the traffic you want through rather than some being allowed by default. 

IPCop has a heap of addins (e.g. blockout traffic that defaults to blocking outgoing traffic like pfsense does).

Addins, almost by definition, mean greater threat of security holes so this additional flexibility comes at a cost.

Summary: with a lot of effort, you could make a more secure firewall with pfsense but, given an existing installation of IPCop, why would you bother?

---

