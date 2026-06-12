---
title: "VMware Connect to Internet over Ubuntu"
date: 2011-05-22
forum: Virtualisation
---

### Post by xanbkn on 2011-05-22
Hello everyone, I have a minor problem with VMWare Player 3.  After downloading 64-bit Ubuntu 11.04 and trying to install it, I get a message saying "Could not connect Ethernet0 to virtual network "VMnet8". More information can be found in the vmware.log file.
Failed to connect virtual device Ethernet0." Regardless of Host-only, NAT, or Bridged connections, it doesn't work!

On vmware.log, I found:

May 22 13:51:10.963: vmx| DICT         ethernet0.present = TRUE
May 22 13:51:10.963: vmx| DICT  ethernet0.connectionType = nat
May 22 13:51:10.963: vmx| DICT      ethernet0.virtualDev = e1000
May 22 13:51:10.963: vmx| DICT   ethernet0.wakeOnPcktRcv = FALSE
May 22 13:51:10.963: vmx| DICT     ethernet0.addressType = generated

and

May 22 13:51:12.558: vmx| Ethernet0 MAC Address: 00:0c:29:20:93:f0

and finally

May 22 13:51:12.744: vcpu-0| VNET: MACVNetPort_Connect: Ethernet0: can't open vmnet device (997)
May 22 13:51:12.744: vcpu-0| Msg_Post: Warning
May 22 13:51:12.744: vcpu-0| [msg.vnet.connectvnet] Could not connect Ethernet0 to virtual network "VMnet8". More information can be found in the vmware.log file.
May 22 13:51:12.744: vcpu-0| [msg.device.startdisconnected] Virtual device Ethernet0 will start disconnected.

Any help would be appreciated!

Thanks, 

XanBKN

---

### Post by fjgaude on 2011-05-22
Ubuntu is installed as the host?

You have a 64-bit CPU? You installed VMware Player 3.1.4?

Do you have more than one NIC?

In NAT I believe Player should be connected to eth0, and not vmnet8 or vmnet1.

---

### Post by xanbkn on 2011-05-28
Wait--I got it!  Upgrading to the newest version of Player fixed my problem.  Just goes to show you, when in doubt, upgrade software.

Thanks,

XanBKN

---

