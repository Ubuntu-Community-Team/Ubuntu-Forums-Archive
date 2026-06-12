---
title: "apache2 and rails, shows index instead of app"
date: 2006-12-21
forum: Server Platforms
---

### Post by nephish on 2006-12-21
lo there all.
i have rails installed and the apps work under webrick
however, when i point apache2 at the /var/www/myapp/public/ directory, only the index of: loads in the browser. I have the mod-ruby installed, also the fcgi module, when i click the index.rhml file in the index of page, it loads it as text. 
so what do i do to get apache to load the ruby app ?

thanks for any help here.

---

### Post by az on 2006-12-21
Does this page help?

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by nephish on 2006-12-21
ok, i think the article was very helpful, wish i knew about it earlier, 
but, i have this problem now, 
when i do the /etc/init.d/apache2 restart, i get this
```

Syntax error on line 10 of /etc/apache2/sites-enabled/000-default:
Invalid command 'RewriteEngine', perhaps mis-spelled or defined by a module not included in the server configuration
```

do you know what that could mean ?

thanks

---

### Post by nephish on 2006-12-21
ok. forgot to do the a2enmod rewrite thing, 

its working now

thanks, great link by the way

---

