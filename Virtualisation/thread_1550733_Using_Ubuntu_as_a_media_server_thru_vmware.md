---
title: "Using Ubuntu as a media server thru vmware"
date: 2010-08-11
forum: Virtualisation
---

### Post by Gr3ghammett on 2010-08-11
On my server machine, for paticular reasons, i had to switch from having Ubuntu as my host OS to having Windows 7 be the host os instead, and running my Ubuntu OS in VMware.

     What I'm wanting to do is use my Ubuntu Virtual Machine to run as my Media Server for the network again through VMware.  Is that even possible? and what is the best way for me to set that up with only one ethernet interface that's shared between my host and guest os?

---

### Post by TheFu on 2010-08-11
If you are just looking to share media via SAMBA or DLNA, then sure, you can use almost any Linux distro in a VM. MediaTomb and miniDLNA work as does SAMBA. I tend to use samba/SMB shares since they are easier to work with for my playback devices. I suspect many of the other *non-recording* media center solutions will work fine. However, some of the newest releases to these tools have higher graphics card requirements than is supported by VMs, so you'll want to do a little research.  XBMC lists OpenGL 2.x as a requirement. I don't know if that is supported in VMs.

If you are looking to hook up any TV recording device (USB or PCI card), then I think you'll want to use the hostOS for recording.

---

### Post by Gr3ghammett on 2010-08-11
cool i'll give it a shot and let you know.  dont plan on doing any tv recording, just media streaming and sharing.  i've used the built in *right click folder, share* deal, and the host os picks it up, but no one else in the network does. i'll try mediatomb and samba first and see if that helps. also i've disabled nat and have given the vmmachine it's own ip in my router based off it's unique mac.

---

### Post by TheFu on 2010-08-16
> **Gr3ghammett said:**
> cool i'll give it a shot and let you know.  dont plan on doing any tv recording, just media streaming and sharing.  i've used the built in *right click folder, share* deal, and the host os picks it up, but no one else in the network does. i'll try mediatomb and samba first and see if that helps. also i've disabled nat and have given the vmmachine it's own ip in my router based off it's unique mac.

Great!  You need to be certain that bridging and firewalls are setup where the VM client OS can be accessed by other physical machines on the network that are not on the same physical machine. If it doesn't "just work", that's where I'd check first for some issue.

---

