---
title: "dhcp3 server install help"
date: 2012-06-02
forum: Server Platforms
---

### Post by 1885 on 2012-06-02
Here is my startup error:
root@io2:/etc/dhcp3# /etc/init.d/isc-dhcp-server start
 * Starting ISC DHCP server dhcpd                                                                * check syslog for diagnostics.
                                                                                         [fail]

All I want to do is set up a simple dhcp server.
on a close experimental network.  

Here is my conf
# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1,
option domain-name "e.com";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.90 192.168.1.100;
range 192.168.1.150 192.168.1.200;
}


Here is my interface:
  GNU nano 2.2.6              File: /etc/default/dhcp3-server                                   

option netbios-name-servers 192.168.1.1;
INTERFACES="eth0"


I'm using this guide:
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)


Here is my syslog:
Jun  2 07:34:25 io2 dhcpd: No subnet declaration for eth0 (192.168.1.20).
Jun  2 07:34:25 io2 dhcpd: ** Ignoring requests on eth0.  If this is not what
Jun  2 07:34:25 io2 dhcpd:    you want, please write a subnet declaration
Jun  2 07:34:25 io2 dhcpd:    in your dhcpd.conf file for the network segment
Jun  2 07:34:25 io2 dhcpd:    to which interface eth0 is attached. **
Jun  2 07:34:25 io2 dhcpd: 
Jun  2 07:34:25 io2 dhcpd: 
Jun  2 07:34:25 io2 dhcpd: Not configured to listen on any interfaces!


?  I thought I included an interface.
Any help would be appreciated.

---

### Post by coffee412 on 2012-06-02
Here is my working dhcpd.conf for you to build from. I use it on my shop server to assign an ip and backup files.

> subnet 10.0.1.0 netmask 255.255.255.0 {
    option routers 10.0.1.1;
    option subnet-mask 255.255.255.0;
    option domain-name-servers dino.athome.net;
    option ip-forwarding off;
    range dynamic-bootp 10.0.1.50 10.0.1.55;
    default-lease-time 21600;
    max-lease-time 43200;
}

Its very basic and gets the job done.

---

### Post by 1885 on 2012-06-02
> **coffee412 said:**
> Here is my working dhcpd.conf for you to build from. I use it on my shop server to assign an ip and backup files.



Its very basic and gets the job done.

thanks for the line snoopy.  I tried your script:

Here is my error on start:
Jun  2 07:53:32 io2 dhcpd: ** Ignoring requests on eth0.  If this is not what
Jun  2 07:53:32 io2 dhcpd:    you want, please write a subnet declaration
Jun  2 07:53:32 io2 dhcpd:    in your dhcpd.conf file for the network segment
Jun  2 07:53:32 io2 dhcpd:    to which interface eth0 is attached. **
Jun  2 07:53:32 io2 dhcpd: 
Jun  2 07:53:32 io2 dhcpd: 
Jun  2 07:53:32 io2 dhcpd: Not configured to listen on any interfaces!

---

### Post by coffee412 on 2012-06-02
Did you edit the config to match your setup? If you did could you post more info?

1. Your network setup

2. Your edited config file

---

### Post by 1885 on 2012-06-02
> **coffee412 said:**
> Did you edit the config to match your setup? If you did could you post more info?

1. Your network setup
root@io2:/etc/network# ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces  run
root@io2:/etc/network# more interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.20
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.30
    # dns-* options are implemented by the resolvconf package, if installed
    dns-search e.com
root@io2:/etc/network# 


2. Your edited config file
# Sample /etc/dhcpd.conf
# (add your comments here)

subnet 192.168.1.0  netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers e.com;
option ip-forwarding off;
range dynamic-bootp 192.168.1.200 192.168.1.240;
default-lease-time 21600;
max-lease-time 43200;
}

thanks

---

### Post by coffee412 on 2012-06-02
Please post the output of the following:

ifconfig

