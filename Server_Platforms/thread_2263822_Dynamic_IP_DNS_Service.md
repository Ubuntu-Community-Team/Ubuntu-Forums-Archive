---
title: "Dynamic IP DNS Service?"
date: 2015-02-03
forum: Server Platforms
---

### Post by d4m1r on 2015-02-03
Hey all, basically I want to relocate a small server to brothers place because I've got no more space here :)

It only runs a small FTP server, but the problem is he hosts his own servers and now mine all behind a residential cable connection so he does NOT have a static IP. While his IP rarely changes (like once every 2-3 months), I don't want to keep bugging him to give me his current IP and just want to connect to my server via a simple DNS name.

In the past for Windows-based servers, I've installed a GUI client from a free DNS service that would monitor the servers public IP and update the assigned free DNS name to point to whatever the servers current IP was, all automatically. I understand this is all possible under Ubuntu as well using the **DDclient** and the free **DynDNS** service, is that correct?

Does anyone have any better recommendations? Is anyone using the DDclient in combination with DynDNS, and if so, is everything working as expected?

---

### Post by TheFu on 2015-02-03
ddclient is commonly used, but it is easier to just use one of the services supported by most residential routers.  BTW, DynDNS isn't free anymore for recent accounts. Cannot recommend any other free service, sorry.

Any chance I could convince you to [stop using plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")?

---

### Post by gordintoronto on 2015-02-03
I'm happy with DNS Exit.

---

### Post by ian-weisser on 2015-02-03
I use duckdns.org.

---

### Post by d4m1r on 2015-02-04
> **TheFu said:**
> ddclient is commonly used, but it is easier to just use one of the services supported by most residential routers.  BTW, DynDNS isn't free anymore for recent accounts. Cannot recommend any other free service, sorry.

Any chance I could convince you to [stop using plain FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")?

He has a high end (but still consumer grade) Dlink router and has some kind of DNS service built in, but I assume it's then going to apply it at the router level for ALL devices....Unless I could specify for it to apply only to the static IP I configure for my server? Yes, I realize now DynDNS no longer offers free accounts so I am looking elsewhere.....And don't worry, I guess I should have been more specific but it is actually an SFTP server, not plain FTP :)

> **gordintoronto said:**
> I'm happy with DNS Exit.

Are you using it with a version of Ubuntu server and everything is working fine? Do they offer free accounts? I would ofcourse donate to the project but am hesitant to add another monthly subscription service to my list :P

> **ian-weisser said:**
> I use duckdns.org.

Same question for you :)

Thanks for the replies so far guys!

---

### Post by ian-weisser on 2015-02-04
> **d4m1r said:**
> Are you using it with a version of Ubuntu server and everything is working fine? Do they offer free accounts? I would ofcourse donate to the project but am hesitant to add another monthly subscription service to my list 

The flavor of Ubuntu is irrelevant.
If it did not work with Ubuntu, we would not mention them in an Ubuntu forum.
Cost you must verify for yourself anyway.

---

### Post by TheFu on 2015-02-04
> **d4m1r said:**
> He has a high end (but still consumer grade) Dlink router and has some kind of DNS service built in, but I assume it's then going to apply it at the router level for ALL devices....Unless I could specify for it to apply only to the static IP I configure for my server? Yes, I realize now DynDNS no longer offers free accounts so I am looking elsewhere.....And don't worry, I guess I should have been more specific but it is actually an SFTP server, not plain FTP :)

There is only 1 public IP, so the router would tell the dynamic DNS service that and have a name which follows it. It isn't like each system inside gets a public IP - at least not on residential services I know about. Trust me - just use one of the services that is built into the router.  Your PC will need a static IP on the LAN anyway, so the router will know where to forward whatever port you want at the static LAN IP for it.  

Plain FTP is **Nothing** like sftp.  Best to spread the word and **never, ever, ever** confuse those. Always say "sftp" and spread how much more secure it is over plain FTP.

---

### Post by d4m1r on 2015-02-04
> **TheFu said:**
> There is only 1 public IP, so the router would tell the dynamic DNS service that and have a name which follows it. It isn't like each system inside gets a public IP - at least not on residential services I know about. Trust me - just use one of the services that is built into the router.  Your PC will need a static IP on the LAN anyway, so the router will know where to forward whatever port you want at the static LAN IP for it.  

Wow, did I ever have a brain fart....Yes of course, it is a resident cable connection so he only has 1 IP and if I configure it on the router, the Dlink router will update via some Dlink free DNS service (forgot the name) whatever public IP it is feed by the modem. Then, I could just create a virtual server entry to forward the SFTP port to static lan IP X.Y.Z on the router, and voila :)

---

### Post by TheFu on 2015-02-04
We all have those moments when over-thinking happens.  ;)

BTW, would be good to have a plan for when the dlink router fails. What then?  All my dlink equipment here failed before I expected.  Basically, none of the other brands have failed ... well ... except a tplink router that never worked at all.

A ask because I had Mom setup with Lubuntu and dyndns (I'm grandfathered with free management forever). Then her router died. I was 3 states away and couldn't get there for a few months.  Got that fixed, thanks to a windows-centric BiL who lived nearby.  Fine - next year, her PC died. It was old P4, so swapped out for a cheap Core i7 box, literally swapped in the HDD and that was it ... except the udev rules for the NIC were screwed.  Tried to talk my BiL through that and couldn't. He's a point-n-click guy. 

Anyway - having a plan before would be good.

---

### Post by gordintoronto on 2015-02-04
> **d4m1r said:**
> 
Does DNS-Exit work with Ubuntu Server?

Cost?



I don't run Ubuntu Server, but I'm pretty sure it will work.

I have bought multiple domain names from them, and the price was competitive. No other costs.

---

### Post by papibe on 2015-02-04
Hi d4m1r.

I frequently do 'family support' to my brother's machines. I set him up for free with noip.com. He using the ddclient on an Ubuntu Server 12.04.

I believe no-ip have their own Linux client, but so far ddclient have worked just fine.

Hope it helps.
Regards.

---

### Post by TheFu on 2015-02-04
I'm fairly certain that no-ip is one of the main supported DynDNS options in most home routers too.

My company pays no-ip for DNS service - but these are for domains we own.  You don't need to own any domain, just use one of the free subdomains they offer.

---

### Post by d4m1r on 2015-02-07
For anybody else wondering....Many free DNS services available out there that support the ddclient.

I first checked out the built in option in my Dlink router (called DlinkDDNS), but it was actually based on DynDNS which as we know, stopped offering free services and now, Dlink users only get a 6 month trial.

Namecheap does offer free DNS and supports the ddclient BUT I did not purchase my domain from them nor is my domain hosted on their DNS servers so I would have to transfer at least 1 domain to them and I don't want to them. 

Why? Because like many people, I already using CloudFlare for the many positive features they provide. Cloudflare supports the linux ddclient so all I had to do was to creating a subdomain from 1 of my domains hosted with them (free account), A record to my server, install ddclient on my linux server, and then configured it per their instructions, and it connected to their service perfectly fine and now my linux server will constantly/automatically update that A record itself if the external IP changes!

> **papibe said:**
> 
I frequently do 'family support' to my brother's machines. I set him up  for free with noip.com. He using the ddclient on an Ubuntu Server 12.04.

I believe no-ip have their own Linux client, but so far ddclient have worked just fine.


They do have their own client and I actually have used them in the past (because they offer free subdomains, so don't need to host a real domain with them) BUT you have to re-activate the service every 30 days with them and I didn't like that....With Cloudflare, you don't have to do that and I have real domains hosted with them and am already using their services so no need for additional accounts :)

---

