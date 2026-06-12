---
title: "how to do I enable fsockopen() on ubuntu 8.04"
date: 2008-09-13
forum: Server Platforms
---

### Post by kustomjs on 2008-09-13
Hi Guys
I need to know how to enable fsockopen() onto my server can anybody help?

and also I am getting this error:
Warning: fsockopen() [function.fsockopen]: SSL operation failed with code 1. OpenSSL Error messages: error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol in /class.smtp.php on line 122

Warning: fsockopen() [function.fsockopen]: Failed to enable crypto in /class.smtp.php on line 122

Warning: fsockopen() [function.fsockopen]: unable to connect to ssl://smtp.gmail.com:25 (Unknown error) in /class.smtp.php on line 122
Message was not sent
Mailer Error: SMTP Error: Could not connect to SMTP host.

---

### Post by windependence on 2008-09-14
Can you post the code you are using to call the fsockopen() function?

You should have this line in your php.ini file:

```
allow_url_fopen = On
```

The php.ini file should be at /etc/php5/apache2/php.ini. If not, you will have to create it by downloading a template file. If I remember right there is one somewhere in the php installation. If not, you can get one at the php web site.



-Tim

---

