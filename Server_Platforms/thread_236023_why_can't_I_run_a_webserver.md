---
title: "why can't I run a webserver?"
date: 2006-08-14
forum: Server Platforms
---

### Post by newtolinuxx on 2006-08-14
I have Ubutnu server 6.06 LAMP installed with ubuntu-desktop.

I'm trying to run a webserver but I can only serve pages across my lan, not to the outside world.

I have ports 80, 81 and 20080 open (I'm running emule ok on another computer so I'm sure they're open).

I've added them to ports.conf for apache2 and restarted apache2

My iptables are empty (all set to policy ACCEPT)

I'm using IP not FQDN to request


When I request on port 80 I get a connection refused 111 error message from my ISP but I still see data in tcpdump

When I request on any other port I get a firefox cannot connect to server error but I still see data in tcpdump


Can someone help me decode the tcp dump output?

 tcpdump port 20080 -i 2
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
15:21:53.801856 IP peterserv.40287 > pppBKK.20080: S 175549812:175549812(0) win 5840 <mss 1460,sackOK,timestamp 383331 0,nop,wscale 2>
15:21:54.003413 IP pppBKK.20080 > peterserv.40287: R 0:0(0) ack 175549813 win 0

2 packets captured
4 packets received by filter
0 packets dropped by kernel

---

### Post by harisund on 2006-08-14
I have a real strong feeling your ISP blocks port 80 (most ISPs do)

---

### Post by riverman on 2006-08-14
Forgive me for wading in; I'm no expert on this. Maybe you know all about what I'm about to say, and it's not an issue for you. But, does your ISP know that you're trying to serve webpages from your computer?  If you haven't ok-ed it with them, it's unlikely to work - you might get in trouble as well ;) They might not look kindly on the extra traffic, and with most ISPs you wouldn't get a fixed IP address, which would cause problems with the DNS system.

I hope I'm not covering ground you're already familiar with here; just pitching in with my thoughts! You may be a webserver expert for all I know :) If there is anything you want me to explain in more detail, let me know. I'm working on setting up an Ubuntu webserver myself, but only for testing websites over my LAN, so I'd be interested to hear how you get on. Good luck with it.

---

### Post by Axrst on 2006-08-14
It's sure that your ISP blocks the specific ports (also 20, 21 for ftp). Try to open another port for your web server (eg. 8080).

OR,

you're behind a NAT (possibly a DSL router) and you have'nt configure your router to pass the requests for the specific ports to your server... (or maybe you're allready done this? - I don't understand well what do you mean, when you say: 

```
I have ports 80, 81 and 20080 open
```

---

### Post by linuxpenguin on 2006-08-15
I can't sympathize with your problem, because my ISP (Comcast) most certainly is not blocking these ports.  However, I do know that a lot of ISPs do this so that you're not hogging up all the bandwidth.

Also, if you're going to run a webserver, might I recommend using a service such as DynDNS?  It's made things so much easier for me to set up my web server.

---

### Post by newtolinuxx on 2006-08-30
I can run a webserver!

My ISP doesn't block any ports.

I was trying to test my webserver by entering my IP (not LAN IP) into firefox.  Due to NAT (I believe) I was getting my router's config screen instead of my webserver so I thought that it wasn't working when in fact it was.  Always get someone else to check it!

I also had some confusion about what my IP actually is, most websites tell me one thing and a few tell me another, in my case the few are right.

Thanks

---

### Post by Kurt` on 2006-08-31
In that case, your router's administration interface listens on port 80, so any incoming requests from behind your router are picked up by the router instead of being forwarded (to the machine port 80 is forwarded to). :p

Behind your router, refer to your webserver using its router-assigned IP (e.g. 192.168.1.102) or hostname, or run apache on a different port number.

Good luck

---

### Post by linuxpenguin on 2006-08-31
> **newtolinuxx said:**
> I also had some confusion about what my IP actually is, most websites tell me one thing and a few tell me another, in my case the few are right.
Most of these websites are probably telling you your router's IP, incorrectly assuming that your PC is directly connected to the Internet.
[QUOTE=Kurt`]Behind your router, refer to your webserver using its router-assigned IP (e.g. 192.168.1.102) or hostname, or run apache on a different port number.[/quote]
I wouldn't recommend running Apache on a different port - most web browsers specifically look at port 80 - if you set it to something else it won't find it unless you specifically tell the web browser what port it needs.

That's fine if this web server is only for you and your family, but not for if you want others to connect to it.

---

### Post by marioXXL on 2007-12-02
I've got kinda the same problem. My Network looks like this:
 [PHP]
                               INTERNET
                                  | 
                                  |
                             (real IP)
         NAT / FIREWALL / PORT FORWARD (web, mail, ftp   all to 10.10.1.1) 
                           (10.10.1.254)
                       _________|__________________
                      |                            |
          LAN (10.10.1.0/24)      SERVER web, mail, ftp (10.10.1.1)
[/PHP]
How can I configure the server and the router in order to access the domains hosted on the SERVER from the LAN? It works from the internet, I've tested with an proxy and also from another location. I've tryed with both SNAT and MASQUERADE.

Any suggestions?

---

### Post by freebeer on 2007-12-02
> **marioXXL said:**
> 
How can I configure the server and the router in order to access the domains hosted on the SERVER from the LAN? It works from the internet, 

The lan machines will access the server if you use a hosts file.  In the hosts file (a text file) you map the ip address of the server to the name that you want.  (The host file is on the client machines.)

```

10.10.1.1 www.mydomain.com

```

So when someone on the lan types "www.mydomain.com" in their browser, the host file is consulted, it now knows the IP address of the server, and the page is loaded.

I think this is what you're asking, anyway.  :)

---

### Post by marioXXL on 2007-12-11
> **freebeer said:**
> The lan machines will access the server if you use a hosts file.  In the hosts file (a text file) you map the ip address of the server to the name that you want.  (The host file is on the client machines.)

```

10.10.1.1 www.mydomain.com

```

So when someone on the lan types "www.mydomain.com" in their browser, the host file is consulted, it now knows the IP address of the server, and the page is loaded.

I think this is what you're asking, anyway.  :)
that is quite a good ideea. it will be alot of work, since i use alot of subdomains, but at least they will work on my machine :)

---

### Post by rsw686 on 2007-12-12
Have somebody outside your LAN test it out. Your router probably doesn't support NAT reflection and if it does you need to set its WebGUI to run on a different port.

---

