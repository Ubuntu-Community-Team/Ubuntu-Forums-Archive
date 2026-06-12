---
title: "VMware Server: Host-only network issue. Used to work."
date: 2010-08-04
forum: Virtualisation
---

### Post by consciousness_of_* on 2010-08-04
[FONT=Arial][FONT=Arial, sans-serif][SIZE=2]The "guest" and the "host" cannot ping each other via the host-only network. All guests can ping each other just fine over the same host-only network. The bridget network also works fine. The host-only network used to work for the host a couple of months ago; ping, samba shares, etc. As far as I can remember, I have not touched the configuration other than regular host security updates and, now, a new kernel.[/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2][COLOR=black]Product: VMware Server 2.0.2-203138.x86_64 [/COLOR][/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2][COLOR=black]Host: Ubuntu 9.10 desktop amd64 / 2.6.31-22-generic, ipv6 disabled[/COLOR], UFW firewall[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]vmnet0 - Bridget, static IP's[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]vmnet1 - Host-only, static IP's, DHCP disabled ("answer VNET_1_DHCP no" in /etc/vmware/locations). [/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]All host-only network traffic is enabled in the UFW firewall and in hosts.allow (just in case). [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]Guests 1 and 2: Debian 5.03 / 2.6.26-2-686, one host-only and one bridget network interface adapter, no firewall.[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]Guest 3: Windows XP SP3, one host-only adapter, firewall disabled. [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]_Host routing table:_ [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Destination Gateway Genmask Flags Metric Ref Use Iface[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]localnet * 255.255.255.0 U 0 0 0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]vmnet * 255.255.255.0 U 0 0 0 vmnet1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]link-local * 255.255.0.0 U 1000 0 0 eth0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]default {my router} 0.0.0.0 UG 100 0 0 eth0 [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]_Guest 1 and 2 routing table:_[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]Destination Gateway Genmask Flags Metric Ref Use Iface[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]localnet * 255.255.255.0 U 0 0 0 eth0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]vmnet * 255.255.255.0 U 0 0 0 eth1[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]default {my router} 0.0.0.0 UG 0 0 0 eth0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]default vmhost 0.0.0.0 UG 0 0 0 eth1 [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]_ifconfig reports zero received packets by the host via the host-only interface:_ [/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]vmnet1 Link encap:AMPR NET/ROM HWaddr[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]inet addr:192.168.201.1 Mask:255.255.255.0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]UP RUNNING MTU:0 Metric:1[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]TX packets:162 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]collisions:0 txqueuelen:0[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]So far I have tried:[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]1) [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]Uninstalling (vmware-uninstall.pl) and re-installing the VMware Server.[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]2) [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]Disabling the UFW firewall.[/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2]Any [FONT=Arial, sans-serif][SIZE=2]troubleshooting [/SIZE][/FONT]ideas? Thank you. [/SIZE][/FONT]
 
 
[FONT=Arial, sans-serif][SIZE=2][FONT=Arial, sans-serif][SIZE=2]I posted the same question on the VMware forums and will cross-reference any successful resolution posted either here or there: [/SIZE][/FONT][http://communities.vmware.com/thread/279060?tstart=0](http://communities.vmware.com/thread/279060?tstart=0)[/SIZE][/FONT]
[/FONT]

---

### Post by consciousness_of_* on 2010-08-11
OK. I will do a clean install of ubuntu 10.04 – time to upgrade – and VMware Server in another partition. Hopefully the issue will go away by itself. Otherwise, I may give VirtualBox a try. I have been playing with it in the past couple of days and it seems a reasonable alternative.

---

