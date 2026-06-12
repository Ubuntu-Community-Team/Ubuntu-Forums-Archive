---
title: "apache and sendmail, 3 questions"
date: 2007-01-17
forum: Server Platforms
---

### Post by Howlin' Hobbit on 2007-01-17
I develop websites (mainly my own) on my older laptop running Ubuntu 6.06. I recently installed Apache (to replace a different webserver) and even more recently, sendmail. Both of these start at bootup and both, but especially sendmail, seem to eat my minimal RAM (256meg) up and slow various things down. Plus bootup is slowed way down when sendmail starts, eventually telling me that it's not running (though when I run any of my php code that sends mail, the mail gets sent... I dunno what's up there).

I don't dev each and every day and don't always test mail-equipped bits when I *am* working on a site, so my first two questions are:

1. How do I prevent Apache and sendmail from starting at bootup? They're not in the "run at startup" part of Sessions.

2. Once I've got question 1 under control, how do I start and stop Apache and sendmail manually?

Lastly...

3. Is there some lighter-weight mail sending thing that php's "mail" function will work with? I don't really need something that's listening all the time for incoming mail and such, just something to send mail to my address as I'm testing various things for my site.

If I've left out any important info please let me know.

Thanks much!

---

### Post by souki on 2007-01-17
hello,

some quick explanations, home it will help

> **Howlin' Hobbit said:**
> 
1. How do I prevent Apache and sendmail from starting at bootup? They're not in the "run at startup" part of Sessions.


these processes are started from the init system, not from your gnome session
that means they are started before you enter your gnome session

in order to control your init processes, you don't really need to understand how it works but you need a tool (runlevel editor)

I use two tools, from the universe repository :
- rcconf (console based)
- bum (gtk based)

bum is really cool and you can start/stop your sevices from it
from a console, you have to do :
```
sudo /etc/init.d/sendmail stop
sudo /etc/init.d/sendmail start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
```> 
2. Once I've got question 1 under control, how do I start and stop Apache and sendmail manually?
see previous point

> 
3. Is there some lighter-weight mail sending thing that php's "mail" function will work with? I don't really need something that's listening all the time for incoming mail and such, just something to send mail to my address as I'm testing various things for my site.
you don't need the smtp server to be running, you just need the "sendmail" binary on your system and a working network configuration (dns is important here)
the mail() function execute the sendmail binary which is responsible of the sending

you can also tune your apache config to minimize the amount of ram used
important parameters are in /etc/apache2/apache2.conf in this section :

```
<IfModule prefork.c>
StartServers         5
MinSpareServers      5
MaxSpareServers     10
MaxClients          20
MaxRequestsPerChild  0
</IfModule>
```you can lower StartServers, MinSpareServers and MaxSpareServers
but you'd better ask

---

