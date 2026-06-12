---
title: "ufw log getting spammed with 224.0.0.1 every 3 minutes - how disable?"
date: 2014-06-27
forum: Security
---

### Post by greg2lapa on 2014-06-27
found this thread that describes the same problem, yet no solution was ever posted to the thread before it was closed [http://ubuntuforums.org/showthread.php?t=1886913](http://ubuntuforums.org/showthread.php?t=1886913)

I am not interested in changing my ufw settings as the firewall is correctly blocking. I want to know how to terminate whatever is causing that multicast address to attempt a connection every 3 minutes. I don't do multicasting so I see no reason for this to be occurring.

Does anybody know a fix? I'm running 14.04 fully up to date.

---

### Post by deadflowr on 2014-06-27
Moved to ***Security Discussions***

---

### Post by uRock on 2014-06-27
Hello and welcome to the forums,

Would it be possible for you to copy paste the log output for further analysis?

---

### Post by greg2lapa on 2014-06-28
> **uRock said:**
> Hello and welcome to the forums,

Would it be possible for you to copy paste the log output for further analysis?

After investigation, I have confirmed it is not originating from my router. I'm not sure if it's originating from ubuntu itself (all computers running ubuntu have same log entries), my Cable Modem, or my ISP. Can anyone provide any more information about this, has anyone discovered anything as it appears others have experienced it too?

If the source is outside my router I could block/deny the traffic at my router. I am running OpenWrt but do not know how I would create a firewall setting that would block this from entry into my LAN. If anybody can help with this I would really appreciate it. Thanks.

```
[UFW BLOCK] IN=eth0 OUT= MAC=redacted SRC=0.0.0.0 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

```

the above log entry occurs every 2-3 minutes without stop with only the time/date changing for each entry.

---

### Post by bashiergui on 2014-06-29
Your best option is still to capture traffic with Wireshark. It will be very quick and easy to see what's sending the traffic by filtering by the IP ```
ip.addr == 224.0.0.1
```

---

### Post by greg2lapa on 2014-06-30
> **bashiergui said:**
> Your best option is still to capture traffic with Wireshark. It will be very quick and easy to see what's sending the traffic by filtering by the IP ```
ip.addr == 224.0.0.1
```

well I could not get wireshark to work on ubuntu. so I pulled out an old windows laptop and installed wireshark on that. It is showing the MAC for the LAN-Interface of the openwrt router. I guess I was wrong in ruling out the router. I assume this means that that MAC is the origin of the 224.0.0.1 spam? 

Is anyone familiar enough with openwrt to help me configure it to not be sending the 224.0.0.1 multicasts?

---

### Post by bashiergui on 2014-06-30
Yah your router probably uses multicasting for upnp, so if you disable it you'll probably lose upnp. 
I don't use openwrt so I'm not sure how to disable multicasting on the router. This might help as it seems pretty basic:
[http://www.generationip.com/documentation/mini-howto/142-howto-enable-or-disable-multicast-on-interface-with-ifconfig](http://www.generationip.com/documentation/mini-howto/142-howto-enable-or-disable-multicast-on-interface-with-ifconfig)

---

### Post by The Cog on 2014-06-30
If you can't get wireshark to work (no reason why you shouldn't, except that it needs root privileges to perform packet capture) the tcpdump will work. 
This will probably print the onfo you need:
```
tcpdump -p -n -e host 224.0.0.1
```
Or if that printout isn't enough, this will capture to a file that wireshark can read:
```
tcpdump -p -w capture.cap host 224.0.0.1
```

One post says that the log says PROTO=2. Protocol 2 is IGMP - Internet Group Management Protocol. My guess is that it's the local router asking if there are any hosts interested in receiving multicasts - nothing to worry about. Tcpdump (without the -w option) will possibly print enough to tell you. Failing that, opening the capture file in wireshark will tell you.

---

### Post by greg2lapa on 2014-06-30
> **bashiergui said:**
> Yah your router probably uses multicasting for upnp, so if you disable it you'll probably lose upnp. 
I don't use openwrt so I'm not sure how to disable multicasting on the router. This might help as it seems pretty basic:
[http://www.generationip.com/documentation/mini-howto/142-howto-enable-or-disable-multicast-on-interface-with-ifconfig](http://www.generationip.com/documentation/mini-howto/142-howto-enable-or-disable-multicast-on-interface-with-ifconfig)

I have no need for UPnP. I thought it was off (or not available) in openwrt. I don't see any config allowing me to turn it off. Anyone know how to ```
ifconfig eth0 -multicast


``` on openwrt? Is it just a matter of SSH in and run that command? I don't want to mess anything up so if someone could advise I'd be really thankful. multicast occurs on both eth0 or wlan0.

---

### Post by uRock on 2014-06-30
I've never managed an OpenWRT product, but maybe these guys can help. [https://forum.openwrt.org/index.php](https://forum.openwrt.org/index.php)

---

### Post by The Cog on 2014-07-01
If you use tcpdump -e it will show you the MAC address that sources the packets, as well as printing a decode.
The MAC address should help identify the sender.

---

### Post by greg2lapa on 2014-07-02
> **The Cog said:**
> If you use tcpdump -e it will show you the MAC address that sources the packets, as well as printing a decode.
The MAC address should help identify the sender.

i did tcpdump but 224.0.0.1 isn't even showing in the output. And the log is still showing that 224.0.0.1 is being blocked by the firewall.
Anybody have any ideas? I'm not even sure if the router is the source as wireshark isn't exactly easy to use and understand.

---

### Post by clearski on 2014-07-03
Based on your network topology, I think you can find out who's the sender.

First of all, just erase the ufw rule which is now blocking the multicasts and reload the firewall on your host.

Then open a terminal and watch what's happening there:

```
sudo tail -f /var/log/ufw.log
```

Meanwhile, physically remove the cables that connect any other LAN devices to your router's ports (or switches or whatever intermediary devices you might have), leaving just your host connected. If you have any wireless devices that share this network at your location, turn all of them off. TV's, tablets, phones etc. Leave the WAN interface active, so your topology is now: HOST - ROUTER - WAN. Just two devices and two cables.

Check your log. Do you still receive multicasts? If the answer is Yes, just remove the cable from the WAN interface. Now it's between your host and your router. What does the log say?

If the answer is No (with or without the WAN interface), just add devices (turn them on and connect them to your network), one at a time, until you discover who's the sender.

In my case, it was the router sending multicast data to all my hosts. As the firmware was proprietary, I just blocked the sender with a simple ufw rule. The logs are silent now.

More about Multicast communication here:

[http://www.firewall.cx/networking-topics/general-networking/107-network-multicast.html](http://www.firewall.cx/networking-topics/general-networking/107-network-multicast.html)

[Update]

It seems that inside this document, from page 6 to 8, is an explanation of what's going on.

[http://www4.ncsu.edu/~rhee/clas/csc495j/ip-multicast-part1.pdf](http://www4.ncsu.edu/~rhee/clas/csc495j/ip-multicast-part1.pdf)

It's probably the the router, trying "to update its knowledge of the group members present on each network interface" (hints: 224.0.0.1, IGMP, TTL: 1).

---

### Post by greg2lapa on 2014-07-04
> **clearski said:**
> Based on your network topology, I think you can find out who's the sender.

First of all, just erase the ufw rule which is now blocking the multicasts and reload the firewall on your host.

Then open a terminal and watch what's happening there:

```
sudo tail -f /var/log/ufw.log
```

  As the firmware was proprietary, I just blocked the sender with a simple ufw rule. The logs are silent now.



When you say you blocked it, this prevents the logs from showing the traffic, but the traffic is still occurring on the network? Or did you block the traffic from even being on the network? I am wondering if there is a way to disable the traffic at its origin so that the traffic is not occurring.

---

### Post by clearski on 2014-07-04
> **greg2lapa said:**
> When you say you blocked it, this prevents the logs from showing the traffic, but the traffic is still occurring on the network? Or did you block the traffic from even being on the network? I am wondering if there is a way to disable the traffic at its origin so that the traffic is not occurring.

Initially, I just blocked the traffic from being recorded in the firewall log file. Yesterday, after a few months, I removed the rule which blocked the multicast frames / datagrams to reach the interface because I wanted to capture some data and have a look at it. To my surprise, I had no entry. I checked the log now and it's still empty. It might be a service that I disabled on the router and was sending multicast data. I don't know... However, first you have to make sure about what device is the sender. In my case, I knew it was the LAN interface on the router that was used.

---

### Post by bashiergui on 2014-07-05
Just curious, what's your concern with the router sending multicast packets that your computer is dropping?

---

### Post by Doug S on 2014-07-09
In my case it is my ISP that sends the annoying packets. I have a specific iptables rule to DROP the packets without logging and a more generic one later on for anything else, but with logging.
Here is a segment:```
doug@doug-64:~$ sudo iptables -v -x -n -L
[sudo] password for doug:
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   27169  2164555 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
[COLOR=#ff0000]  108273  3465000 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1[/COLOR]
       6      312 LOG        tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state INVALID LOG flags 0 level 6 prefix "IINVALID:"
    1083   576045 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW LOG flags 0 level 6 prefix "NEW TCP no SYN:"
    1083   576045 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW reject-with icmp-port-unreachable
 2726300 211958179 ACCEPT     all  --  eth0   *       192.168.111.0/24     0.0.0.0/0
       0        0 LOG        all  --  eth1   *       192.168.0.0/16       0.0.0.0/0            LOG flags 0 level 6 prefix "Sub192:"
       0        0 DROP       all  --  eth1   *       192.168.0.0/16       0.0.0.0/0
       0        0 LOG        all  --  eth1   *       10.0.0.0/8           0.0.0.0/0            LOG flags 0 level 6 prefix "Sub10:"
       0        0 DROP       all  --  eth1   *       10.0.0.0/8           0.0.0.0/0
       0        0 LOG        all  --  eth1   *       172.16.0.0/12        0.0.0.0/0            LOG flags 0 level 6 prefix "Sub172:"
       0        0 DROP       all  --  eth1   *       172.16.0.0/12        0.0.0.0/0
       0        0 LOG        all  --  eth1   *       240.0.0.0/5          0.0.0.0/0            LOG flags 0 level 6 prefix "Sub240:"
       0        0 DROP       all  --  eth1   *       240.0.0.0/5          0.0.0.0/0
[COLOR=#ff0000]       0        0 LOG        all  --  eth1   *       224.0.0.0/4          0.0.0.0/0            LOG flags 0 level 6 prefix "Sub224:"
       0        0 DROP       all  --  eth1   *       224.0.0.0/4          0.0.0.0/0[/COLOR]
...
```I do not use ufw and do not know how to do the same with it.

---

### Post by clearski on 2014-07-13
> **Doug S said:**
> In my case it is my ISP that sends the annoying  packets. I have a specific iptables rule to DROP the packets without  logging and a more generic one later on for anything else, but with  logging.

Hello, Doug!

Since the multicast range 224.0.0.0 - 224.0.0.255 is reserved for local link addresses, what's the relationship between the IP address on the router's interface to your provider and the IP address of your provider (default-gateway)? Are they on the same subnet?

---

### Post by Doug S on 2014-07-13
> **clearski said:**
> Hello, Doug!

Since the multicast range 224.0.0.0 - 224.0.0.255 is reserved for local link addresses, what's the relationship between the IP address on the router's interface to your provider and the IP address of your provider (default-gateway)? Are they on the same subnet?Really good question, one that is testing my memory. How did I originally figure this out? My ISP is telus and they seem to use the 10.0.0.0 non-public subnet for some internal stuff. My router is my externally facing Ubuntu server box and I have never been able to figure out the relationship between my external static IP address and the addresses on the 10.0.0.0 subnet that telus uses. These are examples of what I get on my external interface from the 10.0.0.0 subnet:```
2014-05-13 11:53:29.748213 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2014-05-13 11:53:59.746924 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2014-05-13 11:54:29.746636 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2014-05-13 11:54:59.746385 IP 10.197.248.13 > 224.0.0.1: igmp query v2
...
2014-05-13 12:01:02.087450 IP 10.0.0.138.28228 > 239.255.255.250.1900: UDP, length 274
2014-05-13 12:01:02.088358 IP 10.0.0.138.28228 > 239.255.255.250.1900: UDP, length 274
2014-05-13 12:01:02.095711 IP 10.0.0.138.28229 > 239.255.255.250.1900: UDP, length 285
2014-05-13 12:01:02.096663 IP 10.0.0.138.28229 > 239.255.255.250.1900: UDP, length 285
...
2014-06-09 11:54:10.767030 IP 10.31.202.1 > 173.180.45.4: ICMP time exceeded in-transit, length 38
2014-06-09 11:54:10.853533 IP 10.31.202.1 > 173.180.45.4: ICMP time exceeded in-transit, length 38
2014-06-09 11:54:24.526836 IP 10.31.202.1 > 173.180.45.4: ICMP time exceeded in-transit, length 38
2014-06-09 11:54:24.710153 IP 10.31.202.1 > 173.180.45.4: ICMP time exceeded in-transit, length 38
```Hmmm... As a side note, I better look into those time exceeded things, as my server seems to have sent packets with a TTL of 1. With a TTL of just 2, I get time exceeded replies from "real" IP addresses. Anyway, I digress...

Did this help, or confuse things more?

---

### Post by clearski on 2014-07-13
> **Doug S said:**
>  These are examples of what I get on my external interface from the 10.0.0.0 subnet:```
2014-05-13 11:53:29.748213 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2014-05-13 11:53:59.746924 IP 10.197.248.13 > 224.0.0.1: igmp query v2
...
2014-05-13 12:01:02.087450 IP 10.0.0.138.28228 > 239.255.255.250.1900: UDP, length 274
...
2014-06-09 11:54:10.767030 IP 10.31.202.1 > 173.180.45.4: ICMP time exceeded in-transit, length 38


```

Same here. My ISP is using an address from the 10.0.0.0/8 range. When I connect using PPPoE, they automatically assign me a routable IP address.

The queries in your logs show both link local (224.0.0.1) and globally scoped (239.255.255.255) multicast addresses. As they say that globally scoped can be used to multicast data across the Internet, the query might have come from a point behind the first ISP router, but I'm not sure I understand exactly how it works, so it's just a guess.

I think this could explain the link local requests:

*"Multicast routers use IGMP to learn which groups have members on each of their attached physical networks"* ([https://www.rfc-editor.org/rfc/rfc2236.txt](https://www.rfc-editor.org/rfc/rfc2236.txt))

*"224.0.0.1 is assigned to the permanent group of all IP hosts (including gateways).This is used to address all multicast hosts on the directly connected network." *([http://tools.ietf.org/html/rfc1112](http://tools.ietf.org/html/rfc1112))

It should be the ISP's router trying to locate multicast members for some reason. I still don't understand how a non routable and a public address can be on the same logical network, however.

> **Doug S said:**
> Hmmm... As a side note, I better look into those time exceeded things, as my server seems to have sent packets with a TTL of 1. With a TTL of just 2, I get time exceeded replies from "real" IP addresses. Anyway, I digress...

Did this help, or confuse things more?

What is the destination of the packets with TTL 1? I am curious. As far as I know, communication using link local addressing is set a TTL to 1 because the services are not forwarded by the routers.

---

### Post by Doug S on 2014-07-14
> **clearski said:**
> What is the destination of the packets with TTL 1? I am curious. As far as I know, communication using link local addressing is set a TTL to 1 because the services are not forwarded by the routers.In the specific example I looked up, it seems to have been from the blu-ray player on my LAN to netflix streaming services. Traffic was heavy at the time, and I assume someone was watching something on netflix. It seems to increase the TTL by one each time until (I assume) it gets the response it wants.

---

### Post by gustavo-lapido on 2014-08-14
> **greg2lapa said:**
> I have no need for UPnP. I thought it was off (or not available) in openwrt. I don't see any config allowing me to turn it off. Anyone know how to ```
ifconfig eth0 -multicast


``` on openwrt? Is it just a matter of SSH in and run that command? I don't want to mess anything up so if someone could advise I'd be really thankful. multicast occurs on both eth0 or wlan0.

Yes, it's just a matter of SSH in and run it.

I'm getting the same ufw block as you and I found out that it comes from my openwrt router.

I issued that command (ifconfig -multicast) to all interfaces available in the router that were multicasting-enabled (br-lan, eth0, eth1 and wlan0) and the simple ifconfig command showed that multicasting was disabled.

I even add those commands to the startup script (System -> Startup, at the bottom):

```
# Put your custom commands here that should be executed once
# the system init finished. By default this file does nothing.
ifconfig br-lan -multicast
ifconfig eth0 -multicast
ifconfig eth1 -multicast
ifconfig wlan0 -multicast
exit 0
```

then reboot, ssh in and ifconfig showed that the startup commands had been executed.

However, ufw keeps receiving those messages.

I don't understand.

Have you solved this?

---

### Post by greg2lapa on 2014-08-20
> **gustavo-lapido said:**
> 
Have you solved this?

No. Haven't solved it.

I have systematically eliminated every connection to the router and the multicast was still occuring. So it appears that nothing on the network (device wise) is causing the traffic. I contacted the cable modem maker and they said the modem is simple passthrough and wouldn't introduce something like that. So I'm thinking the traffic is originating from one of two sources:

1) the openwrt router

2) my ISP

Someone else in this thread said they localized it to the openwrt router. so I'm guessing it's that. But I have no idea how to fix it. I haven't given up, but so far I haven't had much luck fixing it. I have never found the openwrt forums to be helpful and they have provided no help so far. This forum has been more helpful :)

---

### Post by gustavo-lapido on 2014-08-20
> **greg2lapa said:**
> No. Haven't solved it.

I have systematically eliminated every connection to the router and the multicast was still occuring. So it appears that nothing on the network (device wise) is causing the traffic. I contacted the cable modem maker and they said the modem is simple passthrough and wouldn't introduce something like that. So I'm thinking the traffic is originating from one of two sources:

1) the openwrt router

2) my ISP

Someone else in this thread said they localized it to the openwrt router. so I'm guessing it's that. But I have no idea how to fix it. I haven't given up, but so far I haven't had much luck fixing it. I have never found the openwrt forums to be helpful and they have provided no help so far. This forum has been more helpful :)

Have you unpluged your router  and connected your computer directly onto the modem?

Maybe you'll have to reboot the modem to get your computer online (as far as I know, some modem models need that in order to get a new MAC passthrough), but then you could easily confirm which source is multicasting: if the multicast continues, then it's your ISP, else, it's your openwrt router.

---

