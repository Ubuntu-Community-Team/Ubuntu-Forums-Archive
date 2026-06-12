---
title: "Suggestions for KVM manager?"
date: 2020-02-13
forum: Virtualisation
---

### Post by mn1247 on 2020-02-13
I have a home server based on Ubuntu18.04 and KVM.  Currently, I manage it from a Macintosh laptop using libvirt (virt-manager) via VNC.  I'm wondering if there are better solutions for this.  For example, I looked at Kimchi (web-based) and it seemed excellent, but I could not get it to run correctly on Ubuntu (it appears to want CentOS or similar).  

Any other (free and open-source) useful management utilities I could install?  

Thanks
Eric

---

### Post by TheFu on 2020-02-13
Use **virsh**. It is already on the system.

If the server is dedicated to virtual machines, you might like **proxmox**.
If you go with CentOS or RHEL, there is **oVirt**, though it is for a larger installation normally.

Being stuck using OSX really takes away from the network based management of VMs. If your workstation was an Ubuntu Desktop, VNC  wouldn't get in the way and you wouldn't have any security issues common with VNC/RDP solutions.  libvirt expects ssh to be used from virt-manager into the VM host.  
Or you can use **x2go**. That should work from a Mac.  Best to avoid VNC, always.

---

### Post by kevdog on 2020-02-14
Honestly is your server is dedicated to virtual machines, I prefer Xen or xcp-ng over Proxmox.  I realized that Proxmox is based on KVM and that might be what your used to using, however in all honestly if you are new to using hypervisors, proxmox's documentation is limited and questions on their forums take forever to answer.  It's really frustrating to a user where maybe you are used to getting questions answered quicker.  Another problem I found was many of the proposed answers may be applicable to older versions of Proxmox, and the problem described was fixed in later releases.  Oh course there really is no way to know the problem was fixed with later releases since there isn't really a followup explanation in the thread saying -- problem fixed with xx.xx.xx release.  

Xen orchestra does a great job of managing xcp-ng, and in fact with Xen-orchestra you can manage hypervisor clusters if needbe.  There is a built-in console for each running VM, so within the console you would login as if you were at the command line, so its totally possible to be presented with a GUI if needed.  It's similar to the VM interface used with FreeNAS.   

x2go isn't a bad option as well, however sometimes its nice to have a central management console rather than a bunch of open x2go windows if you are managing multiple hosts.

---

### Post by TheFu on 2020-02-14
I never use more than one x2go connection.  It is only to connect to my desktop, not servers.  I do have a number of ssh connections active from that desktop to many servers.  Some people use tmux for a similar purpose.

Of course, most server management is really done using ansible or clusterssh, but sometimes a quick ssh to deal with a tiny, specific issue is best.

I've always avoided web-based VM interfaces for security reasons.

---

