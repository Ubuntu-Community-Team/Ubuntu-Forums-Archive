---
title: "DHCP server for small lan"
date: 2012-04-04
forum: Server Platforms
---

### Post by samopal on 2012-04-04
Dear ubuntu comunity, 

I've got a big multi-purpose server where Ubuntu 11.04 is running. I've made a basic dhcp server based on the official documentation. 
```

authoritative; 
default-lease-time 21600;
max-lease-time 21600;
INTERFACES="eth1"; 

subnet 192.168.1.0 netmask 255.255.255.0 {
 interface eth1;
 range 192.168.1.10 192.168.1.90;
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 option domain-name-servers 192.168.1.1;
 option subnet-mask 255.255.255.0;
} 

# host hp-server { hardware ethernet 00:1C:C4:96:5C:38; fixed-address 192.168.1.9;}

# zberne dat 
host zber01 { hardware ethernet 00:1B:EB:20:2D:38; fixed-address 192.168.1.121; } 
host zber02 { hardware ethernet 00:1B:EB:21:18:1F; fixed-address 192.168.1.122; } 
host zber03 { hardware ethernet 00:1B:EB:35:12:6A; fixed-address 192.168.1.123; } 
host zber04 { hardware ethernet 00:1B:EB:21:18:1A; fixed-address 192.168.1.124; } 
#host zber05 { hardware ethernet xxxmac; fixed-address 192.168.1.125; } 
#host zber06 { hardware ethernet xxxmac; fixed-address 192.168.1.126; } 
#host zber07 { hardware ethernet xxxmac; fixed-address 192.168.1.127; } 
#host zber08 { hardware ethernet xxxmac; fixed-address 192.168.1.128; } 

# pouzivatelia 
host user1 { hardware ethernet 00:19:DB:D2:7D:93; fixed-address 192.168.1.150;}
host user2 { hardware ethernet C4:17:FE:02:60:19; fixed-address 192.168.1.151;}
host user3 { hardware ethernet 50:E5:49:27:86:B3; fixed-address 192.168.1.152;}
host user4 { hardware ethernet F4:CE:46:F0:E8:7D; fixed-address 192.168.1.153; }

# ostatne 
host alnet-server { hardware ethernet 00:1E:8C:1B:05:C8; fixed-address 192.168.1.97;}
host qi-xp { hardware ethernet 08:00:27:CA:E3:6F; fixed-address 192.168.1.101;}
host deb-java { hardware ethernet 08:00:27:28:18:64; fixed-address 192.168.1.102; }
host canon4660.printer { hardware ethernet 00:00:85:9F:A2:84; fixed-address 192.168.1.103;}
host akvarko.alnet-server { hardware ethernet 00:24:1D:88:C0:85; fixed-address 192.168.1.108;}
host narezovna-masina { hardware ethernet 00:24:1D:88:C0:85; fixed-address 192.168.1.109;}
host qi-win7 { hardware ethernet 08:00:27:C6:67:B9; fixed-address 192.168.1.111; }

# sietove prvky 
host asus-danad.net { hardware ethernet 00:1E:8C:D0:70:B8; fixed-address 192.168.1.200; ddns-hostname "asus-danad.net"; }
```

my questions/issues: 
1, sometimes, when I just edit MAC address somewhere (physical machine is replaced by a new one and the old one is thrown out) and restart the server daemon with 
```
/etc/init.d/isc-dhcp-server restart
```
it says on the new machine that there is an IP address conflict. I have to assign a new IP to a new MAC, I can't re-use them, so I'll run out of IP's in my subnet quickly :) 

2, just today, suddenly, 5 computers on my network stopped to work, their networking was in the state "acquiring IP address". It doesn't matter if this or that PC was with mapped MAC-IP in config file, or without (IP was assigned to it dynamically). They were not able to get IP address at all, they were effectively stuck, all of them at once. Only way to work around that was to set-up static IP address/subnet/gateway to them temporarily. 

3, don't know how to set-up logging of dhcp server itself (not just leases). I've seen some guides around but they don't seem to apply to my ubuntu version.

I'm new to dhcp server, this is my first, I don't know how to fix these issues, I've tried to set-up DHCP leases to more aggresive value, no help. 

edit: dhcp server is at 192.168.1.9 (ubuntu 11.04 64bit), router is at 192.168.1.1 (including DNS). I've tried to set up my own DNS server but I find it complicated and not necessary for such a small network.

---

