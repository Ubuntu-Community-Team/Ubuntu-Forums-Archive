---
title: "PowerEdge 1850"
date: 2010-08-24
forum: Server Platforms
---

### Post by S.R on 2010-08-24
Checked the certified hardware on the Ubuntu website and says it supports the PowerEdge 1950. Does anyone know if the PowerEdge 1850 will run Ubuntu Server equally well?

---

### Post by scorp123 on 2010-08-24
It's easier to check the single components (network cards, SCSI cards, fibre channel cards, etc.) than entire server models. So if you can't find the particular server model as a whole, take a look about what it says about the components inside your server? Google works great for this.

And if in doubt: You could boot the Ubuntu Live CD and check what it says about your hardware. The advantage would be that because it's a live CD it won't touch your server's harddisk in any way (unless you choose to install the OS).

In my experience most 'real' x86 server hardware works out of the box with Ubuntu, no matter if it's a Dell, IBM, HP, Compaq, Sun, Unisys ... 

They usually work "out of the box".

---

### Post by S.R on 2010-08-24
Thanks. It is going to be fresh build and I am not worried about installing Ubuntu. Trying to figure out what pitfalls might be lurking but good suggestion on looking at the individual components.

---

### Post by doogy2004 on 2010-08-24
> **S.R said:**
> Checked the certified hardware on the Ubuntu website and says it supports the PowerEdge 1950. Does anyone know if the PowerEdge 1850 will run Ubuntu Server equally well?

I'm sure that Ubuntu can run on it no problem, because I'm running VMware ESXi 4 on my PE1850 and esxi is more restricted in hardware support.

---

### Post by scorp123 on 2010-08-25
> **S.R said:**
> Trying to figure out what pitfalls might be lurking but good suggestion on looking at the individual components. The only time I ever had serious troubles getting a server to work with Ubuntu was with an older Compaq/HP ProLiant DL-380. Some of those ProLiant machines have a Compaq/HP-proprietary RAID controller and without proper kernel support a Linux distro won't see any harddisks ... which makes installing a bit more complicated as you can imagine. :D

The solution would be to boot with a modified Linux kernel that has the required module compiled in ... Getting there was a bit of a hassle. Some Enterprise-focused distros such as RHEL, SLES and CentOS will work better with such servers as they already have "out of the box" support for such rather exotic disk controllers.

Unless your server has some really exotic hardware like that inside it should pretty much work without any hassles. SCSI cards, Fibre Channel cards, Host Bus Adapter cards, Quad Ethernet-Controllers, 10 Gbit Ethernet cards, professional Quad-Head graphics controllers for CAD, SATA SSD's, SAS RAID controllers,  ... I have had such hardware in my HP and SUN servers and rarely if ever had troubles getting any of it to work with Ubuntu. 

The few times I really had trouble was with multi-pathing, e.g. disk-arrays where the same disks due to redundant connections could be reached multiple times under different device names ... it seems Linux can still learn a trick or two from commercial Unix flavours such as Solaris in that area ... but OK, you fire up Google and taddaaaa ... somewhere somehow there will be a solution for such problems as well.

That's as far as potential pitfalls go IMHO and I imagine your server should do tip top.

---

