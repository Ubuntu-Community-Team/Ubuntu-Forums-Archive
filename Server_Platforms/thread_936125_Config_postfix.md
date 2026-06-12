---
title: "Config postfix"
date: 2008-10-02
forum: Server Platforms
---

### Post by Vegan on 2008-10-02
I have installed postfix, and now I want to get it operational for phpBB use for security reasons. I have a total of 5 URLs running in vhosts with Apache2. 

[http://contract-developer.dyndns.biz](http://contract-developer.dyndns.biz)
[http://computer-chess.dyndns.biz](http://computer-chess.dyndns.biz)
[http://econ.dyndns.biz](http://econ.dyndns.biz)
[http://vegan.dyndns.biz](http://vegan.dyndns.biz)
[http://web-developer.dyndns.biz](http://web-developer.dyndns.biz)

I wanted to create one e-mail account for each, [email]contact@url.com[/email]

Here is the output from the install.





Setting up postfix (2.5.1-2ubuntu1.2) ...
Adding group `postfix' (GID 120) ...
Done.
Adding system user `postfix' (UID 110) ...
Adding new user `postfix' (UID 110) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 121) ...
Done.
setting myhostname: ubuntu.contract-developer.dyndns.biz
setting alias maps
setting alias database
changing /etc/mailname
setting myorigin
setting destinations: contract-developer.dyndns.biz, ubuntu.contract-developer.dyndns.biz, localhost.contract-developer.dyndns.biz,
localhost
setting relayhost:
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all

Postfix is now set up with a default configuration.  If you need to make
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
   ...done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

