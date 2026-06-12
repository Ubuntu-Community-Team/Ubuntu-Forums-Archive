---
title: "Can't login to Courier. chdir failed"
date: 2011-05-01
forum: Server Platforms
---

### Post by larskhansen on 2011-05-01
Hi,

I'm trying to setup a Postfix+Courier+SquirrelMail Mailserver on an Ubuntu Server.

I can see that the mails are getting to the right folders, but I'm not able to login :(

The mail.info log says:

May  1 21:52:59 nmh authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=lkh/, address=lkh, fullname=lkh, maildir=/var/mail/virtual/lkh/, quota=<null>, options=<null>
May  1 21:52:59 nmh authdaemond: Authenticated: clearpasswd=XXXXXXX, passwd=XXXXXXXXX
May  1 21:52:59 nmh imapd-ssl: lkh: chdir(lkh/) failed!!
May  1 21:52:59 nmh imapd-ssl: error: No such file or directory
May  1 21:52:59 nmh imapd-ssl: LOGIN FAILED, user=lkh, ip=[::1]
May  1 21:52:59 nmh imapd-ssl: authentication error: No such file or directory

The /var/mail/virtual/lkh folder exists with /tmp /new etc.. folders.

The folders are owned by "virtual: postfix" with a 775 permission.

Why the heck aren't I able to login?

Regards,

Lars Hansen

---

