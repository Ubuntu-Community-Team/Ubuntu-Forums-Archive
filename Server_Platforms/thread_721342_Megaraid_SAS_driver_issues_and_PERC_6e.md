---
title: "Megaraid_SAS driver issues and PERC 6/e"
date: 2008-03-11
forum: Server Platforms
---

### Post by Petersonz on 2008-03-11
I have a Poweredge 2950 with the internal Perc 5/i and a RAID 5 array on it, plus an external MD1000 attached to a Perc 6/e.

Using Gutsy, if there is heavy disk I/O on on the MD1000/Perc 6/e, it fails and crashes and becomes unavailable until the next reboot.

The entire system is less than a month old and never shows any indicators in the hardware or BIOS.

I have checked firmware of the Dell, there is a newer one, but I havent tried it yet.

The Perc 6/e has the latest firmware on it.

I even tried the Hardy kernel 2.6.24-11-server (AMD/64) and still it has the 00.03.10-RC5 Megaraid_SAS driver in it.

Dell has 00.03.15 Megaraid_SAS driver available for download (As does LSI Logic), but its in Redhat or Suse format.

How can I get those drivers to load in Ubuntu server to see if it fixes the problem? Is there a source available elsewhere?

Finally, I have a Poweredge 1950 with the same configuration except the internal Perc 5/i has just a mirrored array on it instead of the RAID 5 array. So far, its very stable. But it did take the 2.6.24-11-server kernel to make it stable.

Thanks for any help you can provide.

---

### Post by sr20ve on 2008-03-11
If you want to run the perc 6 controller in an unsupported OS for that controller, you'll need to do some work. I'm not sure if it would work, but you might be able to download the RHEL version of the driver from Dell's website and convert the DKMS RPM to DEB using alien. Install DKMS, convert the driver RPM to a tarball and install the driver using DKMS.

---

### Post by Petersonz on 2008-03-13
Alien didnt work, but I forgot to do dkms too so the module could be compiled and installed.

I ran out of time and went Redhat Enterprise. 

I really dont like being forced there, it would be nice if the Hardy developers could either update the megaraid_sas drivers in the kernel or in Gutsy's kernel... Dell servers are quite well priced and popular. The Perc 5's and Perc 6's are here to stay.


On a side note, the cciss driver in Ubuntu's kernel has some strange problems in HP Generation 5 servers with the smartarray 6'es. I have yet to figure them out, but in the end might have to revert to Redhat on those too unless the kernel is updated soon with newer cciss drivers...

Dell and HP seem to be only supplying Redhat and Suse drivers for servers. The Ubuntu community should turn up the heat and convince them to release source drivers that can compile modules against the Ubuntu kernel source :) 

Intel does for their network cards. 
Broadcom does for their network cards (under GNU).

Whats the holdup with Dell and HP and their storage drivers?!

---

### Post by gtdaqua on 2008-03-13
> **Petersonz said:**
> Alien didnt work, but I forgot to do dkms too so the module could be compiled and installed.

I ran out of time and went Redhat Enterprise. 

I really dont like being forced there, it would be nice if the Hardy developers could either update the megaraid_sas drivers in the kernel or in Gutsy's kernel... Dell servers are quite well priced and popular. The Perc 5's and Perc 6's are here to stay.


On a side note, the cciss driver in Ubuntu's kernel has some strange problems in HP Generation 5 servers with the smartarray 6'es. I have yet to figure them out, but in the end might have to revert to Redhat on those too unless the kernel is updated soon with newer cciss drivers...

Dell and HP seem to be only supplying Redhat and Suse drivers for servers. The Ubuntu community should turn up the heat and convince them to release source drivers that can compile modules against the Ubuntu kernel source :) 

Intel does for their network cards. 
Broadcom does for their network cards (under GNU).

Whats the holdup with Dell and HP and their storage drivers?!

Thats right. How come no one ever pursued dell on this. I am now asking Dell for solutions because our data centre runs on dell gears (not just servers). It will be a difficult and arrogant on their part if they are going to diplomatically refuse to support.

---

