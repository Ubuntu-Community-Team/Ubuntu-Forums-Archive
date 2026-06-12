---
title: "How to setup a server."
date: 2009-07-11
forum: Server Platforms
---

### Post by Cam42 on 2009-07-11
I'm a total n00b when it comes to servers, so I need to know how to set one up. I'm looking to host my blog/website on my server, and maybe a few other things. How would I do this? I'll be using wordpress.org 
Also, would you recommend using the 8.04 LTS or Jaunty? What would I need to be able to access my blog/website over the internet?

---

### Post by happypolla on 2009-07-12
I recently installed 8.04 LTS as a personal server, and it was easy to get going. In fact after install, it's ready with LAMP (as long as you select it during install).

You should probably try get some understanding of apache, and then you will probably need to register a domain so it is easier for people to access you server.

---

### Post by Copernicus1234 on 2009-07-12
Well, just install apache, php and mysql and follow the instructions ([http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install](http://codex.wordpress.org/Installing_WordPress#Famous_5-Minute_Install)) for install on the wordpress site. :)

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server

Go to localhost with a browser and check out the "It Works" message from Apache. Put in wordpress. Start playing. :)

---

### Post by Ian_F on 2009-07-12
If I were you I'd install Ubuntu Server Jaunty. You can administer the server in a number of ways: Putty, VNC, Webmin. I personally use all 3.

Does your ISP provide a static IP address or a dynamic one?

Have you checked that your ISP allows you to host your own website?

Do you already have your own domain name?

Why are you thinking of hosting it yourself rather than going with a hosting service?

---

### Post by Cam42 on 2009-07-12
> 
Does your ISP provide a static IP address or a dynamic one?
I'm not sure, but I think it's dynamic
> Have you checked that your ISP allows you to host your own website?
Haven't checked
> Do you already have your own domain name?
No, but I'll get one soon.
> Why are you thinking of hosting it yourself rather than going with a hosting service?
Because I have a server laying around that I have no other use for.
__________________

---

### Post by Ian_F on 2009-07-12
> **Cam42 said:**
> I'm not sure, but I think it's dynamic

Haven't checked

No, but I'll get one soon.

Because I have a server laying around that I have no other use for.
__________________

If you've a dynamic IP address then [**see here**]("https://help.ubuntu.com/community/DynamicDNS") for a few ways to solve that one.

Before you get too carried away setting everything up it really is worth checking that your ISP allows you to host your own website. Some do, some don't. If you see anything in the T&C about them blocking port 80 then, although you can work around this, you're probably better off abandoning the whole idea.

Setting the server up is relatively easy, the "tricky" part is getting it online. ;)

---

