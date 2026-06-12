---
title: "Dhcp3 server problems"
date: 2011-08-31
forum: Server Platforms
---

### Post by {davros} on 2011-08-31
ok I am configuring my 10.4.3 server with dhcp3-server snd it is up and running but the ip's it gives out will not connect to the internet.

here is a paste of my settings and different reporting.

...route -n


Destination    Gateway       Genmask         Flags  Metric  Ref      Use  Iface
192.168.1.0    0.0.0.0       255.255.255.0   U      0       0        0  eth1
66.189.112.0   0.0.0.0       255.255.252.0   U      0       0        0  eth0
0.0.0.0        66.189.112.1  0.0.0.0         UG     100     0        0  eth0


..the dhcpd.conf

subnet  192.168.1.0 netmask 255.255.255.0 {
 range  192.168.1.10 192.168.1.200;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 192.168.1.1, 192.168.1.2;
  option domian-name "mine.org";
  option routers 192.168.1.254;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}


..here is the /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 66.189.114.152



..and finally my ifconfig....



eth0 Link encap:Ethernet HWaddr 00:50:45:01:08:ba 
net addr:66.189.114.152 Bcast:255.255.255.255 Mask:255.255.252.0
inet6 addr: fe80::250:45ff:fe01:8ba/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:7613 errors:0 dropped:0 overruns:0 frame:0
TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2500624 (2.5 MB) TX bytes:206021 (206.0 KB)
Interrupt:27 

eth1 Link encap:Ethernet HWaddr 00:50:45:01:08:bb 
inet addr:192.168.1.2 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0 MB) TX bytes:0 (0 KB)
Interrupt:27 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:190 errors:0 dropped:0 overruns:0 frame:0
TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:24703 (24.7 KB) TX bytes:24703 (24.7 KB)


how can I fix this issue ? Thank you in advance.

---

### Post by {davros} on 2011-09-03
nobody?

---

### Post by Zeosa on 2011-09-03
What are your clients getting from the server? (if they're windows clients post the output of ipconfig /all)

Are the settings for your dns servers correct? i.e., do you have working dns services running on 192.168.1.1 and 192.168.1.2? and is your router (gateway) actually at 192.168.1.254?

---

### Post by {davros} on 2011-09-03
ok its actullay looking like this now....

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
option subnet-mask 255.255.255.0;
option domain-name "mine.org";
option routers 192.168.1.0;
option broadcast-address 192.168.1.255;
default-lease-time 600;
max-lease-time 7200;
}

i took the router and made it the servers address at least i thought i did,i also want to make an access point but thats prolly easier than this  i havent set the wireless router/access point up yet. my provider changed my ip and its mask today new mask is 255.255.240.0 from the provider.

"workstations" are all linux 2 slackwares and one ubuntu 10.4 they are all getting ip's assigned to them with in the range. but have no connection to the internet. webpages or pinging known hosts. theres one macbook in the house but that will be wireless only from the access point once i get this all situated and up and running correctly. 

i'm thinking bad gateway , but i honestly have no idea. this is the first server i have ever attempted to configure and its ending up to be quite challenging/frustrating.

---

### Post by {davros} on 2011-09-03
oh heres the lease info as it was before the ip got changed this morning...


lease from server...

lease {
interface "eth0";
fixed-address 66.189.114.152;
option subnet-mask 255.255.252.0;
option time-offset -14400;
option routers 66.189.112.1;
option dhcp-lease-time 3600;
option dhcp-message-type 5;
option domain-name-servers 66.189.0.100,24.159.64.23,24.247.24.53;
option dhcp-server-identifier 68.114.38.40;
option interface-mtu 576;
option broadcast-address 255.255.255.255;
option host-name "server";
renew 4 2011/09/01 18:24:43;
rebind 4 2011/09/01 18:52:43;
expire 4 2011/09/01 19:00:13;
}


lease info from one "client"


lease {
interface "eth0";
fixed-address 192.168.1.11;
option subnet-mask 255.255.255.0;
option routers 192.168.1.254;
option dhcp-lease-time 600;
option dhcp-message-type 5;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option dhcp-server-identifier 192.168.1.5;
option broadcast-address 192.168.1.255;
option domain-name "mine.org;
renew 4 2011/09/01 18:19:14;
rebind 4 2011/09/01 18:23:12;
expire 4 2011/09/01 18:24:27;
}

