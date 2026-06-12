---
title: "Ubuntu Desktop/Server W/ Apache2-PHP5-Firebird"
date: 2009-08-29
forum: Server Platforms
---

### Post by zkriesse on 2009-08-29
When I try have the index php for my localhost...this is the error I get...

**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Unknown: Failed opening required '/var/www/phpinfo.php' (include_path=''.:/usr/share/php:/usr/share/php/PEAR'') in **Unknown** on line [B]0

Any ideas? HELP PLEASE!
[/B]

---

### Post by SoftwareExplorer on 2009-08-29
What if you make a text file called phpinfo.php and put this in it:```
<?php
phpinfo();
?>
``` and then save it as phpinfo.php in /var/www

---

### Post by zkriesse on 2009-08-29
It displays the php info....i've done that...

---

### Post by SoftwareExplorer on 2009-08-30
In that case, I have no idea how to fix it. Hopefully someone who does will come across this thread.

---

### Post by zkriesse on 2009-08-30
Could somebody please help with this!

---

### Post by wojox on 2009-08-30
Try and edit php.ini to:

```
include_path=".:/usr/share/php"
```

---

### Post by zkriesse on 2009-08-31
I've tried that too....nothing seems to work.

---

### Post by hessiess on 2009-08-31
I beleave this is a problem relating to the anoyance that running PHP as mod_php causes it to run as the same user as Apache. what you need to do is chown the files to be owned by Apache, which is normally `http'.

```

sudo chown -R http:http /var/www

```

A better option is to run PHP as your user with fastcgi and suexec.

---

### Post by zkriesse on 2009-08-31
> **hessiess said:**
> I beleave this is a problem relating to the anoyance that running PHP as mod_php causes it to run as the same user as Apache. what you need to do is chown the files to be owned by Apache, which is normally `http'.

```

sudo chown -R http:http /var/www

```A better option is to run PHP as your user with fastcgi and suexec.

What will that do exactly? the sudo part?

---

### Post by hessiess on 2009-09-01
> **Zachk18 said:**
> What will that do exactly? the sudo part?

make /var/www owned by the user apache runs as (http), which I explained above.

---

### Post by zkriesse on 2009-09-01
It gave me invalid user error in terminal....

---

### Post by zkriesse on 2009-09-01
That didn't help. It said something to the effect of http:http is not acceptable or something like that.

---

### Post by cariboo on 2009-09-01
In debian based systems either root or www-data own the files in /var/www, there is no http user or group.

---

### Post by zkriesse on 2009-09-02
I've reloaded my system a full five times in the past three days because of this problem...I would really like a feasible solution. Appreciated the help.

---

### Post by zkriesse on 2009-09-14
SO what DO I DO!!!!! HELP!!!!!!!!!!!!!!!!!!

---

### Post by cariboo on 2009-09-14
A quick search of the forums, says it might be a permissions issue,
try changing the permissions of /var/www/index.php:

```
sudo chmod 644 index.php
```

and make sure the file is owned either by root, or www-data.

---

### Post by SoftwareExplorer on 2009-09-15
> **cariboo907 said:**
> and make sure the file is owned either by root, or www-data.

you would do that by ```
sudo chown -R www-data:www-data /var/www
``` OR ```
sudo chown -R root:root /var/www
```

---

### Post by zkriesse on 2009-09-17
Just so you know...if you're having issues like this don't worry...because I'm working on a Ubuntu Wiki page documenting on how I made all this stuff work. When the Wiki page is finished I'll post the link here.

---

### Post by zkriesse on 2009-09-19
Here is a link that explains how to make all this stuff work. It's still under "construction" by me.....but it will be finished soon. [https://wiki.ubuntu.com/Ubuntu%20with%20Firebird%20Database](https://wiki.ubuntu.com/Ubuntu%20with%20Firebird%20Database)

---

### Post by zkriesse on 2011-01-30
Ok, I'm happy to present a full fledged doc page on setting up Apache2, php5, and Firebird 2.1 on an Ubuntu Linux System. This was done on the Ubuntu 10.10 Desktop Edition. If it helps you please let me know, and if you instead find bugs in the doc then let me know that too. Hope it helps! The Doc page itself can be found here at [Firebird 2.1 on Ubuntu]("https://help.ubuntu.com/community/Firebird2.1/On/Ubuntu") ):P

---

