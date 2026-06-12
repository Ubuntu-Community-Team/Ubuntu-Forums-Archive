---
title: "nginx global setting"
date: 2020-07-10
forum: Server Platforms
---

### Post by dyoms on 2020-07-10
Hi. We are new to managing the Linux Server (Ubuntu 20.04) and are hoping that someone can enlighten us about what settings that we can make so our application can run smoothly on both our server and the application that we developed. So here are the specifications of the server and the application information:

Ubuntu Server 20.04
1TB SAS Raided
64gb RAM (16 cores)

Running there is a administrator website for a mobile application which is a time in and a time our for our employees with a geolocation coordinates and a picture to be uploaded.

For now the application with the website are only consuming 1gb of our ram and wanted to maximize the use of our server. And another problem is that for some reason the server cant smoothly run the time in and time out of more than 5 thousand employees simultaneously and is freezing. Can someone help us what settings can we do with our nginx or any other settings that can help us with our problems especially when it comes to [www.conf](www.conf), nginx.conf etc.

Thank you in advance.

---

### Post by TheFu on 2020-07-10
Why not try using apache?  See how useful that suggestion is?

Sounds like you need a professional engagement by an expert in app tuning, server tuning, monitoring and alarming.  if there is a DBMS, may need a DB tuning expert too.

RAM use is just one possible bottleneck.  Need to look a network and disk I/O, wait states, caching, CPU, and optimize the session data as much as possible.

is all the traffic good or can some be nefarious that should be blocked?

---

### Post by dyoms on 2020-07-11
Good day! Brother TheFu.

Is Apache better than Nginx?

Yes professional tuning is what we need right now. Can you suggest a settings that we can use for now?

Yes all traffics are good and nothing should be blocked.

---

### Post by LHammonds on 2020-07-11
Well, depending on the app, web servers have a simultaneous connectivity limit.  If you are running a single web server, you might want to change that up a bit.

In your description of the server, you left out a lot of details...the very-most important being your network capability.  Are you utilizing a single NIC?  Is it a 100 mbit card or 1000 bit or is it fiber?

When setting up a web server for high-availability (especially for bandwidth), you need a design that exceeds your expectations (because growth is rarely downward).

If you only have a single server, you are fairly limited in your options, however, it is likely you can benefit from virtualization.  Install a hypervisor on the server so you can run multiple virtual servers which seems like a good idea since you have the RAM and CPU capability.

Here is a design that would allow adding multiple web servers and databases easily to compensate for any needed capability however it is likely overkill in your scenario but it can be adjusted to your needs.  It is something to think about.  I also have detailed instructions you can go through for each component if you want to look through them.

[IMG]https://hammondslegacy.com/images/linux/design-ha-lamp-service.jpg[/IMG]
Please don't forget about having a backup server that can take over if the primary goes offline or at least just a destination for backups to exist so you can restore your server(s) in a disaster.

LHammonds

---

### Post by TheFu on 2020-07-11
> **dyoms said:**
>  Is Apache better than Nginx?

Sometimes. "It depends" is the only answer. Are there things that nginx cannot be tuned to accomplish that apache can?

> **dyoms said:**
> Yes professional tuning is what we need right now. Can you suggest a settings that we can use for now?
Changing settings without facts is counter productive. Gather the facts first. Determine what is performing below accepted values and tweak those things one at a time. Gather the facts again for the entire solution to see if those tweaks helped or hurt. If they helped, now there is a new bottleneck to be addressed.  Do those steps over and over and over based on the data and facts.  There's no magic setting here.  You have to do the work ..... or pay someone else to do it.  

Further, it may be **good enough** after the first few iterations, but once you have someone (or a company) engaged, you probably want to free up as many bottlenecks as possible. Early things found can be 10% or 500% improvements or more.  Probably need to go through at least 1 round of fixing bottlenecks for each of the main areas before stopping.

Be certain your developers pay attention and learn.
Be certain your network and systems admins also pay attention and learn.  Or in 5-10 months, you'll be back with similar problems again.

