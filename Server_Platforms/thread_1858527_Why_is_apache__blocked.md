---
title: "Why is apache  blocked?"
date: 2011-10-12
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2011-10-12
Hi,
I have an Ubuntu server at my workplace set up as a gateway for our network as well as a small website.  I can't access the website from outside our lan.  

The gateway works fine, it has a transparent squid proxy server which has all local traffic sent to the squid port by the firewall.  I can access the internet fine from any computer on the lan.  

When I try to access our website from an external ip I get the following message in the web browser:
```

ERROR
The requested URL could not be retrieved

The following error was encountered while trying to retrieve the URL: http://MY.IP.ADDRESS/

    Access Denied.

Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

Your cache administrator is webmaster.

Generated Wed, 12 Oct 2011 16:39:06 GMT by xxxx(squid/2.7.STABLE9)
```

It mentions squid in the error message so I suspect that port 80 is routed to squid for external access as well.  Its iroic that I am the administrator.  I guess I should contact myself.

I'm not really keen on iptables so I may have made a mistake here.  Take a look at my iptables settings:

```

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X

echo "Rules Reset"

## Masquerade settings
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.3.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

echo "Masquerade Set"

##  Squid Setting
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.3.1:8080
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080

echo "Squid Set"

```

The server is installed like this:
internet <--> ADSL modem <--> eth0 <--> eth1 <--> LAN

so eth0 is the external interface and eth1 is connected to the lan.  Port 8080 is the squid port.



Here's my squid.conf file if it helps:
```
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl purge method PURGE
acl CONNECT method CONNECT
acl uwg src 192.168.3.0/24
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow uwg
http_access allow localhost
http_access deny all
icp_access allow localnet
icp_access deny all
http_port 8080 transparent
hierarchy_stoplist cgi-bin ?
logformat squid %tl %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
access_log /var/log/squid/access.log squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$	0	20%	2880
refresh_pattern .		0	20%	4320
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
hosts_file /etc/hosts
coredump_dir /var/spool/squid

```


Any ideas?

---

### Post by erixnow on 2011-10-12
I know this may not help,  I was good with ipchains and earlier iptables.

It is always best to get a hardware gateway unless you need a specific setup.  Nothing I have come across configures iptables correctly.  I just recently had problems ingress packets.  it took me two days to debug,  and that is without having anothercomponent like squid.

Why do you need squid. are you planning to proxy company users?  iptables will do the Natting for you if that is what you need.



Regards,
  Eric Peyser

---

### Post by erixnow on 2011-10-12
also at a glance squid config looks restrictive to WAN

---

### Post by The Sorrow on 2011-10-12
Check the squid config and make sure its not preventing access. I use squid on my firewall and it is a tricky little app.

---

### Post by abandonedthe_mulletator on 2011-10-12
I'm not very familiar with squid.conf.  I recently set it up.  Which part is restricting WAN?  That might be my problem.

---

### Post by SeijiSensei on 2011-10-12
```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.3.1:8080
```

If eth0 is the externally-facing interface, you probably don't want this rule.  I'm guessing you only want to push internal LAN requests through the squid cache.  Try commenting this out and connecting again from outside.

Personally, I'd make the default INPUT policy be DROP and add specific INPUT rules to enable the networks and services you need.  But let's start small and see if you can get what you have set up working first.

---

### Post by abandonedthe_mulletator on 2011-10-12
Thanks SeijiSensei,

I took that part out of the iptables rules.  It did not solve my problem.  Everything else still works so I'll leave it out for now.

I'll have to redo the iptables rules in the future, I am quite new to it.

I suspect squid is to blame.  How can squid deny apache if iptables does not redirect traffic to squid?

---

### Post by SeijiSensei on 2011-10-12
Try moving the squid rules ahead of the masquerading rules.

---

### Post by abandonedthe_mulletator on 2011-10-12
I tried that and it did not make a difference.

---

### Post by The Sorrow on 2011-10-12
[_Here is a good explanation of Squid.conf_]("https://calomel.org/squid.html")

---

### Post by abandonedthe_mulletator on 2011-10-14
I tried a couple of things with no luck.

I stopped the squid service and the website became unreachable

I commented out the "http_access deny all" part of squid.conf

Also tried adding an "allow" section for an external IP and tried connecting from that IP.
```
acl external src xxx.xxx.xxx.xxx[external IP]
http_access allow external
```

I still have not got it working.

---

