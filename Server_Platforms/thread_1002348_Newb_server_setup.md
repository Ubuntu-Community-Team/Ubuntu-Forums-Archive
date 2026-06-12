---
title: "Newb server setup"
date: 2008-12-04
forum: Server Platforms
---

### Post by trs21219 on 2008-12-04
ok here goes,

i have an old computer (Celeron Processor, 256MB RAM). i wanted to make a server at home for just playing around with stuff that i dont want to put on my hosted box. (SSH Practice, configurations, load balancing etc). the only problem is that i cant get it to connect to the internet. 

its hooked up via Ethernet directly into my router and it shows up in the connected devices on the network page of my router. i try to ping google and i get "connect: Network is unreachable" i try to download updates and i get "Could not resolve 'security.ubuntu.com'"

this is the first time ive used linux (other than some minor ssh configuring my webserver for work). i dont want to install the desktop version because i want to learn how to do it via command line for the future.

any help would be much appreciated :)

---

### Post by hictio on 2008-12-04
How are all the other computers on your LAN getting their IP address? Do you set it up manually, or the computers get their IP address automatically?

---

### Post by trs21219 on 2008-12-04
the others are automatic but i set a static ip for the one im trying to get.

i set it to  192.168.1.4 as static on my router

---

### Post by trs21219 on 2008-12-04
here is a couple shots of my router...

BTW the name for it is SERVER-01

---

### Post by hictio on 2008-12-04
> **trs21219 said:**
> the others are automatic but i set a static ip for the one im trying to get.

i set it to  192.168.1.4 as static on my router

Ok, on the router, but what about on the Ubuntu Server itself?
What does return if you type:

```

ifconfig (ENTER)

```

On the Server's console?

---

### Post by trs21219 on 2008-12-04
if i do the ifconfig i get

> 
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
intet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collions : 0 txqueuelen:0
RX bytes: 0 (0.0 B) TX bytes: 0 (0.0B)


---

### Post by trs21219 on 2008-12-04
just tried to test it by using the router to ping it and got 100% loss

---

### Post by hictio on 2008-12-04
Cool, you don't have an IP address assigned to your NIC.
Post the outout of this command:

```

lshw -C Network (ENTER)

```

To see which NIC do you have, if any.
Yes, you won't be able to ping your box from the router, nor your router from the Ubuntu box because the Ubuntu Server has no IP address, it is for every means, offline.

---

### Post by trs21219 on 2008-12-04
k here is the output
> 
WARNING: you should run this program as a super user
*-network DISABLED
description: Ethernet Interface
product: RTL...
vendor: realtek
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth1
version : 10
width: 32bits
clock: 33MHz
bapabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes
driver = 8139too driver version = 0.9.28 latency=64 max letency = 64 mingnt = 32 module = 8139too multicast=yes


---

### Post by hictio on 2008-12-04
Cool, do this.

```

sudo ifconfig eth1 192.168.1.4 netmask 255.255.255.0 up (ENTER)
sudo route add default gw 192.168.1.1 (ENTER)

```

**Important!** I'm *guessing* the netmask & the default gateway values!! Taylor those to your LAN! :D

After that, ping your router, and from the router ping your Ubuntu box to test it.
If works, ping 64.233.161.83 (which is one of the gmail.com IPs), if it works, to are reaching the internet. You'll need to see if you have a couple of DNSs on /etc/resolv.conf, tyr pinging gmail.com to see if it works.

---

### Post by trs21219 on 2008-12-04
ah yes! that worked perfectly. thank you so much... ):P

---

### Post by hictio on 2008-12-05
Be aware that this won't survive a reboot, you'll have to setup the values thru the file: '/etc/network/interfaces' and also, don't forget to add a couple of DNS servers' IPs to /etc/resolv.conf; you'll have to do that as the user root, thru sudo, they are simple text files.

/etc/network/interfaces:
```

auto lo eth1
iface lo inet loopback
iface eth1 inet static
address xxx.xxx.xxx.xxx (your ip)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx (gateway ip)

```

/etc/resolv.conf:
```

nameserver xxx.xxx.xxx.xxx (dns server ip)
nameserver xxx.xxx.xxx.xxx (dns 2 server ip)

```

Setup this, and reboot to test that everyhing comes up A Ok.

---

### Post by trs21219 on 2008-12-05
hmm didnt work the first time let me try agian... when it loads it says it couldnt load the interfaces one so im assuming i did that one wrong.. the other one looks to be ok though i set it to opendns

---

### Post by trs21219 on 2008-12-05
sweet got it working :) thank you so much.. im beginning to like this linux stuff.

---

### Post by hictio on 2008-12-05
Cool, now make it a server and serve something :D

---

