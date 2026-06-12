---
title: "how to start recovery mode for Ubuntu Server 18.04.3 LTS when connecting through SSH?"
date: 2020-05-24
forum: Server Platforms
---

### Post by natiya2 on 2020-05-24
[COLOR=#242729][FONT=Arial]I have a virtual machine running Ubuntu Server 18.04.3 LTS and I need to modify some settings using the recovery Mode. I have to connect through a VPN using SSH (Putty), so I'm not sure what the sequence would be to do this, as I think if I restart it, I'll loose the connection in Putty, right?[/FONT][/COLOR]

---

### Post by TheFu on 2020-05-24
> **natiya2 said:**
> [COLOR=#242729][FONT=Arial]I have a virtual machine running Ubuntu Server 18.04.3 LTS and I need to modify some settings using the recovery Mode. I have to connect through a VPN using SSH (Putty), so I'm not sure what the sequence would be to do this, as I think if I restart it, I'll loose the connection in Putty, right?[/FONT][/COLOR]

You need console access to the VM.  Depending on the hypervisor, that shouldn't be hard.  The console access is provided from the hostOS via virsh or using a gui like virt-manager if you use KVM.  virt-manager connects from anywhere the client machine has ssh access to the VM-host.

For physical servers, many support ipmi or drac or riblo cards.

---

