---
title: "dns--domain newb"
date: 2012-03-01
forum: Server Platforms
---

### Post by tomdagreek on 2012-03-01
Howdy!
I have a simple or maybe not a simple question.
I have servers that are connected to various routers behind a comcast modem.
All routers have been assigned static ips. I have 5 static ips of which i have owned for a while now.Is it possible to start a new domain within this setup to be visible to the outside world? Or must it go thru a registrar? Is it possible to more than one top domain within this setup?
I have a cpl of domains on godaddy which i can forward all traffic to a specific ip.
or..
Should I just create subdomains on these ip and maybe connect them to the top domain I have already created thru godaddy?
Tom

---

### Post by volkswagner on 2012-03-02
Your question is not unlike me asking if I should buy apples or oranges for my lunch.   Haha, it really depends on your needs and preferences.

If you are trying to save money, I'd say use subdomains since there will be no extra cost.  If you want to create unique web prerense, you may want to purchase top level domains. 

It may be helpful to describe what you'd like to accomplish.  Do you want to just host websites?  Will you be running a mail server?  You may want to reserve ip's for mail and even ssl.

You can setup a subdomain(s) and point the A record to one of your static ip's.

To answer your question, individuals can not just pioneer their own domain names without using a registrar.  There are free domain providers (ie: dyndns.com, no-ip.com) if you don't want to use one of your godaddy domains.

---

### Post by tomdagreek on 2012-03-02
To answer your question, individuals can not just pioneer their own domain names without using a registrar. 

Ahh.. kinda of what I wanted to hear. I wasnt sure if that could be done.
Very simple.. I would just like to give someone a domain name instead of a ip for ftp and such.
Would it be smart to add my top level domain when building a new nix box?
Virtualmin is very handy,I am getting the hang of it.Would i use godaddys nameservers?

---

### Post by volkswagner on 2012-03-02
You can use your top level domain when building a box, or you can edit your hostname any time after the install.

If you use a subdomain you will use DNS servers from GoDaddy.  You also have the option of free domains at dyndns or no-ip.  You would then use their respective nameservers.  There would be no need to configure the dynamic DNS service since your ip is static.

---

### Post by aeiah on 2012-03-02
incidentally, you could use both of your domains and have them point to the same IP address, but actually delivering different content. apache and other web servers can do this sort of thing

---

