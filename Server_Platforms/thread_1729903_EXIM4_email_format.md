---
title: "EXIM4 email format"
date: 2011-04-15
forum: Server Platforms
---

### Post by spindler on 2011-04-15
I am having some issues with EXIM4.   One of the issues is the way email is sent out.

I tested the EXIM4 by sending an email out to my gmail account.    the email address looked like the following.

[email]www-data@server.com[/email]

the server.com is listed in the mailname file and this is a dumby variable... not an actual domain name.

What I do not like is the www-data  name in the email address.  www-data is a system name on my server. 

Does anyone know how I can change EXIM4 to use a dumby user instead of the www-data user name?  

I was hoping to have the server send emails as  [email]no-reply@server.com[/email]

---

