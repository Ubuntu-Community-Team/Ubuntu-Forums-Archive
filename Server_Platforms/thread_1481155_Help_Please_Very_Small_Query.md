---
title: "Help Please Very Small Query"
date: 2010-05-12
forum: Server Platforms
---

### Post by sligoman on 2010-05-12
Hi all

Just a small enquiry. I am following a guide to help me setup postfix with mysql and have got to the stage in the setup guide that I am not sure about:

Edit the file /etc/aliases, making sure the "[COLOR="Black"]**postmaster" and "root**[/COLOR]" directives are set properly for your organization.

File: /etc/aliases

postmaster: root
root: [email]postmaster@yourdomain.com[/email]


What exactly am I changing postmaster: **root** and **postmaster@yourdomain.com** too

Thanks in advance

Liam

---

### Post by TheFuturian on 2010-05-12
I think they'd just be meaningful names.. i.e.

```
postmaster: John Smith
root: john@yourdomain.com

```
What guide are you following?

---

### Post by sligoman on 2010-05-12
Hi

Thanks for your reply

Yes the guide is [http://library.linode.com/GBqpaM]("http://library.linode.com/email/postfix/postfix-dovecot-mysql-debian-5-lenny") Configure Mail Aliases

It seems that getting the email side of the server is no easy task to complete when you are only a newbie to Linux

Thanks 

Liam

---

### Post by sligoman on 2010-05-13
> **TheFuturian said:**
> I think they'd just be meaningful names.. i.e.

```
postmaster: John Smith
root: john@yourdomain.com

```
What guide are you following?

OK I will go with what you suggest can always change it later if not correct..

Many Thanks

Liam

---

### Post by ruuden on 2010-05-13
this is just to make sure that mail from your system to the root user get to your local mail account. so you set up an alias like 

```
root: yourname
postmaster: yourname
```I don't think you need the @yourdomain part because it is defined in the /etc/postfix/main.cf file under the mydomain entry.

---

### Post by sligoman on 2010-05-13
Thanks ruuden

Will give it a go..

Regards

Liam

---

