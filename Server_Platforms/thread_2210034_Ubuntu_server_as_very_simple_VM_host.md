---
title: "Ubuntu server as very simple VM host"
date: 2014-03-08
forum: Server Platforms
---

### Post by smeerbartje on 2014-03-08
I'm planning to buy new hardware for my little home server. Now I want to make this server be my router (dual NIC, IPTABLES), samba share, LAMP, Bittorrent Sync client, etc. I also want to use it as a very simple host for one or two virtual machines. Now my questions are:
[LIST=1]
[*]What software is available for ubuntu? About five years ago I experimented with vmware, but what is the default nowadays?
[*]Do I need special hardware requirements for this?
[*]
[/LIST]
As said above: I'm planning to run one or two virtual machines on the Ubuntu server (as host). Nothing special, maybe a Windows 7 and maybe a Ubuntu desktop.

---

### Post by nerdtron on 2014-03-09
Your computer CPU should support Virtualization technology. Almost all modern processors support this. Also, you should have enough RAM on you server to run the virtual machines at least 4GB-6GB.
Then you need to install packages on your server for virtualization such as the KVM packages.
See this tutorial for managing virtual machines. [http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)
Using Ubuntu virtual machine manager, you can manage the virtual machines of your server from you ubuntu desktop computer without the need for complex codes in creating virtual machines.

---

### Post by smeerbartje on 2014-03-09
Thanks big time! Very helpfull! However one additional question: is there also a Mac client available to access the Virtual Machines running on my (headless) Ubuntu server?

---

### Post by nerdtron on 2014-03-09
I don't know of any. I'm using Ubuntu desktop for controlling the VMs in the headless Ubuntu server.

---

### Post by sandyd on 2014-03-09
> **smeerbartje said:**
> I'm planning to buy new hardware for my little home server. Now I want to make this server be my router (dual NIC, IPTABLES), samba share, LAMP, Bittorrent Sync client, etc. I also want to use it as a very simple host for one or two virtual machines. Now my questions are:
[LIST=1]
[*]What software is available for ubuntu? About five years ago I experimented with vmware, but what is the default nowadays?
[*]Do I need special hardware requirements for this?
[*]
[/LIST]
As said above: I'm planning to run one or two virtual machines on the Ubuntu server (as host). Nothing special, maybe a Windows 7 and maybe a Ubuntu desktop.

I would suggest virt-manager+qemu (KVM)
You can easily then run virt-manager (gui) and manage the VMs from there.

If you want to setup a _full_ virtual machine host, try Proxmox (which has a nice online interface where you can configure and open a VNC console into your VMs)

---

### Post by smeerbartje on 2014-03-10
Thanks; will have a look at it.

---

