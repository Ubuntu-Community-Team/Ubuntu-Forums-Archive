---
title: "PHP only works with WWW"
date: 2011-03-01
forum: Server Platforms
---

### Post by uzd4ce on 2011-03-01
I just installed Apache2 for the first time, on Mint 10 (Ubuntu 10.10) and put PHProxy in /var/www/x

The php page works fine if I access it via [www.domain.com/x](www.domain.com/x), and it works both with and without the www when I access it via https.

But if I go to just [http://domain.com/x](http://domain.com/x), then it tries to download the php file.

I know zero about Apache, so have no idea what I may have misconfigured,so would appreciate any advice.

---

### Post by artheus on 2011-03-01
Hey there,

Could you post your vhost/apache2 configuration, please?

Would make it alot easier for us to help you then.

Cheers,
Artheus

---

### Post by SeijiSensei on 2011-03-01
Add a ServerAlias declaration in your virtual host configuration right below the ServerName directive like this:

```

ServerName    www.example.com
ServerAlias   example.com

```

---

