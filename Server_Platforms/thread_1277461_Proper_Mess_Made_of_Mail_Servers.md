---
title: "Proper Mess Made of Mail Servers"
date: 2009-09-28
forum: Server Platforms
---

### Post by iannem on 2009-09-28
Hi,

I am new ubuntu user, currently trying to setup a web server on a dedicated server environment.

Following several different online tutorials, about getting the server up and running.

I am experiencing problems with setup of the mail servers. No matter what I do, I seem to end up unable to start the mail server. I have tried uninstall and reinstall of ubuntu server 9.04 several times. Each time I seem to get a different issue.

I think my main problem is due to a certificate that I setup that any subsequent installs inherit.

[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p6) (didn't find a locales error)

[http://www.mysql-apache-php.com/#phpmysqlapachekits](http://www.mysql-apache-php.com/#phpmysqlapachekits) (mail server won't start)

[https://help.ubuntu.com/9.04/serverguide/C/postfix.html](https://help.ubuntu.com/9.04/serverguide/C/postfix.html) (doesn't seem to be any kind of problem, just doesn't work)

I am fully aware this is not a problem with the system, and is totally user error, I just can't seem to find a way to get it to work or anyway back.

Does anyone have any suggestions?

Thanks

---

### Post by qwertysockets on 2009-09-28
I too am having trouble with certificates. If you followed the Ubuntu guide, you should be fairly well off, but...with that being said:

Try a ps -A and look for smtpd or what not. Try a telnet localhost 25.

If it isn't running at all, you may have to check the chrooted install of Postfix (if it installed that way).

You may have to apt-get --purge postfix and try a reinstall if nothing is working, and there are no debug errors listed.

I will say that the certificate issue is a fairly major one. For me, I can't install new certificates, as dovecot/postfix want to use the snakeoil ones, and I can't link or specify in either dovecot.conf or dovecot-postfix.conf.

I think that it should be fairly easy to install new certs, but apparently not. 

The 9.04 documentation should also reflect that the dovecot-postfix install uses the dovecot-postfix.conf for configuration and NOT the dovecot.conf.

SSL certs should also be easier to change out, or maybe we're doing something wrong?

---

