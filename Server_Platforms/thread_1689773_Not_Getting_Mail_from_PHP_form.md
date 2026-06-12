---
title: "Not Getting Mail from PHP form"
date: 2011-02-17
forum: Server Platforms
---

### Post by Captainnow on 2011-02-17
I have several forms created on my server. I'm running Ubuntu server 10.04. 

I was running Ubuntu server 10.10 up until Tuesday Night. I decided to go to Ubuntu Server 10.04 in favor of the long term support of it.

While running Ubuntu server 10.10 all my forms worked and would send the form data to my email without issue. 
Now after transfer the site to Ubuntu 10.04 I'm not getting any of the email messages. I have verified my email works by sending a test email directly to the account.

I'm wondering what I can do to troubleshoot this and resolve this issue. I'm pretty new to linux so I'm still learning.

Thank You,

---

### Post by rbishop on 2011-02-17
Is your server that is hosting the php forms also your mail server?

---

### Post by Captainnow on 2011-02-17
No. The machine hosting the php forms and the website isn't the mail server. It is sending the mail to a gmail account that have configured with my purchased domain name.

---

### Post by rbishop on 2011-02-17
Are you seeing the emails in the mail queue?  Have you verified the mail settings on the webserver?  You may want look at the old mail config and compare it to the new one.

Least that's my 2cents anyway.

---

### Post by Captainnow on 2011-02-17
How do I check the mail queue? I never changed any default settings on php mail handling on either 10.10 or 10.04. I just coded the PHP code to process and send the data to an email address.

---

### Post by koenn on 2011-02-17
forget the mail queue. 

look at your web server logs and see what it says when the mailer script is accessed or requested (increase verbosity on the logging if need be)

---

