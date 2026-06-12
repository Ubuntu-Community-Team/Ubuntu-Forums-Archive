---
title: "500 error in .htaccess?"
date: 2008-01-19
forum: Server Platforms
---

### Post by Cirdan7 on 2008-01-19
I'm getting a Request exceted the limit of 10 internal redirects due to probably config error. Use LimitInternalRecursion to increase the limit if necessary.

What is causing the problem is my .htaccess that I am using for the Zend Framework.

RewriteEngine on
RewriteRule !\.(js|ico|gif|jpg|png|css)$ index.php



The error was because I was messing with the url through and Alias in the apache2.conf

---

### Post by MJN on 2008-01-20
That's because the first redirect results in index.php, which also matches your rule given it doesn't end in js|ico etc hence it redirects again, and again...

Try excluding index.php from the conditions by adding **RewriteCond !index.php$** above your RewriteRule.

Mathew

---

