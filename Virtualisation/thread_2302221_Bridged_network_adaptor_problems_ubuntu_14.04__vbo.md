---
title: "Bridged network adaptor problems ubuntu 14.04 / vbox"
date: 2015-11-08
forum: Virtualisation
---

### Post by snobskidoo on 2015-11-08
Dear all,

I am struggling to get my VMs online via bridged network adaptors since upgrading my server from 12.04 to 14.04. The host machine runs smoothly and can ping everything / connect / etc, but each of the VMs can only ping localhost but not the router or other computers (destination host unreachable). The router shows the static IP addresses as attached in the router settings, but without the hostname. The host machine has two network interfaces, but as far as I can see all goes through eth0. All machines are headless. I can connect to the VMs via the remote desktop interface, but not via SSH. All guests have vbox guest additions installed. 

The host is currently ubuntu 14.04, with virtualbox 5.0.8 managed via phpvirtualbox. 

Here is some output from the guest (ubuntu 12.04), which is unable to connect:

[ATTACH=CONFIG]265433[/ATTACH][ATTACH=CONFIG]265434[/ATTACH][ATTACH=CONFIG]265435[/ATTACH]

Can you please help me find out where I've gone wrong?

---

### Post by snobskidoo on 2015-11-09
On host here is output of "VBoxManage list bridgedifs"

 VBoxManage list bridgedifs
Name:            eth0
GUID:            30687465-0000-4000-8000-74d435ef7b3f
DHCP:            Disabled
IPAddress:       192.168.0.13
NetworkMask:     255.255.255.0
IPV6Address:     fe80:0000:0000:0000:76d4:35ff:feef:7b3f
IPV6NetworkMaskPrefixLength: 64
HardwareAddress: 74:d4:35:ef:7b:3f
MediumType:      Ethernet
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-eth0

Name:            eth1
GUID:            31687465-0000-4000-8000-74d435ef7b3d
DHCP:            Disabled
IPAddress:       0.0.0.0
NetworkMask:     0.0.0.0
IPV6Address:
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: 74:d4:35:ef:7b:3d
MediumType:      Ethernet
Status:          Down
VBoxNetworkName: HostInterfaceNetworking-eth1

Name:            wlan0
GUID:            6e616c77-0030-4000-8000-a0a8cdc5c16e
DHCP:            Disabled
IPAddress:       0.0.0.0
NetworkMask:     0.0.0.0
IPV6Address:
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: a0:a8:cd:c5:c1:6e
MediumType:      Ethernet
Status:          Down
VBoxNetworkName: HostInterfaceNetworking-wlan0

---

### Post by SeijiSensei on 2015-11-10
As a guess, you probably don't have a default gateway specified.  Did you configure eth0 in /etc/network/interfaces?  Do you have a "gateway" directive, probably one that points to 192.168.0.1 if that's your router's address?

The VirtualBox manager application is very easy to use.  I don't see any reason to use some PHP-based application to manage them if you have physical access to the host.  If the host is only available over the network, and it has a GUI interface, you can manage the VMs remotely by enabling X forwarding in SSH.  You can log in with "ssh -X user@host" then run the graphical manager on the remote machine from the command prompt.  The program will appear on your local desktop.

---

### Post by snobskidoo on 2015-11-10
Thanks for your reply - the /etc/network/interfaces is configured for static IP on the host and all VMs with the gateway/network/broadcast/DNS/netmask settings (as you can see above in the host images) and "route -n" reports that that is where it is trying to go.

My machine is completely headless with no X-server install so I presume X-forwarding won't work - hence the php based access.  I am reasonably comfortable working via SSH and the command line, but use some web-based tools for some things and have webmin installed.

Thanks again

---

