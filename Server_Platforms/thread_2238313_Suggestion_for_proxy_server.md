---
title: "Suggestion for proxy server"
date: 2014-08-07
forum: Server Platforms
---

### Post by Teku_Ram on 2014-08-07
Hi,

I have a new IT admin job at a school. My management wants me setup a proxy server so that we can filter the unwanted internet traffic (i.e. porn, torrent etc) and also they want to block social networking sites. Now i have configured a squid on ubuntu server and is able to block porn sites and doing a cache server for internet data traffic. I am still struggling to do the following:- 

1. Block out torrents (both downloads and website)
2. Blocking out HTTPS/SSL social network sites. I have tried doing this with setting squid self certifying certificate man-in-middle method but in that case i have to add certificate to all the users. I have around 1000 + users with multiple devices. So it is practically impossible to install certificate at each one of them. 
3. I know students are using anonymous public proxy applications to bypass the traffic, unable to find any solution for that also. 

I request you all to kindly suggest me what the configuration or byways to do so.

- Tek

---

### Post by TheFu on 2014-08-07
I'd use pfsense to block all that traffic - including any HTTPS. 

Is there any valid reason for students to have HTTPS for any reason?  IF there is, I'd talk to the administration about having a signed internet use agreement for anyone who needs HTTPS access, then force the install of a CERT so that all traffic can be monitored.  I'd also force individual logins - to there is a userid connected to the access.  Of course, the people with extra access would need to use a different installation of squid.  Virtualization will handle that easily.

I've never actually performed this myself - besides the pfsense stuff. pfSense has built-in traffic blocks based on the type. Where I worked, we deployed [BlueCoat]("https://www.bluecoat.com/products/packetshaper") solutions for this stuff. I don't think it was cheap.

---

### Post by SeijiSensei on 2014-08-07
I use a rule on gateways that prohibits traffic from "high" ports (>1023) on client machines being able to communicate with high ports on remotes.  This blocks a lot of unwanted stuff like torrents.

```
iptables -A FORWARD -p tcp -i eth1 --sport 1024:65535 --dport 1024:65535 -j REJECT
iptables -A FORWARD -p udp -i eth1 --sport 1024:65535 --dport 1024:65535 -j REJECT
```

These rules would block all high port to high port traffic from machines connected to eth1, the internally-pointing interface on the gateway. They won't block users from connecting to remote servers on standard ports like 80 or 443.

I can't see ruling out HTTPS connections entirely.  What about students who use online banking?  Who want to connect to health-care providers?  Or do any of a number of perfectly legitimate activities that require SSL encryption?

---

### Post by TheFu on 2014-08-07
> **SeijiSensei said:**
> I can't see ruling out HTTPS connections entirely.  What about students who use online banking?  Who want to connect to health-care providers?  Or do any of a number of perfectly legitimate activities that require SSL encryption?

I'd assumed this was high school based on the size and that a desktop person was put in charge of servers. Students don't have any rights - certainly not to manage their health care or access any financial accounts from a school network. If it is that important, they will use a data plan on their cell phone.

OTOH, if this is a college or university - then you probably need professional help and really NEED pfsense.

---

### Post by Teku_Ram on 2014-08-07
> **TheFu said:**
> I'd assumed this was high school based on the size and that a desktop person was put in charge of servers. Students don't have any rights - certainly not to manage their health care or access any financial accounts from a school network. If it is that important, they will use a data plan on their cell phone.

OTOH, if this is a college or university - then you probably need professional help and really NEED pfsense.

> **SeijiSensei said:**
> I use a rule on gateways that prohibits traffic from "high" ports (>1023) on client machines being able to communicate with high ports on remotes. This blocks a lot of unwanted stuff like torrents.

```
iptables -A FORWARD -p tcp -i eth1 --sport 1024:65535 --dport 1024:65535 -j REJECT
iptables -A FORWARD -p udp -i eth1 --sport 1024:65535 --dport 1024:65535 -j REJECT
```

These rules would block all high port to high port traffic from machines connected to eth1, the internally-pointing interface on the gateway. They won't block users from connecting to remote servers on standard ports like 80 or 443.

I can't see ruling out HTTPS connections entirely. What about students who use online banking? Who want to connect to health-care providers? Or do any of a number of perfectly legitimate activities that require SSL encryption?

