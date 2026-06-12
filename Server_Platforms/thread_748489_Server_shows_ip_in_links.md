---
title: "Server shows ip in links"
date: 2008-04-07
forum: Server Platforms
---

### Post by animatedantmo on 2008-04-07
Hi everyone,

Ive been searching all over to find an answer to my question and have found similar topics but nothing that works for me. Heres my situation. I am running Ubuntu server 7.10 with the standard LAMP setup. I am hosting my website on my own server and things seem to be working for the most part. My main problem is that when i browse a few test links that i have put up on the site I notice that the lnks contain the server ip instead of my domain name. I have registered my domain name and have configured it with them to mask my url. The mask is working in the address bar on the first page. But all links show [http://ip](http://ip) instead of [http://mydomain](http://mydomain) when i mouse over them.  Ive tried updating the servername in apache but it never seems to change from the ip no matter what I try. Just to summarize, im looking to ensure that an ip address isnt shown or given to the person viewing since it might change in the future. Any ideas?

---

### Post by cdenley on 2008-04-07
It sounds like what you have configured is a seperate web host using your domain which uses frames to display your web server using your ip address. If you view the source code in your browser, do you see your html, or some framesets? When you ping your domain, does it show your ip? If this is the case, you need to setup your domain with DNS service so your domain name resolves to your ip.

A work-around would be to use the [base]("http://www.w3schools.com/TAGS/tag_base.asp") tag, but if you're running your own server, there's no reason to use that frames hack.

---

### Post by animatedantmo on 2008-04-07
Hi cdenley,

You are correct. I noticed the frames at first but didnt know that it could cause problems. My problem is that the server is behind a very restricted firewall. I only have 1 port to work with so i was using the url forwarding options (which i have now disabled) in order to get the http requests to use the correct port. However now that i have created an A record pointing my domain to the server ip I dont see any way to specify a port for usage on my domain control panel. I have contacted them about this. Any other ideas or recommendations?

---

### Post by cdenley on 2008-04-07
If you can't listen on port 80, and can't have the user enter mydomain:8080, then you will need an external host to either redirect them, stick your site in a frame, or function as a proxy.

---

