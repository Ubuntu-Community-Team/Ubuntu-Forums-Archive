---
title: "LTSP server having problems"
date: 2015-12-02
forum: Server Platforms
---

### Post by Howard_Jeffrey on 2015-12-02
Hello I am trying to set up a 12 client LTSP server on a 4x dual core RAID 5 100GB HD 2GB RAM with ubuntu 14.04 server. I got local network with internet access on one LAN card and the group of about 12 thin clients networked to a 2nd second LAN card. Using a "Thin Client Howto" in the community help wiki as a guide, I went through the install of the ltsp-server-standalone, openssh-server packages and they seemed to install w/o problems. I ran ltsp-build-client and it completed sucsessfully, but I couldn't get the clients to boot to it. I made some adjustments to dhcpd.conf and /opt/ltsp/i386/etc/ssh/ssh_known_hosts according to the how-to.

dhcpd.conf:
--------------------------------------------------------------------------------
##
# DHCP for LTSP and Phones 
#

authoritative;

option tftp-server-name "192.168.0.254";
option domain-name "example.org";
option ntp-servers 192.168.0.9;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.50;
    option domain-name-servers 192.168.0.254;
    #option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    #option routers 192.168.0.1;
    option routers 192.168.0.254;

#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}


##
# Phones
#
host x107 {
    hardware ethernet 00:08:5d:1b:ef:99;
    fixed-address 192.168.0.107;
-----------------------------------------------------------------------------------


I added 192.168.0.254 before the "ssh-rsa..." and "ssh-dss..." lines on ssh_known_hosts file also.

When I try to PXE boot the clients it just goes to non system disk error after looking for the image on the network.

Not sure where to go from here. Any help appreciated.

---

### Post by Howard_Jeffrey on 2015-12-03
Another thing I am noticing is upon bootup of the server I get "FAIL" after "Starting IS BHCP IPv4 server".

---

### Post by Howard_Jeffrey on 2015-12-04
So I figured out that the network isn't configured properly. I have 2 Ethernet cards installed but when I run ifconfig it only displays eth1 and lo, so eth0 isn't even configured is what that means, right?

eth1 goes to the router and seems to be accessing the internet just fine, eth0 is connected to my network of thin clients. I believe I need to investigate the /etc/network/interfaces file at this point? Any guidance would be helpful... thanks.

---

### Post by cariboo on 2015-12-05
Could you paste the output of the following command in your next post:

```
sudo lshw -C nework
```

---

### Post by Howard_Jeffrey on 2015-12-08
So I think I got the network configured now after correcting a type-o in /etc/network/interfaces. Strange though the command sudo lshw -C network didn't output anything?? I just ran sudo lshw w/o any options and here is the portion that contained ethernet information:

```

     *-bridge:0
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:08.0
          logical name: eth0
          version: a3
          serial: 00:30:48:7b:e2:e8
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.254 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
     *-bridge:1
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: eth1
          version: a3
          serial: 00:30:48:7b:e2:e9
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.106 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s

```

and the output of ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:30:48:7b:e2:e8  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe7b:e2e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49376713 (47.0 MB)  TX bytes:2467264864 (2.2 GB)
          Interrupt:218 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:30:48:7b:e2:e9  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe7b:e2e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:983576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:957868911 (913.4 MB)  TX bytes:219349989 (209.1 MB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2096666 (1.9 MB)  TX bytes:2096666 (1.9 MB)

```

So I'm still unable to boot the clients, just goes to non system disk error after displaying "DHCP..." with the spinning slash. I'm assuming that means they are not getting assigned IP addresses? something with my DHCP config files? the dhcpd.conf file is the same as listed in my original post. Any ideas???

---

### Post by Howard_Jeffrey on 2015-12-08
OH, Also still getting a fail at bootup but it flashes by so fast I can't tell what it is. Probably still the line that says IPv4 DHCP, its in the same general area anyway.

---

### Post by newbie-user on 2015-12-08
It's been a while since I ran ltsp in my environment, but I'm pretty sure you need the next-server line to be uncommented and pointing to your ltsp server:

```
next-server 192.168.0.254;
```

---

### Post by Howard_Jeffrey on 2015-12-09
I gave that a whirl and the server booted with the same symptoms. Try to connect a client to it and it just spins at DHCP... :(

I have a working server (the one we're trying to replace) with 8.04 Hardy Heron, that line is commented out it it's dchpd.conf too. It's been handy to have as I have been using it to compare things... I just don't know what else to look at? :( any advise would be so helpful, please.

I used this tutorial [ [http://moo.nac.uci.edu/~hjm/LTSP_HOWTO.html](http://moo.nac.uci.edu/~hjm/LTSP_HOWTO.html) ] to set up the new server. I basically started at 4.2 "Installing over a pre-installed system" because we had this other machine with a fresh install of 14.04 on it. Other than that it's the same infrastructure as far as the router, switch, and cables and whatnot. I am stumped :(

---

