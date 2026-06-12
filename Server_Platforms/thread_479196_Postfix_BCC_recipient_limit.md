---
title: "Postfix BCC recipient limit"
date: 2007-06-20
forum: Server Platforms
---

### Post by ozpak on 2007-06-20
Sorry to post about Postfix in a Ubuntu forum - but this is killing me!

Server running Ubuntu Edgy / php5 / postfix for smtp

A website on the server is using php to send a mailout to users.

It is using the imap_mail(); function to send a single email - with a huge number of BCC recipients (> 10,000) on it (not good I know but they don't want to change script).

Postfix is limiting the number of recipients for the single email to 1000. 

Does anyone know the configuration parameter I need to put in main.cf to get postfix to allow more ?

I have already tried:
- smtpd_recipient_limit
- default_recipient_limit
- default_extra_recipient_limit
- smtpd_recipient_overshoot_limit

---

### Post by Mr. C. on 2007-06-20
Yes, postfix does limit recipients to 1000.

The main.cf var to use is smtpd_recipient_limit.  But its more complex.

You might want to ask this on the postfix list, as this is one of the details areas that needs expertise and explanation.  There are serious issues of bounce handling.  This is an area where list management software is required.  See:

[http://tinyurl.com/yp5bo8](http://tinyurl.com/yp5bo8)
[http://tinyurl.com/25w8o3](http://tinyurl.com/25w8o3)

MrC

---

