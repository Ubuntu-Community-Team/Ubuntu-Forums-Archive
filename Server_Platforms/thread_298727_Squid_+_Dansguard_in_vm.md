---
title: "Squid + Dansguard in vm"
date: 2006-11-13
forum: Server Platforms
---

### Post by yeleek on 2006-11-13
Hi,

Running ubuntu on a vm on a Windows 2k3 server.  Windows 2k3 is pushing out a gpo (group policy) to make sure everyones browsers connect via squid proxy.

I'm very familiar with Windows but had almost no dealings with Linux.  How can I go about configuring squid/dansguard to restrict what websites can be visited?  And can i go further and restrict instant messaging?

Thank you

B

---

### Post by yeleek on 2006-11-15
Any thoughts or suggestions please?  Or pointers on how to setup both proxy and dansguard?

Do i need squid could i use tinyproxy?  What are the pros/cons?

Thank you!

---

### Post by darrenm on 2006-11-15
> **yeleek said:**
> Any thoughts or suggestions please?  Or pointers on how to setup both proxy and dansguard?

Do i need squid could i use tinyproxy?  What are the pros/cons?

Thank you!

Its really easy mate. just apt-get both squid and dansguardian then edit a couple of config files for dansguardian. All the other defaults will do fine for Squid. Then just change everyones default gateway to the IP of the VM machine, put a DNAT iptables rule to redirect port 80 to 8080 on the VM ubuntu and its done. You can then download the main blacklist if you want to.

Just say where you get to and post if you can't do anything.

---

### Post by tomBorgia on 2006-11-15
Squid can be set up to block a list of sites (I use one to block adverts...) In your squid.conf file add 

acl bad url_regex "/etc/squid/squid-block.acl"
http_access deny bad

where squid-block.acl is a file with a list of addresses - i.e. 
[www.myspace.com](www.myspace.com)
ads.server.com
etc...
You can use a * wildcard. e.g. 
ads.*
(blocks anything with ads in the start of the URL).

If you want to restrict IM then you simply disallow the ports needed by that particular IM protocol... i.e. for msn -
acl msn port 1429 1431 1863 6901 6891-6900     
http_access deny msn

If you just allow port 80 and port 443 (https) then most websites should be ok but IM (and other things like ftp) should not work through the proxy. 

If you really need to lock stuff down tho you'll need to make sure no-one on your network can access an external proxy instead of yours (use a firewall - only allow outgoing port 80,443 and 3128 connections from your proxy server) - otherwise your hard work will be in vain!

~Tom

---

### Post by yeleek on 2006-11-15
With you up until the iptables bit - whats that then?

Many thanks

---

### Post by darrenm on 2006-11-15
Well you force everyone to proxy to the server on port 8080 (dansguardian) which then filters stuff and talks to squid on 3128 

or the easier way is to add an iptables firewall rule such as a script I've used in the past to switch between squid only or dansguardian filter:

```
#!/bin/bash

DANSGUARDIAN () {

/sbin/iptables --flush -t nat
/sbin/iptables -t nat -A PREROUTING -i eth0 -s 10.11.0.0/16 -p tcp --dport 80 -j
 REDIRECT --to-port 8080

}

SQUID () {

/sbin/iptables --flush -t nat
/sbin/iptables -t nat -A PREROUTING -i eth0 -s 10.11.0.0/16 -p tcp --dport 80 -j
 REDIRECT --to-port 3128

}
case $1 in

dansguardianplussquid) DANSGUARDIAN; clear ; echo -e "Enabling the Dansguardian
Filter\n";;
justsquid) SQUID;clear ; echo -e "Changing to Squid proxy only\n";;

esac

```

Call the script something like switchproxy, chmod it +x and put it in /sbin/

Then just run switchproxy dansguardianplussquid to redirect web traffic through dansguardian and switchproxy justsquid for just squid.

---

