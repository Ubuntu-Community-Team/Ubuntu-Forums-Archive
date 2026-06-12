---
title: "Postfix and Saslauthd"
date: 2005-04-12
forum: Server Platforms
---

### Post by asdf_46 on 2005-04-12
I am setting up postfix to use saslauthd with pam for e-mail authentication. I just can't find where the smtpd.conf file needs to be. In other distros it is /usr/lib/sasl2/, and I read somewhere that for debian it was /etc/postfix/sasl/.

Also the only package I saw with saslauthd was in universe. Am I going about this the wrong way?

Thanks for all the help,
      John

---

### Post by alastair on 2005-04-12
Is postfix and postfix-tls installed?

postfix-tls - TLS and SASL support for Postfix

Check the README :

/usr/share/doc/postfix/README.Debian

and, for Postfix, there is a good web site :

[http://www.postfix.org](http://www.postfix.org)

and a great mailing list.

---

### Post by shufla on 2005-04-18
Hello,

/etc/postfix/sasl/smtpd.conf
And do not forget to add postfix to sasl group ```
sudo adduser postfix sasl
```.

Best regards,
Luke

---

### Post by zirpu on 2005-05-18
One thing that I did not see in this thread is that postfix is
chroot'd to /var/spool/postfix

So, to get it to work, I had to edit /etc/defautls/saslauthd and
put:
PARAMS="-m /var/spool/postfix/var/run/saslauthd"

and of course do:  mkdir -p /var/spool/postfix/var/run/saslauthd

After that, all worked well.

---

### Post by cbqwinner on 2005-06-15
Thank you so much for that last tip.  I've been beating my head against a wall trying to get saslauthd to work right.  Amazing that this is the only place I've found that nugget of info after searching for 3 days.

---

### Post by cartman on 2005-06-25
[QUOTE=cbqwinner]Thank you so much for that last tip.  I've been beating my head against a wall trying to get saslauthd to work right.  Amazing that this is the only place I've found that nugget of info after searching for 3 days.[/QUOTE]
 Also remember you need to so

chown -R root:sasl /var/spool/postfix/var/run/saslauthd

---

