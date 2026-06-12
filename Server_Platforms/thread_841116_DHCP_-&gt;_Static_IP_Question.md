---
title: "DHCP -&gt; Static IP Question"
date: 2008-06-26
forum: Server Platforms
---

### Post by skunkbad on 2008-06-26
I just installed Ubuntu Server 8.04. I understand the need to switch the installer's default DHCP network settings to static, but after viewing many threads I have uncertainty as to what to do with /etc/resolv.conf. /etc/network/interfaces seems pretty straightforward. I've included copies of both here, and my ifconfig, and would appreciate somebody telling me what to do with my /etc/resolv.conf. When I set up the server, I set the hostname as "webserver", in case that matters. The host name "dsl.gtei.net" came from the router, but according to the router manual, this could be deleted. Please review:

```

#This is my /etc/network/interfaces :

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp




#This is my /etc/resolv.conf

search dsl.gtei.net
nameserver 4.2.2.1
nameserver 4.2.2.2
nameserver 4.2.2.3



#This is my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:03:47:e9:88:68  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fee9:8868/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:715951 (699.1 KB)  TX bytes:547674 (534.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30912 (30.1 KB)  TX bytes:30912 (30.1 KB)

```

So again, I'm confused about what to do with /etc/resolv.conf.

Thanks in advance for your help

---

### Post by 505 on 2008-06-26
Just edit /etc/network/interface to look like:
```

auto eth0
iface eth0 inet static
	address 192.168.1.105 # your static address
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.1.255
	gateway 192.168.1.1 # IP address of your router
	dns-nameservers 4.2.2.1 # optional
	dns-search dsl.gtei.net # optional

```

As for resolv.conf, the only thing I have in there is "nameserver 192.168.1.1" (same IP as gateway above) and all works well.

---

### Post by skunkbad on 2008-06-26
I assume I also need to set up a static IP for the server on my router, but I'm not sure my router is capable of this. I have set up port forwarding for SSH and HTTP traffic, and the manual says that to do so DHCP must be disabled, but the port forwarding IS working, and I haven't disabled DHCP. I recycled the router to see if it would keep 192.168.1.105 static, but it does not.

My router is old; its a linksys [BEFSR41]("ftp://ftp.linksys.com/pub/manuals/befsr41.pdf"). <<link to pdf manual

If anyone has this router, or can tell me by looking at the manual how to make only the server have a static IP, I'd really appreciate it. There are 6 other computers on the network, and a network printer, so I don't want to mess it up!

---

### Post by cariboo on 2008-06-26
You don't have to do anything in your router setup, just use an ip address outside the address used by dhcp eg: 198.162.1.200

Jim

---

### Post by skunkbad on 2008-06-26
Thanks!

It's done, and it is working!

---

