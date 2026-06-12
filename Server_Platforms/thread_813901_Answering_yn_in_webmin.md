---
title: "Answering y/n in webmin"
date: 2008-05-31
forum: Server Platforms
---

### Post by Strychnine45 on 2008-05-31
When I run a command in webmin that requires me answering y/n, I cant seem to answer, when I type y and run, it tries to run y as a command and not the reply to the question y/n

Anyone help?

---

### Post by quelx on 2008-05-31
the console in webmin is **non**-interactive, only programs that display information and do not need input will execute properly.

you need to SSH into the box to actually interact with console applications.

check out [http://www.webmin.com/standard.html](http://www.webmin.com/standard.html) and the **telnet.wbm.gz** module on that page.

---

### Post by Strychnine45 on 2008-05-31
Sorry for being a noob, okay im in webmin and have the ssh login up.  What are the user and pw ?

I have tried my login I am using for webmin, etc, and that doesnt work...

---

### Post by quelx on 2008-05-31
Hmmm, there seems to be a problem with the SSH/Telnet module I suggested.

Remove it and try this one (I tried it first this time)

[http://www.webmin.com/download/modules/ssh2.wbm.gz](http://www.webmin.com/download/modules/ssh2.wbm.gz)

---

### Post by Strychnine45 on 2008-05-31
That worked, you are a gentleman, a scholar, and a judge of good character

---

### Post by windependence on 2008-05-31
> **Strychnine45 said:**
> Sorry for being a noob, okay im in webmin and have the ssh login up.  What are the user and pw ?

I have tried my login I am using for webmin, etc, and that doesnt work...

The user ID and password will always be a user on the system. It can be any user, and you probably should not log in as root. Of course with sudo set up, you can't anyway. :)

-Tim

---

