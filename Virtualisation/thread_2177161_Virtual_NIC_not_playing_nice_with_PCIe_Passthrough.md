---
title: "Virtual NIC not playing nice with PCIe Passthrough NICs"
date: 2013-09-27
forum: Virtualisation
---

### Post by Tim_Strommen on 2013-09-27
I have a 64-bit Ubuntu Desktop 12.04.3 LTS running as a QEMU/KMV virtualization host on a Tyan Server motherboard.  I only use the machine as a virtualization host, all other functions are handled by 64-bit Ubuntu Server 12.04.3 LTS guest machines - **ALL GUEST MACHINES ARE THIS VERSION**.

I have a Visio diagram of how in general the system is set up, but at 235KB apparently the PDF is too big to upload.  [Here it is on Google Docs]("https://docs.google.com/file/d/0B9nWouV0BQO4SDM0WGNYRUlLdFk/edit?usp=sharing")...

The issue I am having is with one of the guest machines, which I am using as a Shorewall firewall/router.  I have used PCIe passthrough to give a physical "Internet" and "LAN" interface, as well as USB passthrough to allow a 4G failover using a standard USB 4G-LTE modem (Pantech UML290).  That all worked fine.  The trouble started when I added an isolated network to another guest machine for web hosting.  Once I added the Virtual NIC, ALL of the networking stopped functioning.  I tried several combinations, (e1000, virtio, etc... virtual NICs) with various combinations of the PCIe passthrough and every time I have a real NIC with a virtual NIC, all networking ceased to function.

I even went so far as to rebuild the VM twice just to make sure I didn't screw anything obvious up, and I tried doing the networking manually (removing network manager on both the host and guest[s]).

[EDIT:] I should comment that all of the guest machines that are using exclusively virtual NICs to talk to each other (no real hardware passed through) are working perfectly. [/EDIT]

I have searched the forums exhaustively and found nothing that is similar, I've searched KVM and QEMU forums and found nothing.  Even the great and powerfull Google was no help here.

Any ideas?

---

### Post by Tim_Strommen on 2013-12-18
This appears to be a kernel issue with the Ubuntu 12.04 LTS release.

After updating to kernel 3.5.0-42 from 3.5.0-41 the networking began to operate.  However the VM host AND all guest VMs must be at this level - even the ones that didn't have a working network connection.  Building a Host/Guest-VM with the freshest Ubuntu ISO will give you 3.8.0-43 so this is a non issue going forward (good excuse to start clean and not give up).

For this, I did the following starting with my firewall VM:

* Removed all networks and connections from all Guest VMs
* Added a pass-through NIC to an "alive" NIC on the VM host (using default DHCP and NAT)
* Updated the system using the normal apt-get procedure (apt-get update, apt-get upgrade, apt-get dist-upgrade, apt-get autoremove, apt-get autoclean, reboot)
* After the clean reboot, I shut down and removed the pass-through NICs and added back my virtIO NICs
* I ensured that the firewall machine was up and happy with both PCIe pass-through NICs plus the six virtIO NICs, plus the USB pass-through modem
* Rinse, repeat for the other VMs

There is one quirk I noticed after bringing this up, but I think it's a Shorewall firewall issue - the VM-to-VM isolated networks don't pass traffic until there is traffic sent from the Firewall into the respective DMZ(s).  for this I simply send a ping to the machine in the DMZ and the traffic begins to flow.

I'm sure it's a Shorewall thing, but I wanted to put it out there in case it helps someone else!

---

