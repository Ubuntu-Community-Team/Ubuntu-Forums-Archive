---
title: "apache2 restrict users to use suExec / shell_exec EXCEPT e.g. root or some other one"
date: 2010-10-18
forum: Server Platforms
---

### Post by windsxs on 2010-10-18
Hi,
I'm few steps from completing my hosting server, but I see a threat, that users can do e.g. ```
shell_exec('nano /var/www/<otherUsersSite>/public_html/index.php')
``` I is not good, because then they can see passwords to login database... BUT, I want to create registration form, using shell_exec or something similar by e.g. user "root" or "www". So the question is: HOW TO RESTRICT ALL USERS FROM USING THESE COMMANDS EXCEPT SOME, WHICH I WANT TO ALLOW? I think this could be reached by editing some configuration file or restricting user to use commands..
Thanks for advises in advance :)

---

