---
title: "noob:  3 server home uec setup"
date: 2010-12-02
forum: Ubuntu Cloud and Juju
---

### Post by ringonian on 2010-12-02
i know setting up uec for the home sounds like overkill but i'm contemplating a home setup for the sake of academia.  but i do have a few questions:

1.  looking at the minimum and recommended requirements from the documentation [https://help.ubuntu.com/10.10/serverguide/C/uec.html](https://help.ubuntu.com/10.10/serverguide/C/uec.html), wouldn't the numbers seem a little excessive for a home setup especially for the uec front-end? i don't get the dual-core suggestion for the front-end.

1 1/2.  shouldn't the numbers be a little more clear like "X mb ram per concurrent vms running" or "X ghz processing speed for X amount of nodes or controllers in the cloud"?

2.  assuming i have a setup of:
Server A:  clc/ws3/cc/sc
Server B:  ws3/cc/sc/nc
Server C:  nc
as there can only be 1 clc according the glossary [https://help.ubuntu.com/community/UEC/Glossary](https://help.ubuntu.com/community/UEC/Glossary), i can still have a stable cloud if Server's B or C go down.  But what happens when Server A goes down?

---

### Post by possnfiffer on 2010-12-02
Hmm I'm also involved in a setup at home right now I've just used a dual core with two gigs of ram and a hex core with eight gigs for the vt nc its just that I'm having trouble with the network setup.

---

### Post by ringonian on 2010-12-02
> **possnfiffer said:**
> Hmm I'm also involved in a setup at home right now I've just used a dual core with two gigs of ram and a hex core with eight gigs for the vt nc its just that I'm having trouble with the network setup.

subnetting was always my worst subject.  6-core with 8gb node.  that's alot of vm's.

---

### Post by kim0 on 2010-12-02
Hi!

High availability for CLC is not supported out of the box. However if that interests you it has been done, check out
[http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto](http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto)

---

### Post by ringonian on 2010-12-02
> **kim0 said:**
> Hi!

High availability for CLC is not supported out of the box. However if that interests you it has been done, check out
[http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto](http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto)

thanks alot.  that's exactly what i needed.  after reading the link, it seems like a 3 server system wouldn't be enough - but 4 is.  that seems like overkill for a home environment.

this guy [http://www.roaksoax.com/2010/10/my-first-uec-deployment/comment-page-1#comment-1913](http://www.roaksoax.com/2010/10/my-first-uec-deployment/comment-page-1#comment-1913) actually used vm's (kvm) to build his cloud.  Depending on performance, this may be the perfect setup with a minimum of 2 physical systems to set up the cloud.

another alternative i just thought of would be to use lxc instead of kvm.  it would be the same 2 system requirement with less the load (i think).  the only thing about that is my knowledge of lxc is very limited.  i would have no idea on how i would create "virtual block devices" to install the controllers/nodes on.  but i'm sure anything's possible.

---

### Post by kim0 on 2010-12-03
Note that in your case .. serverA and serverB can be merged into one box! so I think your 3 boxes can be enough, even if you want HA CLC, and one NC

---

### Post by ringonian on 2010-12-04
> **kim0 said:**
> Note that in your case .. serverA and serverB can be merged into one box! so I think your 3 boxes can be enough, even if you want HA CLC, and one NC

i'm not sure what kind of benefit i'd get merging A and B into one box.  if i have a hardware failure, there goes my cloud, right?  or am i missing something?

EDIT:  or if a natural disaster hit that box; same deal.

on another note, sticking with a 2 physical server ha clc, it would seem like striping the disks (2 or more disks per system) would increase performance without sacrificing stability.  the one problem i see with that is if there is a disk failure on one of the machines, i'd still have my cloud up but i'd have to rebuild the entire machine.

---

