---
title: "convert ubuntu-desktop to ubuntu-server?"
date: 2006-09-01
forum: Server Platforms
---

### Post by snek on 2006-09-01
Ok I am currently not aware if there is a package called ubuntu-server, but I named it that to make my point clear :tongue:

Anyways, I have an ancient laptop which can not boot from CD or USB, and I managed to get Ubuntu 6.06 running, which I later converted to Xubuntu 6.06. However I don't really plan on using the laptop anymore, so I want to only use it as a low-power server. The Ubuntu Server package is great but I can't install that since I have no CD or USB boot support.. Is it possible to just install it like ubuntu-desktop/xubuntu-desktop? 

Otherwise I'll be stuck with just uninstall ubuntu and putting debian on it with XAMPP or something.. But I'd prefer to stick with ubuntu, since I've really gotten used to it now.

---

### Post by Titus A Duxass on 2006-09-01
You can remove the Ubuntu/Xubuntu desktop and you will have pretty near the server install.  There might be a few apps or packages lurking that will never be used.

---

### Post by snek on 2006-09-01
Yeah, that's sort of my problem at this moment though.. I fear I have many packages installed which are not being used, as my 4GB hdd in that laptop is basically full. Which is a bit odd because after initial install & upgrade of Ubuntu I had quite a bit of space left still, so I'm a bit confused as to where it all went..

I was just thinking that the server install would have nice(r) features for managing the various server components like apache/php/mysql.

---

### Post by chrisfay on 2006-09-01
> I was just thinking that the server install would have nice(r) features for managing the various server components like apache/php/mysql.  

I think the server version differs only in the lack of a GUI and the inclusion of a LAMP stack (if you choose that option). Additional admin features would have to be installed on top of the base installation from the CLI.

If you already have Apache, MySql, and Php installed on your desktop, removing your GUI would effectively be the same as installing the server option with the LAMP stack; obviously with the edition of extra packages you've installed. 

I'm not sure but depending on whether you installed the desktop version originally or upgraded the server version with ubuntu-dekstop using aptitude you may be able to remove it using aptitude. I don't know for certain and am curios about doing it myself...

---

### Post by blubbi321 on 2007-09-14
hi there.

i got a similar problem. ive got ubuntu-desktop installed on a slow machine and want to convert it to a server installation.

apt-get remove ubuntu-desktop did nothing :/

which pakets do i need to remove in order to get my server version?

thanks in advance

---

### Post by smartboyathome on 2007-09-14
You can do a "apt-get autoremove ubuntu-desktop" after you install it again, and it should remove all of its dependancies. Then, do an "apt-get install ubuntu-server"

---

### Post by mikewhatever on 2007-09-14
Try 'sudo apt-get remove ubuntu-desktop' in recovery mode, the second boot option.

---

### Post by smartboyathome on 2007-09-14
sudo apt-get remove won't do anything but remove the ubuntu-desktop package (that is it). That is why you need to do autoremove in order to remove the whole bundle.

---

### Post by blubbi321 on 2007-09-14
apt-get autoremove ubuntu-desktop seems to do the same as just "remove" :/

---

### Post by kugn on 2007-09-15
perhaps it should be "apt-get autoremove" after you've already "apt-get remove ubuntu-desktop"

---

### Post by blubbi321 on 2007-09-16
no sorry ... i already tried that :/

---

