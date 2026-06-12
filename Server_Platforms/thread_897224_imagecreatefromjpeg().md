---
title: "imagecreatefromjpeg()"
date: 2008-08-21
forum: Server Platforms
---

### Post by Detrol on 2008-08-21
Hello, im getting this error:

Fatal error: Call to undefined function imagecreatefromjpeg() in *

On one of my pages.

I have been reading through various posts regarding the same problem but their solution hasnt worked for me. Such as:

running sudo apt-get install php5-gd

adding extension=gd.so to php.ini , uncommenting extension_dir and setting it correctly.

What else could there be?

Thanks in advance!

---

### Post by windependence on 2008-08-22
What php application are you using, i.e. message board, CMS, Drupal, etc.

This message comes up frequently when trying to open remote URLs in php code and your fopen wrapper in php.ini is not set to On. If this is your own code, you should be aware that this is a security risk. To test and see if it works, edit your php.ini file and insert this line:

```
allow_url_fopen = On 
```

or if that doesn't work you can try:

```
allow_url_fopen = 1
```

-Tim

---

### Post by Detrol on 2008-08-22
Thanks but no go.
Im running an image hosting site, so no remote URLs, and the option was set to On, tried with 1 either way but no difference.

---

### Post by windependence on 2008-08-22
Well remote  is a relative term. If it's outside your doc root it is considered remote. :)

I will keep looking for more ideas and post them here for you.

-Tim

---

### Post by Detrol on 2008-08-22
Ahh alright :), well it is, but tried putting it in the root folder, made no difference either.

And thanks, ive yet to find a solution.

---

### Post by cpetercarter on 2008-08-22
You have restarted apache since installing php5-gd?

---

### Post by Detrol on 2008-08-22
Yeah, countless times :)

---

### Post by cpetercarter on 2008-08-22
Ok. And if you run phpinfo(), does the output show that the gd module is in fact installed and enabled?

---

### Post by Detrol on 2008-08-22
Hmm... no =/

Only GD in there is

"additional .ini files parsed 	
/etc/php5/apache2/conf.d/gd.ini"

Thats it.. 
Inside that file it says extension=gd.so

---

### Post by cpetercarter on 2008-08-22
This is a pure guess. When I installed the gd package on my computer, I simply downloaded php5-gd from Synaptic Package Manager - no editing of php.ini was required at all - restarted apache, and it worked out of the box. Most of the other posts which I have seen on this subject simply say ```
sudo apt-get install php5-gd
``` with no mention of needing to change any of the php.ini files.
Why not try undoing the changes you made to php.ini (so that php will revert to the default configuration), restart apache, and then run phpinfo() again.
And if that doesn't work, try uninstalling and re-installing the php5-gd package, in case there is a problem with it.
Sorry if these are all things you have tried already.

---

### Post by Detrol on 2008-08-22
Thanks for the reply, i didnt try reinstalling it before, just did though, made no difference, and as far as i can tell the php.ini file has been restored properly aswell.

Im all open ears for suggestions.

---

### Post by windependence on 2008-08-23
Well obviously the module for GD isn't loading. We'll have to find out why.

-Tim

---

### Post by Detrol on 2008-08-26
Sorry was a way for a few days, and yeah. Well according to phpinfo():

```

additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/pdo_sqlite.ini, /etc/php5/apache2/conf.d/sqlite.ini 

```

gd.ini is loaded which says "extension=gd.so" , which should lead to: /usr/lib/php5/20060613+lfs

Where all .so files are ( gd, mysql , pdo ).

What else could there be? shouldnt it be loading just fine by that?

---

