---
title: "ISP DNS vs domain company's DNS"
date: 2010-01-16
forum: Server Platforms
---

### Post by programming.name on 2010-01-16
[IMG]http://postfiles11.naver.net/20100116_74/s2130286_1263627571742ETKc2_jpg/untitled_s2130286.jpg?type=w3[/IMG]
Hi, there 
 
Please refer to the attachment so that what's going on around my network circumstances.
 
As you can see in the picture, I got DNSs from ISP and Name Servers from a domain company(I don't really know what's the difference between ISP's DNS address and domain company's name servers. Are DNS and name server the same?). Since I haven't grasped the concept of the DNS I just played a 'number guess game' all the way round for a week. What I mean by the number guess game is that in order for people from the world to access my domain, I just thought that some connection between my IP address and the domain name would be needed. Becuase if someone typed my domain address in a browser, then the browser would know the domain is associated with my IP. So I went to the domain company's web page where my domain's name servers can be changed, and tried to change the name server with my ISP's DNS address(219.250.36.130 as the Master DNS and 210.220.163.82 as the Secondary DNS). But it won't change at all. Finally I called the domain company whats going on and they answered me that name server CAN'T be changed with IP address like 219.250.36.130 and its format should be ns.xxxx.yyy.
 
But I don't have ns.xxxx.yyy stuff anymore. What do I do with that? Ah I set the portforward to my desktop computer with ubuntu 9.10 server edtion installed(192.168.0.11).
 
Thanks

---

### Post by ronniestamps on 2010-01-16
DNS = Domain Name Server... the exact same thing as a name server.

Your ISP DNS is provided to you so that human readable domain names can be resolved to the IP address of the servers hosting those websites. ISP DNS are servers that harvest or keep records of domain names to IP address correlation. The DNS for your web server are different in that they tell all other DNS where your website is hosted. They basically report to your ISP DNS as well as everyone else's ISP DNS. Without your DNS for your website, the rest of the world will not know where your website is hosted.

So in short... 

For internet access, use your ISP DNS.
For a website DNS, use your Host's DNS. NS1.xxx.xxx NS2.xxx.xxx and so on.

The reason why you can't plug in an IP address for your website's DNS is that those types of DNS have to be registered as actual DNS that will report to other DNS so that ultimately the entire world will know where your website is hosted.

---

### Post by programming.name on 2010-01-16
Thanks, but I am getting confused. What 's the meaning of 'host'? And if then as long as ISP DNS has my domain company's DNS informatioin that also has info about my domain,  isn't it true that I can simply use a domain company's DNS in order to run the ubuntu server?

---

### Post by lisati on 2010-01-16
> **programming.name said:**
> [IMG]http://postfiles11.naver.net/20100116_74/s2130286_1263627571742ETKc2_jpg/untitled_s2130286.jpg?type=w3[/IMG]
Hi, there 
 <...snip...>
 
