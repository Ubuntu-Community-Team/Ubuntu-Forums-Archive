---
title: "Sendmail Issues"
date: 2010-07-14
forum: Server Platforms
---

### Post by Stroik52 on 2010-07-14
Hi everyone, 
I'm new at configuring sendmail and I'm working on configuring sendmail as a gateway for our MS Exchange server. Mail seems to relay correctly for the most part.

I'm having an issue that I am unsure how to fix though. Say the exchange mail server is mail.mydomain.com and the sendmail gateway is smtp.mydomain.com, when I send mail to [email]user@mydomain.com[/email], my message will bounce back with the message "user address required", if I send mail to [email]user@mail.mydomain.com[/email] though, mail goes through without a hitch.

Is there a way to make mail.mydomain.com = mydomain.com? I've been using virtusertables to compensate for this but that doesn't sound like a good solution. There must be some other way to do this?

Thanks in advance

---

### Post by mysteron on 2010-07-16
Put this into your virtusertable

```
@mydomain.com	%1@mail.mydomain.com
```

and run cmd:

```
sudo /etc/init.d/sendmail reload
```

this will make sendmail relay email for user@mydomain.com to the user user@mail.mydomain.com.


/mysteron

---

