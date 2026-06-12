---
title: "Moving phpbb3 from //ip/phpbb to //ip/"
date: 2013-03-01
forum: Server Platforms
---

### Post by RandomP on 2013-03-01
Google is proving to be no use. 

I am trying to move my phpbb3 forums  from localhost/phpbb to just localhost, the main page of the server. Can anyone tell me how to do this?

I used this tutorial to set up the forums:
[https://help.ubuntu.com/community/PhpBB3](https://help.ubuntu.com/community/PhpBB3)

This is running on Ubuntu 12.10 Server Edition (x64 of course)

Any help would be greatly appreciated.

---

### Post by GordThompson on 2013-03-02
In the tutorial you cited, phpBB is activated by creating the link

```
sudo ln -s /usr/share/phpbb3/www /var/www/phpbb
```
Since phpBB is actually stored in /usr/share/phpbb3/www you can make it appear as the "main page" of the server by editing the file...

/etc/apache2/sites-available/default

...and changing the DocumentRoot directive for the default site from...

```
DocumentRoot /var/www
```
...to...

```
DocumentRoot /usr/share/phpbb3/www
```

---

### Post by RandomP on 2013-03-02
Cool, thank you very much!

---

