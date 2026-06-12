---
title: "Apache Webserver In Web Min"
date: 2006-09-24
forum: Server Platforms
---

### Post by tc3racer on 2006-09-24
Hey guys im a beginner at linux and i still not up to scratchs with it. I have just installed the LAMP version of ubuntu on a P3 500mhz machine that previously ran windows 2000 it running nice and smooth  however i have just installed web min and found that this resolved some of my problems that i posted last week about samba however im now trying to set up an _INTRANET_and im not sure how to set up apache webserver in webmin i dont want to set up a virtual host i just want to get one site going at the moment. im not even sure if the defalt server is working or not please help me.:| :confused:

---

### Post by etcpool on 2006-09-24
just please calm down and tell us what you exactly want at first ,

then someone here can give u a first go!

remember to calm down.....


your apache2 configuration files is in /etc/apache2/   the main configuration files is the apache2.conf  and all mods you might want to enable or disable is just in the mod available, but just only the mods that have been made linked to the /etc/apache2/mod-enable is just workable, as same as your virtual sites.. most of them are stored at /etc/apache2/sites-available. there're the commands for ubuntu but i don't remember, just don't remember but, just make the symbolic line from /etc/apache2/site-available to /etc/apache2/site-enable the these your virtual-sites should work fine , 

or if you want them to run strait through just create your configuration of you virtual host in /etc/apache2/site-enable the those should work fine too !


for the case of yours only one site needed just only edit your /etc/apache2/sited-available/default file and then add your file to your /var/www/html path make sure to replace the index.html or have it in place for the peace..



now hope you should have a peace living with it in apache2 part...

---

### Post by tc3racer on 2006-09-25
Hello

as i said in the last post i want to get an intranet working on my home network i have set up a lamp install of ubuntu which is ok however i have installed a program called web min how do i find out if the server is working and wen i click on apache webserver in web min i get asked for default server or virtual host which one do i click on.i just want to be able to host an intranet for the momonet on a LAN using apache webser please help

---

### Post by bluefrog on 2006-09-25
See the first answer to your post. 
Just put you files in /var/www (basically) and you're up and  running.

Installing webmin to make apache running is a bit useless as apache is running fine when you install it from synaptic. So you end up having to learn how to configure webmin to control apache instead of concentrating on apache itself.

So if you are a linux beginner I'd rather suggest you to stick with apache only and asks if you have problems with it.

James

---

### Post by tc3racer on 2006-09-25
Hello Blue Frog I dont understand what you are saying i just want a gui so that i can control apache and i just want to be able to host an intranet.

Please Help](*,) :confused: :-?

---

### Post by bluefrog on 2006-09-25
install your web folder and html files into /var/www/ and you are up and running.

I understand you may want a gui to administer apache but you will need to learn how webmin works first (to set the apache modules config for example wihtin webmin)

So if you really want an intranet running as of yesterday, just throw everything in /var/www/.

you know that apache is working by accessing it thru your internet browser at [http://localhost](http://localhost) (from your apache hosting machine)


[http://www.linux.org/lessons/advanced/index.html](http://www.linux.org/lessons/advanced/index.html)

James

---

