---
title: "postfix installation"
date: 2006-12-11
forum: Server Platforms
---

### Post by pragon on 2006-12-11
Hi
I have a problem while executing the following commands

apt-get install postfix-mysql postfix-tls postfix
apt-get install libsasl2 libsasl2-dev libsasl2-modules-sql
apt-get install spamassassin
apt-get install amavisd-new

after the last command I get the error


Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
The value of variable $myhostname is "servers", but should have been
a fully qualified domain name; perhaps uname(3) did not provide such.
You must explicitly assign a FQDN of this host to variable $myhostname
in amavisd.conf, or fix what uname(3) provides as a host's network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
amavisd-new
E: Sub-process /usr/bin/dpkg returned an error code (1)



so /etc/mailname is not created by default.How can I fix that problem?<Thanks>

---

### Post by Koybe on 2006-12-12
Did you try putting on the /Etc/mailname file? It's just a text file with the name of your domain.

The other way would be changing your /etc/postfix/main.cf and change the line referencing to /etc/mailname.

Hope this help...

---

### Post by MJN on 2006-12-12
Or, better still, do what it says and set **$myhostname = your.fully.qualified.domain.name **(e.g. servers.your.domain) in amavisd.conf.
 
Mathew

---

