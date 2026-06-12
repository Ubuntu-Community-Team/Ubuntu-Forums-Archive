---
title: "OEM install to virtualbox or VMWare"
date: 2010-05-26
forum: Virtualisation
---

### Post by rwslippey on 2010-05-26
I have an issue here, and can't seem to find the awnser..

I'm looking to doing some virtualization on my laptop. It's a Panasonic Toughbook CF-52  on a side note, yes the warranty and cost are worth it. It's already survived a beating (not intentional of course)


I have an OEM disk from Panasonic to install from, however I want to install it to Virtualbox and run XP as a guest and Ubuntu as my primary OS, doing this either with VMWare workstation or virtualbox.

Anyone have any ideas on how to convert a windows installation to a virtal machine?

Thanks

Rob

---

### Post by TheFu on 2010-05-26
> **rwslippey said:**
> I have an OEM disk from Panasonic to install from

Here's the issue. Recent OEM disks are tied to the physical hardware that they support. I suspect yours will try to validate it is being installed on a Panasonic laptop and refuse to install on anything else.  That limitiation is part of the OEM Windows license agreement.

That's why OEM Windows versions are cheap and full retail versions are not. The full versions can be installed on different hardware over the life of the OS.  Heck, I'm still using a WinXP retail DVD from 2001 (pre-SP1) and it is on about the 4th physical PC since the first install. Just installed it into VirtualBox this week to get the 2nd CPU HAL working. It was actually an upgrade from Win95, so I had to find that CD to prove I earned the upgrade. ;)

Ok, to your last question - how to convert a physical install into a virtual machine.  VMware makes some free software to do it.  It is called P2V conversion.  The official name is "Converter Standalone Client". [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/) or[SIZE=2] VMware vCenter Converter[/SIZE]. I think you'll need a free vmware.com account to download it.  I can't recall, but I think you may need an ESX or ESXi server to target during the conversion process. I have 1, so it wasn't a big deal.  VMware is the main game for p2v conversions, but some other 3rd parties also do it. For some reason I think they concentrate on servers, not desktop conversions.

---

