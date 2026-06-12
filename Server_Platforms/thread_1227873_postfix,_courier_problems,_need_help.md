---
title: "postfix, courier problems, need help"
date: 2009-07-31
forum: Server Platforms
---

### Post by csurlee on 2009-07-31
Hi everybody!

first i want to tell you what kind of services i use:

-postfix
-courier
-mysql
so i use postfix with mysql backend

i have some problems with my postfix or courier server 

i cannot connect to the IMAP server with SquirrelMail, the message i get is "ERROR: Connection dropped by IMAP server."
i have created the users i sent the first message.
 
i think i have everything UP and working properly, but still its not working

i found something in the mail.err log file:

```
Jul 31 12:47:13 revistafirme imapd: authentication error: Input/output error
Jul 31 12:48:31 revistafirme pop3d: authentication error: Input/output error
Jul 31 12:49:02 revistafirme last message repeated 10 times
Jul 31 12:49:17 revistafirme last message repeated 7 times
Jul 31 12:59:24 revistafirme imapd: authentication error: Input/output error
Jul 31 12:59:32 revistafirme imapd: authentication error: Input/output error
Jul 31 13:17:11 revistafirme pop3d: authentication error: Input/output error

```

thanks 

best regards.

PS.: if it helps i used this howto from [http://articles.slicehost.com/2008/9/2/mail-server-postfix-and-mysql-installation](http://articles.slicehost.com/2008/9/2/mail-server-postfix-and-mysql-installation)

---

### Post by csurlee on 2009-07-31
i find the problem ...

---

### Post by confusedstingray on 2009-08-01
this a howto i started with and it works 

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04)

---

### Post by noway2 on 2009-08-01
So what was the problem an dhow did you fix it?

I had a lot of trouble sending email with Squirrelmail that appeared to be a problem with authentication, though I could read mail just fine.  What fixed it for me was changing the settings so that it used "sendmail" instead of SMTP.  This threw me off because I am not otherwise using Sendmail, but I do have postfix as an SMTP server.

---

### Post by HermanAB on 2009-08-01
Note that the 'sendmail' program that comes with Postfix, is not the real Sendmail, it is a little utility that serves as an interface between programs that expect to work with Sendmail and Postfix.  In other words, your little sendmail program on your machine is actually Postfix!

Hope that explains the confusion a little.

---

### Post by noway2 on 2009-08-07
Yes this explains things, thank you very much.

While attempting to help in another post of Dovecot, I noticed that it had a reference to "sendmail" and this deepend my confusion.  

Then I read your kind response this morning and all became clear.

---

