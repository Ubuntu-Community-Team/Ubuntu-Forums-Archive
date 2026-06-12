---
title: "Mail"
date: 2007-03-30
forum: Server Platforms
---

### Post by noone123 on 2007-03-30
Hi, i have seen some info about postfix, sendmail and mailman. These are some mail servers that should send to my Mail Box a letter, lets says from my web. Guess what... it wont send! The thing is that i use apache+php5 and i have tried some mail servers and i don't know how to configure them so they can send me a letter. If you must know i need just to make work the "Forgot my password" option in my Phpbb forum. I have no experience whit mail servers so i don't even know what i need to type in php.ini. Please be nice to me :)

---

### Post by elst on 2007-03-31
If you are using Ubuntu Server, then the supported email service is Postfix. Once it's  installed, applications running on the same system can use it to dispatch emails (this is sometimes called "sendmail delivery" or similar, because Sendmail was basically the first email program). I don't know much about PHP, but the online manual at php.net will probably help you with setting up your php.ini correctly.

---

### Post by noone123 on 2007-04-01
its just in php.ini, i don't know what to type... he asks me the address  of smtp, username, password(but thats for win32) and mail_path... i don't know what to type there if im using postfix.

---

### Post by elst on 2007-04-01
If it needs a network address then use 127.0.0.1, since the mail service is on the same system. Again, if you are unsure, the docs should tell you what these options mean.

---

