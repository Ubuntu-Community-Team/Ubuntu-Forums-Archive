---
title: "2 sites out of 3 offline on virtual apache2"
date: 2013-11-08
forum: Server Platforms
---

### Post by Mariane on 2013-11-08
I have 3 site on the same apache2 (up-to-data Ubuntu) server. They each have their own IP. 

Each site has its own file in "sites-enabled". 

Apache2 seems to be running fine: /var/log/apache2/error.log only says:
[Fri Nov 08 12:30:12 2013] [notice] Apache/2.2.22 (Ubuntu) PHP/5.4.6-1ubuntu1.4 configured -- resuming normal operations

The DNS files seem OK: I did not modify them and no program modified them either. They used to function before. I'll post a copy if someone asks me to do it. 

When I point a browser to the second and third site (to their domain names or to their IP adresses), it just hangs until timeout. 
Same with a ping:
ping 92.243.20.169: OK
ping 92.243.21.141: 100% packet loss
ping 92.243.4.114: 100% packet loss

ip addr
```

    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        inet6 ::1/128 scope host 
           valid_lft forever preferred_lft forever
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:93:68:c0 brd ff:ff:ff:ff:ff:ff
        inet 92.243.20.169/22 brd 92.243.23.255 scope global eth0
        inet6 2001:4b98:dc0:45:216:3eff:fe93:68c0/64 scope global dynamic 
           valid_lft 2591871sec preferred_lft 604671sec
        inet6 fe80::216:3eff:fe93:68c0/64 scope link 
           valid_lft forever preferred_lft forever
    3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:84:91:0a brd ff:ff:ff:ff:ff:ff
        inet 92.243.21.141/22 brd 92.243.23.255 scope global eth1
        inet6 2001:4b98:dc0:45:216:3eff:fe84:910a/64 scope global dynamic 
           valid_lft 2591871sec preferred_lft 604671sec
        inet6 fe80::216:3eff:fe84:910a/64 scope link 
           valid_lft forever preferred_lft forever
    4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:1f:2d:85 brd ff:ff:ff:ff:ff:ff
        inet 92.243.4.114/21 brd 92.243.7.255 scope global eth2
        inet6 2001:4b98:dc0:41:216:3eff:fe1f:2d85/64 scope global dynamic 
           valid_lft 2591952sec preferred_lft 604752sec
        inet6 fe80::216:3eff:fe1f:2d85/64 scope link 
           valid_lft forever preferred_lft forever

```

ifconfig
```

    eth0      Link encap:Ethernet  HWaddr 00:16:3e:93:68:c0  
              inet addr:92.243.20.169  Bcast:92.243.23.255  Mask:255.255.252.0
              inet6 addr: 2001:4b98:dc0:45:216:3eff:fe93:68c0/64 Scope:Global
              inet6 addr: fe80::216:3eff:fe93:68c0/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:9550641 errors:0 dropped:3 overruns:0 frame:0
              TX packets:3749560 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:953636357 (953.6 MB)  TX bytes:6983319124 (6.9 GB)
              Interrupt:27 
    
    eth1      Link encap:Ethernet  HWaddr 00:16:3e:84:91:0a  
              inet addr:92.243.21.141  Bcast:92.243.23.255  Mask:255.255.252.0
              inet6 addr: 2001:4b98:dc0:45:216:3eff:fe84:910a/64 Scope:Global
              inet6 addr: fe80::216:3eff:fe84:910a/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:5797827 errors:0 dropped:3 overruns:0 frame:0
              TX packets:34854 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:607191525 (607.1 MB)  TX bytes:1464788 (1.4 MB)
              Interrupt:28 
    
    eth2      Link encap:Ethernet  HWaddr 00:16:3e:1f:2d:85  
              inet addr:92.243.4.114  Bcast:92.243.7.255  Mask:255.255.248.0
              inet6 addr: 2001:4b98:dc0:41:216:3eff:fe1f:2d85/64 Scope:Global
              inet6 addr: fe80::216:3eff:fe1f:2d85/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:9231950 errors:0 dropped:2 overruns:0 frame:0
              TX packets:29473 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:914989353 (914.9 MB)  TX bytes:1349244 (1.3 MB)
              Interrupt:29 
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:11570 errors:0 dropped:0 overruns:0 frame:0
              TX packets:11570 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:1135320 (1.1 MB)  TX bytes:1135320 (1.1 MB)

```

