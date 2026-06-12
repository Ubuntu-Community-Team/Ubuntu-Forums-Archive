---
title: "need to setup a mail server.."
date: 2008-02-22
forum: Server Platforms
---

### Post by Mia_tech on 2008-02-22
I need to setup a mail server, I'm looking for something easy to setup, like straight from the repos.....if someone could point me to the right direction?

thanks

---

### Post by igknighted on 2008-02-22
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I love these guides for server setup, just skip the server parts you don't need.  There are other server setups available, but postfix is the "tried and true".  If you need an easy config tool (and I know most here hate it), Webmin is pretty nice.  Cpanel isn't too bad either.  Beyond that you get into more complex "collaboration suites" that, while easier to manage sometimes, are resource hungry and have features you may or may not need.  See [www.zimbra.com](www.zimbra.com) for details on Zimbra (has a free, open source edition).

---

### Post by HermanAB on 2008-02-23
Well, there isn't anything easier than Citadel.

[http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

---

### Post by FakeOutdoorsman on 2008-02-23
> **HermanAB said:**
> Well, there isn't anything easier than Citadel.

Postfix is just a mail server (MTA): plain, simple, and fast, and it is in the repos.  Citadel, however, is a large and encompassing package which includes calendaring, instant messaging, bulletin board, etc, etc, etc. Maybe you're looking for something like Citadel.

---

### Post by dcsystems on 2008-02-23
I've setup postfix as a mail gateway and mailserver running cyrus... Postfix works great.

---

### Post by Rick Z on 2008-04-04
I have a question about setting up using Citadel or Postfix.  

Do I need to register a Domain Name first?  If I did buy a Domain Name, how would I redirect/point the name I purchased to my ISP?  I think I would need a static ip.

I saw a lot to howto suggest to get free DynDns or No-IP, but not a Domain Name I purchase.  Can anyone point me to right direct to setup my own webserver with mail-server function?


Thanks.

R

---

### Post by andguent on 2008-04-04
Keep in mind that you only need a domain name if you want to do external email. If you are playing with just internal company mail that doesn't go outdoors, you don't need a domain at all.

Dyndns can definitely work. If you are ok with an email address of [email]Bob@SirSparksALot.dyndns.org[/email] then it will do what you want. If you want a domain name more professional, you need to buy a domain. Search the WWW for "domain name registrar", any hits there will gladly take your money for you, and will include an option to specify where your mail server is.

Start with Dyndns first and see if you can get it working.

Once you have a domain name (Dyndns, or 'full', either work) you are looking for either "Mail Server Exchanger", "Mail Server Record", or MX. Those terms are all the same thing. The company you have your domain name through should give you the option to set that. Point that record at your server, poke some NAT holes, and the rest of the setup is daemon configs.

If you are going all out with this, and it needs to be professional grade email, a static IP address from your ISP is required. If this is just for personal education or a school project, don't worry about it. Some emails may get lost/delayed every time your power goes out, but everything else should work.

---

