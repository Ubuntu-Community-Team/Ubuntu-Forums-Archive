---
title: "Setting up a DNS,DHCP,Proxy server on Ubuntu 10.04"
date: 2011-05-02
forum: Server Platforms
---

### Post by hawk2010 on 2011-05-02
Hi All,

Yet again I'm having a bit of a problem figuring out the following. 

I have a server running Ubuntu 10.04 LTS (server edition) which has two NICs. One of the NICs (eth0) is connected to my ADSL router and the other (eth1) is connected to a Wireless AP. most of my client's are on wireless
. What i want to do is to have a transparent proxy for wireless access and also add rules so the wireless clients can access some of the servers on the eth0 side (I have AV server, network, servers, printers, running on that IP range)

Currently the DHCP3 server is listening on eth1 and giving out IP addresses, Also I have setup BIND9 dns listening on eth1 as well.

My issues are 
1.how am I going to forward the web based traffic to the proxy like port 80, 443 etc. and
2. How can I configure the DNS so that it can use my ISP's DNS to resolve domain names.
3.. how can I forward traffic destined to the network printer (which is on the etho network) using this gateway.

Thanks a lto!!

---

### Post by Demented ZA on 2011-05-02
1) Google squid transparent proxy or look [here]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html"). Keep in mind that in order to run a _transparent_ proxy server, you can't use authentication. I suppose you can use some form of ACL, like limitin IP ranges, hostnames etc, but since the browser doesn't know its going through a proxy, it doesn't expect to be challenged for authentication. This is a limitation of browsers, not squid. If you want authentication, you'll have to drop transparent from requirements and be prepared to configure each browser to use a proxy.

2) Is your DNS server not already forwarding unresolved DNS queries to your ISP's DNS? This is default behavior if you have bind9 installed.

3) Have you set up your firewall yet? If you are not familiar with ip tables and such, or even if you are, have a look at [Shorewall]("http://www.shorewall.net/"). Shorewall greatly simplifies setting up the 
Linux firewall but doesn't sacrifice functionality, security or speed. It basically simplifies IPTables. Thats it.

---

### Post by SeijiSensei on 2011-05-02
> **Demented ZA said:**
> Keep in mind that in order to run a _transparent_ proxy server, you can't use authentication. I suppose you can use some form of ACL

That's the easiest solution.  The default /etc/squid/squid.conf file has sample ACL's that allow localhost and the local network to use the proxy and block other IPs.  Of course, if an intruder can get your wireless router to give him or her an address, then all bets are off.  You are using WPA2 for password authentication to the router, I hope?

Note that you can't proxy HTTPS connections without it appearing like a "man-in-the-middle" attack from the browser's point of view.  If you're using squid to control website access, you'll need to use iptables rules to block HTTPS connections.

---

### Post by koenn on 2011-05-02
> **Demented ZA said:**
> 1) ... you'll have to drop transparent from requirements and be prepared to configure each browser to use a proxy.
or use Web Proxy Auto-Detection.

---

### Post by Demented ZA on 2011-05-02
> **koenn said:**
> or use Web Proxy Auto-Detection.

Yes, you can definitely use Web Proxy Auto-Detection (WPAD). 

Its not "transparent", as the clients browser has to be set to auto detect, (a few clicks to set up) but its the next best thing. On that note, I think IE 8 and 9 are set by default to auto detect proxy settings? Firefox has to be adjusted. Not sure about Chrome. Haven't used WPAD yet, but I plan to.

