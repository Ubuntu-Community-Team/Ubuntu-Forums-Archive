---
title: "Webserver setup"
date: 2011-06-30
forum: Server Platforms
---

### Post by ScottG89 on 2011-06-30
I am complete beginner when it comes to this stuff but I have been reading a lot about how to setup lamp and have found some good tutorials. I think I just have one remaining question, once I get the server all up and running for localhost. How can I set it up so it has a domain name and can be accessed to everyone on the internet (not just on my home network). Thank you in advance.

-Scott

---

### Post by TechSupportx86 on 2011-06-30
You must forward port 8080 to your server in your router's settings. This is so when someone connects to XXX.XXX.XXX.XXX:8080, it goes to your server instead of your router (which doesn't host anything).

For am actual domain you need to register a domain name and link it your IP. Sites like godaddy.com or any will do just fine.

---

