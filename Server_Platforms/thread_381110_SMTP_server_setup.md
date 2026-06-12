---
title: "SMTP server setup"
date: 2007-03-10
forum: Server Platforms
---

### Post by Bachstelze on 2007-03-10
Greetings to everyone :)

So, here's the deal. I often connect to the net via public wifi hotspots and I have no SMTP sever I can connect to to easily send email. But I have a home server - running Dapper as my sig says - which can connect to my ISP's SMTP server.

The question is : could I use my ISP's SMTP via my home server to send mail wherever I am and if so, how do I set this up ?

---

### Post by Mr. C. on 2007-03-10
Sure, you can use your home system to send email.  It requires a more complex configuration to do securely.

First, does your ISP not provide you with the ability to connect to their mail server remotely?  I believe many do.  You simple need to configure your mail client to make the secure connection.

If this is not an option, let's go to the next step.

MrC

---

### Post by Bachstelze on 2007-03-10
Problem solved by doing a SSH tunneling :

```
ssh -L 2525:smtp.orange.fr:25 myhost.no-ip.org
```

and then setting 127.0.0.1:2525 as SMTP server in my mail client on my laptop.

Thanks nevertheless :)

---

### Post by Mr. C. on 2007-03-10
Perfect solution!  Nice work.

---

