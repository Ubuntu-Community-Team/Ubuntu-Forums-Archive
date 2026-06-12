---
title: "error redirecting http to https"
date: 2009-09-28
forum: Server Platforms
---

### Post by artheus on 2009-09-28
Hey

I've installed SSL on my apache now. And now I want [http://www.mydomain.com](http://www.mydomain.com) to be redirected to [https://www.mydomain.com](https://www.mydomain.com)..

But is I do this using the 

```
<virtualhost *:80>
    ServerName mydomain.com
    Redirect / https://www.mydomain.com
</virtualhost>

<virtualhost *:443>
    ServerName mydomain.com
    DocumentRoot /var/www
</virtualhost>
```

It will complain about
```
Error code: ssl_error_rx_record_too_long
```

so if I instead redirect it to [https://www.mydomain.com:443](https://www.mydomain.com:443) it works just fine. But I don't want that ":443" to be there! It bugs me! So how can I do this?

Cheers,
Artheus

---

### Post by artheus on 2009-09-28
Well.. solved this the very moment I posted it..
I just had to write in the server local ip instead of *.

```
<virtualhost 192.168.1.64:443>
    ServerName mydomain.com
    DocumentRoot /var/www
</virtualhost>
```

Cheers,
Artheus

---

