---
title: "Thin Client Server, with Windows VMs"
date: 2008-08-07
forum: Server Platforms
---

### Post by aaaantoine on 2008-08-07
Because I work remotely from company headquarters -- scratch that -- because the entire IT team works remotely from company headquarters, it is very difficult to administrate the network.  I am trying to develop a solution to this issue that will allow us to configure a user's system quickly and without having to come into the office.

The idea I've come up with is to use thin clients.  We have about 20 people on site, usually working either with web applications or with Microsoft Office.  Nothing processor intensive, mainly customer service.

I've never done anything like this before, so I need to know what below is a pipe dream and what is possible.

We can set up a single server that handles these 20 people at once.  The server itself can probably get away with just 16-32 GB of RAM (512MB-1GB per user) and 500GB storage over RAID 5 (probably 24GB per user after overhead).  The plan is to test it with maybe one or two thin clients, and then expand from there.

The thing I want to know is this.  Is it possible to have the thin client boot off the server, maybe require a log in, and then load a Windows Virtual Machine on the server?

Why Windows VM?  Because I think it would be enough of a shock for the people there to go from fat clients to thin clients.  Plus, it would allow me to just wipe the image and replace it with a fresh one if someone breaks something.

Why not a Windows Host OS?  Well, I dunno.  I guess I somehow get the feeling it would be easier to set up Ubuntu Server or Debian.

Is this endeavor worthwhile?  All feedback from experienced administrators is appreciated.

---

### Post by aaaantoine on 2008-08-07
Basically, I want to do this:
[http://h18004.www1.hp.com/products/servers/vmware/vdi.html?psn=servers](http://h18004.www1.hp.com/products/servers/vmware/vdi.html?psn=servers)

Except with VirtualBox OSE (if possible).

---

### Post by cariboo on 2008-08-07
VMWare ESXi is now free check it out here:

[https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1](https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1)

Jim

---

### Post by tinny on 2008-08-07
> **cariboo907 said:**
> VMWare ESXi is now free check it out here:

[https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1](https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1)

Jim

VMWare ESXi is now free!!! COOL (VMWare server would be too slow for you). 20 VM's would be hard work for the server right? It would help if you could split the VM's amongst multiple hard disks (a shared hard disk is always going to be a big over head for the VM's). You can do this in VMWare.

But it sounds to me like you need [Citrix XenApp]("http://en.wikipedia.org/wiki/Citrix_XenApp") or [LTSP]("http://www.ltsp.org/")

I dont think LTSP works for windows clients :(

---

### Post by aaaantoine on 2008-08-08
> **tinny said:**
> VMWare ESXi is now free!!! COOL (VMWare server would be too slow for you).

I'll have to check it out.  Thanks, cariboo!

> **tinny said:**
> 20 VM's would be hard work for the server right? It would help if you could split the VM's amongst multiple hard disks (a shared hard disk is always going to be a big over head for the VM's). You can do this in VMWare.

That's part of the idea behind running a RAID 5 setup.  That, and drive failure insurance.

> **tinny said:**
> But it sounds to me like you need [Citrix XenApp]("http://en.wikipedia.org/wiki/Citrix_XenApp") or [LTSP]("http://www.ltsp.org/")

XenApp sounds optimal for Windows clients, but I have no idea how much it would cost.  Ah well, I guess contacting them wouldn't hurt...

> **tinny said:**
> I dont think LTSP works for windows clients :(

Yeah, probably not.  Maybe I'll just do a trial run of Ubuntu clients and see if the call center likes it.

---

### Post by m_j_lyons on 2008-10-08
I'm also seeking to answer the same question - if you have any luck, please post it here.

---

### Post by lykwydchykyn on 2008-10-08
LTSP could work in this scenario if you wanted to use it, though there are commercial apps that are probably slicker.  

But for the sake of argument:
 - set up ltsp
 - have the thin clients auto-login to the server
 - replace the client's .xsession with a script that launches winxp in VirtualBox instead of a desktop or wm.

It's all very doable, though it's admittedly a hacked-up roll-your-own kind of solution that nobody would really support if you needed support.  But I'll wager that's about 90% of what most of the commercial solutions are actually doing behind the scenes.  There would probably be a lot of tweaking to do to get it just right, but then again it'd be free (in both senses).

---

### Post by windependence on 2008-10-09
Well, the best way with your hardware would be to get an enterprise version of VMware ESX (street price is about $5700 for two processor sockets - not cores). You could run even 50 VMs on a box like that because Vmware has shared memory paging meaning if 10 or 15 of your VMs need the same memory page, it is only necessary to load it into physical memory on time. This saves a huge amount of physical memory. VMware is the only virtualization software that uses this feature.

A common mistake most people make when sizing VMs to the host is that they want to give the guest as much memory as it would have on a physical box. It's not necessary to do that because whatever memory is not being used by other VMs is available for that particular guest when needed, eliminating the need to use so much physical memory on the guest.

ESX and ESXi do not need a host OS, they run on bare metal so they are much faster.

I know of a guy in Canada that uses thin clients for his school district. The boxes are diskless, basically just terminals. If you want some local storage with fast boot, you can use flash media with  and IDE adapter and boot from there. I'll see if I can find out more from him about how he does it, but I know it works very well for him.

-Tim

---

### Post by tinny on 2008-10-09
> **windependence said:**
> Well, the best way with your hardware would be to get an enterprise version of VMware ESX (street price is about $5700 for two processor sockets - not cores). You could run even 50 VMs on a box like that because Vmware has shared memory paging meaning if 10 or 15 of your VMs need the same memory page, it is only necessary to load it into physical memory on time. This saves a huge amount of physical memory. VMware is the only virtualization software that uses this feature.

A common mistake most people make when sizing VMs to the host is that they want to give the guest as much memory as it would have on a physical box. It's not necessary to do that because whatever memory is not being used by other VMs is available for that particular guest when needed, eliminating the need to use so much physical memory on the guest.

ESX and ESXi do not need a host OS, they run on bare metal so they are much faster.

I know of a guy in Canada that uses thin clients for his school district. The boxes are diskless, basically just terminals. If you want some local storage with fast boot, you can use flash media with  and IDE adapter and boot from there. I'll see if I can find out more from him about how he does it, but I know it works very well for him.

-Tim

I see there is a free version of VMware ESXi. Is there an enterprise version? If so what are the differences?

---

### Post by windependence on 2008-10-09
Essentially, the free version has all the features of the big one, with the exception that you have to manage it one server at a time using the VIC (virtual infrastructure client). With the enterprise version you can admin them all at once from one central source. Not much of a difference for a small operation since we tend to work on one box at a time in that environment.

There are also some open source tools out there that claim to be able to manage VMs like VMware's Virtual Center product. I have not tried them yet because I have only needed to work with the VIC and that was fine.

-Tim

---

