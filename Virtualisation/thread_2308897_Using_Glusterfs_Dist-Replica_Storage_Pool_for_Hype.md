---
title: "Using Glusterfs Dist-Replica Storage Pool for Hyper-V Virtual Machine Storage"
date: 2016-01-06
forum: Virtualisation
---

### Post by ryan_3 on 2016-01-06
Am chasing down some information regarding an upcoming project. So Basically we have a large Glusterfs Dist-Replica Storage pool running on ubuntu and we want to have several virtual machines running off this from our windows 2012 server,
Now we are using Hyper-V to run the Virtual machines and so far I am having a bit of trouble getting the VHDX to actually create on the Gluster Storage pool.
I've created a mount point with Gluster and have tried to share it out with Samba yet it would never create the VHDX or run an existing one on the cluster as it continously would throw errors like: Error Incorrect Function on the hypervisor. Changed Permissions, Allowed Anon access, Made sure it could RW etc etc still would not allow any VHDX to be created.
Then Tried to share it out with NFS and the Hyper-V when creating a VM would throw out errors like this: File System limitation Found out this is rather common: [https://slog.starwindsoftware.com/hyper-v-vms-on-nfs-share/](https://slog.starwindsoftware.com/hyper-v-vms-on-nfs-share/)
So I'm curious if anyone out there does have Hyper-V Virtual machines running on Glusterfs and if so how you got it configured? Any information at all would be fantastic :)
On a side note please let me know if anyone has used VMware with Samba/NFS and if this performed better than Hyper-V.
Thanks team

---

### Post by howefield on 2016-01-06
Thread moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-01-06
Note: Even though he's talking about doing virtualization, his topic is more server SANS, or ... "network distributed storage pools." <-- That just happen to be used to stored their VM's. So this may be more specifically a server topic, but no matters.

Didn't you also ask this same question today on Server Fault? I have questions... Why GlusterFS network distributed storage nodes? If so, you would still need soemthing like Samba t use with Windows server right?

I'm a LInux guy, and I do crossplatform, but ... Now for the hard to swallow questions. If using Windows Server 2012R2, why are you not looking into iSCSI and Windows Storage Spaces (Software Defined Storage or SDS)? If I were doing vSpere or KVM, I usually do LVM. When I was doing my MSCS certs, it seemed to me that 2012R2's new Storage Spaces, was Windows equivalent to LVM. When I thought of setting up Hyper-V, Storage Spaces made sense to me to fit the bill for expanding storage needs for virtual servers, just like LVM does for me in the Linux realm.

---

