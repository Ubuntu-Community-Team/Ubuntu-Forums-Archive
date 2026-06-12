---
title: "Help please ! a default dovecot.conf file ??!!!"
date: 2012-03-01
forum: Server Platforms
---

### Post by dchen on 2012-03-01
When ungraded from Ubuntu 11.04 to 11.10, dovecot can't start successfully with lots of errors i.e.
"dovecot: doveconf: Warning: ... 'imaps' protocol is no longer necessary, remove it"...

At any rate, I want to setup a postfix(MTA)/dovecot(MDA) servers on Ubuntu 11.10, by following the Postfix installation and configuration instruction in Ubuntu Serverguide, in "1.4 Configuring SASL" section on page 190, after run "sudo apt-get install dovecot-common", it requires to edit the section of "auth default" and the "socket listen" option...,in the /etc/dovecot/dovecot.conf file, BUT my /etc/dovecot/dovecot.conf (only about 4k byes) CAN'T find the "auth default" "socket listen" !

I also checked into the /usr/share/doc/dovecot-common/dovecot/example-config, there is a
dovecot.conf, it's also about 4k size, and there is no such "auth default" or "socket listen" words can be found !  where is the default dovecot.conf file I can get a copy ?

BTW, there is the dovecot.conf.ucf file, whcih's about 50k and has the "auth default" and "socket listen" words there !   what is supposed the size for the /etc/dovecot/dovecot.conf ? i'm confused!

---

### Post by Neill_R on 2012-03-04
I am running 11.04 and am totally lost. Any chance of a how to install postfix / Dovecot. How did you set it up.

One point of possible confusion I am running Likewise open to join a Windows AD domain.

Sorry i can't be of help on your problem

---

### Post by promet on 2012-06-23
I am also having this precise issue. The server config howto notes these " 'auth default' and 'socket listen' " sections, but they don't appear in my default dovecot.conf file either. I've been trying to insert them manually, but no complete success as of yet.

Mail server config is some quite mystifying voodoo apparently ;)

---

