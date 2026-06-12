---
title: "Editing php-setup on a LAMP server (@server edition)"
date: 2009-10-25
forum: Server Platforms
---

### Post by jaybirdz on 2009-10-25
Hey!
 
Testing to set up a MediaWiki server, on Ubuntu Server Edition following this: [http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu](http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu)
guide.
 
And at the php-setup, I see he is using some commands as 
```
upload_max_filesize = 2M
``` and such.
 
And I wondered, can I just type it in like shown on the picture below?
 
[IMG]http://img203.imageshack.us/i/phpr.jpg/[/IMG]_[[IMG]http://img263.imageshack.us/img263/7083/php1.th.jpg[/IMG]]("http://img263.imageshack.us/i/php1.jpg/")_
 
Thanks for the help!

---

### Post by kevin11951 on 2009-10-25
If your looking for your php config file, its stored at "/etc/php5/apache2/php.ini"

---

### Post by jaybirdz on 2009-10-26
Kinda wondered where to type the commands, where to do the configuration?

---

### Post by wojox on 2009-10-26
Isn't that your picture? Just

```
sudo nano /etc/php5/apache2/php.ini
```

If your not sure how to use nano just Google it.

---

### Post by jaybirdz on 2009-10-26
Yea I understand the nano-part, but I'm wondering how/where to write command to change the values like "upload_max_filesize = 2M" and so on.

---

### Post by kevin11951 on 2009-10-26
> **jaybirdz said:**
> Yea I understand the nano-part, but I'm wondering how/where to write command to change the values like "upload_max_filesize = 2M" and so on.

Inside the file I listed above, is "upload_max_filesize =" followed by a number, change that number to whatever you want (in this case 2M).

If you want to know how to find it, type <ctrl>+"w", then type in "upload_max_filesize" and hit <enter>

---

### Post by jaybirdz on 2009-10-27
Thanks! :)

---

