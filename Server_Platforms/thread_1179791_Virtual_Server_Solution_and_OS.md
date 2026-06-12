---
title: "Virtual Server Solution and OS"
date: 2009-06-06
forum: Server Platforms
---

### Post by victorbrca on 2009-06-06
Greetings!

I will be implementing a virtual sever solution at work and I'm trying to get as many facts as possible for the best setup. 

We want to setup a server at our support department to host a minimum of 8x Windows machines running simultaneously (ranging from XP up, including server, 32 and 64-bit). Some of these machines might run MSSQL which will increase the overhead, however they will be used for testing and bug replication only, so there is no need for them to be lightning fast. 

The department could grow and the number of virtual machines might increase in the future (let's say 3x additional machines).

There's also a need for backup, user management and remote management. Costs need to be kept as low as possible, while still providing a good and acceptable performance. Also, the company does not have a formal Linux guy, so they might need to outsource support if I ever leave the company.

I've been doing some research on the following OS's and Virtual Server solutions, including cost, support, usability and other aspects:


=> OS
-CentOS
-Ubuntu
-Suse
-Open Suse
-Open Solaris

=> Virtual Severs
-Vmware Server
-Vmware ESXi
-VirtualBox
-Xen
-KVM


My choices are going for VMware ESXi and either CentOS or OpenSuse (even thou I'm an Ubuntu guy). 

Any ideas and/or comments are very welcome!


Vic.

---

### Post by iponeverything on 2009-06-06
NILFS seems like it would be good filesystem for the project. Take a look at this linux-mag article. I have been looking for a project where I can use it, but have not come across one yet.

 [http://www.linux-mag.com/cache/7345/1.html](http://www.linux-mag.com/cache/7345/1.html)

---

### Post by windependence on 2009-06-07
Vic, with ESXi, you do not need an OS. You load ESXi on the machine, and then load your guests on top of that. It runs on the bare metal and is extremely efficient and robust. You will have to be careful with hardware selection, but if you are using common server stuff like HP, Dell, IBM, etc, you have a good chance of getting goo results. ESXi also has a nice GUI for configuration. It's a very mature product. There is nothing wrong with the others but my recommendation would be ESXi.

Whatever you decide to use, you will need gobs of memory to do all 8 on one machine. I would recommend at least 16 GB of RAM for that.

-Tim

VMware Partner

---

### Post by victorbrca on 2009-06-07
> **windependence said:**
> Vic, with ESXi, you do not need an OS. You load ESXi on the machine, and then load your guests on top of that. It runs on the bare metal and is extremely efficient and robust. You will have to be careful with hardware selection, but if you are using common server stuff like HP, Dell, IBM, etc, you have a good chance of getting goo results. ESXi also has a nice GUI for configuration. It's a very mature product. There is nothing wrong with the others but my recommendation would be ESXi.

Whatever you decide to use, you will need gobs of memory to do all 8 on one machine. I would recommend at least 16 GB of RAM for that.

-Tim

VMware Partner

Hey Tim,

Thanks for the reply. I'm aware that ESXi is a bare-metal solution, but I thought I'd include which OS I was leaning to in case I do decide for another Virtual Solution other than ESXi.

Right now it seems to be the most mature of the options, and my preferred one. But I wanted to keep an open mind for the other apps until I had all the pros and cons of each of them.

Vic.

---

### Post by windependence on 2009-06-07
I can give you a quick run down of my opinions. I am a consultant and I can choose any solution unless the client wants something else.

KVM looks promising, but last I looked, it only supported processors with the VT technology built in so that eliminated many of my current customer's machines. 

Xen was looking good when it was the Red Hat default VM solution, but then Citrix bought them and now it seems the open source version is not getting the attention it once had.

Virtual Box is good and stable, but setup can be a bear as far as networking and some other things go. Also, now that Sun we probably be eaten by Oracle, who knows what will happen.

Since EMC (a storage company) owns VMware, I feel pretty safe even of their paid stuff is pricey. All that tells me is people are willing to pay the price because it works. I have been runnning production on VMware stuff since 2006 and I have had little, if any problems. With ESXi, the tricky part is getting storage that will work with it if you want to use local storage. If you have a SAN, it can use an NFS or iSCSI share without any problems.

HTH,

-Tim

---

### Post by scottro on 2009-06-07
We tried VMware server on a CentOS host, with Linux guests.  It didn't seem adequate.  We wound up going with ESX (not ESXi) as it was still a cost savings of several thousand dollars over giving each host its own machine.  


I don't know how VBox would perform in such a situation either.  KMV *might* be a possibility--I haven't used it in awhile, and never on the type of server that we'd use to run 8 VMs simultaneously.  

I don't know that any of them, save perhaps for ESXi, are designed for large scale (and 8 machines is rather large scale)  :) production use.  ("them" refers to the choices that you mention.)

I know that RH is apparently choosing KVM over Xen now, but I'm not sure if it intends it to be used for large scale production use on the scale that you mention.

[http://www.workswithu.com/2009/04/27/kvm-vs-vmware-a-case-study/](http://www.workswithu.com/2009/04/27/kvm-vs-vmware-a-case-study/)

seems to contradict what I've said though, and we didn't try KVM.

---

### Post by windependence on 2009-06-07
> **scottro said:**
> We tried VMware server on a CentOS host, with Linux guests.  It didn't seem adequate.  We wound up going with ESX (not ESXi) as it was still a cost savings of several thousand dollars over giving each host its own machine.  


I don't know how VBox would perform in such a situation either.  KMV *might* be a possibility--I haven't used it in awhile, and never on the type of server that we'd use to run 8 VMs simultaneously.  

I don't know that any of them, save perhaps for ESXi, are designed for large scale (and 8 machines is rather large scale)  :) production use.  ("them" refers to the choices that you mention.)

I know that RH is apparently choosing KVM over Xen now, but I'm not sure if it intends it to be used for large scale production use on the scale that you mention.

[http://www.workswithu.com/2009/04/27/kvm-vs-vmware-a-case-study/](http://www.workswithu.com/2009/04/27/kvm-vs-vmware-a-case-study/)

seems to contradict what I've said though, and we didn't try KVM.

Yep, ESX is even better if you can afford it. If you are consolidating, it's worth the price. Very nice, stable product. ESXi was not free until Micro$oft made their hypervisor free. It's kind of a "cut down" version of ESX without all the central management stuff.  It also has about a 32 MB footprint which is great. We have some running off CF cards.

-Tim

---

### Post by garretwp on 2009-07-20
This thread is over a month old, but I wanted to chime in. Check out Proxmox. It is an open source baremetal type VM. It uses kvm and has web management and other sort of nice features. I have not used it, but it is worth a look. I will probably look into using it later on down the road to move my VM's off of my main box.

- Garrett

---

### Post by senor_smile on 2009-07-21
The other great thing about proxmox is that it can use OPENVZ or KVM.  With openvz, it "always runs the same OS kernel as the host system (while still allowing multiple Linux distributions in individual containers). "  For Windows clients, KVM is still available.  I haven't tried it out yet, but intend to soon.

---

### Post by dragos2 on 2009-07-21
I would recommend you around 20 GB RAM, some sort of raid except 0, and 2 CPUs'
preferably quad core at high frequency (2 x Quad Xeon at 3.3 GHz )if you want to
make it tick well :)

Many people recommends the ESXi.

---

### Post by PilotJLR on 2009-07-21
Two great choices:
1. ESXi (free)
2. Citrix XenServer (free)

XenServer includes centralized management and live migration for free. It's pretty sweet. I don't know why it doesn't get more attention.

---

### Post by dragos2 on 2009-07-22
> **PilotJLR said:**
> Two great choices:
1. ESXi (free)
2. Citrix XenServer (free)

XenServer includes centralized management and live migration for free. It's pretty sweet. I don't know why it doesn't get more attention.

Let me understand please.


Xen.org is now different from the XenServer offered by Citrix ?

---

### Post by PilotJLR on 2009-07-22
Citrix bought XenSource, which is the company that developed Xen. Xen itself is still open source.

What Citrix did is enhance the PV drivers quite a bit and add centralized management and live migration. Sure, you can do live migration with Xen on any distro, but with Citrix is drag-and-drop. Like most companies, the goal is to get the features usable by any windows sysadmin.

I'm oversimplying, though... both XenServer (free) and XenServer Essentials (not free) add a lot of functionality the Xen hypervisor itself does not have.

---

### Post by JedMeister on 2009-08-09
> **garretwp said:**
> This thread is over a month old, but I wanted to chime in. Check out Proxmox. It is an open source baremetal type VM. It uses kvm and has web management and other sort of nice features. I have not used it, but it is worth a look. I will probably look into using it later on down the road to move my VM's off of my main box.

- Garrett

Thanks for your suggestion Garrett. Proxmox looks awesome - just what I was looking for! I have just installed it and it was easy. The web interface looks good. Now just going to migrate some stuff to it and set up a few more vms for testing.

---

