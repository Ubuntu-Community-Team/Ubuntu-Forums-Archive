---
title: "Virtual Network br0"
date: 2014-07-23
forum: Virtualisation
---

### Post by admmorketh on 2014-07-23
This is an odd situation i have a catalyst 3550 series switch with a desktop server set up how ever i am not near the router.
i have a windows 7 laptop that i have install Oracle VM on and as a guest OS i have ubuntu 12 server i am trying to bridge my Wireless to my Ethernet using a virtual machine
i know this seems a bit over complicated how ever i have spent several days trying to get a normal windows bridge working and having previous network experience with ubuntu decided to try it this way

router ))))) laptop wifi -----> [guest eth0] br0 [guest eth1] ----> Laptop NIC ------> Catalyst 3550 -----> Centos 6

bolth network adapters are bridged to there respective host adapters and up untill i configured br0 on guest i was able to use the internet from the guest machine how ever once the bridge was configured i have no internet access on the guest OS and still no access on the private network

my configuration file for the guest network:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# autmatic ifaces
auto lo br0

# LOOPBACK - localhost, 127.0.0.1, etc.
iface lo inet loopback


# BRIDGED ADAPTERS
#iface eth0 inet manual
#iface eth1 inet manual


# NETWORK BRIDGE eth0 <---> eth1
iface br0 inet static
        address 192.168.1.2
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports all
```

running an arp-scan on interface br0 gives these results
```
root@USS-Intrepid:~# arp-scan --localnet --interface=br0
Interface: br0, datalink type: EN10MB (Ethernet)
Starting arp-scan 1.8.1 with 256 hosts (http://www.nta-monitor.com/tools/arp-scan/)
192.168.1.1     20:aa:4b:a2:a0:e9       (Unknown)
192.168.1.3     00:13:d4:3b:bf:a1       ASUSTek COMPUTER INC.
192.168.1.134   ac:81:12:47:70:98       Gemtek Technology Co., Ltd.
192.168.1.142   00:13:c3:78:59:80       Cisco Systems
192.168.1.110   c0:9f:42:c6:9c:21       (Unknown)
192.168.1.113   00:1f:e1:3d:53:76       Hon Hai Precision Ind. Co., Ltd.
192.168.1.135   78:92:9c:99:04:00       Intel Corporate
192.168.1.107   00:d0:2d:2d:2e:f6       ADEMCO

8 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.8.1: 256 hosts scanned in 1.321 seconds (193.79 hosts/sec). 8 responded
```

address 192.168.1.142 is the catalyst 3550 
and address 192.168.1.3 is the centos server
i am also able to connect from host to guest using SSH
SSH connection from host (windows 7) to Centos server timed out also ping times out
SSH connection from Centos to guest works fine
before the br0 interface was configured i was able to access all network services on the Centos 6 server with a private lan address using the host machine
im not sure if it means anything but all ports on Catalyst 3550 all belong to the same VLAN
based on the connections being made or rather not connecting i would guess at this being an error in the way that Guest was configured any help in solving this would be very helpful

---

### Post by admmorketh on 2014-07-23
well after reading my post i looked back at the host network interfaces and relized i had not configured my NIC correctly since adding the bridged adapter connected the LAN Section to the Wifi i had to reconfigure my NIC for the new address how ever this only fixes the host seeing the Centos server the guest is still unable to connect to the internet as to is the Centos Server
this also added the NIC on the host to the arp-scan results with the new address i assigned but still no internet connection on guest or the LAN

---

### Post by TheFu on 2014-07-23
Does [http://manpages.ubuntu.com/manpages/trusty/man5/bridge-utils-interfaces.5.html](http://manpages.ubuntu.com/manpages/trusty/man5/bridge-utils-interfaces.5.html) help?

I've never used "all" for the bridge_ports, but the manpage says that should work.  However, I do always have the manual lines uncommented.
```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
  address 172.22.22.99
  gateway 172.22.22.1
  netmask 255.255.255.0
  broadcast 172.22.22.255
  # mtu 9014
  dns-nameservers 172.22.22.1
  dns-search example.com example.lan
  bridge_ports eth0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off

```
is what I use.

---

### Post by admmorketh on 2014-07-24
well i think maybe the DNS might be the fix i was looking for i havent had a chance to try it but i will post back once i have. after posting initially i ran more tests and found that i was able to ping google with the IP address but not with the name on every side of the bridge thank-you for the example i will have to try that. the man page was helpfull in the way of configuring it to start with as you may have noticed my configuration is straight off the first example of the man page.

---

### Post by TheFu on 2014-07-24
Solved? Please mark it as such in the thread tools.

---

### Post by admmorketh on 2014-07-24
not exactly solved the bridge DNS is now working however the Centos 6 server is still unable to get to the internet
(the switch is some what new to me so i may not have that configured correctly)
also i dont belive the DHCP is crossing the bridge i just tried attaching another laptop (windows 7) to the Catalyst and it auto-configured with a private lan address of 169.254.201.61
i am capable of making a cross-over cable if that would eliminate the need for the Catalyst however i would like to try and avoid that solution


EDIT: up untill now i was using static addresses on everything pluging in the windows 7 laptop was the only DHCP enabled device on the LAN Segment

---

