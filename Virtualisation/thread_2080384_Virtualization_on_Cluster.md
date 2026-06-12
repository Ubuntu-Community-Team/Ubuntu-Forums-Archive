---
title: "Virtualization on Cluster"
date: 2012-11-03
forum: Virtualisation
---

### Post by ocpistol on 2012-11-03
We are a small company with 4 servers, (Web,File, ERP, DVR/Surveillance). We are looking at wanting to make a cluster of 2 or more machines to Run all these. Is it possible to put vmware on a cluster then put all our servers inside of vmware? In case one physical server went down everything wouldn't go down?

Thank You

---

### Post by 2F4U on 2012-11-04
In general, yes, it is possible. But I would suggest you do some basic research.

[http://www.vmware.com/virtualization/virtual-infrastructure.html](http://www.vmware.com/virtualization/virtual-infrastructure.html)

---

### Post by ocpistol on 2012-11-04
Yes Iv dont this But I dont want to spend thousands for vsphere. Has to be a free easy way to do this with ubuntu.

---

### Post by Old_Grey_Wolf on 2012-11-04
You may want to look at this: 

[Ubuntu Cloud Infrastructure]("https://help.ubuntu.com/community/UbuntuCloudInfrastructure").

---

### Post by kow777 on 2012-11-06
You could look into Proxmox. It run on top of Debian, but you can install it on top of Ubuntu.
[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

---

