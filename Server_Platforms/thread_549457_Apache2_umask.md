---
title: "Apache2 umask"
date: 2007-09-12
forum: Server Platforms
---

### Post by Gammell on 2007-09-12
Howdy,
I used to run Gentoo on a personal server, but after installing Ubuntu on my laptop,  I also switched the server over to Ubuntu in June or so. The transition was a little hectic, but I learnt a lot about Linux in the process and everything's been humming along fine all summer... Except for *one* little annoyance, umask settings in apache2.conf. In Gentoo I was able to use the umask keyword to set the file permission settings for the www-data user that apache ran as, it was as simple as:
```
user www-data
group www-data
umask 002
```
and any files created through apache2 would happily be 775. However since switching to Ubuntu,  using the umask keyword only results in:
```
* Restarting web server apache2
Syntax error on line 127 of /etc/apache2/apache2.conf:
Invalid command 'umask', perhaps misspelled or defined by a module not included in the server configuration
```
As far as I know, I hadn't enabled a module to use the umask keyword, but at this point, I can't be absolutely certain (and it easily could have been a module that was enabled by default in Gentoo). I've tried googling, various capitalizations of "umask" and reading the apache2 documentation but haven't found anything, can anyone help? I just hope it's not a compile-time option ;) Thanks.

---

### Post by sukibabee on 2007-09-15
the apache2ctl script starts apache, and calls on /etc/apache2/envvars for custom environment variables.

So add "umask 002" to /etc/apache2/envars and restart Apache.

---

### Post by Gammell on 2007-09-15
That does the trick, thank you kindly.

---

### Post by jdmelton on 2008-04-28
Thanks sukibabee.

I had the same problem and this fixed it on Apache 2.2.6.

---

