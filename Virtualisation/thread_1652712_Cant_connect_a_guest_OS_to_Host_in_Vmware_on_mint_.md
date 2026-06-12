---
title: "Cant connect a guest OS to Host in Vmware on mint 9"
date: 2010-12-25
forum: Virtualisation
---

### Post by kunwar.tej on 2010-12-25
Hi every one . I am having problem in connecting my virtual machines with my host OS that is linux mint 9 .Two days ago every thing was working fine but now it just does not work. I am using host only Networking. As  guest operating systems i am having windows XP SP3 and linux mint 10. Both virtual machines are able to ping each other but they just cant ping the host and neither the host pings them...Please help. Thanks in advance.

---

### Post by HermanAB on 2010-12-26
Howdy,

My guess is that your host is plugged into a home router and that it changed your network settings via DHCP.

Check everything with 'ifconfig' and 'route'.

---

### Post by kunwar.tej on 2010-12-27
Hi there thanx for respone .Please let me inform u that i am not using DHCP from the vmware Network editor .Also using route -n i find that corect ip range is assigned for all my machines. For example , host has 172.16.119.1
and rest all my virtual machines have ip range from 172.16.119.2 to 172.16.119.16 . i am using host only connection .And also i am not using any router. The interesting thing is that same virtual machines work perfectly fine on windows 7.

---

