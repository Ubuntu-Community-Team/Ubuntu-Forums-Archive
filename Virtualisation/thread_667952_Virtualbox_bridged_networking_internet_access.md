---
title: "Virtualbox bridged networking internet access"
date: 2008-01-14
forum: Virtualisation
---

### Post by anthropop on 2008-01-14
I installed Virtualbox with  WinXP as the guest and with Ubuntu Gutsy as host and can not get an internet connection from WinXP.  I have tried NAT and bridged networking.  

I have gotten to the point where bridged networking was working perfectly on my network, so that from WinXP I could ping other machines including the DSL gateway/firewall as well as see the windows shares on my network.  I also can ping WinXP from any machine on my network.  I then added a static route in the DSL gateway to the WinXP IP and restarted the gateway.  Still no internet access.

It may be easier to follow this with specific IP addresses.  The DSL gateway/firewall is at 192.168.0.10.  The Ubuntu machine is at 192.168.0.6 which is assigned via DHCP from the gateway.  So in my bridged configuration br0 is 192.168.0.6 instead of eth0.  I then created a tun tap1 attached to br0.  In Virtualbox I selected "Host Interface" and tap1 for the interface name as the wiki suggested.  In WinXP I setup my network to IP 192.168.0.20 (I picked this address), and the gateway to 192.168.0.10 with netmasks of 255.255.255.0.

In order to isolate between DNS issues and raw internet access I tried a ping to a known internet IP address, thus not requiring nslookup.  All my other machines get their IP address from the gateway via DHCP, and I assume that the WinXP box not getting the IP from DHCP is a source of trouble, and so I tried a static route in the gateway/firewall.  Anyway, I can't ping anything outside of my network.

I have seen others on the net struggle with bridged and NAT configurations with Virtualbox so I think this post may help many people.  I also have VmWare 2.0 beta installed, and I really want to get away from that as it is a CPU hog and very buggy.  Virtualbox is already way faster and less CPU intensive.

I don't know much about DHCP, so if someone can help in that area I think that may be a source of the problem.  If I could get the router to assign the IP address to WinXP I think it would then allow http traffic to the interface.  All the wikis talk about assigning a static address to the Windows guest OS.  This does not work through a gateway.

---

### Post by karyonix on 2008-01-15
This is my host machine network settings. It may work for you.

Install **bridge-utils** and **uml-utilities**.
```
sudo apt-get install bridge-utils uml-utilities
```

Add user account to **uml-net** group.
```
sudo gpasswd -a my_username uml-net
```

Edit **/etc/network/interfaces** like this. Change my_username as appropriate.
BEFORE
```
auto lo eth0

iface lo inet loopback

iface eth0 inet dhcp
```
AFTER
```
auto lo eth0 tap1 br0

iface lo inet loopback

iface eth0 inet manual

iface tap1 inet manual
  tunctl_user my_username

iface br0 inet dhcp
  bridge_ports eth0 tap1
  pre-up ip link set eth0 promisc on
```

In VirtualBox's VM Settings - Network - Host Interface Settings, set Interface Name to your tap interface name. In this example it's tap1.

Log out and log in again to apply changed group membership.
Restart networking to apply changed network settings.
```
sudo /etc/init.d/networking restart
```

Both my host machine & guest VM get ip addresses from DHCP server on another machine on the local network and can communicate with other computers on the network.

---

### Post by mozetti on 2008-01-15
Why don't you just set the XP VM to DHCP?

---

### Post by Hero of Time on 2008-01-15
I use virtual box too and have no problems using either bridge or nat. Nat worked just fine straight away. Be sure to set the Xp machine to dhcp for nat to funtion. For bridging, all I did was 'sudo apt-get install bridge-utils' and create a bridge with my lan adapter in it, then with vbox I created the host interface and added that to the bridge. Works like a charm. I can use internet, go trough my network, everything.

---

### Post by anthropop on 2008-01-17
I had posted (see below) how this failed to work, but it did work after all!  My iptables were screwed up, so I disabled the firewall and returned WinXP to DHCP and it found the internet...So now I need to figure out what is wrong with my iptables config.  I'll post the iptables -L result in my next post.  It would help to know what port or protocol DHCP uses to narrow this down.

