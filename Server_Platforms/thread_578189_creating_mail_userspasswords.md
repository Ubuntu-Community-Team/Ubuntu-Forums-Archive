---
title: "creating mail users/passwords"
date: 2007-10-17
forum: Server Platforms
---

### Post by xIke on 2007-10-17
I followed the excellent tutorial to setup a mail server from this link: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html).  I was wondering about the next step, though...how can I set the passwords that users will use to check their emails?  I assume that right now if I get an email at [email]bob@mdomain.com[/email], it will be archived correctly, but how can I set the password for bob so that he can login via imap or pop3?

Thanks.

---

### Post by foxylad on 2007-10-17
Try adding Bob as a user. You probably don't want to give him shell access to the server, so do something like **sudo adduser --shell /bin/false --no-create-home bob**. Then give him a password with **sudo passwd bob**.

---

### Post by xIke on 2007-10-17
Thanks for the response.

The imap server isn't accepting that username/password combo...  I'm using mbox's to store mail, if that makes any difference.  I don't know how to check this via telnet, so I'm simply putting the information into a mail client and trying it.

Any suggestions?

Thanks.

---

### Post by xIke on 2007-10-19
Hm.  I seem to have that working now.  My postfix server bounces back any email to it though.  Not sure how to troubleshoot that.

---

