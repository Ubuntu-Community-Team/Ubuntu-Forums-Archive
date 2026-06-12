---
title: "Weird apache problems"
date: 2008-01-20
forum: Server Platforms
---

### Post by Dooley on 2008-01-20
Hi,

Im getting a strange warning when I restart my apache server.

apache2: apr_sockaddr_info_get() failed for myBoxName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

When I try 127.0.0.1 in my browser, works fine I see the contents of /var/www but when I try connect  a local php soap client to a local php/soap server that "should" definitely work it doesn't.

Just wondering if this could be an issue and how to resolve it.

My /etc/hosts

127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thanks in advance for any help

---

### Post by tlcoffee on 2008-01-24
add myBoxName your /etc/hosts like so:

127.0.0.1 myBoxName localhost

make sure you hostname shows myBoxName as well:


eg.
tlcoffee@NorDock:~$ hostname
NorDock


you should be good afterwards.

---

