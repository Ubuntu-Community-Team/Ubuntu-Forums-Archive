---
title: "Max resources I can provide to Windows VM?"
date: 2016-06-09
forum: Virtualisation
---

### Post by Oliver_Davey on 2016-06-09
Hi everyone. I was hoping you could answer this for me. I won't be doing a ton with Ubuntu but for various reasons I would like to install it and run Windows through a VM (via VMware).

My specs are as follows. Can you tell me what I can feasibly allocate as far as resources to get the most out of what I have without draining Ubuntu? I'll be upping the RAM on the system to 12GB before long but I would like to get going with this now and allocate the extra memory later.

- Intel Core i5-4200U Processor 1.6 GHz
- 6GB RAM
- 500 GB HDD

Thanks.

---

### Post by MAFoElffen on 2016-06-10
It all depends on what you will be doing... 

A quick rule of thumb (suggests recommends by most) says that you should resrve half your memory and and one core reserved for the host. Most hypervisosrs will tell you how many cores you can allocate. For my main server I have 2x 4core CPU's. It says I can allocate 7 cpu's. So you can allocate 3 vcpu's.

But the memory is subjective. On 96 GB RAM, keep 2 GB reserved for my host. That is far from the 1/2 rule of thumb rule. I think that rule of thumb must have came about years ago, Server now can run 1TB RAM.

When allocating resources, I lean towards the stingy side. On memory, even if the hypervisor I'm using can do dynamic memory allocation, I'll tell is to start on a minimum, and limit it to what I feel it might take. For instance on Windows desktop VM's, I usually tell them to start on 1GB and limit them to 2GB. If I see it lagging, I'll bump it up, as needed.

On disk, on Windows, I do between 64 GB on a minimum Win Server or 120 GB minimum on a Win Desktop. I used to do dynamic disks. Now I allocate what I think it might need (fixed size), then do LVM for Linux / Storage spaces for Win (Win's version of LVM) ... that way if it need's more room, I can add more on the fly. This does two things for me. (1) Keeps the host disk from filling up without me noticing. (2) Makes it easy to add storage. (you don't having to copy to a larger recreated VM image file.)


My Ubuntu on My main box, I've had for about 5 years. I have a lot of programs installed on it ... and lots of files ... And I think it's about 300 GB, with lots of room to spare. It's It's a dual boot. The other side of it is Win 10. That part is tight in 700 GB and tight. Lots of games and every program on it takes a fair chunk. 

But if doing tests, I do a Linux desktop in 10GB and a Win Desktop in 120GB. But those are wiht not a lot of programs installed to each. I would say, on the average in my tests, about a 1:4 ratio between the two.

You didn't say what it's job will be, You talked about a memory upgrade, which would not hurt, but storage (disk) is where I can see you wanting in the near future. Note my comments on that ... and adding more to it that way will make that easier in the future.

My recommends would be to start out with Dynamic: start on 1 GB, limit to 3 GB RAM; Fixed disk, 200 GB, using storage spaces. But just a shot in the dark without knowing what you will be doping.

---

