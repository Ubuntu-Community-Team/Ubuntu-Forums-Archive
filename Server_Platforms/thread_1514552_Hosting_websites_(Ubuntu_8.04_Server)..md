---
title: "Hosting websites (Ubuntu 8.04 Server)."
date: 2010-06-21
forum: Server Platforms
---

### Post by Freyja on 2010-06-21
Good morning board members.

I am trying to set up a server where i can host my websites, since my profession is website developper, using Ubuntu 8.04.


[color=blue]****************************
Note:
There is no bug or problem with an existing guide, just wanted to ask whether I am following the right path and if there are any further guides (if needed).
****************************[/color]


**Alright, so far I have read various guides and executed followed ones**:
 - [The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
 -> Web Server: Apache 2.2 with PHP 5.2.4 and Ruby [color=green](worked)[/color]
 -> Database Server: MySQL 5.0 [color=green](worked)[/color]
 -> Mail Server: Postfix [color=green](worked)[/color]
 -> DNS Server: BIND9 [color=green](worked)[/color]
 -> FTP Server: proftpd [color=orange](assuming it worked)[/color]
 -> POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP. [color=green](worked)[/color]
 -> Webalizer for web site statistics [color=orange](assuming it worked)[/color]
 -> ISPConfig [color=red](did not try install)[/color]

 - [Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 8.04 LTS)](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)
 -> Send local messages and view those via SuirrelMail. [color=green](worked)[/color]

 - [Virtual Hosting With Proftpd And MySQL (Incl. Quota) On Ubuntu 8.04 LTS](http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04)
 -> Access from local windows machine. [color=green](worked)[/color]
 -> Seems to be rather slow to get the 'welcome message' from the ubuntu server. [color=orange](still assuming it worked)[/color]

 - [DNS server Setup using bind in Ubuntu](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)
 -> No error in the syslog (anymore).  [color=orange](assuming it worked)[/color]

**Server data**:
 - Servername: lainHost.
 - Hostname: Used 'lainHost.lain.ch' in all guides (did register the domainname at switch.ch).
 - IP-Address: Used 192.168.1.100 in all guides.

**Questions**:
 - So basically I am wondering if that is all or if I missed something, which is required to display websites via my ubuntu server.
 -> Do I need a static IP-Address (or am I to change the DNS on switch.ch each day)?
 -> How do I make that local SquirrelMail system global?


Thank you for reading, every help is appreciated.

---

### Post by pogztimz on 2010-06-21
> **Freyja said:**
> Good morning board members.

I am trying to set up a server where i can host my websites, since my profession is website developper, using Ubuntu 8.04.


[color=blue]****************************
Note:
There is no bug or problem with an existing guide, just wanted to ask whether I am following the right path and if there are any further guides (if needed).
****************************[/color]


**Alright, so far I have read various guides and executed followed ones**:
 - [The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)
 -> Database Server: MySQL 5.0 [color=green](worked)[/color]
 -> Mail Server: Postfix [color=green](worked)[/color]
 -> DNS Server: BIND9 [color=green](worked)[/color]
 -> FTP Server: proftpd [color=orange](assuming it worked)[/color]
 -> POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP. [color=green](worked)[/color]
 -> Webalizer for web site statistics [color=orange](assuming it worked)[/color]
 -> ISPConfig [color=red](did not try install)[/color]

 - [Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 8.04 LTS)](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)
 -> Send local messages and view those via SuirrelMail. [color=green](worked)[/color]

 - [Virtual Hosting With Proftpd And MySQL (Incl. Quota) On Ubuntu 8.04 LTS](http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-ubuntu-8.04)
 -> Access from local windows machine. [color=green](worked)[/color]
 -> Seems to be rather slow to get the 'welcome message' from the ubuntu server. [color=orange](still assuming it worked)[/color]

 - [DNS server Setup using bind in Ubuntu](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)
 -> No error in the syslog (anymore).  [color=orange](assuming it worked)[/color]

