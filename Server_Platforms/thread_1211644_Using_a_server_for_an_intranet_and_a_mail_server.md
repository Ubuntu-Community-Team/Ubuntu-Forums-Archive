---
title: "Using a server for an intranet and a mail server?"
date: 2009-07-12
forum: Server Platforms
---

### Post by darren884 on 2009-07-12
I want to use 8.04 LTS Server Edition possible for an upcoming server I am going to use... however does anyone know if I can make the web server only available to the intranet while still using it as a mail server? I am thinking I just install the Apache web server on it and then using hosts.allow just allow the local IP of the company (1-10 users) to access that, and then allow incoming and outgoing mail. The webserver would just be used for development purposes. Does anyone know if this is possible? Also does anyone know any good free anti-spam daemons I can use to tie in with my mail server? Thanx so much.

---

### Post by abaden on 2009-07-13
You can use Allow/Deny directives in your virtual host configuration to only allow certain IPs to access the server. You will see an example for the "/usr/share/doc" directory when you install httpd.

I've had good luck with SpamAssassin as free anti-spam. For email anti-virus, clamav seems to work well.


Alex

---

### Post by Cheesemill on 2009-07-13
As long as you don't forward port 80 from your external IP to your internal network then it won't be accessible from outside the LAN anyway.

---

