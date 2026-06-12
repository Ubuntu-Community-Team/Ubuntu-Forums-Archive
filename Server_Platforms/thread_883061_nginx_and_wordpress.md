---
title: "nginx and wordpress"
date: 2008-08-07
forum: Server Platforms
---

### Post by jwxie on 2008-08-07
hey all, just installed nginx on ubuntu 8.04 server
okay, so it works fine 
[http://goko.no-ip.org/](http://goko.no-ip.org/)

i followed this guide, and trying to install wordpress
[http://bc-dev.net/category/linux/](http://bc-dev.net/category/linux/)

i am not very well with command
i mean, i just started these days, so still have questions

1. i followed to the downloaded

i am at the root i believed
```
jwxie@ubuntu-804-goko: ~$
```

then i type each respectively

```
wget http://wordpress.org/latest.tar.gz
tar zxvf latest.tar.gz
sudo cp -R /home/jwxie/wordpress/* /var/www/nginx-default/
```

once i completed the last command, i got just a blank message
```
jwxie@ubuntu-804-goko: ~$
```
is this really normal? 
shouldn't the system shows "you have sucessfully copy / move it to the destinated location"? ( this is just my thought)


okay, if it is, then how do i check if wordpress has already move to nginx-default?

is there any command that i can check to list the folder and files at a specific direcotry, instead of using cd xxxxxxxxxx

#2
```
sudo cp wp-config-sample.php wp-config.php
sudo nano wp-config.php

```
since i don't think the file has been cp to nginx-default, i don;t know, not sure, it doesn;t work, it shows, no such file or direcotyr

i am looking forward to receive some great help ^^
thank you:):)
and when i checked [http://goko.no-ip.org/wordpress/](http://goko.no-ip.org/wordpress/)
it shows 404, not found, so ....please help me out with these newbie questions^^

---

### Post by cariboo on 2008-08-07
Commands like cp and mv and I'm sure lots of other don't acknowledge that they have successfully completed a task. If you want to know what is happening use -v for verbose.

If you want to check to see if the files are in the directory you copied them you can cd into the directory eg:

```
cd /var/www/nginx-defaul/
```

and then:

```
ls -la
```

For a listing of the files.

If this is where you want the wordpress files to live then remember, you have to change the document root in /etc/apache2/apache2.conf to reflect this change.

**Ignore the stuff about apache, I didn't know what nginx was**

Jim

---

### Post by jwxie on 2008-08-07
oh nvm with the two questions

---

