---
title: "How to access shared folders in Virtualbox Ubuntu VM?"
date: 2014-07-02
forum: Virtualisation
---

### Post by Bobby_James on 2014-07-02
I have installed the latest version of VirtualBox with the Extensions under 12.04. I've created an Ubuntu 12.04 LTS VM.  I then created shared folders from my non-VM Ubuntu. The shared directory is persistent.

However, I've no idea how to access the shared folders on the VM.  I've done this in Windows VMs but cannot do it in Ubuntu VM. 

I've read a number of guides which talk about the vboxusers group and suchlike.  I've tried it all but cannot see the shared folder in the Ubuntu VM.

So, my question is: how would you go about accessing the shared folder in an Ubuntu VM?

Thanks.

---

### Post by TheFu on 2014-07-03
You need to mount the vbox file system inside the guest. Browing don't work.
$ sudo mount -t vboxsf D /Data
Where 'D' is the name of the share inside vbox (hostOS) and /Data is the pre-existing mount point where you want it mounted. Any empty directory is fine.

I understand the virtualbox manual is really good on this stuff, but haven't looked at it in a few years.

---

