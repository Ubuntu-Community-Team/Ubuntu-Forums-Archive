---
title: "Uploading website to server?"
date: 2009-07-17
forum: Server Platforms
---

### Post by ericwj08 on 2009-07-17
Okay, I have my LAMP server setup and working, when I go to htttp://localhost it says that it's working... but now how do I upload my website to the server and make it viewable to the world wide web?

---

### Post by happypolla on 2009-07-17
if you have installed LAMP to the default settings, it will have it's context root at: /var/www/

you will see the index.html which publishes "It Works!" there.

so, to answer the first part of you question, you want your website to be contained there, alternatively, you can set up other paths in the httpd.conf.

if you have your apache port available to the Internet, that is all you need for it to be viewable, but to make things easier you will generally want to register a domain, etc...

---

### Post by ericwj08 on 2009-07-17
Okay, sorry I'm new to all this....  How do I make my apache port available to the internet?

---

### Post by happypolla on 2009-07-17
depends, if you have a router you need to forward the port, if you don't, just make sure no firewall is blocking it.

default port = 80.

---

