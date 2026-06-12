---
title: "Web hosting using Tomcat 6"
date: 2008-03-25
forum: Server Platforms
---

### Post by aiflin on 2008-03-25
Hello,
    I have created a website that is running on Tomcat 6, on Ubuntu 7.1. I also have bought a domain name. I have a static IP address. Now, how do I do the web hosting? Can somebody please help me here with the required configurations ?

---

### Post by pseudo-random on 2008-03-25
You need to change your domains DNS settings to point it at your home IP.
Ensure port 80 (HTTP) is open on your firewall and your web server is securely configured, especially if it is run on a computer containing private data you wouldn't want public.

---

### Post by aiflin on 2008-03-25
Thanks Psuedo. I don't have any web server such as Apache HTTP serve r configured. Do I need one ? 

What I understood is that web servers are primarily used for load balancing but I just have one Tomcat instance running. So do I still need to have Apache HTTP server in front of my Tomcat ?

Also, I am running from my home computer. Can just securing the Tomcat server enough ?

Thanks

---

### Post by pseudo-random on 2008-03-25
Never touched tomcat myself.
I've hosted from home before using apache2.
It's easy enough. I'd recommend a standard apache2 install since it takes seconds and doesn't use much resources.
From what I understand tomcat has its own HTTP server so you shouldn't need apache. Just point your browser at [http://localhost](http://localhost) to find out.

---

### Post by aiflin on 2008-03-25
Thanks Pseudo.

Tomcat having its own HTTP server, is this a new feature in Tomcat 6 ?

Also, if that is the case do I have to do anymore configuration apart from pointing my domain to my static IP address ?

---

