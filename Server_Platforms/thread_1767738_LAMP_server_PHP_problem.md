---
title: "LAMP server PHP problem"
date: 2011-05-26
forum: Server Platforms
---

### Post by doctorstupidmd on 2011-05-26
sorry if i am a noob, i normally dont ask for help that much, but this **** has me so frustrated.

ive been running my linux box as a lamp server for months now with minimal problems.. all the sudden the other day it stops running my PHP scripts.. it started downloading them instead. then it got to the point where it would not show respond to any requests at all, so i was going to reinstall lamp-server^...

but every single way i tried to remove the packages.. forcing them.. EVERY single way.. it said the packages were broken... 

i decided a clean reinstall of the OS was the easiest way. but it didnt work.. its now back up with .html docs... but apt-get still will never be able to remove them (i have to use tasksel) 

ive done 4 reinstalls of the OS today alone.. same thing every time. wont run PHP... yet all the necessary software is installed and processes are running

i dont understand why this could not work after a clean install of everything! theres nothing to pollute it!!!

im also sure my PHP is error free (im only using the include() and date() functions.. pretty easy to debug) 

i dont understand how everything can go wrong all at once? 

like i said.. it works well with straight html and css now.. it has to be that the PHP is not configured right.

but i am using the default config! argghh! please help

---

### Post by boutch55555 on 2011-05-28
Assuming your php code gets executed right from the command line :
```
php /path/to/file
```
I would assume you miss the php apache mod :
```
apt-get install libapache2-mod-php5
```

If that doesn't work, check if the php is enabled :
```
a2enmod php5
```

And I'm out ou ideas... 

Look for errors in 
```
/var/log/apache2/error.log
```

???

---

