---
title: "Can someone give me some tips for setting up a mail server?"
date: 2013-08-23
forum: Server Platforms
---

### Post by Matthew_Snyder on 2013-08-23
I got my own domain registered and I wanted to setup my own email server with ubuntu.

I set up postfix as well as courier imap and pop3 and went through several setup guides to try and get my own mail server running.  Unfortunetly, parts of it do not work.  I can send and receive email, but security features (SSL, TLS) do not work.  I have gone over numerous guides, and I still just have no clue why.

I can get plain text starttls to work on my outgoing server, but I can't get any security (TLS, SSL) to work on my incoming mail server.  My log files don't seem to be any help, they just say user disconnected for unknown reasons when I try to setup a mail client with TLS or SSL on the incoming side.

Am I correct in thinking that Postfix is supposed to support incoming mail server security?  I installed the libsasl2-2, sasl2-bin, and libsas12-modules for the security and followed guides to get them to work, but they just don't.

When I try and get thunderbird or outlook to connect to the incoming mail server with ssl or tls, it always fails.  The autoconnect features always settle on unsecured incoming mail settings.

Am I supposed to get some other program for the incoming side of things?  Can someone drop me a clue?

---

### Post by Habitual on 2013-08-23
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)
may help you on the way.

---

### Post by CharlesA on 2013-08-23
Check this out.
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

I used it to help me set up my mail server on a Debian box, but it was written for Ubuntu 12.04.

---

### Post by nerdtron on 2013-08-24
Our mail server was up in less than 30 mins. Postfix, courier, spamassassin, amavisd and roundcube webmail. It has support for SSL by default and works for thunderbird and outlook.
After it is setup I just edited some config files to make it fit for our company. Goodluck on yours :)

And remember to install it on a FRESH install of ubuntu 12.04. Try it on a VM and see how it works.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

