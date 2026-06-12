---
title: "newbie help need setting up website"
date: 2009-10-02
forum: Server Platforms
---

### Post by Jdratcliffe on 2009-10-02
[http://ubuntuforums.org/showthread.php?t=1277260](http://ubuntuforums.org/showthread.php?t=1277260) - outline of story

i have sorted the server out i can "see" both machines from home - now looking to host a copy of my site on this ubuntu server so i can see changes "live" without affecting the main site..? bit of a newbie so please go slow for me need to know how to get this website running as had loads of changes to add to this site but dont want to do this live.

---

### Post by Jdratcliffe on 2009-10-02
:s 30 views and no one can give my a hand..?

---

### Post by stlsaint on 2009-10-02
why dont you just setup the LAMP server using the [UbuntuServerGuide]("https://help.ubuntu.com/9.04/serverguide/C/index.html") and transfer all website files over from main site to 'test' vps into the apache2 folder. Then you will be able to see it all local on your home system before testing on main site...or you can look into [CHROOT]("http://en.wikipedia.org/wiki/Chroot")! Using chroot you can setup and test apps and updates before putting on main system.

---

### Post by BQAggie2006 on 2009-10-02
How is the web page developed? If it's basic HTML/JavaScript/Flash without any server side scripting or database backends, then a general Apache installation is all you need__[]("http://ubuntuforums.org/member.php?u=814785").

First, you will need to install Apache:
```
sudo apt-get install apache2
```

Once the installation is complete, you can copy all the web files from the production server to the /var/www folder and then you will be able to access this development site.

However, if the site goes beyond basic with PHP/Ruby/Java/etc and/or runs a database backend, then you will need a little bit more installation and configuration.

Let us know how your web site is developed and we can give you a bit more guidance.

---

### Post by Jdratcliffe on 2009-10-05
its a php site with database back end the live version is [www.carnivalproperties.co.uk](www.carnivalproperties.co.uk)

---

### Post by BQAggie2006 on 2009-10-05
Do you know which DB backend it is running?

---

### Post by Jdratcliffe on 2009-10-30
no i dont unfountunatly

---

### Post by cariboo on 2009-10-31
You're making it pretty hard to give you any help, with out knowing what it is you need. What is the server running, is it Apache? IIS? or some other web server. What database postgresql, mysql or mssql?

---

### Post by headvampyre@hotmail.co.uk on 2009-10-31
you need to find where server files are stored but i think youll have to do this live so try and prepare the pages before you host and if ur on apache try /opt/lampp/htdocs

---

