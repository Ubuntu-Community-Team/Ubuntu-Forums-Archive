---
title: "Apache modueles don't work"
date: 2008-09-17
forum: Server Platforms
---

### Post by mexlinux on 2008-09-17
I have already enabled mod_rewrite_ and mod_userdir

I can see them enabled in phpinfo()


But they don't work

I can not access [http://localhost/~user](http://localhost/~user)

And my .htaccess enabling mod_rewrite does not work (it works in my isp)
so is a local problem

any clues?

---

### Post by RealPSL on 2008-09-17
Did you get an error message when you tried to access the ~user site? Did you check the /var/log/apache2/error.log file?

---

### Post by mexlinux on 2008-09-18
The error on the browser is:
```

403 Forbidden
You don't have permission to access /~user/ on this server.

```

error.log
```

Permission denied: access to /~user/ denied

```

Permisions of /home/user/public_html:
```

drwxr-xr-x  2 user user 4.0K 2008-09-13 10:25 public_html

```

Permisions of the index within such dir:
```

-rw-rw-r-- 1 user user 5 2008-09-13 10:25 index.html

```

---

### Post by windependence on 2008-09-18
Looks like an ownership problem. Apache can't access the files owned by "user"

-Tim

---

### Post by anderswestrup on 2008-09-18
No, it isn't an ownership issue, the file permissions in the above post allow read to all users..

My guess is that you need to add a permission in your apache config:

<Directory /home/user/public_html>
order allow,deny
allow from all
</Directory>

---

### Post by mexlinux on 2008-09-18
I think I need more help here:
This is already in userdir.conf

```

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
		order allow,deny
		allow from all
        </Directory>
</IfModule>

```

Should I replace it with your code, or add, or what?


Note: This is a standard hardy installation

---

### Post by MJN on 2008-09-18
> **anderswestrup said:**
> No, it isn't an ownership issue, the file permissions in the above post allow read to all users..

Ah.. but we haven't seen the permissions of the parent directory tree - these folders all need execute permissions setting to allow Apache to traverse them.

Mathew

---

### Post by mexlinux on 2008-09-18
> **MJN said:**
> Ah.. but we haven't seen the permissions of the parent directory tree - these folders all need execute permissions setting to allow Apache to traverse them.

Mathew

This was the problem, 
```

chmod o+x /home/user

```

solevd the problem

---

### Post by windependence on 2008-09-19
> **MJN said:**
> Ah.. but we haven't seen the permissions of the parent directory tree - these folders all need execute permissions setting to allow Apache to traverse them.

Mathew

You know Mathew, this is one thing I think EVERYBODY forgets. Even I don't think about it sometimes and I do this every day. ;)

-Tim

---

### Post by MJN on 2008-09-19
> **windependence said:**
> You know Mathew, this is one thing I think EVERYBODY forgets. Even I don't think about it sometimes and I do this every day. ;)
I think it only sticks in my mind because it had me stumped for so long when I set my first server up! :lol:
 
Mathew

---

