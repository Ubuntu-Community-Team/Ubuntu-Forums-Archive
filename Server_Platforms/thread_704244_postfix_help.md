---
title: "postfix help"
date: 2008-02-22
forum: Server Platforms
---

### Post by rahuljk2002 on 2008-02-22
I am using postfix 2.4 server with my ubuntu 7.10.i have configured postfix server with it.I want my all mails going out of mailserver should go to hold queue expect the local mails which should deliver to its local user.i have make /etc/postfix/header_checks  file in which /^Received: / Hold  and then in /etc/postfix/main.cf i have made header_checks = regexp:/etc/postfix/header_checks parameter.
With this all my Mails are put into hold queue.Please help me out.

Thanks

---

### Post by rahuljk2002 on 2008-02-23
no one can help me in this issue.Please help me out i am not able to solve this out.:(

---

### Post by HermanAB on 2008-02-23
Hmm, specialized questions like this should be posted on the Postfix mailing lists:  [http://www.postfix.org/lists.html](http://www.postfix.org/lists.html)

---

### Post by thekat on 2008-02-24
> **rahuljk2002 said:**
> I am using postfix 2.4 server with my ubuntu 7.10.i have configured postfix server with it.I want my all mails going out of mailserver should go to hold queue expect the local mails which should deliver to its local user.i have make /etc/postfix/header_checks  file in which /^Received: / Hold  and then in /etc/postfix/main.cf i have made header_checks = regexp:/etc/postfix/header_checks parameter.
With this all my Mails are put into hold queue.Please help me out.

Thanks

The first thing that comes to mind...
What do your maillogs tell you..
- Second do you have the relayhost set up as most ISPs (I am assuming you have a residential account and not busisness) do not allow outbound
port 25, only outbound port 25 through your ISP smtp gateway.

hth
tk

---

### Post by Mr. C. on 2008-02-24
> **rahuljk2002 said:**
> i have make /etc/postfix/header_checks  file in which /^Received: / Hold  and then in /etc/postfix/main.cf i have made header_checks = regexp:/etc/postfix/header_checks parameter.
With this all my Mails are put into hold queue.Please help me out.

header_checks/body_checks apply to *ALL* mail.  You cannot use these checks to do what you want.

You can use restrictions classes to do what you need.  See:

[http://www.postfix.org/RESTRICTION_CLASS_README.html](http://www.postfix.org/RESTRICTION_CLASS_README.html)

MrC

---

