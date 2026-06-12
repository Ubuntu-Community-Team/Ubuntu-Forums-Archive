---
title: "remote smtp server for web applications (relay not permitted)"
date: 2006-09-02
forum: Server Platforms
---

### Post by thommSK on 2006-09-02
I think the Thread says all. I have a web server and i need to send e-mails from php. But I can't have a smtp on localhost. In php.ini is option "SMTP = server", but it's only for windows. And of course, relay is not permitted (i know it from email logs). So I need that e-mail go direct to the ISP smtp machine.. google doesn't help..](*,) ](*,) :( Please, how can i do that?

thanks for all posts.

p.s.: i'm sorry for my english.

---

### Post by Uluen on 2006-09-03
Just curious, why isn't relay permitted? If it's from the same network it's usually ok. And why can't you have SMTP on the same host?

Is this a local testing server?
Does it have a real hostname? If your ISP can't do reverse DNS, it might complain about relaying, I've seen that before.

---

### Post by foxmulder on 2006-09-03
Relaying is not permitted to prevent spam!

---

### Post by thommSK on 2006-09-03
Yes, foxmulder's right. Relaying is not permitted to prevent spam. So,  I can have smtp on localhost, but i can't send email direct to the world(ISP's firewall). And when i set relay host in postfix, in logs is relay not permitted...:confused:

---

### Post by Uluen on 2006-09-03
[QUOTE=thommSK]Yes, foxmulder's right. Relaying is not permitted to prevent spam.[/QUOTE]I know relaying isn't allowed from *other* hosts, that's why I asked.

I can run a local SMTP here and use my ISP as relay because they know I'm on their network, see?

---

### Post by Miademora on 2006-09-03
You need to find out how to authenticate against your ISP to be allowed to relay E-Mail.

Most common options are SMTP-AUTH and POP-Before-SMTP.

Id advise to use a class like [PHPMailer]("http://phpmailer.sourceforge.net/") for authentication and almost transparent relaying of mails regardless of the authenticationmethod you have to use.

---

