---
title: "TFTP Server Setup Failure"
date: 2011-06-14
forum: Server Platforms
---

### Post by Nohtanhoj on 2011-06-14
Hey all:
Looking for some help with setting up a dedicated DHCP/TFTP server... I'll be using it for re-flashing the firmwares on consumer internet routers. Basically, right now I have to use a tftpd GUI on windows xp to do each router manually, and I could cut 80% of my time out if I could automate this.

I want my linux server to act as a DHCP server, assign the routers IP addresses, and then use TFTP to transfer over new firmware files.

I'm using standard Ubuntu 11.04 32 bit (not server), since this machine will be used by other people in the future. However, that shouldn't affect my ability to configure the server daemons.

I've installed all of the following packages: xinetd (for setting up the tftp connections), tftpd, tftp, and dhcp3-server. After installing the various tftp packages, I created /etc/xinetd.d/tftp with the following code. 

```
service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}

```

My /tftpboot directory has been created and the permissions modified properly using chown. However, I'm having a massive problem with configuring the DHCP server. My /etc/network/interfaces file looks like this:

```

auto lo
iface lo inet loopback

mapping hotplug
[INDENT]script grep[/INDENT]
[INDENT]map eth1[/INDENT]

auto eth0
iface eth0 inet static
[INDENT]address 192.168.2.10
netmask 255.255.255.0[/INDENT]

auto eth1
iface eth1 inet dhcp
```

My /etc/dhcp/dhcpd.conf file looks like this:
```
ddns-update-style none;

authoritative;

option routers 192.168.2.10;
option subnet-mask 255.255.255.0;
option domain-name-servers 192.168.2.10;
option broadcast-address 192.168.2.255;
option root-path "192.168.2.10:/tftpboot";
default-lease-time 600;
max-lease-time 86400;
server-name "tftp-overlord";

subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.20 192.168.2.200;
next-server tftp-overlord;
filename "lanrescue.img.secure_v06.01.bin";
}
```

I can successfully start both the xinetd and isc-dhcp-server services, but the problem is that when I connect any client to my server machine, no DHCP address is given out. I've tried both routers and working computers - still no address is given out.

I've googled this extensively, and clearly there's something wrong with my dhcpd.conf file, but I have absolutely no idea what.

Any ideas?

---

