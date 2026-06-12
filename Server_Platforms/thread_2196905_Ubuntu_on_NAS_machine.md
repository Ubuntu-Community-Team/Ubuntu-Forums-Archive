---
title: "Ubuntu on NAS machine"
date: 2014-01-01
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2014-01-01
I was thinking of getting one of these [NAS machines](http://www.ebuyer.com/store/Enterprise-Storage/cat/Network-Attached-Storage/subcat/Desktop-NAS-4-bay?q=nas), I haven't decided on the exact one yet.

Has anyone tried putting ubuntu server on one of them, I'd much rather use the cli I'm familiar with as opposed to a web interface.

Is it straight forward, I'm assuming when it comes down to it they are still just a computer. Where would the current OS be stored do you think? Will I need to connect that drive to another machine install the Linux then reconnect it to the NAS machine? 

I'm just wondering if anyone has done it and if it's possible and if there are requirements I should be looking for?

Cheers.

---

### Post by TheFu on 2014-01-01
If you want a NAS where you control the OS, perhaps building an Atom-based box for $150 would be a good thing to research?  That way you can ensure drivers exist, the CPU is known, amount of RAM is your choice, PCI-x, networking and the number of SATA ports needed are provided.

Many of those boxes (but not all) do not use Intel-compatible CPUs. They run on Marvell. Nothing wrong with that, but it doesn't run a stock Ubuntu. I'd also expect drivers for the SATA, NIC, etc. to be hard to find.

OTOH, I've built external eSATA arrays for my needs and found that an acceptable solution. [http://addonics.com/category/nas_systems.php](http://addonics.com/category/nas_systems.php) might give you some ideas?

---

### Post by tgalati4 on 2014-01-01
Take one or two of the models on that page and research them further.  You will quickly find the limitations of these boxes.  Synology boxes run a specialized linux operating system, so you might check their forums for additional capability.  I presume that you want to run Ubuntu because you are familiar with it and you want to load a bunch of additional services on the NAS.

The requirements that you are looking for are really the specifications that you are looking for.  The requirements are what you define:

1.  Explicit Requirements
2.  Implicit Requirements

So what are your explicit requirements for this NAS?  What does it have to do in the home?  How do you plan to use it?  Who plans to use it?  Who will maintain it?

The implicit requirements are those things that the NAS needs to do that you didn't mention, but are related to the explicit requirements.  Once you have defined those, then you can flow down the functional specifications (drive capacity, CPU speed, RAM amount, OS, etc) and that will quickly narrow down your choices.

Or just buy one set it up and complain that OS on these NAS machines generally suck.  Or at least that is the impression I get reading the reviews of some of these machines.

---

### Post by AmbiguousOutlier on 2014-01-01
The atom machine is my other choice, I just like the size and compactness of the dedicated NAS boxes. 

And yes you're right I like Ubuntu and I prefer it to any other OS, its purpose is as a home file server, which I can control and maintain from ssh. It might end up just being a back up for my other server which is nearing capacity.

I guess I'm better off building it myself, I know what I'm getting then.

---

