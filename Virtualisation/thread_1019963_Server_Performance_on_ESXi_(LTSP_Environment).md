---
title: "Server Performance on ESXi (LTSP Environment)"
date: 2008-12-23
forum: Virtualisation
---

### Post by Rich_B_uk on 2008-12-23
Hi all :)

I'm wondering if anyone with experience with the above can impart some advice?

Basically, I'm considering deploying an Edubuntu powered server to support in the region of 15 thin clients. I'm really excited about the big leaps forward in LTSP5, and in particular the great work on LocalApps.

Anyway, I'm just wondering what the performance hit is for running an Edubuntu server as an appliance under VMWare ESXi or similar products as opposed to as its own OS.

I imagine it's pretty much a non-starter due to the vast amount of data flowing to and from the server at a network level but I'm looking for some confirmation/stats/testimonials. This in turn could also degrade the performance of other appliances on the VMware server significantly? 

Ideas guys & gals?

Thanks in advance for any help. It's very much appreciated! :P

---

### Post by PilotJLR on 2008-12-26
Provided there is sufficient network bandwidth to the host, I wouldn't be concerned with that. Even a single gig connection to the VM Network port group could feed 15 clients with room to spare. I have clients with hundreds of Citrix users on ESX vm's (provided the infrastructure is sized properly).

Terminal servers, by their nature, have very differnet workloads... so bottlenecks are going to depend on what apps your users are going to run. Some term servers are io constrained, some memory, etc... it all depends on the workload.

Provided the ESXi host has enough disk io and RAM, you should be fine. If you see a yellow or red bang in the VI Client on host memory, then you know you need an upgrade!

---

### Post by Rich_B_uk on 2008-12-26
Hi PilotJLR. Cracking timing that! Happened to click on and see your response.

For the scenario I'm thinking of, it would be helpful if I could put all my dependent services in as apps on a single low power, multi-core box, hence the focus on VMware. Like I say, I think I just had it in my head that I would be constrained by overheads within ESXi when dealing with some network heavy apps. From my reading, a Gig connection can soon get saturated if users are attempting multimedia apps (raw pixel data et al).

What also occurs to me is that if I have another appliances (Squid & DansGuardian) on the same box then in many ways, keeping all the services on one unit will be kind of beneficial so long as I spec up hardware with enough internal memory bandwidth (Ah RAMBUS, how I miss thee).

I take your point about the disk io and RAM. I'm thinking 2GB, 2 cores and a separate small SATA RAID1 array should see it flying for around 15 users.

Perhaps using [Hardinfo ]("http://hardinfo.berlios.de/HomePage")or following [Ben Martin's methodology here]("http://www.linux.com/feature/144532") will give me some solid numbers on the overheads. If I get around to it and VMWare allow the numbers to be posted, I'll be sure to post them.

Any thoughts anyone? Am I missing anything major here? Open to ideas or analysis! :P

Oh, and hope you all had a good Christmas.

---

### Post by PilotJLR on 2008-12-26
You could bond NICs on the ESX host to increase throughput... so getting to 2 or 4 GB of throughput on the host would be inexpensive to do, if 1 GB isn't quick enough. Bandwidth aside, you'd normally team at least 2 NICs for redundancy.

I'd beef up this server considerably more. As a really general ballpark estimate, most people with dual proc quad core servers can achieve 20-25 production VM's per host with 32 GB of RAM on the box... this target may help extrapolate what you need given the workloads you plan to put on the host.
So this is still really workload dependent, but I'd recommend putting several gigs more on this machine. With 2 GB of the host, you'll hit the ceiling really fast. ESX or ESXi should never have to swap to disk; performance is severely impacted when ESX has RAM contention.

From a disk standpoint, a 2 disc SATA array is quite slow... this may be completely okay, it also depends on your needs. If the users will have disk intensive apps open, then this may not be fast enough. Going to SAS, or using more drives in RAID 10, are two possible solutions.

Do you have an existing LTSP? If so, you can pull disk performance numbers with iostat. Getting a peak iops requirement would help determine if SATA will work in this setup.

Lastly - will this be a whitebox? If so, do lots of research of the chipset you're using, as the ESX / ESXi compatibility list is stringent. It's entirely possible a desktop motherboard, for example, would have either storage controllers or network interfaces that ESXi can't use. The easier solution is to buy a branded server from HP, IBM, etc that is listed on the ESXi HCL.

---

### Post by Rich_B_uk on 2008-12-27
Hi again Pilot. To expand upon this, the server itself is intended to be placed in a mobile environment, to the point that it won't always be powered up, and it certainly won't be able to run what we consider traditional server class hardware.

We're looking at the high efficiency X4 Phenoms coming in at <45w TDP paired with 4-8GB RAM for the entire server.

It needs to support a max of 15 students doing relatively intensive apps (although we're looking to offload where possible through localapps) as well as 2-3 other VMs at any one time to provide cached net access, a CMS, and possibly another couple of bits and pieces. As you can see, we're not talking about a commercial environment and squeezing as many VMs out per host as possible. It simply needs to the job well while meeting a certain electrical envelope.

At other times, the server may have to perform other functions as a captive portal, running a different CMS, and providing OLPC Server capabilities. This is why I'm so focused on keeping everything centric on one box. I will certainly look into the LAN bonding you mentioned as it's something I didn't heavily consider. Certainly, I would like to give the LTSP its own Gig connection into the switch, and run the other VMs off other Network Adapters (and of course different cores.

---

### Post by Rich_B_uk on 2009-01-15
Seems to be running well with a couple of clients off a modest P4 2.8ghz HT / 3gb box (Ed has 2gb)

It did briefly occur to me to use XFCE instead of Gnome, but I don't think the setup would benefit greatly. Plus, the whole scenario is intended for users who may not have been exposed to many PCs (let alone Windows) machines in their life so I think it would be wise to let them cut their teeth on Gnome because they're simply more likely to come across a distro running it.

When I have some screencasts/how2s on the go, I'll post them. I know the vast majority of people will know how to achieve the same results, but more support documents for the community can never be a bad thing. :P

---

