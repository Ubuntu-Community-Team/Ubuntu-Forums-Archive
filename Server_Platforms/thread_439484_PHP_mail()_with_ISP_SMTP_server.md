---
title: "PHP mail() with ISP SMTP server"
date: 2007-05-10
forum: Server Platforms
---

### Post by noaktree on 2007-05-10
Hi,

I just installed Ubuntu Linux Server 7 on an "at home" dev box. I followed the [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704) tutorial except I didn't install bind or ISPConfig.

I installed postfix to run as SMTP but I am having problems getting my emails out of the queue when using the php function mail(). 

Anyway, I got the idea that I already have an SMTP to send emails with my ISP. I wonder if I can setup mail() to just use that server rather then sendmail.

Anybody?

---

### Post by noaktree on 2007-05-10
Thanks for looking. That didn't last very long at all. 

I've just discovered PHPMailer and it will let me use my ISP's SMTP.

Now I've just got to figure out how to remove the email servers I've setup and I'm good.

---

