---
title: "Network adapters in Virtualbox"
date: 2012-05-11
forum: Virtualisation
---

### Post by RAND0M1ZER on 2012-05-11
I'm trying to set up a pfSense router in VirtualBox and I'm having trouble figuring out how to configure the host network adapters. 

-The computer has 2 Intel NICs
-em0 (LAN) and em1 (WAN)

Before I switched my server to Ubuntu I was running pfSense in VirtualBox on Windows so I know it can be done fairly easily but what is stumping me is how to configure the host's interfaces.

Currently my /etc/network/interfaces looks like this:
[PHP]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
[/PHP]

And my VM was configured using phpvirtualbox which I attached screenshots for.

Based on a few guides like [this]("http://definitelynotanerd.com/2012/04/pfsense-as-a-wifi-access-point-in-virtualbox-on-osx/") one and the documentation on [adapter networking modes]("http://www.virtualbox.org/manual/ch06.html#networkingmodes") it seems like bridge mode for both would be the easiest.

---

### Post by RAND0M1ZER on 2012-05-13
Anyone? The error I'm getting now is:

[PHP]
administrator@Server:/$ VBoxManage startvm pfsense --type headless
Waiting for VM "pfsense" to power on...
VBoxManage: error: Failed to open/create the internal network 'HostInterfaceNetworking-eth0' (you might need to modprobe vboxnetflt to make it accessible) (VERR_PERMISSION_DENIED).
VBoxManage: error: Failed to attach the network LUN (VERR_PERMISSION_DENIED)
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component Console, interface IConsole, callee
[/PHP]

I added administrator to the vmboxusers group and I know it worked correctly because :
[PHP]

administrator@Server:/$ cat /etc/group
vboxusers:x:119:administrator
[/PHP]

I only get this problem when I use bridged interfaces.

---

### Post by markbl on 2012-05-13
> **RAND0M1ZER said:**
> 
I added administrator to the vmboxusers group and I know it worked correctly because :
[PHP]
administrator@Server:/$ cat /etc/group
vboxusers:x:119:administrator
[/PHP]

You only have that 1 line in your /etc/group? I suspect that output is actually from "grep vbox /etc/group"?

Anyway, you have to log out/in for group changes to have effect.

---

### Post by RAND0M1ZER on 2012-05-13
> **markbl said:**
> You only have that 1 line in your /etc/group? I suspect that output is actually from "grep vbox /etc/group"?

Anyway, you have to log out/in for group changes to have effect.

No, there's several groups actually I just put that one to save space and I've rebooted several times so I don't think its that.

But I think I've narrowed down the problem a bit more to the vboxnetflt service. When I reboot the machine it says
[PHP]cannot unload vboxnetflt[/PHP]

Also when I run
[PHP]/etc/init.d/vboxnetflt setup[/PHP]
it fails

---

