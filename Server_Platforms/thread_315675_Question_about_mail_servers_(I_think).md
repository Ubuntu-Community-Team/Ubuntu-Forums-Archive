---
title: "Question about mail servers (I think)"
date: 2006-12-09
forum: Server Platforms
---

### Post by ironfistchamp on 2006-12-09
Hey all


I am starting a new business (or am part of it) and we need to be able to send and receive mail from our domain name. I am not sure who the name is registered with (I didn't do that, will find out asap). How easy would this be to do. I have just used mailx to send an email from a user at the domain name (not illegal is it as we own the domain name and it was going to my private email address) so I don't think that is a problem. All I really need to know how is to receive and emails sent back. 

Any help would be great.

Thanks

Ironfistchamp

---

### Post by saiman on 2006-12-09
Hi, 

the way I see it - you need to point your domain's MX record to your mail server s IP address. Then you must set up a mail server, which handles mail sending and receiving.

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)

I run postfix and dovecot. Works fine for my needs.

---

### Post by ironfistchamp on 2006-12-10
Thanks for the reply I shall check that out :)

---

### Post by technodigifreak on 2006-12-12
> **saiman said:**
> Hi, 

the way I see it - you need to point your domain's MX record to your mail server s IP address. Then you must set up a mail server, which handles mail sending and receiving.


That's basically all that needs to be done.  You'll want to have the mail server set up before you point the MX record to it, so you don't just drop those emails into a bit-bucket somewhere.  Also, allow 24-48 grace period for the domain information to fully propagate. So if the email addresses are active, you may want to make the change on a Friday evening, and everything should be great by Monday morning!

---

### Post by ironfistchamp on 2006-12-12
Excellent thanks for the reply. That makes a lot of sense.

Thanks again

Ironfistchamp

---

