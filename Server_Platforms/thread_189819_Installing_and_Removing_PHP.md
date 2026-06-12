---
title: "Installing and Removing PHP"
date: 2006-06-05
forum: Server Platforms
---

### Post by Freddie on 2006-06-05
A while ago, before PHP5 was available in the Ubuntu repositories, I followed the guide on the Ubuntu wiki (which is now a re-direct) to install PHP 5.0.4 from source. But times change and I now feel that it is best if I use the PHP5 packages from the Ubuntu repositories rather than my own. However, I am not sure how to remove my current version of PHP (Apache2 and PHP 5.0.4, which I used a make install command to install) and then install the ones from the repositories.

Thanks for any help/advice you can give me.

---

### Post by goneskiing on 2006-06-05
Well you can use synaptic - remove all the php files you can find - then make sure all /etc/php5 files are removed.  Then log out (cleans out any caching) Then re-install.  Then you might have to reinstall several of the packages (I had to reinstall both my apache and postgres php files).  I'm not sure why this happens - either there are problems in the packages or in synaptic but after reinstalling Php if some module doesn't work - remove it - log out and then log back in and reinstall it.  I also had to do that in my /etc/apache2/mods-enable - remove the existing php mod and then re a2enmod php5.  Frustrating but hope that helps.

---

### Post by LordHunter317 on 2006-06-05
If you left the sources around, you can do 'make uninstall' to remove the installed binaries.  

Hopefully you installed to /usr/local or a similiar place, in which case the software should be self-contained and easy to remove.  If not, you should do that in the future and there is no good way to track down what was installed.

---

### Post by Freddie on 2006-06-06
I have kept the source around - but the PHP developers forgot to put in an uninstall command so there is little that I can do. This is the guide that I used to install it: [https://wiki.ubuntu.com/PHP5FromSource?action=diff](https://wiki.ubuntu.com/PHP5FromSource?action=diff) not sure if it will help with me uninstalling it, but thanks anyway.

---

### Post by Freddie on 2006-06-15
Does anyone have any ideas? Someone must have had this problem before, as what do the people who compile PHP all the time do when they want to update to a newer version, do they just compile it and type make install over the top?

---

### Post by Eagleorn on 2006-06-27
I also have this problem, I have compiled php5 on my own, and  I used the default location (/usr/local) for installation. But how can I get rid of it? I used synaptics and removed everything that has to do with apache2 and php, but I am still able to run command such as php -m from the terminal and get a complete list of in compiled modules

---

### Post by lamego on 2006-06-27
If you do install from sources and don't want to mess with the rest of the package you should use something like /opt/appname for the installation dir.
Now is a bit late, according to the procedure you should have the apache and php installed on /usr/local, spread over several subdirectories, you will need to find the related files and deleted them manually or try to find an automated way to list the installed files.

There is a utility program to create debian packages, the name is "checkinstall", this utility checks for every file installed by "make install" and creates a debian package from it. You probably will be able to install/remove this debian package created from the source installation and remove the files, please note that I have never tested this.

---

