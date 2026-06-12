---
title: "KVM Network Transfer between Guest to Host with CIFS"
date: 2010-02-12
forum: Virtualisation
---

### Post by Dexter104 on 2010-02-12
Hello All,

I recently installed Ubuntu 9.10 Server to control a large number of SATA drives using mdadm software raid that is serving data via CIFS shares to a large number of Windows Servers. I am on a gig network and currently getting great transfer speeds from the Windows Servers to Ubuntu (around 80 MB/s) and vise versa. I decided to also install KVM to visualize a Windows 2008 Server that runs proprietary software built by our company to take advantage of some of the extra cpu bandwidth the Ubuntu Server has.

The problem I am having is that transfer speeds from the Windows 2008 Enterprise Server guest to the Ubuntu host over CIFS is extremely slow (around 8 MB/s). I am using a bridged connection and I selected the e1000 network device after trying the others and finding them even slower including the virtio driver. Another note on this is that speeds going from the guest to another windows server is also fast around 70 MB/s.

I can't seem to find what the issue is, I thought the network card was being saturated during the day but I get the same results late a night when the guest OS would be the only thing transferring files to the host.

Any thoughts? Please let me know if I can provide any other information.

Thanks.

---

