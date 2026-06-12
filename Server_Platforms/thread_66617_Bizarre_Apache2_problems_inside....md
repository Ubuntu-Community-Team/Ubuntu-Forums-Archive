---
title: "Bizarre Apache2 problems inside..."
date: 2005-09-17
forum: Server Platforms
---

### Post by daveisadork on 2005-09-17
Ok, I'm having a very strange problem. If you crack open a browser window and try to go to [http://www.davehayes.org](http://www.davehayes.org) , the browser attempts to download my index.php file and doesn't know what it is. Same happens if I enter [http://localhost](http://localhost) The weird thing is, if you go to [http://davehayes.org](http://davehayes.org) or [http://69.137.83.185](http://69.137.83.185) or [http://www.davehayes.org/index.php](http://www.davehayes.org/index.php) then it works fine. I'm using apache 2.0.54 and php 4.4.0-2. Any ideas?

---

### Post by Burke on 2005-09-17
try this:

sudo /etc/init.d/apache2 restart

This will restart apache, and maybe it will work...  if not, maybe this:

sudo a2enmod php4

...this will enable the php4 mod for apache if for some reason it is disabled... or try:

sudo apt-get install php4 apache2

to make sure the packages are installed and are the newest version. Or maybe none will work... try them, anyway, then post back.


EDIT:  Never mind, seems to me like your page is working... browser issues, maybe?

---

### Post by daveisadork on 2005-09-18
[QUOTE=Burke]try this:

sudo /etc/init.d/apache2 restart

This will restart apache, and maybe it will work...  if not, maybe this:

sudo a2enmod php4

...this will enable the php4 mod for apache if for some reason it is disabled... or try:

sudo apt-get install php4 apache2

to make sure the packages are installed and are the newest version. Or maybe none will work... try them, anyway, then post back.


EDIT:  Never mind, seems to me like your page is working... browser issues, maybe?[/QUOTE]

The browser thing got me thinking because I had only tried it in Epiphany and Firefox, both of which acted the same: trying to download the file instead of displaying it. However, IE6, Opera and Galeon all displayed the page. Could someone else verify [http://www.davehayes.org](http://www.davehayes.org) for me using Epiphany or Firefox?

---

### Post by Burke on 2005-09-18
I'm using FFox1.0.6 and it works fine.

---

### Post by pgmario on 2005-10-14
I had exactly the same problem, "fixed" it by doing a
 ```
dpkg -l | grep apache
``` and running 
 ```
sudo apt-get remove --purge
``` on the results.
 Then installed apache2 and php4 again and everything was fine.

---

