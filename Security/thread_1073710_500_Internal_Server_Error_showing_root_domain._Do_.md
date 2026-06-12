---
title: "500 Internal Server Error showing root domain. Do not want."
date: 2009-02-18
forum: Security
---

### Post by Swerve1000 on 2009-02-18
Hi,

I have a shared hosting account with Hostgator using CPanel and am hoping someone can help me.

I am creating a site in an addon domain, but when I view a page which doesn't exist I get the following:

> **Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  [email]webmaster@**myaddondomain.maindomain.com[/email]** and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
 Additionally, a 500 Internal Server Error error was encountered while trying to use an ErrorDocument to handle the request.
  Apache/2.2.11 (Unix) mod_ssl/2.2.11 OpenSSL/0.9.8i DAV/2 mod_auth_passthrough/2.1 mod_bwlimited/1.4 FrontPage/5.0.2.2635 Server at **[www.addondomain.com]("http://www.addondomain.com")** Port 80I need to prevent people finding out my main domain name, so need to find out how I can prevent this from occurring.

Many thanks for any kind assistance.

---

### Post by cariboo on 2009-02-18
If I remember correctly you have to setup the admin address in your virtual domain file, so wouldn't it be easy to setup the admin email address in the virtual host file?

Jim

---

### Post by Swerve1000 on 2009-02-18
Many thanks for helping me cariboo907 :)

Since this is a shared hosting account, I don't think I have access to what you are describing, I've had a look through the CPanel control panel. 

I tried deleting the old email address and making a new one, not using [email]me@addondomain.maindomain.com[/email], I used [email]me@addondomain.com[/email], but it still shows the same.

Any other ideas ?

:)

Thanks!

---

### Post by cariboo on 2009-02-18
The only other place I can see an email address is in /etc/apache2/sites-enabled/@000-default, so check any configuration files in that directory.

Jim

---

