---
title: "Postfix / Dovecot Problems"
date: 2007-12-31
forum: Server Platforms
---

### Post by cypsteel on 2007-12-31
I am having a problem with my Postfix > Dovecot installation.  I have used webmin to administer with mostly defaults.  The problem I am having is this:

When I migrated their old cpanel backups, it put all their waiting mail in a file called /var/mail/username@domain.com

Dovecot is working fine with this, I can access webmail and also pop mail from this box.  

However, postfix is delivering all new mail to a file called /var/mail/username-domain.com.  Thus its not getting received by the users.  

In virtual domains under the postfix configuration in webmin, I can see the translation of   [email]username@domain.com[/email] ----->  username-domain.com   but if I try to edit this to [email]username@domain.com---->username@domain.com[/email] or just delete this mapping period, postfix bounces the mail back to sender with "username" is not on this server.

Thanks for any help in advance,
Justin

---

### Post by HermanAB on 2007-12-31
Yup, you should restrict things to POSIX portable characters.  Some programs are OK with funny characters, some not.  So get rid of those appersats and don't use underscores either.  in mail systems, appersats are delimeters, just like a space.

Dashes should be fine, dots will have problems with some things.  Sudo for example don't like either dashes or dots.

Sooo, the general rule is: Don't use funny characters in names.

Cheers,

Herman

---

### Post by cypsteel on 2007-12-31
These mail accounts were moved off of reseller account on another server. Their usernames were [email]username@domain.com[/email] .  I was trying to make it a transparent migration to the new server without having them change their username.

---

### Post by HermanAB on 2007-12-31
Well, as I said - some things will work and some won't, depending on your platform.  If you deviate from POSIX, then you are on your own.  RedHat Linux doesn't even allow dots in usernames even though that is allowed under POSIX portable rules.  

Making the appersats work on the new machine would require hacking several utilities such as useradd, usermod, chown and chmod, to name a few and in this case Postfix itself too.  It isn't worth it, since you then have to maintain these utilities forever, unless you have huge numbers of users - been there myself.

Cheers,

Herman

---

### Post by rsw686 on 2008-01-02
Since we are talking about virtual mail you should be able to store the mail in any format. The login will should be username@domain regardless of the directory structure. For example on my box I store the mail in /var/mail/domain/username and they log in with username@domain.

Why not use the below command to change the old mail files to username-domain. Then update the dovecot config to reflect this.

for file in *; do mv "$file" $(echo "$file" | sed 's/@/-/g'); done

---

