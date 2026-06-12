---
title: "[SOLVED] iptables i don't understand can you help me?"
date: 2007-08-29
forum: Server Platforms
---

### Post by nowshining on 2007-08-29
well I read and read but I DO NOT understand and am only trying to block ALL multicast from my computer out and all Multicast in and drop both..

I switched to arno-iptables-firewall which there is a file to just input the rules and of course next reboot it will set it up which is easy but I DO NOT get how to setup the rule to block multicast (incl. IGMP) in iptable form...

I tried copy and pasting some rules but I do not know if they are right, I DO NOT like opening up calc, or terminal and then it sending DNS protocol out to the internet thru My ISP...

so I believe even after disabling multicast with PPP0 on each dialup (i have a how to) it still does that...

So can anyone give me a one time rule for this? so I can copy + paste it to be honest.... other than that all is well for me..

---

### Post by steve.horsley on 2007-08-29
I think you can just drop IP addresses in the range 224.0.0.0/4 in both directions to block multicasts. This will prevent DHCP from working of course.

DNS does not use multicasts, so blocking multicasts will not affect DNS. Are you really trying to block DNS as well? Why? If you really want to block DNS outgoing, you need to block outgoing UDP to port 53. This will prevent you from web surfing etc of course.

---

### Post by nowshining on 2007-08-29
well everytime i open up a terminal to do something or calc and some others something is sent out over to my ISPs IP DNS I guess, anway I filed help but haven't heard back except for that it was Multicast - I tried everything on that and it says disabled in network tools, allmulti is off no arp, but still something is sent out for some unknown reason which it shouldn't go over the Internet ISP namerserver at all or so...

and that's what I am trying to block but I DO NOT Know what it is, I do not need DHCP tho, but here's a link to the last post with a screenshot of ethereal - & the problem - the problem is the in Blue in the screnshot (default color for ethereal) & it's the end of the first post: 

again that's what I am trying to stop from happening & again I DO NOT know what Is causing it to happen when those programs are opened up and I am connected to the net and this only happens when I open up terminal or calc at least..

