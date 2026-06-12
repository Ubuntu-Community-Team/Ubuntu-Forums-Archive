---
title: "Proxy server questions"
date: 2010-06-15
forum: Server Platforms
---

### Post by garfonzo on 2010-06-15
Hey all,

I am wanting to monitor all websites visited from all computers within my LAN. After a bit of searching, I am thinking that setting up a Proxy Server with Squid is the way to go. 

However, I'm not sure about how (physically) a proxy server is to be set up. My understanding is that when a computer on the LAN requests a website (ie: types in [www.google.com](www.google.com) or whatever) this request is sent to the Proxy server which then  requests the site from google itself. So the proxy server is the in between computer between the LAN computers and the actual internet websites. As a result, the Squid machine can log all websites visited.

Now, if the above is incorrect, please do correct me. 

Assuming that my understanding is correct, I'm not sure how the actual, physical, setup should look like. I have two ideas as follows:

1) Internet --> ISP modem --> Proxy Server --> router ===>>> LAN (multiple computers)

2) Internet --> ISP modem --> router ===>>> LAN with Proxy server

So with setup 1, the proxy server really is (physically) in between the LAN and the internet. This setup concerns me because now the Proxy server itself is not behind the router's firewall.

With option two, even though the Proxy is behind the router, I would assume that all LAN computers would be setup to make their web requests to the proxy server instead of the router.

I'm new to this proxy server thing so I'm trying to get a grasp of it before setting anything up. 

I have lots of questions regarding the setup, but I suppose the first few are:
1) Which of the two setups I described above are accurate?
2) Would the proxy server need two NICs?
3) If all traffic is flowing through the Proxy Server and my connection speed provided by the ISP is 15 Mbs, having 100Mbs ethernet cards will not effect internet speeds on the LAN right because the Proxy's NICs are able to handle up to 100Mbs? (I have lots of old hardware and don't want to shell out for a couple of new Gb NICs)


Thanks

---

### Post by HermanAB on 2010-06-16
Howdy, you can do the proxy server, router, firewall thing on a single machine.

---

### Post by sikander3786 on 2010-06-16
> **garfonzo said:**
> Hey all,

I am wanting to monitor all websites visited from all computers within my LAN. After a bit of searching, I am thinking that setting up a Proxy Server with Squid is the way to go. 

However, I'm not sure about how (physically) a proxy server is to be set up. My understanding is that when a computer on the LAN requests a website (ie: types in [www.google.com](www.google.com) or whatever) this request is sent to the Proxy server which then  requests the site from google itself. So the proxy server is the in between computer between the LAN computers and the actual internet websites. As a result, the Squid machine can log all websites visited.

Now, if the above is incorrect, please do correct me. 

Assuming that my understanding is correct, I'm not sure how the actual, physical, setup should look like. I have two ideas as follows:

1) Internet --> ISP modem --> Proxy Server --> router ===>>> LAN (multiple computers)

2) Internet --> ISP modem --> router ===>>> LAN with Proxy server

So with setup 1, the proxy server really is (physically) in between the LAN and the internet. This setup concerns me because now the Proxy server itself is not behind the router's firewall.

With option two, even though the Proxy is behind the router, I would assume that all LAN computers would be setup to make their web requests to the proxy server instead of the router.

I'm new to this proxy server thing so I'm trying to get a grasp of it before setting anything up. 

I have lots of questions regarding the setup, but I suppose the first few are:
1) Which of the two setups I described above are accurate?
2) Would the proxy server need two NICs?
3) If all traffic is flowing through the Proxy Server and my connection speed provided by the ISP is 15 Mbs, having 100Mbs ethernet cards will not effect internet speeds on the LAN right because the Proxy's NICs are able to handle up to 100Mbs? (I have lots of old hardware and don't want to shell out for a couple of new Gb NICs)


Thanks


Hi.

Install 2 NIC's on the proxy server machine so that...

Internet ---> ISP Router ---> Eth0
Proxy Server ---> Eth1 ---> LAN Computers

For getting the proxy server running physically on the same interface and subnet will be something complicated to achieve which will need a firm grip on the firewall thing.

So the easiest way I thought is mentioned above.

The LAN PCs will not be physically connected to the ISP's router and therefore will be easily configured to direct all the traffic to the proxy server.

Ask if any doubts.

Regards.

---

### Post by garfonzo on 2010-06-16
> **sikander3786 said:**
> Hi.

Install 2 NIC's on the proxy server machine so that...

Internet ---> ISP Router ---> Eth0
Proxy Server ---> Eth1 ---> LAN Computers

For getting the proxy server running physically on the same interface and subnet will be something complicated to achieve which will need a firm grip on the firewall thing.

So the easiest way I thought is mentioned above.

The LAN PCs will not be physically connected to the ISP's router and therefore will be easily configured to direct all the traffic to the proxy server.

Ask if any doubts.

Regards.


Hang on, I'm a bit confused when you say "ISP router". I have an ISP modem and a DLink router. Two separate pieces of hardware. I'm assuming you meant the following:

Internet --> ISP **modem** --> eth0//Proxy Server\\eth1 --> DLink Router ===>>> LAN

If so, doesn't this mean the Proxy Server must now have its own firewall to protect it from internet intrusion? My understanding was that the DLink router with the built in firewall protected the LAN from outside attack. Seems to me that placing the Proxy Server on the other side of the router opens it up to attack. 

From what I've been reading on the net, most "Transparent" proxies also have their own firewalls to protect from such attacks (using iptables I believe). 

Am I on the right track so far?

If I do need a separate firewall on the Proxy Server via iptables or something, how concerned should I be regarding possible attack on my Proxy Server? Is it relatively straight forward to set up iptables to be secure?

thanks

---

### Post by The Real Dave on 2010-06-16
Your modem doesn't offer any Firewall at all? I'm guessing it's just a modem, as opposed to being a modem and router mix? 

If the router between the proxy and the internet doesn't have a Firewall,  your server will need one AFIK. How is best to do that, I really don't know. 

As for monitoring website visited using Squid, I'd advise using Squid3 and the Squint monitoring script. It generates a nice web accessable list using the Squid access reports, shows sites visited, number of pages, download size, and access times. You can get Squint on the Squid webpage.

If your not going to cache any of the web traffic, any machine will probably do, something with 64MB of ram will be fine, anything that will run Ubuntu server. If your going to cache the traffic, you'll need something more powerful. Squid recommends 32MB per GB of cache, and it's size will depend on your web bandwidth. But still, my 1.7Ghz Pentium IV with 384MB RAM easily handles the 7.5GB cache, as part of a home server

Being honest, it's much easier IMO to setup the router behind the proxy server, tunnelling everything through, rather than sticking the proxy server on the LAN and diverting things. But you will need a Firewall AFIK. 

Your Squid ACLs will be important too, to prevent anyone from the outside accessing your proxy server.

---

