---
title: "want webserver and mail"
date: 2008-04-25
forum: Server Platforms
---

### Post by roas300 on 2008-04-25
Hi

I love Ubuntu, I do not know much about linux, but I am wanting to have my own web server and my own e-mail server

I have DSL through a extremely small rural phone company and they do not have anyone on staff that has a clue about there DNS server.  I may have a remote chance that one of the owners can put mu FQDN and an MX record on there DNS, But it may be better for me to run DNS.

I have a fqdn, and 2 static ip's.  do I have to run bin9 to have an e-mail server (postfix) and run apache web server?

Should I be using a LAMP server?

Does anyone have a set of instructions. I have printed out a load of stuff on bind9.  I rebuilt my ubuntu server for the XXXX time to start clean, I am sure I have a syntax error that is preventing bind from starting,  If I do not need bind, it may be easer to do this.

Thank you for your assistance, even with people that are so new to this.

Steve

---

### Post by kidders on 2008-04-26
Hi there,

It's not normally a good idea to run a mail server on a domestic DSL connection. Aside from the fact that they don't tend to be terribly reliable, many SPs block messages from addresses in domestic IP pools. (There is effectively a 100% probability that mail from a domestic IP will be spam.) That's not to say you shouldn't try it ... but it may not work out as well as you'd like. On the other hand, running your own web server has *lots* of benefits.

> **roas300 said:**
> do I have to run bin9 to have an e-mail server (postfix) and run apache web server?No, but you do need *somebody* to store DNS records for you. Unless you know exactly what you're doing, that shouldn't be you though. Unless you want to run a DNS server purely for private use on your own local network, I would suggest ignoring Bind completely.

> **roas300 said:**
>  Should I be using a LAMP server?That's up to you. LAMP is a very commonly used combination, but there are plenty of other options.

---

### Post by FakeOutdoorsman on 2008-04-27
> **roas300 said:**
> Should I be using a LAMP server?

That depends on what you're planning on using it for.  If you're going to use php and mySQL, and/or host multiple domains then Apache is just fine.  If you're going to host small, static pages, then lighttpd and thttpd are both excellent lightweight alternatives.  These are all in the Universe repository.

The Ubuntu Wiki has some good information on installing [Apache, mySQL, and PHP]("https://wiki.ubuntu.com/ApacheMySQLPHP").

---

