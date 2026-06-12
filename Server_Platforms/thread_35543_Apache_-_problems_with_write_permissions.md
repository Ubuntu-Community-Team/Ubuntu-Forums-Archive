---
title: "Apache - problems with write permissions"
date: 2005-05-19
forum: Server Platforms
---

### Post by JaF on 2005-05-19
How can I configure apache so that it can write to /var/www/ ?

When I run:
```
<?PHP
touch("newfile.txt");
?>

```

I get:

```

Warning: touch(): Unable to create file newfile.txt because Permission denied in /var/www/touch.php on line 2
```

---

### Post by Sam on 2005-05-19
You have to chmod 666 the folder. But don't do with /var/www it's a bit unsecure, create a special folder which is allowed for writing.
```
$ sudo chmod 666 /var/www/<dir>
```
666 means read-write for everybody.

---

### Post by JaF on 2005-05-19
I now have a /var/www/write but I get a 403 forbidden error. :(

---

### Post by LordHunter317 on 2005-05-19
[QUOTE=Sam]666 means read-write for everybody.[/QUOTE]**NO, NO, NO**.

Don't **ever, ever, ever** make a file 666 or a directory 777.  666 is the Antichrist's number for a reason.  

It's always wrong.  In the very few rare cases where it's not wrong to do this, you'll know.

Having to set something 666 or 777 almost always means you're doing something else wrong.  So don't do it.  Don't suggest it.  Just pretend it's impossible.  You'll be happier and your systems will be safer this way.

Anyway, if you really need a writable webroot, make it group-owned by the Apache group (www-data) and set the permissions like so:```
chgrp www-data /var/www
chmod 775 /var/www
```

But you don't want a writable webroot.  That's almost always a mistake.

Instead, write your PHP application correctly.  Use the mktemp() function or similar to create a file in a temporary directory outside the webroot, where you will have write access.  This is much more secure and correct.

---

