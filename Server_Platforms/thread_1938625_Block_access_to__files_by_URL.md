---
title: "Block access to  files by URL"
date: 2012-03-10
forum: Server Platforms
---

### Post by mohitdaksh on 2012-03-10
Hello, I am new to webhosting and building a very small website as a part of my project. It will not be used for practical purposes for now, but still I want to make sure that it is not TOO insecure.

I have a few files which I don't want users to access by URL(some text and CSV files) but my PHP code should be able to use them. How can I achieve something like this?

---

### Post by nsnidanko on 2012-03-12
I would look into htaccess

---

### Post by Jonathan L on 2012-03-12
> **mohitdaksh said:**
> Hello, I am new to webhosting and building a very small website as a part of my project. It will not be used for practical purposes for now, but still I want to make sure that it is not TOO insecure.

I have a few files which I don't want users to access by URL(some text and CSV files) but my PHP code should be able to use them. How can I achieve something like this?

Hi Mohitdaksh

If I've understood your question properly, you've got some text and csv files which your PHP code needs to read (or write) but which you don't want visible as [http://yoursystem/anything](http://yoursystem/anything)

It's usual  to simply put them outside of the web tree.  A current project of mine (on a dedicated machine) has a php file which is runnable, and a config and file1 which are inaccessible via apache.  doit.php simply opens them with a full path name.
```
/var/www/doit.php
/etc/projectname/project.conf
/var/lib/projectname/file1
```Perhaps that helps?

Kind regards,
Jonathan.

---

### Post by Habitual on 2012-03-13
[http://corz.org/serv/tricks/htaccess.php](http://corz.org/serv/tricks/htaccess.php)
[http://corz.org/serv/tricks/htaccess2.php](http://corz.org/serv/tricks/htaccess2.php)
[http://www.garnetchaney.com/htaccess_tips_and_tricks.shtml](http://www.garnetchaney.com/htaccess_tips_and_tricks.shtml)

should get you started...

---

### Post by mohitdaksh on 2012-05-06
Thanks to all of you. I placed the file outside the default /var/www directory.

And sorry for replying so late. :)

---

### Post by SeijiSensei on 2012-05-06
While putting those files outside the publicly-visible directory is always the best choice, I'll just mention that you can also control which files are available using the "[<Files>]("http://httpd.apache.org/docs/2.2/mod/core.html#files")" directive in Apache.

---

