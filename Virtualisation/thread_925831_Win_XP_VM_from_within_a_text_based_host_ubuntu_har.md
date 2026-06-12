---
title: "Win XP VM from within a text based host ubuntu hardy?"
date: 2008-09-21
forum: Virtualisation
---

### Post by pradeep.gatram on 2008-09-21
I was wondering if it is possible to run a Win XP virtual machine from within a text based ubuntu server install? I would prefer to do this using kvm, but am also open to considering other tools (again preferably FOSS).

I have already created a win XP vm using qemu and it boots up properly using kvm on a ubuntu hardy host (with gui installed). 

When I try attempting this bootup on a ubuntu server using either kvm or qemu, I get an error (will post the exact message from office tomorrow). What I could make out was that I would need a gui based host OS to boot up the win XP vm.

---

### Post by trmentry on 2008-09-21
Take a look at Virtualbox.   YOu can run a vm in virtualbox on a headless server.  YOu would attach to the 'console' of the vm using RDP.

[http://download.virtualbox.org/virtualbox/2.0.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.0.2/UserManual.pdf)

I believe you have to use the PUEL version of VIrtualbox to get the RDP functionality.  

vmware server is free although it's not open source.  but it works great and is really easy to setup.


Foudn this howto for vb [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by veloce on 2008-09-21
> **pradeep.gatram said:**
> I was wondering if it is possible to run a Win XP virtual machine from within a text based ubuntu server install? I would prefer to do this using kvm, but am also open to considering other tools (again preferably FOSS).

I have already created a win XP vm using qemu and it boots up properly using kvm on a ubuntu hardy host (with gui installed). 

When I try attempting this bootup on a ubuntu server using either kvm or qemu, I get an error (will post the exact message from office tomorrow). What I could make out was that I would need a gui based host OS to boot up the win XP vm.

You need a gui to run the vm's gui.  This does not need to be on the host running the vm (as per the previous response you can rdp to the windows vm).

---

### Post by pradeep.gatram on 2008-09-22
ah, so I need a gui to view the vm's gui. Fine, that makes sense. A bit of googling led me to

[http://www.linux-kvm.com/content/tip-how-run-headless-guest-machine-using-vnc-kvm](http://www.linux-kvm.com/content/tip-how-run-headless-guest-machine-using-vnc-kvm)

[http://www.linux-kvm.com/content/securing-your-vnc-headless-guest-simple-passwords](http://www.linux-kvm.com/content/securing-your-vnc-headless-guest-simple-passwords)

I am going to try these and see how it goes.

---

### Post by veloce on 2008-09-22
I've found rdp better than vnc for remote access to XP machines.  

But once you've got a vm up on the "headless" machine you can switch to rdp easily. 

kvm is more adventurous than virtual box or vmware but should run pretty well.  (Might have a go myself!)

---

### Post by quad3d@work on 2008-09-22
I use Xen. Deployed Windows XP and Win2k3 servers guests on host environment without GUI. Works great, good performance with GPLPV drivers.

It's a bit of pain to find which HVM guests is grabbing which VNC ports sometimes, but I agree with others, RDP is the way to go after installation.

---

