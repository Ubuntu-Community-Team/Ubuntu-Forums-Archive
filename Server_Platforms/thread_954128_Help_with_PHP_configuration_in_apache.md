---
title: "Help with PHP configuration in apache"
date: 2008-10-20
forum: Server Platforms
---

### Post by DFord425 on 2008-10-20
I want to be able to send email in using PHP. I read online that i have to change the php.ini file if i want to use a remote server. Does anyone know where the file is that i have to change in kubuntu. I know that .ini files are used in windows, right?

---

### Post by scragar on 2008-10-20
```
/etc/php5/apache2/php.ini
```you will need root perms, so run something like:
```
kdesu kwriter /etc/php5/apache2/php.ini
```replacing kwriter with the text editor of your choice.

You need to set:
**SMTP** to your server
**smtp_port** to the port

I can't be 100% sure this will work though, I've never had to do this myself.

---

### Post by DFord425 on 2008-10-20
I appears i need to use sendmail. Is it possible to setup sendmail to use my google account?

---

