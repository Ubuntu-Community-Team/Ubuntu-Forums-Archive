---
title: "Setting up a mail server."
date: 2009-04-25
forum: Server Platforms
---

### Post by TR1X on 2009-04-25
Well, I set up apache2 just fine along with mysql, php, etc. all the web server stuff went fine for me.

Now I'm a total n00b with the mail server.

I tried reading guides and they just haven't worked for me.

So far I have postfix and all the INSTALLED, but I don't get how to work it.

I have port 80 blocked (if thats a problem with mail servers, idk)
[www.coleryandesigns.com](www.coleryandesigns.com) is the website I got up and I want to use the same domain for mail.

Please help me out guys, thanks.

---

### Post by HermanAB on 2009-04-25
Howdy,

Installing a Postfix based system is very difficult.  A first time Postfix install will take you about two weeks (80 to 100 hours) of full time head scratching. If you want something easy, install Citadel or Zimbra.  You can install Citadel in about 20 minutes, which is rather easier:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

The problem with postfix is that you also need spam assassin, clamav, dovecot, apache and roundcube to have a full system.  Citadel or Zimbra does it all in one package and Citadel has special hooks for RBLs, spam assassin and clamav.  If you are truly lazy, then you can download a fully working Citadel virtual machine (including spam assassin and clamav) and run it on VMware.

Note that to install a mail server, you first have to get a domain name, set the hostname and configure the DNS with A, PTR and MX records.  If any one of those settings is bad then the server *will not work*.  The hostname *must* resolve forward and reverse, otherwise you are just wasting your time.

Some guides here:
[http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

---

### Post by Wiebelhaus on 2009-04-25
> **HermanAB said:**
> Howdy,

Installing a Postfix based system is very difficult.  A first time Postfix install will take you about two weeks (80 to 100 hours) of full time head scratching. If you want something easy, install Citadel or Zimbra.  You can install Citadel in about 20 minutes, which is rather easier:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

The problem with postfix is that you also need spam assassin, clamav, dovecot, apache and roundcube to have a full system.  Citadel or Zimbra does it all in one package and Citadel has special hooks for RBLs, spam assassin and clamav.  If you are truly lazy, then you can download a fully working Citadel virtual machine (including spam assassin and clamav) and run it on VMware.

Note that to install a mail server, you first have to get a domain name, set the hostname and configure the DNS with A, PTR and MX records.  If any one of those settings is bad then the server *will not work*.  The hostname *must* resolve forward and reverse, otherwise you are just wasting your time.

Some guides here:
[http://aeronetworks.ca/citadel-basics.html](http://aeronetworks.ca/citadel-basics.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Just to reiterate with this user suggested , hella fine post. exactly what I was going to post.

---

### Post by bejita on 2009-04-26
Perhaps this guide will help someone who wanna learn how to set up [a mail server]("http://winhows.net") using Ubuntu Server 9.04

---

### Post by TR1X on 2009-04-26
Thanks!
I'll try this out next weekend when im working on it next.

and after all thats setup on to figuring out ftp >.<

---

### Post by HermanAB on 2009-04-26
Howdy,

FTP is quite trivial.  Install proftpd or vsftpd.  Both are in Synaptic.  It works right out of the box.  You don't have to configure anything.  In fact, changing the configuration is a sure way to break it, so make a backup of the setup before changing anything.

---

### Post by bejita on 2009-04-28
Yes, setting ftp is depend on requirement. For large deployment, database support needed and that feature is not supported by vsftpd.

---

