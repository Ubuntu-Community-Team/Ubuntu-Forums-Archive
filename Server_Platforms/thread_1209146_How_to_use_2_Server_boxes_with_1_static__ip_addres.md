---
title: "How to use 2 Server boxes with 1 static  ip address"
date: 2009-07-10
forum: Server Platforms
---

### Post by R.Bucky on 2009-07-10
I host over 6 domains on my primary server box at home using Apache Named Based Virtual Hosting. I would like to add another box to my network to serve up pages. However, I only have 1 static ip. What is the best way of doing this? Any ideas?

My primary box is more than adequate - no problems. But, I wonder if it can be accomplished?

Operating Ubuntu Server 8.04, RAID1 w/hot spare. The other box would be a standard 1-disk installation.

---

### Post by guilly on 2009-07-10
Ahh maybe I'm not understanding the question correctly so ignore this if this is true. 

But a simple router would do the trick would it not? One static ip will be seen from the outside world while multiple private ip's can be used inside your LAN...

---

### Post by credobyte on 2009-07-10
I would go for a router - 1 static + 2 local IP's should work just fine :)

---

### Post by R.Bucky on 2009-07-10
Naaaa. Could it really be that simple? Going to give that a shot tonight.

---

### Post by windependence on 2009-07-10
You are not going to be able to forward port 80 to two different local IPs. You could run it on a different port, but I would just buy a block of IPs from your ISP. I have a block of 8 for $14.95 a month.

-Tim

---

### Post by R.Bucky on 2009-07-10
My ISP charges $4.95/ip. It would be nice to have a block of 8 for that low price! If it were uber critical, I would go ahead with that. My current server is more than adequate for hosting my multiple domains. Just tossing around an idea...

---

### Post by guilly on 2009-07-10
That's what I was afraid of... the port 80 thing. There must be some sort of work around for that though, no???

---

### Post by Cheesemill on 2009-07-10
Check out mod_proxy for apache, it will allow your current server to forward requests for specific sites to a different web-server on your internal network. I've never used it myself so can't give you a more detailed solution. Google is your friend here.

---

### Post by R.Bucky on 2009-07-10
If I used two routers off my modem... i wonder if Named Based hosting would still work. 

So many experiments to try!!!

---

### Post by Cheesemill on 2009-07-10
> **R.Bucky said:**
> If I used two routers off my modem... i wonder if Named Based hosting would still work. 

So many experiments to try!!!

Nope, this won't work. Take a look at my post above for the solution.

---

### Post by kustomjs on 2009-07-10
I am using apache with virtual hosting and I am hosting 3 sites on one static IP and all my sites are on port 80.  how I am doing this is by smoothwall and using internal ports.

also here is how I got mine setup:

under /etc/apache2/sites-available:
you need to have a file setup under domain.com.conf
<VirtualHost *:80>
ServerName domain.com
DocumentRoot /var/www/domain/
</VirtualHost>  

the key is the servername.

under this setup I have 3 different websites under port 80 like that

---

### Post by Cheesemill on 2009-07-10
The OP is already doing this, the question is how to use more than one internal server with only one external IP.

---

### Post by kustomjs on 2009-07-10
if he wants to that he would have to change the different port to 8080 and look at mod_rewrite.

---

### Post by windependence on 2009-07-11
You should all be aware that messing around with the default port will kill some traffic to your site. Many many corporate sites will block any traffic they think is being redirected. When I first started hosting sites in house I hosted several on 8080, but my clientele soon informed me that they could not access the site. As soon as I fixed that, everyone could view the content. You may never know if it's a sales site or a blog, but I run message boards, and I got tons of people letting me know it wasn't working. If you are just hosting a private site and don't care then it's fine, but if you are trying to run a site that everyone can access, you should not do this. I know, I know, many people here are doing it but they are not informed and probably don't know people can't see their site. Fact is, most people surf at work. My traffic goes way down on the weekends.

-Tim

---

### Post by doogy2004 on 2009-07-13
Just an idea...

How about trying some type of load balancer?

---

