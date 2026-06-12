---
title: "Heartbeat doesn't listen services like apache2 and mysql"
date: 2012-10-10
forum: Server Platforms
---

### Post by XaviBS on 2012-10-10
I'm trying to set a HA cluster with two nodes master/slave with drbd, heartbeat, apache2 and mysql.

I'm using a dedicated eth for heartbeat in order to listen both nodes. 

When the master turns off then the slave node takes the control and  heartbeat inicializes apache2 and mysql previously off.

The problem is when I simulate an apache2 or mysql fault turning off manually (/etc/init.d/apache2 stop). In that case heartbeat doesn't realize that apache2 is off and doesn't switch to slave node. 


**_The system configurations_**

Ubuntu Server 12.04.1 LTS
Apache 2.2.22 (Ubuntu)
MySQL 5.5
Heartbeat 3.0.5
DRDB 8.3.2


**_DRBD configuration_**

(/etc/drbd.conf)
```

#include "drbd.d/global_common.conf";
#include "drbd.d/*.res";
global {
usage-count yes;
}
common {
  syncer { rate 100M; }
}

resource r0 {
  protocol C;
  handlers {
    pri-on-incon-degr "echo o > /proc/sysrq-trigger ; halt -f";
    pri-lost-after-sb "echo o > /proc/sysrq-trigger ; halt -f";
    local-io-error "echo o > /proc/sysrq-trigger ; halt -f";
    split-brain "/usr/lib/drbd/notify-split-brain.sh root";
  }

  startup {
    degr-wfc-timeout 60;    
  }

  disk {
    on-io-error   detach;
  }

  net {
  }

  syncer {
    rate 100M;
    al-extents 257;
  }

on machine01 {
    device /dev/drbd0;
    disk /dev/sda2;
    address 172.168.1.71:7788;
    meta-disk internal;
  }

on machine02 {
    device /dev/drbd0;
    disk /dev/sda2;
    address 172.168.1.73:7788;
    meta-disk internal;
  }
}
```


**_Heartbeat conf_**

(/etc/ha.d/ha.cf) master node (machine01):

```
debugfile /var/log/ha-debug
logfacility local0
logfile /var/log/ha-log
keepalive 1
deadtime 30
warntime 10
initdead 120
udpport 694
ucast eth1 172.168.1.73
auto_failback on
node machine01
node machine02

```


(/etc/ha.d/ha.cf) slave node (machine02):

```
debugfile /var/log/ha-debug
logfacility local0
logfile /var/log/ha-log
keepalive 1
deadtime 30
warntime 10
initdead 120
udpport 694
ucast eth1 172.168.1.71
auto_failback on
node machine01
node machine02
```


(/etc/ha.d/haresources) in both nodes:

```
machine01 drbddisk::r0 Filesystem::/dev/drbd0::/mnt::ext4 IPaddr2::192.168.1.72 apache2 mysql
```


**_Network configuration_**
 
(/etc/network/interfaces) master node:

```


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.71
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
dns-nameservers 8.8.8.8 8.8.4.4

auto eth1
iface eth1 inet static
address 172.168.1.71
netmask 255.255.255.0
network 172.168.1.0
broadcast 172.168.1.255
```


(/etc/network/interfaces) slave node:

```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.73
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
dns-nameservers 8.8.8.8 8.8.4.4

auto eth1
iface eth1 inet static
address 172.168.1.73
netmask 255.255.255.0
network 172.168.1.0
broadcast 172.168.1.255
```


(/etc/hosts) in both nodes:

```
127.0.0.1       localhost
172.168.1.71    machine01
172.168.1.73    machine02
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


I'm not sure if there are any mistake in the conf files or heartbeat just doesn't listen services. 

Thanks for your help!!

---

### Post by Crafty Kisses on 2012-10-10
Do you have Pacemaker?

---

### Post by jopieboontje on 2012-10-24
You list two networks, 192.168 wich is a valid C-class range for private use. The other 172.168 is a B-class range for public use while subnetted as a C-class range.

If you wish to use the 172 prefix you should stick to 172.16.x.x to 172.31.x.x

Why not have network 1 : 192.168.88.x/24 and network 2 : 192.168.89.x/24

---

