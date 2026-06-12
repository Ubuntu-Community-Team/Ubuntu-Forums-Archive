---
title: "lamp won't run `.php` files was creating or editing on windows"
date: 2013-06-20
forum: Server Platforms
---

### Post by kamrava on 2013-06-20
Hi there

When i create or edit some file like `index.php` with below simple content (on Windows) :

```
<?php
echo 'Hello world';
?>

```

Now, I want to run it on Ubuntu by lamp-server. Copied that `index.php` file on `~/public_html/`.
Finally trying below in Browser :

```
localhost/index.php
```

I get following error:
> **Server error**

[COLOR=#000000][FONT=Helvetica]The website encountered an error while retrieving **[http://localhost/home.php](http://localhost/home.php)**. It may be down for maintenance or configured incorrectly.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]**Here are some suggestions:**


[LIST]
[*][Reload]("http://localhost/home.php") this webpage later.
[/LIST]
[/FONT][/COLOR]
[COLOR=#777777][FONT=Helvetica]HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request.[/FONT][/COLOR]

But if i create that `index.php` on ubuntu with same content it works fine.

It's some weird isn't it ?

---

### Post by monkeybrain2012 on 2013-06-20
index.php is in var/www

---

### Post by kamrava on 2013-06-20
> **monkeybrain2012 said:**
> index.php is in var/www

I have changed www folder to `~/public_html/`
When i create `index.php` file in Ubuntu and put that in `~/public_html/` it works fine.

---

### Post by Irihapeti on 2013-06-20
*Thread moved to **Server Platforms**.*

---

### Post by kamrava on 2013-06-20
I find out the problem :)

Answer :
```
sudo chmod -R 755 ~/public_html
```

---

### Post by CharlesA on 2013-06-20
You didn't say what Web server you were using, but I'm assuming it's Apache (cuz of LAMP). Checking error logs helps tremendously. :p

Glad you got it sorted.

---

