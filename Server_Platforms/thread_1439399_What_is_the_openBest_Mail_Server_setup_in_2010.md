---
title: "What is the openBest Mail Server setup in 2010"
date: 2010-03-26
forum: Server Platforms
---

### Post by elitefox on 2010-03-26
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey

reference [http://flurdy.com/docs/postfix/edition8.html#software]("http://flurdy.com/docs/postfix/edition8.html#software")

I am wondering if this is still the best choice since I am planning to setup a mail server

category might be the following
how fast it is to send receive email?
how many email can it process?
how secure it is?

OS - ubuntu(first choice since I know this pretty well)
   - ubuntu 8.04 lts (good choice?)

mail server - I think this is where there are a lot of options [LIST]
[*]exim
[*]sendmail
[*]etc
[/LIST]Postfix
MTA - courier (is there any better/alternative to this)
    - using POP

db - mysql(this is my first choice since I know this well than pgsql)

content check - Amavisd-new (haven't heard of this though) is this really needed or it might slow the system?

spamassasin - needed

clamav - needed

SASL + TLS - don't really know this, isn't this just configurable in ubuntu server(please lighten me up TIA)

mail front - squirrelmail (I see a lot of goodbye squirrelmail, hello to roundcube)

postgrey - defined as a script to ward off spam also :D
         - probably needed

please lighten me up as much as you can


will be using 
ibm server xseries 266 
2gb memory may alot 4 gb swap 
120gb hd


can anyone tell me also the best config for a mail server
i.e. /home - 20 gb
     /var/mail - remaining since it is a mail server? (just a sample)

and another thing is the firewall?
is ufw enough or do I need another i.e. shorewall

TIA
elitefox


hope there will light to me tomorrow :popcorn:

---

### Post by fang0654 on 2010-03-27
I recommend you try out Zimbra:

[http://www.zimbra.com/community/]("http://www.zimbra.com/community/")

It is open source, free, and already packages together all of the stuff you are looking for (Postfix for MTA, SpamAssassin/ClamAV, etc).  Additionally, you also get a very nice and Ajax-y web interface for both webmail, and administration.

At my company we use a combination of the Open Source and Network (licensed) Editions, and couldn't be happier for it.

---

### Post by kewlrichie on 2010-03-27
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10")

if u want real ease of setup look into iredmail sets everything up in a few clicks
[http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04]("http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04")

---

