---
title: "Php5"
date: 2008-10-29
forum: Server Platforms
---

### Post by malatoforte on 2008-10-29
premise: php5 is installed and is running....so why if you click here [http://blackserver.hopto.org/forum/index.php](http://blackserver.hopto.org/forum/index.php) it ask you to download the index.php ????
Anticipate thx
(sorry for my bad english)

---

### Post by gpsmikey on 2008-10-29
Unless I have it wrong, PHP is a server side scripting - apparently the server you went to does not support PHP (or it's not enabled).  From the client side, it should not be able to tell there is any php embedded since what the server should put out is HTML.

mikey

---

### Post by malatoforte on 2008-10-29
i've installed ubuntu server edition
until 2 days ago all works very good...but the current went down and when i restart the server (my computer) begin a lot of problem...first apache2 dont wonna go and php too....now apache2 work very good but now php dont wonna work...and i dont have got any idea...

---

### Post by malatoforte on 2008-10-29
i've installed ubuntu server edition
until 2 days ago all works very good...but the current went down and when i restart the server (my computer) begin a lot of problem...first apache2 dont wonna go and php too....now apache2 work very good but now php dont wonna work...and i dont have got any idea...

---

### Post by cariboo on 2008-10-29
It works quite well from here. See Attached screenshot.

JIm

---

### Post by malatoforte on 2008-10-29
lol....so...i'm the only with this problem....
mmm
ok...now im confused....look what i see...
open me the download dialog

---

### Post by gpsmikey on 2008-10-29
I get the same image as cariboo907 does.  Looks fine (except it is in Italian :)  )  You might try it with a different browser or at least from a different computer to see if it is just on that one.

mikey

---

### Post by jpeddicord on 2008-10-29
> **cariboo907 said:**
> It works quite well from here. See Attached screenshot.

JIm

Same. Maybe it's a caching issue? To those having problems, try clearing your browser cache and restarting Firefox.

---

### Post by R.Bucky on 2008-10-29
Have you added this to your apach2.conf?

AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by malatoforte on 2008-10-30
i just clean firefox cache e added that 2 new line in apaache conf
THANX!!!!

---

### Post by Vegan on 2008-10-30
I would advise not modifying apache2.conf but rather put you stuff in httpd.conf which is intended for user configurations above the defaults.

---

