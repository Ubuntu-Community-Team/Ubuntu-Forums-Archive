---
title: "Recommendation to provide linux virtual desktops solution"
date: 2015-02-16
forum: Virtualisation
---

### Post by perumal_raj on 2015-02-16
Dear Folks,

We need to provide a VDI solution for anyone of the following Linux desktops.

1.       Ubuntu dektop
2.       Linux Mint
3.       Red hat Desktop OS

According to details I gathered so Far these are the options
 
1.       VERDE
2.       Oracle VDI
3.       RHEV
4. Ulteo

We need both persistent and non persistent desktops. Please provide your recommendations any idea's. Help us choose the right solution

Thanks and Regards
J P Raj

---

### Post by TheFu on 2015-02-16
I've been using NX-based x2go for about a year. Before that, used FreeNX - the NX protocol is amazing, but has some challenges too. Our deployment is small-scale.  NX includes a secure channel - no extra VPN is required and HTTPS (not really secure) isn't used.

It would be worth looking at Xen VDI too ... citrix, right? Citrix XenDesktop

RHEV ... is just Spice over KVM. Any Linux should be able to do that. What Redhat adds from a management side I don't directly know.

---

### Post by perumal_raj on 2015-02-17
Hi, we are looking large numbers say 2k linux desktops to be virtualized.

---

### Post by redger on 2015-02-26
umm 2k is a lot

I use LXC containers and x2go along with KVM VMs on the same desktop class machine

my intel 4670 cpu runs (permanently) a mythtv-backend container, 2 desktop containers (1 attached to host x-server directly and 1 via x2g), with another 4 containers started as required ..... plus it runs a KVM Windows machine and a couple of KVM Ubuntu machines as required ..... with no noticeable performance issues. The point being containers are very lightweight so even a low powered CPU can support many of them ... and they're very stable and quite secure (I run my mission critical HTPC as a container :) )

I can't imagine the management of 2k images tho ... you will need one of the large scale container management tools for that (like Docker, tho Docker is probably not the best tool - being stateless)

---

### Post by TheFu on 2015-02-26
> **perumal_raj said:**
> Hi, we are looking large numbers say 2k linux desktops to be virtualized.

Why not put 500 users per server (or whatever the server supports) and let them share the OS? No need for every person to have a private install - actually, I'd put teams/groups onto the same system so they can cooperatively edit documents using AbiWord.

Linux is multi-user just like Unix - use it to your advantage.

Also - the security for containers of any type is completely unknown. Saying anything else is simply unproven.  It takes time to prove any new technology is actually secure.  There's a [great quote about container security here.]("https://www.quora.com/How-secure-is-docker") > Docker is not a security boundary (nor is LXC). There are numerous privilege escalation bugs that have been found in Linux, and nobody pretends that there aren't more. Further, once you have root, it's fairly easy to break out of a chroot jail, and from there, out of any other process restrictions.

If you need security, don't trust any containers.  If you need to spin up virtual environments and can trust all the users and external access is very limited, containers make a great solution.  I like containers for developers who need new VMs all the time for testing. Never on production and never, ever, ever, on the internet.

IMHO.

As far as management goes - devops tools like puppet, ansible, saltstack, rexify, ... chef, cfengine .... others have that solved.  Managing 10 or 1000 systems really isn't much different, especially if they are the same.

---

### Post by SeijiSensei on 2015-02-26
> **perumal_raj said:**
> Hi, we are looking large numbers say 2k linux desktops to be virtualized.
I have no experience with any of this, just approaching it as an intellectual problem.

Aren't the minimum memory requirements for a task like this something on the order of 0.5-2 GB/desktop * 2K desktops = 1-4 Terabytes?  Dell sells [this monster]("http://www.dell.com/us/business/p/poweredge-r920/") that supposedly can support up to 6 TB.  You'd probably have to contract to build something that large.  Using the online form, I could only buy a machine with 256 GB.

Still that might be a better choice than one single machine which means a single point of failure.  How about buying 16 of those machines and using [clustering]("https://www.thomas-krenn.com/en/wiki/HA_Cluster_with_Linux_Containers_based_on_Heartbeat,_Pacemaker,_DRBD_and_LXC") to create a single 4 TB memory space and run all the desktop instances in that?  That seems a lot more fault-tolerant to me. Linux clustering is a well-established technology that powers enormous machines at places like the [Lawrence Livermore National Laboratory]("https://computing.llnl.gov/tutorials/linux_clusters/").  The Department of Energy is now deploying [this system](https://computing.llnl.gov/tutorials/linux_clusters/TLCCannouncement.pdf) in its three principal research laboratories.  [IBM's Watson]("http://www.zdnet.com/article/what-makes-ibms-watson-run/") also runs on a Linux cluster.

That Dell R920 comes in a bit under $13K with 256 GB and a mediocre CPU.  There are some pretty expensive processor upgrades that can push the price over $20K per machine.  With 16 machines, you're essentially supporting 125 simultaneous sessions on each one, so you might need those expensive processors. Using a farm of 32 machines with 128 GB each and cheaper processors might prove more cost-effective.  I'll let you do the math for that!

All told, we're probably looking at a minimum cost just for the servers of $300-500K.  You'll still need terminal hardware on the desktops of course.  Even at $100-200 per desktop, that's going to double roughly the cost of the project.  Add in the supporting hardware and we're looking at a minimum of $1 million in hardware, or about $500/desktop.  From a support perspective that's a good deal in the long run compared to desktop PCs.

---

### Post by TheFu on 2015-02-26
Some folks in my LUG did a [LTSP]("http://www.ltsp.org/") deployment for a local school system years ago.  I think it was for 500 concurrent users, so not nearly as large as this.  IBM has been doing this too, but they are using TinyCore as the basis for their custom image according to what I've heard.

Because students tend to run the same programs, the use of shared libraries really reduces the total RAM needed for each OS instance - basically just the DS will be different for each user. That's the theory.

---

### Post by SeijiSensei on 2015-02-26
The OP is talking about 2000 simultaneous virtual machines though, isn't he, and not just a terminal server deployment?

---

### Post by TheFu on 2015-02-26
> **SeijiSensei said:**
> The OP is talking about 2000 simultaneous virtual machines though, isn't he, and not just a terminal server deployment?

Perhaps, but often people don't consider that Linux is multiuser and that is a real, and usually better, option.  

I re-read the OP and it isn't clear. Read the follow-up post - it isn't clear either.  2K servers is very different from 2K users.  I'd guestimate that 2K users would be supported by 10 servers or so, depending on the workload. It really is about the workload which will drive networking, SAN, RAM, ....

---