cat /etc/hosts

See if we can clear this up quick,

best regards,

coffee412

---

### Post by 1885 on 2012-06-02
> **coffee412 said:**
> Please post the output of the following:

ifconfig

cat /etc/hosts

See if we can clear this up quick,

best regards,

coffee412
root@io2:/# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:0b:57:50:e0  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:bff:fe57:50e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12056047 (12.0 MB)  TX bytes:1177674 (1.1 MB)
          Interrupt:22 Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7008 (7.0 KB)  TX bytes:7008 (7.0 KB)

virbr0    Link encap:Ethernet  HWaddr 62:12:14:d3:4e:90  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:74:03:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)root@io2:/# cat /etc/hosts


root@io2:/# cat /etc/hosts
hosts        hosts.allow  hosts.deny   
root@io2:/# cat /etc/hosts
127.0.0.1    localhost
192.168.1.20    io2.e.com    io2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@io2:/#

---

### Post by coffee412 on 2012-06-02
subnet 192.168.1.0  netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers e.com;

-----------------------
Line 2 is wrong - should be 192.168.1.20
Line 4 is wrong - should be io2.e.com

You list your dhcp server as 192.168.1.1 but I do not see that in your ifconfig output. Im assuming this is a wireless router. I run iptables on my ubuntu server as my router. 

Line 4 is listing your domain name server as e.com. I bet you cannot ping your listed domain server then. Update your config to reflect your actual domain server.

My router is 10.0.1.1 my dhcpd server is also 10.0.1.1 my domain is athome.net but my domain server is dino.athome.net (10.0.1.1).

Make the changes and see if things start to jell :)

---

### Post by 1885 on 2012-06-02
> **coffee412 said:**
> subnet 192.168.1.0  netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers e.com;

-----------------------
Line 2 is wrong - should be 192.168.1.20
Line 4 is wrong - should be io2.e.com

You list your dhcp server as 192.168.1.1 but I do not see that in your ifconfig output. Im assuming this is a wireless router. I run iptables on my ubuntu server as my router. 

Line 4 is listing your domain name server as e.com. I bet you cannot ping your listed domain server then. Update your config to reflect your actual domain server.

My router is 10.0.1.1 my dhcpd server is also 10.0.1.1 my domain is athome.net but my domain server is dino.athome.net (10.0.1.1).

Make the changes and see if things start to jell :)

thanks again.  no luck. made changes:
here's the error:
Jun  2 09:15:54 io2 dhcpd: 
Jun  2 09:15:54 io2 dhcpd: No subnet declaration for eth0 (192.168.1.20).
Jun  2 09:15:54 io2 dhcpd: ** Ignoring requests on eth0.  If this is not what
Jun  2 09:15:54 io2 dhcpd:    you want, please write a subnet declaration
Jun  2 09:15:54 io2 dhcpd:    in your dhcpd.conf file for the network segment
Jun  2 09:15:54 io2 dhcpd:    to which interface eth0 is attached. **
Jun  2 09:15:54 io2 dhcpd: 
Jun  2 09:15:54 io2 dhcpd: 
Jun  2 09:15:54 io2 dhcpd: Not configured to listen on any interfaces!
Jun  2 09:16:20 io2 dhclient: DHCPDISCOVER on virbr0 to 255.255.255.255 port 67 interval 3
Jun  2 09:16:22 io2 dhclient: DHCPDISCOVER on virbr0 to 255.255.255.255 port 67 interval 8
root@io2:/#

---

### Post by coffee412 on 2012-06-02
The default Debian install of DHCP doesn't bind it to any interface.  This is to stop a default DHCP configuration from polluting the network.  To bind and interface you need to make and entry in */etc/default/dhcp3-server* for example:
     Code:
     INTERFACES="eth1"

-------------------------------

coffee@dino:/etc/default$ cat isc-dhcp-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

---

