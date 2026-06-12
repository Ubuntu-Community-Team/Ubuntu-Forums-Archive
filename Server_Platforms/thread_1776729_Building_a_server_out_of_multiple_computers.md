---
title: "Building a server out of multiple computers"
date: 2011-06-06
forum: Server Platforms
---

### Post by valindil89 on 2011-06-06
So at my work we are trying to reuse some old dell computers that are just sitting around we have about 40 or so dell gx620's. 

We are wanting to create a server out of them that will be used to host ghost image files. I have been doing alot of research but have not found anything very useful or informative about how to set this up. My first thought was to just build a cluster. Well for computing that is good (or so that is what I am told), but for storage that is not so good. So the question is, how to I have all the computers link up and show all of their hard drives and one drive on the network. I realize I probably have to have 1 frontend node and then all the other nodes off of that computer.

I already have all the equipment, switches, cat5, computers, power. I just need a pointer in the right direction to start this process. I thought a cloud would be the way to go but after learning the true definition of a cloud I don't think that is right either.

Basically 40 computers all look like 1 computer/1 storage device...

Any advice?

---

### Post by collisionystm on 2011-06-06
> **valindil89 said:**
> So at my work we are trying to reuse some old dell computers that are just sitting around we have about 40 or so dell gx620's. 

We are wanting to create a server out of them that will be used to host ghost image files. I have been doing alot of research but have not found anything very useful or informative about how to set this up. My first thought was to just build a cluster. Well for computing that is good (or so that is what I am told), but for storage that is not so good. So the question is, how to I have all the computers link up and show all of their hard drives and one drive on the network. I realize I probably have to have 1 frontend node and then all the other nodes off of that computer.

I already have all the equipment, switches, cat5, computers, power. I just need a pointer in the right direction to start this process. I thought a cloud would be the way to go but after learning the true definition of a cloud I don't think that is right either.

Basically 40 computers all look like 1 computer/1 storage device...

Any advice?

Is your end goal to have all their disk space treated as one large combined drive? I.E. 46 1tb drives appearing as 46tb or something along those lines

---

### Post by collisionystm on 2011-06-06
[http://hadoop.apache.org/](http://hadoop.apache.org/)

[http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-multi-node-cluster/#what-we-want-to-do](http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-multi-node-cluster/#what-we-want-to-do)

---

### Post by collisionystm on 2011-06-06
[http://www.petur.eu/blog/?p=59](http://www.petur.eu/blog/?p=59)

you can probably also use bits from that, minus installing John the Ripper

---

### Post by valindil89 on 2011-06-06
I will take a look at this hadoop. It looks like a step in the right direction. Thank you. 

As for the supercomputer, that's the way I started to do it but realized its mainly used for computational work, and not storage.

But in response to your question yes... 46 1 tb hds looking like 1 46 tb hd.

---

### Post by valindil89 on 2011-06-06
The hadoop could work, I just can't have that many machines out over the work network, so I would have to have 1 machine with 2 eth ports. 1 to link with public network 1 to link with cluster. Question is... 

Does anyone know how to setup the 1 machine to route the cluster through it and onto the network, so that the cluster appears as 1 machine on the network?

---

