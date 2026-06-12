---
title: "Domain Name Questions"
date: 2007-05-16
forum: Server Platforms
---

### Post by blmartin777 on 2007-05-16
I registered a domain name. I set up from the company to forward it to my apache server? I am new at this so. My question is I use dyndns so I set the domain to forward to (example) name.dyndns.org. Lets say the domain name I bought is [www.example.com](www.example.com). Well when I type in [www.example.com](www.example.com) it goes to the right web page but the the address bar shows name.dyndns.org/website/index.html. Is that something that I need to change in the website or do I need to set up virtual hosts in apache for this. I still want it to show [www.example.com/index.html](www.example.com/index.html).

Thanks

---

### Post by Frosty Cold Drink on 2007-05-16
> **blmartin777 said:**
> I registered a domain name. I set up from the company to forward it to my apache server? I am new at this so. My question is I use dyndns so I set the domain to forward to (example) name.dyndns.org. Lets say the domain name I bought is [www.example.com](www.example.com). Well when I type in [www.example.com](www.example.com) it goes to the right web page but the the address bar shows name.dyndns.org/website/index.html. Is that something that I need to change in the website or do I need to set up virtual hosts in apache for this. I still want it to show [www.example.com/index.html](www.example.com/index.html).

Thanks

You don't want to forward. Forwarding is bad. (CNAMEs are bad too, but eh.)

So, first you need to have the DNS hosted. GoDaddy lets you do it. I don't know who else will. Then change the DNS records for "example.com" and "www.example.com" to be CNAME records instead of A records, and point them to yourname.dyndns.org.

This causes a second DNS lookup when trying to access the web site (as does the forwarding) but it will still look like "example.com" in the address bar.

---

### Post by strixy on 2007-05-16
also check out zoneedit.com

Godaddy will allow you to hand the DNS over to zoneedit completely. You can use their dynamic ip updating tools if you need to. That way you can control more than just the URL.

But that's a whole couple of weeks or researching and learning for someone whose never done it before. (which, if you're up for it I highly recommend spending the time to learn it)

If you just want to get it done easy cheesy, no muss no fuss, use what you've got going already, but enable URL masking. That will seriously hamper your ability to do certain things (like subdomains, email, etc) but it works for simple things like blogs, galleries, etc.. Go with what works.

---

### Post by Frosty Cold Drink on 2007-05-16
> **strixy said:**
> also check out zoneedit.com

Godaddy will allow you to hand the DNS over to zoneedit completely. You can use their dynamic ip updating tools if you need to. That way you can control more than just the URL.

Side note: I forgot about that, and dyndns.org will let you update reords directly for your domain as well. The down side is that you have to pay :)

Using the cheap CNAME approach is a way to get for-pay type services with the free account.

---

### Post by blmartin777 on 2007-05-17
Can't I set up my own dns server? so I can just point [www.example.com](www.example.com) that I bought from go daddy to my server?

---

### Post by Frosty Cold Drink on 2007-05-17
> **blmartin777 said:**
> Can't I set up my own dns server? so I can just point [www.example.com](www.example.com) that I bought from go daddy to my server?

You can set up your own DNS server BUT
 - There are prerequisites your ISP needs to handle
 - You'll need to use a static IP address for the DNS server

---

### Post by blmartin777 on 2007-05-17
Just so I make sure I have this right. Say I am hosting 3 web sites ([www.example.com](www.example.com), [www.site.com](www.site.com), and [www.the.com](www.the.com)). That is why I set up virtual hosts? So when someone types [www.site.com](www.site.com) the vitual host conf file I set tells it that the doc root is /file/file/site. Is this right? Or am I misunderstanding something. I did set up a DNS Server but since I have Dynamic DNS that will do me no good so I can just turn it off, right?

Thanks for all the help.

---

### Post by Frosty Cold Drink on 2007-05-17
> **blmartin777 said:**
> Just so I make sure I have this right. Say I am hosting 3 web sites ([www.example.com](www.example.com), [www.site.com](www.site.com), and [www.the.com](www.the.com)). That is why I set up virtual hosts? So when someone types [www.site.com](www.site.com) the vitual host conf file I set tells it that the doc root is /file/file/site. Is this right? Or am I misunderstanding something. I did set up a DNS Server but since I have Dynamic DNS that will do me no good so I can just turn it off, right?

Thanks for all the help.

You are right.

---

