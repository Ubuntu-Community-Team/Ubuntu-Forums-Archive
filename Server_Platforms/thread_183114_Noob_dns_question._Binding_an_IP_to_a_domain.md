---
title: "Noob dns question. Binding an IP to a domain"
date: 2006-05-27
forum: Server Platforms
---

### Post by 0MG on 2006-05-27
Hey all,

I managed to get this working in the past on an old server, but am runnign a new one now and I've forgotten how! I want to use bind to allow outside computers (outside my network) to be able to reach my domain. Extremely noobescent. If you could point me in the direction of a howto, that would be great.

---

### Post by ddoctor on 2006-05-28
The bind manuals are a good place to start. [http://www.bind9.net/manuals/](http://www.bind9.net/manuals/). I set up bind on fedora 3 mainly with the help of this. I think the same principles apply to ubuntu. 

Sounds like you want to host a public authoritative DNS server for a domain (like bobsbarnacles.com). If so, I think this is how to do it:

Your domain's whois record needs to point to the public IP of your DNS server (known as "delegating your domain" and is normally done on your registrar's website). This is something your registrar does.

In your named.conf file (might be in /etc/named.conf):
- set up a domain and specify the zone file. 
- in the options section, set allow-query to allow the whole world to query this dns server

Make a zone file for this domain specifying the A records etc.

Whenever you change the zone file or named.conf, you need to restart the "named" service. 

You'd also have to open port 53 on your firewall to allow DNS traffic.


I think this is the go... but, check it out for yourself. Read the bind manual and some howto's and do a bit of experimenting. There's lots of resources on the subject and plenty of howto's around for all the types of bind server you could run.  

Hope this helps.

---

