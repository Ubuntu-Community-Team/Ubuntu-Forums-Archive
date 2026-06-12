---
title: "Cannot connect to Apache beyond localhost"
date: 2015-01-03
forum: Server Platforms
---

### Post by joelstobart on 2015-01-03
I've setup apache on a server, with PHP and a few other bits. 
There are no errors in the error log. If I go on the server and crafting a port 80 request to the IP I get the page (source) back. This is a clean re-install of apache2 so all the configuration is default. I just want to get the example page.

When I connect from outside the server, there is no connection possible. 

I have tried enabling and disabling UFW. When enabled this is the config:

Apache                     ALLOW       Anywhere
22                         ALLOW       Anywhere
OpenSSH                    ALLOW       Anywhere
Apache (v6)                ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)
OpenSSH (v6)               ALLOW       Anywhere (v6)

When I dump netstat I get:

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      7102/apache2    

I've changed the listen directive too force it to IPV4  (to prevent errors).

Apache gives me no errrors. And an apache (apache -S) dump does the following (domain name hidden):

VirtualHost configuration:
*:80                   serverX-XXX-XXX-XX.domain.name (/etc/apache2/sites-enabled/000-default.conf:1)

Ideas would be appreciated. Have I missed a firewall (other than UFW and IPTABLES)? Is there something I should know? What other information would you like?

---

### Post by joelstobart on 2015-01-04
In case it helps anyone I have also started a port on 8080. I opened the firewall and then used NMAP internally and externally:

internally  ( nmap -sS -O -PI -PT <ipaddress>)
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
8080/tcp open  http-proxy

externally ( nmap -sS -O -PI -PT <ipaddress>)
PORT   STATE SERVICE
22/tcp open  ssh

I guess that means it's a firewall/apparmor or something?

---

### Post by Doug S on 2015-01-04
Could you edit your post to clarify which is external and which is internal, as currently they both say internal. Yes, I think you have a router or firewall issue and http requests don't even get to your server.

---

### Post by joelstobart on 2015-01-07
I think it's firewall related - but I've disabled UFW and checked the rules on ipchains. So I don't know what other firewalls it is. I'm going to check with my server provider about the router

---