---

### Post by Zeosa on 2011-09-03
What is the actual internal IP of your router?

Also, in your 'new' configuration, you're not assigning any dns servers, try for now just assigning the routers ip as they typically forward dns requests to your isp. I also added google's public DNS servers as 'backups' for now.


```

subnet 192.168.1.0 netmask 255.255.255.0 {
     range 192.168.1.10 192.168.1.200;
     option domain-name-servers 192.168.1.1 , 8.8.8.8 , 8.8.4.4;     
     option subnet-mask 255.255.255.0;
     option domain-name "mine.org";
     option routers 192.168.1.1;
     option broadcast-address 192.168.1.255;
     default-lease-time 600;
     max-lease-time 7200;
}

```

This should work assuming your router ip is 192.168.1.1...

---

### Post by {davros} on 2011-09-03
ok can i ask how you came to the 192.168.1.1 address for the router? i dont have a router, other than the server its self. 

modem -> server -> switch -> clients and access wireless point. 

i'm just curious so that i understand this :)

---

### Post by {davros} on 2011-09-03
oh and do i need to have the gateway line in this 
/etc/network/interfaces

auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway myipfromprovider

---

### Post by {davros} on 2011-09-03
and unfortunately no it still doesn't have online connections


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
71.87.208.0     0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         71.87.208.1     0.0.0.0         UG    100    0        0 eth0



eth0      Link encap:Ethernet  HWaddr 00:50:45:01:08:ba  
          inet addr:71.87.208.93  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::250:45ff:fe01:8ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1591071 (1.5 MB)  TX bytes:257811 (257.8 KB)
          Interrupt:27 

eth1      Link encap:Ethernet  HWaddr 00:50:45:01:08:bb  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.255
          inet6 addr: fe80::250:45ff:fe01:8bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:122944 (122.9 KB)  TX bytes:5213 (5.2 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9012 (9.0 KB)  TX bytes:9012 (9.0 KB)




subnet 192.168.1.0 netmask 255.255.255.0 {
     range 192.168.1.10 192.168.1.200;
     option domain-name-servers 192.168.1.1 , 8.8.8.8 , 8.8.4.4;     
     option subnet-mask 255.255.255.0;
     option domain-name "mine.org";
     option routers 192.168.1.1;
     option broadcast-address 192.168.1.255;
     default-lease-time 600;
     max-lease-time 7200;
}


lease from server 

lease {
  interface "eth0";
  fixed-address 71.87.208.93;
  option subnet-mask 255.255.240.0;
  option time-offset -14400;
  option routers 71.87.208.1;
  option dhcp-lease-time 79507;
  option dhcp-message-type 5;
  option domain-name-servers 66.189.0.100,24.159.64.23,24.247.24.53;
  option dhcp-server-identifier 68.114.38.40;
  option interface-mtu 576;
  option broadcast-address 255.255.255.255;
  option host-name "server";
  renew 6 2011/09/03 23:55:22;
  rebind 0 2011/09/04 10:23:53;
  expire 0 2011/09/04 13:09:32;
}

lease from client...

lease {
  interface "eth0";
  fixed-address 192.168.1.13;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1,8.8.8.8,8.8.4.4;
  option dhcp-server-identifier 192.168.1.2;
  option broadcast-address 192.168.1.255;
  option domain-name "mine.org"
  renew 6 2011/09/03 15:13:41;
  rebind 0 2011/09/04 15:17:42;
  expire 0 2011/09/04 15:18:57;
}

---

### Post by Zeosa on 2011-09-03
So you're using your server as a router? If so, then use it's ip as the gateway address in your configuration. I just used that address as an example sorry I wasn't more clear.

Also, this brings a whole new level of potential problems into the fray, are you certain you have ip forwarding/masquerading set up properly on your server so it can function as a gateway? Does you're server itself  have connectivity at this point?

---

### Post by {davros} on 2011-09-03
ahhh ok so the given ip from provider it the option routers address. 

 ip forwarding/masquerading i do not know if that is operational ....after looking it up id say no it is not. 

and yes it is online

---

### Post by {davros} on 2011-09-03
ok so i followed this.... [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

idk what it did but all went threw

---

