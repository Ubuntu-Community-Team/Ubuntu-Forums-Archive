---
title: "HTTP server on other than port 80"
date: 2013-10-08
forum: Server Platforms
---

### Post by rebeltaz on 2013-10-08
I am not sure who to ask this question, so if this is not the right place (or even the right forum), if you could at least point me in the right direction I would appreciate it.

For 5+ years, I have ran a server for my web site. My IP is AT&T and the router/modem I have used was the Netopia Motorola. This was no problem because I simply changed the port that the modem listened to to 8080. Due to ONGOING issues with dropouts and speed reductions, I am going to have to switch to a Netgear modem. Unfortunately, none of the modems supplied by AT&T allow you to change the port on which the modem listens. That means that the modem will be answering on port 80. 

I'll admit that there is quite a bit I don't know about servers, so here is my question. Using this new modem, how do I get the Apache HTTP server to process web requests correctly without having to change anything different in my web address?

Thank you in advance.

---

### Post by TheFu on 2013-10-08
Huh?

3 questions.

1) What URL do you want the world to access your site using - please include the port.
2) What port do you have apaching listening on? [https://httpd.apache.org/docs/2.2/bind.html](https://httpd.apache.org/docs/2.2/bind.html)
3) Are you saying that the new router doesn't support the most basic of capabilities called port translation? Seems odd if that is true.

I take it this is an all-in-1 DSL-modem+router?  BTW, you could spend $20 and get a dedicated router that will do port translation - it will not have a DSL modem, however.

---

### Post by rebeltaz on 2013-10-08
1) as in my signature: [www.RobotsAndComputers.com](www.RobotsAndComputers.com) - standard port 80 so that it does not have to be specified
2) there are no additional Listen commands so I assume 80 is the only port it listens on
3) port translation? not sure. I am told that I cannot change the port on which the modem listens. 

It is an all-in-1 DSL-modem-router. 

Maybe I don't understand the problem here. 

If the modem listens on port 80, would that not interfere with a web site where the apacher server also listens on port 80?

While I know a quite about about computers, I readily admit that I only know a passing amount of knowledge about networking.

---

### Post by TheFu on 2013-10-09
We've all been where you are.  I was programming computers long before I understood networking.

The modem has at least 2 interfaces - 1 on the WAN and 1 (or more) on the LAN side.  The modem itself shouldn't listen at all on the WAN side using IP by default.  All connections from there, especially if you "open a port" should be passed thru to the static IP on the LAN you specify. Port 80 is fine externally.

If your management connection to the modem is on port 80, that is on the LAN side (not WAN) and it really should be on port 443 to be encrypted. Router security is a big deal - please secure it.

If you'd like to learn more about IP networking ... there's a podcast series that teaches it (great when driving into work daily) - "Security Now" - around episode 25 he starts the "networking" stuff.  [Found it.]("https://www.grc.com/sn/sn-025.htm") Don't worry that it is old. IPv4 still works the same as it has the last 40 yrs.

---

### Post by rebeltaz on 2013-10-09
I will listen to that. Thank you. Real quick question, though, if I may.

I forwarded WAN port 80 to my server. It seems like that works fine from outside, but if I try to access my server, using the link in my signature, from WITHIN my local network, it doesn't respond. That's not a question is it? I guess the question is why? Thank you again.

---

### Post by TheFu on 2013-10-09
a) you don't have to listen, you can read the "show transcript" if that's easier/faster.

b) Why - there is probably a difference in how DNS names are resolved inside your LAN and outside on the internet.  I hope there is.

---

### Post by rebeltaz on 2013-10-09
> **TheFu said:**
> 
If your management connection to the modem is on port 80, that is on the LAN side (not WAN) and it really should be on port 443 to be encrypted. Router security is a big deal - please secure it.

BTW - that is/was my main issue. With this modem (and the configuration address is on port 80), I cannot change that port. At least not that I can tell. It's a NetGear VersaLink Model 	B90-755025-15

---

### Post by TheFu on 2013-10-09
I know that network people prefer netgear over the other opens, but I've never been anything but disappointed with the lack of common features in the equipment I've touched from that company.

It is what it is.

Also, your broadband provider may insist on certain firmware configs from the vendor so they can limit the stupid-user-support-calls. If you aren't buying the equipment yourself (and sometimes even if you do), the network provider can do whatever they choose.  Back in the old days when I was on a residential cable modem plan, I owned the modem, but Comcast could remotely control it even without my management password. I freaked a little over this.  I can only assume that the DOCSIS standard requires a bad door for network providers to use ... it is simple enough via tftp to set new firmware with a different remote admin password on a management-only WAN connection ... that you and I and anyone on the internet cannot access.  

Networking can get pretty complicated.

---

### Post by SeijiSensei on 2013-10-09
> **rebeltaz said:**
> I forwarded WAN port 80 to my server. It seems like that works fine from outside, but if I try to access my server, using the link in my signature, from WITHIN my local network, it doesn't respond. That's not a question is it? I guess the question is why? Thank you again.

As TheFu suggests, it is probably a DNS issue.  Here's one way to test.  One one of the local machines add an entry to its [hosts file]("http://en.wikipedia.org/wiki/Hosts_%28file%29#Location_in_the_file_system") that links the server's local address to your domain name.  If the server has address 192.168.100.50, you'd add an entry to the hosts file like this:

```
192.168.100.50     www.robotsandcomputers.com
```

If that resolves the problem, you'll either need to add an equivalent entry in every machine's hosts file, or set up an internal DNS server.

Oftentimes routers, especially ones designed for residential use, have a problem with traffic from internal hosts that is intended for another internal host but addressed with the router's external address. For example, suppose the router's public IP address was 10.10.10.10, and its port 80 was forwarded back to 192.168.100.50:80.  From the internal network, you should be able to connect to the latter address, but connections to 10.10.10.10 may fail.

(I just worked with a client who was switching to a new ISP, and that ISP provided a router that had this exact problem.  After we tore our hair out for a while, we changed the target addresses in the organization's local DNS server to point to the internal addresses, and it all worked as expected.)

---

### Post by rebeltaz on 2013-10-09
Adding that line to the hosts file did work, so that's good. Thank you both. (How do I do that on a Windows machine? I have four Linux systems and one Windows. I know... but that one is the girlfriends, so...)

However.... Now I have another problem. Even though DHCP is on and supposedly working, nothing that I haven't manually configured with an IP address/gateway IP/DNS server(s) works. I can maually configure the computers, but for devices like the Roku, that isn't possible. 

I don't suppose you guys have a suggestion for a decent DSL modem, do you?

Thanks again...

---

### Post by Doug S on 2013-10-10
> **rebeltaz said:**
> How do I do that on a Windows machine?The same way. The link Seiji gave also tells you where to find the hosts file on a windows computer.

---

### Post by rebeltaz on 2013-10-10
> **Doug S said:**
> The same way. The link Seiji gave also tells you where to find the hosts file on a windows computer.

d'oh! I didn't even notice that that was a link! Thanks.

---

