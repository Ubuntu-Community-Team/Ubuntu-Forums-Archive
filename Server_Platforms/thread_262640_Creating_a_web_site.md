---
title: "Creating a web site"
date: 2006-09-22
forum: Server Platforms
---

### Post by elpuerco on 2006-09-22
Not sure if this is the right place to post, but here goes...

I own the domain name [www.elpuerco.co.uk](www.elpuerco.co.uk) and previously rented a hosting package to runmy web site.

I no longer do this due to cost.

Question is how does one go about creating your own web site and linking it to the domain name above.

Is this something that would require a lot of hardware and a lot of learning to achieve?

Thx

---

### Post by stalefries on 2006-09-22
You will definitely need to learn a lot, but as long as you have a basic computer that can connect to the internet, you should be fine hardware-wise. I would suggest searching Google for tutorials to setup a Linux-based server.

---

### Post by elpuerco on 2006-09-22
OK I shall try that, thanks

---

### Post by CzarAlex on 2006-09-22
Actually.. Just sudo apt-get install apache2

All files in /var/www will then be accessable via the internet

Use a free DNS service like [www.zoneedit.com](www.zoneedit.com) to point yer domain to yer IP address.

Good to go.

---

### Post by elpuerco on 2006-09-24
CzarAlex,I like the idea of that :D 

But a few things though, apologies for my ignorance...

Would:

Pointing my domain name to my IP address would require me to get a static IP from my ISP?

I would in some way be opening up my hard disk to hackers?

Obviously I sould really have this running on a computer that will be left on 24/7?

I would need a powerful computer to deal with hits?

My bandwith would take a huge hit!!

I would need to learn HTML etc to actually create the pages?

---

### Post by chrisfay on 2006-09-24
> Would:

Pointing my domain name to my IP address would require me to get a static IP from my ISP?

Short answer: No

It is ideal to have a static IP to circumvent DNS issues resulting from abrupt dynamic IP changes. The recommendation given to use zoneedit.com's free dynamic dns service will also solve this problem; though a static IP is the easiest.

All you would need to do is create an account at zoneedit, create a zone for your domain  [www.elpuerco.co.uk](www.elpuerco.co.uk) and add some A records that point to your public IP. You are given a couple name servers by zoneedit that you have to give to your registrar in order for requests for [www.elpuerco.co.uk](www.elpuerco.co.uk) to get routed to zoneedits DNS servers and from there to your server.  

> I would in some way be opening up my hard disk to hackers?

Running a public server is always a risk; one that can be substantially minimized with good preventitive measures. Apache has good documentation on their site regarding securing your Apache server. I would highly recommend reading them.

> Obviously I sould really have this running on a computer that will be left on 24/7?

If you want public access to your website 24/7, then you've got your answer. 

> I would need a powerful computer to deal with hits?

Unless you're running an extremely large site with tons of traffic you'll be fine. I've heard of stories regarding terrible hardware handling a fair ammount of traffic; I wouldn't worry about that.

> My bandwith would take a huge hit!!

Again, most likely not. If you're really concerned about it, you can install bandwidth monitoring tools to analyze with accuracy and go from there. I know with my webserver I run at home, which gets a decent ammount of traffic on a cable line, I don't have any issues. Depends on your connection speed as well I suppose. 

> I would need to learn HTML etc to actually create the pages?

Yes and no. There are a ton of templates out there for you to basically edit a little and poof; you have a site. The filpside is that you'll be running something generic; not to mention you'll have your hands tied if you want to do more than basic modification. 

I would recommend picking up an html/css book and learning the basics of site design. It will go a LONG way in saving you sleepless nights designing your site.

Just some ideas.....;)

---

### Post by elpuerco on 2006-09-24
Thanks, a lot for me to look into ;) 

Some long sleepless nights ahead with coffee in hand:D

---

