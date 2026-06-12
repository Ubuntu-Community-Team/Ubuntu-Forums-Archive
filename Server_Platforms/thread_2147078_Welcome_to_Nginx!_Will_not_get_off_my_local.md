---
title: "Welcome to Nginx! Will not get off my local"
date: 2013-05-20
forum: Server Platforms
---

### Post by diaz21 on 2013-05-20
Hello to everyone that will read this,

     Lets start by saying I am completely new to Linux but am pretty well off on my computer skills. I was trying to set up a Drupal site for my employer and saw a link talking about running Drupal 8. It recommended that I used nginx so I installed it. Once that was done and I took care of installing php5,mysqlAdmin, and apache2 i had the issue of whichever pages I created even when there is only an index.php file in the var/www/ file that seems to still pop up with nginx. With my frustration I did uninstall nginx which i have checked to see if those files are gone and it does say it is. I checked by doing a cd /var/www/  and then ls which shows a index.php and myPhpAdmin. 

    I am still having issues with even starting apache as well. I get a 87: ulimit: error setting limit (operation not permitted) (13) Permission denied: for 80 and 0.0.0.80. I know i seemed to have this problem about some kind of password phrase key that I thought I fixed before but is apparently not working now. 

Is there anyway that nginx might of made some files invisible?
 By chance is Apache2 Server have some setup that was messed with to have it auto direct files to this nginx site?
Is there a more permenant solution to getting apache2 to start up with no issues? (this problem I will probably figure out myself as I tried uninstalling apache2 to see if that would fix it so I think i have to reset that password stuff.) 

Any way, any help is greatly appreciated. I am not to savvy with Linux so I am unsure of what to post for you guys to make things easier. Please let me know what I could post for you to help though. 
I do know that I have Ubuntu 13.04 and so far have very standard settings.


*Added 5/20/2013*
I have worked passed the password issue but i get a 98 address already in use. I use the sudo netstat -ltnp | grep ':80' and it shows me that nginx is using the sockets. If I kill it, it takes the next socket and then is tagged as nginx: worker. Not sure why this exists since i uninstalled nginx.

---

### Post by matt_symes on 2013-05-20
Thread moved to **Server platforms**.

---

### Post by sandyd on 2013-05-21
If its still using the default configuration, the folder that nginx serves from is /usr/share/nginx/www

The directories that are in use can be checked by running
```
cat /etc/nginx/sites-enabled/* | grep root| sed 's/^[ \t]*//' | sed '/^\#/d'
```

Nginx can be removed by running
```

apt-get remove nginx nginx-*
```

---

### Post by diaz21 on 2013-05-24
Sandyd,

    Just want to start by saying thank you for taking the time to help me. I ran the first code string that you gave me and it get:

    root /usr/share/nginx/html; 

    I am guessing that I need to change the path of what is being used somehow to go to my index.php that I have created in my /var/www folder?

    I also ran the second string of code which I had to add sudo to allow admin privileges and that did remove everything nginx but still did not change that path which I would think it would of taken it out and just left me with a blank screen when i web search localhost. I am sadly running out of time at work and will not be back in till Wednesday which then I will try to see how to change the path for sites enabled. Since I am new to Linux I really do not understand what the first code string does (by code bit by bit). I did try looking at some of your posts and threads from before that had to do with something kind of similar.

---

### Post by CharlesA on 2013-05-24
The first code tells you what Nginx is serving. The second code tells apt-get to remove nginx.

Run this to make sure nginx isn't running anymore:

```
sudo netstat -nlp | grep 80
```

---

### Post by diaz21 on 2013-05-29
it shows that 1285/apache2 and 1258/dhclient are running.

---

### Post by diaz21 on 2013-05-29
Actually,

    I just checked it today after having a restart and seems to be working now. Thank you for all of your help! :D

---

### Post by diaz21 on 2013-05-29
OK so how do I mark a thread as solved?

---

### Post by CharlesA on 2013-05-29
> **diaz21 said:**
> OK so how do I mark a thread as solved?

You need to edit the Original post and change the prefix. I have done that for you. :)

---