> **dyoms said:**
> Yes all traffics are good and nothing should be blocked.

I find that nearly impossible to believe for any system on the internet.  Just today, I've seen over 10,000 attacks, mostly useless, against my network. They are mostly useless because I've spent the time to look at the requested URLs and block access to all admin URLs from non-company subnets. Saw a few guacamole attacks today.

---

### Post by dyoms on 2020-07-11
thanks for the reply bro Lhammonds

we can provide another 2 or 3 servers but the specifications are not as the main server. we will try to do this as you instructed for some uploads are still slow after computing the settings and then adjusted.

Yes we are utilizing a single nic and has a 1000mbit capability. 

do you have a guide on how to set up 3 nodes with 3 servers not virtual. it will be much appreciated.

---

### Post by dyoms on 2020-07-11
Bro TheFu

one of my colleagues suggested we use nginx so i dont know really. and ooh ive been computing some settings and it actually makes a difference on how our website loads like 10x better now after doing some minor global settings.

and yep i dont think someone would spend a lot of time hacking a small attendance system right. well we would be delighted to learn some counter for those attacks. honestly, we are really a newborn baby here in ubuntu/linux. trying to learn and really grateful to you guys who take time to help us with our concerns. anyways will try brother Lhammonds method and we will see where itll get us. will update soon.

---

### Post by LHammonds on 2020-07-13
> **dyoms said:**
> we can provide another 2 or 3 servers but the specifications are not as the main server.I would still lay down a hypervisor on each server (such as Proxmox), even if you only plan to run a single virtual server on it.  It would allow you the flexibility to add other VMs if desired and you can utilize virtual-based backup systems with snapshots.  Just imagine having 4 physical servers, all setup as virtual hosts.  You could have the HA configuration in the picture I showed where you could lose a single physical server (think failed hardware) and the whole system would continue to function....if you separated the sources correctly such as no server being a single point of failure (e.g. not having all the databases or web server or load balancers on it).  You could test all this design out on a single machine using virtualization.

> **dyoms said:**
>  do you have a guide on how to set up 3 nodes with 3 servers not virtual. it will be much appreciated.
When I documented how to setup a web and database server for high availability (like the image I showed you), I did so using Ubuntu Server 18.04.  You can do the same thing with 20.04 but there will likely be small differences in specifics.  The design is flexible though.  You could setup two proxies (each on a different physical server) which load balance traffic to multiple web servers (two or more).  You could have just a single database server with no HA option or you could split it into 5 servers for HA (2 proxy, 3 DB cluster nodes).

Typically, the web app servers do not need to be super-beefy...you just need more of them.  The database is typically what needs to be on a powerful server with lots of RAM.

I don't have more time to go over all the potential variations but here is a list of tutorials I did for 18.04 which you can tailor to your needs:

