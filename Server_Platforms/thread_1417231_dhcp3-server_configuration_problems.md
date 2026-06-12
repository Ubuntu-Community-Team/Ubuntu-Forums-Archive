---
title: "dhcp3-server configuration problems"
date: 2010-02-27
forum: Server Platforms
---

### Post by nerr on 2010-02-27
Hello, I'm attempting to run a DHCP server on my home network to enable PXE booting for ethernet clients, but I'm having quite a few issues getting it all up and running.  I'm not entirely sure what is wrong, but I keep encountering errors in syslog as follows:

```
Feb 27 02:26:46 servnerr-1 dhcpd: Wrote 0 leases to leases file.
Feb 27 02:26:46 servnerr-1 dhcpd:
Feb 27 02:26:46 servnerr-1 dhcpd: No subnet declaration for eth0 (192.168.1.3).
Feb 27 02:26:46 servnerr-1 dhcpd: ** Ignoring requests on eth0.  If this is not what
Feb 27 02:26:46 servnerr-1 dhcpd:    you want, please write a subnet declaration
Feb 27 02:26:46 servnerr-1 dhcpd:    in your dhcpd.conf file for the network segment
Feb 27 02:26:46 servnerr-1 dhcpd:    to which interface eth0 is attached. **
Feb 27 02:26:46 servnerr-1 dhcpd:
Feb 27 02:26:46 servnerr-1 dhcpd:
Feb 27 02:26:46 servnerr-1 dhcpd: Not configured to listen on any interfaces!

```I am attempting to set this server up on a box with one ethernet interface (eth0), and a static IP address of 192.168.1.3.  I have set INTERFACES="eth0" in /etc/default/dhcp3-server.  Here is all the information I can provide:

**dhcpd.conf:**
```
authoritative;

default-lease-time 3600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.3;
option domain-name-servers 192.168.1.1;

option time-offset -18000;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.150;
range 192.168.1.200 192.168.1.254;
}
option netbios-name-servers 192.168.1.3;
```**ifconfig information for eth0:**
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:8b:e1:a2
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::20a:e4ff:fe8b:e1a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30004274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23587990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:875400748 (875.4 MB)  TX bytes:4128397250 (4.1 GB)
          Interrupt:16
```**/etc/network/interfaces:**
```
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.254.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```Networking is not exactly my strong suit, but I would like to get this up and running if at all possible.  I will continue to research myself, but any information that could be helpful would be very much appreciated.  Thank you!

---

### Post by ICEB3AR on 2010-02-27
I would expect that the declaration of you dhcp-server's subnet (255.255.255.0) is not the same subnet of your nic-configuration (255.255.254.0). 
To my mind this should be the solution. 
And be sure to change both values of subnet-masks in your dhcpd.conf
Best Regards

---

### Post by nerr on 2010-02-27
No such luck, the same error occurs unfortunately.  Thank you for your time though.

---

### Post by ICEB3AR on 2010-02-27
Can you tell me what you have changed? Because on your Interface (eth0) you say netmask 255.255.254.0 that means:

Address:   192.168.1.0           11000000.10101000.0000000 1.00000000
Netmask:   255.255.254.0 = 23    11111111.11111111.1111111 0.00000000
Wildcard:  0.0.1.255             00000000.00000000.0000000 1.11111111
=>
Network:   192.168.0.0/23        11000000.10101000.0000000 0.00000000 (Class C)
Broadcast: 192.168.1.255         11000000.10101000.0000000 1.11111111
HostMin:   192.168.0.1           11000000.10101000.0000000 0.00000001
HostMax:   192.168.1.254         11000000.10101000.0000000 1.11111110
Hosts/Net: 510 
And you define: network 192.168.1.0 isn't it 192.168.0.0 ?
Same thing on DHCP. So the Information have to be the same, that dhcp-server can identify your eth0 with the subnetdeclaration.

Another thing which caught my eye was: 
option routers 192.168.1.3;
in your dhcpd.conf.
Option routers defined as far as i know the gateway for the dhcp-clients. So i don't think your dhcp-server is your gateway. 192.168.1.1 could possibly your gateway.

---

### Post by nerr on 2010-02-27
I now realize that I may have made a mistake when setting up the static IP on eth0, and have now modified its subnet mask to 255.255.255.0.   I also modified the network declaration in /etc/network/interfaces to 192.168.0.0 and the subnet declaration in dhcpd.conf to 192.168.0.0.  Here's the current state of dhcpd.conf and /etc/network/interfaces:

**dhcpd.conf**
```
authoritative;
ddns-update-style none;

default-lease-time 3600;
max-lease-time 7200;
option domain-name "nerr.ath.cx";
#option subnet-mask 255.255.255.0;
#option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;

option time-offset -18000;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.150;
}
option netbios-name-servers 192.168.1.3;
```**/etc/network/interfaces**
```
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        pre-up iptables-restore < /etc/iptables.rules
        post-down iptables-save > /etc/iptables.rules
```

---

### Post by Iowan on 2010-02-27
Any change after restarting?

---

### Post by ICEB3AR on 2010-02-28
Okay so you say at your dhcp config:
```
subnet 192.168.0.0 netmask 255.255.255.0
```
that means that your dhcp could give addresses in the range: 192.168.0.x and x is not allowed to be 0 and not 255 because of broadcast etc. 
But your Network-Connection has address 192.168.1.x (x == 3) in the subnet 255.255.255.0
that means everything you only have to change the above Code to ```
subnet 192.168.1.0 netmask 255.255.255.0
``` that it is in your subnet. 

And the same in your Interfaces-file:
```
network 192.168.0.0
```
Should become 
```
network 192.168.1.0
```

Then everything should work properly.
Maybe you want to have a look at [http://en.wikipedia.org/wiki/Subnetwork]("http://en.wikipedia.org/wiki/Subnetwork") :)

Sorry if i was to confusing :D

---

### Post by nerr on 2010-02-28
Still no good, after a few restarts and modifying the config files as follows:

**/etc/network/interfaces**
```
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        pre-up iptables-restore < /etc/iptables.rules
        post-down iptables-save > /etc/iptables.rules
```**dhcpd.conf**
```
authoritative;
ddns-update-style none;

default-lease-time 3600;
max-lease-time 7200;
option domain-name "nerr.ath.cx";
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;

option time-offset -18000;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.150;
}
option netbios-name-servers 192.168.1.3;
```I'm almost wondering if I should just buy a second network interface and use it strictly for LAN communication at this point.  Perhaps that would be beneficial.

---

### Post by ICEB3AR on 2010-02-28
Your configuration should be okay. I don't know why he did not found your subnet declaration. The only thing which comes up to my mind is that he did not use the right dhcpd.conf .... you could try this by moving your dhcpd.conf to another directory and try to (re)start dhcp3-server if he say's that there is no configuration file then I don't know. Else your dhcpd.conf is obviously on the wrong place.

But the 2. NIC has to be also configured ;)

---

### Post by nerr on 2010-02-28
I figured it out!  Thanks so much for your help!  /etc/init.d/dhcp3-server checks to see if LTSP is installed early on in the script, and if it is, it uses the config file in **/etc/ltsp/dhcpd.conf** instead of **/etc/dhcp3/dhcpd.conf**!  I wish I would have known this in the first place!  Thanks so much!

---

