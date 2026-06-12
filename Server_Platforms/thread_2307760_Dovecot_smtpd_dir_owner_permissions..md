---
title: "Dovecot smtpd dir owner permissions."
date: 2015-12-28
forum: Server Platforms
---

### Post by Turrrbulence on 2015-12-28
Hey Ubuntu Forums !
Here is a question about UNIX groups and virtual mail.

While trying to set up an email server with postfix dovecot and mysql but I've had issues with vmail configuration.
It's giving me back the following error:

Error reading configuration: stat(/etc/dovecot/dovecot.conf) failed: Permission denied (euid=150(vmail) egid=8(mail) missing +x perm: /etc/dovecot, dir owner missing perms) lda: Fatal: Internal error occurred. Refer to server log for more information. )
Dec 28 12:16:53 ip-172-31-21-40 postfix/smtpd[4938]: idle timeout -- exiting
^C
root@mail:/etc/dovecot/conf.d# vim 10-mail.conf
root@mail:/etc/dovecot/conf.d# grep vmail /etc/passwd
vmail:x:150:8:Virtual maildir handler:/var/vmail:/sbin/nologin


I made sure that the first_valid_uid setting in 10-mail.conf was set to 150.

What do you think is stopping dovecot(as vmail) from accessing config files ?

Turrr

---

### Post by darkod on 2015-12-28
You didn't post the permissions of /etc/dovecot. To me that message sounds like vmail user has no execute/search rights on /etc/dovecot.

> euid=150(vmail) egid=8(mail) missing +x perm: /etc/dovecot

But I can't be sure if this behavior is normal or not. It looks to me like the setup/config is not standard. The vmail user shouldn't need further permissions on the file/folder structure. What it does need are access/search rights so it can look into your user/mailbox DB, or something like that. Dovecot is running as root I believe, no? No need dovecot to be running as vmail...

---

### Post by Turrrbulence on 2015-12-28
> **darkod said:**
> You didn't post the permissions of /etc/dovecot. To me that message sounds like vmail user has no execute/search rights on /etc/dovecot.



But I can't be sure if this behavior is normal or not. It looks to me like the setup/config is not standard. The vmail user shouldn't need further permissions on the file/folder structure. What it does need are access/search rights so it can look into your user/mailbox DB, or something like that. Dovecot is running as root I believe, no? No need dovecot to be running as vmail...

Hi darkod,

The dovecot directory doesn't have any permissions and will not save modifications done to them. 

root@mail:/usr/sbin# ls -ld /etc/dovecot
d--------- 4 vmail dovecot 4096 Dec 28 09:56 /etc/dovecot
root@mail:/usr/sbin# chmod -R o-rwx /etc/dovecot
root@mail:/usr/sbin# ls -ld /etc/dovecot
d--------- 4 vmail dovecot 4096 Dec 28 09:56 /etc/dovecot
root@mail:/usr/sbin# 

Turrr

---

