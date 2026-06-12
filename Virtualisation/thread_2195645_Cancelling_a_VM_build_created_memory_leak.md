---
title: "Cancelling a VM build created memory leak"
date: 2013-12-25
forum: Virtualisation
---

### Post by jauntyjoshy on 2013-12-25
I made a mistaaaaaaaaaaaake!

What is the preferred course of action when cancelling the creation of a virtual machine doesn't free the space that was to be allocated for it? Today I tried to create a VM, allocating 2GB of RAM and 350GB of disk space. While creating it, however, I had cold feet and cancelled the process. Now I have no virtual machine, and GParted is informing me that those 350GB are in use. Is there a way to get them back?

Ubuntu 13.10, System76 laptop, and let me know if there's anymore information you need.

---

### Post by deadflowr on 2013-12-26
What kind of vm was it?
Virtualbox or something?

If virtualbox, it makes a folder in the home folder called Virtualbox VMs
you can delete the folder within for the vm you started to build.
Of course the above question would have to be in fact virtualbox.
Don't know about where other virtualization progams store such stuff.

---

### Post by jauntyjoshy on 2013-12-27
> **deadflowr said:**
> What kind of vm was it?
Virtualbox or something?

If virtualbox, it makes a folder in the home folder called Virtualbox VMs
you can delete the folder within for the vm you started to build.
Of course the above question would have to be in fact virtualbox.
Don't know about where other virtualization progams store such stuff.

It was indeed a VirtualBox VM. The folder you mention doesn't appear to exist, though. I must have cancelled the build before it could create a directory for that particular machine...

After further inspecting my disk usage, I've found a file within my eCryptFS that is ~350GB in size. If I delete this file, will my problem roughly be solved? I get the sense from the Googling I've done that the eCryptFS should be tampered with at one's own risk.

---

