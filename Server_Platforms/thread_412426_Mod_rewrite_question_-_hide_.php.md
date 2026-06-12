---
title: "Mod_rewrite question - hide .php"
date: 2007-04-18
forum: Server Platforms
---

### Post by hagen00 on 2007-04-18
Hi there

I've got a question regarding mod_rewrite. I've done some searching but haven't come across an answer yet. 

I'm building an application that will have URI such as mysite.com/admin/login.php

I would like to hide the php extension, i.e. have the URI mysite.com/admin/login

To achieve this I've been trying to use mod_rewrite. The rule that i've tried is

```
RewriteRule ^([A-Za-z0-9-]+) $1.php [L] 
```

but this rewrites the ULR to mysite.com/admin.php. 

I've tried playing around with some RewriteCond, but no luck so far. 

Any ideas?

Thanks

H

---

### Post by jameso on 2007-04-18
I personally haven't tested this, but if you add the following to a .htaccess file, all files without an extension will be parsed by the PHP interpreter:

```
DefaultType application/x-httpd-php
```
Ref: [http://www.radwin.org/michael/blog/2002/11/hiding_php_extensions_in_a.html](http://www.radwin.org/michael/blog/2002/11/hiding_php_extensions_in_a.html)

---

### Post by hagen00 on 2007-04-18
Hi

Thanks for the suggestion. I've tried that and it doesn't seem to work. Tried all kinds of variations, some mentioned in the link you posted. That's why i was hoping that there is a mod_rewrite solution, since that is tried and tested on our servers. 

Thanks

H

---

### Post by jtc on 2007-04-18
The problem seems to be the fact that  *([A-Za-z0-9-]+)* don't matches the slashes in your pathname. In your example that means that it captures admin, but then comes a slash, and it can not match anymore.

How about instread trying this expression?

```

(([A-Za-z0-9\-]+/)*[A-Za-z0-9\-]+)

```

---

### Post by hagen00 on 2007-04-18
Hi jtc

Thanks a lot. If i use your code it works for [http://localhost/system/admin](http://localhost/system/admin) (admin being my folder) and [http://localhost/system/admin/login](http://localhost/system/admin/login) (login being login.php).

Howerver when I try go to [http://localhost/system/](http://localhost/system/) (the root of the system) then it says /system/.php was not found. How would i modify the modrewrite rule so that it also works when i just type in the root directory, i.e. [http://localhost/system/](http://localhost/system/)

Many thanks

h

---

### Post by jtc on 2007-04-18
Well, if you'r going to a directory you don't really need to do any rewriting at all? That can be accomplish by RewriteCond. Add the following line just before your RewriteRule and it won't touch actually directories.

```
RewriteCond %{REQUEST_FILENAME} !-d
```

If you also want it to skip actually filenames, which I'm pretty sure you do, add this line as well.

```
RewriteCond %{REQUEST_FILENAME} !-f
```

---

### Post by hagen00 on 2007-04-18
Cool! That works great. Thanks very much for your help jtc. So to recap for anyone who's searching...

RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(([A-Za-z0-9\-]+/)*[A-Za-z0-9\-]+)?$ $1.php

This lets you put in your URLs without the .php

---

### Post by Brazen on 2007-04-18
jtc, you are freaking amazing.  RewriteJunk always looks like Greek to me :D

---

### Post by jtc on 2007-04-18
Well, should be noted that it is not a perfect solution, since there are a bunch of special cases which might break it. Why that is the case, and how to fix it, will simply be a good exercise for you to figure out :p

---

### Post by hagen00 on 2007-04-18
I've done a bit of ad hoc testing and so far so good. 
1. If i do include the .php at the end it works. 
2. If I pass some variables in the URL and retrieve them using $_GET then that also works. 
3. If i just go to directories without specifying a file (i.e. index.php should be parsed), it also works. 

So jtc, seems like your solution is a very good one! No?

---

### Post by jtc on 2007-04-18
> **Brazen said:**
> jtc, you are freaking amazing.  RewriteJunk always looks like Greek to me :D
Well, I did live a couple of years in Greece 8-) 

> **hagen00 said:**
> So jtc, seems like your solution is a very good one! No?
How about this path then?

*main.directory/file_name*

See where I'm going?

---

