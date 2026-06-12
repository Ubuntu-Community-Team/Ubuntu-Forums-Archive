---
title: "DNS behind static router how to"
date: 2011-11-15
forum: Server Platforms
---

### Post by vladimirproiect on 2011-11-15
Hello friends,
 
I am new here so this is my first post, so please bear with me.
I have a static Huawei Router with public static IP, and behind it i have configured a Ubuntu 10.04 Lucid Lynx machine for DNS , WWW, and mail purposes.
 
From outside the LAN i can access my services on the router fine via [www.domain.com]("http://www.domain.com"), or webmail.domain.com, ftp, etc.
The problem is that when i'm trying to access any of my services from LAN i have to do that by typing either the server name e.g.:server1, or by typing its IP address.
 
If i am trying to access my webpage via www, i get to the routers management page, although i've move it to port :8080.Any other NAT mapping works fine on the router, only the www issue. I've tryed changing the apache2 port in Ubuntu, but i still get the same issue.
Been talking to tech support from Huawei, and it seems that they dont know either if the router is capable to lookup reverse NAT mapping.
 
So my question is: is something wrong with my current DNS (bind) configuration on Ubuntu, or is it simply a router problem?Note that on my router i have a public IP registered to my domain.
 
Thank you in advance for your help!

---

### Post by volkswagner on 2011-11-15
I'd say your router and NAT is the problem.

Perhaps you can do a work around with your /etc/hosts file.

Edit your hosts file on the client pc you are trying to access your server from.  If you point your domain names and aliases at your LAN ip for your server it may help.

If you are using a linux client edit /etc/hosts, if you are using winXP edit /windows/system32/drivers/etc/hosts, you'll have to look up for Vista and Win7.

Also if your server is running DNS, do you have your router settings for DNS pointed at your Ubuntu server ip first?

---

### Post by Jonathan L on 2011-11-15
> **vladimirproiect said:**
> Hello friends,
 
I am new here so this is my first post, so please bear with me.
I have a static Huawei Router with public static IP, and behind it i  have configured a Ubuntu 10.04 Lucid Lynx machine for DNS , WWW, and  mail purposes.
 
From outside the LAN i can access my services on the router fine via [www.domain.com]("http://www.domain.com/"), or webmail.domain.com, ftp, etc.
The problem is that when i'm trying to access any of my services from  LAN i have to do that by typing either the server name e.g.:server1, or  by typing its IP address.
 
If i am trying to access my webpage via www, i get to the routers  management page, although i've move it to port :8080.Any other NAT  mapping works fine on the router, only the www issue. I've tryed  changing the apache2 port in Ubuntu, but i still get the same issue.
Been talking to tech support from Huawei, and it seems that they dont  know either if the router is capable to lookup reverse NAT mapping.
 
So my question is: is something wrong with my current DNS (bind)  configuration on Ubuntu, or is it simply a router problem?Note that on  my router i have a public IP registered to my domain.
 
Thank you in advance for your help!

Hi Vladimir

As I understand it, you have something like this:

[LIST]
[*] a router, with addresses like 1.2.3.4 on the outside, and 192.168.0.1 on the inside.
[*] an Ubuntu 10.04 server, say 192.168.0.2, serving DNS, web, ftp etc.
[*] Router forwards ports 53 (DNS), 80 (web) and others to 192.168.0.2.
[*] Other computers on the inside, including a laptop 192.168.0.128
[*] The DNS config is with external addresses, ie [www.domain.com]("http://www.domain.com") -> 1.2.3.4
[/LIST]
  I assume the laptop uses the server for DNS.  When it asks for [www.domain.com,if](www.domain.com,if)  the DNS gives the correct 'outside' answer, 1.2.3.4, then your laptop  will think the system is outside: this is exactly correct if you were  running DNS but hosing your server elsewhere.  And so laptop routes the  request outside, and the router picks it up for itself!
 
 If however, your DNS server gives the answer 192.168.0.2, your internal clients  will work correctly.  But unless the router does the right thing with  the NAT on the DNS packets, you'll be giving out the unreachable  internal address.  But doing the "right thing" with NAT in DNS is basically impossible (because you may have ports forwarded to different internal addresses) and so what you need is split DNS.

_**Split DNS**_

For "split DNS" -- different answers to different enquirers --  you basically run  two sets of DNS, one for internal queries, one for external.

_Easy way_

The easy way is use separate DNS servers for internal and external  answers, and the easiest way to do that is to use a domain company's DNS  servers for your external addresses (ie, to give to people who are  outside your LAN).  Then your internal server delivers local 192.168  addresses, and is only used by your local hosts.   Only systems inside your LAN ask your server to resolve [www.yourdomain.com]("http://www.yourdomain.com"), and so they get internal answers.  External people ask the DNS company's servers, and get external answers.

_Clever way_

The clever way to do this is with bind's "view" command, which can instruct it to give different answers to the same question depending on who asks.  The client gets the first matching view.  "localnets" means any network which the server has an interface on (in this case 10.0.0.0/8 and 127.0.0.1)

Basically you set up your zones like this:
```
view "inside" {
  match-clients { localnets; };
  zone "example.com" {
    type master;
    file "/etc/bind/example.com.inside";
  };
};
view "outside" {
  match-clients { any; };
  zone "example.com" {
    type master;
    file "/etc/bind/example.com.outside";
  };
};

```Then you have two definition files for example.com.

