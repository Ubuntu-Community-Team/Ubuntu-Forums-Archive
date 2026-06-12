---
title: "Setting up bind on my web server"
date: 2007-07-08
forum: Server Platforms
---

### Post by federune on 2007-07-08
Hi,

Im new to the BIND dns server and am hoping you can help my problem:

I have a web server running hosting a website. The server has a dynamic ip and a dyndns.org account called "munk.mine.nu". I have another more pretty domain called "cdraid.com" and would any user that enters this in a browser to be directed to the website on "munk.mine.nu", i.e. "http://munk.mine.nu/WebApp/MySite" - without changing the address in the browser ("cdraid.com"). Am I able to solve this problem by setting up a nameserver on the machine the is hosting the web server? I can't seem to google any information about this scenario..  thanks

---

### Post by koenn on 2007-07-08
On first sight, I'd say you can do this with a DNS server - all thats required is that it has an alias (CNAME) record that points [www.cdraid.com](www.cdraid.com) to munk.mine.nu.
As the Adress record for munk.mine.nu. will be at a different dns server (the one that provides your dynamic dns for the dynamic ip address), i'm not 100% sure it will work, but it's worth a try (or some research).
In any case, the url in the browsers won't change, the browsers just don't care about the underlying network.

some remarks:
- you don't have to run your own dns for this to work - a dns server hosted by eg. an ISP or whatever company that handled the registration of your cdraid.com domain will also do the trick?

- even if you want to run your own DNS server, it doesn't necessarily have to be running on the same machine as the web server.

---

