---
title: "Guest user on host machine KVM"
date: 2021-04-07
forum: Virtualisation
---

### Post by aljames2 on 2021-04-07
At home I want re-purpose a desktop computer to be the host machine for VM‘s.  The host OS would be MATE.  Currently on this computer is our home ubuntu desktop that my wife and I both use.  I’d like to move this production Ubuntu desktop to a VM.  I think I know how to do all this but my question is how would my wife use the VM desktop without getting confused with the host side of things?  Is there a way when the machine reboots that she could have a separate login straight to the VM without seeing the host stuff?  I suppose I could put a dummy icon on the host desktop that would launch the VM for her.  

I have not seen the virt manager side of things yet to see how the user management stuff works.  Perhaps it’s a trivial thing once I get the host set up with KVM on it?

---

### Post by TheFu on 2021-04-07
Don't let your wife use virt-manager. That's just for admins.  Set her up with a **virt-viewer** link and all the settings needed in a script.  

You could make that script run after the GUI session is started - look for autostart somewhere in the Mate interface.  

I've posted my **virt-viewer** startup files here a few times.  Be certain to setup the QXL video drivers and Spice protocol for access to the VM.  I doubt she'd notice any performance issue, unless she games or needs direct GPU accesss. On the same hardware, hidef video plays back smoothly. On a fast network with fast clients, hidef video plays smoothly over the network on clients too.  However, Spice really wants relatively high speed links, so over the internet, I'd use x2go to connect into her VM.

Spice only works for KVM VMs and is by far the fastest F/LOSS remote/local desktop protocol.  Over a remote connection, it can use ssh tunnels. Locally (VM and host on the same physical machine), it doesn't.

Found it: [https://ubuntuforums.org/showthread.php?t=2453035&p=13997262#post13997262](https://ubuntuforums.org/showthread.php?t=2453035&p=13997262#post13997262)

---

### Post by aljames2 on 2021-04-08
Great, just what I was looking for.  Thanks @TheFu.  Now I have a project this weekend.

---

