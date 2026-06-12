---
title: "[SOLVED] sendmail EHLO"
date: 2008-08-08
forum: Server Platforms
---

### Post by cdenley on 2008-08-08
How can I change the hostname sendmail uses for the EHLO command? It keeps using EHLO localhost, and some SMTP servers don't like that. I at least need to make it use a valid name. If I could set it with a command-line argument, that would be great, but I couldn't find one in the manual.

```

Connected to mx1.comcast.net.
Escape character is '^]'.
220 IMTA03.westchester.pa.mail.comcast.net comcast ESMTP server ready
EHLO ubuntu.com
250-IMTA03.westchester.pa.mail.comcast.net hello [(MY IP)], pleased to meet you
250-HELP
250-SIZE 15728640
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 OK
MAIL FROM: anyone@yahoo.com
250 2.1.0 <anyone@yahoo.com> sender ok
EHLO localhost
250-IMTA03.westchester.pa.mail.comcast.net hello [(MY IP)], pleased to meet you
250-HELP
250-SIZE 15728640
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 OK
MAIL FROM: anyone@yahoo.com
550 5.1.0 <anyone@yahoo.com> sender rejected
Connection closed by foreign host.

```

---

### Post by windependence on 2008-08-08
I would install postfix as it is a drop in replacement for sendmail, and sendmail is a bear to configure and maintain. It's also not as secure as Postfix. DO NOT uninstall sendmail, just install the postfix package.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

-Tim

---

### Post by cdenley on 2008-08-08
I think I actually was using postfix, but didn't realize it for some reason. That explains why my sendmail configuration changes didn't seem to have any affect. I just changed myhostname in the main.cf file, and now it works.

---

### Post by windependence on 2008-08-08
Hehe, we all do this from time to time, you know get in a hurry and forget what we did. It's all good. Glad you got it fixed. :)

-Tim

---

