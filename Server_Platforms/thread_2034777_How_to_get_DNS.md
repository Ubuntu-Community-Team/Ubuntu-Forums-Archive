---
title: "How to get DNS?"
date: 2012-07-29
forum: Server Platforms
---

### Post by hesson on 2012-07-29
OK, so I recently purchased a domain name from Network Solutions that I would like to attach to my Ubuntu web server that I have recently installed. My website has an IP that can be accessed from anywhere in the world (let's say it is 200.200.200.200 for simplicity's sake). Now, I thought I could just tell Network Solutions my server IP and they could automatically configure that, but why are they asking for at least two DNS name servers, and where should I get that from? It doesn't accept IP's only domain names. So where should I get those from? Is it the domain names of the DNS IP's in **/etc/resolv.conf**? If so, I can get the domain names using **traceroute**. Also, after I enter the name server domains, it asks for an IP for each DNS, and it has to be unique too. I only have one IP on my server so what should I input in that case?
Thanks

---

### Post by sandyd on 2012-07-29
Use namecheap DNS servers.
[http://www.namecheap.com/products/freedns.aspx](http://www.namecheap.com/products/freedns.aspx)

---

### Post by BkkBonanza on 2012-07-29
What you're running into is that apparently Network Solutions doesn't provide DNS servers for you for free (or at all). Typical, since they charge so much for names! But most other competitive registrars in the market do provide DNS servers when you register a name.

You can either setup your own DNS servers (not really recommended since this means having at least two redundant servers and IPs) or you can use one of the free ones out there. The free ones usually provide multiple redundant servers so this is the better solution for most small web sites.

As sandyd said, [namecheap]("http://www.namecheap.com/products/freedns.aspx") is good. I've also used sitelutions.com as they offer fast reliable free DNS servers.

You will want to sign up at one of these, create an A record for your domain and possible MX and CNAME records. Then you will want to write down the IPs of their (namecheap or sitelutions etc) DNS servers and go enter those in your registrar records. 

If you are happy with your DNS server over the next year you may want to support them by later transferring your domain to them. After all they're probably cheaper than NS and they at least give you DNS servers to use.

BTW I've used name.com for years and they're lower priced and have an excellent DNS server management console.

---

### Post by hesson on 2012-07-29
Thanks, I just used freedns.com, and set up my domain name with them. It should be working now. I just need to wait for the changes to propagate through the internet.

---

### Post by BkkBonanza on 2012-07-30
Don't wait too long. 
DNS changes nowadays propagate in minutes not hours or days.
:)

---

### Post by hesson on 2012-07-30
It's been over a day now, and I'm still getting that crappy network solutions under construction page at home. Although, it's fine from my computer at work, so I know I set up the DNS properly. I'll give it another day, and then I'll give Network Solutions a call if nothing changes. Either there's some sort of weird caching going on (which is strange cause it's server-side code that's not getting updated) or propagation is slow on my end.

---

### Post by BkkBonanza on 2012-07-30
You should check the DNS caches at OpenDNS here,

[http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/)

If your local DNS isn't getting it then it's not Network Solutions fault. It's your ISP. And many ISP are known to be lousy at handling DNS correctly.

Your best bet is to not use your ISP DNS servers. Change your home settings to use Google DNS (8.8.8.8, 8.8.4.4) or OpenDNS servers (208.67.222.222, 208.67.220.220).

Check your DNS server records TTL values. They should not be too long. I'd suggest 300 seconds if you are expecting to change soon and maybe 1800 seconds if your DNS is stable.

---

### Post by hesson on 2012-07-31
Perfect, that did the trick! I updated resolv.conf, restarted the network and there it was.

---

### Post by hesson on 2012-07-31
Just a question, on my laptop (not the server), resolv.conf had a nameserver of 127.0.0.1. Also, interfaces did not contain any info on dns nameservers. So how does my computer resolve domain names? I mean on my server, I had to configure that, but does it work differently on the home version of Ubuntu?

---

### Post by BkkBonanza on 2012-07-31
Most home users use DHCP which will generally update the local DNS servers according to your router settings. If you have Network Manager running then it takes care of that for you but I'm not sure where it stores the values. I don't use Network Manager myself now but I read that the newer versions have a DHCP option that allows still setting fixed DNS servers locally.

---

