---
title: "how to: configure DHCP"
date: 2007-11-21
forum: Server Platforms
---

### Post by johnswb on 2007-11-21
Hello all,

I've installed Ubuntu Server 7.10 and now trying to configure my DHCP.  I have done the following steps listed [here]("http://doxfer.com/Webmin/DHCPServer") after installing Webmin.  When I click on start I get the following error "Failed to start dhcpd :"  I've always been a Windows guy and now I'm really moving to linux.  I'm just having a hard time with DHCP which I think is a simple think to do, if I knew what I was doing.

please help

---

### Post by koenn on 2007-11-21
if a service s.a. dhcpd fails to start, its usually because of an eroor, typo, inconsistency, ... in its configuration file. 

I don't use webmin so I don't know what it does to dhcpd conf, but if you 
- describe what you want dhcpd to do
- post it's config file (probably somewhere near /etc/dhcpd3/dhcpd3.conf) 
we can have a look.

---

### Post by johnswb on 2007-11-21
I have a Windows DHCP server currently and would like to switch to the Ubuntu server instead. I would like to go all Linux and get away from Windows.

This is what I have in my dhcpd.conf file.  Thank you for replying.

root@userver:/etc/dhcp3# cat dhcpd.conf
option domain-name-servers 10.80.20.4;
option domain-name "example.com";
option subnet-mask 255.255.255.128;
option broadcast-address 10.80.20.127;
option routers 10.80.20.1;
ddns-update-style none;
# example.com
subnet 10.80.20.0 netmask 255.255.255.128 {
        range 10.80.20.10 10.80.20.50;

---

### Post by koenn on 2007-11-21
there's a closing } missing in your subnet declaration. 
you probably want something like
```
subnet 10.80.20.0 netmask 255.255.255.128 {
      range 10.80.20.10 10.80.20.50;
};

```
I'm no sure the final ; is necessary but probably it wont hurt either.

---

### Post by johnswb on 2007-11-21
Thanks for replying.  Starting the dhcp server is still failing.  May be I need to reinstall and start over?  Configuring a dhcp server should not be this difficult

---

### Post by koenn on 2007-11-22
configuring a dhcp server isn't hard. The first dhcp server i ever set up on linux took 10 minutes : install package, modify default config file to reflect my whishes, save, restart service, done. 

It looks like together with the trailing }, webmin cut of or forgot some required settings. Wild guess : a lease time or so. 

Here's a simple config that works : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp)
you could probably use it as an example to fix yours

---

