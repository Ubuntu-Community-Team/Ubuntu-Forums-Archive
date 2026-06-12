---
title: "desktop server???"
date: 2007-02-22
forum: The Cafe
---

### Post by TheRingmaster on 2007-02-22
Is there any way to have my home pc as a server also? I am trying to find a good free website hosting for my website and I have failed to find any ( I really hate 1111mb, 8888mb, freespace.com). They all seem to mess with my (x)html, the worst being freespace.com. So I am on a journey to use my own computer as a small web server. Is this possible? Does any have a recommendation for an online web service?

---

### Post by Tenicus on 2007-02-22
sudo apt-get install apache ?

---

### Post by TheRingmaster on 2007-02-22
> **Tenicus said:**
> sudo apt-get install apache ?

Are you sure that is all I would have to do?

---

### Post by Medieval_Creations on 2007-02-22
Depending on what you are going to use it for apache2 is all you really need to have your desktop run as a web server.  Other packages to consider php5, mysql-server, mysql-client, & tomcat5 to name a few.

Setting up access to it from the web is a different story.  I've only done it once and I had a heck of a time (mostly noob configuration mistakes).  Alot of it depends on you ISP too, some don't allow web hosting.  Afraid I'm not much help on that part of it.

---

### Post by Tenicus on 2007-02-22
Well you would have to forward port 80 as well

---

### Post by RandomJoe on 2007-02-22
Most home ISPs block port 80 entirely - no one would be able to access your site.  You can set up Apache to use a different port, but then everyone would have to remember to browse to [www.yoursite.com:8080](www.yoursite.com:8080) or something.

Further, most home ISPs have in the Terms of Service clauses prohibiting home servers.  For small-scale, lightly-used applications they generally overlook (or just don't notice) them (I run a couple myself).  However, it _is_ against the ToS, which means if they decide you're using too much bandwidth or they just go on a crackdown they can shut off your connection / penalize you / whatever the ToS says.

If you really want a world-accessible site, many ISPs will offer "home office" connections that are more expensive than a residential connection but cheaper than an actual "business" account.

That said, yes all you have to do is install (and maybe configure) Apache.  For most uses, it'll be configured okay as-is, but I'd certainly want to check through the settings to be sure they are safe before exposing it to the web at large.

If you have a spare computer laying around, I would use a separate computer for the web server.  If someone is going to try hacking on my web server, I'd just as soon it wasn't the same machine I kept all my other data on!

---

### Post by sonny on 2007-02-22
You can always use something like [No-IP]("http://www.no-ip.com/") to make the calls to a given address be redirected to your machine, that way you can setup an FTP or webpage and have everyone look at it through "normal" browsers or as my aunt'd say normal "internet".

---

