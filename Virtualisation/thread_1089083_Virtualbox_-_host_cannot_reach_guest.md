---
title: "Virtualbox - host cannot reach guest"
date: 2009-03-06
forum: Virtualisation
---

### Post by BrownieBoy on 2009-03-06
I've setup an XP guest on a Ubuntu Intrepid host using VirtualBox 2.1.4 (closed-source version).  I want to use that XP guest as a web server.  Only the host needs to access it at present.

I followed the instructions for Host Interface Networking in section 6.5 of the VirtualBox User Manual, namely:

"to enable Host Interface Networking, all you need to do is to open the Settings dialog of a virtual machine, go to the &#8220;Network&#8221; page and select
&#8220;Host Interface&#8221; in the drop down list for the &#8220;Attached to&#8221; field. Finally, select desired host interface from the list at the bottom of the page, which contains the physical network interfaces of your systems".

It's working in that the XP guest has internet access and it can ping the Ubuntu host (IP 192.168.1.1).  However, the host cannot ping the XP guest (IP 192.168.1.6).  Is there something else that I need to do?

Output for ipconfig on the XP guest:
IP Address. . . . . . . . . . . . : 192.168.1.6
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.254

Output for ifconfig on the Ubuntu host (eth1 is my network card):
eth1      Link encap:Ethernet  HWaddr 00:11:d8:cd:98:73  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fecd:9873/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34562438 (34.5 MB)  TX bytes:3361239 (3.3 MB)
          Interrupt:17

---

### Post by BrownieBoy on 2009-03-07
Doh!

Windows Firewall on the guest was preventing the ping response from the host.  I didn't even realise I had it running there.

---

