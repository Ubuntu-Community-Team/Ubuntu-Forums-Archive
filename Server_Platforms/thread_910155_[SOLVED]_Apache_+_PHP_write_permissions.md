---
title: "[SOLVED] Apache + PHP write permissions"
date: 2008-09-04
forum: Server Platforms
---

### Post by TeknoPhil on 2008-09-04
Hi all ... I'm totally new to this and I was wondering how I should I properly configure apache and php so my php scripts can edit/create XML files?

Here's the case:
Users can access their home directory via FTP (they only have access to their home dir.) PHP 5 is installed. I want them to be able to create/run script that can edit/create XML files.

Right now, unless the files are chmod 777, this won't work (apache does not have the permission to write files).

How should I configure permissions so apache/php can edit/create XML files for every users?

Thanks!

---

### Post by TeknoPhil on 2008-09-05
Any advice?
Thanks

---

### Post by windependence on 2008-09-05
Take a look at the Apache module suexec. You enable the module like this after you install it:

```
a2enmod suexec
```

More info:

[http://httpd.apache.org/docs/2.0/suexec.html](http://httpd.apache.org/docs/2.0/suexec.html)

[http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html](http://www.ubuntugeek.com/apache2-web-server-installation-with-php4-and-php5-support-in-ubuntu.html)

[http://www.linode.com/forums/viewtopic.php?t=2982](http://www.linode.com/forums/viewtopic.php?t=2982)


-Tim

---

### Post by orpheus07 on 2008-09-05
You can add **apache** to the user's list of groups, then set their home directories to "group writable", e.g 775

You can check a user's groups by running the **groups** command.

[FONT="Courier New"]host:~/ groups my_user_name[/FONT]

But I suggest you put your users xml files (created by your php script) in a shared directory, e.g, /files/[user name/, if your network is accessible outside. In that way, only one folder is "apache writable".

---

### Post by TeknoPhil on 2008-09-05
Thanks for the help, 
unfortunalty, I'm not able to write to a file.

To test, here's what I did (not sure I'll use this solution but just to test)
1 - chmod my home dir to 775 (/home/teknophil/)
2 - added the user "www-data" to the group teknophil (I don't have any apache group, should I create it?)

If I change the ownership and/or group of the file i'm trying to edit to "www-data", it is working.

On the other hand, since "www-data" is in the same group as "teknophil" (owner of all the files and dir. in /home/teknophil), why am I not able to edit that file (while leaving the ownership to "teknophil")?

Thanks a lot for your help.

---

### Post by orpheus07 on 2008-09-05
www-data is right. it's apache in red-hat based distros.

can you post the output of this:

```
groups teknophil
```

---

### Post by TeknoPhil on 2008-09-06
> **orpheus07 said:**
> www-data is right. it's apache in red-hat based distros.

can you post the output of this:

```
groups teknophil
```
Sure:
```

teknophil adm dialout cdrom floppy audio dip www-data video plugdev fuse lpadmin admin
```

---

### Post by hyper_ch on 2008-09-06
apache's ability whether he can create or delete a file depends on the directory permissions. If you want user-based control you might want to have a look at su-php

---

### Post by TeknoPhil on 2008-09-06
> **hyper_ch said:**
> apache's ability whether he can create or delete a file depends on the directory permissions. If you want user-based control you might want to have a look at su-php

If apache is in the same group as the owner of the directory and this directory is group writable, it should work no?

Right now www-data is in the same group as teknophil.

```
teknophil@myserver:~$ groups www-data
www-data teknophil

```

both directory and file where apache should write are 775.

I will take a look at su-php. 
Thanks

---

### Post by TeknoPhil on 2008-09-06
Thank you all for your help, It's working fine now.
I feel stupid, I just had to reboot.
While testing, I was only restarting apache and though it would pick the changes to the groups.

---

### Post by hyper_ch on 2008-09-06
well, with suphp it will all file permissions will be to the actual user and not to apache... it's a bit more difficult to setup - for the users it's more confortable... especially when uploading files and such.

---

### Post by TeknoPhil on 2008-09-06
> **hyper_ch said:**
> well, with suphp it will all file permissions will be to the actual user and not to apache... it's a bit more difficult to setup - for the users it's more confortable... especially when uploading files and such.

Thanks for the hint. I'll make sure to test it.

---

