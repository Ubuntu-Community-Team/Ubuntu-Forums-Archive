---
title: "To Virtualize or not Virtualize. That is the question!"
date: 2011-10-18
forum: Server Platforms
---

### Post by collisionystm on 2011-10-18
First, I see that** Virtualize** is not even a real word? It fails my spell check. Lovely.

Now on to the question!

I have a 32 bit 2003 Terminal server with 30 CAL. Being 32bit it can only support up to 4gb of ram. It has had a rough life  and needs a revival. It started on a Poweredge 2600, then converted with disk2vhd and ported to Virtualbox on an Ubuntu host, and now it has been ported over to Vmware. Whew. 

Now-a-days Server 2003 is lagging when users are in ACT! and HandHeldContact is running. The CPU will sit at 100% inside of Windows with SQLServer taking up all the ram.

Rather than waste my time fixing a box that needs updating anways, I decided to embark upon the task of creating a new one. I have a Poweredge R310 with 12GB of ram and RAID1 of 500gb. Plenty of room. But then I have my Vmware Server with Plenty of ram, 2 Xeon CPU's and a Raid 10 redundancy.

I think I should NOT virtualize it because it is a terminal server and it will suck down so many resources, but having it virtualized has proved to be a real blessing because I can just shut it off, clone the VM to make a backup and move the Cloned VM to another machine for backup or new home.

My question.. What would those in this community do??

And what do you think of Ubuntu Hypervisor, MS Hyper-V and Vmware ESXi? I am pretty sure Ubuntu Hypervisor is really only intended by canonical to run other Ubuntu Servers.

---

### Post by collisionystm on 2011-10-19
No one?

---

### Post by rubylaser on 2011-10-19
Personally, I either use [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") or ESXi.  I personally wouldn't hesitate to virtualize this.  Although, it would be nice for your machine to have more RAM and really more hard drives, so you could get higher IOPS.  I imagine that the disks are the real bottleneck in your scenario.

---

### Post by collisionystm on 2011-10-19
> **rubylaser said:**
> Personally, I either use [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") or ESXi.  I personally wouldn't hesitate to virtualize this.  Although, it would be nice for your machine to have more RAM and really more hard drives, so you could get higher IOPS.  I imagine that the disks are the real bottleneck in your scenario.

From what I have been reading, ProxMox and similar solutions are meant for servers that do not require a GUI. But this is a terminal server.

The machine I am considering putting it on ( no virtualization ) has 12gb currently and the ability to move to 16gb.
I have another server that I need to get more memory for. It will be my future VMWARE box. It is an R900 that can handle up to 192 gb of ram I think. It has a Raid 10 across 2tb drives giving me 4tb of useable drive space. The other vmware server has the same drives, just less memory.

---

### Post by CharlesA on 2011-10-19
The Terminal server we have at work is virtualized on a dell PowerEdge (something or another). It's been running fine so far. Running in Hyper-V.

The host is a dual quad core from what I understand, with 16GB of RAM - that VM has four cores and 8GB of RAM dedicated to it.

Running it on a physical box might be better if it does get a lot of load, since it won't slow down the host if it's run as a VM.

---

### Post by collisionystm on 2011-10-19
> **CharlesA said:**
> The Terminal server we have at work is virtualized on a dell PowerEdge (something or another). It's been running fine so far. Running in Hyper-V.

The host is a dual quad core from what I understand, with 16GB of RAM - that VM has four cores and 8GB of RAM dedicated to it.

Running it on a physical box might be better if it does get a lot of load, since it won't slow down the host if it's run as a VM.

Yeah I am thinking the physical box is the best bet. 

I would love to virtualize this thing, but it is a resource hog. 

BTW, how is Hyper-V ? I was curious to try it. I have Server 2008 R2 and from what I understand Hyper-V is just a simple install to it.

---

### Post by CharlesA on 2011-10-19
> **collisionystm said:**
> Yeah I am thinking the physical box is the best bet. 

I would love to virtualize this thing, but it is a resource hog. 

BTW, how is Hyper-V ? I was curious to try it. I have Server 2008 R2 and from what I understand Hyper-V is just a simple install to it.

I haven't really messed with it since that's not my job, but from what I can remember, you add it as a role and it "just works"

We haven't had any problems with it and the interface is quite nice too.

---

### Post by collisionystm on 2011-10-19
> **CharlesA said:**
> I haven't really messed with it since that's not my job, but from what I can remember, you add it as a role and it "just works"

We haven't had any problems with it and the interface is quite nice too.


Gotcha.

Well so far I am having bad luck install 2003 R2 Sp2 with a PERC 6/i. I had to integrate drivers into the cd for it to recognize the raid controller and It finished install and gave me an immediate blue screen! Lovely.

I just loaded 2008 R2 with SP1 and it recognized everything. Installing now...

Hopefully I can migrate my CAL's from 2003 to 2008. 

If not, I will look at another solution

---

### Post by CharlesA on 2011-10-19
Oh that's not fun. I wonder what the difference between SP1 and SP2 were that would have caused that.

Hopefully you'll be able to migrate the CALs over.

---

### Post by rubylaser on 2011-10-19
Proxmox doesn't have a GUI for the Host just a web interface to perform all of your vm administration tasks.  You'd setup a KVM Windows 2008 virtual machine and enable terminal services on the virtual machine.  If you're host is highly loaded though, a physical box isn't a bad idea.

---

### Post by TheR on 2011-10-21
> **collisionystm said:**
> 

And what do you think of Ubuntu Hypervisor, MS Hyper-V and Vmware ESXi? I am pretty sure Ubuntu Hypervisor is really only intended by canonical to run other Ubuntu Servers.

There is no Ubuntu hipervisor. Ubuntu uses KVM as hipervisor and it works just fine with virtual windows hosts.

UI might not be polished as other hypervisors, but if you don't have to control remote servers anything can be done local with Virt-Manager. 

And even remote control has only problems assigning remote resources to VM. Everything else can be controlled as expected.


by
TheR

---

### Post by collisionystm on 2011-10-22
I ended up just building my Server on a physical box.

Server 2008 R2
Dell R900
4 X 2TB Raid 10
1 X 2TB Hot Swap backup drive.
2 X 3.0 Ghz Xeon Quad Core
16 gb of Ram
Redundant power supplies

It as originally going to be on an R310 with a single Xeon, 16gb of ram and raid 1 500gb, but I had so many problems with it I just said screw it and went with the R900 I have. Best server I have ever had.

---

### Post by Vegan on 2011-10-22
I use Hyper-V in my shop and I had no insurmountable problems

I have a couple of distros in VMs so if some coding is needed I can see what is up

---

### Post by CharlesA on 2011-10-23
> **collisionystm said:**
> I ended up just building my Server on a physical box.

Server 2008 R2
Dell R900
4 X 2TB Raid 10
1 X 2TB Hot Swap backup drive.
2 X 3.0 Ghz Xeon Quad Core
16 gb of Ram
Redundant power supplies

It as originally going to be on an R310 with a single Xeon, 16gb of ram and raid 1 500gb, but I had so many problems with it I just said screw it and went with the R900 I have. Best server I have ever had.
Nice rig there. Glad you were able to get everything up and running. :)

---

### Post by collisionystm on 2011-10-23
> **CharlesA said:**
> Nice rig there. Glad you were able to get everything up and running. :)

