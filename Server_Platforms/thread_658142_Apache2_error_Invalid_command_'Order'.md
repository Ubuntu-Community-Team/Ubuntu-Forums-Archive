---
title: "Apache2 error Invalid command 'Order'"
date: 2008-01-04
forum: Server Platforms
---

### Post by trymbill on 2008-01-04
When I try to start up Apache2 I get this error:

```
Syntax error on line 141 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
```

Does any one know what module controls this feature in Apache2? :(

---

### Post by MJN on 2008-01-04
It might be helpful to post the reference line (141), or indeed the whole section covering that line.
 
The 'order' directive is provided by mod_access.
 
Mathew

---

### Post by trymbill on 2008-01-04
From my Apache2.conf file, this is around line 141:

```

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

```

This is the first time "Order" is used in the config file so i guess if I remove this line it will just say that some other line, with the command "Order" is bad ...

How can I uninstall and re-install mod_access?  Or how can I fix this problem? : - /

---

### Post by MJN on 2008-01-05
What release are you using (it's useful to put this into your profile as it is quite significant)?

Also, have you just installed Apache? Of was it already running previously? Have you changed any of the config?

Regarding the module status, it's part of the base build and so unless you've removed it intentionally it'll be there.

Have you just added the above config, or was it there by default?

Mathew

---

### Post by trymbill on 2008-01-05
I'm using Ubuntu 7.10.

I've been running Apache2 O.K. now for maybe a month.  I just installed the php-mail package via APT-GET, then I restarted Apache2 and this error came up.

This config is default, I have not changed it.

I'm using ISPconfig now but I'm thinking about changing into just using Webmin.  So if I do that, probably today or tomorrow, I won't have to worry about this error but I still would like to know what's causing it.

B.t.w., do you know of any software like Webmin which is even better then Webmin?

Thanks alot for your responce,
Magnus

---

### Post by MJN on 2008-01-05
I'm not sure I follow what you mean about the error disappearing once you start using Webmin - can you elaborate?

Mathew

---

