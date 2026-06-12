---
title: "VirtualBox - Can't ping guests"
date: 2011-06-17
forum: Virtualisation
---

### Post by HorseBox on 2011-06-17
I installed a Windows 7 guest on my Ubuntu host and initially it was on its own subnet (10.0.2.15) so I went into Settings > Network then changed NAT to Bridged Adapter so now the guest seems to be on the same subnet as the host (it has the IP 192.168.1.13 and my host is 192.168.1.17) and I can ping the host from the guest but when I try to ping the guest from the host it doesn't detect any live host on 192.168.1.13. I tried port scanning it with nmap too but nmap couldn't detect it either. I followed this tutorial:
[http://riethorst.net/phpmyfaq/index.php?action=artikel&cat=29&id=96&artlang=en](http://riethorst.net/phpmyfaq/index.php?action=artikel&cat=29&id=96&artlang=en)
and according to that tutorial I should be able to detect the Windows 7 guest on my LAN now but 192.168.1.13 isn't responding to pings or any nmap scans. Does that mean its not actually on the same subnet?

---

### Post by lmarmisa on 2011-06-17
Your problem seems related to the firewall of Windows 7. Check if the answers to the ping requests are disabled.

---

### Post by emiller12345 on 2011-06-17
Give this a try from the Ubuntu host to the Win7 Guest...
```
$ arping -I $UBUNTU_INTERFACE -c 1 192.168.1.13
```arp is quite a low level protocol, it might get through

---

### Post by HorseBox on 2011-06-18
lmarmisa: I didn't configure the firewall at all, I literally installed the Windows 7 guest, got it onto my subnet then tried pinging it. I can't imagine Win7 blocking pings by default. I'll check though. 

emiller12345: heres what happened when I ran that command:
```
$ arping -I eth0 -c 1 192.168.1.13
WARNING: interface is ignored: Operation not permitted
ARPING 192.168.1.13 from 192.168.1.17 eth0
Unicast reply from 192.168.1.13 [08:00:27:40:77:93]  0.982ms
Sent 1 probes (1 broadcast(s))
Received 1 response(s)

```so its responding to ARP but not ICMP? I'm watching what wireshark captures when I ping 192.168.1.3 and plenty of these come up:
[IMG]http://img857.imageshack.us/img857/9531/pings.png[/IMG]
I don't know too much about TCP/IP so I don't know what to make of it but wireshark is picking up plenty of packets coming from 192.168.1.13. Loads of SSDP packets what ever they are. Strangely enough wireshark captures packets from 2 other IP's 192.168.1.3 and 192.168.1.12, they might be the other laptops in the house but when I do a ping sweep with fping the only live host it identifies is me.

EDIT: I installed wireshark on the windows host and pinged it and heres what it sniffed:
[IMG]http://img713.imageshack.us/img713/8012/ping2n.png[/IMG]
so it is receiving to the pings and responding to them. Would I be right in assuming it has to be the ubuntu host thats ignoring the pings? Ah **** now I remember, I configured firestarter to not allow "Echo reply (pong)" in ICMP filtering, I thought that meant it would stop my computer from replying to pings in order to make myself invisible to ping sweeps. Instead it was blocking replies from computers I ping. That was pretty stupid on my part lol. 

A quick side question: I notice that the windows guest has a different MAC address to my ethernet cards MAC address. Do VM's use virtual network interfaces or something?

---

### Post by Dedoimedo on 2011-06-18
Yes, virtual adapters.
Dedoimedo

---

### Post by emiller12345 on 2011-06-18
> **HorseBox said:**
> 
I don't know too much about TCP/IP so I don't know what to make of it but wireshark is picking up plenty of packets coming from 192.168.1.13. Loads of SSDP packets what ever they are. 
Simple Service Discovery Protocol (SSDP) packets are apart of Windows' Universal Plug and Play (UPnP) 
If you don't need UPnP/SSDP you can disable it.  I found this from 
hxxps://kb.berkeley.edu/jivekb/entry.jspa?entryID=2455
It looks about right I think. Generally speaking, I dislike the unnecessary use of open ports.
```

To manually disable UPnP/**SSDP** in **Windows** 2000/XP/Vista: 
 
[LIST]
[*]Go to Start Menu-->Run...
[*]Type "services.msc" and click OK
[*]Find the service named "Universal Plug and Play Device Host" service
[*]Click the Stop button to stop the service
[*]Under Startup type, select Disabled from the pull-down menu and click OK
[*]Find the service named "**SSDP** Discovery Service" and double-click
[*]Click the Stop button to stop the service
[*]Under Startup type, select Disabled from the pull-down menu and click OK
[/LIST]

```

---