My tutorials assume the base server was setup following this template: [How to Install and Configure an Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244")

To setup a high-availability system:
[How to Install Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261")
[How to Install MariaDB Galera Cluster on Ubuntu 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262")
[How to Load Balance Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260")
[How to Load Balance Galera/MariaDB Servers on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264")

To setup a single web server and single database server:
[How to Install Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261")
[How to Install MariaDB 10.4.x on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=266")

**EDIT #1:** If all I had was 4 physical servers total, I would setup the 10 virtual servers on 2 physical servers in such a way that one going offline will not take down the system.  I would also make sure I had 2 UPS each going to a different electrical circuit.  If the server has 2 power cables each, I would criss-cross them into each UPS to ensure best potential for uptime in a loss of power event.  I would use the other two as remote backup targets and maybe even have them running some of the nodes in case one site goes completely dark, you can "still" stay online.  ;)

**EDIT #2:** Keep in mind that I do not know your site or requirements and that the HA system may very-likely be complete overkill.  However, it does allow the flexibility to scale out addition servers as needed with little fuss.

**EDIT #3:** You "could" use just a single database instance and if you want to expand it to a cluster in the future, it shouldn't be too problematic.  You could insert the DB load balancer's virtual IP as the old database's IP address that the web server(s) referenced so you could slide the cluster into use fairly easy and little downtime.  So you could setup a couple web servers (with load balancer proxy front-ends) and utilize a single DB server at the beginning.  Then increase the amount of web servers as needed and implement a DB cluster if needed later.  Again, this is VERY trivial "if" you initially set it up as virtual machines...not so trivial if you installed directly onto a physical server.

LHammonds

---

### Post by TheFu on 2020-07-13
+1 on using VMs or at least Linux Containers.
We stopped running servers directly on hardware around 2005. Since then, the servers running on physical computers are all VM hosts.

---

### Post by dyoms on 2020-07-13
> **LHammonds said:**
> 

My tutorials assume the base server was setup following this template: [How to Install and Configure an Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244")

To setup a high-availability system:
[How to Install Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261")
[How to Install MariaDB Galera Cluster on Ubuntu 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262")
[How to Load Balance Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260")
[How to Load Balance Galera/MariaDB Servers on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264")

To setup a single web server and single database server:
[How to Install Apache Web Server on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261")
[How to Install MariaDB 10.4.x on Ubuntu Server 18.04 LTS]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=266")



Thank you for these. Will do these and will let you know. BTW we are running NGINX instead of apache and mySQL instead of MariaDB.

---

### Post by dyoms on 2020-07-13
> **TheFu said:**
> +1 on using VMs or at least Linux Containers.
We stopped running servers directly on hardware around 2005. Since then, the servers running on physical computers are all VM hosts.

Does this mean our servers should be running VMs instead of Physical Servers? Please treat us as newborn, we dont know much I promise.

---

### Post by LHammonds on 2020-07-14
It means installing a hypervisor directly onto the physical machine (such as Proxmox or vmware ESXi).  This physical machine is referred to as a "host." Then allocate resources to a virtual machine and start it up...which is a machine in a machine.  Depending on the OS workload, you could run a dozen servers on a single host.  Most servers will sit mostly-idle....so running multiple virtual servers on a single host allows you to make better use of the hardware.  I like to run enough servers on a host to utilize 70% to 80% of the resources (I have 8 hosts).  However, that also depends on the amount of hosts running.  If you only have 2 servers ***with a similar resource configuration*** and want a high-availability setup, that means you need to run at no more than 40% to 45% of capacity on each host so that if one host goes down, you can run all the VMs on a single host (e.g. maintenance of host hardware).  You can utilize more and more per host the more hosts you have.  Such as being able to run at 60% capacity if you have 3 hosts or 70% capacity if you have 4 hosts, etc.

I started to document [how to install, configure and use Proxmox](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=276&) but it is not "finished" documentation since I got pulled off it to work on other projects.

LHammonds

---

### Post by TheFu on 2020-07-14
People in IT have been using virtual machines or containers almost exclusively for over a decade. Some places for over 15 yrs.  

There is so much added flexibility and minimal overhead in running VMs today that is just isn't worth NOT using a VM.  Decoupling the OS from the hardware is a very great thing.  After you've done your first migration of a VM from one system to another with nearly zero downtime, you'll become a believer too.

I would avoid all VMware stuff due to the high costs.  VMware is sorta like Apple stuff. Once you buy the laptop, all those little extra devices and software also cost more.  OTOH, if you say with F/LOSS ... like Proxmox, Xen-NG or KVM+virt-manager, all those little extras are free too.  A quick example is backup software.  On VMware ESXi, everyone uses commercial backup software. Last time I priced out those tools, they were $1000 for each system.  OTOH, our KVM system use F/LOSS backup tools - source code and running as many copies as we need are $0 - and actually work much faster than the paid options for VMware.

What you get with VMware is a phone number to call. Paid training is available (but not cheap) and when something bad happens, related to the hypervisor, an expert you can pay to show up and fix stuff.  That expert won't be cheap.  My company worked with a certified VMware expert - he also did training for VMware.  The guy retired at age 40.  You don't do that being underpaid.  I think his hourly rate was $200-$300.  Easy access to certified people is one great thing about VMware.  Everything around ESXi is expensive ... so that can be a good thing or a bad thing depending on your career goals.  If you are technical, you want to know ESXi because you'll always be employed, somewhere. Those places will be used to paying for costly software AND for the people to run those systems.  An ESXi admin will earn 15% more than what other hypervisor admins earn.  But they tend to become silo'ed.  They don't keep up with other hypervisors, so they become like MSFT-certified people - only pushing MSFT solutions. The same happens for VMware trained people.  

I was one of those VMware trained people, but when I started my own company and VMware raised the costs to run their software over 50%, I started looking at other solutions. That was in 2010.  Found KVM and switched all our ESX/ESXi and Xen hypervisor hosts over to KVM.  I have never, not once, regretted that choice. I could have made much more money if I'd stayed in the VMware world, but my conscience would not like that knowing what I know about the other options.

Finding someone certified in Xen or Proxmox or KVM isn't as easy - though both Xen (Citrix) and Proxmox have commercial companies behind them, so you can get experts easily, for a price.  

KVM experts are harder to find. That's because there isn't any formal training for KVM. Nobody is registered. Most are self-taught, like me.  I'm only an expert in KVM for the things I've used.  I have friends who run huge KVM server farms - over 2500 physical servers. These are part of openstack deployments.  My day to day work is around a few small clients who have 3-server KVM setups, running fewer than 50 VMs.

For my home environment, I only run about 10 VMs on 3 physical systems. Most run on a single machine with the others used for testing and when HW upgrades are planned.  These systems are extremely stable, BTW. If it wasn't for patching requiring a reboot, they'd run indefinitely without fail.

With all that said, I completely agree that proxmox is probably the best answer for your initial VM needs.

---

### Post by LHammonds on 2020-07-14
> **TheFu said:**
> I completely agree that proxmox is probably the best answer for your initial VM needs.Yes, for a Linux-newbie, it is an AWESOME introduction to virtualization.  And even though I cannot claim the role of newbie on Linux anymore, I will say that I tried to setup KVM but found it a bit painful and time-consuming compared to vmware ESXi and Nutanix Acropolis...which is why I looked for other better-integrated options and found Proxmox which is very similar to the Nutanix interface which is KVM-based too...but like vmware ESXi, it costs a pretty penny.

LHammonds

---

### Post by TheFu on 2020-07-14
> **LHammonds said:**
> Yes, for a Linux-newbie, it is an AWESOME introduction to virtualization.  And even though I cannot claim the role of newbie on Linux anymore, I will say that I tried to setup KVM but found it a bit painful and time-consuming compared to vmware ESXi and Nutanix Acropolis...which is why I looked for other better-integrated options and found Proxmox which is very similar to the Nutanix interface which is KVM-based too...but like vmware ESXi, it costs a pretty penny.

LHammonds

KVM doesn't mandate taking over the entire machine, unlike ESXi and Proxmox.  But with flexibility comes complexity.  A basic KVM setup using virt-manager really only needs a few non-KVM things setup.
[LIST]
[*]Linux bridge
[*]Storage Backend(s)
[/LIST]

Manually setup Linux bridges ensure the network performance isn't poor. I don't know if this is an issue any longer, but only a NAT virtual-interface is setup by default.

Storage backends are many and extremely flexible.  I use a mix, depending on the VM purpose.  Most of the time, I'll use an LV.  Virt-manager will "do the right thing" from allocating from a VG pool.  The VM is presented with a block storage device that's very fast.  The hostOS can create a snapshot of the storage which can be used to make a backup - I think that's what proxmox does too.

I don't know how clustered/replicated storage is handled for proxmox.

But KVM supports many backend storage solutions like ceph and sheepdog for when we need near real-time block replication to N+1 storage devices.  openstack supports ceph too, but openstack doesn't make sense for fewer than about 20 physical servers.

---

