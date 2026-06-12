---
title: "mail() in xampp server"
date: 2011-07-19
forum: Server Platforms
---

### Post by npsabari on 2011-07-19
I am a newbie to php.
I installed apache xampp server(latest version).
Everything works fine except the mail() function.
Whenever I try to send email from my php scripts(with host:'localhost'), it fails.
My doubt is : Is it possible to send emails using xampp
server(localhost)... and if yes, How?
If not, atleast can I connect to some webpages in the internet or
servers on other machines, from my xampp server?

Thanks in advance for any help..

PS:  I did not make any changes to the php.ini file.

---

### Post by ruffEdgz on 2011-07-19
So the mail function doesn't really have anything to do with your php.ini or any other configuration related to the web part: [http://php.net/manual/en/function.mail.php](http://php.net/manual/en/function.mail.php)

In this manual, it forgets to place a dependency that it probably should talk about which is your server needs to have postfix/sendmail setup and working.

You will have to make sure either application is working on your server before the mail() function on php can work.

postfix for Ubuntu - [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

