---
title: "configuring postfix to use external smtp server"
date: 2008-11-23
forum: Server Platforms
---

### Post by boneill3 on 2008-11-23
Hello and thank you for helping me out with this!

I currently have postfix set up to use gmail smtp server for outgoing mail. I set this up because yahoo was not taking my emails since it is coming from a residential ip.

Would it be possible to use a external smtp server like smtp.gmail.com but have the outgoing emails not use the gmail login for the from field.

So I want to send mail as [email]root@ubuntu.com[/email] for example, but it's sending as [email]brian@gmail.com[/email]

is this possible or should I just create a new gmail account?

Thanks!

---

### Post by boneill3 on 2008-12-07
Is there any info I can give to get an answer to this? Anyone know if this is possible? Thanks.

---

### Post by troyready on 2008-12-07
I don't believe this is possible with gmail. All mail authenticated with your user name on their server will be sent "FROM" that username.

I relay my mail through AT&T's mail servers, and they don't do this.

---

### Post by hictio on 2008-12-07
You should ask you ISP, it is pretty likely that they have an SMTP server that you can use, configuring your the Postfix setup on your box to send all the outgoing email thru that server.
On the Postfix's config file, look for the option:

```

relayhost = 

```

Add the server's hostname that your ISP tell you, and restart Postfix to make the change active.

Usually these SMTP servers have a limit, or a cap, if you try to send more than X amount of emails per minute, it is pretty common to ban the offending IP address.

---

### Post by ekrack on 2008-12-07
I can send staright from my box using DDNS

Received-SPF: neutral (google.com: 68.XXX.XXX.85 is neither permitted nor denied by best guess record for domain of [email]ekrack@postfix.homelinux.com[/email]) client-ip=68.XXX.XXX.85;
Authentication-Results: mx.google.com; spf=neutral (google.com: 68.XXX.XXX.85 is neither permitted nor denied by best guess record for domain of [email]ekrack@postfix.homelinux.com[/email]) smtp.mail=ekrack@postfix.homelinux.com

I better start reading
[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

---

