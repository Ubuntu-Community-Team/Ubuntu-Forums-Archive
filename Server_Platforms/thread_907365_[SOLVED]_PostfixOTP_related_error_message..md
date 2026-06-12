---
title: "[SOLVED] Postfix/OTP related error message."
date: 2008-09-01
forum: Server Platforms
---

### Post by cpetercarter on 2008-09-01
I have a website on a server running Ubuntu 6.06 server edition. Postfix is installed on the server.

The events log in my Control Panel contains frequent messages which read:

> OTP unavailable because can't read/write key database /etc/opiekeys: No such file or directory

I have done some google research which suggests that the error message is caused by the the absence of a One Time Password (OTP) package.One [post]("http://www.zimbra.com/forums/administrators/13627-otp-unavailable.html") suggests that there is a Debian bug and that the appropriate workround is to remove /usr/lib/sasl2/libotp.*

I am reluctant to take risks with my server, but I would like to get rid of this error message. Any advice or previous experience?

---

### Post by cpetercarter on 2008-09-03
Well, since no-one replied to my earlier post, I went ahead and backed-up/removed the libotp.* files from /usr/lib/sasl2. And the sky did not fall in, and the sun came up this morning, and my server and e-mails seem to be working normally, and there are no more error messages. So it seems to have been the right thing to do.

---

