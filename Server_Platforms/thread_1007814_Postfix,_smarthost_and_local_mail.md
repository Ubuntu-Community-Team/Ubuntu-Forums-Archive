---
title: "Postfix, smarthost and local mail"
date: 2008-12-10
forum: Server Platforms
---

### Post by BSK on 2008-12-10
Hi,

I'm using Ubuntu 8.04.1 LTS on a server and I need to configure Postfix.

I want it to relay any external emails to my isp's smtp server and still route my localhost emails properly.

My localhost emails are mainly from scripts and daemons.

I was able to get it running fine in the "Internet with Smarthost" mode but my problems comes from the two following things :

1. /etc/mailname which is used by myorigin in postfix's main.cf file
2. the mydestination setting from postfix's main.cf file

My isp will reject all emails if /etc/mailname doesn't contain a valid domain, so I entered a valid domain and I entered the following for mydestination :

mydestination = myserver, myserver.local, localhost, localhost.local

If I run postfix like that the local mail for users have to use "username@localhost" to work, if I omit the "@localhost" postfix will append the domain from /etc/mailname automatically and route then to the smarthost.

So for now I added the domain from /etc/mailname to mydestination like so :

mydestination = myserver, myserver.local, localhost, localhost.local, myvaliddomain.com

So like this local mail is working but sending any external email to myvaliddomain.com is impossible since postfix treats them as local mail.

Is there any way to avoid making myvaliddomain.com local only ?

Thanks!

---

### Post by hyper_ch on 2008-12-11
I think you are lacking the proper setup of relaying through your ISP.

(1) add those lines to you your /etc/postfix/main.cf config:
```

smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_always_send_ehlo = yes
relayhost = [smtpauth.bluewin.ch]:587

```
Replace *[smtpauth.bluewin.ch]:587* with your ISP. My ISP only lets smtp traffic go through port 587 and not default port 25. So I had to enclose it in [] brackets and tell it the port. You just might use somethign like:
```

relayhost = smtp.yourisp.com

```

(2) Create the /etc/postfix/saslpasswd file and add
```

smtpauth.bluewin.ch     LOGIN:PASSWORD

```
of course use your ISPs smtp server instead and set the login and password accordingly. Login for me is the whole email address like:
```

smtpauth.bluewin.ch     username@bluewin.ch:PASSWORD

```

(3) make a map file out of the saslpasswd file
```

sudo postmap /etc/postfix/saslpasswdd

```

(4) finally restart postfix
```

sudo /etc/init.d/postfix restart

```

Now when you try to send email through your postfix server it will then relay it through you ISP.

---

### Post by MJN on 2008-12-11
As a quick-and-dirty fix you could simply set your origin to being an unused sub-domain of your domain.
 
For example:
 
```
myorigin = local.myvaliddomain.com
append_at_myorigin = yes
mydestination = myserver, myserver.local, localhost, localhost.local, local.myvaliddomain.com
```
 
The result of this should be as follows:
 
EHLO/HELO will be fully qualified as **$myhostname.local.myvaliddomain.com**
Mail sent to **user** will be rewritten as **user@local.myvaliddomain.com** and be delivered locallly.
Mail sent to **user@myvaliddomain.com** will be delivered via the smarthost
Mail sent to **user@anyotherdomain.com** will be delivered via the smarthost
 
..which is presumably exactly what you want?
 
Mathew

---

### Post by BSK on 2008-12-11
MJN: It works! Thanks!

hyper_ch: My ISP doesn't use authentification for SMTP, and the relaying already works for all other domains so I don't need sasl...maybe I'm wrong.

---

