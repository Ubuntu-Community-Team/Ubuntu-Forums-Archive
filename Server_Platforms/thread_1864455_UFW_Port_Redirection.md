---
title: "UFW Port Redirection"
date: 2011-10-19
forum: Server Platforms
---

### Post by jemate18 on 2011-10-19
I have built an Internet gateway using Ubuntu Server 11.10 x64_86. 

Details:
* IP address: 192.168.1.1
* Only one interface - eth0 (There is a separate firewall device that translates this to public IP for internet access)
* UFW enabled
* Squid3 plus squidguard

What I want
1. forward all traffic from port 80 to port 3128 so that squid may block unauthorized sites.

What I did.
*On my test PC, i put the 192.168.1.1 as the gateway so that I can access the Internet. On the browser, no PROXY settings. Results, successful connection and can access different sites.*

*However, squid3 seems not to be intercepting traffic, and therefore sites are not blocked*

What I test
[I]I used tcpdump port 3128. Result, no traffic.
I used tcpdump port 80. Result, successful logging of sites
accessed by my test PC[/I]

To test if squid/squidguard is working here is what I did.
*On the test PC i set the proxy to 192.168.1.1:3128. Result, blocking successful and squid is working*


What I want
*Port forwarding for 80 to 3128*


here is the status of my ufw
```
Status: active

To                         Action      From
--                         ------      ----
3128                       ALLOW       192.168.1.0/24
22                         ALLOW       192.168.1.70
80                         ALLOW       192.168.1.0/24

```


Here is a partial code of my /etc/ufw/before.rules
```
#
*nat
:PREROUTING ACCEPT [0:0]
[COLOR="Green"]-A PREROUTING -i eth0 --src 192.168.1.1 -p tcp --dport 80 -j REDIRECT --to-ports 3128[/COLOR]
COMMIT

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines

```


Partial squid.conf
```
http_port 3128 transparent 
acl localnet src 192.168.1.0/24
http_access allow localnet


```


please help on port forwarding

---

### Post by jemate18 on 2011-10-19
Is there any rule I need to add for /etc/ufw/before.rules?

Seems like port redirection is not working.

---

### Post by jemate18 on 2011-10-19
Just tried the setup again, without changing any configuration.

My client PC can't access the Internet anymore if "no proxy" is set to the browser.

Therefore, the "gateway" seems not to be working anymore?

This is some strange behavior as yesterday the gateway works and that only port forwarding does not work.

---

