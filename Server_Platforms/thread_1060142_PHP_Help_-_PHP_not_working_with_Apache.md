---
title: "PHP Help - PHP not working with Apache"
date: 2009-02-04
forum: Server Platforms
---

### Post by Alexander Barnes on 2009-02-04
Hi, I'm a student in a class we are using LAMP.  I seem to be unable to get PHP to work.

Using Hardy Heron with Gnome on ThinkPad r52 32bit laptop.

-----------------------
Disclosures:
I posted to kubuntuforums.net a few days ago but no replies there.  
[http://kubuntuforums.net/forums/index.php?topic=3101389.0](http://kubuntuforums.net/forums/index.php?topic=3101389.0)

I am not using a server platform except insofar as apache is a web server...it seems that most apache related thread are in this forum - my Linux install is not to the best of my knowledge a full-blown server installation.
-----------------------


1) Successfully installed Apache using apt-get.  Pointing my browser to [http://localhost](http://localhost) brings up the default index.html with "It Works!".

2) Successfully installed php5 with apt-get.  Checked a2enmod and verified that it is enabled.  Also have installed libapache2-mod-php5, php5-common (the latter two installed with Apache packages I believe)

3) I'm a little confused about permissions and users but for now...I've used sudo to put some simple files into /var/www -- in particular, a file called test.html which has the following content:

<?php

echo "Hello World....???";

?>

4) Pointing my browser to [http://localhost/test.html](http://localhost/test.html) brings up a blank screen (not a hello world message as hoped).

Thanks for any insight.  I'm a 6-month Ubuntu newb with Gnome on my laptop and KDE on my desktop.

---

### Post by spiderbatdad on 2009-02-04
```
http://localhost/test.php 
```Also rename the file to test.php

---

### Post by Alexander Barnes on 2009-02-04
Thank you...wow.  Very simple -- but I thought everything looked right so I'm not surprised :-)

---

