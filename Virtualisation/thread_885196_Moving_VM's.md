---
title: "Moving VM's"
date: 2008-08-09
forum: Virtualisation
---

### Post by bluewhale on 2008-08-09
Hi.  I'm running 8.04 with VMWare Workstation 6.0.4.  
My primary hard drive is a bit small, so I tried to copy/move my VM's to another drive in the system. I then went back into VMWare and pointed toward the new location of the VM's. 

VMWare asked if I had moved or copied the VM. I chose 'moved'.. a few questions later I was told 

VMware Workstation unrecoverable error: (vcpu-0)  Failed to allocate page for guest RAM!

The posts I've seen on this stem from other issues, at least it looks that way. One recurring theme is that I need to have read/write access to the drive I've placed the VM's on. I don't follow that tho: I already have those rights as I move files in and out of that drive all the time. 

I've tried lowering the memory size of the VM. Still getting the error. 

Could anybody point me in the right direction?

---

### Post by bluewhale on 2008-08-13
Does BUMP do any good on these forums?

---

### Post by HermanAB on 2008-08-13
Check the ownership on the old directory with 'ls -al' and make the new one the same with 'chown -R what:ever /where/ever'.

Otherwise, copy it again, this time using the '-a' flag:
# cp -a /old/vmware /new/vmware

Cheers,

Herman

---

