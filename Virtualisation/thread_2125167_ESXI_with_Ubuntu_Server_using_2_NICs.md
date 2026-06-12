---
title: "ESXI with Ubuntu Server using 2 NICs"
date: 2013-03-13
forum: Virtualisation
---

### Post by chrisguk on 2013-03-13
Hi,

I decided to dive into the virtualisation world and install ESXI on my physical server.  My Specs are as follows:

2 x Intel Quad Core CPUs
32 GB RAM
4 TB storage available
2 x NICs

I setup the VM in the vsphere client and selected the VM to have 2 NICs because I want the Virtual server to be a DNS/DHCP and gateway to the network (internet facing).  So I installed Ubuntu Server and I found that it only shows 1 NIC and not the two I selected in the VM setup.  Does anyone have any experience with this?

---

### Post by chrisguk on 2013-03-13
bump.... anyone?

---

### Post by TheFu on 2013-03-14
Which virtual NICs is ESXi presenting to the clientOS? Are they supported? Are they enabled?

This seems more like a question for the VMware/ESXi support forums.

BTW, we dumped ESXi for KVM and have never felt better. Performance is similar and some huge companies are actively working to make KVM better every day.  Because KVM runs on a complete OS, we can do more things than we could ever do under ESXi, plus all the software is cost free. The license costs are better too ($Free). In a few more years, only the fortune 100 companies and tiny Mom-n-Pop companies will still be using VMware ESX/i.  People with an IT department running Linux will switch to KVM when the next annual bill from VMware arrives.

OTOH, if you are trying to learn this to increase your job and earning, then ESXi is a good choice still. Companies paying $10k+ for ESXi licenses per server can probably afford to pay you as well.

What do the log files on the clientOS and ESXi show?

Did you setup the 2nd NIC in /etc/network/interfaces?
Is the driver loaded?

---

### Post by chrisguk on 2013-03-15
Hi,

Thanks for your lengthy reply.

There was no issue with drivers etc it was purely my lack of understanding the relationship between virtual topology and physical.  Because the metal box has two NICs I was able to have one NIC as internist facing and named WAN and the other NIC LAN facing and named LAN for a private internal network.  I have the virtual cables setup perfect now and currently have 5 Linux based servers running.  I plan on installing Windows Server today at some point if I can find the time.

I have looked into this KVM and of course I understand that it is a kernel based installation that sits on top of and already installed OS.  I can see only one flaw with this and it is this flaw that is keeping me with ESXI.

With ESXI you can install the OS onto a flash drive therefore keeping the physical disk available for the VMs and other related storage.  It is very easy to use and virtually no command line.  Of course the higher end of the package costs money but they do provide a free version with a lifetime license which is more than enough if you only have 5 to 10 servers so there is no need to deploy a data centre using venter for example.

Even with all this I am not going to walk around with my eyes closed, so I will learn more about KVM to see if its a viable option in the future.  I know you can migrate the VMs so at least I don't need to worry about that.

---

### Post by TheFu on 2013-03-15
> **chrisguk said:**
> There was no issue with drivers etc it was purely my lack of understanding the relationship between virtual topology and physical.  Because the metal box has two NICs I was able to have one NIC as internist facing and named WAN and the other NIC LAN facing and named LAN for a private internal network.  I have the virtual cables setup perfect now and currently have 5 Linux based servers running.  I plan on installing Windows Server today at some point if I can find the time.

I have looked into this KVM and of course I understand that it is a kernel based installation that sits on top of and already installed OS.  I can see only one flaw with this and it is this flaw that is keeping me with ESXI.

With ESXI you can install the OS onto a flash drive therefore keeping the physical disk available for the VMs and other related storage.  It is very easy to use and virtually no command line.  Of course the higher end of the package costs money but they do provide a free version with a lifetime license which is more than enough if you only have 5 to 10 servers so there is no need to deploy a data centre using venter for example.

Even with all this I am not going to walk around with my eyes closed, so I will learn more about KVM to see if its a viable option in the future.  I know you can migrate the VMs so at least I don't need to worry about that.

We've all been there with the virtual/physical networking. Sometimes I have to draw a picture to straighten out even some fairly simple virtual connections.

<rant on>
The ESXi license that I read said we **could not use it in production without paying a full license** fee.  Plus there is required use of Windows to manage it - uuuug, so that "free" lab license requires a $120 Microsoft license too.  The free ESXi is only for evaluation and lab use.  I remember 2 yrs ago when VMware corporate screwed around with all the licensing costs. That is why my company dropped VMware as quickly as we could. After an uproar, they changed to licensing to be more like what they had prior, but it still sucked and the VMware using community had learned what sort of a "corporate machine" we were buying from.

You are correct that KVM will use more storage for the OS, but that doesn't mean you can't install it on a CF and boot from that or use a 5G SSD for the KVM-OS and all the SAS disks for VMs or boot it from a network repo and use a 5G RAM disk for the OS+KVM hypervisor.  Options.  It is nice to have full control over the VM host AND to be able to add other programs to enhance management.  Why not use Puppet (or Chef or Salt or Rex) to manage your KVM hosts AND all your clientOSes?  Patching non-running VM and VM images concurrently from the hostOS is nice too. Those are just a few examples.  Flexibility to do what you want without waiting for some commercial provider is nice.

Having a shell is nice.  Lacking a shell interface for everything is a negative in my book. No need to use a "command line" to manage KVM VMs, if you don't like that, use  virt-manager (or any of the 5+ other VM management tools).  

Choice and flexibility.  With scripts, I can manage 5, 10, 100, 1000 systems with about the same level of effort.  Using point-n-click would make that impossible.

Serious VM setups will have the storage on a SAN to support live VM migrations between different physical hosts.  A SAN provides all sorts of flexibility.  iSCSI or AoE are great for cheap SAN storage if you can't afford a NetAPP or EMC frame. 
<rant off>

Regardless, I'm happy that you were able to solve the base technical issue.

---

