---
title: "Passing a VPN connection through the Host OS to a HostOnly network"
date: 2011-10-21
forum: Virtualisation
---

### Post by tonysathre on 2011-10-21
I'm running VMware Server on Windows Server 2003. I have numerous Linux VMs running on top of VMware Server in a lab environment and would like to setup an OpenVPN connection to access only the VMs and the virtual network VMnet8 that all the VMs reside on. I do not want access to the rest of my physical network if at all possible. Is this possible and if so, how would I go about setting it up? Thanks.

---

### Post by dcstar on 2011-10-27
> **tonysathre said:**
> I'm running VMware Server on Windows Server 2003. I have numerous Linux VMs running on top of VMware Server in a lab environment and would like to setup an OpenVPN connection to access only the VMs and the virtual network VMnet8 that all the VMs reside on. I do not want access to the rest of my physical network if at all possible. Is this possible and if so, how would I go about setting it up? Thanks.

Add a separate network card and let the VMs have access to it.

---

### Post by tonysathre on 2011-10-27
Yep. I found this guide on how to do it.

[https://community.rapid7.com/community/infosec/blog/2011/01/05/how-to-set-up-a-pentesting-lab](https://community.rapid7.com/community/infosec/blog/2011/01/05/how-to-set-up-a-pentesting-lab)

---

