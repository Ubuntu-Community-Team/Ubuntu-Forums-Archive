---
title: "Ubuntu 9.04 on ESX4i - poor network performance after a while"
date: 2009-09-08
forum: Server Platforms
---

### Post by pgruber on 2009-09-08
Hello!

I've got a problem with an virtual NAS I built on an ESX4i under Ubuntu 9.04 (x86).

Hardware: Homebuilt PC (Asus MB/AMD 5050e/8GB RAM/Dell Perc 5i Controller with 4 Samsung 1TB HDDs (RAID5)/onboard NIC and additional Intel PRO/1000MT)

Did a minimal install of Ubuntu with NFS-Kernel-Server and Samba.

After switching on the VM, I get a Samba Performance of about 70 to 80 MB/s reading. NFS is somewhere in this range.

But after 3 minutes or so, the performance drops down to about 3MB/s. Rebooting theVM does not help. Only shutting it down and switching it on again. (The VM! not the ESX-Server)

I only have this Problem with this Linux-Machine. No problems at all with neither my Windows 2008 x64 and Windows 2003 x86/x64 servers nor the XP-Client x86. All VMs on the same ESX.

VMWare-Tools are installed.

Very annoying as this is my Fileserver.

Tried it on onboard NIC and Intel NIC. The same. Tried another switch. The same.

Someone has an idea?

Thanks,
Patrick

---

### Post by windependence on 2009-09-08
How many NICs do you have in the machine? It is very easy to bond NICs in ESXi. I would have to see how you have your hardware set up to really help you with this.

The other thing is you are using desktop hardware. This may have nothing to do with your problem, but ESXi and ESX are built for server class hardware, and in my experience, sometimes desktop hardware doesn't perform as well.

-Tim

---

### Post by pgruber on 2009-09-08
Hi Tim,
 
I know this is desktop-hardware. But for my server at hme, I had to look for a energysaving type of hardware, that ha also be quiet and - for sure - cheap.
 
This machine performs very well.
 
I have two NICs in this machine. The onboard one (forcedeth) and the PCI Intel PRO/1000MT (e1000).
 
Regards,
Patrick

---

### Post by windependence on 2009-09-09
Check this out:

[http://www.supermicro.com/products/motherboard/ATOM/945/X7SLA.cfm?typ=H](http://www.supermicro.com/products/motherboard/ATOM/945/X7SLA.cfm?typ=H)

Can't get much more low power than that one.

I'm gonna try to get a screen capture for you so you can bond those nics. Since you're running the Intel 1000, there should not be a problem at all with that as that is the hardware VMware emulates.

-Tim

---

### Post by pgruber on 2009-09-09
Hi Tim,
 
thanks, I'm aware of bonding NICs in ESX. I have only an unmanaged switch, so bonding is not possible.
But I don't think it's related to network-bandwidth as the other VMs are fast on network and harddisk.
 
Thanks for the link to the Atom-Board. I have an Atom in use (for HTPC/XBMC). This CPU is not powerful enough fo my ESX-Host and max-memory is too low.
My rig now uses a 45W-Athlon but I think most power is consumpted from the 4 Samsung F1-Harddisks.
 
Regards,
Patrick

---

