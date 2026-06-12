---
title: "Build my own webserver or pay for hosting?"
date: 2010-08-09
forum: Server Platforms
---

### Post by garfonzo on 2010-08-09
Hi folks,

I am about to start a business where I sell products online. I have been researching web services from various companies such as Yahoo!, GoDaddy, etc. They have the typical $19/month or so for some web hosting space although I'm worried that with my limited budget, a "cheap" hosting service will be limiting.

Therefore, I was wondering if it might be easier to just set up my own web server to run my website. I have my domain purchased and some spare computers with (I think) sufficient specs. Beyond the process of actually getting the server online (I consider that the easy part) I am wondering about some other issues that you may be able to help out with. In general I'm trying to get an overall sense of what it would take to run the website myself from a cost and time requirement perspective.

My questions are varied:

1) I know that it won't be difficult to actually set the server up, but will it be rather consuming to keep it maintained? (Keep in mind I've run a Ubuntu Server for my home lan for years now, and am quite comfortable running a server in general -- I've never maintained a web server though, thus the question)

2) What types of things should I consider when deciding on paying someone to host my website versus hosting myself? 

3) Do I need to be concerned with traffic volume? I only have a few products to sell, but I'm not sure how to gauge how much traffic will require a faster ISP connection. I will likely be adding products soon so the e-store will grow. 

4) Anything else I should consider such as security issues?


I'm just toying with the idea thus far. It just seems that web hosting could become expensive quick as well as limiting and doing it myself might be cheaper and provide more options (keeping a MySQL database, CGI scripting, -- options that are sometimes "extras"). However, I would be OK with paying for someone else to host it if doing it myself would mean endless maintenance or simply detract from running the business. 

Cheers

---

### Post by rubylaser on 2010-08-09
Have you considered what application you plan on using for your store.  Have you thought through using a secure credit card storage vault so that you don't have to worry about VISA / Mastercard PCI compliance?

Setting up a webserver is really pretty simple if you've got these two parts figured out.  I'd suggest hosting it with a webhost if you plan on seeing any significant volume, as they'll almost certainly have better bandwidth and potentially more reliable than you would.

The PCI compliance is a HUGE factor to consider with accepting credit cards online.  The penalties for failure are very steep.

---

### Post by garfonzo on 2010-08-09
Thanks for the quick reply!

> **rubylaser said:**
> Have you considered what application you plan on using for your store. Have you thought through using a secure credit card storage vault so that you don't have to worry about VISA / Mastercard PCI compliance?

We're using PayPal so that we don't have to worry about credit card payments. People can pay with a credit card through PayPal without needing a PayPal account. I think (more research necessary) that PayPal provides "Add to cart" buttons so they can handle the "store" functionality.

> **rubylaser said:**
> I'd suggest hosting it with a webhost if you plan on seeing any significant volume, as they'll almost certainly have better bandwidth and potentially more reliable than you would.

That's something I'm not sure about. What is considered significant volume? 100 visitors per day? 1,000? 10,000? What kind of ISP upload speed is necessary for that?

---

### Post by Falter on 2010-08-09
Setting up a webserver is easy - and it is quite easy too, to have more problems than you probably want with it. Just think about security. If you don't know what you are doing, let professionals do it (a webhost).

---

### Post by garfonzo on 2010-08-09
> **Falter said:**
> Setting up a webserver is easy - and it is quite easy too, to have more problems than you probably want with it. Just think about security. If you don't know what you are doing, let professionals do it (a webhost).

That is my big concern. (1)Security and (2) Possible downtime as a result. 

I worry that if something happens and something takes down my server, how long will it take to get it up again and what does that mean as far as lost revenue. 

Hmmm... perhaps paying someone else is a good idea? 

There's the DIYer in me that is screaming for me to do it myself!

---

### Post by ginge6000 on 2010-08-09
Your upload speed may be restrictive.  If you have the hardware (or use a virtual machine if not) set up a test server with apache and create a test websites with images etc.  I was surprised at how slowly the pictures loaded on my uplink.

---

### Post by FuturePilot on 2010-08-09
The biggest problem will be your connection. I wouldn't recommend hosting a business website on a home connection. Your upload bandwidth is going to be very small so even with light traffic it's going to be slow. Not to mention home connections aren't the most reliable. Either pay for hosting or get a VPS if you want to set everything up yourself.

---

### Post by stlsaint on 2010-08-09
Setting up the webserver is by far your smallest concern! :D
Security is real simple and there are many options if you want to really lock a system down, IPtables, deny/allow.hosts, apache mods, fail2ban, etc. Literally the list is beyond measure!:popcorn:

Now your problem is going to be bandwidth. 100 visitors a day is very small in comparasion of what you can expect to see when your site becomes more popular. You have to consider browsing time as they *shop* around, purchasing multiple items or bulk items, etc.

So in conclusion,
1. Making the webserver would be most cost affordable route.
BUT
2. If you are serious about your site taking off than you must consider bandwidth (unless you plan to upgrade to a T1 connection for business use) you will want to go through hosting with an outside company! Hope i helped!! ;)

---

### Post by garfonzo on 2010-08-09
Thanks for all your input. 

> **ginge6000 said:**
> Your upload speed may be restrictive.  If you have the hardware (or use a virtual machine if not) set up a test server with apache and create a test websites with images etc.  I was surprised at how slowly the pictures loaded on my uplink.

This was always going to be part of my solution. Set up a server on a dedicated business level connection. This would solve two things, (1) Upload speed would be sufficient and (2) the business connection would be physically separate from my home LAN. 

Ok, so what I'm hearing from you folks is that the real kicker here, the bottleneck so to speak, is really just upload bandwidth? If I pay for a dedicated business level connection I should be good to go? 

That doesn't sound too bad. As far as security issues, I think it would be similar to my home LAN server where the sever is behind a router's firewall, and then the server itself is for the most part secure out of the box (Ubuntu server version). I could go a little further with the business server and lock down some potential security holes (IP Tables, etc).

---

### Post by kgatan on 2010-08-13
Go for hosting, it just isnt worth it to do it your self.

Look at it from a business perspective, your supposed to sell products online not host websites. Hosting is only usable if thats the business idee or your setup have huge demands on configuration.

If you like the challenge of your own server setup a site on the side and do all development there instead.

Imagine when the server runs hot and the thing goes down, that can cost you alot more money then the monthly charge. Customers on the web expect alot these days.

Even the cost of setting up a reliable server is more then its worth. Im not talking about performance stuff but the more reliable hardware, backups etc.

---

### Post by garfonzo on 2010-08-13
> **kgatan said:**
> Go for hosting, it just isnt worth it to do it your self.

Look at it from a business perspective, your supposed to sell products online not host websites. Hosting is only usable if thats the business idee or your setup have huge demands on configuration.

If you like the challenge of your own server setup a site on the side and do all development there instead.

Imagine when the server runs hot and the thing goes down, that can cost you alot more money then the monthly charge. Customers on the web expect alot these days.

Even the cost of setting up a reliable server is more then its worth. Im not talking about performance stuff but the more reliable hardware, backups etc.

You have basically summed up my thoughts exactly after people's respond to this thread. I have decided to just pay for hosting, but also to set up my own site for kicks.

---

### Post by fro1269 on 2010-08-14
I personally pay for hosting on my e-commerce sites. I setup a dyndns account and am slowly teaching myself about the ins and outs of LAMP on my home server. The what-if scenario of "What happens when my server breaks" convinced me to outsource any mission-critical web servers.

---

