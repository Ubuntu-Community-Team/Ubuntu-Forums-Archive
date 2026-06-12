---
title: "edubuntu ltsp 14.04 as host and windows 8.1 vm"
date: 2014-10-18
forum: Virtualisation
---

### Post by pe1992ter on 2014-10-18
i have installed edubuntu and windows 8.1 in virtualbox. the guest can ping the host and connect to the internet but ubuntu can't ping guest i have disabled firewall as well as looked online and added rules to iptables to allow ping but with no use. please help your help is greatly apperciated

---

### Post by bashiergui on 2014-10-18
Depending on the networking option you chose for the guest, you will use the IP on different interfaces for the host. Is the guest using bridged or NAT?[https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes)

---

### Post by pe1992ter on 2014-10-18
thanks bashiergui for your reply. so i tried bridged network the host and guest couldn't ping each others so i tried Nat and the output was vm can ping host but host can't ping the vm. 
from the vm i can ping eth0 and wlan0 but from host i can't ping vm at all it says host unreachable.

that's the output of ifconfig (host)

eth0      Link encap:Ethernet  HWaddr 84:34:97:84:8f:88  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:876324 (876.3 KB)  TX bytes:876324 (876.3 KB)

wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:81:ad:f3  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::86a6:c8ff:fe81:adf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26186906 (26.1 MB)  TX bytes:6418923 (6.4 MB)


the output of ipconfig (guest VM)

ipv4 10.0.3.15
subnet mask 255.255.255.0
Default gateway. 10.0.3.2

please let me know if there is more info you need to see. your help is much apperciated

---

### Post by bashiergui on 2014-10-18
> ipv4 10.0.3.15
subnet mask 255.255.255.0
Default gateway. 10.0.3.2Okay so if you choose NAT, then what that does is turn your host into the guest's router. That would make the host = 10.0.3.2 as far as the guest knows. The guest can't find the host on the 192.168 subnet because the guest isn't on that subnet and can't have any way to know it exists. 

if you choose to bridge the guest, then both the guest and host will use your router as their gateway. That means they would both be on the 192.168 subnet. And if they ping each other's 192.168.0.X address, they would be able to find each other. If they can't then you must have ICMP blocked on the router, host, and/or guest.

---

### Post by pe1992ter on 2014-10-18
here is the output of my iptables 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


i have tried bridged before i will attach a screen shot as well

---

### Post by pe1992ter on 2014-10-18
here is the screen shot in the following link please advice with the soultion your help is reallt apperciated
[URL="http://www.mediafire.com/view/69l59xgqua2lhvu/Screenshot_from_2014-10-18_221857.png"]
[www.mediafire.com/view/69l59xgqua2lhvu/Screenshot_from_2014-10-18_221857.png](www.mediafire.com/view/69l59xgqua2lhvu/Screenshot_from_2014-10-18_221857.png)


[/URL]

---

### Post by bashiergui on 2014-10-20
From the link I gave you > There are four limitations of NAT mode which users should be aware of:ICMP protocol limitations:Some frequently used network debugging tools (e.g. ping or tracerouting) rely on the ICMP protocol for sending/receiving messages. While ICMP support has been improved with VirtualBox 2.1 (ping should now work), some other tools may not work reliably.Can you ftp or telnet or ssh between host and guest? Try to connect with some service that uses TCP. That way we can determine if it's networking or ICMP that's broken.

---

