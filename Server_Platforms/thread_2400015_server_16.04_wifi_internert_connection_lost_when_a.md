---
title: "server 16.04 wifi internert connection lost when assign static ip address to ethernet"
date: 2018-09-01
forum: Server Platforms
---

### Post by pppp.kalagh on 2018-09-01
Hello
I have a specific problem and I searched lots of posts and sites but couldn't find a solution. I even post this question on askUbuntu but i've got no answer. Here is my problem:

  a) My tools.

  
[LIST=1]
[*]I have a laptop (Ubuntu server 16.04 LTS) with one Ethernet and one wifi interface.

[*]I have a PC (both Windows 10 and Linux Mint) with one Ethernet and one USB wifi interface.
[/LIST]
  b) What I want.
  What I want is to connect to the internet both on PC and laptop using  WIFI, and also create a local network between PC and laptop using  Ethernet.
  c) Problem or Issue.

  PC can connect to the internet through WIFI card. The problem is my Ubuntu server. The Ubuntu server is **connected** to the internet through wifi when my setting inside **/etc/network/interfaces** is like this:

  ```
auto wlp18s0b1
iface wlp18s0b1 inet dhcp
wpa-ssid <ssid-name>
wpa-psk <pass>

```  but when I change **/etc/network/interfaces** to assign static ip address to Ethernet, internet connection fails and I can't **ping google.com**. Below is content of **/etc/network/interfaces** which results to WIFI internet connection failure:

  ```
auto wlp18s0b1
iface wlp18s0b1 inet dhcp
wpa-ssid <ssid-name>
wpa-psk <pass>

auto enp19s0
iface enp19s0 inet static
address 192.168.92.6
netmask 255.255.255.0
gateway 192.168.92.1

```  and something else, while second **/etc/network/interface** configuration results in ping google.com to fails. My wifi card is connected to a WIFI hotspot, it only can't reach the internet.

  As a side note, I tried both **ping -I wlp18s0b1 google.com** and **ping google.com.**

  also i tried adding **dns-nameservers 192.168.92.1 **to second configuration but it has no effect too.

Thanks in advance.

---

### Post by TheFu on 2018-09-01
**route -n** when both connections are active would be helpful.  From both systems.

The real key is that the wifi and ethernet shouldn't be on the same subnet.
If the wifi is on a network without any router, then you have to manually create routes between any systems for any IP protocols to work.  Broadcasts might eventually "find" each other, IDK.

---

### Post by volkswagner on 2018-09-01
Remove the gateway from Ethernet. You are creating two default gateways, this is a problem. You especially don't need/want a gateway listed if it's only local traffic anyway.

There's cofigurations to allow multiple gateways, but it's more complex and they both can't be default gateway.

---

### Post by darkod on 2018-09-01
+1 to removing the gateway from the Ethernet connection... As volkswagner says, you don't assign gateway on secondary connections. Since you want local direct traffic between the PC and laptop ethernets, you only need to assign correct static address/netmask values and they will be able to see each other and communicate.

The wifi gateway will remain the primary for all the rest of the traffic.

---

### Post by pppp.kalagh on 2018-09-02
hi
thank you [**[COLOR=#000000]volkswagner[/COLOR]**]("https://ubuntuforums.org/member.php?u=288711") and **darkod**. that was it. once i removed gateway everything worked.

---

