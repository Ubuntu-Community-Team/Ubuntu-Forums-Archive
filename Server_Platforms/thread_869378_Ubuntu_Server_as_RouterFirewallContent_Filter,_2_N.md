---
title: "Ubuntu Server as Router/Firewall/Content Filter, 2 NICs setup help"
date: 2008-07-24
forum: Server Platforms
---

### Post by SergeiFranco on 2008-07-24
I need help setting up the following:
ADSL modem ->**eth0** Ubuntu Server/Squid/Dansguardian/Router/DHCP server  **eth1**-> switch -> rest of network

So far I have setup:
Ubuntu Server
Squid Proxy
Dansguardian
and eth0+eth1 as br0 bridge

But I need:
modem -> eth0 -> Router/Firewall/Gateway/Content filter/DHCP server -> eth1 -> network

It all works (sort of), the problem so far is with port 80 traffic redirection, it is not reliable, it decided not to work on some PC (randomly, either connection reset or time out).
iptables are pain to use, I could not find from quickly reading man on how to display the current rule or anything like that, so I have tried to use two different rules with similar effect, god knows what do those switches, but anyway I found these rules on "internet", obviously I understand (more or less) what is going on. Here they are:
```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```
or
```
iptables -t nat -I PREROUTING -p tcp --dport 80 -j DNAT --to 127.0.0.1:8080
```
neither of them work reliable (if I set up the machines that do not work to use proxy/8080 they work fine).

Anyway the goal is not to setup bridge (bridge was setup to test the Squid/Dansguardian). The goal is to setup router with firewall. Is there any front end (that will work in tty) for iptables, or better, web based administration?

Can some one point me on how to setup the following:
Router
Firewall (iptables??? real pain with lots of switches and obscured syntax, how to make it display current rules?)
DHCP Server

Thank you very much, your help will be highly appreciated.

---

### Post by windependence on 2008-07-24
Well, I would use untangle or pfsense, but that's just me. :)

-Tim

---

### Post by SergeiFranco on 2008-07-25
Looked at [http://www.untangle.com/index.php](http://www.untangle.com/index.php), and WOW! looks very promising.

---

### Post by rahmath on 2008-07-25
To list the current IP Tables rule;

# iptables -L

---

### Post by dark_harmonics on 2008-07-25
I just setup a squid server at my house and i had problems until i used the squid3 package not the squid package.

Then inside the /etc/squid3/squid.conf file you add the transparent option in the same place you changed the port option.
http_port 8080 transparent.

This also assumes that eth0 is your internal network card. For me i had to change the eth0 to eth1. Also i had to manually add this to my /etc/iptables.up.rules. In the section under *nat add:
-A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

Next restart squid3 with sudo /etc/init.d/squid3 restart

edit: After reading your OP i know that you need to point that command at your eth1 network interface not eth0 so the line you need to add under *nat is:
-A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080

---

### Post by macfusbluer on 2008-07-28
REDIRECT doesn't work for me on https pages, I used DNAT but didn't work for me too.

What is happening with iptables? Actually once I type the rule, it does not work, I delete the rule and I won't have internet in the server anymore.

---

### Post by dark_harmonics on 2008-07-28
It will not redirect your https traffic because https does not allow for man in the middle sort of situations. This is by design and can't be bypassed. On my network, with squid3 installed here is the iptables that is working (and i think we have the same sort of configuration). Pay special attention to my redirect command there which should be similar to yours but im using the default 3128 port for proxy. 

```
*nat
:OUTPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o eth0 -j MASQUERADE
# SQUID3 re-route to port 3128 from port 80 traffic (http)
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
COMMIT

*mangle
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
COMMIT

*filter
:FORWARD ACCEPT [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
# Internal network
-A INPUT -i eth1 -j ACCEPT
# loopback
-A INPUT -i lo -j ACCEPT
# external interface
-A INPUT -m state -i eth0 --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -m state -i eth1 --state ESTABLISHED,RELATED -j ACCEPT
COMMIT
```


We only want to redirect port 80 traffic to your proxy for a transparent solution. Otherwise i think you need to specify a separate redirect for the protocol you want to proxy. You also want to make sure you are giving permissions to your clients to your proxy, but it would give you a denial error if that was the problem. Also, if you are statically setting the proxy settings on the client to bypass the problem this cant be the cause.

---

### Post by brocky102 on 2008-07-29
I followed this tutorial [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html") and it worked great first go. Mine uses squid 2.6 runnning on port 3128 and dansguardian running on 8080 the same as the article has.

---

