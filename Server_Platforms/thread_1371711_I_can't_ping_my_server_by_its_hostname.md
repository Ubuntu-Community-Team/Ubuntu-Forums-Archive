---
title: "I can't ping my server by its hostname"
date: 2010-01-03
forum: Server Platforms
---

### Post by buntolith on 2010-01-03
Hi,

I have installed a ubuntu 9.10 server to use mostly as a fileserver. When I installed the server I set it up as DHCP and later on I have changed the /etc/network/interfaces file, the /etc/hosts file and the /etc/hostname file. I have the ip 192.168.1.100 set on the server and I can ping and SSH this address. But I can not ping my server by it's hostname enighet. I am setting up a NFS server and I would like to use my servers hostname when I do this. Why can I not ping my server by it's hostname? These are the 3 files I have changed...

```
johan@enighet:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

```
johan@enighet:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       enighet
192.168.1.100   enighet

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

```
johan@enighet:~$ cat /etc/hostname
enighet
```

---

### Post by Iowan on 2010-01-03
The quick/dirty way is to include the hostname - IP address pair in the /etc/hosts fle of the client machines. The alternative is to install a DNS server on the network. IF your DHCP server (router?) can act as DNS server, you might consider leaving the server with DHCP address, and configuring the DHCP server to issue a static lease based on MAC address.

---

### Post by buntolith on 2010-01-03
Aha! I tried the quick and dirty way and it worked fine of course. Maybe I will install a DNS server later on. Thanks a lot for your help!

---

