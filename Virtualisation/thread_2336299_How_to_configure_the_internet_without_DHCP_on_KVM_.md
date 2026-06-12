---
title: "How to configure the internet without DHCP on KVM Ubuntu Server 16.04 VM"
date: 2016-09-06
forum: Virtualisation
---

### Post by fromwin2lin on 2016-09-06
[FONT=Verdana]Here's what I'm trying to tell you: I installed Ubuntu server 16.04 on a vm. The setup wanted my to connect to one of my virtual networks with DHCP. My virtual network does not have DHCP. So, I selected "Do not configure the network". Ubuntu finished installing. No internet!!!!! How do i connect to one of my Virtual networks without DHCP??? My hypervisor is KVM.[/FONT]

---

### Post by wildmanne39 on 2016-09-06
*Thread moved to **Virtualisation**.*

---

### Post by heiko_s on 2016-09-07
AFAIK the network manager can also take static IP addresses. Unfortunately I use Linux Mint (based on Ubuntu) and I'm using the /etc/network/interfaces file for a static network configuration. I've written a tutorial over at the Linux Mint forum, but it should work with Ubuntu as well. Have a look at [https://forums.linuxmint.com/viewtopic.php?f=231&t=112013#p628768]("https://forums.linuxmint.com/viewtopic.php?f=231&t=112013#p628768").

Hope its useful.

---

### Post by TheFu on 2016-09-07
Ubuntu server doesn't use network manager, to my knowledge.  You'll need to edit the /etc/network/interface file. The manpage has examples.
However, you'll also need for the VM host to have Linux bridging installed, enabled, and configured.  This is NOT automatic. The automatic methods only provide NAT subnets to client-VMs. An example from a VM guest:
```
$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 10.22.22.11
  gateway 10.22.22.1
  netmask 255.255.255.0
  dns-nameservers 10.22.22.254

```
Obviously, the subnet, netmask, IP and device will need to be changed for your setup.

So - do you have bridging already setup on the host machine? The command is:
**$ brctl show**

I should point out that I don't have **any** 16.04 KVM hosts, so if anything changed from 14.04, then things could be different. I haven't heard of anything changing.  16.04 is just a little too new for our tastes still.

---

### Post by heiko_s on 2016-09-07
@TheFu: Thanks for pointing out that Ubuntu server doesn't use network manager - one headache less!

About the bridge: I'm under the assumption that the OP is running Ubuntu server in a VM. Inside the VM he/she doesn't need to configure the bridge. It's done in the host.

---

### Post by TheFu on 2016-09-07
I've never seen automatic bridges setup on a host that weren't NAT'd.  I tried to be very clear about host/guest networking above.

I don't really use desktop distros. Learn how to do things the server-way and it always works.  Just purge nano, network-manager* and any bloated GUI(s) that may be loaded. ;)  NM just gets in the way if there are non-trivial network needs.

---

### Post by fromwin2lin on 2016-09-07
> **heiko_s said:**
> @TheFu: Thanks for pointing out that Ubuntu server doesn't use network manager - one headache less!

About the bridge: I'm under the assumption that the OP is running Ubuntu server in a VM. Inside the VM he/she doesn't need to configure the bridge. It's done in the host.


Here's what I'm trying to tell you: I installed Ubuntu server on a vm. The setup wanted my to connect to one of my virtual networks with DHCP. My virtual network does not have DHCP. So, I selected "Do not configure the netwrok". Ubuntu finished installing. No internet!!!!! How do i connect to one of my Virtual networks without DHCP???

---

### Post by TheFu on 2016-09-07
Please re-re-review post #4 above.  Please post the output of the commands and contents of the files referenced.
We cannot help without any data.

---

### Post by fromwin2lin on 2016-09-07
> **TheFu said:**
> Please re-re-review post #4 above.  Please post the output of the commands and contents of the files referenced.
We cannot help without any data.

Here is the output: 

# The loopback network interface
auto lo
iface lo inet loopback

Like I said, I didn't configure the internet during the setup. There should be at least one eth device on the list. But since my virtual network had no DHCP, ubuntu refused to configure my virtual network during install.

---

### Post by TheFu on 2016-09-07
And the bridge for the hostOS?  Did you configure that?
[http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking) has some hints and steps.

On the VM-guest side, using the **interfaces** file posted above as a template, please make yours with the required changes to the settings.  Your network admin should provide the IP address, netmask, gateway ...  You will need to determine the ethernet device to be used.  Check **dmesg** output for that.  [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) has the official server guide steps.

In short, if you don't have DHCP on the network, then you **must** use static IPs.

---

