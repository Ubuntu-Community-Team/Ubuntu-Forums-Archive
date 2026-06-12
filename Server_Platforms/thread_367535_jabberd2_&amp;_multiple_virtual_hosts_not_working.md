---
title: "jabberd2 &amp; multiple virtual hosts not working"
date: 2007-02-22
forum: Server Platforms
---

### Post by el3ktro on 2007-02-22
Hi,
I'm trying to set up a jabberd2 server with multiple hosts. I got it running successfully with only one hostnames. New users can register and login, everythings working fine - but as soon as I try to use multiple hosts it fails. I've set up multiple hosts after this how-to:

[http://www.jms1.net/jabberd2/](http://www.jms1.net/jabberd2/)

(at the end of the page). Basically, I've put all domains I have in c2s.xml, then I've created one sm.xml file for each hostname (sm-domain.de.xml, sm-domain.com.xml, sm-domain.org.xml and so on), and I've put one line for each sm with it's own config file into jabber.cfg. When I start the server, it runs, and existing users of my first domain can login, but I can't register new users on ANY of the domains, also the one domain that was working before. The log files are not saying anything. When I try to register a user, there's just two lines in c2s.log - thats all:

```
Thu Feb 22 15:06:15 2007 [notice] [10] [172.16.3.31, port=33946] connect
Thu Feb 22 15:06:15 2007 [notice] [10] [172.16.3.31, port=33946] disconnect
```

The relevant parts of my config files look like this:

```
c2s.xml:
<id>domain.de</id>
<id>domain.com</id>
<id>domain.co.uk</id>
<id>domain.fr</id>
<id>domain.es</id>
```

```
sm-domain.de.xml:
<id>domain.de</id>
<pidfile>/var/run/jabber/sm-domain.de.pid</pidfile>
```

```
jabber.cfg:
sm          /etc/jabberd2/sm-domain.de.xml
sm          /etc/jabberd2/sm-domain.com.xml
sm          /etc/jabberd2/sm-domain.org.xml
```

When I start jabber, I see one sm process for each domain, I see the responding pid files in /var/run - but I can't register any new users. When I start the jabber daemons in the foreground with the -D (debug) options, there's not any valuable information at all. What am I missing here!?

---

