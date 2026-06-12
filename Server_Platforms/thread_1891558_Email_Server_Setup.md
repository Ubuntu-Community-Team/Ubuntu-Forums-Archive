---
title: "Email Server Setup"
date: 2011-12-05
forum: Server Platforms
---

### Post by hgurol on 2011-12-05
I want to setup an email server on my ubuntu 11.10 vps using postfix, dovecot and mysql.

I have found a couple of guides about how to do it...
one of theme is here [http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.10-maverick](http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.10-maverick)

...and one another GREAT guide here...
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

However, all the guides I have found is for ubuntu 10.10 or for debian squeeze.

Im not able to follow those guides since the Dovecot version for all of those guides is 1.x, while my ubuntu 11.10 server have Dovecot version 2.x

The Dovecot configuration differs between version 1.x and 2.x, therefore Im not able to fully follow the guide and complete my setup successfully.

Does anyone knows a similiar guide which is written with Dovecot version 2.x in mind?  Or is there anyone willing to translate one of the above guides to version 2.x ?

Thank you so much...

---

### Post by maverickaddicted on 2011-12-06
Have you tried this -

[http://en.gentoo-wiki.com/wiki/Mail_server_using_Postfix_and_Dovecot](http://en.gentoo-wiki.com/wiki/Mail_server_using_Postfix_and_Dovecot)

[http://wiki2.dovecot.org/](http://wiki2.dovecot.org/)

---

### Post by hgurol on 2011-12-06
Dovecot wiki is just a documentation, which I need more than that. However the Gentoo link is more like an easy guide to follow.

Im gonna try that.
Thank you

---

### Post by collisionystm on 2011-12-06
[www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html)

---

### Post by Dry Lips on 2011-12-06
The best tutorial I've come across is by far this one: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
It is quite updated as well I assure you :)

---

### Post by hgurol on 2011-12-16
> **Dry Lips said:**
> The best tutorial I've come across is by far this one: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
It is quite updated as well I assure you :)

That's a GREAT tutorial. I wish it was using Dovecot 2.x instead of Courier.

Thank you so much...

---

### Post by moonpup on 2011-12-17
I find it funny when reading these forums that no one ever recommends reading the official ubuntu documentation, which is actually quite good...

[https://help.ubuntu.com/11.10/serverguide/C/email-services.html](https://help.ubuntu.com/11.10/serverguide/C/email-services.html)

---

### Post by HermanAB on 2011-12-18
I always thought that these forums are specially for people who refuse to read any documentation and prefer to do things the hard way...

---

### Post by lisati on 2011-12-18
> **HermanAB said:**
> I always thought that these forums are specially for people who refuse to read any documentation and prefer to do things the hard way...

:lolflag:

And there's also [https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)

---

### Post by hgurol on 2011-12-21
Official docs are far from being adequate(moonpup's link) or recent(lisati's link) !!

If you take a quick look at these guides at...
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)
(unfortunately its for debian sqeeze with Dovecot version 1.x, therefore Im not able to follow the guide step by step. It doesn't work with Ubuntu 11.10 as it is. And 11.10 comes with Dovecot version 2.x)

or

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
(Great and pretty recent guide but unfortunately it uses Courier IMAP instead of Dovecot and Im really looking for a Dovecot 2.x solution.)

None of official documentation comes close to these guides for a complete solution.


....but thanks anyway.

---