Some info on the topic I looked at:
[http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol](http://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol)

I know this is for Windows, but it shows whats needed in a few simple steps. Substitute Win for *nix:
[http://www.grape-info.com/doc/win2000srv/internet-gw/wpad/index.html](http://www.grape-info.com/doc/win2000srv/internet-gw/wpad/index.html)

---

### Post by koenn on 2011-05-02
AFAIK both IE and Firefox ship with "proxy: detect settings for this network". 
the catch is that firefox ignores wpad / pac settings provided in DHCP options. It does work with wpad through DNS. 
Accoding to wikipedia, same with Chrome.
IE does WPAD through both DHCP and DNS.

---

### Post by hawk2010 on 2011-05-02
Thanks a lot. I have configured it to use as a transparent proxy and I do not use proxy authentication and had configured to issue DHCP static IPs based on the client's NIC MAC.

The issue is the DNS doesn't resolve since. Now BIND9 listens to eth1 because my client's are on that interface. When it gets a query on eth1 if the DNS doesn't know it should ask right ? So how do i configure that.? I have done ipforwarding on sysctl.conf

I'm planning to use the ubuntu server's built in iptables. and use ufw to config it.


> **Demented ZA said:**
> 1) Google squid transparent proxy or look [here]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html"). Keep in mind that in order to run a _transparent_ proxy server, you can't use authentication. I suppose you can use some form of ACL, like limitin IP ranges, hostnames etc, but since the browser doesn't know its going through a proxy, it doesn't expect to be challenged for authentication. This is a limitation of browsers, not squid. If you want authentication, you'll have to drop transparent from requirements and be prepared to configure each browser to use a proxy.


2) Is your DNS server not already forwarding unresolved DNS queries to your ISP's DNS? This is default behavior if you have bind9 installed.

3) Have you set up your firewall yet? If you are not familiar with ip tables and such, or even if you are, have a look at [Shorewall]("http://www.shorewall.net/"). Shorewall greatly simplifies setting up the 
Linux firewall but doesn't sacrifice functionality, security or speed. It basically simplifies IPTables. Thats it.

---

### Post by hawk2010 on 2011-05-02
Yup  I have configured it to my internal IP range on the ACLs. and my Wireless is on WPA2. Can i let the proxy pass the https connections without getting that MiTM ? 

My client's do use gmail and other services which uses https. further they need to connect to our mail server, samba server and printer as well. 

My problem is first :

1. How can I configure my DNS to forward queries to my ISP dns since its listening on eth1. my ISP can be reached on eth0?

2. How can I allow all http/https traffic through my squid proxy.?

3. How can I allow only my chosen services to be accessed from my clients.? (should i configure this in squid or iptables?)


> **SeijiSensei said:**
> That's the easiest solution.  The default /etc/squid/squid.conf file has sample ACL's that allow localhost and the local network to use the proxy and block other IPs.  Of course, if an intruder can get your wireless router to give him or her an address, then all bets are off.  You are using WPA2 for password authentication to the router, I hope?

Note that you can't proxy HTTPS connections without it appearing like a "man-in-the-middle" attack from the browser's point of view.  If you're using squid to control website access, you'll need to use iptables rules to block HTTPS connections.

---

### Post by SeijiSensei on 2011-05-03
> **hawk2010 said:**
> 1. How can I configure my DNS to forward queries to my ISP dns since its listening on eth1. my ISP can be reached on eth0?

Squid will resolve addresses using the servers appearing in /etc/resolv.conf.  I'd let the DNS server bind to localhost (127.0.0.1) as well as eth1.  Then set the first entry in /etc/resolv.conf to "nameserver 127.0.0.1".  Alternatively you can replace 127.0.0.1 with the IP address assigned to eth1.  The DNS server will actually not query your ISP but the designated name servers for the domains it needs to resolve.  You need to make sure that your firewall leave UDP port 53 open in both directions so your nameserver's queries can be replied to.

> 2. How can I allow all http/https traffic through my squid proxy.?

If you don't have any ACLs defined in /etc/squid/squid.conf, all HTTP traffic will be permitted.  As I said before, you can't proxy HTTPS traffic without a lot of work.

> 3. How can I allow only my chosen services to be accessed from my clients.? (should i configure this in squid or iptables?)

Do you mean letting your clients access, say, remote SSH servers, but not FTP servers?  You'd do that in iptables:

```

iptables -P INPUT DROP

[some rules]

iptables -A INPUT -p tcp --dport 22 -j ACCEPT


```

The default DROP policy blocks all traffic not specifically permitted by an INPUT rule.  The example rule allows connections to all SSH servers (port 22).

---

### Post by hawk2010 on 2011-05-03
I will do the DNS server changes and test. With regard to squid, I'm using ACLS to define the network and the services that can be accessed. I'm passing through https traffic though. 

how to configure IPtables to send all http traffic through to the proxy and for the proxy to send it back to the client?

