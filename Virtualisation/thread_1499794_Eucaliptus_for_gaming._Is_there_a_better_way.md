---
title: "Eucaliptus for gaming. Is there a better way?"
date: 2010-06-02
forum: Virtualisation
---

### Post by pashenka on 2010-06-02
I'v been trying to set up Eucalyptus(cloud computing) for my little home net using Ubuntu. I was really disappointed when i succeed. I could lunch games in virtuals, but they just say like "no harware video card was found, go to hell".

i have 4 average pc's, a netbook, and Gigabit Ethernet connecting them. My goal is to play hardware-greedy games, or running CPU-greedy apps at the netbook with my 4 PCs powers simultaneously. 
Is there a better way to do it than Eucalyptus?
Please, point me in right direction. (like "gaming on demand", but, using my own PCs powers.)

problems summary:

[LIST=1]
[*]Is there a way to "tell" the cloud to use video card on concrete PC? (/point exact hardware on exact pc to use) (that seem to go bad with "cloud" concept)
[*]Is there a way of getting hardware video card resources at all, using virtal machine?
[*]Any better (easier) way to play 1 game using more than 1 PCs computing powers?
[/LIST]

p.s.
sorry my English is poor.
vnc or rdp style is cool, i am using it for now, but my other 3 PCs feel lonely...
Eucalyptus has much to do with virtualization, but if you feel like moving the thread, please, PM me where to :)

---

### Post by dragos2 on 2010-06-02
Yes. Build one fast standalone system. Graphics are supported by kvm and xen but at a basic level. Also there are network latencies. PCI-E bandwidth used by games are in the GB/sec range and your Eucalyptus 10/100 network can transport only 10 MB/sec and you need gigabytes. Even if you have a fast enough network you will still need support in Eucalyptus and even so the network latency will get you small framerates.

Eucalyptus was not build for this kind of work.

---

