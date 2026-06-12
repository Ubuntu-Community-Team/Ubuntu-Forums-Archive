---
title: "true dns?"
date: 2008-11-20
forum: Server Platforms
---

### Post by tomdagreek on 2008-11-20
new to ubuntu.. had a quick question that may have a easy answer.
is ubuntu server fully able to be a dns server? or must u always go though a registrar site. if i set up ubuntu with a domain name that is not takin by anyone else,dmz the server and let it run should i be able to access that domain name through a web browser from a friends computer? when i tried settin up this my server brought my isps dns records up. something like blah.blah.comcast.com. ( i forget what it said exactly).this might be a noob question but was just wondering. i had set this up through another os (what other os? hehe) but i think it was interfering with gomommy(:P) records.. i dunno...
thanks for any help

---

### Post by jpkotta on 2008-11-20
If all you want is to be able to access your machine from the internet, you could use dynamic dns.  I use no-ip.com, but there are many others.  If you actually want your own domain, I'm guessing you have to register.  

You can run a nameserver on your LAN, but this won't be accessible from the internet.  Ubuntu obviously has bind, and other simpler nameservers.  I used to use dnsmasq on my LAN.

---

### Post by tomdagreek on 2008-11-20
i forgot to mention that i have static ips

---

