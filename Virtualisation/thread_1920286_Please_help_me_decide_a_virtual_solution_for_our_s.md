---
title: "Please help me decide a virtual solution for our smb"
date: 2012-02-04
forum: Virtualisation
---

### Post by greavette on 2012-02-04
Hello,

There are so many types of solutions out there, I'm going in circles trying to figure out the best solution for our smb.

We have successfully been running VMware Server v2 on three host servers for the past 3 years.  One of our Servers is a Dell 710 so it is the only one that has vt available to it.  The other 2 servers don't have that option.

Performance has been good on all our VM's.  I'm sure if we were using esxi or hyper-v we would be able to run more VM's 
off of one server and have great performance, but this is the environment I was given when we started. 

With VMware Server not being supported or upgraded anymore, I really want to move away from using it.  I'm hesitant to using hyper-v or esxi since only one of our servers can use that technology so if it went down, we'd be up a creek.  Performance is important to me in that I don't want performance to be any worse than what we have now.  
I also can't rebuild our VM's right now using a different technology, so our solution has to work with the VM's we have now.  I'm also quite worried about support for our VM environment.  I support this smb remotely and have the help of an onsite resource who has no experience with Linux or no GUI's.

I think my only option is to use VirtualBox on an Ubuntu Desktop.  

All three of our Host Servers could easily run Ubuntu Desktop and could therefore use VirtualBox.  VirtualBox could recognize our vmdk files.  Each host has anywhere from 8gb to 16gb of RAM with hardware raid controllers (Raid 10 and Raid 5).  I could bond the nics on each host (but I'd have to see if our unmanaged switches that have jumbo frames would work or not).  With 3 hosts available, if one host failed we would still be able to run all VM's off of 2 hosts.

I'm thinking this would be our best solution.  What do you think?

All opinions are welcome.

Thank you.

---

### Post by majestic12 on 2012-02-06
I am in the same position.  I have not worked with virtual box though I hear good things about it.  Personally I am moving towards KVM since it is most like the type of product VMware Server used to be. I think importantly is that KVM is a part of the standard Linux kernel and therefore supported by just about all Linux distributions. Having said that, I have had proportionately more problems out of KVM than I ever had out of VMware. At present I have a system that as soon as I initiate my guest I lose control over my host.  The console just stops working. I have to remote sh into my guest, shut it down and then hit the reset button (DOH!) to unlock it. The VM continues to run in that state but I have no control over the host.  I'm bummed about that and haven't found a way to correct it yet. I am sure it is something simple.

Try KVM if you haven't yet.

---

### Post by Cheesemill on 2012-02-07
For an out of the box KVM solution take a look at Proxmox VE, I use it successfully at at couple of my clients sites.

[http://www.proxmox.com/](http://www.proxmox.com/)

---

