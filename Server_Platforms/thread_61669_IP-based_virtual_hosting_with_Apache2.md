---
title: "IP-based virtual hosting with Apache2"
date: 2005-09-01
forum: Server Platforms
---

### Post by kozimodo on 2005-09-01
Hi,

I'm having some problems with my Apache setup.  I have set it up to do IP-based virtual hosting but it doesn't seem to be working correctly.  I went with IP-based rather than name based because I eventually want to enable SSL for some of my pages.  The problem is that when I type one of the URLs, I am automatically directed to apache-default.  If, on the other hand, I use one of the virtual IP addresses, it goes to the correct page.  I'm baffled and any suggestions would be much appreciated.  Thanks!

My setup has three virtual hosts set up -- apache-default and two virtual hosts that have been enabled and reside in the sites-available directory:
```

<VirtualHost 192.168.1.40>
ServerName www.xxx.xxx
DocumentRoot /var/www/xxx/
CustomLog logs/xxx-access_log combined
ErrorLog logs/xxx-error_log
</VirtualHost>

```
and
```

<VirtualHost 192.168.1.41>
ServerName xxx.xxx.xxx
DocumentRoot /var/www/xxx
CustomLog /var/www/logs/xxx-access_log combined
ErrorLog /var/www/logs/xxx-error_log
</VirtualHost>

```
I set up IP aliases in the /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.33
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth0:0
iface eth0:0 inet static
    address 192.168.1.40
    netmask 255.255.255.0
    broadcast 192.168.1.255

auto eth0:1
iface eth0:1 inet static
    address 192.168.1.41
    netmask 255.255.255.0
    broadcast 192.168.1.255

```
and the output from ifconfig is
```

eth0      Link encap:Ethernet  HWaddr 00:0A:27:E4:09:B2
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:27ff:fee4:9b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1033042 (1008.8 KiB)  TX bytes:1118489 (1.0 MiB)
          Interrupt:41 Base address:0x400

eth0:0    Link encap:Ethernet  HWaddr 00:0A:27:E4:09:B2
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0x400

eth0:1    Link encap:Ethernet  HWaddr 00:0A:27:E4:09:B2
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0x400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:27344 (26.7 KiB)  TX bytes:27344 (26.7 KiB)

```

---

### Post by lao_V on 2005-09-08
What is in your ports.conf file? You need to be listening to correct ips/ports in there For more info have you looked [here]("http://httpd.apache.org/docs/2.0/vhosts/ip-based.html")?

---

### Post by relix42 on 2005-09-08
[QUOTE=kozimodo]The problem is that when I type one of the URLs, I am automatically directed to apache-default.  If, on the other hand, I use one of the virtual IP addresses, it goes to the correct page.  I'm baffled and any suggestions would be much appreciated.[/QUOTE]

Have you verified your DNS/hosts entries?  Are they all pointing to the 1.33 address by chance?

---

### Post by LordHunter317 on 2005-09-08
If it works when you access it by IP, but not by DNS, then your DNS is wrong.  Yuo need to correct your entries in your DNS.

---

### Post by kozimodo on 2005-09-10
[QUOTE=LordHunter317]If it works when you access it by IP, but not by DNS, then your DNS is wrong.  You need to correct your entries in your DNS.[/QUOTE]
I have both domain names in my hosts file -- I can ping them.

---

