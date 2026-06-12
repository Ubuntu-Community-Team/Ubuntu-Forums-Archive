---
title: "warning message"
date: 2013-08-22
forum: Server Platforms
---

### Post by joe672 on 2013-08-22
when restarting apache 2 i get the message
> [warn] The Alias directive in /etc/apache2/apache2.conf at line 240 will probably never match because it overlaps an earlier Alias.



line 240 is

> Alias /phpmyadmin /usr/share/phpmyadmin

any help is appreciated

---

### Post by Habitual on 2013-08-22
```
grep Alias /etc/apache2/apache2.conf
```output please?

---

### Post by joe672 on 2013-08-22
> **Habitual said:**
> ```
grep Alias /etc/apache2/apache2.conf
```output please?


Alias /phpmyadmin /usr/share/phpmyadmin

alias in red

---

### Post by Habitual on 2013-08-22
bizarre. 
Someone else who knows Ubuntu's http file structure better than I will be along to offer some assistance.

Don't do anything drastic. :)

---

### Post by CharlesA on 2013-08-22
phpmyadmin should have added a conf file to Apache. Did you add that Alias yourself?

---

### Post by joe672 on 2013-08-22
> **CharlesA said:**
> phpmyadmin should have added a conf file to Apache. Did you add that Alias yourself?

maybe mate, i really cant remember.. i jumped into the deep end when doing all this, everything is working ok, i only seen this message while trying to setup another website. i wouldnt have known about it if i didnt need to restart apache2

---

### Post by CharlesA on 2013-08-22
Seeing as it is a [warn], I don't think it will hurt anything to leave it alone, especially if everything is working now.

You could try commenting out the alias in apache2.conf and restarting apache and seeing it the warn goes away and if it does, see if you can access phpmyadmin ok.

---

### Post by joe672 on 2013-08-22
ok thanks

---

