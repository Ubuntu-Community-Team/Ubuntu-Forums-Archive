---
title: "Multiple Virtual Machines within one Ubuntu Server"
date: 2020-05-06
forum: Server Platforms
---

### Post by divgup1986 on 2020-05-06
Hi,

I have never use Linux, ubuntu or ubuntu server before, so kindly ignore if i misinterpret any usual ubuntu keywords.

I am looking for a way to provide multiple virtual instances of a server to users for purpose of learning.

The sole purpose is , so that a user doesn't have to configure or download any other tools on the instance.
For example a engineer might be looking to work on arduino, whereas some other person might be looking to work on Java projects or IOT.

We wish to provide pre-built mix of apps to the user over cloud.
Do let me know , if its possible through Ubuntu or any other platform.



Thanks and Regards,

---

### Post by deadflowr on 2020-05-06
Multipass is probably something you'd want:
[https://multipass.run/]("https://multipass.run/")

---

### Post by TheFu on 2020-05-06
This is extremely common and has been possible for about 15 yrs on almost any Linux host using Xen or KVM+QEMU.  x86 will use the hardware the best, but QEMU can emulate lots and lots of other CPUs.

Most cloudy providers would support only x86/amd64 CPUs, but you can setup whatever you want on HW you own.
Have zero idea whether an arduino would be supported or not. That's pretty specific.
[https://www.qemu.org/](https://www.qemu.org/) is software so it will be slower than a HW-based solution like KVM.
[https://virt-manager.org/](https://virt-manager.org/) is what i use to manage 20 or so VMs at home.  Some currently running:
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 7     spam3                          running
 8     zcs45-16.04                    running
 9     blog44-1604                    running
 10    xen41-1604                     running
 25    regulus                        running
```

2 are for email stuff.
2 are for websites.
1 is for a 20.04 desktop.  There are many others, just not currently running until some more RAM arrives.

---

### Post by LHammonds on 2020-05-06
No experience in Linux administration?  Well, you will want a solution that is as simple as possible but you are wanting something that requires some knowledge in various aspects of computer science (networking, virtualization, server management, etc.)

You "can" install Ubuntu and throw on KVM+QEMU but you are going to have to jump through quite a few hoops before you can even get your 1st VM running and you won't have a front-end that is easily used by non-admins for rolling out pre-configured template servers.

I started to look into raw KVM management but decided I needed a better / easier front-end experience for other admins / managers / helpdesk people so I looked at [this page](https://www.linux-kvm.org/page/Management_Tools) to see what is out there.

I ended up choosing Proxmox and I am currently setting up and environment right now and documenting the process as I go (many revisions will occur before I'm done).

I come from a large vmware / esxi shop and we started to switch over to Nutanix but I was curious about a less expensive solution and Nutanix was built on KVM...thus my research into the core components to see what I could do with various hardware / configurations for home, small business and the enterprise.

If interested in following what I am doing, I am posting it on [my site](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=276) but I'm in the VERY early stages of research.

LHammonds

---

### Post by aljames2 on 2020-05-06
I've wondered about the OP topic from the standpoint of host machine hardware.  VMs can be taxing on hardware.  Is it better to use a cluster of machines to host VMs vs. having say one 16 core ryzen system with a bunch of RAM?  I'm thinking so...if one in the cluster goes down you don't lose everything?

---

### Post by LHammonds on 2020-05-06
> **aljames2 said:**
> I've wondered about the OP topic from the standpoint of host machine hardware.  VMs can be taxing on hardware.  Is it better to use a cluster of machines to host VMs vs. having say one 16 core ryzen system with a bunch of RAM?  I'm thinking so...if one in the cluster goes down you don't lose everything?Completely depends on what you are running.  Most typical single-OS servers sit mostly idle.  Turning the physical box into a hypervisor to allow more operating systems to be running at the same time allows for better utilization of the hardware.  When running multiple VMs on a single host, you have to monitor the RAM, CPU, HD and NIC usage and make sure nothing is being taxed too heavily.  You might be able to run 20 web servers on a single host but the NIC might not be able to handle the bandwidth.  But the most typical resource that is taxed is RAM and occasionally CPU depending on what you are running.

Having multiple hosts will of course help alleviate CPU/RAM/NIC constraints but you will typically want some kind of NAS when you have multiple hosts and that can get expensive quick the more you need and better redundancy, local and offsite backups.

I had some more thoughts but alas, they left me.  Time for bed. LoL

LHammonds

---

### Post by TheFu on 2020-05-06
> **aljames2 said:**
> I've wondered about the OP topic from the standpoint of host machine hardware.  VMs can be taxing on hardware.  Is it better to use a cluster of machines to host VMs vs. having say one 16 core ryzen system with a bunch of RAM?  I'm thinking so...if one in the cluster goes down you don't lose everything?

"Better" is highly subjective.  in business, we would analyze what the downtime costs are per hour and decide whether any redundancy was needed, HA was required, and what the cost to the business - lost revenue, cost of idle workers, etc. would be included.  if a failover system costs $25M to stand up and the cost of an hour of downtime is $10M to the company, it doesn't take much brains to realize that HA is needed in locations far enough apart to handle region-wide issues.  in the end, that system got near real-time data replication 4 states away where transactions where usually 3 seconds behind, but not guaranteed.  During busy periods, transaction could queue and be 90 seconds behind.  This was NOT a financial system.

At home, "better" is dependent on costs first with other considerations as lower priority.  i've run 20 VMs on a 1st-gen Core 2 Duo desktop. Most of the time, that system was under 30% utilized.  Today, those systems have been migrated twice and sit on a 65W Ryzen 2600.  Most aren't needed all the time, so only 7 services are running now. Not all run inside VMs. Some are inside LXD containers which have a tiny footprint compared to a VM.  i've been running VMs are home (and work) for decades.  Since around 2008, all the linux-based VMs have been extremely solid.  They don't fail or crash.  if you have a linux box that crashes, then you've done something wrong.  The only times my Linux systems come down are when i bring them down for maintenance or some non-redundant hardware fails. About 10 days ago a UPS failed with no warning.  That brought down a non-critical system (backup server and Win VM for accounting stuff running in a VM).
Right now, only 1 of my systems doesn't have automatic, daily, backups working.  2 are on RAiD1 storage but the rest are not on any RAiD the last 16 months.  i moved them to an nice SSD, but not enterprise level.

The old school way to handle redundancy is with RAiD storage, but that likely has single points of failure unless you spend $3000 on the HW. 
OR
we can build 2 $500 nice desktops, run storage replication using sheepdog or ZFS and have truly redundant systems for less than 50% the cost.  We'll end up with very capable systems that are cooler, use less power, and are much quieter.  But when we do this, we need to be adults about over extending workloads beyond what a single system can handle.  People who cannot setup sufficient backup storage probably shouldn't be trusted with 2 systems that need to run at less than 40% utilization peak, unless one of them fails and the entire workload has to run on 1 box.

imho.

---

### Post by 1clue on 2020-05-07
> **divgup1986 said:**
> Hi,

I have never use Linux, ubuntu or ubuntu server before, so kindly ignore if i misinterpret any usual ubuntu keywords.

I am looking for a way to provide multiple virtual instances of a server to users for purpose of learning.

The sole purpose is , so that a user doesn't have to configure or download any other tools on the instance.
For example a engineer might be looking to work on arduino, whereas some other person might be looking to work on Java projects or IOT.

We wish to provide pre-built mix of apps to the user over cloud.
Do let me know , if its possible through Ubuntu or any other platform.



Thanks and Regards,

This thread has gotten very complicated, and unnecessarily so. Everything you mentioned is very feasible and widely supported. There is an arduino simulator and certainly Java/IoT is widely supported too. All this is possible on pretty much any computing platform based on x86, x86_64 and to a lesser degree on other platforms. Meaning you may have to jump through more hoops to get it working elsewhere.

Virtualization is possible on almost any computing device. If the device has hardware support for virtualization it's much easier and lower load on the CPU. If the virtual hardware is the same as the host hardware -- especially when the host hardware has virtualization support -- then there is almost no difference in execution speed inside a VM or without a VM present.

Virtualization can happen on a Raspberry Pi, and it is widely used in almost every large business with a cluster of very big computers. You can use it on your laptop or desktop, or even your phone for limited use.

You can start out by making VMs on your personal hardware, and then when you get one or more that you want to share the way you described, you can rent/buy server hardware in a datacenter and make them available to others. There are a LOT of frameworks for this.

If your mind is boggled already then maybe you should stop reading here. I just commented that the thread is too complicated, and this is going to make it worse. It's not my intent to complicate, but in the interest of completeness I want to mention kubernetes.

There are several types of virtualization:
[LIST=1]
[*]A hypervisor is a minimal operating system with just enough tools to create and manage VMs.
[LIST=1]
[*]VMware ESXi is one of these.\
[*]Xen (now Citrix) is a hypervisor which requires a VM with management software. I don't have much experience with this one. 
[*]KVM is also in this category as its support is in the kernel, but many Linux admins make a "thick" hypervisor which means they have a much more functional OS as the host, possibly a complete install. 
[*]Hypervisors are designed to run on the bare metal and run VMs continuously.\ 
[*]If you use a server farm to host lots of VMs, possibly rented to third parties, this is your best approach for conventional VMs. 
[*]This approach is widely assisted by hardware designed for virtualization. 
[*]You can get almost complete isolation of the virtual environment from the host and other VMs. You can also "share" resources between the host and guests or between guests. Each level of sharing exposes the collaborators more, so care should be taken. 
[*]Your host can run any mainstream OS, including Linux, Windows, Mac OS X, FreeBSD or whatever, and your guests can be pretty much anything including Arduino. 
[/LIST]
  
[*]A user-space VM host, like the most common mode for VirtualBox, is an app that you run as a user which can run virtual machines.
[LIST=1]
[*]If you use VMs only occasionally then you will probably like this approach. 
[*]This approach can have similar isolation characteristics with hypervisors, meaning pretty much complete isolation or levels of sharing as above. 
[*]Again your host can run almost any mainstream OS and your guests can run pretty much anything. 
[/LIST]
  
[*]Kubernetes is a namespace oriented virtualization scheme.
[LIST=1]
[*]Unlike the top two items, namespaces does not completely emulate a piece of hardware. Instead it uses the host kernel and then operates its own stack of libraries and software. 
[*]Linux can have namespaces that run Linux, and Windows can have namespaces that run Windows. And so on. 
[*]This approach is newer and already widely used but possibly less tested? 
[*]You do NOT achieve complete isolation this way. 
[*]Rather than focusing on a virtual computer, you are designing a service in a container. 
[*]The benefit is that each image is much lighter than a VM would be, allowing many more guest apps on the same hardware compared with traditional VMs. 
[*]I don't think you can emulate alien hardware with this, so your Arduino requirement is probably not going to work here. 
[*]The learning curve on this one is much steeper than for regular VMs, but this is already hosting a lot of commercial sites. 
[/LIST]
  
[/LIST]

---

### Post by TheFu on 2020-05-07
Kubernetes is most definitely an advanced topic, but also widely deployed inside enterprises.  The only people at home using Kubernetes are those people trying to up their skills for professional reasons. It is not a casual answer for emulation.

Agree with the rest, but most of the popular virtualization tools are for amd64 or x86 virtualization.  To get support for other CPUs, emulation is required. That is almost always built using qemu. It has been a few years, but I remember qemu being pretty simple.  
**sudo apt install aqemu**
will load the dependencies and a little GUI with a wizard to get started. Some CPU emulators it install are: PPC, Sparc, x86, ARM, MIPS. What does the beagle board or arduino use? Looks like there are ARM-based arduinos, but also some other 8-bit CPUs.

---

### Post by 1clue on 2020-05-09
@TheFu,

To run a VM of a system not using the native format, it must use emulation.  An ARM host can emulate an ARM guest in native mode, but can't emulate any other platform in native mode.

I see confusion sometimes because not everyone runs Intel on the host. 

That's nit-picking, not trying to derail anything.


WRT kubernetes being an advanced topic, though. Certainly now it is, but I don't think it should have to be. The tool set is still mostly command line edit-a-file type stuff, but if there were good documentation it would all be a lot easier. Some of the features are just plain not documented, and you have to read the source code to figure out what to do.

The elegance of k8s is that you don't just define a VM and start installing stuff on it. You define what the VM should start from (parent image) and then define what steps must be taken to get the image you want (upgrade script more or less) and pretty much everything about it. So your VM is literally irrelevant. You define a set of services necessary to perform a specific task, on several VMs, and then tell the service controller how many of each thing you want or better yet, when to put another of something online or take one offline.

k8s is a recipe for a collection of desired services and the "wiring" necessary to make it go.

---

