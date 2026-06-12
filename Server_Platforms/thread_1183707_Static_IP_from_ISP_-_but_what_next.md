---
title: "Static IP from ISP - but what next"
date: 2009-06-10
forum: Server Platforms
---

### Post by philtrim on 2009-06-10
I just wanted some clarification.  My ISP package includes a Static public IP.  I want to host my own website, and perhaps email.  What is my next step? 

Do I have to register a Domain Name i.e. mydomain.???  ?
If I do, do I need to tell the registrar what my Public IP is
in order to get DNS setup?  Or is this something I do myself, and if so, what is the process? I am familiar, somewhat with DynDNS, so could I just go there and setup a HOST record to match my IP with my new domain name?
As you can see, I am a bit confused with my options.

I am using Ubuntu Server 9.04 / and Apache 2

I hope this was clear.

Thanks.

---

### Post by grantemsley on 2009-06-10
Assuming you have already registerd a domain, you have to tell the registar what DNS servers to use for your domain.  You can host them yourself, but I'd strongly recommend using a free service like everydns.net since they have several DNS servers spread out across different networks.

You put everydns.net's DNS server addresses in at your registrar.  Then at everydns, you create the DNS records pointing to your IP address.  For mail, you'd want an MX record, and for a website, an A record.

---

### Post by mbeach on 2009-06-11
I think you have it correct.

You can either 
a - have your own domain name which you purchase from netfirms, godaddy etc, and once you own it you can point your domain name to your ip using the registrar's tools. They are usually quite easy to use and well documented, or:
b - use dyndns using the same method as you would with a dynamic address. I think they have an option to say that the ip address is static.

---

### Post by el.otro on 2009-06-11
If you have experience with dyndns.org you can simply point a hostname to your IP; however, having a static IP doesn't necessarily mean you are permitted to set up a webserver, so you'd have to check your ISP's terms.

Registering a domain name is about $10-20/yr, unexpensive, but you could make it free, the thing is, you'd have to use a subdomain...By the way, google-ing around, I found this site ([http://www.freedomain.co.nr](http://www.freedomain.co.nr)) for URL Redirection, you could point a shorter URL to your long subdomain, and shorten it; I haven't tried the service, so I could not really endorse it, but it's an idea...

Hope I'm being helpful, not redundant...

---

