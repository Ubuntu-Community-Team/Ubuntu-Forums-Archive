---
title: "Apache 2 help!"
date: 2008-12-02
forum: Server Platforms
---

### Post by chrini on 2008-12-02
Hello all,

I used to use apache 2 to preview my php web pages before posting (it´s been more than a year since I have made a web page) and now that I have it on my home computer it doesn´t seem to be working as I remember. I thought I used to type in (for example):

[http://[IP](http://[IP) address]/var/www/[file].php

and it would load my php file. But now it is saying ¨404 Not Found¨. I have also tried just:

file:///var/www/[file].php

and it wants to download the file.

I have done quite a bit of research, but nothing seems to fix it. Can someone remind how to open a php file in the web browser and/or how to fix my apache2/php5 problem.

Much appreciated, thanks!:guitar:

---

### Post by GROMS on 2008-12-03
The only thing I can think of would be character case in part of the name or file extention. If your browser is Firefox, use the File/Open File which will let you search for the file. 

Now then, I'm new to Linux and want to install the Apache 2 web server on my desktop. I see that it is in the Package Manager but don't know if there are any dependencies needed (there are 12 related items shown) and with PHP 5.  I also want to add Pearl, Python and Ruby. Is there a quick lesson I can find??

Stephen

---

### Post by chrini on 2008-12-03
I think you can just do a 

> sudo apt-get install apache2 php5

From my experience, if there are dependencies then it won't install it.

Or you can install it from the synaptic package manager as well, it will also fail to install if there are dependencies.

Hope that helps.

> The only thing I can think of would be character case in part of the name or file extention. If your browser is Firefox, use the File/Open File which will let you search for the file.


That is pretty much what I did in my second case

> file:///var/www/[file].php

and it just tries to download the php file, when I really want it to load as a webpage. Like the one you are looking at right now:

> [http://ubuntuforums.org/newreply.php](http://ubuntuforums.org/newreply.php)

Any other thoughts out there?

---

### Post by puppywhacker on 2008-12-03
hi,

If you do a file://somefile.php it will not use your webserver and will use straight file access, which means the browser wouldn't receive a mime-type and the file will just be displayed or downloaded.

the webserver uses /var/www as it's root directory so try accessing the php as this:
```

http://[IP address]/[file].php

```
if that downloads as a file you may still have to
```

apt-get install libapache2-mod-php5

```

and restart the webserver after all changes
/etc/init.d/apache2 restart

if that still doesn't work check that /etc/apache2/mods-enabled/php5.conf exists and contains an "AddType" for php5

goodluck

---

### Post by GROMS on 2008-12-03
edit 12/3.08 6:52
Did the apt-get as you suggested and it downloaded and installed. Using the default [http://127.1.1.1](http://127.1.1.1) I got the default file  var/www/index.html which says "It works". I tried to edit the file but was denied saving it. Like you, I could not get a file from another location without it being put in an editor. I went looking for the apache program but can't find where it was installed. Aparently you need root access to www. Is there any documentation? I installed the apache2-doc but cant find it either.
--------------- 


Only thing I can think of is that for some reason it doesn't see it as a php file - that or something is messed up in one of the settings. Very strange problem.

Rambling - When you try to open a php file in stright windows xp, it will ask for what application you want to use. Again on win, using the FF browser and the get file {file:///C:/Documents and Setting/name/Desktop/login.php} it loads the file and displays it correctly. Now then, with this file, if I try to interact [ like a submit button] I get an error 'File not found' ..../php/<?php print $_SERVER['PHP_SELF'];?>.

Thought, maybe it is the browser settings? Somehow it's not seeing that it needs to call the php interpiter. Maybe there is a setting in Apache2 isn't set right.

I know this doesn't answer the question but hopefull will give you other places to look.

Stephen

Ps: the apt-get worked.

---

### Post by sierd on 2009-04-26
what you can do too is 
```
sudo apt-get install phpmyadmin
```
this wil install a webserver with apache2 and mysql and php5 and phpmyadmin

---

### Post by Sef on 2009-04-26
Moved to server platforms.

---

