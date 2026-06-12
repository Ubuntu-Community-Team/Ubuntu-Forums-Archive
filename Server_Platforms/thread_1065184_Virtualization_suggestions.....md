---
title: "Virtualization suggestions...."
date: 2009-02-09
forum: Server Platforms
---

### Post by robmypro on 2009-02-09
Hey guys, I wanted to get an opinion about the various VM solutions available. I want to set it up at home, as a test. I will probably be running 2-3 VM's on a Dell PowerEdge 830 Server with 8GB RAM. What would you guys suggest?

Ubuntu 8.10 Running KVM
Ubuntu 8.10 running VMware Server
ESXi 
Something else?

The VM's will be Win2k and Win2k3 Servers, along with Ubuntu 32 bit server. 

Thoughts appreciated!

---

### Post by inphektion on 2009-02-09
If you can get esxi on that poweredge that would be my first choice simply to eliminate the overhead of a host OS.

---

### Post by windependence on 2009-02-09
ESXi.

Runs on bare metal, no host OS needed.
Free (as in beer).
Great management via the VMware Infrastructure Client. (also free)
32 MB footprint.
Wide industry support.
Biggest number of guest OS support.

If you need help, let us know.

-Tim

---

### Post by robmypro on 2009-02-09
Thanks guys! Sounds like ESXi is the winner. I will give you guys a shout if I get in trouble. 

Thanks again!

---

### Post by robmypro on 2009-02-10
Unfortunately I don't think ESXi is going to work on my hardware. It appears that it won't support my SATA drives or my USB backup drive. So...I guess I am stuck using Ubuntu Server running VMware Server. I have one VM that I have to support so VM has to be part of my implementation.

I really don't understand why I cannot connect a USB drive to the system. It wouldn't be used to boot, or as a VM. But I need an external backup system. Since I have SCSI also, I guess I could get a SCSI drive and use it as a backup.

Any thoughts guys?

---

### Post by Robstarusa on 2009-02-10
Proxmox VE?[Link]("http://www.proxmox.com/cms_proxmox/en/products/proxmox-ve/proxmox-ve-startseite.html")

---

