---
title: "how do i use gufw to forward port 80 to 8080"
date: 2012-05-21
forum: Security
---

### Post by lance bermudez on 2012-05-21
I have squide with dansguardian on a laptop and need to have incoming port 80 forwarded to 8080 so that even if the user tries to change the proxy setting it will still go to port 8080. was told to add the below to /etc/ufw/before.rules

*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
COMMIT
iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080

but do not know were to put them. below is my whole file

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
COMMIT
iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080

*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT

# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT


when i have ufw enable no internet traffic works
:/etc/ufw$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
8080/tcp                   ALLOW       Anywhere (log-all)
127.0.0.1 8080             ALLOW       127.0.0.1 80 (log-all)
127.0.0.1 3128             ALLOW       127.0.0.1 8080 (log-all)
3128/tcp                   ALLOW       Anywhere (log-all)
127.0.0.1                  ALLOW       80 (log-all)
8080/tcp                   ALLOW       Anywhere (v6) (log-all)
3128/tcp                   ALLOW       Anywhere (v6) (log-all)

---

### Post by cariboo on 2012-05-22
A bump for the move to bring it to the top of the page.

---

### Post by lance bermudez on 2012-05-23
If it dose not go at the top then were do I place them at? I have been reading the file and is say i need something that starts with

# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
# ufw-before-input
# ufw-before-output
# ufw-before-forward

How would you do this? I have been looking arount the internet and have found some people use iptables to do this. I thought gufw and ufw was a front to iptables?

---

### Post by Ms. Daisy on 2012-05-23
Yes, ufw is a front end for iptables.

Did you see this:

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

You need to follow the ufw directions (toward the end of the page) if that's what you're using.

---

### Post by satish_j on 2012-05-23
> **lance bermudez said:**
> I have squide with dansguardian on a laptop and need to have incoming port 80 forwarded to 8080 so that even if the user tries to change the proxy setting it will still go to port 8080.

iam not sure but i think this(port forwarding) is not something firewall is supposed to handle..

---

### Post by lance bermudez on 2012-05-27
I'a doing this on one compter with one net card. using 
http://blog.bodhizazen.net/linux/how-to-transparent-proxy/

sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-port 8080
sudo iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-port 8080

at very end of file
# don't delete the 'COMMIT' line or these rules won't be processed

COMMIT

*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A OUTPUT -p tcp -m tcp --dport 80 -m owner --uid-owner root -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 8118 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080
-A OUTPUT -p tcp -m tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-port 8080

# don’t delete the ‘COMMIT’ line or these rules won’t be processed
COMMIT

ufw looks like
8080                       DENY        Anywhere
3128                       DENY        Anywhere
192.168.#.7 8080           ALLOW       192.168.#.0/24
192.168.#.7 3128           ALLOW       192.168.#.0/24
8080                       DENY        Anywhere (v6)
3128                       DENY        Anywhere (v6)


squid looks like
# Squid normally listens to port 3128
http_port 3128 transparent
acl lbermudez src 192.168.2.0/24 
acl localnet src 127.0.0.1/32
http_access allow lbermudez
http_access allow localnet

this does not work I can still get around the filter unless the settings are set in firefox and the above was suppost to work with out have to set the setting.

---

### Post by bodhi.zazen on 2012-05-27
I can not really tell from what you have posted what you are trying to do exactly. In your first post you are talking about filtering incoming traffic to port 80, are you running a server ? My guess is that you are not.

In order to properly configure your proxies you need to understand iptables and how to configure proxies.

Starting with the proxies, your outbound traffic goes first to dansguardian listening on port 8080 , and then from dansguardian to squid listening on port 8123, and then from squid to servers on "the Internet" listening on port 80.

So , do you have your proxies properly configured ?

Assuming so ...

```
# allow root out for tools such as apt-get
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner root -j ACCEPT

# redirect anyone trying to directly access squid back to dansguardian.
sudo iptables -t nat -A OUTPUT -p tcp --dport 8123 -m owner ! --uid-owner dansguardian -j REDIRECT --to-port 8080

# redirect all traffic on port 80 to dansguardian 
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner ! --uid-owner proxy -j REDIRECT --to-port 8080
```

---

### Post by lance bermudez on 2012-06-01
do I put this in /etc/ufw/before.rules or just at the command line?

---

### Post by bodhi.zazen on 2012-06-02
> **lance bermudez said:**
> do I put this in /etc/ufw/before.rules or just at the command line?

Personally I would get it working on the command line first, then move it to before.rules

---

