---
title: "tasksel mail-server; it ain't working"
date: 2009-01-25
forum: Server Platforms
---

### Post by ChrisBuchholz on 2009-01-25
Hi,

I have setup an Apache2 server with PHP5 and MySQL+PHPMyAdmin which are fully functionel, but I also want to be able to send mails from PHP, so I've ran sudo *tasksel install mail-server*, but it ain't working.

I have restarted apache and everything, but it doesn't work. PHP doesn't say it can send the mail, but I never recieve 'em in my inbox either.

How do I fix it?

---

### Post by HermanAB on 2009-01-25
Install nullmailer and forward mail to your ISP mail server:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

Cheers,

Herman

---

### Post by ChrisBuchholz on 2009-01-25
> **HermanAB said:**
> Install nullmailer and forward mail to your ISP mail server:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

Cheers,

Herman

Can you please come with some more details? Especially because I only will need to send a few e-mails from php to check if things are working before they get on the ftp. I just need the most simplistic setup which just works almost out-of-box.

---

### Post by cariboo on 2009-01-25
Nullmailer is in the Intrepid repositories, so there is no need to try and convert it from an rpm to deb.


Have a look at this [thread]("http:///ubuntuforums.org/showthread.php?t=56077") for a hwoto.

Jim

---

