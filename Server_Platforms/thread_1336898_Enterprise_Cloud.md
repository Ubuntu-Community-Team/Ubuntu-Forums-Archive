---
title: "Enterprise Cloud"
date: 2009-11-25
forum: Server Platforms
---

### Post by pepsifx357 on 2009-11-25
Hey everyone, so I've just been able to understand how Virtualization works, and have a server using VMware.  I'm trying to get my head around this "cloud" business.  Is it possible to wipe my computer clean, install ubuntu with cloud, set up a "cluster," and install VMware on top of the cloud?  That way you could have multiple computers consolidated into 1 and install a bunch of virtual machines on it?  That would be badass if you could.  I know that there seems to be a difference between a cloud and a cluster but to what extent?  Because I want to create a "super computer" and clusters are next to impossible to setup.

Also, just to be able to understand the cloud, how would you use it?  I really want to play around with it, but I don't understand it enough to know what to try with it.  I have a few computers to mess with so I know I could play with something.

I know this all seems vague but maybe someone can help me make sense of it.

Thanks,
Ben

---

### Post by pepsifx357 on 2009-12-01
bump

---

### Post by Meatshield on 2009-12-01
The basic difference between the "cloud" and a cluster is how it's presented to the user. A cluster looks like a "super computer" as you termed it in that each node of the cluster is not seen by the user. Thus to interact with the controller node is to interact with all the other nodes, and it all looks like one powerful computer. There is no virtualization involved at all. It looks like an N core computer with the cumulative amount of RAM each system has(I think, usually clusters are just for calculations as far as I know)

The cloud on the other hand is a bunch of linked computers from which you abstract the hardware and run virtual machines on top of that hardware. And since virtual machines (as far as I know) can't be expanded past the size of the host computer, you're limited in a VM to the underlying hardware, such that if a server has only 4 GB of RAM in it, you could never have more than that 4 GB (well, less with a VM but that's getting too technical)
Cloud applications basically use a central controller to run programs on multiple VMs. The power here is that your application can dynamically scale as needs arise, whereas with a cluster you can't increase or decease it as far as I know. It's always constant.

Now, with those basic definitions down, if you want one computer that can do very computationally complicated tasks, then you want a cluster. If however you want a bunch of different computer, say a windows server here, an Ubuntu desktop there, and to be able to turn those on and off at a whim, then you want a cloud.

Personally I don't have anything complex enough for a cluster (like 3D animation) but I do use the occasional VM for software testing on different platforms. What you need is based really on what you're going to do with it.

---

### Post by Vegan on 2009-12-01
I use virtual machines daily on my Windows box. If Ubuntu would boot in Virtual PC I would junk the old server immediately. For now the server lives on an old P4 and runs Ubuntu on bare hardware.

VirtualBox and VMware would cure my problem but I am in no rush. The old P4 is not in the way at all.

Given my need for storage I have looked at rack mounted servers with 10 TB and up of my chess project. I need about 75 TB in total. That is what I need for storing chess databases.

I may post some more stuff on my site on extreme computing. I have a bit now.

---

### Post by pepsifx357 on 2009-12-06
Thank you for your posts.  OK, what I want to do, or what I think I want to do is this.

Have a few computers "consolidated" together to where they are perceived in the virtual world as one BIG computer, and use VMware to install Various OS's on top of the big computer, thus, in a way, making a multiple partition out of a RAID 5, so to speak.  Preferably with the ability to use specific hardware from anyone of the consolidated computers, such as a sound card.  Then be able to set up thin clients to log into the OS's that I install.

See I thought that you had to have a "super computer" or cluster to be able to do that.  But maybe a cloud system is what I really am looking for.

Small question:  If my servers or computers that I want to use do not support hardware virtualization will that effect a cloud in a big way?

Thanks,

Ben

---

