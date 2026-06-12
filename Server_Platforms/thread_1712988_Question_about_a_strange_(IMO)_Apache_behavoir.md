---
title: "Question about a strange (IMO) Apache behavoir"
date: 2011-03-23
forum: Server Platforms
---

### Post by Aaron44126 on 2011-03-23
Have Apache running on Ubuntu Server.

Say I have a domain, [www.somewhere.com](www.somewhere.com), and I have uploaded a file, phpinfo.php.

If I hit http://www.somewhere.com/phpinfo.php, I get my file as expected.

HOWEVER

If I hit non-existent file http://www.somewhere.com/phpinfo/somefile.dat, it also acts as if I hit phpinfo.php, instead of giving me a 404 error.

It seems that because the DIRECTORY "phpinfo" does not exist, it decided that I must have meant to hit phpinfo.php at the root of the site.  If I create an empty "phpinfo" directory then it behaves as expected and gives me a 404 not found page.

This is reproducible for any other file name you can think of.

I'm sure this is some Apache convenience behavior but I would like to disable it (it is messing with some mod_rewrite stuff I would like to do).  Because it's hard to describe I cannot figure out which Apache option it might be (whatever I Google for gives me completely unrelated results).  Does anyone know anything about this?

Thanks!

---

### Post by falko on 2011-03-23
Do you use any rewrite rules that might cause this (also check your .htaccess files)?

---

### Post by Aaron44126 on 2011-03-23
No.  I was careful to try this with no rewrite rules (no .htaccess at all actually) and a very minimal virtual host config.

---

### Post by tgalati4 on 2011-03-23
Perhaps there is a default setting in your /etc/php5/apache2/php.conf file?

---

### Post by Aaron44126 on 2011-03-23
Hmm, definitely related to PHP (I am unable to reproduce using the same method, but a .html file).  However, I haven't changed any of the default PHP configuration.

I have now reproduced this on two different servers (one Ubuntu 10.04 and one Ubuntu 10.10).  Whatever causes this behavior is present in the default Ubuntu configuration.

Still looking for suggestions.

---

### Post by tgalati4 on 2011-03-23
Try setting the document root path to /var/www or wherever your website path starts.  It's located in the php.ini configuration file.

It appears that the PHP processor redirects to the default root directory instead of a specified one when an invalid php file is processed.

---

### Post by Aaron44126 on 2011-03-23
Unfortunately, the server I actually need this fixed on runs about 50 different domains so there's not just one document root.

Why would Apache invoke PHP when I didn't request a PHP file?

---

### Post by SeijiSensei on 2011-03-23
Did you modify /etc/apache2/sites-enabled/000-default in any way?  That contains the VirtualHost definition that handles requests not matching another VirtualHost configuration.  It's also best that this file load first; that's why it has the 000-default name.  Apache processes the files in /sites-enabled/ in alphabetical order, and the first file it encounters will become the default.

---

### Post by Aaron44126 on 2011-03-23
No, that file is in its original state.

I'm curious if anyone has tried to reproduce the behavior I described in the original post and FAILED to do so?  You can test it quickly if you have a Ubuntu Apache/PHP server set up.  Just toss up a dummy php file and try to access it like it was a directory.

---

### Post by falko on 2011-03-23
Take a look at the AcceptPathInfo directive:
[http://httpd.apache.org/docs/2.0/mod/core.html#acceptpathinfo](http://httpd.apache.org/docs/2.0/mod/core.html#acceptpathinfo)

I think you should try
```
AcceptPathInfo Off
```

---

### Post by Aaron44126 on 2011-03-24
Brilliant!  That is it.  Thanks.

---

