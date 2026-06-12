---
title: "Host Multiple Sites with Apache2"
date: 2009-01-22
forum: Server Platforms
---

### Post by thesnipah on 2009-01-22
I have already re-installed ubuntu 8.10 server over 20 times already trying to get the server to host 2 websites. All my DetaiIs:
I want the server to host my dads website and my website.
My server installed apache thru the ubuntu cd setup and I chose LAMP server
My server is behind a router, with the ip address of 192.168.1.6 and has port 80 forwarded to it

I cannot find a single tutorial online that covers how to set this up from start to finish. Some leave out that you have to modify httpd.conf or apache.conf, some have me enable virtual hosts thru its own config file, other have me "append" it to the end of a config file, some have me put the html docs in a new folder, others have me leave them in /var/www. I have been trying to get this to work for MONTHS now, and my stress level is just about to explode. All i want to do is host 2 separate websites on 1 server.... it was so easy with windows and IIS......... please, if anyone knows of a truly good tutorial for first time apache2 users to host multiple websites, please... help me.... I need a complete tutorial from start to finish..... I beg you, I dont want to go back to a windows server.....

---

### Post by uzi09 on 2009-01-22
Hey.

I've been wanting to set this up for some time as well, however never got around to it. 

[This]("http://www.64bitjungle.com/tech/apache-virtual-hosts-and-mod_rewrite-on-ubuntu-hardy/") tutorial seems to be a good one so far, however I haven't given it a try.

If you try it out, please let everyone know how well it is to follow.

I found it from [this]("http://www.unix-tutorials.com/tutorials.php?os=Ubuntu") site, which seems to have a number of tutorials related to servers.

Hope it helps.

uzi

EDIT:

Or perhaps [this]("http://httpd.apache.org/docs/1.3/vhosts/ip-based.html").

---

### Post by spiderbatdad on 2009-01-22
As far as I know, even using Mod_rewrite requires the second site have a real FQDN separate from the first site...unless you only want access inside a LAN.
The simplest way is to register a second domain and create a virtual host container.

---

### Post by HighCommander540 on 2009-01-22
Actually all you would need to do. Is follow most virtual host tutorials. The only thing that you have to do is after wards make sure that you forward both of the ports that you are going to be using for both your father's and your server.

You will have to make two different directories for both your father and yourself. Ubuntu makes it really easy, because the sites-enabled fold is already made. All you have to do is make another file the same that the default one is but specific another port and enable the virtual host module.

---

### Post by spiderbatdad on 2009-01-22
lol. if the names dont resolve to the ip address they will not work outside the lan. The virtual host file that matches the FQDN registered to the ip address is the only one that will be displayed. It is much easier to register another name for the other site.

---

