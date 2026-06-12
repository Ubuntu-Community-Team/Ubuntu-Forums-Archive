---
title: "I need an NFS export to run on TCP...."
date: 2008-12-20
forum: Server Platforms
---

### Post by Underpants on 2008-12-20
I need to setup an NFS export compatible with VMware ESXi. When I add the export to vmware it says "the nfs server does not support mount version 3 over tcp" 

Is there a setting I can tweak to support TCP instead of UDP?

---

### Post by Underpants on 2008-12-20
bump for help

---

### Post by RealPSL on 2008-12-21
From what I have read and there is an example below the proto=tcp setting should help you but it is configured on the client side.

[http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/]("http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/")

---

### Post by windependence on 2008-12-21
Just a tip, for ESXi I set up a NAS using FreeNAS. It has a GUI web interface to set up all your NFS shares as well as iSCSI. Works great and is rock solid with ESXi or ESX enterprise server.

-Tim

---

### Post by Underpants on 2008-12-21
> **windependence said:**
> Just a tip, for ESXi I set up a NAS using FreeNAS. It has a GUI web interface to set up all your NFS shares as well as iSCSI. Works great and is rock solid with ESXi or ESX enterprise server.

-Tim

I need a full blown linux. It does more than just store files.

---

### Post by windependence on 2008-12-21
> **Underpants said:**
> I need a full blown linux. It does more than just store files.

I think we're not on the same page here. ESXi will not load on most SATA drives so I though you were attempting to set up a SAN to use for installing VMs on ESXi. ESXi runs on bare metal, no underlying OS needed. You can then run a Linux VM on a slice of your NAS box. See what I'm saying?

-Tim

VMware Channel Partner

---

### Post by Underpants on 2008-12-21
ESX is already installed and running. I am trying to add storage from within the infrastructure client. I'm not trying to install ESX on the NFS.

---

### Post by windependence on 2008-12-21
No, no, that is exactly what I though you were doing. What I did was build myself a FreeNAS box with 2 TB of RAID 5 storage and then slice it up to use on my servers as LUNs. That's what I though you wanted to do also. It works great BTW.

-Tim

---

### Post by Underpants on 2008-12-21
> **windependence said:**
> No, no, that is exactly what I though you were doing. What I did was build myself a FreeNAS box with 2 TB of RAID 5 storage and then slice it up to use on my servers as LUNs. That's what I though you wanted to do also. It works great BTW.

-Tim


Cool. :D

I'm skipping the freenas (i prefer openfiler) step since the box needs to run various scripts and provides routing from time to time. 

I'm comfortable using mdadm to manage my arrays. To each his own.

thanks for the help

---

### Post by windependence on 2008-12-21
I tried OpenFiler and I dunno, maybe I just didn't get it or something but it seemed a bit complex for me and I'm a FreeBSD guy so I opted for FreeNAS. Same principle though. Since I use the SAN for customer web sites I wanted a dedicated box. I do use softraid on that box. It's the *BSD version so no mdadmin but pretty much just as easy if not simpler.

-Tim

---