### Post by 1885 on 2012-06-02
I have dhclient and dhcleint3 installed.
Do I remove those packages?

---

### Post by 1885 on 2012-06-02
> **coffee412 said:**
> The default Debian install of DHCP doesn't bind it to any interface.  This is to stop a default DHCP configuration from polluting the network.  To bind and interface you need to make and entry in */etc/default/dhcp3-server* for example:
     Code:
     INTERFACES="eth1"

-------------------------------

coffee@dino:/etc/default$ cat isc-dhcp-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

I have an interface set.  
I also notice I have dhclient3 and dhclient install.  
Should these be removed?

---

### Post by coffee412 on 2012-06-03
No, Leave them alone. They should not have anything to do with your problem. 

Ok. To recap and confirm:

1.You have checked your file /etc/defaults/isc-dhcp-server and have verified that it is set to the correct interface. 

2. You have double-checked your /etc/dhcpd.conf file to make sure the syntax and settings are correct?

3. You have restarted the dhcpd server after changes?

sudo service isc-dhcp-server restart

If you are still having problems then the ultimate quick fix is to copy your /etc/dhcpd.conf file to /etc/dhcpd.conf.bak and delete your dhcpd.conf file. Stop your dhcpd server. Then install firestarter and run thru the setup real quick and tell it you are going to run a dhcpd on your selected interface.

If you have your own firewall settings setup please back them up before running firestarter. 

This will clear up your problem(or should). Then for learnings sake, Compare the lines in your new dhcpd.conf file with those of your old one and see what was not right. 

coffee412

---

### Post by 1885 on 2012-06-04
> **coffee412 said:**
> No, Leave them alone. They should not have anything to do with your problem. 

Ok. To recap and confirm:

1.You have checked your file /etc/defaults/isc-dhcp-server and have verified that it is set to the correct interface. 

2. You have double-checked your /etc/dhcpd.conf file to make sure the syntax and settings are correct?

3. You have restarted the dhcpd server after changes?

sudo service isc-dhcp-server restart

If you are still having problems then the ultimate quick fix is to copy your /etc/dhcpd.conf file to /etc/dhcpd.conf.bak and delete your dhcpd.conf file. Stop your dhcpd server. Then install firestarter and run thru the setup real quick and tell it you are going to run a dhcpd on your selected interface.

If you have your own firewall settings setup please back them up before running firestarter. 

This will clear up your problem(or should). Then for learnings sake, Compare the lines in your new dhcpd.conf file with those of your old one and see what was not right. 

coffee412

I'm back.  I did a full re-install. :)  This is a test server.
I got "start isc-dhcp-server start to work"

Now the question is which dhcpd.conf file do i use?

/etc/dhcp/dhcpd.conf

/etc/dhcp3/dhcpd.conf

or do i create one at /etc/

Thanks for being patient:)

---

### Post by coffee412 on 2012-06-04
Mine is located in /etc/dhcpcd.conf

Depending on what you did it might have put it elsewhere.

Hope all is going well.

Best Regards,

coffee

---

### Post by coffee412 on 2012-06-04
> **1885 said:**
> I'm back.  I did a full re-install. :)  This is a test server.
I got "start isc-dhcp-server start to work"

Now the question is which dhcpd.conf file do i use?

/etc/dhcp/dhcpd.conf

/etc/dhcp3/dhcpd.conf

or do i create one at /etc/

Thanks for being patient:)


Have you read this yet?

[https://help.ubuntu.com/12.04/serverguide/dhcp.html](https://help.ubuntu.com/12.04/serverguide/dhcp.html)

---

### Post by 1885 on 2012-06-05
Solved.

- Reinstalled
- Set up static ip.
- Edited /etc/dhcp/dhcpd.conf
- Started service 
root@io2:/etc/dhcp# /etc/init.d/isc-dhcp-server start

root@io2:/etc/dhcp# more dhcpd.conf
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.200 192.168.1.250;
}

---

