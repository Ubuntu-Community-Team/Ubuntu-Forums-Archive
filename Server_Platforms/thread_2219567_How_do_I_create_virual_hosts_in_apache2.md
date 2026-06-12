---
title: "How do I create virual hosts in apache2?"
date: 2014-04-24
forum: Server Platforms
---

### Post by Blix775 on 2014-04-24
I'm managing a server in a class and my group has the task to create differnet pages for all of the other groups so that they can have their own wordpress pages to post things in it. I have installed servers in the past but I've never created virtual servers before. The pages should be in the following format. group1.example.com, group2,example.com and so forth. I've been reading the apache2 Documentations but I found a couple of problems. First of all Ubuntu uses the /etc/apache2/sites-available folder instead of the httpd folder for its virtualhost files. Second, I tried the examples on the apache.org documentation on how to create the virtual host and it did not change anything at all. Another group configured the DNS so that might have something to do with it. The apache documentation is just making me a bit more confused so I'd like to know what things should I take into consideration when setting this up. The server is accessible through it's ip number but the url still doesn't work even though I enteres it in the 000-defult.conf file. Also, the folders inside /var/www are working like extra pages for the main site instead of individual sites which is what I'd like. Any help will be appreciated.

---

### Post by sandyd on 2014-04-24
What version of ubuntu are you using for this?

---

### Post by Blix775 on 2014-04-24
> **sandyd said:**
> What version of ubuntu are you using for this?

The server is using Linux Mint 16, but since it is based on Ubuntu and apache should work the very same way I decided to ask here because I don't have an account in the linux mint forums and did not really feel like creating one. Also, I like this forum best for linux questions. We're editing the files directly because the whole point is to learn to work directly with Apache. If there's some important discrepancy I'll make an account there and ask there.

---

