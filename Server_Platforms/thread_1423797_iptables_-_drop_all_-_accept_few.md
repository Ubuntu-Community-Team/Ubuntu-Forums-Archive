---
title: "iptables - drop all - accept few"
date: 2010-03-07
forum: Server Platforms
---

### Post by arpheus on 2010-03-07
Hello, I have an Ubuntu server with 2 network cards.
eth0 connects to the internet
eth1 connects to the internal network (it's a dhcp and gives local ip's to the clients)

I need to block everything for the clients (in and out), but only allow access to a few http sites and a few radio stations (utp).

I have tried and tried, got something to work but doesn't work as it should.

Please give me some generic iptables rules for this.

---

### Post by koenn on 2010-03-07
```

## set policy to drop all
iptables --policy FORWARD DROP


## allow execptions
# allow connection to specified host 
iptables -A FORWARD  -d 123.123.123.123  -j ACCEPT

# allow connection to specified host on given tcp port
iptables -A FORWARD -p tcp -d 123.123.123.234 --dport 80  -j ACCEPT

# allow connection to specified host on given udp port
iptables -A FORWARD -p udp -d 123.123.123.111 --dport 53  -j ACCEPT



## allow traffic once a connection has been made 
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

```
remember to allow exceptions for all dns, dhcp, ... as required

you probably need a MASQUERADE rule as well


---
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/security-guide/s1-firewall-ipt-fwd.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/security-guide/s1-firewall-ipt-fwd.html)
[http://www.brandonhutchinson.com/iptables_fw.html](http://www.brandonhutchinson.com/iptables_fw.html)

---

### Post by arpheus on 2010-03-07
Would this be needed as a first line?
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

Allow DNS and DHCP like this?
```

# dns
iptables -A FORWARD -p udp -s 192.168.1.0/24 --dport 53  -j ACCEPT

# dhcp
iptables -A FORWARD -p udp -s 192.168.1.0/24 --dport 67  -j ACCEPT

```

Is there a way to use hostnames instead of ip's (in case the website changes their ip)? Would this slow down iptables, or the server?

I have set the dhcp to assign a few ip's based on the client mac.
Do i need a MASQUERADE rule?

Also, would this do for squid?
```
iptables -A FORWARD -p tcp --dport 80 -j REDIRECT --to-port 3128
```

Thank you koenn for your help, I wouldn't have guessed the last line. Looks like it's important.

---

### Post by koenn on 2010-03-07
you need to set  /proc/sys/net/ipv4/ip_forward to 1, but it doesn't need to be the first line. It's a kernel option that allows your server to forward packets to other hosts. You might want to put it last so that your firewall is up before your server to route traffic.

i think your dns and dhcp rules are OK. although you don't stricktly need the specify a source network, I think. 

You're using addresses from a private address space, so you need to masquerade to have internet access for those hosts

iptables understands host names but using them is not a good idea because it will require dns lookups to resolve them to addresses. This causes delay and processing overhead, and stuff will stop working if there is no DNS servoice available. 
It's not unusual, on the other hand, to use variables to hold addresses and network numbers, so the firewall script is more maintainable.

re your squid question, it looks like you want a transparent proxy.
you probably need a --dport 80 -j ACCEPT before you do the redirect, and in the REDIRECT statement you probaby need to specify a table (nat or prerouting, I'm not sure which)

---

### Post by koenn on 2010-03-07
re squid:

try something like
```

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

```

since this is traffic *towards* your server, the FORWARD rules don't apply and you *may* need additional INPUT and OUTPUT rules, something along the lines of 

```
iptables -A INPUT -i eth1 -p tcp --dport 80   -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --dport 3128 -j ACCEPT

iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```
but you might want to check that or find a transparent proxy howto

---

### Post by arpheus on 2010-03-07
Thanx, sounds ok.

What about masquerading?

---

### Post by koenn on 2010-03-07
```
iptables -t nat -A POSTROUTING  -o eth0 -j MASQUERADE
```

i.e. everyting going out of eth0 (the public interface) should use eth0's ip adress as source address (ie. the 192.168.... source addresses will be replaced by eth0's  adres, so the replies will know a routable destination)

---

### Post by arpheus on 2010-03-08
Isn't this better?

```
iptables -t nat -A POSTROUTING  -i eth1 -j MASQUERADE
```

---

### Post by koenn on 2010-03-08
why do you think it would be better ?

---

