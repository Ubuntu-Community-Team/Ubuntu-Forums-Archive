---
title: "HTTP_ACCEPT_LANGUAGE phpinfo() set value problem"
date: 2008-01-31
forum: Server Platforms
---

### Post by teutatis on 2008-01-31
Hallo community 

I know noobs like me shouldn't run a webserver but as a student I can't effort canonical support. 

My problem is: 

When i print out the apache variables with phpinfo() I get 

```
HTTP_ACCEPT_LANGUAGE    en-us,en;q=0.5 
```

but I need additional** de **support. 

So I change the web7.conf (vhost.conf) 

I tried 
```

php_admin_value HTTP_ACCEPT_LANGUAGE de
php_admin_value HTTP_ACCEPT_LANGUAGE de-de
php_admin_value HTTP_ACCEPT_LANGUAGE de_de
 
php_admin_flag HTTP_ACCEPT_LANGUAGE de
php_admin_flag HTTP_ACCEPT_LANGUAGE de-de
php_admin_flag HTTP_ACCEPT_LANGUAGE de_de 

```

and restarted the server but nothing works. 

```
HTTP_ACCEPT_LANGUAGE    en-us,en;q=0.5 
```

stays the same. 

Any ideas? help? 

thx

---

### Post by teutatis on 2008-01-31
HTTP_ACCEPT_LANGUAGE is a browser thing

dpkg-reconfigure locales solved my problem 

thx

---

