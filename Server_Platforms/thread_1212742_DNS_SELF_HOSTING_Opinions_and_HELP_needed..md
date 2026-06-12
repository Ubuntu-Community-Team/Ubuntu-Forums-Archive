---
title: "DNS SELF HOSTING Opinions and HELP needed."
date: 2009-07-14
forum: Server Platforms
---

### Post by numeroususr on 2009-07-14
First off, I've been doing a lot of homework on this but I'm stuck.

I need to know if it is possible to setup my own nameserver and point my domains to my own server so people on the outside can reach my server.

I have it setup right now so if i type myotherdomain1.com and myotherdomain2.com it interprets the name and forwards localy so the virtual hosting is setup correctly the problem is how do I point myotherdomain1.com and myotherdomain2.com to my server DNS wise or is there a better way?

Here is the setup:

I have windows 7 running vmware server and it is running ubuntu juanty server x64. VM Ubuntu is set to bridged so it has its own IP 192.168.1.5 on my router, I'm forwarding all main ports 80,52,22, etc to this IP on my router. LAMP is installed, bind9 reports to be started.

I have dynamic dns setup for my modem, its IP never changes anyway but the router is linked up to it for updating as well. If you type: [http://numerous.endofinternet.net/](http://numerous.endofinternet.net/)  
thats the link to my server via DYNDNS.org . You can see my LAMP server info, of course it is the equivalent of me typing in 192.168.1.5, 

So far I've setup named based virtual servers for multiple domains
numerous.endofinternet.net points to localhost so I can see the phpinfo() page, outside the server i cannot. 

I also have other domains registered at my old hosting company and I'm trying to point those to a nameserver so they can be forwarded to my server which will serve mutiple domains as a virtual host.

Any help greatly appreciated, I can easily post conf files if someone wants to see. Thanks in advance.

---

### Post by windependence on 2009-07-14
IMHO it's not necessary OR desirable to run your own DNS. You can easily use your registrar's DNS (not your ISP's) servers and your DNS will be reliable and correct, not to mention it probably will propogate much faster.

It's a common myth on this board that you must use your own DNS to run a web server. I run many commercial web sites for customers, and not one of them runs their own DNS. I do it this way for relaiblilty, because to properlly run DNS, you should have at least two and optimally three DNS servers to do it right.

Setting up DNS with your registrar (such as Godaddy) is MUCH easier than trying to configure your own also. Their control panel is almost always a nice GUI and easy to understand. I can't say the same for Bind or some of the other DNS servers.

Good luck!

-Tim

---

### Post by numeroususr on 2009-07-17
Thanks, I had a feeling you would say that. Can't agree more. Trying to get domains transfered to goddady where I can use their DNS. My current Registrar will end up charging me a bundle otherwise.

Thanks again!!

---

### Post by windependence on 2009-07-17
Well there's also some free DNS out there I am told. Also, Godaddy will extend your domain registration if you transfer, and they make transferring very easy and fast as everything is automated. I just did one a few weeks ago. 

There aren't too many registrars that don't do your DNS, who are you with if I may ask? 

If worst comes to worst, I can probably help you with Bind as I have set up a few of those. 

HTH

-Tim

---

### Post by numeroususr on 2009-07-18
My registrar is Aplus.net. I'm pretty sure they offer DNS i just don't like the way they are setup for a lot of reasons. I have a feeling godaddy is cheaper and easier anyway. Even now I am waiting on the DNS transfer after 3 to 4 days, only half domains transfered easy the others are hung up on their end (back and forth emails). Godaddy's system is pretty good as long as you don't use a browser like Opera.

Thanks. Pretty sure by next week will have it runnin.

---

### Post by Thirtysixway on 2009-07-18
> **windependence said:**
> Well there's also some free DNS out there I am told. Also, Godaddy will extend your domain registration if you transfer, and they make transferring very easy and fast as everything is automated. I just did one a few weeks ago. 

There aren't too many registrars that don't do your DNS, who are you with if I may ask? 

If worst comes to worst, I can probably help you with Bind as I have set up a few of those. 

HTH

-Tim

I use GoDaddy, but I point my nameservers to the two that my hosting provider gave me.  If I use GoDaddy's dns service instead, would I just create two ns entries for @, pointing to my hosting's servers to continue using them?

It would make it a lot easier to manage subdomains and things like that, but I'm afraid that I'll mess up my existing setup...

---

### Post by windependence on 2009-07-19
Yup, no need for middle men here, just point your domain directly at your server with your A record, and then create CNAMES and MX records all in GoDaddy's DNS control panel. It's much simpler.

-Tim

---

### Post by numeroususr on 2009-07-24
Question?

I have still yet to get my other two domains transfers (because of APLUS.NET), thankfully I managed to get the other two transferred and linked up and working. I think I had the bind working possibly all along there was an error in the vhosts config that I ended up fixing as there was no change after hooking up the godaddy dns. But it is really easy to config on godaddy and it helped to eliminate any possible errors with the DNS so i could focus on the other probs. Thanks again!!!

---

### Post by dexter1983 on 2009-07-24
Hello ubuntu fans! I have almost the same situation:
I have my own domain: example.ro.
A internet conection with dinamic IP, connected from a  linux router with freedns.net client.
LAN: 10 workstation and my notebook. 
I put my domain to DNS entry on the freedns.net.
ns1,2,3,4.freedns.net are in the nameserevr section to my registar.
I want to make: domain controller from samba, I know how to that.
I want to make my own website, accessed from internal  and outside my LAN
I want to make a mail server, yes I know because dinamic IP , my mails are seem like spam.
My questions:
What is the corect value for hostname of linux server: host.example.ro or host.example.local, where EXAMPLE is my local domain configured in samba.
If I don't use my own DNS server, how do I setup mail server?
I am a bit confuse because ,because till now I use windows 2003 sbs.

---

### Post by grantemsley on 2009-07-24
> **numeroususr said:**
> Thanks, I had a feeling you would say that. Can't agree more. Trying to get domains transfered to goddady where I can use their DNS. My current Registrar will end up charging me a bundle otherwise.

Thanks again!!

everydns.com will host your DNS for free, for any domain.  That's what I use.

Actually, I use a combination of services since I'm hosting stuff on my home DSL with a dynamic IP:

dyndns.org --> has a hostname something.dyndns.org that always gets updated to my current IP.
everydns.com --> hosts my real domain.  Most of the entries are CNAME records that point to something.dyndns.org

I do this because although everydns.net lets you have dynamicly updated records, they don't update as fast as dyndns.

---

