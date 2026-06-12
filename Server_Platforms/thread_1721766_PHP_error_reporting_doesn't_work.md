---
title: "PHP error reporting doesn't work"
date: 2011-04-05
forum: Server Platforms
---

### Post by julianb on 2011-04-05
I am developing/testing a PHP app on my netbook. For some reason apache/php are returning nothing but a "500 internal server error" response when there is a problem with my php script. For example, if there is a semicolon or closing brace missing, it should cause the script to die with a hint about which line caused the script to stop working. Instead it displays nothing but a "500 internal server error" message.

Anybody know how to resolve this?

---

### Post by falko on 2011-04-05
How do you call the script? Through mod_php, FastCGI, CGI, or suPHP?

Are there any errors in Aapche's error log?

---

### Post by julianb on 2011-04-05
i am assuming it's "mod_php" because i used apt-get to install these packages:
apache2 php5-mysql libapache2-mod-php5 mysql-server

...

I am using Natty Narwhal desktop edition.
latest part of the error log copied from :
```
09:50:11 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: meeting in /var/www/index.php on line 172, referer: http://localhost/?q=camden
[Tue Apr 05 09:50:11 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined index: n in /var/www/index.php on line 46, referer: http://localhost/?q=camden
[Tue Apr 05 09:50:11 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: lin in /var/www/index.php on line 75, referer: http://localhost/?q=camden
[Tue Apr 05 09:50:11 2011] [error] [client 127.0.0.1] PHP Notice:  Undefined variable: ret in /var/www/index.php on line 80, referer: http://localhost/?q=camden
[Tue Apr 05 11:02:00 2011] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '}' in /var/www/index.php on line 320
[Tue Apr 05 11:02:00 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico

```
(so the syntax errors do generate something in the log file, see php parse error above)

---

### Post by SeijiSensei on 2011-04-05
Most distributions configure PHP to write errors to the virtual host's error log rather than the displayed page.  Putting raw PHP errors on the page is both ugly and a security hole.

---

### Post by thewooleymammoth on 2011-04-29
is there a way to change it back to showing on the page? It's much better for development

---

### Post by m3bik on 2011-04-29
Add this to the PHP code in the file you're looking to find an error (or a common file shared between your entire project):

```
ini_set('display_errors', 1);
```

Then to turn it back off:

```
ini_set('display_errors', 0);
```

---

