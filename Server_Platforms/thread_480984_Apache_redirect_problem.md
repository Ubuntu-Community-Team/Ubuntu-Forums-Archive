---
title: "Apache redirect problem"
date: 2007-06-22
forum: Server Platforms
---

### Post by tarek on 2007-06-22
Hi,

I'm hosting my site on my computer - ubuntu 7.04 and I just moved my blog from CSMonkey.com/blog to CSMonkey.com and added a .htaccess to www:

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^blog/(.*)$ [http://csmonkey.com/](http://csmonkey.com/)
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

That redirects anything from CSMonkey.com/blog to the main folder CSMonkey.com

However the problem is that links on digg and other sites don't work for example:
[http://csmonkey.com/blog/2007/06/19/how-to-make-sun-java-5-the-default-java-compiler-on-ubuntu/](http://csmonkey.com/blog/2007/06/19/how-to-make-sun-java-5-the-default-java-compiler-on-ubuntu/)

should now point to:
[http://csmonkey.com/2007/06/19/how-to-make-sun-java-5-the-default-java-compiler-on-ubuntu/](http://csmonkey.com/2007/06/19/how-to-make-sun-java-5-the-default-java-compiler-on-ubuntu/)

without the "blog" folder in the url

Is there a way to fix that in apache using .htaccess or other options?

Thanks
Tarek

---

### Post by tarek on 2007-06-22
Hello again,

For anybody else who is having the same problem, I found a solution:

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^blog/(.*)$ http://csmonkey.com/$1 [R,L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

This is what I changed:
RewriteRule ^blog/(.*)$ http://csmonkey.com/$1 [R,L]

Now works!

Tarek

---