netstat -a
```

    Active Internet connections (servers and established)
    Proto Recv-Q Send-Q Local Address           Foreign Address         State      
    tcp        0      0 *:mysql                 *:*                     LISTEN     
    tcp        0      0 *:gandi-agent           *:*                     LISTEN     
    tcp        0      0 *:ftp                   *:*                     LISTEN     
    tcp        0      0 *:ssh                   *:*                     LISTEN     
    tcp        0    368 Charlotte:ssh           reverse-27.fdn.fr:37999 ESTABLISHED
    tcp6       0      0 [::]:http               [::]:*                  LISTEN     
    tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61519 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61352 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61442 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61209 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61550 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61421 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61579 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61606 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61386 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61469 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61275 TIME_WAIT  
    tcp6       0      0 Charlotte:http          ks4000493.ip-198-:61247 TIME_WAIT  
    Active UNIX domain sockets (servers and established)
    Proto RefCnt Flags       Type       State         I-Node   Path
    unix  3      [ ]         DGRAM                    2346     /dev/log
    unix  2      [ ACC ]     STREAM     LISTENING     229      @/com/ubuntu/upstart
    unix  2      [ ACC ]     STREAM     LISTENING     3598978  /var/run/mysqld/mysqld.sock
    unix  2      [ ACC ]     SEQPACKET  LISTENING     430      /run/udev/control
    unix  3      [ ]         STREAM     CONNECTED     3597550  
    unix  3      [ ]         STREAM     CONNECTED     3597549  
    unix  2      [ ]         DGRAM                    3597541  
    unix  3      [ ]         STREAM     CONNECTED     709      @/com/ubuntu/upstart
    unix  3      [ ]         STREAM     CONNECTED     706      
    unix  3      [ ]         DGRAM                    438      
    unix  3      [ ]         DGRAM                    437      
    unix  3      [ ]         STREAM     CONNECTED     393      @/com/ubuntu/upstart
    unix  3      [ ]         STREAM     CONNECTED     390      

```

/etc/apache2/sites-enabled/001-www.lapf.eu 
```

<VirtualHost 92.243.20.169:80>
        ServerAdmin admin@92.243.20.169

        DocumentRoot /srv/d_Charlotte/www/www.lapf.eu/htdocs/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

/etc/apache2/sites-enabled/002-www.felkin.info
```
 
<VirtualHost 92.243.21.141:80>
        ServerAdmin admin@92.243.21.141

        DocumentRoot /srv/d_Charlotte/www/www.felkin.info/htdocs
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

/etc/apache2/sites-enabled/003-www.seidhr.fr 
```
 
<VirtualHost 92.243.4.114:80>
        ServerAdmin admin@92.243.4.114

        DocumentRoot /srv/d_Charlotte/www/www.seidhr.fr/htdocs
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```


I have no idea what to do next... Please help.

---

### Post by SeijiSensei on 2013-11-08
Looks like a routing problem to me since you cannot ping the interfaces.  Does the client's default gateway point to a router with static routes for each of the three subnets?

---

### Post by Mariane on 2013-11-12
I have no idea... How can I check this, please?

---

### Post by SeijiSensei on 2013-11-13
If you have control over the router, what is the output of "route -n" or the equivalent command to display the router's routing table?

If you don't have control over the router, you need to speak with whoever does.

---

### Post by Mariane on 2013-11-24
route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         92.243.23.254   0.0.0.0         UG    0      0        0 eth0
92.243.0.0      0.0.0.0         255.255.248.0   U     0      0        0 eth2
92.243.20.0     0.0.0.0         255.255.252.0   U     0      0        0 eth0
92.243.20.0     0.0.0.0         255.255.252.0   U     0      0        0 eth1

```

Sorry I didn't answer before, I thought I had no control over the router, but apparently this command still outputs something...

---

### Post by nerdtron on 2013-11-25
Sorry for not helping much, can't you just host all 3 domain names in a single IP and use named virtual hosts? I think that will be easier to manage.

---

### Post by Mariane on 2013-11-25
Two of these sites are related to groups of people, and some of them would object. They would say that having a common IP with the other site links unrelated and independent groups too much.

---

### Post by Mariane on 2013-11-29
Solution: 

The virtual cable to my interfaces was "unplugged". It could be seen with the commands "ethtool eth1" and "ethtool eth2". If the answer does not say "Link detected: yes", something is wrong. 

I had to edit a file called "/etc/sysctl.conf" 

So I typed 
```

sudo nano /etc/sysctl.conf

```

At the end of the file, I added several lines. I'm not sure at all which one did the trick, maybe not all of them are actually useful. This example is for 3 interfaces (eth0, eth1 and eth1) and should be adapted if the number of interfaces is different:
```

net.ipv4.conf.all.arp_announce = 2
net.ipv4.conf.default.arp_announce = 0
net.ipv4.conf.lo.arp_announce = 0

net.ipv4.conf.eth1.arp_announce = 0
net.ipv4.conf.eth2.arp_announce = 0

net.ipv4.conf.all.arp_filter = 0
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.default.arp_filter = 0

net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.eth0.arp_filter = 0
net.ipv4.conf.eth1.rp_filter = 0
net.ipv4.conf.eth1.arp_filter = 0
net.ipv4.conf.eth2.rp_filter = 0
net.ipv4.conf.eth2.arp_filter = 0 

net.ipv4.conf.eth0.arp_announce = 2
net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.eth1.arp_announce = 2
net.ipv4.conf.eth1.rp_filter = 0
net.ipv4.conf.eth2.arp_announce = 2
net.ipv4.conf.eth2.rp_filter = 0

```

I saved to sysctl.conf and closed nano. 

Then I went to my control interface (provided by my ISP, Gandi). From there I stopped the server. Once it was fully stopped, I disconnected all 3 interfaces. Then I reconnected them. Once they were fully reconnected, I relaunched the server, still from the interface. 

My 3 sites are back online :)

---

