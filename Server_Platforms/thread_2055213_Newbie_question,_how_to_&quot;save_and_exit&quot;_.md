---
title: "Newbie question, how to &quot;save and exit&quot; in Terminal"
date: 2012-09-08
forum: Server Platforms
---

### Post by felinoel on 2012-09-08
Original issue resolved,  see [here](http://ubuntuforums.org/showthread.php?p=12228387#post12228387) for current issue.











I was following a guide and it said to save and exit... but it doesn't say how?

[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
> Now check if php is working :

```
$sudo vi /var/www/info.php
```

and add

```
<?php
phpinfo();
?>
```

save and exit

---

### Post by randrews on 2012-09-08
Looks like you used the vi editor to create your file.

You should be able to press [Esc], then ZZ, to "save and close".

---

### Post by felinoel on 2012-09-08
> **randrews said:**
> Looks like you used the vi editor to create your file.

You should be able to press [Esc], then ZZ, to "save and close".
When I pres escape nothing happens, when I type zz it just remains like it was, no z's added.

---

### Post by randrews on 2012-09-08
Did you use capital Z's?

vi is... special.

---

### Post by felinoel on 2012-09-08
> **randrews said:**
> Did you use capital Z's?

vi is... special.

I used capital Z's I used r's and f's and capitals of those too, it wouldn't let me type anything.

---

### Post by randrews on 2012-09-08
You might want to consider a less mysterious text editor for now, to be honest.

You could use the same command as before to create your file, only instead of "vi" use "nano".

nano /var/www/info.php

---

### Post by steeldriver on 2012-09-08
agreed - use a simpler editor

however if you are already in vi, you can use

```
ESC
:wq
```

(ESCape gets you out of insert mode; then "colon w q" for **w**rite **q**uit)

---

### Post by felinoel on 2012-09-08
> **randrews said:**
> You might want to consider a less mysterious text editor for now, to be honest.

You could use the same command as before to create your file, only instead of "vi" use "nano".

nano /var/www/info.phpI don't know what vi is, I only followed the instructions and did it in the Terminal, if vi runs through the Terminal then idk

> **steeldriver said:**
> agreed - use a simpler editor

however if you are already in vi, you can use

```
ESC
:wq
```

(ESCape gets you out of insert mode; then "colon w q" for **w**rite **q**uit)Nothing types, not even a colon, because of this I pressed a bunch of buttons and now it says at the bottom, "search hit TOP, continuing at BOTTOM"

---

### Post by sandyd on 2012-09-08
Press Control+C to get out of any modes.
Type
:w to save
:q to quit

---

### Post by felinoel on 2012-09-08
> **sandyd said:**
> Press Control+C to get out of any modes.
Type
:w to save
:q to quit

"/var/www/info.php"
"/var/www/info.php" E212: Can't open file for writing
Press ENTER or type command to continue

---

### Post by steeldriver on 2012-09-09
OK let's get you out of vi - type

```
:q!
```to exit without saving your changes, then when you're back in the terminal either 

```
sudo nano /var/www/info.php
```and make your edits there; or you could just do

```
echo -e "\n<?php\nphpinfo();\n?>" | sudo tee -a /var/www/info.php
```

---

### Post by felinoel on 2012-09-09
> **steeldriver said:**
> OK let's get you out of vi - type

Oops, did not see the new page```
me@3MJ:~$ echo -e "\n<?php\nphpinfo();\n?>" | sudo tee -a /var/www/info.php
[sudo] password for me: 

<?php
phpinfo();
?>
me@3MJ:~$ 
```So... does it work now?


EDIT:
I went back to the guide and continued from there, it is now asking lighttp or apache2... I want phpbb3 though?

---

### Post by felinoel on 2012-09-09
After reading about the two I went with lighttp and now it is installed... right?

```
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
Lighttpd not installed, skipping
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

I go to the next step on that guide which is to go to either of these sites```
http://ip/phpmyadmin   or http://localhost/phpmyadmin
```and it is just simple phpbb stuff from there... but... those sites give me a 404 error?

---

