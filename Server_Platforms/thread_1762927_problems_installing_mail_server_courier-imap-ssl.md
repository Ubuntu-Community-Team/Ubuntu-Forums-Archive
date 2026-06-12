---
title: "problems installing mail server courier-imap-ssl"
date: 2011-05-19
forum: Server Platforms
---

### Post by n0tiz on 2011-05-19
Hi,

I am busy installing a mail server. I am using the following tutorial:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

The following error came up while configuring and I am in desperate need of help.
 * ERR: /etc/courier/imapd.pem missing
The error shows up when I want to stop/restart/start courier-imap-ssl.
I tried to remove and reinstall the package but it gives the same error...

If you need more information, config files, ... feel free to ask.

Thank you in advance!

---

### Post by n0tiz on 2011-05-19
Got it fixed, got to remove courier-imap-ssl by using:

sudo rm /var/lib/dpkg/info/courier-imap-ssl.prerm

and:

sudo dpkg --remove --force-remove-reinstreq courier-imap-ssl

and next reinstalled it all :)

---

