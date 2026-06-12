---
title: "Ubuntu send mails from address"
date: 2013-01-09
forum: Server Platforms
---

### Post by fernandoch on 2013-01-09
Hello,

I just setup postfix to send emails, but when I send a mail I get it as from [email]root@mylocalhost.com[/email]

How can I change this from? I bought a domain name and I would like to be able to send mails as [email]support@mydomain.com[/email]

Thank you.

---

### Post by chadk5utc on 2013-01-09
> **fernandoch said:**
> Hello,

I just setup postfix to send emails, but when I send a mail I get it as from [email]root@mylocalhost.com[/email]

How can I change this from? I bought a domain name and I would like to be able to send mails as [email]support@mydomain.com[/email]

Thank you.

I think youll find what your looking for here
[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)

---

### Post by fernandoch on 2013-01-09
The answer is in here [http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

I have to change the myorigin variable.

I will try it, thank you.

---

### Post by fernandoch on 2013-01-09
This is good to change the domain name, but how can I specify the whole address I want? for example [email]support@mydomain.com[/email] ??? I was only able to get [email]root@mydomain.com[/email] :(

Thank you.

---

### Post by volkswagner on 2013-01-09
How are you sending mail?

---

### Post by fernandoch on 2013-01-09
With wordpress, I think it manages all that for me and no need to virtual users... and multiple domains. Is that correct?

---

