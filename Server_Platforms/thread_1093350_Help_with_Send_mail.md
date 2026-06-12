---
title: "Help with Send_mail"
date: 2009-03-11
forum: Server Platforms
---

### Post by alexv305 on 2009-03-11
Hello everyone. I recently setup my own Ubuntu 8.10 on an old machine I had sitting around. I installed the desktop edition not the server edition since I'm not completely comfortable with the gui-less server core.

Anyways, my problem is this. I installed Apache, PHP, and MySQL. Everything is working great. PHP is working MySQL is working and has a forum on it now, but I can't seem to get any type of form mailer to work in PHP. I have tried many scripts and have had no success. Do I need to setup a mail server?

When I use the phpBB mass mail within the forums it says mail sent, but I never receive anything.
It does the same for any other type of PHP mail script.

Thanks.

---

### Post by albandy on 2009-03-11
install exim4

---

### Post by alexv305 on 2009-03-11
Thats all I have to do? Just install it and thats it? No configuring?

---

### Post by albandy on 2009-03-12
Well, If it's a developer machine you don't need to configure nothing, the exim4 mail server it's listening at port 25 and working.

But if you are planning to use it in a server machine it will require more configuration, securizing it, specifiying mail domains, ....

Another option it's to use sendmail, but requires more configuration and it's a bit difficult.

---

