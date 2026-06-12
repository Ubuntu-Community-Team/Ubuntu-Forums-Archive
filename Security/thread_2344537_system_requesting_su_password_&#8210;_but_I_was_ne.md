---
title: "system requesting su password &#8210; but I was never asked to set one up!"
date: 2016-11-26
forum: Security
---

### Post by engine on 2016-11-26
When I upgraded to 16.0.4 a couple of months ago I was not &#8210; as far as I remember &#8210; asked to set a [new] root password. Now I have to install java, and su is asking for a password. I have tried both the super-user passwords I remember, without success.

I'm hoping I will not have to reinstall the entire system, watching it at every stage in case a dialogue for "set su password" flashes up … but is there anything else I can do?

Thanks in advance for helping get me out of this fix!

---

### Post by steeldriver on 2016-11-26
"su is asking for a password" - so what's asking for su? how exactly are you trying to install java?

---

### Post by engine on 2016-12-02
I hate this sort of question &#8230; trying to check and reproduce the problem, it's gone away :-{
Thanks for answering, all the same!

---

### Post by kpatz on 2016-12-02
Ubuntu doesn't use a root password by default - when an installer or other program needs superuser privileges it asks for the password to your user account, which you would have set when you installed Ubuntu.  Provided you are part of the admin group it'll give you the privileges you need (and the account you created when installing will be).  Same thing when using sudo in the command line.

---