**Server data**:
 - Servername: lainHost.
 - Hostname: Used 'lainHost.lain.ch' in all guides (did register the domainname at switch.ch).
 - IP-Address: Used 192.168.1.100 in all guides.

**Questions**:
 - So basically I am wondering if that is all or if I missed something, which is required to display websites via my ubuntu server.
 -> Do I need a static IP-Address (or am I to change the DNS on switch.ch each day)?
 -> How do I make that local SquirrelMail system global? u


Thank you for reading, every help is appreciated.

have u tried to install "Apache"?

---

### Post by Freyja on 2010-06-21
Thank you for your reply.

Apache installation was a part of the first guide, sorry I forgot to append it in my post:
 - Web Server: Apache 2.2 with PHP 5.2.4 and Ruby

PHP works and I can access local websites too.

---

### Post by wojox on 2010-06-21
Look at this  page. it is how got mine going.


[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

---

### Post by volkswagner on 2010-06-21
You need your DNS record to point to your external ip address.

You need to verify port 80 is open and you are able to host from your location.

You will need to open port 80 on your router and forward that port to the internal ip 192.168.1.100.  Also make sure this address is outside the DHCP range of your router to avoid future conflicts.

To set you DNS record go to your registrar and set your domains A record to point to your ISP provided external ip address.

To verify your port 80 is open go to canyouseeme.org from inside your LAN and verify port 80 is open.


A simple early test to verify apache is working is to check it on the local LAN.  From inside your LAN on a second computer enter the interal ip address for the server in a browser.  You should at least get the default apache2 "it works" page.  Then you can set up virtual domains for your test sites, using Name based virtual domains in apache2.

EDIT:  Yes if you have a dynamic ip from your isp, you will need to setup a service such as noip, or dyndns for when the ip changes.  Starting with the basics first is a good idea, so set the ip as it is now before setting up dynmic forwarding.

---

### Post by Freyja on 2010-06-23
Thank you two for your replies.

Sorry that my feedback took so long, had to read through a few manuals/guides to make the further steps you recommended me.
Since your suggestions are mostly the same I will only quote one for simplicity.

> You need your DNS record to point to your external ip address.
So far I have made the following entries:
¦---------------------------------------------------------------------------
¦ /etc/bind/named.conf.local
¦---------------------------------------------------------------------------
¦ zone "lain.ch"{
¦        type master;
¦        file "/etc/bind/zones/lain.ch.db";};
¦
¦ zone "lain.li"{
¦        type master;
¦        file "/etc/bind/zones/lain.li.db";};
¦
¦ zone "1.168.192.in-addr.arpa"{
¦        type master;
¦        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";};
¦---------------------------------------------------------------------------

¦---------------------------------------------------------------------------
¦ /etc/bind/named.conf.options
¦---------------------------------------------------------------------------
¦ options {
¦         directory "/var/cache/bind";
¦ 
¦         forwarders{
¦                 195.186.1.162;};
¦---------------------------------------------------------------------------

¦---------------------------------------------------------------------------
¦ /etc/bind/zones/lain.ch.db
¦---------------------------------------------------------------------------
¦ lain.ch. IN SOA lainHost.lain.ch. admin.lain.ch.(
¦         2007031001
¦         28800
¦         3600
¦         604800
¦         38400)
¦ 
¦ lain.ch. IN NS lainHost.lain.ch.
¦ lain.ch. IN MX 10 lainHost.lain.ch.
¦ 
¦ www IN A 192.168.1.100
¦ mta IN A 192.168.1.100
¦ ns1 IN A 192.168.1.100
¦---------------------------------------------------------------------------

¦---------------------------------------------------------------------------
¦ /etc/bind/zones/lain.li.db
¦---------------------------------------------------------------------------
¦ lain.li. IN SOA lainHost.lain.ch. admin.lain.li.(
¦         2007031001
¦         28800
¦         3600
¦         604800
¦         38400)
¦ 
¦ lain.li. IN NS lainHost.lain.ch
¦ lain.li. IN MX 10 lainHost.lain.ch
¦ 
¦ www IN A 192.168.1.100
¦ mta IN A 192.168.1.100
¦ ns1 IN A 192.168.1.100
¦---------------------------------------------------------------------------

¦---------------------------------------------------------------------------
¦ /etc/bind/zones/rev.1.168.192.in-addr.arpa
¦---------------------------------------------------------------------------
¦ @ IN SOA lainHost.lain.ch. admin.lain.ch.(
¦         2007031001;
¦         28800;
¦         604800;
¦         604800;
¦         86400)
¦ 
¦ IN NS lainHost.lain.ch.
¦ 100 IN PTR lain.ch
¦---------------------------------------------------------------------------


> You need to verify port 80 is open and you are able to host from your location.
Using the command:
 - iptables -A INPUT -p tcp --dport 80 -j ACCEPT
Gave me the result:
 - ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www

> You will need to open port 80 on your router and forward that port to the internal ip 192.168.1.100. Also make sure this address is outside the DHCP range of your router to avoid future conflicts.
This one took a while. Now the result of 'canyouseeme.org' is:
 - Success: I can see your service on wh.at.ev.er on port (80)
 - Your ISP is not blocking port 80

> A simple early test to verify apache is working is to check it on the local LAN. From inside your LAN on a second computer enter the interal ip address for the server in a browser. You should at least get the default apache2 "it works" page. Then you can set up virtual domains for your test sites, using Name based virtual domains in apache2.
I can see the sample 'It works!' website using 'lainHost' or '192.168.1.100' also can see own added sample pages.

> To set you DNS record go to your registrar and set your domains A record to point to your ISP provided external ip address.
This is the step where I am stuck with currently.

When I go to my registrar (switch.ch) I can not set any A records, all I can enter are name servers.
Do I have to enter an other name server, like everydns and put my external IP-Address in their A record or can I put my external address in the name server field of my registrar site?
Probably I am confusing something here:)

---

### Post by volkswagner on 2010-06-23
It seems your registrar does not offer DNS control.

First you will need to determine if you have a static or dynamic ip address from your provider.  This will determine the best path.

If you have a static ip, then you will need to find a DNS provider offering services.  As far as this newbie knows, you cant run your own DNS server from home for WAN.  Zoneedit.com or similar shall suffice.

If you have a dynamic ip address, you will need to set up a service with a dynamic provider such as dyndns.com or noip.com.  These providers charge a fee for services when you select your own domain name.

---

### Post by Freyja on 2010-06-24
Thank you again volkswagner.

I am using a dynamic IP-Address currently. Wanted to setup and test everything before getting a static one, since at least here it is a bit more expensive.
So I did link my domain to 'everydns.com' (its name servers) on my registrar site and link the A record on 'everydns.com' to my external address.

**It works!**

Thank you, thank you:)
Will do for now (with changing 'everydns.com' everyday) for testing.

The only question left for now is, is it possible to set a root directory to domain names in some settings or do I need a script (like a php index page) for this?
For example 'domainA.com' not going to '/var/www/' but to '/var/www/domainA.com' and 'domainB.com' to '/var/www/domainB.com'.

Did try to search for it, but hard without really knowing how it is called.

---

### Post by volkswagner on 2010-06-24
You will want to set up virtual hosts within apache2.

Ther [server guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") or [apache wiki]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") should get you started.

---

### Post by Freyja on 2010-06-28
Time for my report:
 + So I set up two virtual hosts, which are working now.
 + Can access both websites from external computers (until my IP-Address changes).
 + Set up rights according to a forum post to 'chmod -R 555 /var/www'.
 - The only step I did not understand in the whole was the DNS setup ([DNS server Setup using bind in Ubuntu](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)).

To do:
 - Setup the local-only working PostFix/SquirrelMail for external usage too.

Right now, everything is working.
Thanks to all the helpers and readers. I will post again if any further issues appear.

---

