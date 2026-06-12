---
title: "apache 2 wont work right"
date: 2009-06-29
forum: Server Platforms
---

### Post by Duxter on 2009-06-29
Hello i just installed apache2 php 5 and mysql through apt-get. everything installed with no error messages but when i try localhost i got "error connecting to localhost" any ideas?

thanx for your time.

---

### Post by lykwydchykyn on 2009-06-29
Post the output of these commands:

First see if apache is running:
```

ps -e |grep apache

```

if it's not, try this:
```

sudo /etc/init.d/apache2 restart

```

If it was running, or if it still doesn't work, check the error log:
```

sudo cat /var/log/apache2/error_log

```

Post the output from those commands and that will give us a place to start.

---

### Post by Iowan on 2009-06-29
I presume you're trying to connect to "localhost" from the server itself. (sorry, gotta ask...)
/etc/hosts still has definition for localhost?
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Edit%20Apache%20Configuration") is a good help page - if you haven't already seen it.

---

### Post by Duxter on 2009-06-30
sorry for all the fuss mates i just rebooted and everything was fine except that i put a forum script (smf) in www folder and when i pointed firefox to install.php it promted me to download it except execute it. php seems to run smoothly from the phpinfo test script. any ideas?

thanks again.

---

### Post by Duxter on 2009-06-30
should i open a new thread?

---

### Post by masux594 on 2009-06-30
A new thread no, that's more than enough.. Well.. Does this .php file has an header?

Sysc, A

---

### Post by lykwydchykyn on 2009-06-30
Did you install the php module for apache?  I believe it's libapache2-mod-php5, but don't quote me on that.

---

### Post by Duxter on 2009-06-30
@masux: i presume you mean <php and ?> then yes it has.
@lykwydchykyn: yes it is installed.

---

### Post by v3xtra on 2009-06-30
Check [This thread](http://ubuntuforums.org/showthread.php?t=1109551&highlight=apache+.php+download)

or [this one](http://ubuntuforums.org/showthread.php?t=995039)

and [this one](http://ubuntuforums.org/showthread.php?t=926692&highlight=apache+.php+download)

:)

---

### Post by masux594 on 2009-06-30
> **Duxter said:**
> @masux: i presume you mean <php and ?> then yes it has.
@lykwydchykyn: yes it is installed.

No =|, something like [PHP]header("some string");[/PHP]

Sysc, A

---

### Post by Duxter on 2009-07-01
No there is no header in the file. ill go check the links too. thanks for the replies mates.

---

### Post by Duxter on 2009-07-01
Well i did what these pages instructed php files work except thta install.php!

---

### Post by masux594 on 2009-07-01
Can you attach the .php file in the next post?.. looks very strange..

Sysc, A

---

### Post by Duxter on 2009-07-01
This IS weird. I read the posts the links directing to. I only did a:
```
sudo a2enmod php5
```

Which gave me an already installed message. i rebooted for some reason and voila all working like a charm. to prevent comfusion i had restarted the apache daemon a hundred times.

i cant attach the file install.php as it is too big. thank you all from the bottom of my heart and the root of my linux system
I hope everything runs smoohly from now on or else i ll post again. this IS a threat. :lolflag:

You :guitar: mates!

---

