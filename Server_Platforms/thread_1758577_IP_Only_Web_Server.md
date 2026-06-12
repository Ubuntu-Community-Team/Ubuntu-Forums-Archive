---
title: "IP Only Web Server"
date: 2011-05-14
forum: Server Platforms
---

### Post by coljohnhannibalsmith on 2011-05-14
Hello,

I'm wondering if it's possible to operate a Web Server 'without' registering a domain name, [COLOR=Blue]***using an IP address alone.***[/COLOR]

**Explanation:**

I currently have Apache & Tomcat running on one of my workstations.  I am currently using these servers as development sandboxes; and I have P2P Search Engine 'YaCy' running under Apache, which is accessible from the outside to the entire P2P network.

Since my Apache server is accessible from the outside, I was thinking that I might setup one of my other workstations as a server with just my 'external' IP address & port number as a way of reaching my site, i.e.** http:// 255.183.47.201:8090/.**  I can't see any reason why this wouldn't be possible.  I seem to remember several of my former companies doing this on their corporate Intranets.  Also, I wouldn't be locked into registering a domain name every year; and I wouldn't have to worry about any content restrictions.   If my intended audience knows where to find me; I can't see any reason why this wouldn't work. [COLOR=Blue]*** And, I don't see why my site couldn't be indexed by search-engines.***[/COLOR]  The only caveat I can think of is making sure I have enough bandwidth from my ISP to support the anticipated traffic.

If this will work, I assume I can setup a regular website, an online store, podcast, or provide any other type of tradional web-service this way.

[IMG]http://i.technet.microsoft.com/dynimg/IC85187.jpg[/IMG]

---

### Post by Ryan Dwyer on 2011-05-14
Sure, it's possible. But if you're concerned about search engine results and your audience knowing the IP, what happens if you get a different IP address (by moving house or ISPs)? The search engine results would all be dead links, and you'd have to contact your audience to tell them the new IP.

You're probably better off getting a domain name. You could even use a free service such as DynDNS.

---

### Post by crispy_420 on 2011-05-15
Your solution of people connecting is possible but forget about new/unknown visitors. Even if you get found (very unlikely) that port number may be an issue. 

Like mentioned earlier, get a free dynamic dns service. There are many options but check you router for its options (Netgear likes DynDNS) and choose their vendor.

If you have that odd port number for a reason (ISP blocks port 80/443) some of these dynamic dns services offer a service of converting port 80 to one that the ISP may not block.

---

### Post by coljohnhannibalsmith on 2011-05-15
> **Ryan Dwyer said:**
> Sure, it's possible. But if you're concerned about search engine results and your audience knowing the IP, what happens if you get a different IP address (by moving house or ISPs)? The search engine results would all be dead links, and you'd have to contact your audience to tell them the new IP.

You're probably better off getting a domain name. You could even use a free service such as DynDNS.

Good Point!!!

[COLOR=Blue]***BTW, DynDNS Rocks!!!  I never even considered this.  Thank you...***[/COLOR]

[http://www.dyndns.com/](http://www.dyndns.com/)

[Dynamic DNS service]("http://www.dyndns.com/services/dns/dyndns/") allows you to point a hostname to a dynamic or static IP address or URL.
 
[LIST]
[*]Host your own website at home for free!
[*]Connect to your workstation, server, DVR, webcam from anywhere.
[/LIST]
    
**Keeping Connected with DNS**

 As the Internet continues to move further away from the "television"  model &#8212; many viewers, few channels &#8212; more people want to produce their  own content, from blogs to streaming radio stations to game servers to  self-hosted websites. Hosting a server used to require a great deal of  technical knowledge and a business-class Internet connection; today,  anyone can install an entire webserver with a suite of powerful  utilities in mere minutes with a package like [XAMPP]("http://www.dyndns.com/support/kb/xampp_apache_quick_guide.html"); and residential Internet connections are more than enough to host any manner of content.

 Recognizing this growing need for creative freedom, DynDNS.com exists to help you make your message heard. By using our [Dynamic DNS Free]("http://www.dyndns.com/services/dns/dyndns/") service or a [domain registration]("http://www.dyndns.com/services/domains/") with our premier [Custom DNS]("http://www.dyndns.com/services/dns/custom/")  service, DynDNS.com provides an easy way for visitors to reach your  content hosted at home or the office. This gives you the opportunity to become a self-reliant author,  affording you complete control to offer whatever content you wish to the  world at large.

 DynDNS.com isn't just for home use. We also cater to growing businesses with our [SendLabs]("http://www.dyndns.com/services/sendlabs/") suite and [SSL Certificates]("http://www.dyndns.com/services/sslcert/"). Whatever your needs, DynDNS.com aims to provide a stable, reliable and highly customizable foundation for your business.

[IMG]http://www.ernan.net/images/pirate-radio.jpg[/IMG]

I am somewhat concerned about censorship, DNS Blocking, and DDOS attacks.  Perhaps I can use a service like DynDNS and publish [COLOR=Blue]***'both'***[/COLOR] the IP ***[COLOR=Blue]and[/COLOR]*** the DNS???

---

### Post by coljohnhannibalsmith on 2011-05-15
> **crispy_420 said:**
> Like mentioned earlier, get a free dynamic dns service. There are many options but check your router for its options (Netgear likes DynDNS) and choose their vendor.

If you have that odd port number for a reason (ISP blocks port 80/443) some of these dynamic dns services offer a service of converting port 80 to one that the ISP may not block.

[COLOR=Blue]***Good Point.  Thank you!!!***[/COLOR]

---

### Post by coljohnhannibalsmith on 2011-05-17
[COLOR=Blue]***It appears that this problem is now solved!!!***[/COLOR]

[IMG]http://tshirtgroove.com/wp-content/uploads/2008/10/problem-solved-tshirt.jpg[/IMG]

---

