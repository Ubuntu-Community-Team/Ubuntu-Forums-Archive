---
title: "Need help setting up server"
date: 2010-12-22
forum: Server Platforms
---

### Post by clay7 on 2010-12-22
Hello,

I recently just got a Linode and I've seen several tutorials about how to set up name-based virtual hosts, but I don't think those apply to me. All I want is one domain on my server.

Here's what I've done: 
[LIST]
[*]Installed LAMP via **sudo tasksel install lamp-server**
[*]Configured SSL
[*]Installed Webmin
[/LIST]

Here are my questions:

[LIST=1]
[*]Is only one domain on my VPS still considered a virtual host? (from my OS's perspective, not from the host company's)
[*]How should I configure ** /etc/apache2/sites-available/default**?
[*]As for email, I need the PHP scripts to be able to generate emails, and I need online email access like squirrelmail. I don't need to download email (e.g., Outlook). Will Postfix be all I need (in addition to squirrelmail)?
[/LIST]

Thank you!!

---

