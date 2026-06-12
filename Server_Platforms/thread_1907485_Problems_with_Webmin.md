---
title: "Problems with Webmin"
date: 2012-01-11
forum: Server Platforms
---

### Post by ollie123 on 2012-01-11
I have installed Webmin on my VPS running Ubuntu Server 10.04. I can access Webmin my going to https://<my ip address>:10000. However, I cannot access it by going to https://<my domain name>.com:10000.

However, I am able to access my web server on https://<my domain name>.com:10000.

I haven't set up iptables as of yet. My hosts file is as below (in the interest of privacy I have replaced my hostname with foo and my ip with bar).

```
127.0.0.1	localhost	foo.com	foo
bar	foo.com	foo

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Is there any way I can make Webmin accessible through [https://foo.com:10000](https://foo.com:10000), or will I have to keep using the exact IP address?

---

### Post by jonobr on 2012-01-11
Whos hosting your domain?

Do you have your own DNS?
If not the very very simplest way is to modify the host file of all clients, 
if you want resolution on your own network, then you need to either setup your own DNS or have your name registered in a DNS somewhere.

Having foo.com on your hosts file on the target system wont work.
The connecting host needs to resolve either to its own host file or a DNS thats its using

---

