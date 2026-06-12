---
title: "PHP/Netbeans/firefox problems..."
date: 2010-06-09
forum: Server Platforms
---

### Post by Gerdion on 2010-06-09
Okay. I'm stumped. I'm just trying to get php set up so I can write some simple learning code and I decide to follow all the steps as outlined on [http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

For some reason, my test page that is supposed to open the phpinfo() method within the firefox browser doesn't work. Instead, firefox asks what application should open the index.php file. 

Now, the troubleshooting section on the above page covers this and gives me specific instructions, however the instructions to purge the php5-common and replace it with php5 and phpmyadmin do nothing to amend the problem. Firefox is still clueless as to what to do with the php file given it.

What exactly is wrong with all this? I did everything correctly.

I am using Lucid Lynx in case that makes any difference (which I don't think it should).

Many thanks in advance.

---

### Post by kevin11951 on 2010-06-10
> **Gerdion said:**
> Okay. I'm stumped. I'm just trying to get php set up so I can write some simple learning code and I decide to follow all the steps as outlined on [http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

For some reason, my test page that is supposed to open the phpinfo() method within the firefox browser doesn't work. Instead, firefox asks what application should open the index.php file. 

Now, the troubleshooting section on the above page covers this and gives me specific instructions, however the instructions to purge the php5-common and replace it with php5 and phpmyadmin do nothing to amend the problem. Firefox is still clueless as to what to do with the php file given it.

What exactly is wrong with all this? I did everything correctly.

I am using Lucid Lynx in case that makes any difference (which I don't think it should).

Many thanks in advance.

SSH on server:

```
chown -R www-data:www-data /var/www
chmod -R 0755 /var/www
```

Also, replace the contents of "/etc/apache2/sites-available/default" with:

```
<VirtualHost *:80>
	DocumentRoot /var/www/

</VirtualHost>
```

Then, clear you browser's cache, and refresh the page.

---

### Post by Gerdion on 2010-06-10
That made it even worse. Now firefox doesn't even recognize it as a php file any longer. It is asking to open a PHTML file. Perhaps I am omitting relevant information?

---

### Post by kevin11951 on 2010-06-10
> **Gerdion said:**
> That made it even worse. Now firefox doesn't even recognize it as a php file any longer. It is asking to open a PHTML file. Perhaps I am omitting relevant information?

Post the contents of the PHTML file...  or at least a chunk of it.

edit: also, post the output of:
```

ls /var/www/

```

---

### Post by Gerdion on 2010-06-10
> **kevin11951 said:**
> Post the contents of the PHTML file...  or at least a chunk of it.

edit: also, post the output of:
```

ls /var/www/

```

Contents? After opening it with gedit it is the following:
```

<?php
     phpinfo();
?>

```Which is exactly what it should be.

Output of ls /var/www is... index.html

I was trying to set up a local public_html file as directed in the previously mentioned walkthrough page. Do I need to tie up a loose end here?

---

