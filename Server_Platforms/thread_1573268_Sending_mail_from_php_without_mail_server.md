---
title: "Sending mail from php without mail server?"
date: 2010-09-12
forum: Server Platforms
---

### Post by johan.alfa on 2010-09-12
Hello,

I will setup a LAMP server 10.04.
I had 8.04 until last week and that worked perfect for my needs.

No I would like apache and php send mail without setting up a mail server. 

In xampp one can just change a line in php.ini
SMTP = smtpserver 

With 8.04 I used a simple mail program but I can't remember the name anymore.  

Any tips?

Regards,

Johan

---

### Post by kamicc on 2010-09-12
are You searching for solution like this [http://www.cyberciti.biz/tips/howto-php-send-email-via-smtp-authentication.html](http://www.cyberciti.biz/tips/howto-php-send-email-via-smtp-authentication.html)  ? :)

or simply add 

```

[mail function] 
; Setup for Linux systems 
sendmail_path = /usr/sbin/sendmail -t 
sendmail_from = me@myserver.com

``` 

into Yours PHP.ini, [mail function] section and restart apache :)

---

### Post by johan.alfa on 2010-09-12
Hello kamicc

No it was a simple program I had to install on the server.
I did not need sendmail.

Regards,

Johan

---

### Post by hictio on 2010-09-12
> **johan.alfa said:**
> Hello kamicc

No it was a simple program I had to install on the server.
I did not need sendmail.

Regards,

Johan

I bet you mean ssmtp ;) Amazing little program, free, and it is on the repositories.

[Sending Email From Your System with sSMTP](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by johan.alfa on 2010-09-12
> **hictio said:**
> I bet you mean ssmtp ;) [/url]

Hello,

It was not this one but it looks like it will work also.
Thanks,

Regards,

Johan

---

### Post by johan.alfa on 2010-09-12
Hello,

Found it in the ubuntu archives in my own messages.

Program is nullmailer

Don't know if I can still use is with ubuntu.

Regards,

Johan

---

### Post by cj13579 on 2010-09-12
nullmailer works on Ubuntu. It's in the repositories:

```
sudo apt-get install nullmailer
```

---

