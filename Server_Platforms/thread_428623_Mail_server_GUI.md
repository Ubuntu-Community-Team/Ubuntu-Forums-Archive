---
title: "Mail server GUI?"
date: 2007-04-30
forum: Server Platforms
---

### Post by Scooter7 on 2007-04-30
Hi, I've installed Postfix, and Dovecot, using this guide: [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html).

Coming from a Windows background (don't we all? ;)), I'm used to having a graphical interface to do things.   So, I'm wondering if there's a GUI frontend for these things.   Something that I can use to make users, domains, etc.   I don't mind using the terminal for things, but I do try to use a GUI when I can.

I tried phpMailAdmin, but I had problems with setting it up.

I'm using Ubuntu Feisty Fawn, Desktop edition.

---

### Post by madmetal on 2007-04-30
well i am not sure if this going to help you but give a look at webmin 
[http://www.webmin.com/](http://www.webmin.com/)

UAResolved.

---

### Post by az on 2007-04-30
> **Scooter7 said:**
> 
Coming from a Windows background (don't we all? ;)), 

No.

As for the GUI, this project may eventually lead to a nice set of GUI utilities for running a web/mail server:
[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)

It is a Google summer of code project and will be renamed to SOHObuntu.

---

### Post by Scooter7 on 2007-04-30
Thanks, guys.   I've downloaded Webmin, and it seems to be what I need - and more. ;)

It just might help with other problems I'm having, such as setting up Samba...

And I'll keep an eye on SOHObuntu.

Thanks again,

   ~Teh DS (Scooter7)

---

### Post by az on 2007-04-30
Webmin is no longer in the Ubuntu repositories because it is so badly broken it is not supportable.  It may work for some things, but YMMV.

---

