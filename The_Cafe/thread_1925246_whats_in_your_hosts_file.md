---
title: "whats in your hosts file?"
date: 2012-02-14
forum: The Cafe
---

### Post by chickenPie4breakfast on 2012-02-14
As a new linux user I was wondering what you have in your hosts file.
I know on windows I had dozens of sites to block in there

---

### Post by Gremlinzzz on 2012-02-14
The hosts file is one of several system facilities that assists in addressing network nodes in a computer network. It is a common part of an operating system's Internet Protocol (IP) implementation, and serves the function of translating human-friendly hostnames into numeric protocol addresses, called IP addresses, that identify and locate a host in an IP network.

In some operating systems, the hosts file content is used preferentially over other methods, such as the Domain Name System (DNS), but many systems implement name service switches (e.g., nsswitch.conf) to provide customization. Unlike the DNS, the hosts file is under the direct control of the local computer's administrator.[1]:popcorn:

[https://en.wikipedia.org/wiki/Hosts_file](https://en.wikipedia.org/wiki/Hosts_file)

---

### Post by yetiman64 on 2012-02-14
> **chickenPie4breakfast said:**
> As a new linux user I was wondering what you have in your hosts file.
I know on windows I had dozens of sites to block in there
In my windows xp and vista installs spybot had literally thousands of entries in the hosts files. Never have I seen anything but the stock file in my use of Ubuntu.

Only thing I've used /etc/hosts for is in changing my hostname of the system. It's one of two files that get altered.
Stock standard but for my actual hostname censored.
> 127.0.0.1    localhost
127.0.1.1    **************
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by Jesus_Valdez on 2012-02-14
The usual blocking of ads sites and facebook.

that way I'm not tempeting to waste time while I'm working.

---

### Post by cariboo on 2012-02-14
I use my host file for aliasing host names to ip addresses to access other computers on my network by name, and not ip address. I use my router to block access to web sites.

---

