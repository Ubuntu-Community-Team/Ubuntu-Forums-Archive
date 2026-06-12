---
title: "dovecot-postfix installation consistently fails"
date: 2009-10-20
forum: Server Platforms
---

### Post by dlouwers on 2009-10-20
Hi,

When doing an apt-get install dovecot-postfix on Jaunty 9.04 the process allways fails. Afther that apt-get remove dovecot-postfix will also fail, complaining of missing configuration files every step until it works. If I then use dpkg to --purge and try to reinstall I get the same hell all over again.

I am not posting the errors yet because that would mean making it fail again and that would take some time. So I would first like to probe if this is a known issue. Note that installation is on a Rackspace virtual server that has root password enabled, if that's at all relevant.

---

### Post by dlouwers on 2009-10-20
Ok, the error is: 'egrep: /etc/dovecot/dovecot.conf: No such file or directory' 
So somehow it seems that dpkg fails to purge the dovecot files and expects the config files to still be there. Trying to purge dovecot results in a message that it isn't installed.

When creating this file and trying to install again it fails with the very vague: 'dpkg: error processing dovecot-postfix (--configure)'

This happens ad eternum when I try to remove/install again. Also removing takes a lot of hacks in the form of using touch to create all kinds of expected config files.

Any ideas or does this mean that my installation is irretrievably damaged?

Best,

Dirk Louwers

---

### Post by rahmath on 2009-10-21
ok, for this mail server, where is the user database? it it configured to connect to a LDAP Server...??? if so, most probably the problem is your LDAP server is not working or cant be reachable by this mail server.

I faced almost a same problem like this. When i tried to install dovecot it was not working at all... but at the same time all other packages are installing without any probs... finally i found that the LDAP service in the LDAP server was not running, so this mail server was not able to contact the ldap service while installing the dovecot.

---

### Post by dlouwers on 2009-10-21
Nothing has been configured yet. Everything is default. So: plain system -> install dovecot-postfix -> trouble. Configuring the mail system would be the next step after installation.

---

### Post by Samatva on 2009-11-16
Bump - I'm having the same problem - Please Help!

Server ver 9.04, fresh install without Postfix, no LDAP or other special case, tried to add Postfix first, then Dovecot - have tried to uninstall and start over, including manually removing the .conf files (this may have been a mistake, but was after encountering other errors...).

TIA,
Peace,
- Samatva

---

### Post by kewlrichie on 2009-11-17
Have you checked then usual server guide links ? [https://help.ubuntu.com/9.04/serverguide/C/email-services.html]("https://help.ubuntu.com/9.04/serverguide/C/email-services.html") and this guide also which should work for 9.04 for the install of postfix and dovecot [http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10]("http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10")

---

### Post by Samatva on 2009-11-23
Thanks for the info, kewlrichie.

I *think* the separate package for Dovecot expects the mailbox files to be in a different location (user home folders?).

I ended up copying the config files from a fresh Ubuntu install where the mail server was selected upon install, changed the host name and was off and running....

Had I followed the instructions you referenced (i.e. install dovecot-postfix instead of just dovecot (dovecot-common, et al)), I probably would have been OK. Live an learn!

I think from now on, we will go ahead and install with everything and then turn off the unused services. We use Webmin, so it's really easy.

---

