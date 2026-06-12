---
title: "DNS problem - no nameservers"
date: 2021-08-02
forum: Ubuntu/Debian BASED
---

### Post by bomberb17 on 2021-08-02
Hello, I have a problem with my DNS nameservers in my 20.04:

```
$ dig www.google.com

; <<>> DiG 9.16.1-Ubuntu <<>> www.google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
#source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet static
    address 192.168.1.12
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1 8.8.8.8


$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients directly to
# all known uplink DNS servers. This file lists all configured search domains.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

# No DNS servers known.

$ systemd-resolve --status
Global
       LLMNR setting: no                  
MulticastDNS setting: no                  
  DNSOverTLS setting: no                  
      DNSSEC setting: no                  
    DNSSEC supported: no                  
          DNSSEC NTA: 10.in-addr.arpa     
                      16.172.in-addr.arpa 
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa 
                      18.172.in-addr.arpa 
                      19.172.in-addr.arpa 
                      20.172.in-addr.arpa 
                      21.172.in-addr.arpa 
                      22.172.in-addr.arpa 
                      23.172.in-addr.arpa 
                      24.172.in-addr.arpa 
                      25.172.in-addr.arpa 
                      26.172.in-addr.arpa 
                      27.172.in-addr.arpa 
                      28.172.in-addr.arpa 
                      29.172.in-addr.arpa 
                      30.172.in-addr.arpa 
                      31.172.in-addr.arpa 
                      corp                
                      d.f.ip6.arpa        
                      home                
                      internal            
                      intranet            
                      lan                 
                      local               
                      private             
                      test                

Link 4 (eth0)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no  

Link 3 (sit0)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no  

Link 2 (usb0)
      Current Scopes: none
DefaultRoute setting: no  
       LLMNR setting: yes 
MulticastDNS setting: no  
  DNSOverTLS setting: no  
      DNSSEC setting: no  
    DNSSEC supported: no  

```


I have tried this approach with resolvconf but DNS won't persist after reboot
[https://www.tecmint.com/set-permanent-dns-nameservers-in-ubuntu-debian/](https://www.tecmint.com/set-permanent-dns-nameservers-in-ubuntu-debian/)

Any suggestions?

---

### Post by chili555 on 2021-08-02
Is this a server or a desktop install? In either case, I recommend that you revert your changes to /etc/network/interfaces. They are ineffective, as you've seen.

Please also run and post:
```
ip addr show
```

---

### Post by bomberb17 on 2021-08-02
It was originally a desktop install, but removed all desktop-related packages to become a server.
The problem started when I set a static address in /etc/network/interfaces. What do you mean revert? I need the static address. Just take the nameservers out?
Here's the output

```
$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: usb0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether be:03:ac:6e:71:1c brd ff:ff:ff:ff:ff:ff
3: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether ba:5d:6d:41:68:6f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.12/24 brd 192.168.1.255 scope global eth0
       valid_lft forever preferred_lft forever
```

---

### Post by chili555 on 2021-08-02
In Ubuntu 20.04, the method is now netplan: [https://askubuntu.com/questions/976464/why-is-the-network-configuration-i-set-in-etc-network-interfaces-ignored-on-ubu/976497#976497](https://askubuntu.com/questions/976464/why-is-the-network-configuration-i-set-in-etc-network-interfaces-ignored-on-ubu/976497#976497)

As yours is an ethernet interface, please see the example here: 

```
cat /usr/share/doc/netplan/examples/static.yaml
```

> What do you mean revert? It means remove all the lines you added so as to return it to its default state.

---

### Post by bomberb17 on 2021-08-02
But:
```

$ ls /etc/netplan
ls: cannot access '/etc/netplan': No such file or directory
$ sudo netplan
sudo: netplan: command not found
```


I don't seem to have netplan installed.. (my installation is a custom-built [image]("https://github.com/hexdump0815/imagebuilder/releases/tag/210508-01") for ODROID U3 SBC)

---

### Post by chili555 on 2021-08-02
> (my installation is a custom-built image for ODROID U3 SBC)As far as I can tell, briefly reviewing the link you gave, as well as browsing the Issues pages, this has many changes from default Ubuntu. I don't begin to understand the few that I reviewed.

Here is an example:

> I'm using the odroid_u3-armv7l-ubuntu-focal-dev image from the current release (200823-01) and I'm wondering why ipv6 is disabled in /boot/extlinux/extlinux.conf (ipv6.disable=0).

Is it ok to enable it in a ipv6 environment or do I have to face problems?conf files are in /etc/modprobe.d in Ubuntu, not, of all places, /boot. I have nothing on my system at all named extlinux.

I am sorry that I have no further suggestions.

---

### Post by QIII on 2021-08-02
Moved to Ubuntu/Debian BASED.

As a custom build, yours is not an official Ubuntu flavor.

---

