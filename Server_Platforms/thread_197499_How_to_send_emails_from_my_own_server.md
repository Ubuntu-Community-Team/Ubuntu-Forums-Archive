---
title: "How to send emails from my own server?"
date: 2006-06-15
forum: Server Platforms
---

### Post by pahbi on 2006-06-15
I am a complete newbie, but if someone could help me, I would really be greatful.

I'm trying to get away from Windows, after trying a couple different distro's, I decided on Kubuntu.  So far, everything has gone great, I can do everything I need to do, that I used to do with Windows.

But I have one nagging problem, email.

I would like to configure my laptop to use Mozilla Thunderbird, and to configure the laptop to be its own server when it sends out emails.

I tried the instructions at [http://help.ubuntu.com/ubuntu/serverguide/C/email-services.html](http://help.ubuntu.com/ubuntu/serverguide/C/email-services.html) and so far, Mozilla Thunderbird says its successfully sending messages, but when I check for the messages, nothing actually got sent.

If worse comes to worse, I can continue using yahoo mail, but it would just be sooooo cool to be able to send out emails from my laptops own email server.

If anyone could help, it would be greatly appreciated.
THanks,
- Pahbi

---

### Post by peanut butter on 2006-06-16
you will have to install postfix or another MTA, instructions can be found here:
[http://doc.ubuntu.com/ubuntu/serverguide/C/email-services.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/email-services.html")

---

### Post by peanut butter on 2006-06-16
oh sorry didnt look at the url of the guide that you used.

---

### Post by cyracks on 2006-06-18
What is in your log files ? (/var/log/mail.*)

---

### Post by Randomskk on 2006-06-18
Many email servers reject email from some IPs or from servers they cannot connect to, as well.
Also, you'd need a dedicated SMTP server listening on port 25 on a static IP that didn't have port 25 blocked (like a lot of ISPs do) for anyone to be able to reply.

---

