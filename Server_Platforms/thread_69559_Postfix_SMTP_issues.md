---
title: "Postfix SMTP issues"
date: 2005-09-27
forum: Server Platforms
---

### Post by dcostelloe on 2005-09-27
The good news: I'm almost there!
Squirrelmail now works. I figured how to access the admin screens. Have to generate a file called admins and place it in the /var/www/squirrelmail/plugins/administrator/admins

Add your accounts to be admin:

Example:
[email]david@mydomin.com[/email]
root


I do managed to have the following issues:

Postfix reports all is well then I get these in the queue:

connect to 127.0.0.1 [127.0.0.1]: read timeout

Can't seem to nail this one down any ideas?
:cool:

---

