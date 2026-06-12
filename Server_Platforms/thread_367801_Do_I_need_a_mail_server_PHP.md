---
title: "Do I need a mail server? PHP"
date: 2007-02-22
forum: Server Platforms
---

### Post by kramerkeller on 2007-02-22
I have a server running at home with virtual hosting, FTP access, and most everything for administrating some websites.  

However, I have some code that uses php's mail() function.  I know I need a mail transfer agent to utilize this function.

So I began to install postfix and next thing I know things are getting pretty complicated.

Although, a mail server would be cool, is it necessary to configure everything just to have some automatic emails sent out?

Do I need pop3 smpt and everything?

Please help and thanks in advance.

---

### Post by Mr. C. on 2007-02-22
Where do you want to deliver the mail ? Just locally?

Postfix's default is to allow sending, so if you're just sending locally, there should be no difficulty.

PHP uses the sendmail command (which can be either Sendmail or postfix's compatibility sendmail).   This is specified in php.ini (sendmail_path = /usr/sbin/sendmail -t -i)

You don't need a POP server running if you are just reading email from the local machine.  Again, where do you want your email sent?

SMTP is just the language, so to speak, that the mail agents speak.  Your PHP mail interface however will use the sendmail command, not SMTP, to do its job.  The sendmail interface will just drop the mail into one of Postfix's queues, where it will take care of the delivery.

---

### Post by Keneo on 2007-02-26
I used the option: use smarthost during configuration of postfix
and the smarthost is my isp :)

f.ex smtp.my.isp

works good

only way I could get it to work, since my isp blocks port 25 to the outside world

---

