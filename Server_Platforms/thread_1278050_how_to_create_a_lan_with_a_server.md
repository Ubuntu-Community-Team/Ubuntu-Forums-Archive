---
title: "how to create a lan with a server"
date: 2009-09-29
forum: Server Platforms
---

### Post by pnewbie on 2009-09-29
Hi! everybody,
       I am new to ubuntu so please help me. I am trying to setup a server using Ubuntu 8.04 edition for my LAN having 10 computers. We have a switch and a broadband connection. Most of systems in lan are using windows platform while only two peoples including me are using Ubuntu. We want to set up the server using ubuntu 8.04 lts edition while others are insisting on windows 2000 ......so please help me.

---

### Post by nandemonai on 2009-09-29
> **pnewbie said:**
> Hi! everybody,
       I am new to ubuntu so please help me. I am trying to setup a server using Ubuntu 8.04 edition for my LAN having 10 computers. We have a switch and a broadband connection. Most of systems in lan are using windows platform while only two peoples including me are using Ubuntu. We want to set up the server using ubuntu 8.04 lts edition while others are insisting on windows 2000 ......so please help me.

What do you need the server to do?

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by pnewbie on 2009-09-29
Thanks for asking....... the server will be used for this purpose:
1) creation and testing of web based application
2) file sharing between systems using different platforms
3) if we can create a local mail server using this

Thanks again

---

### Post by nandemonai on 2009-09-29
> **pnewbie said:**
> Thanks for asking....... the server will be used for this purpose:
1) creation and testing of web based application
2) file sharing between systems using different platforms
3) if we can create a local mail server using this

Thanks again

1) Apache / MySQL / PHP
2) SAMBA / NFS
3) Postfix / Dovecot etc

Ubuntu Server will handle all that and more ;)

See the above link in my previous post.

---

### Post by theozzlives on 2009-09-29
> **nandemonai said:**
> 1) Apache / MySQL / PHP
2) SAMBA / NFS
3) Postfix / Dovecot etc

Ubuntu Server will handle all that and more ;)

See the above link in my previous post.

You can setup Ubuntu Desktop to act as a server. You'll need to use SAMBA to share with Windows computers. I wouldn't use Server Edition unless I was running a REAL server machine.

---

### Post by Grenage on 2009-09-29
This may sound off, but if two people want Linux and eight want Windows, wouldn't it be more logical to go for the majority?

---

### Post by nandemonai on 2009-09-29
> **Grenage said:**
> This may sound off, but if two people want Linux and eight want Windows, wouldn't it be more logical to go for the majority?

I don't see any logic in paying for software when something else can do the job fine, if not better for free.

If we were talking AD / GP then maybe but for a simple file, web and email server I don't see much point.

The admin will also learn some new skills in the process which is always a plus :)

---

### Post by Grenage on 2009-09-29
Considering you can't buy 2000 any more, I have to assume they already have a copy :)


Don't get me wrong, I'd rather use Linux!

---

### Post by Iowan on 2009-09-29
> **Grenage said:**
> This may sound off, but if two people want Linux and eight want Windows, wouldn't it be more logical to go for the majority?Guess that depends who's paying the bill (or is it Bill)? :P

---

