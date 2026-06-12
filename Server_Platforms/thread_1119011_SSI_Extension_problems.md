---
title: "SSI Extension problems"
date: 2009-04-07
forum: Server Platforms
---

### Post by mermulade on 2009-04-07
Hello, i have a question about the infamous server side includes: 
I would like to make my includes work without the .shtml extension. (it works fine with .shtml but I am too lazy to change all the extensions on my website...) I attempted to create a .htaccess file that I placed in the /var/www/ directory. It reads:

  AddType text/html .shtml
  AddHandler server-parsed .shtml .html

Please help, Mermulade

---

### Post by cdenley on 2009-04-07
Edit the file /etc/apache2/mods-available/mime.conf

change this part (change in red)
```

#
# Filters allow you to process content before it is sent to the client.
#
# To parse .shtml files for server-side includes (SSI):
# (You will also need to add "Includes" to the "Options" directive.)
#
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml**[COLOR="Red"] .html[/COLOR]**

```

then restart apache
```

sudo /etc/init.d/apache2 restart

```

---

