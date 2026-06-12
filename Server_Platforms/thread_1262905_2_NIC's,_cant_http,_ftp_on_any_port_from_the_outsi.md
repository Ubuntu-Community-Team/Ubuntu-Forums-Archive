---
title: "2 NIC's, cant http, ftp on any port from the outside!"
date: 2009-09-10
forum: Server Platforms
---

### Post by joeinbend on 2009-09-10
I've searched profusely through the forums before posting, so here it goes: I have a Ubuntu 9.04 server with 2 NIC's, one is attached to my DMZ the other to my internal LAN. I do this because I run VMware Server on it, and I have my web/ftp server VM's attached to the DMZ interface and my internal VM's attached to the LAN, works like a charm.

I have my routes in place to forward my port 80 traffic to my VM web server on the DMZ side, and that works just fine, so does FTP, and any other ports I forward, including a couple internal ports for remote access to my LAN. However, I cannot successfully forward anything to the actual Ubuntu server, I'm only able to connect to servers sitting on top of it that are virtual machines. I can connect to those services on the Ubuntu server when I am on my internal LAN, just not from the Internet. Sounds like a firewall/routing issue, but it is not, as I can forward those same ports to another system on my internal LAN or my DMZ, virtual or physical, and those connections go through just fine. It's not just apache2 on my Ubuntu server, because I cannot get FTP to connect either. I thought maybe it was apparmor so I stopped that service, to no avail. Maybe I am missing something in my network config on the Ubuntu server, due to the 2 NIC's? below is my /etc/network/interfaces   let me know if you see anything or can suggest another reason I am having trouble. Thanks!!


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1

# Secondary DMZ network interface
auto eth2

# uncomment the next line to enable DHCP
# iface eth1 inet dhcp

# lines below are static IP
iface eth1 inet static
        address 192.168.4.25
        netmask 255.255.255.0
        network 192.168.4.0
        broadcast 192.168.4.255
        gateway 192.168.4.1

# lines below are static IP
iface eth2 inet static
        address 10.1.50.25
        netmask 255.255.255.0
       network 10.1.50.0
        broadcast 10.1.50.255
        gateway 10.1.50.1



Also just in case it's of use, here's my "lshw -C network"

*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:92:f2:d2:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.4.25 latency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth2
       version: 24
       serial: 00:10:4b:6a:eb:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=10.1.50.25 latency=64      maxlatency=10 mingnt=10 module=3c59x multicast=yes

---

### Post by recentcoin on 2009-09-10
The whole idea behind VMWare is that you don't really deal with the physical box.  The physical box is acting like a router because of the way VMWare handles networking.  I'm not sure what you can do to get around that short of using the VMWare console.

---

### Post by joeinbend on 2009-09-10
I see what you're saying, and I would prefer for it to be the way you are describing, but my VMware server is basically a multi-function server, hosting services other than just VMware. The thing is, I know it will work, because from another PC in my LAN, I can access those services!

---

### Post by recentcoin on 2009-09-10
If you can get to them locally, then it's not the box. Its likely a firewall or router issue.

---

### Post by joeinbend on 2009-09-10
That was my first thought too, however, I route the exact same ports to a different IP, weather internal or external, and they work fine. the Ubuntu server is the only one rejecting the requests.

For troubleshooting, what would be helpful is if someone can point me in the right direction for log files on Ubuntu that would show me if incoming connections are being rejected/dropped. I verified my firewall is in fact routing it and not dropping, so it's getting killed elsewhere internally.

---

### Post by joeinbend on 2009-09-10
Well this didnt exactly answer my question, but I was able to work-around the issue, and probably to a result that is more best-practices-oriented in terms of security: I reconfigured the services on the Ubuntu server that I need to see, to default to the DMZ subnet on eth2, and routed to that IP, and everything is working. I guess that's how I'll leave it!

---

