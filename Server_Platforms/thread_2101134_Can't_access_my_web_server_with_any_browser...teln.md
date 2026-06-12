---
title: "Can't access my web server with any browser...telnet and ping works"
date: 2013-01-03
forum: Server Platforms
---

### Post by slad888 on 2013-01-03
I'm turning an old pc into a new lamp web server for my own personal practice at home.  Just installed ubuntu 12.0.4.1 LTS

I set the servers ip to a static ip : 10.0.xx.xxx

I can access it with telnet 10.0.xx.xx but not  telnet 10.0.xx.xxx http
works with filezilla just fine too.

can't access it with any web browser

[COLOR="Red"]// in network on my mac
ipv4: 10.0.xx.xxx
submask: 255.255.255.0
router: 10.0.xx.xx

//when i log into my router using airport utility
ipv4: 24.23.xxx.xxx
submask: 255.255.254.0
router: 24.23.130.xxx[/COLOR]
Something fishy here not sure how to fix it

ping 10.0.1.xxx
PING 10.0.1.xxx (10.0.1.xxx): 56 data bytes
64 bytes from 10.0.1.xxx: icmp_seq=0 ttl=64 time=3.331 ms
64 bytes from 10.0.1.xxx: icmp_seq=1 ttl=64 time=3.273 ms
64 bytes from 10.0.1.xxx: icmp_seq=2 ttl=64 time=10.829 ms
64 bytes from 10.0.1.xxx: icmp_seq=3 ttl=64 time=1.368 ms
^Z
[1]+  Stopped                 ping 10.0.1.xxx

ifconfig

lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	options=3<RXCSUM,TXCSUM>
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
	inet6 ::1 prefixlen 128 

en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 60:c5:47:0a:76:60 
	inet6 fe80::62c5:47ff:fe0a:7660%en0 prefixlen 64 scopeid 0x4 
	inet 10.0.1.xxx netmask 0xffffff00 broadcast 10.0.1.255



FROM SERVER:
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:05:5d:34:42:bb  
          inet addr:10.0.1.xxx  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe34:42bb/64 Scope:Link

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host

/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 10.0.xxx.xxx
netmask 255.255.255.0
gateway 10.0.1.xxx


PLEASE HELP!!

---

### Post by chadk5utc on 2013-01-03
first thing do if thats your real IP in RED on router side remove(from here) and replace it with xxx.xxx Etc save yourself headaches as its public the others are private and wont matter.

---

### Post by slad888 on 2013-01-03
k

---

### Post by chadk5utc on 2013-01-03
> **slad888 said:**
> airport utility say ip is 24.xx.xx.xx
LAN ip is 10.0.1.1
wireless is 10.0.1.6 in your post change your real ip like so to avoid issues we generally dont need it. I just lookin at the numbers to see if I see anything obvious.

---

### Post by chadk5utc on 2013-01-03
I think your 10.xx addressing is ok but the PC's need to point to the gateway 24.23.130.xxx on the router as this is the way In/Out of your network.
in terminal type
> 
cat /etc/resolv.conf                     (corrected typo)

and post the results

please excuse any delay as I am sick and will be working in a few

---

### Post by cariboo on 2013-01-03
The 10.0.0.0 netblock is non-routable, so you don't have to hide that.

One thing I'd check is if port 80 is open on the server, there are several port scanning tools, but I prefer to use nmap, which is available for all plaforms.

Once you've determined that port 80 is open, try to access the server using it's ip address eg:

```
http://10.0.xxx.xxx
```

you should see the ***It Works!*** message. You won't be able to access the server from inside your internal network, using your external ip address.

---

### Post by slad888 on 2013-01-03
does that go for the submask as well

---

### Post by chadk5utc on 2013-01-03
> **slad888 said:**
> does that go for the submask as well

the subnet needs to be the same on all connected pc's if they are to talk

---

### Post by slad888 on 2013-01-03
netstat -anltp | grep "LISTEN"

tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      690/perl        
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      624/inetd       
tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN      624/inetd       

this was my output.... there isn't even a port 80
I swear i installed LAMP shouldn't it be there...

---

### Post by chadk5utc on 2013-01-03
yes your correct it should be listed Im trying to remember 
> sudo service apache2 status
if not running then
sudo service apache2 start

sorry earlier I misunderstood your original post.

---

### Post by slad888 on 2013-01-03
No clue why but apparently when I installed it only installed basic and not LAMP.. what a headache. installing now. i'll post again if i have a similar issue.

Thanks so much for the help everyone!!!

---

