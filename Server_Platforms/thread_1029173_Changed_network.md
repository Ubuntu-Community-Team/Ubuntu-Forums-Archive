---
title: "Changed network"
date: 2009-01-03
forum: Server Platforms
---

### Post by happyhacker on 2009-01-03
I have taken my server home to try to get it setup over the hols. Thing is my network at home is 192.168.1.x but normally at work is 192.168.0.x. I have managed to get the server added so I can see its shares on one of my machines but if I try to ping from the server to say 192.168.1.66 (my testing laptop assigned by dhcp from my home router) I get no response (even if I try to type it's name (lt7) in. I have tried "nmblookup 192.168.1.66" which fails (but is ok at work).

I am using webmin because the server has no keyboard/screen. It does say in the webmin network config/routing and gateways screen that the gateway is 192.168.0.1 (router at work), whereas the router at home is 192.168.1.254. I am wondering if my server cannot access outwards even though I can access it's shares etc.

The webmin network interface does seem to offer static routes and local routes but I'm wary of messing up the system.

Some help appreciated.

---

### Post by linux_tech on 2009-01-03
What is output of the following-
In terminal type:
```
sudo lshw -C network
ifconfig
cat /etc/resolv.conf
netstat -l -np -p
netstat -rn
cat /etc/network/interfaces

```

---

### Post by volkswagner on 2009-01-03
First create a backup of /etc/network/interfaces file.

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

You can then enable DHCP or set a static route.  If this is temporary DHCP will probably suffice, unless you have multiple computers on the land that power on and off often.

***SAMPLE FILE***
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.128
        network 192.168.1.1
        broadcast 192.168.1.127
        gateway 192.168.1.1
```

Since you have a backup now edit.  You can comment out existing network information or edit it directly.

If you want to enable DHCP change
```

iface eth0 inet static
```

to 

```
iface eth0 inet dhcp
```

Then comment out the rest like..
```

#address 192.168.1.110
 #       netmask 255.255.255.128
  #      network 192.168.1.1
   #     broadcast 192.168.1.127
    #    gateway 192.168.1.
```

Or you can keep it static and assign the address, netmask and gateway according to your router.

Either way when done restart networking.

```
sudo /etc/init.d/networking restart
```

Test your internet connection.

```
host google.com
```

Hope this helps

---

### Post by happyhacker on 2009-01-03
For LinuxTech:

[COLOR="Blue"]> sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 10
       serial: 00:30:1b:ac:25:14
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:ac:25:14  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feac:2514/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4507456 (4.5 MB)  TX bytes:5846432 (5.8 MB)
          Interrupt:18 Base address:0xbc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2904398 (2.9 MB)  TX bytes:2904398 (2.9 MB)

> cat /etc/resolv.conf
nameserver 192.168.0.1
> netstat -l -np -p
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      5240/smbd       
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      4425/perl       
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4356/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3950/sshd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4242/exim4      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      5240/smbd       
tcp6       0      0 :::22                   :::*                    LISTEN      3950/sshd       
udp        0      0 192.168.0.2:137         0.0.0.0:*                           5238/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           5238/nmbd       
udp        0      0 192.168.0.2:138         0.0.0.0:*                           5238/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           5238/nmbd       
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           4425/perl       
udp        0      0 192.168.0.2:123         0.0.0.0:*                           3653/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           3653/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           3653/ntpd       
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           7420/ping       
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           7200/ping       
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           7131/ping       
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           6039/ping       
raw        0      0 0.0.0.0:1               0.0.0.0:*               7           5969/ping       
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     13304    3967/perl           /var/lib/backuppc/log/BackupPC.sock
unix  2      [ ACC ]     STREAM     LISTENING     13680    4279/winbindd       /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     13678    4279/winbindd       /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     13223    3931/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     13776    4357/apache2        /var/run/apache2/cgisock.4356
> netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1[/COLOR]
 
I will study Volkswagner's input but will wait for a respose to the data I've supplied. Will the configuration hold for both network situations or will I have to tweak it each time (probably the Samba workgroup at least)?

---

### Post by happyhacker on 2009-01-05
This is my current interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
#address 192.168.0.2
#netmask 255.255.255.0
#network 192.168.0.0
#broadcast 192.168.0.255
#gateway 192.168.0.1

I'm a little unsure what Volkswagner is suggesting. Is my current one OK?

UPDATE. I tried Volkswagners suggestion and lost all remote (webmin, etc.) to the server. After some fiddling with VI managed to restore the original spec. I think my problem is that the interfaces file points to the other networks IPs. How do I build in my home network of 192.168.1.x as well as having 192.168.0.x?

---

