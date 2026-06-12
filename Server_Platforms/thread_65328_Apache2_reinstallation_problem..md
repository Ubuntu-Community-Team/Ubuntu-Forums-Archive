---
title: "Apache2 reinstallation problem."
date: 2005-09-13
forum: Server Platforms
---

### Post by sviestainis on 2005-09-13
Hi, I decided to reinstall apache and all of it's configuration, but when i deleted /etc/apache2 folder content and did "apt-get remove apache2 | apt-get install apache2", I found out that the files are still missing. My old configuration is screwed up, but i have no idea where to get new one. Can anyone help me?

---

### Post by rmrf on 2005-09-14
try this:

sudo apt-get remove --purge apache2
sudo apt-get install apache2

type the commands separately to remove any confusion on errors or messages. the first one should completely remove any instance of apache2, and the second will obviously install apache2. I would recommend not deleting the folder manually next time, just use the purge command to remove the folders/files.

hth

---

### Post by tonym on 2005-09-19
apache2 is only a meta package that then pulls in other packages.  Search and remove all packages including apache2 in their name then reinstall apache2.

---

### Post by flightcrank on 2005-09-20
[QUOTE=tonym]apache2 is only a meta package that then pulls in other packages.  Search and remove all packages including apache2 in their name then reinstall apache2.[/QUOTE]
 i deleted my folders for apache and apache2. the actual /etc/apache and /etc/apache2

how would i go about reinstalling apache 2 ?.  because it says its installed, but the folders are empty

---

### Post by tonym on 2005-09-21
Depends on what tool you use to update packages - apt-get,  aptitude, synaptic, kynaptic, kpackage etc

Use that tool to locate and remove any apache2 packages.  Use the purge option rather than just remove so it removes config files.  Then reinstall.

---

### Post by flightcrank on 2005-09-21
[QUOTE=tonym]Depends on what tool you use to update packages - apt-get,  aptitude, synaptic, kynaptic, kpackage etc

Use that tool to locate and remove any apache2 packages.  Use the purge option rather than just remove so it removes config files.  Then reinstall.[/QUOTE]

i did all that but when i reinstall all the folders are still empty !! . what should i do

---

### Post by flightcrank on 2005-09-21
[QUOTE=flightcrank]i did all that but when i reinstall all the folders are still empty !! . what should i do[/QUOTE]
 actualy dont worry, i compiled it from source, and its working now. but i have another problem, for example. on my old server i could add directorys to my apache DocumentRoot and then type.

 [www.mystite.com/directoryname](www.mystite.com/directoryname) 

and it would automaticly find the index.html file and display it. now its says im "Forbidden" and dont have access but i have set all the permissions corrcetly.

so how do i make my apache server reconise any directorys in the document root, and display the index.html file them ?

---

