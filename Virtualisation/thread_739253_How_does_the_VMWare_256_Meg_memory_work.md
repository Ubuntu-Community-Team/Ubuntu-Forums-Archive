---
title: "How does the VMWare 256 Meg memory work?"
date: 2008-03-29
forum: Virtualisation
---

### Post by bluewhale on 2008-03-29
Would anybody be kind enough to explain the VMWare default of 256 megs of RAM in each virtual session? Is the allocation a one for one affair? If so I would think most of us would like to have 1-2 gigs of RAM for each XP instance under Ubuntu. ?

---

### Post by .nedberg on 2008-03-29
256MB is not enough for XP, but remember that giving it 1-2GB requires that you still have something left for Ubuntu and VMWare. If you have 4GB of RAM, go ahead and give it 2GB.

This can be configured for each virtual machine you have.

---

### Post by bluewhale on 2008-03-29
So it IS a straight mapping. I was hoping there were memory tricks at work. If so that would allow me to run many more clients than at present. Fellow who taught an ESX course indicated he had one client who was able to place 100 virtual servers on one physical machine. they all were stripped down and all had the same configs but still... 100...  !

Thanks for the info.

---

### Post by .nedberg on 2008-03-29
Well, with 256MB for each of them it would give about 25GB. It sure is a lot, but not that much.

---

### Post by stefangr1 on 2008-03-29
> **bluewhale said:**
> So it IS a straight mapping. I was hoping there were memory tricks at work. If so that would allow me to run many more clients than at present. Fellow who taught an ESX course indicated he had one client who was able to place 100 virtual servers on one physical machine. they all were stripped down and all had the same configs but still... 100...  !

Thanks for the info.

Luckily you don't need to have as much memory in the host machine as the sum of the client machines that are running.

In vmware-server, under "Edit host settings" in the memory tab, you can specify the maximum host RAM that can be used by all virtual machines together.

As we speak I am running Windows XP and Ubuntu-64, both with 1024mb RAM. Together they use slightly less then 50% of my total 2GiB system memory.

---

### Post by fjgaude on 2008-03-29
> **.nedberg said:**
> Well, with 256MB for each of them it would give about 25GB. It sure is a lot, but not that much.

Yep, many servers have 32Gs of RAM, some 64 or even 128Gs.

---

### Post by dcstar on 2008-03-30
> **fjgaude said:**
> Yep, many servers have 32Gs of RAM, some 64 or even 128Gs.

64 bit servers.......

---

### Post by fjgaude on 2008-03-30
> **dcstar said:**
> 64 bit servers.......

Of course. <smile>

---