Also shouldn't there be a need to include routing entries since I have two interfaces with two different IP ranges.
You proposed including iptables -A INPUT -p tcp --dport 22 -j ACCEPT 


> **SeijiSensei said:**
> Squid will resolve addresses using the servers appearing in /etc/resolv.conf.  I'd let the DNS server bind to localhost (127.0.0.1) as well as eth1.  Then set the first entry in /etc/resolv.conf to "nameserver 127.0.0.1".  Alternatively you can replace 127.0.0.1 with the IP address assigned to eth1.  The DNS server will actually not query your ISP but the designated name servers for the domains it needs to resolve.  You need to make sure that your firewall leave UDP port 53 open in both directions so your nameserver's queries can be replied to.



If you don't have any ACLs defined in /etc/squid/squid.conf, all HTTP traffic will be permitted.  As I said before, you can't proxy HTTPS traffic without a lot of work.



Do you mean letting your clients access, say, remote SSH servers, but not FTP servers?  You'd do that in iptables:

```

iptables -P INPUT DROP

[some rules]

iptables -A INPUT -p tcp --dport 22 -j ACCEPT


```The default DROP policy blocks all traffic not specifically permitted by an INPUT rule.  The example rule allows connections to all SSH servers (port 22).

---

### Post by SeijiSensei on 2011-05-04
> **hawk2010 said:**
> how to configure IPtables to send all http traffic through to the proxy and for the proxy to send it back to the client?

You use an iptables rule on the Squid gateway like this one:

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 10.1.1.0/24 --destination-port 80
```

This tells iptables to take all traffic from the local network that targets a remote port 80 and push it to port 3128.  Replace 10.1.1.0/24 with the address/mask of your local network.

> Also shouldn't there be a need to include routing entries since I have two interfaces with two different IP ranges.

Well the rule I gave you allows all IP ranges.  If you want more narrow rules, use the "-s" parameter:
```
iptables -A INPUT -p tcp -s 10.1.1.0/24 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.1.2.0/24 --dport 22 -j ACCEPT
```
Now only the designated address blocks will be able to use SSH.

---

### Post by hawk2010 on 2011-05-05
Great thanks. 

Now I can browse the http sites but not https. If I need to allow https through I should do the following or is there more things to do

iptables -A INPUT -p tcp -s 10.1.1.0/24 --dport 443 -j ACCEPT


> **SeijiSensei said:**
> You use an iptables rule on the Squid gateway like this one:

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 10.1.1.0/24 --destination-port 80
```This tells iptables to take all traffic from the local network that targets a remote port 80 and push it to port 3128.  Replace 10.1.1.0/24 with the address/mask of your local network.



Well the rule I gave you allows all IP ranges.  If you want more narrow rules, use the "-s" parameter:
```
iptables -A INPUT -p tcp -s 10.1.1.0/24 --dport 22 -j ACCEPT
iptables -A INPUT -p tcp -s 10.1.2.0/24 --dport 22 -j ACCEPT
```Now only the designated address blocks will be able to use SSH.

---

### Post by SeijiSensei on 2011-05-05
Yes, if you deny INPUT by default, you have to permit tcp port 443 to enable HTTPS access.

Just as a general hint, the quickest way to answer questions like yours is to just give it a try.  Either your solution will work or it won't.  You can't really "break" anything if you just make one change at a time and evaluate the consequences.

---

### Post by hawk2010 on 2011-05-06
Hi SeijiSensei, Thanks for all the support. I have put that rule but it  still doesn't work. I even tried to redirect dport 443 traffic to squid  and get squid to send the https traffic through but that didn't work  either. However if I put the proxy IP and the port on I.E. the https  connection goes through. My issue is that i have a variety of clients  using different devices. IS there any additional rule which i can add  for the https to work? I even tried doing WPAD to automatically  configure the clients but even with that https didn't work.

---

### Post by SeijiSensei on 2011-05-07
Do you have a generic masquerading rule in iptables?  Squid will pass through traffic on port 80 since it takes the request and reissues it to the remote server.  All your other outbound traffic needs to be masqueraded.  Just do a Google search for "iptables masquerade", and you'll get lots of help on this.

---

### Post by hawk2010 on 2011-05-10
Hi Sensei. I do not have a masquerading rule. I will check it out.

---