------------------------------------------------------------------------------------------------
[http://postfiles11.naver.net/20100116_74/s2130286_1263627571742ETKc2_jpg/untitled_s2130286.jpg?type=w3](http://postfiles11.naver.net/20100116_74/s2130286_1263627571742ETKc2_jpg/untitled_s2130286.jpg?type=w3)
------------------------------------------------------------------------------------------------
As you can see in the picture,
<...snip...>
Referal denied. See attachment.

---

### Post by programming.name on 2010-01-16
Woops, I put the attachment. Sorry about that!

---

### Post by ronniestamps on 2010-01-16
> **programming.name said:**
> Thanks, but I am getting confused. What 's the meaning of 'host'? And if then as long as ISP DNS has my domain company's DNS informatioin that also has info about my domain

ISP DNS = ip <-> domain name resolution of the internet.

Domain company DNS = ip <-> resolution of the domains they host.

Your ISP DNS will only have info on your domain info IF your domain company DNS has that info. Your domain company DNS reports to ISP DNS to tell them about the domains they host. 

> **programming.name said:**
> isn't it true that I can simply use a domain company's DNS in order to run the ubuntu server?

As long as that domain company has records of your server's IP address.

Imagine living in the middle of nowhere without any post office or address. No one in the world will be able to send you mail unless you have an address and a post office knows that address. That post office can then tell other post offices where you live, so stuff addressed to you will reach you. If a post office half way across the world knows you exist, you still won't receive mail because they don't control mail in your area. You need a post office to report to larger post offices that in turn report to larger post offices.

If you are trying to setup your own webserver, then setup your own DNS servers too. Your DNS servers will report your webserver's IP address to ISP DNS servers across the internet.

If you tell me exactly what you are trying to do I will tell you exactly what you need to do. Sorry if this is confusing for you.

---

### Post by alexfish on 2010-01-16
the name has to be resolved as in the = 

try from the terminal if your on named 

route

route  - n

dig "name"

---

### Post by Cheesemill on 2010-01-16
Your getting confused, the company you got your domain from is only a registar, it looks like they don't run DNS services

Even though you have a domain registered you haven't got  a DNS zone set up for it anywhere. The easiest way to do this is with a company such as [ZoneEdit]("http://www.zoneedit.com/") (you can set up a free account).

First you need to set up an account with ZoneEdit and set up a zone for your domain. Then create an A record in that zone that maps [www.yourdomain.com](www.yourdomain.com) to your external IP address.

Then just go onto your domain registars control panel and set the nameservers to the ZoneEdit nameservers, these will be ns1.zoneedit.com and ns2.zonedit.com (or something similar, it's been a while since I used them).

All sorted :)

---

### Post by programming.name on 2010-01-16
> **ronniestamps said:**
> ISP DNS = ip <-> domain name resolution of the internet.

Domain company DNS = ip <-> resolution of the domains they host.

Your ISP DNS will only have info on your domain info IF your domain company DNS has that info. Your domain company DNS reports to ISP DNS to tell them about the domains they host. 



As long as that domain company has records of your server's IP address.

Imagine living in the middle of nowhere without any post office or address. No one in the world will be able to send you mail unless you have an address and a post office knows that address. That post office can then tell other post offices where you live, so stuff addressed to you will reach you. If a post office half way across the world knows you exist, you still won't receive mail because they don't control mail in your area. You need a post office to report to larger post offices that in turn report to larger post offices.

If you are trying to setup your own webserver, then setup your own DNS servers too. Your DNS servers will report your webserver's IP address to ISP DNS servers across the internet.

If you tell me exactly what you are trying to do I will tell you exactly what you need to do. Sorry if this is confusing for you.


Thanks, ronnie. All I want is building a web hosting server on my desktop with ubuntu 9.10 installed for a learning purpose. Firstly I want to have my DNS setting corretly, and I am NOT going to use the static IP(I heard it is possible, althouth I need to chage the setting every single time my external ip chagnes) and if it is possible I want to run DNS services on my own if possible.  Ah,I already worked on portforwaring for the comtuper to be a web hosting server.
Thanks a lot.

---

### Post by programming.name on 2010-01-16
> **Cheesemill said:**
> Your getting confused, the company you got your domain from is only a registar, it looks like they don't run DNS services

Even though you have a domain registered you haven't got  a DNS zone set up for it anywhere. The easiest way to do this is with a company such as [ZoneEdit]("http://www.zoneedit.com/") (you can set up a free account).

First you need to set up an account with ZoneEdit and set up a zone for your domain. Then create an A record in that zone that maps [www.yourdomain.com]("http://www.yourdomain.com") to your external IP address.

Then just go onto your domain registars control panel and set the nameservers to the ZoneEdit nameservers, these will be ns1.zoneedit.com and ns2.zonedit.com (or something similar, it's been a while since I used them).

All sorted :)

Thanks Cheesmill. Since it is a learning purpose I would like to do it myself. Actually I already have one. Thanks again

---

