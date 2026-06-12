---
title: "Gallery1"
date: 2006-11-16
forum: Server Platforms
---

### Post by mzracer360 on 2006-11-16
I can't seem to install Gallery1 properly.  I follow the instructions on [easylinux.info]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Gallery1_for_Image_Gallery_Server_service"), but when everything installs, I don't have a gallery folder, it does however create the album folder.  I am running 6.10 Edgy LAMP.

---

### Post by mzracer360 on 2006-11-18
Anyone else have this problem?  I'm still not able to install it properly.

---

### Post by lime4x4 on 2006-11-22
i'm having the same issues

---

### Post by lime4x4 on 2006-11-22
okay i solved it. For some reason when u install gallery it will install a folder called albums in /var/www and it will also install a folder called gallery in /usr/share. you have to choices here 1 copy the folder gallery from /usr/share to /var/www or create a link in the /var/www directory

i will cover both here. I beleive all www content should be installed in /var/www 
open a terminal and type

cd /usr/share

then type

sudo mv gallery /var/www

then type

cd /var/www

then type

sudo chown -R www-data:www-data gallery

then type

sudo gedit /gallery/setup/init.php

around line 27 your going to see a line like this

require ('/usr/share/gallery/util.php');

change it to 

require ('/var/www/gallery/util.php');

then save and exit out of text editor

then type this 

sudo sh /var/www/gallery/configure.sh

then follow the rest of the instructions on that page u linked to

the simple and easy way of also doing it is

in a terminal window type this

cd /var/www

then type

sudo ln -s /usr/share/gallery gallery

---

### Post by vmartins on 2006-11-22
Try this two How-To's:

[http://www.howtoforge.com/gallery2_multisite_ispconfig](http://www.howtoforge.com/gallery2_multisite_ispconfig)

[http://www.howtoforge.com/gallery2_codebase_ispconfig](http://www.howtoforge.com/gallery2_codebase_ispconfig)

---

