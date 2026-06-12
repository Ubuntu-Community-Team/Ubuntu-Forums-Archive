---
title: "Help setting up email server"
date: 2012-08-11
forum: Server Platforms
---

### Post by jpcjr92 on 2012-08-11
Hi all,

I am looking for any assistance I can get with my project. I have registered a domain (costguy.com) with Dyn and signed up for dyn dns standard since my charter account is dynamic. I am wanting to install postfix/dovecot/squirrelmail to go along with apache.

Are there any simple guides to do thi? I have looked and gotten samba, webmin, and apache functional but can't figure out the email portion.

If I need to give anymore info, I would be glad to and thanks for any help.

---

### Post by jpcjr92 on 2012-08-11
I have now resetup my Ubuntu server checking LAMP, SAMBA, openssh this time and postfix works. but when I send an email is shows up as [email]user@mail.domain.com[/email] instead of [email]User@domain.com[/email]

Does anyone know how to resolve this?

---

### Post by kennethconn on 2012-08-11
[http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

---

### Post by jpcjr92 on 2012-08-12
Thanks for the link. Postfix is somewhat functional part of it is my ISP though (no reverse DNS)

I don't know if I need to start a new thread, but is there any reason that the DNS server quits. I had set my nameservers to the dyn dns that I am paying for and stopped looking up names. I could ping it but that was it.

I switched to my ISPs (charter) DNS and all is well again.

---

### Post by kennethconn on 2012-08-12
Are you running the update client with the dyn dns?

---

### Post by jpcjr92 on 2012-08-12
I am not.

I thought the Dyn DNS servers they gave me kept my domain updated. My bad. I will install the update client now.

Thanks for your help.

I ended up using this guide to make all my email functional:

[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p6](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3-p6)

---

