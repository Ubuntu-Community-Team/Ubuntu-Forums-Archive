---
title: "Virtual Machine manager from another computer"
date: 2010-07-14
forum: Virtualisation
---

### Post by changlinn on 2010-07-14
I have virtual machine manager installed on another machine connecting to my KVM server, I connect with [email]user@hostname.local[/email] and it asks for users password, I put that in and I can see my vm's one is running (as I turned that on from the kvm servers gui, which I had to run with gksudo to get access to my bridge adapter), if my workstation goes into screensaver or virtual machine manager disconnects any of the machines I have turned on from the workstation, turn off, that one machine that I switched on from the local gui will still be on when I reconnect.
Any ideas as to why this may be? I would obviously like to be able to admin including power on the virtual machines from my workstation, and having a disconnection cause them to switch off is not good.
I have made sure my user is in the kvm group and the libvirtd groups

the crux of the issue is that when connecting remotely to virtual manager I can power on VM's and interact with them, but if the remote machine goes offline, or even simply goes to screensaver the machines I have powered on simply power off

Silly me I checked the logs on the boxes that where shutting down and there was an error.

---

