---
title: "bladepc or virtual machine?"
date: 2008-03-05
forum: Server Platforms
---

### Post by netlogic on 2008-03-05
Any firms in the process of moving or have changed their PC to bladepc or virtual machines? Bladepc is a more expensive solution compare to Virtual Machine Desktop, but it is only little more than the PC. Have anyone did some intensive investigations? Terminal client model is just too slow for today's needs. Also, able to easily choose between Windows and Linux in the future are very desirable.

Thanks in advance.

---

### Post by nickjqw on 2008-03-05
> **netlogic said:**
> Any firms in the process of moving or have changed their PC to bladepc or virtual machines? Bladepc is a more expensive solution compare to Virtual Machine Desktop, but it is only little more than the PC. Have anyone did some intensive investigations? Terminal client model is just too slow for today's needs. Also, able to easily choose between Windows and Linux in the future are very desirable.

Thanks in advance.

I've looked at this or been near others looking at this in the past.  It's been a while since I've priced out blade systems, but with virtualization becoming so much mature, I think that's the better bet.

I'd price out a few dual quad core or larger server class machines with SAN access, then look at how to manage all your systems on these Virtual Server Hosts.  VMWare has a great product, but it's very expensive.  Their product allows seamless migration of VMs from physical host to physical host.

Main selling point of VMs over blades, IMHO, is that you can have several servers that are nearly idle on a virtual server host.  On blades, you have to allocate them 1 to 1.

So say you have 25 Linux servers today.  2 are really busy, 10 are loaded at certain times, and the other 13 are mostly idle.  With 3-4 physical servers, you can host them all with great performance.  With blades, you need 25 blades... and the ones that need lots of resources don't have enough, and the others have too much.

Nick

---

### Post by netlogic on 2008-03-05
I have been playing with Vmware at home office for few years, and four web servers on a physical barebone box. The issue with VM is, what if one user's processing load has to grow larger right away? Let's say, this is a marketing person who utilizes Photoshop and Powerpoint. There is no way to specify percentage of CPU utilization to a particular user such as give 40% max to JOE, 30% to Cindy, and 30% to Matt.  There is no max CPU settings. I know you can use nice to sign priorities, but you can't assign a LOCKED limit to the process load. I don't want one user's demand to impact other users. It is hard to predetermine each users specific processing needs. I know you can assign each virtual machine to a single core on a multicore server environment. I know you can buy 8 core servers and give each users their own core, but these servers are expensive. The bottom line is if the users experience isn't good. It is no sale to the customers. I heard recent clearcube client stations can share multiple clearcube to  one blade now. It is no longer one to one. They are starting to integrate some of the virtual machine technology. Definitely desktop concept has to go away in the future. It is too 90s and cost way too much money to maintain. Also, hiring people to move new PCs aren't cost effective.

---

### Post by netlogic on 2008-03-05
Never mind about the CPU Limit issue. I just found a new app called, cpulimit.  I will do some testing tonight. Now, I need to figure out how to change process limit by hostname on each VM using a script. Anybody already did the work, let me know.

---

### Post by bonezie121 on 2008-03-05
We run 2 Large Servers here with ESX loaded on them.  I dont know about 3-4 Servers running 25 machines.  We have about 25 machines loaded on one physical box now.  The server hardware is identical.  They each have 32Gb of Ram and 8-3.0GHz Procs and we arent even running at about half our recommended max.  I would have 2 servers for redundancy.  You can have a "Mirror Cluster" setup to allow updates to be done in real time and not affect the server connection at all.

---

### Post by netlogic on 2008-03-05
Thank you for the reply. What is your client VM's OS? How much processing limit have you gave to each users? I am assuming you have assigned around cpu limit to 800 to 850mhz limit to each users and left around 5% of CPU capacity to the core  OS that manage the other machines. Are you caching the pagefile to ram? If you have 32gb on the server, I am assuming you have located estimated 1.2 gig per user desktop and 10% slack to the core OS. Have you turned the pagefile.sys off on the workstation or have you created a ramdisk by partition the ram per user's VM? Like 844 megs of ram and 356 on a ramdisk for pagefile. I am assuming running all the pagefiles of 25 workstations on the same raid5 or over SAN might slow the workstation down.

Thanks again.

---

### Post by netlogic on 2008-03-05
One more think I would like to add, which thin client machines did you go with? Did you build your own using VIA itx boards or purchased one from the vendor?

---

### Post by netlogic on 2008-03-07
Anybody has anymore to add to this topic?
Thanks.

---

