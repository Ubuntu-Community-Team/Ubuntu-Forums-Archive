---
title: "i installed  phpmyadmin, but i get &quot;404 not found&quot;"
date: 2009-08-09
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-08-09
i just installed using the code:

```

sudo apt-get install phpmyadmin

```

but when i got to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) i just get 404 file not found

i then uninstalled it using 

```

sudo apt-get remove phpmyadmin

```

then installed again from the synaptic package manager, but still i get 404

---

### Post by AliTabuger7 on 2009-08-09
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

Did you add this to /etc/apache2/apache2.conf?
```
Include /etc/phpmyadmin/apache.conf
```

---

### Post by rhythmiccycle on 2009-08-09
i solved my own problem on when i googled and found this:

[http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/](http://www.blog.highub.com/linux/install-and-configure-phpmyadmin-on-ubuntu-lamp/)

---

### Post by rhythmiccycle on 2009-08-10
> **AliTabuger7 said:**
> 

Did you add this to /etc/apache2/apache2.conf?
```
Include /etc/phpmyadmin/apache.conf
```

that is what i did to solve the problem, thank you AliTabuger7

after i added that code to the bottom of apache2.conf it worked.

---