the link to the screenshot directly is [http://ubuntuforums.org/attachment.php?attachmentid=41332&d=1187784915](http://ubuntuforums.org/attachment.php?attachmentid=41332&d=1187784915)

[http://ubuntuforums.org/showthread.php?t=532006](http://ubuntuforums.org/showthread.php?t=532006) is the forum post in it's whole

IGMP always comes up from my isp so that's not the problem but i'd still like it blocked and to repeat myself the entries that go out are in blue and in the screenshot it's the second one under info saying Standard query AAA and my computers' name but i'd still like a ip rule to totally block and drop multicast as well, but the REAL issue is the Unauthorized DNS out - last time I guess I didn't make myself that clear...



edit: i disabled IPV6 and it's till happening as I found that out just a few minutes ago..

---

### Post by steve.horsley on 2007-08-29
Are you saying that your computers name is bot1net1god1? If so, this should be in your /etc/hosts file in a line like this:
**127.0.0.1 localhost.localdomain localhost bot1net1god1**
This will stop the DNS queries out to your ISP as the name can be resolved locally - there will be no need to ask the ISP any more (just for this name).

If you want your PC to stop querying a single name, the best thing to do is to put that name in /etc/hosts anyway, but your own machines name should **always** be in there against the address 127.0.0.1.

---

### Post by nowshining on 2007-08-29
yes it is my computers name but I never want it to go out to the net, i'll try that but still looking for the iptable igmp block rule...


edit: I believe that helped however now ethereal gives me the following even running as the root menu item

The capture session could not be initiated (socket: Address family not supported by protocol).

Please check to make sure you have sufficient permissions, and that you have
the proper interface or pipe specified.


well that's a mild thing and I can get rid of that program - lolz :P thanks and ONE down and one to go... or so...

---

### Post by steve.horsley on 2007-08-29
That sounds bad. As a check, there are two files that contain your host name, and they MUST agree. These are /etc/hostname which contains only the host name, and /etc/hosts which maps the name to 127.0.0.1. 

As for blocking incoming IGMP, just block packets to 224.0.0.1. I think this might do it:
iptables -A -p all -d 224.0.0.1 -j DROP
but that's off the top pf my head.

---

### Post by ghostcrab on 2007-08-29
try this too 

iptables -A INPUT -p all -j DROP  we forgot INPUT

# Block Mutilecast
iptables -A INPUT -m pkttype --pkt-type broadcast -j DROP
iptables -A INPUT -m pkttype --pkt-type multicast -j DROP
iptables -I INPUT -m pkttype --pkt-type multicast -j DROP
iptables -I INPUT -m pkttype --pkt-type broadcast -j DROP

---

### Post by steve.horsley on 2007-08-29
Hmm. Won't blocking all broadcasts break ARP and leave his PC unable to talk to anything?

---

### Post by nowshining on 2007-08-29
blockging all broadcast with comodo firewall when I had it on windows didn't bother a thing, I also listened to AOL radio with no problem... or at least i only allowed TCP out - blocked all TCP in, allowed only UDP out to the ISPs dns server - or the one's I chose - and blocked all the rest - and then blocked all IP in/out and IP was the rest of the protocols oh and I blocked all ICMP in/out when I had it..but since the firewall lets some such as traceroute in, as long as a Ping reply is no reply that's no problem for me ut since I am using linux I am learning a bit more..

---

### Post by nowshining on 2007-08-29
it says exactly my computers' name in /ets/hostname


edit: the one in hosts was UNCAPITALIZED but I changed that but still wireshark/ethereal will not work

---

### Post by nowshining on 2007-08-29
# Load/insert user plugins
##########################
if [ -e /etc/arno-iptables-firewall/plugins/* ]; then
  echo "Loading (user) plugins"
  for plugin in /etc/arno-iptables-firewall/plugins/*; do
    . $plugin
  done
fi

# Put any custom (iptables) rules here down below:
##################################################







............

that's what the program has and it's called custom rules.. :) the default rules almost are fine, but I want to make SURE it's blocking IGMP/multicast and droping it as I've had other firewall not have that option at all I believe... and firestarter sucks to the brim with problems....anyway this is WAY better and easy to input custom rules IF I find them... or want to but again this gives me the best of both worlds... and doesn't slow down my computer.... :)

---

### Post by nowshining on 2007-08-29
I used both of yours and here's my firewall setup so far found on another post how to see it....is it working?


edit change some firewall settings in firewall.conf :) it was easy and had to figure out to restart the firewall without restarting lolz.. :P arno firewall is named arno-iptable-firewall to to restart I had to issue

sudo /etc/init.d/arno-iptables-firewall restart

lolz again :P i enabled DDOS protection, etc.. disabled ALL ICMP...by changing a setting From 0 to 1 save amd restart tje firewall - used network tools ping to test, etc...

insteat of the normal

```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast 
   83  6780 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
  568  637K ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED tcp dpts:1024:65535 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED udp dpts:1024:65535 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED 
 3543  170K HOST_BLOCK  0    --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
 3543  170K SPOOF_CHK  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = broadcast 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           PKTTYPE = multicast 
 3543  170K VALID_CHK  0    --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
 3508  146K EXT_INPUT_CHAIN !icmp --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state NEW 
   11   376 EXT_INPUT_CHAIN  icmp --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state NEW limit: avg 20/sec burst 100 
    0     0 EXT_ICMP_CHAIN  icmp --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Dropped INPUT packet: ' 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 TCPMSS     tcp  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
    0     0 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED tcp dpts:1024:65535 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED udp dpts:1024:65535 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED 
    0     0 HOST_BLOCK  0    --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 SPOOF_CHK  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 VALID_CHK  0    --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 RESERVED_NET_CHK  0    --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/min burst 3 LOG flags 0 level 6 prefix `Dropped FORWARD packet: ' 
    0     0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 75 packets, 335K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   21  1260 TCPMSS     tcp  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
  573 40569 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 
    0     0 LOG        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `FRAGMENTED PACKET (OUT): ' 
    0     0 DROP       0    -f  *      *       0.0.0.0/0            0.0.0.0/0           
   28  133K EXT_OUTPUT_CHAIN  0    --  *      ppp0    0.0.0.0/0            0.0.0.0/0           

Chain EXT_ICMP_CHAIN (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-request(ping) flood: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-unreachable flood: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-source-quench flood: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-time-exceeded flood: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-param.-problem flood: ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP(other) flood: ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain EXT_INPUT_CHAIN (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    1    40 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:0 limit: avg 6/hour burst 1 LOG flags 0 level 6 prefix `TCP port 0 OS fingerprint: ' 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:0 limit: avg 6/hour burst 1 LOG flags 0 level 6 prefix `UDP port 0 OS fingerprint: ' 
    3   120 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:0 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:0 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spt:0 limit: avg 6/hour burst 5 LOG flags 0 level 6 prefix `TCP source port 0: ' 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:0 limit: avg 6/hour burst 5 LOG flags 0 level 6 prefix `UDP source port 0: ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp spt:0 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:0 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
 3516  146K RESERVED_NET_CHK  0    --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:!2049 multiport sports 20,21,22,23,80,110,143,443,993,995 limit: avg 6/hour burst 1 LOG flags 0 level 6 prefix `Possible DRDOS TCP attempt: ' 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:!2049 multiport sports 20,21,22,23,80,110,143,443,993,995 limit: avg 6/hour burst 1 LOG flags 0 level 6 prefix `Possible DRDOS UDP attempt: ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:!2049 multiport sports 20,21,22,23,80,110,143,443,993,995 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:!2049 multiport sports 20,21,22,23,80,110,143,443,993,995 
    3   101 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 3/min burst 1 LOG flags 0 level 6 prefix `ICMP-request: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-unreachable: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-source-quench: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-time-exceeded: ' 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 limit: avg 12/hour burst 1 LOG flags 0 level 6 prefix `ICMP-param.-problem: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1024:65535 flags:!0x17/0x02 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth scan (UNPRIV)?: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:0:1023 flags:!0x17/0x02 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth scan (PRIV)?: ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:!0x17/0x02 
   13   552 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:0:1023 limit: avg 6/min burst 2 LOG flags 0 level 6 prefix `Connection attempt (PRIV): ' 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:0:1023 limit: avg 6/min burst 2 LOG flags 0 level 6 prefix `Connection attempt (PRIV): ' 
    5   200 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:1024:65535 limit: avg 6/min burst 2 LOG flags 0 level 6 prefix `Connection attempt (UNPRIV): ' 
   13  5140 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:1024:65535 limit: avg 6/min burst 2 LOG flags 0 level 6 prefix `Connection attempt (UNPRIV): ' 
 3470  139K DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           
   20  6464 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           
   11   376 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   12   336 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/min burst 5 LOG flags 0 level 6 prefix `Other-IP connection attempt: ' 
   15   420 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain EXT_OUTPUT_CHAIN (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain HOST_BLOCK (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        0    --  *      *       64.136.0.0           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.0           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.1           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.1           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.2           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.2           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.3           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.3           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.4           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.4           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.5           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.5           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.6           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.6           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.7           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.7           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.8           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.8           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.9           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.9           0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.10          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.10          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.11          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.11          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.12          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.12          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.13          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.13          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.14          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.14          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.15          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.15          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.16          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.16          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.17          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.17          0.0.0.0/0           
    0     0 LOG        0    --  *      *       64.136.0.18          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       64.136.0.18          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.0          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.0          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.1          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.1          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.2          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.2          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.3          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.3          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.4          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.4          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.5          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.5          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.6          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.6          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.7          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.7          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.8          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.8          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.9          0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.9          0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.10         0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.10         0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.11         0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.11         0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.12         0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.12         0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.13         0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.13         0.0.0.0/0           
    0     0 LOG        0    --  *      *       209.244.0.14         0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Blocked hosts violation: ' 
    0     0 DROP       0    --  *      *       209.244.0.14         0.0.0.0/0           

Chain MAC_FILTER (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain RESERVED_NET_CHK (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        0    --  *      *       10.0.0.0/8           0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Class A address: ' 
    0     0 LOG        0    --  *      *       172.16.0.0/12        0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Class B address: ' 
    0     0 LOG        0    --  *      *       192.168.0.0/16       0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Class C address: ' 
    0     0 LOG        0    --  *      *       169.254.0.0/16       0.0.0.0/0           limit: avg 1/min burst 1 LOG flags 0 level 6 prefix `Class M$ address: ' 
    0     0 DROP       0    --  *      *       10.0.0.0/8           0.0.0.0/0           
    0     0 DROP       0    --  *      *       172.16.0.0/12        0.0.0.0/0           
    0     0 DROP       0    --  *      *       192.168.0.0/16       0.0.0.0/0           
    0     0 DROP       0    --  *      *       169.254.0.0/16       0.0.0.0/0           

Chain SPOOF_CHK (2 references)
 pkts bytes target     prot opt in     out     source               destination         
 3543  170K RETURN     0    --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain VALID_CHK (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth XMAS scan: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x37 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth XMAS-PSH scan: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth XMAS-ALL scan: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x01 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth FIN scan: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth SYN/RST scan: ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth SYN/FIN scan(?): ' 
    5   200 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 limit: avg 3/min burst 5 LOG flags 0 level 6 prefix `Stealth Null scan: ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x37 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x01 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 
    6   240 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp option=64 limit: avg 3/min burst 1 LOG flags 0 level 6 prefix `Bad TCP flag(64): ' 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp option=128 limit: avg 3/min burst 1 LOG flags 0 level 6 prefix `Bad TCP flag(128): ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp option=64 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp option=128 
   18 23991 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LOG        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 1 LOG flags 0 level 4 prefix `Fragmented packet: ' 
    0     0 DROP       0    -f  *      *       0.0.0.0/0            0.0.0.0/0   

```

---

### Post by nowshining on 2007-08-30
this nice peer guardian like program showed me that IGMP wasn't being blocked so, I used ghostcrabs' rules and noticed I didn't copy it at all into the custom rules config file, but now the iplists program [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183) is not showing IGMP in which I like and yes I restarted the firewall with the new rules without rebooting.. :)


edit n/m i had it disabled last time.. lolz..

---

### Post by ghostcrab on 2007-08-30
You can spend a lifetime studying iptables
I'm glad it helped you sorry for the late reply but I work late hours.
I just search the net for IGMP iptables drop I also found this .

```

# IGMP noise, log & drop
iptables -A INPUT -i wlan0 -p 2 -j LOG --log-level debug --log-prefix "IPTABLES IGMP-IN: "
iptables -A INPUT -i wlan0 -p 2 -j DROP

```

---

### Post by nowshining on 2007-08-30
it's okay, i tried everything even google and ipblock still LOGS IT (bluetack blocks it) so to solve my problem i am gong to try and get iplists to startup on computer startup and block that in the background to solve the problem once and for all...

---

### Post by nowshining on 2007-08-30
oh yeah it was just me :) i'm gonna re-put the ips in there, however i believe the rules were fine however with that running in the back and a huge hosts file, my dialup flies..

---

