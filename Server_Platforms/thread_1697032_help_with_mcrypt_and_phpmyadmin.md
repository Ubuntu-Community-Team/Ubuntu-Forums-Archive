---
title: "help with mcrypt and phpmyadmin"
date: 2011-02-28
forum: Server Platforms
---

### Post by equinox_ on 2011-02-28
I have searched for almost every solution on this forum about how to solve the:

Cannot load mcrypt extension. Please check your PHP configuration.

However, I can't solve this... I can't see mcrypt anywhere in phpinfo... what should I do? I have it included as an extension=mcrypt.so in the php.ini. I tried to purge it and install it again...

---

### Post by t3r0 on 2011-02-28
Hi,

You need to install it by running:
```

$*sudo apt-get install php5-mcrypt

```

Then you should remove the "extension=mcrypt.so" line from your php.ini since this will be extension will be included from "/etc/php5/conf.d/mcrypt.ini" like all other modules in debian/ubuntu distros.. 

Note: apache needs to be restarted after this.. 

- Tero

---

### Post by equinox_ on 2011-02-28
I actually did that and it still doesn't work

---

### Post by t3r0 on 2011-02-28
> **equinox_ said:**
> I actually did that and it still doesn't work

Have you made any configuration changes to php? 

And ensure that you have /etc/php5/apache2/conf.d symlinked to /etc/php5/conf.d and that /etc/php5/conf.d/mcrypt.ini exists...


- Tero

---