Yeah Iptables can do the job if i block everything. But i might accidentally bring down some useful traffic two. I.e. traffic to SQL/Oracle servers... (i am just assuming). So black out will not work. 

How about this, can i pretend to be  a legitimate CA certificate for x.509 cert from legitimate authority and somehow use that so that Man in middle proxy automatically gets accepted. i can do this by route all the IP's to my proxy for CA authorization. This way I can filter out everything I need to ... as in my test environment, i am able to figure out these things using squid. AFIK, the browser reaches out to CA servers list provided by the OS to findout if the provider is genuine or not. By installing the certificate, i basicly add myself in that list. 

I know ethically, it is not correct and would be termed as spoofing but in my network where I know no financial transactions are involved, i a can afford to do so.

---

### Post by SeijiSensei on 2014-08-07
> **Teku_Ram said:**
> Yeah Iptables can do the job if i block everything. But i might accidentally bring down some useful traffic two. I.e. traffic to SQL/Oracle servers... (i am just assuming). So black out will not work.

Why would students be connecting to SQL servers?  In particular why would they be connecting to SQL servers *outside your network?* It sounds like there's more to this problem than you have told us so far.

If there are specific services you need to enable, just add additional rules for those services ahead of any blanket denial rules like the ones I gave above.

I don't think any solution that requires installing something, even a certificate, on all the devices that might connect to the Internet is a viable one.  We've considered using SSLBump at one of my client's sites, but all their machines are managed with Active Directory so the admin can push the proxy's certificate to all the clients' browsers (IE, at least; don't know about others).  But you're likely working with a diversity of clients including things like smartphones over wifi.  

And, no, I don't think spoofing a legitimate CA is a viable option either.  You might be able to purchase a CA certificate from a known provider like Verisign that would be seen as authentic by browsers, but I've never done anything like that.

One option is to use transparent proxying to push all HTTP requests through Squid then adding authentication to the proxy.  Students would have to login whenever they opened a browser.  If you authenticate centrally now with something like LDAP, Squid could use the same authentication method.

---

### Post by Teku_Ram on 2014-08-07
> **SeijiSensei said:**
> Why would students be connecting to SQL servers?  In particular why would they be connecting to SQL servers *outside your network?* It sounds like there's more to this problem than you have told us so far.

If there are specific services you need to enable, just add additional rules for those services ahead of any blanket denial rules like the ones I gave above.

Yes mate, students do access sql and other servers on regular basis. See our school is a residential school run by non profit org funded by people. So we have very less funds for the hardware and servers etc. At times, we get help from various institutions who lend us servers remotely or individuals who have spare capacity where students can login and learn/practice. 

The whole purpose of this exercise to preserve the valuable  bandwidth we have. With all these measures, I would try to save bandwidth which will keep the budgets in range. 

hopefully it would explain my situation.

Well i have done some testing with squid+squidgarud and that worked upto some level. Atleast porn is blocked AFIK. Also, for HTTPS, I have tested DNS serves for help. See what I am doing is, if anyone asks for https, i have written a script which tells squid that the dns reply is 127.0.0.1. So nothing comes up. But i dont think its a very efficient solution. What say mates?

---

### Post by TheFu on 2014-08-07
I'd turn up the firewall logging to determine the things you can't touch and start blocking huge blocks like SeijiSensei suggests, then add specific filters for specific needs only.  It will get complex, so invest in a good iptables book and start learning.  I've seen home routers that are able to block packets by protocol - pfsense does this too - don't know how effective they really are.

If you could spoof a CA and get away with it, I would be impressed.  To my knowledge, only governments with NSA-level crypto have been able to do that without it being noticed - fewer than 5 countries in the world can do it, I'd guess.  Of course, of you can get your CA installed on all those devices, then generate certs on the fly, as needed, your server could be the man-in-the-middle.  Watch out - there are likely legal limits on doing this, so be careful.

---

### Post by SeijiSensei on 2014-08-07
> **Teku_Ram said:**
> Yes mate, students do access sql and other servers on regular basis. See our school is a residential school run by non profit org funded by people. So we have very less funds for the hardware and servers etc. At times, we get help from various institutions who lend us servers remotely or individuals who have spare capacity where students can login and learn/practice. 

So write rules that exempt connections to your partners and block everyone else.

---

