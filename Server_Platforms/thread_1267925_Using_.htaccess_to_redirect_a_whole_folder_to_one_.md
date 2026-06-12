---
title: "Using .htaccess to redirect a whole folder to one php file"
date: 2009-09-16
forum: Server Platforms
---

### Post by Johnsie on 2009-09-16
Hello, I have a folder that I want redirected:

[http://example.com/SpecialFolder/index.php](http://example.com/SpecialFolder/index.php) ----> [http://example.com/process.php?pageName=index.php](http://example.com/process.php?pageName=index.php)

[http://example.com/SpecialFolder/test.php](http://example.com/SpecialFolder/test.php) ----> [http://example.com/process.php?pageName=test.php](http://example.com/process.php?pageName=test.php)

[http://example.com/SpecialFolder/page2.php](http://example.com/SpecialFolder/page2.php)  ----> [http://example.com/process.php?pageName=page2.php](http://example.com/process.php?pageName=page2.php)

The thing is that I wont alway know what the name of the php file will be. Is there a way I can use .htaccess to do this kind of redirect?

---

### Post by Johnsie on 2009-09-16
I found this example:

[PHP]
RewriteEngine On
RewriteRule    ^([a-z]*)/([a-z]*)/([1-9]+)(-[1-9]+)? $  http://www.example.com/index.php?cat=$2&a=$3&page=$4&lang=$1    [L]

[/PHP]


I'm going to try:

[PHP]
RewriteEngine On
RewriteRule    ^([a-z]*).php? $  
http://www.example.com/index.php?pageName=$2&a=$3&page=$4&lang=$1    [L]
[/PHP]

---

### Post by Lars Noodén on 2009-09-16
If you are using Apache, then you'll want to take a look at the URL Rewriting Guide and mod_rewrite.

[http://httpd.apache.org/docs/2.2/rewrite/](http://httpd.apache.org/docs/2.2/rewrite/)

[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

---

