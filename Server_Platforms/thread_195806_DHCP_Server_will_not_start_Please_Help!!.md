---
title: "DHCP Server will not start Please Help!!"
date: 2006-06-13
forum: Server Platforms
---

### Post by BeagleBen on 2006-06-13
Hello

I am trying to set up my server as a dhcp server, I have 2 network cards installed
eth0 is connected to my router with an isp static ip of 88.96.xx.17

I want eth1 to serve as a dhcp server /gateway to my clients wth a  range of 192.168.0.1 for example, I am really struggling with this

I have carried out  full reinstall and installed GDHCPD, that says ISC DHCPD is not installed or not in your path, also when i try and stop and restart DHCP is just says "fail"

I am a linux newbie, I am used to Windows server 2003 which does all this for me, 

Thank You
Beagle:-x :-x

---

### Post by rbalfour on 2006-06-13
$ apt-get install dhcp-server

gdhcpd is just a front end to the DHCP server package.

---

### Post by BeagleBen on 2006-06-13
Thanks for the reply, 

I have tried this and it says that it is already installed no files to update
Thanks

Beagle

---

### Post by rbalfour on 2006-06-13
oops...

$apt-get install dhcp3-server
is the right command

What I did.

$ apt-get install dhcp3-server
$ apt-get install gdhcpd
$ gdhcpd

set up the leases, hit "activte" every thing was good.

If you still can't get it to work. Remove the above packages and re-install.

---

### Post by elias@cpaefs.com on 2006-06-13
your dhcpd.conf

authoritative;
ddns-update-style interim;
subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.100 192.168.0.250;
    default-lease-time 259200;
    max-lease-time 518400;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
    option domain-name-servers 192.168.0.1;


For first timers I recommend dnsmaq.

uninstall dhcp packedge the install dnsmasq

change the dnsmasq.conf to fit your needs.

interface and range fo starters.

dhcp-range=192.168.0.100,192.168.0.250,72h
interface=eth1

then restart dnsmasq

remmber echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by BeagleBen on 2006-06-13
Thank You

I will give it a try

Beagle

---

### Post by Thiesen on 2006-06-15
[QUOTE=BeagleBen]Thank You

I will give it a try

Beagle[/QUOTE]

Not without doing this in your favourite console:

```
sudo gdhcpd
```

You have to run gdhcpd with root privileges...

After that you can edit your dhcp server... :-)

---

