---
title: "Email Server"
date: 2006-11-12
forum: Server Platforms
---

### Post by amitroy5 on 2006-11-12
I have Apache installed on my Ubuntu box and have mydomain.com that points to it. I have my website set up. However, I want to add email, so that [email]webmaster@mydomain.com[/email] works. I have a gmail account. I was wondering how I can forward any email sent to [email]webmaster@mydomain.com[/email] to [email]myname@gmail.com[/email]? Thanks!

---

### Post by damonc on 2006-11-12
This guide might be helpful: [How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/")

I haven't followed it myself (I plan to this week) but it seems quite comprehensive.

---

### Post by amitroy5 on 2006-11-12
I read the guide. This sets up a mail server. I just want something to forward emails.

---

### Post by rickyjones on 2006-11-13
Well, you DO want a mail server installed then... Example - you could install Postfix and configure it to forward emails to another server. I don't know how to do it, but I'm sure /someone/ has done it at one point or another.

---

### Post by MJN on 2006-11-13
Or you could delegate the DNS for your domain to someone like [www.zoneedit.com]("http://www.zoneedit.com") (free) and use their 'mail forwarding' service (might cost - not sure). You would of course configure your A records to point to your server for the web side of things.
 
Mathew

---

