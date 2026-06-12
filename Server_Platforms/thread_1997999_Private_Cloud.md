---
title: "Private Cloud?"
date: 2012-06-06
forum: Server Platforms
---

### Post by neoculture on 2012-06-06
I am a home enthusiast with a *very *understanding wife. I have been, over the last 6-or-so months, playing with virtual computing using Xen and VirtualBox. I am relatively happy with it and the mail server I am running inside a VM (whose virtual HDD is hosted on a 14TB RAID-5 ubuntu file-server over a 1Gb network) seems pretty stable. I might create a virtual web server next, just to see what happens.

But this has led me to look around my home office (OK - den) and take in the multitude of boxen sitting on the floor, on the desk or (in the case of the aforementioned file server) winking their lights at me from their rack-mount. And it got me thinking that I should probably start messing with cloud computing. And this is where the frustration begins...

There does not seem to be a decent "cloud-computing for dummies" - at least not one *I *can find. Most of them give you cookbooks, but do not explain the basics; for example, can you mix boxen with differing hardware? (e.g. differently-specced CPUs, different amounts of RAM, different amount of HDDs, etc...) What if one box has hardware the other boxen do not have, such as (in the case of one of my spare PCs) a PCIe TV-capture card - will this be unavailable in the cloud? Will it be available to anything I run in the cloud? And what about those HDDs sitting all over the place?

Questions, questions, really *_basic_* questions to which I cannot find the answers. Can someone point me to a decent "I know about computers but I do not know anything about cloud please teach me" websites out there?  Thanks.

(Of course, the best outcome as far as I am concerned, would be for all my disparate hardware to look like one large computer with a really odd set of CPU cores, a large amount of RAM and HDDs and various PCIe cards, which could then run whatever VMs I started on it.  I can dream, can't I?;) ;) )

---

### Post by LHammonds on 2012-06-06
> **neoculture said:**
> 
(Of course, the best outcome as far as I am concerned, would be for all my disparate hardware to look like one large computer with a really odd set of CPU cores, a large amount of RAM and HDDs and various PCIe cards, which could then run whatever VMs I started on it.  I can dream, can't I?;) ;) )
You do realize this is how Skynet begins.  [-X

---

### Post by sandyd on 2012-06-06
> **neoculture said:**
> I am a home enthusiast with a *very *understanding wife. I have been, over the last 6-or-so months, playing with virtual computing using Xen and VirtualBox. I am relatively happy with it and the mail server I am running inside a VM (whose virtual HDD is hosted on a 14TB RAID-5 ubuntu file-server over a 1Gb network) seems pretty stable. I might create a virtual web server next, just to see what happens.

But this has led me to look around my home office (OK - den) and take in the multitude of boxen sitting on the floor, on the desk or (in the case of the aforementioned file server) winking their lights at me from their rack-mount. And it got me thinking that I should probably start messing with cloud computing. And this is where the frustration begins...

There does not seem to be a decent "cloud-computing for dummies" - at least not one *I *can find. Most of them give you cookbooks, but do not explain the basics; for example, can you mix boxen with differing hardware? (e.g. differently-specced CPUs, different amounts of RAM, different amount of HDDs, etc...) What if one box has hardware the other boxen do not have, such as (in the case of one of my spare PCs) a PCIe TV-capture card - will this be unavailable in the cloud? Will it be available to anything I run in the cloud? And what about those HDDs sitting all over the place?

Questions, questions, really *_basic_* questions to which I cannot find the answers. Can someone point me to a decent "I know about computers but I do not know anything about cloud please teach me" websites out there?  Thanks.

(Of course, the best outcome as far as I am concerned, would be for all my disparate hardware to look like one large computer with a really odd set of CPU cores, a large amount of RAM and HDDs and various PCIe cards, which could then run whatever VMs I started on it.  I can dream, can't I?;) ;) )

You want to take a look at -> [https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)

---

### Post by blackbird34 on 2012-06-06
You may like [this]("http://www.debian.org/News/2012/20120425") too : 
**[Deploy your own cloud with Debian Wheezy]("http://www.debian.org/News/2012/20120425")**

---

### Post by neoculture on 2012-06-06
I have read (or at least skimmed) both URLs and (apart from finding out that OpenStack doesn't seem to support VirtualBox) still find myself without any answers. Both URLs (and the pages the pointed to) rated pretty high on the "cookbook" aspect (which may come in useful if I decide to play around with a cloud installation) but none of them (for example) answered as simple a question as:
(1) Can you use disparate hardware as servers (i.e. one box as an i7 CPU, the other an i5, the third an AMD, one has 4Gb RAM, the other 8Gb, etc)?
(2) If a server has a type or piece of hardware (e.g. a PCIe video capture card) which no other server has, how will it be presented to the cloud? Can it even be used?

All of those *basic* questions seem to be overlooked. And the answers may be obvious for those well-versed in Cloud. But for someone who is fresh-new coming to cloud-computing, these are the sort of question which will be asked and require at least an FAQ somewhere.

---

