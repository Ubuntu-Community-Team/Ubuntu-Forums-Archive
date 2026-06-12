---
title: "Hardy, Postfix + Dovecot SASL?"
date: 2008-10-27
forum: Server Platforms
---

### Post by needhelpplease on 2008-10-27
I'm having a maddening problem here.  I'm trying to get Postfix to use the Dovecot SASL mechanism.  I've done everything exactly according to the [setup instructions](http://www.postfix.org/SASL_README.html#server_dovecot), and yet I keep getting:

```
Oct 27 21:26:10 cl-t145-020cl postfix/smtpd[32580]: warning: SASL: Connect to /var/run/sasl/sasl-client failed: No such file or directory
Oct 27 21:26:10 cl-t145-020cl postfix/smtpd[32580]: fatal: no SASL authentication mechanisms
```

And this is when the file clearly exists and clearly has the right perms on it.  Somehow Postfix can't connect to it.

I've Googled all day for this and found other people having the same problem but I can't figure this out.  Any ideas?

---

### Post by HermanAB on 2008-10-27
Hmm, you are not going to like my suggestion, but you can install Citadel in about 20 minutes and it just works.  I don't use Postfix anymore - it is just way too much hassle.

---

### Post by MJN on 2008-10-28
Your issue is likely that Postfix is running in a chroot environment and hence as far as it is concerned the system root is /var/spool/postfix/ and not /
 
Have a look at [https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL) for an implementation likely more suited to your needs (I've never used this myself, but one would hope it is accurate - and equally applicable to Hardy).
 
Mathew

---

### Post by needhelpplease on 2008-10-30
> **MJN said:**
> Your issue is likely that Postfix is running in a chroot environment and hence as far as it is concerned the system root is /var/spool/postfix/ and not /

Absolutely right.  Thanks for the suggestion.  Here's some more info also on [setting up Postfix with TLS, Dovecot, SpamAssassin](http://chiralsoftware.com/linux-system-administration/ubuntu-postfix-imap-dovecot-setup.seam), etc.

---

