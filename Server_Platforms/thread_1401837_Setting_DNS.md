---
title: "Setting DNS"
date: 2010-02-08
forum: Server Platforms
---

### Post by ivanuska on 2010-02-08
Hi.

I want that my home server (public ip) be available at example.com (my personal web page).

Help me please.

---

### Post by Bachstelze on 2010-02-08
You need to set that up on the interface provided by your domain name provider if there is one, otherwise you'll have to run your own DNS server, or find someone that will let you use his.

---

### Post by artemka on 2010-02-09
Yes, I have interface provided by my domain and I can change NS zone.
But I do know what configs need my Ubuntu server (8.04).

[COLOR="SlateGray"]PS. Sorry, my old account "ivanushka" is not work.[/COLOR]

---

### Post by maddog2050 on 2010-02-09
I have done this exact same thing.

As my public IP address is not static I have used a dyndns.com to get myself a free dynamic DNS address e.g. xyz.gotdns.org and use ddclient to keep it updated. Then I created a CNAME DNS record on my domain name and pointed it at the xyz.gotdns.org

[www.xyz.com](www.xyz.com) -> xyz.gotdns.org -> your public IP

This I'm sure is just one of many ways to achieve the same thing. But it may just do what you want.

Adam

---

### Post by artemka on 2010-02-09
Thanks! It's very interesting idea :)

But, I need the full solution. 
I want setting my home server, that he worked as a hosting...

---

### Post by noway2 on 2010-02-09
If you have a dynamic IP address from your provider, the dyndns site that the previous poster referenced will get you started.  If you have a static IP address, you should be set as long as your provider's DNS resolves it to your site.  From there you will need to learn how to forward port(s) on your router and begin adding services to your server.  Are you interested in SSH, Web sites (apache) FTP, Blog (wordpress), email (postfix, exim, zimbra)?  If you search in this forum for keywords related to what you would like to accomplish with your server you will find plenty of information on how to get going.  I apologize for my terseness, but this is a topic that comes up frequently enough that the forum search should answer most of your questions.

---

