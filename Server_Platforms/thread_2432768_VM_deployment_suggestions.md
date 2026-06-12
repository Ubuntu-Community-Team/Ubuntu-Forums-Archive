---
title: "VM deployment suggestions"
date: 2019-12-08
forum: Server Platforms
---

### Post by aljames2 on 2019-12-08
18.04 LTS storage server.  Mine is running on bare metal, 24/7.  The equipment is strong enough to support virtualization with plenty a ram and CPU power.  I&#8217;d like to move the bare metal server to a virtual machine on this same box.  I&#8217;m looking for suggestions on what flavor Ubuntu the host OS should be, and which VM guest software is best to run the storage server from? KVM integrates straight on the same layer as the kernel but it may be over my head to manage.  Then there is the next layer, VB & VMware?  Open to others.  Thanks again

---

### Post by LHammonds on 2019-12-09
That's the exact same thing I have begun to research.  I have always used ESXi hypervisor and have recently been using Nutanix (KVM-based).  I am helping out a local ISP and he has several servers that has/had Ubuntu installed bare-metal on them.  To save him some cash, I am researching how to install/configure/maintain KVM with Ubuntu Server 18.04.3 LTS as the base host OS for all of his servers.  This should provide adequate utilization of the hardware to provide many VMs that he will need.

I am keeping [my notes here](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=270) as I do my trial-n-error process of learning/documenting.

If I fail at figuring out KVM management, I can always fall back to the free version of ESXi but I won't be able to use the more advanced features in the licensed part such as online vmotion of machines between hosts (which helps with uptime counts)

LHammonds

---

### Post by volkswagner on 2019-12-09
Not to steer you away from Ubuntu, but I've been enjoying Univention corporate server (UCS). 

Their implementation of KVM have a web interface. Downside is virt-manager isn't in their repo. Between virsh and the web interface I'm able to get on just fine.

If you're not interested in LDAP/ADDC it may be Overkill. I know hypervisor's are supposed to be lean, but it's a matter of convenience when considering UCS.

---

### Post by LHammonds on 2019-12-09
> **volkswagner said:**
> Not to steer you away from Ubuntu, but I've been enjoying Univention corporate server (UCS). 

Their implementation of KVM have a web interface. Downside is virt-manager isn't in their repo. Between virsh and the web interface I'm able to get on just fine.

If you're not interested in LDAP/ADDC it may be Overkill. I know hypervisor's are supposed to be lean, but it's a matter of convenience when considering UCS.
I took a quick look at UCS.  It's not really free or at least you need to pay to unlock certain features.

It also seems to operate based deploying turnkey applications which is not something I want to do (the OP's case may be different).  Turnkey apps tend to compartmentalize their apps with their own database and before too long, you have a bunch of separate database servers running rather than just one centralized database server for multiple apps.

Using the command-line is something I actually prefer.  I can create menus/scripts that will ensure VM creation is done in a consistent manner (or at least I hope so).  I just need to make sure I can achieve my posted goals....I'm sure I can if I can figure out how it all works (such as sharing storage between hosts).

LHammonds

---

### Post by aljames2 on 2019-12-10
Thanks for the replies.  I am also going to trial and error a setup and see how it goes.  For starters I am considering using this tutorial to start with to learn some basics of KVM.  [https://www.ostechnix.com/setup-headless-virtualization-server-using-kvm-ubuntu/](https://www.ostechnix.com/setup-headless-virtualization-server-using-kvm-ubuntu/)

---

### Post by TheFu on 2019-12-10
I've been doing virtualization since the 1990s across many different platforms.  If you are limited ot amd64 platforms, the list is a little shorter.
There are basically workstation and server hypervisors.  If this is a toy setup and won't be running 24/7/365, then any solution is fine.  The best for developers is probably VMware Workstation if they want a GUI running on a GUI.  The problem with Workstation is they want their money and will require payment from time to time for newer OSes to work.  VMware player is a toy with limitations.  VirtualBox has a less-than-nice "guest additions license" and will come after you for payment, eventually, as Oracle is finally being left by many clients for their current business practices.

For servers running on servers, there are a few reasonable choices.
* KVM + libvirt + virt-manager
* Xen  + libvirt + virt-manager
* ESXi free, though expect VMware to come for their money eventually.

I've run all of these and more over the decades.  VMware changed their license model in 2010 to be hostile towards existing clients, so we moved ourselves and our clients to different solutions within 6 months, before the current agreements ran out and cost some clients 3x more.  After the outrage, VMware did change their licenses enough to prevent the mass exodus from their software which everyone was planning.

I ran Xen for 3 yrs. It was solid, except about once a year after kernel updates it would refuse to boot guests and I'd have to fall back 1 kernel for 1-2 weeks as the different kernel modules would catch up.

Moved to KVM/QEMU around 2010 on 1 server. After a year of ZERO issues - none - we migrated all our Xen, then ESX VMs over to it.  We have 4 KVM servers running now with no plans to change. They have been rock solid all these years, unless some stupid human trick happens.  We run both Intel and AMD servers with it.  Earlier this year, I migrated about 10 VMs from Intel to a new AMD server. Worked fine. 

We use Ubuntu Server 16.04 as the base for our KVM servers. We have normal server networking w/ 6 NICs connected to multiple networks for internet, management, and storage, but it is non-trivial. I keep seeing issues with netplan, so we've delayed moving to 18.04 and will probably skip it completely. Netplan might handle it fine, but even 2 weeks ago a fresh 18.04 install with a single static IP setup during the install failed, so I'm not impressed with netplan.

If you are 100% committed to running only VMs on the server(s), there is **proxmox**. It takes over the entire server and provides a web interface into the VM setup and management. Underneath, it uses KVM and Docker, I think.  It has an idea of clustering, which I've not tried.  

I would more likely use Ubuntu Server with sheepdog as back-end storage spreading the replication across all the nodes so any failures could automatically fail over the running VM to a different node - this is a KVM capability, but with this extra power, you'll need better Linux admin skills.  LHammonds would easily accomplish this. I wouldn't bet on someone new to virtualization with shaky other admin skills would get it working.

The great thing about virt-manager is that it allows control of VM management, installation, from a remote workstation with built-in ssh tunnels.  Setup ssh with keys like normal, and have libvirt installed on both the remote server and the local workstation with virt-manager and you are golden.

I've never used virt-install.  Multipass seems interesting, but since it is only provided as a snap, it is out of consideration here.

My bit tip for using KVM or Xen is to manually setup any needed bridges outside the VM management tools.  If you have 10Gbps networking, you'll want to use openswitch. For GigE networking, the normal Linux bridges are fine.  There are all sorts of tips for PCI passthru of NICs to VMs, if you need that added security.

---

