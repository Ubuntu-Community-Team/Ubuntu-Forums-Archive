---
title: "Php mailing"
date: 2006-03-20
forum: Server Platforms
---

### Post by Compact on 2006-03-20
The emails coming from apache with php appears to come from the right domain, but in the message headers it say that the message comes from [email]apache@localhost.loca[/email]ldomain How can I change it? I think I have changed the server hostname to the domain name.

---

### Post by localzuk on 2006-03-20
Take a look at [http://uk2.php.net/manual/en/function.mail.php](http://uk2.php.net/manual/en/function.mail.php) and also take a look in your httpd.conf file for the server name.

---

### Post by Compact on 2006-03-21
Php is sending the mail from the correct email, the emails not come from [email]apache@localhost.loca[/email]ldomain, is in yhe received header it puts that email comes from [email]apache@localhost.loca[/email]ldomain. Perhaps is the configuration of sendmail?

---

### Post by localzuk on 2006-03-21
Have you checked the apache httpd.conf file?

---

### Post by Compact on 2006-03-22
I cant find anywhere in the httpd config file where i can specify that information. Thanks!

---

### Post by Compact on 2006-03-22
I have just find in ubuntu wiki how to reconfigure postfix and now the server is sending the mails well.
Thank you very much for your help and sorry about my bad english.

---

