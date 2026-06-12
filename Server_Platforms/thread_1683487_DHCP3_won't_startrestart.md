---
title: "DHCP3 won't start/restart"
date: 2011-02-07
forum: Server Platforms
---

### Post by AcademyTS on 2011-02-07
[FONT=Arial]Ubuntu 10.10 w/ dual NICs


here's my etc/network/interfaces file:[/FONT]

[FONT=Courier New]auto eth0
iface eth0 inet static
    address 192.168.2.200
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.2.1

auto eth1
iface eth1 inet static
  address 192.168.3.2
  netmask 255.255.255.0
  network 192.168.3.0/24
  broadcast 192.168.3.255[/FONT]



[FONT=Arial]and the /etc/dhcp3/dhcpd.conf file:[/FONT]

[FONT=Courier New]option T150 code 150 = string;
ddns-update-style none;
ddns-updates on;
deny client-updates;
one-lease-per-client false;
allow bootp;
allow booting;
allow unknown-clients;
authoritative;
option ip-forwarding false;
option mask-supplier false;
default-lease-time 5184000;

subnet 192.168.3.0 netmask 255.255.255.0 {
   interface eth1;
    range 192.168.3.50 192.168.3.60;
    option subnet-mask 255.255.255.0;
    default-lease-time 6000;
    max-lease-time 7200;
    option time-offset -3600;
}
[/FONT]


[FONT=Arial]and the /etc/default/dhcp3-server file[/FONT]:

[FONT=Courier New]INTERFACES="eth1"[/FONT]


Here's the problem -- DHCP wont start and throws the error "Can't create PID file /var/run/dhcpd.pid: Permission denied." Somewhere I found a post that indicated that the following corrected the issue (I dont really know why):

ln -s /var/run/dhcp3-server/dhcpd.pid /var/run/dhcpd.pid
dhcpd3 -cf /etc/dhcp3/dhcpd.conf eth1

When I do the above DHCP will start (in theory, at least no erros are thrown). But if I ask DHCP to restart, it will stop, but not restart. And the error is "No subnet declaration for eth1 (192.168.3.2)"

I'm newbie-ish. Help me Obi-Wan Kenobi.

DS

---

### Post by elico on 2011-02-08
did you try to look at your log?

cat /var/log/syslog |grep dhcpd 

you will get verbose info from there.
you can check every thing in the 
/etc/init.d/dhcp3-server
file
it has info about the conf file location. and the real PID that the system is refering to..
it can be...
DHCPDPID=/var/run/dhcp3-server/dhcpd.pid
try to change the access to the file using 
chmod 777 /var/run/dhcp3-server/dhcpd.pid

just to narrow down the options.

and also make your basic dhcpd.conf file simple without any optons.
```

# Sample /etc/dhcp3/dhcpd.conf
# (add your comments here)
default-lease-time 7200;
max-lease-time 18000;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.101.255;
option routers 192.168.101.200;
option domain-name-servers 192.168.101.1;
# this is for the whole dhcp server

# lan
subnet 192.168.101.0 netmask 255.255.255.0 {
        option domain-name "lan";
        range 192.168.101.10 192.168.101.50;
        }
```

---

### Post by wormyblackburny on 2011-02-08
Looks to me like the /24 might be the problem (either way it is redundant to do so since you already defined the netmask sbove):
[FONT=Courier New]auto eth1
iface eth1 inet static
  address 192.168.3.2
  netmask 255.255.255.0
  _**network 192.168.3.0/24**_
  broadcast 192.168.3.255[/FONT]

Drop the /24 and see if that fixes it?

---

### Post by pfelip on 2011-11-06
Here is the solution to your problem:

[http://ubuntuforums.org/showthread.php?t=1092664](http://ubuntuforums.org/showthread.php?t=1092664)

The only thing you must do is to start/stop your service this way:

service isc-dhcp-server start
service isc-dhcp-server stop

---

### Post by pfelip on 2011-11-08
Just one more thing. I recommend you to consider configuring your network the easy way, I mean, edit /etc/network/interfaces and comment out (ie put a # in front of) or delete every line in the /etc/network/interfaces file except the two with lo in them- they read:

   auto lo
   iface lo inet loopback

After doing that, you can restart your system and then use the nm-applet on the taskbar to configure graphically your network interfaces.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

