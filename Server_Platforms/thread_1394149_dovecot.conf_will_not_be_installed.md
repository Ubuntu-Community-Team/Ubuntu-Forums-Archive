---
title: "dovecot.conf will not be installed"
date: 2010-01-30
forum: Server Platforms
---

### Post by gypsumwolf on 2010-01-30
I was trying to set up an e-mail server. I was trying postfix with dovecot and then removed them and I deleted the dovecot.conf. I decided to try exim4 and that went smoothly. So next I tried to reinstall dovecot and it will not install the config file. To try and fix it I have use the 'purge' to remove it and that didnt solve the problem.

I ran

> apt-get install dovecot-imapd dovecot-pop3d


and here is a snip of the output:

> ..
Selecting previously deselected package dovecot-pop3d.
Unpacking dovecot-pop3d (from .../dovecot-pop3d_1%3a1.1.11-0ubuntu11_i386.deb) ...
Setting up dovecot-imapd (1:1.1.11-0ubuntu11) ...
Can't open /etc/dovecot/dovecot.conf: No such file or directory.

Setting up dovecot-pop3d (1:1.1.11-0ubuntu11) ...
Can't open /etc/dovecot/dovecot.conf: No such file or directory.


---

### Post by artheus on 2010-01-31
you can download it from here

[http://www.dovecot.org/doc/dovecot-example.conf](http://www.dovecot.org/doc/dovecot-example.conf)

_IN TERMINAL_
first browse to the dovecot directory (def. /etc/dovecot/) and then use the command
```
wget http://www.dovecot.org/doc/dovecot-example.conf
```
to download the file.

then rename the file with this command
```
mv dovecot-example.conf dovecot.conf
```

Cheers,
Artheus

---

### Post by artheus on 2010-01-31
And one more thing!

Have you tried the command
```
sudo apt-get install dovecot
```
???

Cheers,
Artheus

---

### Post by gypsumwolf on 2010-01-31
> **artheus said:**
> And one more thing!

Have you tried the command
```
sudo apt-get install dovecot
```
???

Cheers,
Artheus

Of course!!!!

I will try the file probably tomarrow to see if it works. thanks!

---