------------- OLD POST follows for the history:
I appreciate all of the replies, but I tried all of these suggestions and it made no difference.  I realize that this works for others and that there is something broken with my setup, the question is how to find the problem.  I also know from other posts on the net that people have run into the same problem I have.  

Here was my output from /etc/init.d/networking restart
Note that there are errors, but in the end the br0 and tap1 exist and are functional.  I can see all network machines from VirtualBox, but only if I give a fixed IP address.  Otherwise WinXP can't even bring up the network interface.

root@saturn:/etc/network# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                    Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.
Set 'tap1' persistent and owned by uid 1000
 * Stopping the Firestarter firewall...
br0: error fetching interface information: Device not found
br0: error fetching interface information: Device not found
br0: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
br0: error fetching interface information: Device not found
br0: error fetching interface information: Device not found
br0: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
WARNING: The "printer admin" option is deprecated
16671: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:18:f3:bf:0d:71
Sending on   LPF/br0/00:18:f3:bf:0d:71
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.10
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.10
bound to 192.168.0.6 -- renewal in 36789 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
WARNING: The "printer admin" option is deprecated
17331: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


root@saturn:/etc/network# ifconfig 
br0       Link encap:Ethernet  HWaddr 00:18:F3:BF:0D:71  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:197404 (192.7 KB)  TX bytes:347185 (339.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:18:F3:BF:0D:71  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4534276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4673069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1019708322 (972.4 MB)  TX bytes:2471810743 (2.3 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:369470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28826617 (27.4 MB)  TX bytes:28826617 (27.4 MB)

tap1      Link encap:Ethernet  HWaddr 00:FF:70:A0:C5:BC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:31 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.213.1  Bcast:172.16.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.232.1  Bcast:192.168.232.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@saturn:/etc/network# 

I rebooted my ubuntu box as well.  When I started Virtualbox with DHCP, it could not bring up the interface at all.  I changed it to 192.168.0.20 and it worked as far as I already described.
---------------- END of old post

---

### Post by anthropop on 2008-01-17
When I cleaned up my iptables, whether I use Firestarter or just an iptables file, I get some log info:

Jan 17 23:27:24 saturn kernel: [ 3167.991996] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap1 SRC=199.93.33.124 DST=192.168.0.20 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=65361 PROTO=TCP SPT=80 DPT=1142 WINDOW=7956 RES=0x00 ACK FIN URGP=0 

and...

Jan 17 23:36:06 saturn kernel: [ 3689.068772] iptables denied: IN=br0 OUT= PHYSIN=eth0 MAC=00:18:f3:bf:0d:71:00:0f:b3:2e:34:57:08:00 SRC=205.128.79.124 DST=192.168.0.6 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=29750 PROTO=TCP SPT=80 DPT=1164 WINDOW=10720 RES=0x00 ACK FIN URGP=0 

This appears to be some firewall problem around the br0 interface.  My WinXP box gets via DHCP an ip of 192.168.0.20.  I think it goes out to a DNS or other server it is trying to address and does not get the response because the iptables must not let it through.

All I know is that it works without the firewall and fails with it.

---

### Post by anthropop on 2008-01-18
Here is my iptables file that I created by hand.  It is meant to block all ports from the internet, but allow all connections on my internal network.  Doing port scans it works as expected, but it also has something that VirtualBox WinXP guest does not like:

root@saturn:/etc# cat iptables.up.rules
*nat
:PREROUTING ACCEPT [97:15195]
:POSTROUTING ACCEPT [22:2661]
:OUTPUT ACCEPT [88:85214]
COMMIT
*mangle
:PREROUTING ACCEPT [10801:2165062]
:INPUT ACCEPT [10732:2156687]
:FORWARD ACCEPT [96:15119]
:OUTPUT ACCEPT [11040:4443267]
:POSTROUTING ACCEPT [10872:4329768]
COMMIT
*filter
:INPUT DROP [0:0]
:FORWARD DROP [96:15119]
:OUTPUT DROP [5:2284]
:INBOUND - [0:0]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:OUTBOUND - [0:0]
-A INPUT -s 192.168.0.10 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 192.168.0.10 -p udp -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 1:65535 -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 1:65535 -j ACCEPT 

-A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp -j ACCEPT 
-A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp -j ACCEPT 
-A INPUT -i br0 -s 192.168.0.0/255.255.255.0 -j ACCEPT 
-A INPUT -i eth0 -s 192.168.0.0/255.255.255.0 -j ACCEPT 

-A INPUT -m limit --limit 30/min -j LOG --log-prefix "iptables denied: " --log-level 7 
-A OUTPUT -j ACCEPT 
COMMIT

---

### Post by anthropop on 2008-01-18
Thanks to everyone who gave inputs to get this working!  I figured out the last piece which was my iptables rules.  The critical rule was to allow FORWARD to bridge br0.  I checked these rules with a port scan and there were no holes.

Note that this is now in the form of a bash shell script, but it could be put into an iptables restore file by converting to that format (remove "iptables" from the start of each line).

#!/bin/bash
# flush all chains
iptables -F
# set the default policy for each of the pre-defined chains
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# allow all outgoing traffic
iptables -A OUTPUT -j ACCEPT

# allow establishment of connections initialised by my outgoing packets
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# accept everything on local network
iptables -A INPUT -s 192.168.0.0/24 -i eth+ -p udp -j ACCEPT
iptables -A INPUT -s 192.168.0.0/24 -i eth+ -p tcp -m tcp --syn -j ACCEPT
iptables -A INPUT -s 192.168.0.0/24 -i br0 -p udp -j ACCEPT
iptables -A INPUT -s 192.168.0.0/24 -i br0 -p tcp -m tcp --syn -j ACCEPT

# accept anything on localhost
iptables -A INPUT -i lo -j ACCEPT

# accept forwards to my virtual machine
iptables -A FORWARD -i br0 -j ACCEPT

---

### Post by d3n0 on 2008-05-06
Thanx anthropop! I 'borrowed' :) your script because couldn't find a way to cofigure firestarter to forward to br0. But after restart the same problem (network unreachable) appeared. I was able to ping only my router.

It seems that one has to set eth0 in promiscuous mode ```
ifconfig eth0. 0.0.0.0 promisc
``` Didn't find anything about it in VB manual. I tried first to set default route to my router (even if it was already set), that worked also (without eth0 in promis) but with some strange results in metrics and routing table and it wasn't clear to my why it works when default route was already set?

After setting eth0 in promiscuous mode, I was able to connect to internet with my host (ubuntu), but my Guest OS (WinXP) was still off. It couldn't even ping the router. It seems that disabling ipv6 'solved' this problem.

edit:

no, it didn't solve it. both problems appear sometime and sometime everything works. O noticed this message in dmesg output:

br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature

edit:

Hmm now I tried with disabled Network Manager, and it works. Now I'll have to wait a little bit to see if it is going to work afeter couple of reboots.

---

### Post by ronkinoz on 2008-05-07
Hey Karyonix - thanks for your work.

Using your info I quickly got my VirtualBox based WinXP bridged onto the home LAN.

However...  the Ubuntu Network Manager applet no longer shows the VPN connection to my work that I had set up.  It also no longer shows any form of VPN config capability - only "Manual Configuration", which has no VPN related stuff.  

Any ideas on how to get VPN set up again?

Cheers,
ronkinoz

---

### Post by ericragsdale on 2008-11-20
Karyonix, thank you for sharing your configuration.  I, too, was able to set up bridged networking very quickly with your help.  

It works great, however I am unable to run 2 or more VBox guests (each configured to use 'tap1') simultaneously.  I assume I need to create a unique 'tap*x*' for each guest to have functional bridged networking.  

I don't fully understand exactly what is happening in the *interfaces* config file, so I am at a loss on what I need to do to set it up for multiple *tap*s.  Could you possibly help a newb out by pointing me in the right direction or submitting a sample config?

---

