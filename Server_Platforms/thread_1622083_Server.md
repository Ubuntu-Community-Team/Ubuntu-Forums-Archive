---
title: "Server"
date: 2010-11-15
forum: Server Platforms
---

### Post by JKills on 2010-11-15
Hi there first off :)

I'm really new to this server stuff and owning a website.

My question is

I bought a domain & Hosting service from Godaddy.com

WellI no longer want to pay for hosting..Well I have a newer

desktop, which can be on 24/7. Question is The Ubuntu site

is horrible for beginners. (Besides the forums) Anyways..

I'm not sure which setup I need as in like LAMP Server, DNS server..



Could you help me out? 

Thank you 
Sincerely, JKills

---

### Post by lisati on 2010-11-15
*Thread moved to **Server Platforms**.*

You might want to look here: [https://help.ubuntu.com/10.10/serverguide/C/index.html](https://help.ubuntu.com/10.10/serverguide/C/index.html)

Do you wish to host a web site? Would you like to "do" email as well?

---

### Post by JKills on 2010-11-15
> **lisati said:**
> *Thread moved to **Server Platforms**.*

You might want to look here: [https://help.ubuntu.com/10.10/serverguide/C/index.html](https://help.ubuntu.com/10.10/serverguide/C/index.html)

Do you wish to host a web site? Would you like to "do" email as well?


Yes I wish to host two websites and what do you mean email?

---

### Post by lisati on 2010-11-15
It's possible to host websites using Apache, which can be configured to cope with more than one domain name. For example, on my server, I have [http://lisati.homelinux.com](http://lisati.homelinux.com) and [http://lisati.homelinux.org](http://lisati.homelinux.org) - different domain names, different websites.

It is also possible to use Ubuntu to act as an email server.

---

### Post by JKills on 2010-11-15
> **lisati said:**
> It's possible to host websites using Apache, which can be configured to cope with more than one domain name. For example, on my server, I have [http://lisati.homelinux.com](http://lisati.homelinux.com) and [http://lisati.homelinux.org](http://lisati.homelinux.org) - different domain names, different websites.

It is also possible to use Ubuntu to act as an email server.

Well the email part I'm not really interested in

Here is my problem 

I need to host my website 

and their website abc.com (forgot the domain name)

Is it possible to do that? 

But also retaining security? Because I wouldn't want them in my database ><

haha I hope this make's sense.

---

### Post by JKills on 2010-11-15
Since I just want to host websites..I just need to select LAMP Server correct?

---

### Post by JKills on 2010-11-23
Is there a in depth tutorial how to set up ubuntu?

---

### Post by wongo888 on 2010-11-23
You def could host two web sites using name based virtual hosting on Apache.

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

The question is, at your level of system admin knowledge, should you?

You bring up an issue of security. It takes work to keep everything patched and up to date. It takes some skill to configure a system well enough to put on the internet and have it not be immediately taken over by hackers using simple vulnerability scanners.

A decent web hosting company like Dreamhost costs single digit dollars a month and they do all the patching, network debugging, etc. That's like two drinks at Starbucks for your piece of mind. Web hosting is so cheap these days, it doesn't seem like a burden to me.

I'm not saying that you shouldn't learn all you can about Apache, MySQL and Ubuntu, but is it a wise move to rush in?

---

### Post by JKills on 2010-11-23
> **wongo888 said:**
> You def could host two web sites using name based virtual hosting on Apache.

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

The question is, at your level of system admin knowledge, should you?

You bring up an issue of security. It takes work to keep everything patched and up to date. It takes some skill to configure a system well enough to put on the internet and have it not be immediately taken over by hackers using simple vulnerability scanners.

A decent web hosting company like Dreamhost costs single digit dollars a month and they do all the patching, network debugging, etc. That's like two drinks at Starbucks for your piece of mind. Web hosting is so cheap these days, it doesn't seem like a burden to me.

I'm not saying that you shouldn't learn all you can about Apache, MySQL and Ubuntu, but is it a wise move to rush in?

Well I rather learn how to host my own website :)

---

### Post by J_5 on 2010-11-24
> **JKills said:**
> Hi there first off :)

I'm really new to this server stuff and owning a website.

My question is

I bought a domain & Hosting service from Godaddy.com

WellI no longer want to pay for hosting..Well I have a newer

desktop, which can be on 24/7. Question is The Ubuntu site

is horrible for beginners. (Besides the forums) Anyways..

I'm not sure which setup I need as in like LAMP Server, DNS server..



Could you help me out? 

Thank you 
Sincerely, JKills

You will need to at least install Apache on your sever, in order to host your web site. You maybe also need PHP, depending on how you are coding your website. 
This link my get you started: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

You will need update your DNS record for your website in GoDaddy to point your IP address where your sever is located.

---

