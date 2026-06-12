---
title: "apache2 weird php parsing"
date: 2007-09-17
forum: Server Platforms
---

### Post by sopordave on 2007-09-17
I have a LAMP server running, with phpmyadmin and phpbb installed from the repos. I can access [http://localhost/phpmyadmin](http://localhost/phpmyadmin) just fine, but when I try for [http://localhost/phpbb](http://localhost/phpbb), my web browser offers to download the file. However, if I use the exact URL [http://localhost/phpbb/index.php](http://localhost/phpbb/index.php), it works fine.

Any reason why the default index.php would would in one directory, and not the other?

---

### Post by James79 on 2007-09-22
What file does it offer to download?

Look in your /etc/apache2/apache2.conf file, it'll indicate to you exactly what are your "default" files and in what order to look for them.

Mine says:

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```

In my case, if I had an index.html file in the same directory, it would be preferred and chosen over my index.php.

What does your say? Do you have any other of those files in your phpbb directory? What's the filename of the file your browser wishes to download?

---

