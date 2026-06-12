---
title: "retstricting access to phpmyadmin"
date: 2009-01-01
forum: Server Platforms
---

### Post by Kholdstate on 2009-01-01
I'd like to prevent remote users from accessing phpmyadmin on my server but I can't really figure out how to do that? Would this be something I do in the apache or phpmyadmin configuration? Maybe there is some boolean setting for this somewhere?

And secondly, if I want to disable phpmyadmin... how can I go about doing that? Do I just remove the symlink to phpmyadmin.conf from /etc/apache2/conf.d?

---

### Post by TestDummy! on 2009-01-01
If you're using Apache, I don't see why .htaccess couldn't handle it, or the appropriate lines in apache2.conf in the case of phpmyadmin.

For example:

```
<Directory /usr/share/phpmyadmin>
        Order Deny,Allow
        Deny from all
        Allow from (whichever private IP)
</Directory>
```

in **/etc/apache2/apache2.conf**, replacing (whichever private IP) with the one you want to access it, like 192.168.0.2 for instance. It can be configured to work locally for a LAN, but you have to know your network address and subnet mask to do that. In my case, it's 192.168.0.0/24, which would allow 192.168.0.1 to 192.168.0.254 to connect to phpmyadmin.

You can essentially disable it by denying everybody and allowing nobody, removing the allow line altogether.

Editing **/etc/apache2/conf.d/phpmyadmin.conf** and commenting out the Alias line:

```
Alias /phpmyadmin /usr/share/phpmyadmin
```

also seems to "disable" phpmyadmin from the perspective of access by Apache, but you have to restart Apache (sudo /etc/init.d/apache2 restart) after making the change, reloading the configuration doesn't seem to reliably work in this case.

---

### Post by cariboo on 2009-01-01
Phpmyadmin depends on your mysql passwords, if your users don't have a mysql password, all they'll see in the login screen.

Mysql sets up root as a user and asks you to set a password during installation. If nobody has that password they can't access your databases via phpmyadmin.

Jim

---

### Post by Kholdstate on 2009-01-02
thanks guys, works like a charm :popcorn:

I did however put

```
<Directory /usr/share/phpmyadmin>
        Order Deny,Allow
        Deny from all
        Allow from (whichever private IP)
</Directory>
```

in /etc/phpmyadmin/apache.conf

seemed to make more sense

---

### Post by TestDummy! on 2009-01-02
I do take it you adjusted "(whichever private IP)" to match an actual address on your network, right? :)

---