This is example.com.inside:
```
example.com. 1000 SOA this.example.com that.example.com 2011111501 900 900 1800 60
example.com. 100[COLOR=Red]0[/COLOR] A [COLOR=Red]192.168.0.2[/COLOR]
example.com. 100[COLOR=Red]0[/COLOR] NS example.com.
```This is example.com.outside:

```

example.com. 1001 SOA here.example.com there.example.com 2011111502 901 901 1801 61
example.com. 100[COLOR=DeepSkyBlue]1[/COLOR] A [COLOR=DeepSkyBlue]1.2.3.4[/COLOR]
example.com. 100[COLOR=DeepSkyBlue]1[/COLOR] NS example.com.

```When I've done this on large networks there were servers for each  purpose (internal resolution, internal service, external service) so it  was easy enough to use the "easy" way, and there's nothing wrong with it if you have enough real or virtual servers.  The clever way is probably what will suit your situation best.  The only trick to watch out for when using views is this error message (in /var/log/daemon.log) "when using 'view' statements, all zones must be in views", which just means you have to have everything inside a view, including the things normally listed in /etc/bind/named.conf.default-zones

I tested it with bind 9.7.0-P1 on Ubuntu 10.04.2 server (apt-get install bind9),  works perfectly, documentation in [bind manual]("http://ftp.isc.org/isc/bind9/cur/9.8/doc/arm/Bv9ARM.ch06.html#view_statement_grammar").  To test from outside, use a web-based dig such as [http://www.kloth.net/services/dig.php](http://www.kloth.net/services/dig.php)  Testing against the "forwarded-to NAT address may or may not work, depending on your router.


```
ubuntu@ip-10-58-177-204:/etc/bind$ dig @10.58.177.204 example.com a

; <<>> DiG 9.7.0-P1 <<>> @10.58.177.204 example.com a
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9931
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.            IN    A

;; ANSWER SECTION:
example.com.        100[COLOR=Red]0[/COLOR]    IN    A    [COLOR=Red]192.168.0.2[/COLOR]

;; AUTHORITY SECTION:
example.com.        100[COLOR=Red]0[/COLOR]    IN    NS    example.com.

;; Query time: 0 msec
;; SERVER: 10.58.177.204#53(10.58.177.204)
;; WHEN: Tue Nov 15 13:06:37 2011
;; MSG SIZE  rcvd: 59

```This is against the outside interface:

```

ubuntu@ip-10-58-177-204:/etc/bind$ dig @79.125.93.173 example.com a

; <<>> DiG 9.7.0-P1 <<>> @79.125.93.173 example.com a
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19934
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;example.com.            IN    A

;; ANSWER SECTION:
example.com.        100[COLOR=DeepSkyBlue]1[/COLOR]    IN    A    [COLOR=DeepSkyBlue]1.2.3.4[/COLOR]

;; AUTHORITY SECTION:
example.com.        100[COLOR=DeepSkyBlue]1[/COLOR]    IN    NS    example.com.

;; Query time: 0 msec
;; SERVER: 79.125.93.173#53(79.125.93.173)
;; WHEN: Tue Nov 15 13:06:40 2011
;; MSG SIZE  rcvd: 59

```Apologies for length; thought it might be helpful to give a full example of split DNS.

Hope that's of some help.

Kind regards,
Jonathan.

---

### Post by btindie on 2011-11-15
Your clients are using the inbuilt DNS server in the router and not BIND that's running on your server so they're unable to resolve the hostnames.

The easiest option is to probably disable the DHCP server on the router and have your Ubuntu server hand out IP addresses along with the correct DNS server IP.

---

### Post by vladimirproiect on 2011-11-22
hey thanks , you all.I'll try some of your hints, and i'll keep you posted.
 
thanks once again.

---

### Post by vladimirproiect on 2011-11-22
> **volkswagner said:**
> I'd say your router and NAT is the problem.

Perhaps you can do a work around with your /etc/hosts file.

Edit your hosts file on the client pc you are trying to access your server from.  If you point your domain names and aliases at your LAN ip for your server it may help.

If you are using a linux client edit /etc/hosts, if you are using winXP edit /windows/system32/drivers/etc/hosts, you'll have to look up for Vista and Win7.

Also if your server is running DNS, do you have your router settings for DNS pointed at your Ubuntu server ip first?
Yes my router points to the ubuntu dns machine, and forwardings on the router i belive are done properly.eg: wan port :80 -> 192.168.x.x (Ubuntu Dns)-> port :80
 
i belive it's a problem of split DNS just how Johnatan says, however, it also seems like some Huawei gateway Routers cannot perform reverse NAT.
 
One of my options is to buy a linksys or a Dlink adsl/adsl2+ router if i wont be able to resolve this the software way.Its not really a big issue but its anoying pointing my browser all the time to the servers ip or name (eg: [http://server1](http://server1)).

---

### Post by vladimirproiect on 2011-11-22
Hey guy, i solved the problem. I've simply bridged the Huawei HG655b router with a D-Link Di524 router and everything works fine now.
Does reverse NAT flawlessly.
Thank you all for your help!
 
Problem solved

---

