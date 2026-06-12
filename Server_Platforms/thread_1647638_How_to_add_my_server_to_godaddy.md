---
title: "How to add my server to godaddy"
date: 2010-12-17
forum: Server Platforms
---

### Post by 13millerd on 2010-12-17
Ok so I got a domain name at godaddy.com and I can't figure out how to add my web server (ubuntu server 10.10) to be the home page. Any help would be great thanks.

David

---

### Post by Rocket2DMn on 2010-12-17
GoDaddy must have a configuration page where you provide it with the public IP to direct the domain to.  Assuming your web server is setup and working as desired, and you have the correct port(s) open through any routers/switches leading to your server, the URL you purchased should then pull up your web server's homepage.

It can sometimes take a bit of time for the DNS change to make its way across the internet (up to a few hours after GoDaddy makes it available).  You can test by pinging the domain to see if it tries to route to your IP.

---

