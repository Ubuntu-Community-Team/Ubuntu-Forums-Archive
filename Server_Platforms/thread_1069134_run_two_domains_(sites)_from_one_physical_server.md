---
title: "run two domains (sites) from one physical server"
date: 2009-02-13
forum: Server Platforms
---

### Post by jdcnosse on 2009-02-13
Okay, right now I have my Ubuntu 8.04.1 server edition set up for a single website, [http://annaandjameswedding.no-ip.org](http://annaandjameswedding.no-ip.org).

I'd like to know if it's possible to set my machine up to run two completely different (not connected) websites?

I think it's possible, but I don't know what I need to do to Ubuntu or apache to make it work.

---

### Post by Dr Small on 2009-02-13
Setup more VirtualHosts in /etc/apache2/sites-available that have different DocumentRoot's, add the new site to apache with `a2ensite name` and then restart apache.

---

### Post by jdcnosse on 2009-02-13
Okay and how would I connect to the second site then?  Does Apache run it on another port or something?  Or does the apache file just know when to use one and when to use the other?

---

### Post by Dr Small on 2009-02-13
Apache is just accepting requests on port 80 and sending traffic to appropriate directories based on the address. You will need that second subdomain address pointing to the same IP and same port.

As long as your second VirtualHost contains the same ServerAlias as the subdomain, you will be able to connect.

---

### Post by windependence on 2009-02-14
Name based virtual hosting is what you want, and it doesn't only work with subdomains ( I know Dr Small knows this but it isn't clear for the OP). 

One of the gotchas in the setup is that you generally need a default host that doesn't serve any content. There are quite a few great articles on the web. Google search "apache name based virtual hosting" and you will get a ton of hits.

-Tim

---

### Post by volkswagner on 2009-02-14
> **windependence said:**
> ...
One of the gotchas in the setup is that you generally need a default host that doesn't serve any content. There are quite a few great articles on the web. Google search "apache name based virtual hosting" and you will get a ton of hits.

-Tim

Would you mind elaborating on this.  I have seen a few threads, where folks seem to have vhosts set up correctly, yet things like aliasing do not work correctly.

See this [thread]("http://ubuntuforums.org/showthread.php?t=1056525"), the OP now believes it has to do with his default vhost.  I think he may actually be using it for content.

---

### Post by hyper_ch on 2009-02-14
basically you have to teach apache that if a query comes in for domainA.com that it should serve site A and if a query comes in for domainB.com it should serve site B. You do this with virtual hosts in apache. There are extensive guides there.

If you want to host more sites than just two and also email and stuff, I'd recommend you have a look at the perfect howtos at [www.howtoforge.com](www.howtoforge.com) including ISPConfig install.

---

### Post by jdcnosse on 2009-02-16
okay, and what if currently I'm hosting the first server on a port other than 80 because port 80 is blocked by my ISP (although I'm looking into seeing if I can get it unblocked, or if I'll have to move to a different ISP)

---

### Post by Phlee on 2009-02-16
As long as your pointing your DNS records for the two domain names to the same IP and you setup your Virtual hosts right in apache it doesn't matter what port you specify apache to run on.  It will take care of the rest.

---

### Post by windependence on 2009-02-17
> **volkswagner said:**
> Would you mind elaborating on this.  I have seen a few threads, where folks seem to have vhosts set up correctly, yet things like aliasing do not work correctly.

See this [thread]("http://ubuntuforums.org/showthread.php?t=1056525"), the OP now believes it has to do with his default vhost.  I think he may actually be using it for content.

Sure, Just let me find a few minutes to devote some time to the post. I have been swamped lately with projects - even my wife says she misses me. :)

I am going to find this out for myself as I am setting up a client hosting box because of the volume of requests I get to host their sites, so I will keep you all posted. They will be hosted on FreeBSD because of it's stability and simplicity, but I will be using Apache 2.2 and it should be very similar as far as the vhosts are concerned. I have done some configuration and that is where I found out about the non-content default host. I believe it was actually on the Apache site where I saw this mentioned. Then, the bells went off. I have been busy building an ecommerce site though, and I have not gotten back on the hosting project yet.

-Tim

---

### Post by songshu on 2009-02-17
> **Phlee said:**
> As long as your pointing your DNS records for the two domain names to the same IP and you setup your Virtual hosts right in apache it doesn't matter what port you specify apache to run on.  It will take care of the rest.

you would need to connect to this specific port from your browser though.

if your isp blocks port :80 and you setup apache to listen on port :10080 then you can only connect to
[www.mysite.com:10080](www.mysite.com:10080)
and not
[www.mysite.com](www.mysite.com)

if the site is for personal use then thats not a problem, if its a public site this would be a complete bummer.

---

### Post by Phlee on 2009-02-17
> **songshu said:**
> you would need to connect to this specific port from your browser though.

if your isp blocks port :80 and you setup apache to listen on port :10080 then you can only connect to
[www.mysite.com:10080](www.mysite.com:10080)
and not
[www.mysite.com](www.mysite.com)

if the site is for personal use then thats not a problem, if its a public site this would be a complete bummer.

Indeed, nature of the beast;)

---

### Post by jdcnosse on 2009-02-22
@songshu That's sorta what I have currently.  I've got a free domain name from no-ip.com, and I'm using their port 80 redirect service.

---

### Post by songshu on 2009-02-22
> **jdcnosse said:**
> @songshu That's sorta what I have currently.  I've got a free domain name from no-ip.com, and I'm using their port 80 redirect service.

is the traffic coming through or is it blocked by the ISP? mind that if you have a router in between you need to forward the :80 traffic of course.

don't know how long you can hold off the wedding ;)

---

### Post by jdcnosse on 2009-02-22
traffic comes through because I've set it up to just send traffic to my external IP (24.180.***.***:10910)

The router is set to forward port 10910 to my server at port 10910, and apache is set to listen on port 10910

---

