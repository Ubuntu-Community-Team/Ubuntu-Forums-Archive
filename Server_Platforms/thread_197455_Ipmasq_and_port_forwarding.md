---
title: "Ipmasq and port forwarding"
date: 2006-06-15
forum: Server Platforms
---

### Post by pubwho on 2006-06-15
I have an Ubuntu Server machine that acts as an Internet gateway for my network. I installed ipmasq and dnsmasq and it all works fine.

However, I have a web server and an FTP server on my network. Can anyone please explain to me how I open the ports to allow the web and ftp servers to be seen from the Internet?

---

### Post by tymanthius on 2006-06-16
There is an admin package for ipmasq, but as I didn't even know about what you are using until I read your post, I don't know if it will do what you need.  You can always try 'man ipmasq'

---

### Post by Ixzat on 2006-06-16
By the look of it, you should be able to set some custom rules to allow for servers. Since i´m not running ipmasq myself, i do not know how, but this is the output from the package description:
```
This package contains scripts to initialize IP Masquerade for use as a firewall.  IP Masquerade is a feature of
 Linux that allows an entire network of computers to be connected to another network (usually the Internet) with
 only one network address on the other network.  IP Masquerade is often referred to as NAT (Network Address
 Translation) on other platforms.

 By default, this package configures the system as a basic forwarding firewall, with IP spoofing and stuffed routing
 protection.  The firewall will allow hosts behind the firewall to get to the Internet, but not allow connections
 from the Internet to reach the hosts behind the firewall. However, ipmasq now features a very flexible framework
 where you can override any of the predefined rules if you so choose.  It also allows you to control if the rules
 are reinterpreted when pppd brings a link up or down.

 This package should be installed on the firewall host and not on the hosts behind the firewall.

 IP Masquerade requires the kernel to be compiled with masquerading support (please see documentation for specific
 kernel options required).

```

I´m using shorewall as i found it to meet my specifications for what i needed, its easy to set up, integrates well with iptables, and is very easy to customise. If you have little time over you should check it out.

---

