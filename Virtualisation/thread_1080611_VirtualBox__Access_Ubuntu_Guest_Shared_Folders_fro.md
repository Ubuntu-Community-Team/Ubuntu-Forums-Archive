---
title: "VirtualBox :: Access Ubuntu Guest Shared Folders from Win XP Host"
date: 2009-02-25
forum: Virtualisation
---

### Post by marmistead on 2009-02-25
Hi, I'm running Ubuntu 8.10 in VirtualBox 2.1.4 on a WinXP host. It's working great and I have no problem sharing a folders from my host (WinXP) to my guest (ubuntu) using the Shared Folders device built into VirtualBox. I also have no problem accessing the web server (apache) that is on my guest Ubuntu box from my host WinXP computer using the VBoxManage setextradata command and forwarding the ports.

What I want to do though is to share a folder the other direction, from my guest Ubuntu box to access on my host WinXP system. Normally I would use samba but with VirtualBox when if I share a folder on my guest Ubuntu box I cannot see the guest at all on the network of my Windows box.

I'm using the default PCnet-FAST II (NAT) as my network adapter for the Ubuntu guest, if that determines anything. Is there an alternative way to do this?

Any help is greatly appreciated!

---

### Post by Perryg on 2009-02-25
> **marmistead said:**
> Hi, I'm running Ubuntu 8.10 in VirtualBox 2.1.4 on a WinXP host. It's working great and I have no problem sharing a folders from my host (WinXP) to my guest (ubuntu) using the Shared Folders device built into VirtualBox. I also have no problem accessing the web server (apache) that is on my guest Ubuntu box from my host WinXP computer using the VBoxManage setextradata command and forwarding the ports.

What I want to do though is to share a folder the other direction, from my guest Ubuntu box to access on my host WinXP system. Normally I would use samba but with VirtualBox when if I share a folder on my guest Ubuntu box I cannot see the guest at all on the network of my Windows box.

I'm using the default PCnet-FAST II (NAT) as my network adapter for the Ubuntu guest, if that determines anything. Is there an alternative way to do this?

Any help is greatly appreciated!

First you need to have VBox setup with a hosted interface.  Then the two PCs can actually see each other.

Then you should be able to setup your share and access it once you have samba setup to work.  

The only question I have is since you already have a share setup, why do you need another one?  I know that the share on windows is accessible to Ubuntu and the other way around.  Just curious!

---

