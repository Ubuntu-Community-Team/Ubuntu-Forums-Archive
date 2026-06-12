---
title: "Starting IC DHCP IPv4 Server [FAIL]"
date: 2015-12-11
forum: Server Platforms
---

### Post by Howard_Jeffrey on 2015-12-11
I have a Ubuntu 14.04 Server system I am trying to set up for an LTSP PXE server. When starting up I get an error that says:

Starting IC DHCP IPv4 Server                                [FAIL]

I set up dhcpd.conf and isc-dhcp-server according to this tutorial: [http://moo.nac.uci.edu/~hjm/LTSP_HOWTO.html](http://moo.nac.uci.edu/~hjm/LTSP_HOWTO.html).

Been struggling for WEEKS trying to figure this out. Any help would be appreciated.

---

### Post by SeijiSensei on 2015-12-11
Not much we can do until we see the contents of dhcpd.conf.  Please post it inside of [noparse]```

```[/noparse] tags.

---

### Post by newbie-user on 2015-12-11
Also check to see if you specified which interface will serve DHCP in /etc/default/isc-dhcp-server

---

### Post by Howard_Jeffrey on 2015-12-14
```

##
# DHCP for LTSP and Phones 
#

authoritative;

option tftp-server-name "192.168.0.254";
option domain-name "thcf.org";
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

```

and eth0 is my client network.

---

### Post by SeijiSensei on 2015-12-15
I don't see anything strange in that file.  What do you see in /var/log/syslog when you try and start the server?

---

### Post by Howard_Jeffrey on 2015-12-15
I will boot and try to capture that info tonight after everyone leaves. What should I be looking for log files can be huge I'm not very good at reading them.

Also is there any commands I can run to get a more detailed error message that would be helpful? Restarting DHCP maybe? IDK

A little more background on infrastructure I have a 2 NIC card server ETH1 connected to our internet router and ETH0 connected to a handful of clients via a switch. Not sure if I mentioned this or not but I used the ltsp-server-standalone and openssh-server packages to get everything "set up"

---

### Post by SeijiSensei on 2015-12-16
```
sudo grep dhcp /var/log/syslog
```
will display only the lines with the string "dhcp" in them.

However you can limit your attention to just the entries that appear when you try to start the DHCP server.  If you're running a server without a GUI, you can switch to a new terminal with Alt-F2 (or Alt-F3, etc. until you find one with a login prompt).  In that window, log in again and issue the command
```
sudo tail -f /var/log/syslog
```
then switch back to the original window (usually Alt-F1) and issue the service command to start DHCP.  You'll see the log entries appear in the other window.

---

### Post by Howard_Jeffrey on 2015-12-16
OK so this is what I found in the log yesterday

```

Dec  3 16:35:58 cosmosis2 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x7425d748)
Dec  3 16:35:59 cosmosis2 dhclient: DHCPREQUEST of 192.168.1.29 from 192.268.1.1
Dec  3 16:35:59 cosmosis2 dhclient: DHCPOFFER of 192.168.1.29 from 192.168.1.1
Dec  3 16:35:59 cosmosis2 dhclient: DHCPACK of 192.168.1.29 from 192.168.1.1
Dec  3 16:36:00 cosmosis2 dhcpd: Internet Systems Consortium DHCP Server 4.2.4
Dec  3 16:44:34 cosmosis2 dhclient: DHCPREQUEST of 192.168.1.29 from 192.268.1.1
Dec  3 16:44:34 cosmosis2 dhclient: DHCPOFFER of 192.168.1.29 from 192.168.1.1
Dec  3 16:44:34 cosmosis2 dhclient: DHCPACK of 192.168.1.29 from 192.168.1.1
Dec  3 16:44:34 cosmosis2 dhcpd: Internet Systems Consortium DHCP Server 4.2.4
Dec  3 17:12:08 cosmosis2 dhclient: DHCPREQUEST of 192.168.1.29 from 192.268.1.1
Dec  3 17:12:08 cosmosis2 dhclient: DHCPOFFER of 192.168.1.29 from 192.168.1.1
Dec  3 17:12:08 cosmosis2 dhclient: DHCPACK of 192.168.1.29 from 192.168.1.1
Dec  3 17:12:08 cosmosis2 dhcpd: Internet Systems Consortium DHCP Server 4.2.4
Dec 15 17:04:20 cosmosis2 dhcpd: Internet Systems Consortium DHCP Server 4.2.4

```

So there were records from 12-3 which is when I set this up and tried booting a client to it. I noticed the requests coming from Eth1? I was told the clients should be Eth0 and Eth1 going to the router. The internet seems to work fine as the packages downloaded and installed no problem and I'm pretty sure I have the network configured accordingly. Here is the output of ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:30:48:7b:e2:e8  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe7b:e2e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3760339 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2583576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1120665450 (1.0 GB)  TX bytes:305495391 (291.3 MB)
          Interrupt:219 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:30:48:7b:e2:e9  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe7b:e2e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113113696 (107.8 MB)  TX bytes:37193034 (35.4 MB)
          Interrupt:218 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48380 (47.2 KB)  TX bytes:48380 (47.2 KB)

```

---

### Post by SeijiSensei on 2015-12-16
> **Howard_Jeffrey said:**
> OK so this is what I found in the log yesterday
```

Dec  3 16:35:58 cosmosis2 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x7425d748)
Dec  3 16:35:59 cosmosis2 dhclient: DHCPREQUEST of 192.168.1.29 from 192.268.1.1
Dec  3 16:35:59 cosmosis2 dhclient: DHCPOFFER of 192.168.1.29 from 192.168.1.1
Dec  3 16:35:59 cosmosis2 dhclient: DHCPACK of 192.168.1.29 from 192.168.1.1

```

I can't tell where these entries are coming from.  The "dhclient" program, as the name suggests, is the client that obtains an address from a running DHCP server.  Also I don't know why you have 192.**268**.1.1 as the server's address.  Something is definitely not right there.

I recommend explicitly setting eth0 as the interface in the configuration file /etc/default/isc-dhcp-server.  On "multi-homed" machines like yours, it's often best to specify the interface explicitly.

Also are the server's two IP addresses set manually?  While that's not a requirement for a DHCP server, I always prefer to use static addressing on servers so I know for sure what is happening.

---

### Post by Howard_Jeffrey on 2015-12-17
I realized after I left last night that the december 3rd stuff was my first boot after installing. At that time Eth0 wasn't set up at all and Eth1 was not set up with a static IP address. I have since changed the network configuration so both are static at 192.168.1.106 for Eth1 and 192.168.0.254 for Eth2. I guess the only relevant entry regarding DHCP in syslog is this one:

```

Dec 15 17:04:20 cosmosis2 dhcpd: Internet Systems Consortium DHCP Server 4.2.4

```

Damn I thought I was on to something :( anything else I should look at?

---

### Post by SeijiSensei on 2015-12-17
Wait, so now you have an eth1 and an eth2?  What happened to eth0?  Is eth2 facing the network handled by the DHCP server?  If so, you almost certainly need to specify eth2 in /etc/default/isc-dhcp-server.

---

### Post by Howard_Jeffrey on 2015-12-17
No no, sorry. Eth0 and Eth1. I only have 2 nic cards. I only have eth0 listed in isc-dhcp-server. 

Eth0 faces the switch the clients are plugged into. Eth1 faces our router and seems to receive internet data just fine. Sorry about the 1 and 2 thing, <insert excuse here> lol

The switch and cables and clients are already there and function with an older PXE server. It's running ubuntu 8.04 though so some stuff is different as I am struggling to learn all this.

---

