---
title: "Help with Mail Server"
date: 2018-02-11
forum: Server Platforms
---

### Post by rduhb on 2018-02-11
Can I setup my mail server at the same time my email is being hosted by my hosting service?  Do I have to suspend my email with them first?

---

### Post by lisati on 2018-02-11
Yes, you are able to set up your own mail server before you suspend your hosting service. When you have your own mail server set up, you can then arrange for messages you want to keep to be copied to your own server before you suspend your hosted server.

---

### Post by volkswagner on 2018-02-11
It's recommended to have both working side by side. You can have multiple SMTP sender's. Make sure your server can reliably send email before you even change DNS MX records for switching receive function to your new mail server.

---

### Post by TheFu on 2018-02-13
> **volkswagner said:**
> It's recommended to have both working side by side. You can have multiple SMTP sender's. Make sure your server can reliably send email before you even change DNS MX records for switching receive function to your new mail server.

Have both running as volkswagner suggests. There is a priority field in the MX record, lower gets tried first by remote SMTP servers and if it isn't available, the higher ones are tried, in order.  It is a best practice to have multiple SMTP servers accepting email for your domains. This way, no email is dropped.  In theory, SMTP delivery should be attempted multiple times and I **Know** that used to be over 4 days, but now it seems to be more like 4 hrs for retry before a failure is returned to the sender.

Having multiple SMTP servers is also handy for doing server maintenance.

---

### Post by rduhb on 2018-02-24
> **TheFu said:**
> Have both running as volkswagner suggests. There is a priority field in the MX record, lower gets tried first by remote SMTP servers and if it isn't available, the higher ones are tried, in order.  It is a best practice to have multiple SMTP servers accepting email for your domains. This way, no email is dropped.  In theory, SMTP delivery should be attempted multiple times and I **Know** that used to be over 4 days, but now it seems to be more like 4 hrs for retry before a failure is returned to the sender.

Having multiple SMTP servers is also handy for doing server maintenance.


Server is up and running with Postfix and Dovecot.  I tried configuring a test account in Thunderbird, but it appears it's trying to connect to my hosting service servers and not to my mail server.  Need some help with next steps.  I'm using "mail.mydomain.com" as the server name in Thunderbird.  The mail log doesn't show any login attempts.  Any help is appreciated.

---

