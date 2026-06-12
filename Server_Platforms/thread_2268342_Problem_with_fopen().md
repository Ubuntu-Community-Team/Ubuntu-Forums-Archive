---
title: "Problem with fopen()"
date: 2015-03-08
forum: Server Platforms
---

### Post by darko6 on 2015-03-08
Hi, I am trying to learn some PHP via youtube tutorials, and I have run on some problems.

When I want to run fopen('novi1.txt','w') it shows me this :

[B]Warning: fopen(novi1.txt): failed to open stream: Permission denied in [B]/opt/lampp/htdocs/vezba/fajl.php on line 4


[/B][/B]I think that the problem is in Apache, because when I start Xampp the apache wont run and then I must enter this code:

```
sudo /etc/init.d/apache2 stop


sudo /opt/lampp/lampp start

```

---

### Post by lukeiamyourfather on 2015-03-09
The file being opened probably is owned by another user and doesn't have permission set for other users to read and write. Trying adding permission to the file to allow other users to read and write or change the owner of the file.

---

### Post by SeijiSensei on 2015-03-09
Apache runs as the www-data user, and all file transactions happen with that user's permissions.

Rewrite the fopen() command to use a complete file path for the output that points to a directory where www-data can write.  /tmp is a good choice unless you need to preserve the file after the application finishes.  If so, you'll need to consider where you want to have Apache write files.

Also make sure you want to use "w" and not "w+".  The latter lets you [read the file after it has been written]("http://php.net/manual/en/function.fopen.php").

---

