---
title: "A question about cloud computing in 9.10"
date: 2009-10-27
forum: Server Platforms
---

### Post by melsen on 2009-10-27
Alright.. I'm anxiously awaiting 9.10 like many others.

One of the things I'm planning to toy with is naturally the cloud setup.

What I'm worried about is that everytime I see a reference to the cloud computing features in 9.10, it always lists ec2. But what if I dont want to use amazon's ec2 service, but want to host EVERYTHING in-house?

Is that possible?

---

### Post by druhboruch on 2009-10-27
Please, tell us what exactly would you like to do...

Are you planning to start your own hosting service?

---

### Post by Mighty_Joe on 2009-10-27
> Karmic will also include functionality for building "EC2-style" clouds on companies' own hardware. While Jaunty will include work from a University of California-based project called Eucalyptus, which makes it possible for users to set up their own clouds, Karmic will have added functionality to make it easier to deploy applications into that virtualized infrastructure and, in Shuttleworth's words, "make those clouds dance, with dynamically growing and shrinking resource allocations depending on your needs".

[Karmic Koala to make cloud 'dance']("http://news.zdnet.com/2100-9595_22-271852.html")

---

### Post by Vegan on 2009-10-27
I am aware of the Lustre file system for building cloud-like file systems on top of storage machines. Something like that would be attractive with a rack of commodity file servers. Lustre makes it safe to replace a server that is sick.

---

### Post by melsen on 2009-10-27
> **druhboruch said:**
> Please, tell us what exactly would you like to do...

Are you planning to start your own hosting service?


Yeah.. I was toying with that idea. Offering storage and websites as payable services.. in one way or fashion.

Still haven't thought it out properly. But I was thinking about a setup somewhat like this:

1 NAS with ISCSI support
2 node eucalyptus cloud with two servers without disks but booting diskless through PXE on the NAS
And perhaps 1 dedicated cloud controller, if thats needed.

Still  haven't figured out completely how to do the setup and what kind of services I potentially could form the business on.

---

### Post by Vegan on 2009-10-27
To me, Lustre has potential, you can down a server, replace it and not lose any files. Machines could also do other tasks too.

I definitely have go my money's worth out of ancient IBM and it has never let me down. Still having a rack with misc hardware on it as a private cloud is attractive.

I already virtualized HTTP a long time ago, as well as virtualized the PC. So what's left, storage!

Lustre sits on top of the file system, and it can scale to petabytes easily.

---

### Post by melsen on 2009-10-28
> **Vegan said:**
> To me, Lustre has potential, you can down a server, replace it and not lose any files. Machines could also do other tasks too.

I definitely have go my money's worth out of ancient IBM and it has never let me down. Still having a rack with misc hardware on it as a private cloud is attractive.

I already virtualized HTTP a long time ago, as well as virtualized the PC. So what's left, storage!

Lustre sits on top of the file system, and it can scale to petabytes easily.

How would that benefit me if the only thing that was used as a storage for me was the NAS? The servers are not meant to have any harddisks at all, but boot up through PXE on the NAS

---

