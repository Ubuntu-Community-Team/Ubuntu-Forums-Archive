---
title: "Bridged network in virtual box doesn't work with lubuntu"
date: 2017-06-21
forum: Virtualisation
---

### Post by bforbit on 2017-06-21
[COLOR=#111111][FONT=Ubuntu]I have imported an Ubuntu system (Lubuntu) in VirtualBox and setted Bridged network in the settings of Virtual Machine but it can't still connect to the web. If I try to ping my router it returns "Host Unreachable" but in his ARP cache (of router) the ip of vm appears. With NAT settings instead it works fine.. Can anyone help me?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Another thing to note is that in ARP cache of router the MAC address of the virtual system is same as the host but if I use "ip a" command (in vm) the MAC is different. My host system is Windows 8.1[/FONT][/COLOR]

---

### Post by HermanAB on 2017-06-22
A bridged system works exactly the same as a standalone system.  So, use 'ifconfig' to see the name of the interface e.g 'eth0', and use 'dhclient eht0' to get an IP address from your router.  You can simultaneously run 'tcpdump -nlX -i eth0' to see what is happening.

---

### Post by bforbit on 2017-06-22
I have already an IP address, it is assigned by my router (dhcp), so my vm is in my lan but i cannot communicate with other systems. I can only successfully ping my host PC and vice versa.
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by efflandt on 2017-06-24
Strange that your vbox guest gets a dhcp assigned IP from your router, but cannot connect to your router. Do you see you router's LAN IP (as UG flag) if in a terminal you do: **route -n**

Note that even when it does work, anything on the LAN would see the physical MAC of the host for your vbox guest IP, since LAN connections use arp to then connect directly to the MAC address. Something similar happens when I used a router in "wireless client bridge mode", my DSL gateway and LAN would see MAC of the bridged router, not MAC addresses behind it. I have never run virtualbox in Windows, but I know that with a Linux host, the IP of a bridged guest does not show up in "ifconfig", so it probably does not show up in "ipconfig /all" of a Windows host either.

Maybe your issue has something to do with Windows' firewall or other 3rd party security software.

---

