---
title: "DHCP3-Server No Answer"
date: 2011-03-23
forum: Server Platforms
---

### Post by AE7 on 2011-03-23
Hey all,

I am having trouble after just installing and configuring DHCP3-Server. I have it running on my local network, with my DHCP server on my router disabled. I am on my Windows machine right now, and I have tried renewing, only the DHCP server does not reply. I have also tried dhcping on the server IP address on the server itself, with it returning "no answer".

A little about my network:

192.168.1.5(static) - Ubuntu 10.10 Server(x64) DHCP Server
192.168.1.1 - Router/Gateway

I have configured eth0, my server's only interface, to serve DHCP requests.

I have configured dhcpd.conf like so:

```
ddns-update-style none;
option domain-name "home";
option domain-name-servers 192.168.1.1;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;

#default-lease-time 600;
#max-lease-time 7200;
authoritative;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.200;
  option broadcast-address 192.168.1.255;
  option subnet-mask 255.255.255.0;
  option netbios-name-servers 192.168.1.1;
  default-lease-time 6000;
  max-lease-time 72000;
}

```

I am clueless as to why this is not working, am I doing something incredibly stupid?

Thanks in advance!

---

### Post by SeijiSensei on 2011-03-23
First place to look is in the logs, /var/log/messages probably.  Use "sudo tail -f /var/log/messages" on the server to track the log while you boot the Windows machine.  What happens?

You did start the server daemon itself with "sudo server dhcp3-server start", yes?  If the daemon doesn't start automatically at boot, run "sudo sysv-rc-conf dhcp3-server on" to fix that.  See this [Guide](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server) for details.

---