Thanks! Me too. I guess we will see how it handles! I think it has enough power to last me quite a while.

---

### Post by CharlesA on 2011-10-23
> **collisionystm said:**
> Thanks! Me too. I guess we will see how it handles! I think it has enough power to last me quite a while.
No kidding. Twin quad cores with a load of RAM should handle it well.

---

### Post by collisionystm on 2011-10-23
> **CharlesA said:**
> No kidding. Twin quad cores with a load of RAM should handle it well.

Yeah I think it can support up to 192gb of ram lol. Its a shame its only DDR2 compatible...

---

### Post by CharlesA on 2011-10-23
> **collisionystm said:**
> Yeah I think it can support up to 192gb of ram lol. Its a shame its only DDR2 compatible...
Fail! I hope it uses ECC RAM. ;)

---

### Post by Vegan on 2011-10-23
I find that unless a server is running long cycle compute tasks that the extra cost of ECC memory is not worth it.

Better is to simple run a solid series of tests with something like memtest to be sure the chips are all good

---

### Post by CharlesA on 2011-10-23
> **Vegan said:**
> I find that unless a server is running long cycle compute tasks that the extra cost of ECC memory is not worth it.

Better is to simple run a solid series of tests with something like memtest to be sure the chips are all good
I've only used non ECC memory, but I don't have a true "server."

---

### Post by collisionystm on 2011-10-26
I don't have ecc memory

Oh and that R310 that kept failing...apparently the PERC 6/I is not compatible and that's why windows would constantly crash. The funny thing is it wont run CentOs or Fedora either. It gets stuck at udev. However Ubuntu and Esxi run perfect haha. Gotta love it.

---

### Post by CharlesA on 2011-10-26
> **collisionystm said:**
> I don't have ecc memory

Oh and that R310 that kept failing...apparently the PERC 6/I is not compatible and that's why windows would constantly crash. The funny thing is it wont run CentOs or Fedora either. It gets stuck at udev. However Ubuntu and Esxi run perfect haha. Gotta love it.

That's so funny how that works. PERC cards are apparently very touchy. :P

---

### Post by collisionystm on 2011-10-26
> **CharlesA said:**
> That's so funny how that works. PERC cards are apparently very touchy. :P

So I am learning... lol.

Oh well, next up in line is a PERC H200! Let's see if we have better luck with that!

---

### Post by CharlesA on 2011-10-26
> **collisionystm said:**
> So I am learning... lol.

Oh well, next up in line is a PERC H200! Let's see if we have better luck with that!
Good luck!

---

