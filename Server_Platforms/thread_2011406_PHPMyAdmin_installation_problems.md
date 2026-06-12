---
title: "PHPMyAdmin installation problems"
date: 2012-06-27
forum: Server Platforms
---

### Post by FransG on 2012-06-27
As always, PHPMyAdmin proves it's unfriendlyness with yet another installation problem.
 
The installer asks wether i want to install to lighttpd or apache2, the terrible installer want you to press space to mark one of these options but when you press enter you mark nothing and just continue the installation blank.
 
Reinstallation does not prompt me this option again so I cannot correct this. Now I only have a foler in etc/phpmyadmin with some config files.
 
Please help, once again this is costing me hours and hours..

---

### Post by Balgrath on 2012-06-27
questions: do you have Apache installed? and are you building a home webserver???
 
if you are building a home webserver there are hundreds of TUTs out there but in breif I personally install a base os with SSH, then install apache2, mysql server && client and php5. I makesure I can see the "it works" page and then install phpmyadmin and select the apache option and select no for the DB config part. and you should now be able to connect to the phpmyadmin console via http:\\YOURSERVERIP\phpmyadmin and get a login prompt. user the mysql root user and pass you set up to connect and make another that can admin the console.
 
if you have nothing of interest on the box you could trash it and try once more. I would also suggest before you make a change to a file you save a copy i.e. cp xxxx.yy xxxx.yyy.bak or your own convention.. this way you can copy the original or known working version back to the original name. I make a .orig for the original file and then on my working file i backup as .wrkDATEOFSAVE
 
 
 
 
cheers
Balgrath
 
** =; all advice is given as is and I accept no responsibility for my suggestions, use at your own peril **

---

### Post by kennethconn on 2012-06-27
phpMyAdmin is a breeze to install - you made the mistake by not pressing the spacebar and selecting your webserver before you pressed return, so quit complaining about phpMyAdmin. You should ensure that your webserver is up and running first, if you have not done so.
 
If you have not set it up yet, I would imagine a purge followed by an install should get you back to where you want to go.

---

### Post by trundlenut on 2012-06-27
There was and still maybe a bug in the installation package for phpmyadmin in 12.04.  Look [here]("http://ubuntuforums.org/showthread.php?t=1980715").

I am assuming that you have completed the installation but when you go to the webpage you just get a 404 error.

---

