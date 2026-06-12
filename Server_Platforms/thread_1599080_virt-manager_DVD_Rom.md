---
title: "virt-manager DVD Rom"
date: 2010-10-17
forum: Server Platforms
---

### Post by tomgibson on 2010-10-17
Haven't been able to find anything on Google about this so I'm guessing it's not too common a problem.

Is there any way to pass through my VM Host's physical DVD drive to a Windows VM and use it as though it were physically attached to the Windows OS, using virt-manager and kvm as the virtualization platform? So far I have managed to connect the DVD drive to the virtual machine in virt-manager, but every time I change the DVD I have to remount the disk in virt-manager. This means that I have to run virt-manager when I change the disk which isn't so bad, except that when running virt-manager locally on my workstation and connecting to my network VM Host I get the error

"Cannot use storage '/dev/sr0': '/dev' is not managed on the remote host."

Therefore I have to run virt-manager on the remote VM Host via SSH -X, when doing this I don't get the error and the DVD is then attached OK.

Ideally I would like to not have to touch virt-manager when inserting a DVD since I only require the DVD drive to be accessible from a single Windows VM. However, if it is necessary to mount the new disk each time, is there a way to do so whilst running virt-manager on my local workstation instead of using SSH -X to the VM Host?

I'm hoping not to have to keep virt-manager installed on my VM Host since it's preferable to manage the machine using virt-manager on my workstation. The only other reason I have at the moment for keeping it installed is that when creating VM's I have to run virt-manager on the VM Host to select a bridged network, however I suspect I can just use virsh to do this, or perhaps create a template that I can copy. Eventually I'm hoping to remove virt-manager altogether from my VM Host.

Since I have included a lot of detail I will summarize my key questions:

1) Can I simply pass-through my VM Host's DVD drive to my Windows guest so the DVD drive behaves as though it were physically attached to the guest?

2) If this is not possible, can I configure virt-manager on my workstation so that I can mount the disk from there each time rather than using virt-manger on the VM Host via SSH +X.

Thanks in advance!

---

### Post by tomgibson on 2010-10-20
Does anyone have any thoughts or suggestions? I'd settle for removing the need to run virt-manger on the VM Host via SSH.

Thanks!

---

### Post by Nakarti on 2012-01-29
Just popping in 1.5 years later because this is high in the Google results and it does the same BS.
Thanks for pointing out that tunnelled instance works OK but why doesn't a remote instance of virt-manager? Everything else seems to work OK.

---

### Post by XmagusX on 2012-08-31
I encountered something similar and the fix was to add a new storage pool.
Path to do so:
Edit menu
Connection Details
Storage tab
Plus button in lower left hand corner
Filled out fields as was appropriate

Credit for fix:
[https://access.redhat.com/knowledge/solutions/25129](https://access.redhat.com/knowledge/solutions/25129)

---

