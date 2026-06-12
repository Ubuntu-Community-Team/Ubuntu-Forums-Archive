---
title: "Apache2 write permissions"
date: 2012-01-04
forum: Server Platforms
---

### Post by louis vitton on 2012-01-04
Hey guys,

I am having issues with the apache2 server write permissions.

I have a script which is attempting to make a cache directory upon request but atm apache2 is not allowing it to be written.

i made the root user part of www-data group and user the code below to assign www-data group access and write permissions to the folder "api" in which the script is places and i want it to then create the cache directory ".pheal-cache/public/public/map/Jumps/" under that.

Here is the current error message i am getting.
"generic error: 0 message: Cache directory '/var/www/api/.pheal-cache/public/public/map/Jumps/' isn't writeable"

root is part of www-data and www-data is the group that owns "api and all files and directorys inside of it"

I am running ubuntu 11.04 with apache "Apache/2.2.17 (Ubuntu)"

```

cd /var/www 
chgrp -R www-data api 
cd api 
chmod -R g-w * 

```

Cheers for any help.

---

### Post by dazman19 on 2012-01-05
your web server should be running as a user called www-data 

so all the files in the web folder should be owned by www-data.

if your web directory was say... /var/www/
then you would generally make all the files owned by www-data,

sudo chown -R www-data:www-data /var/www/ 

you dont want them owned by root... if you are editing them and they are changing to root as the owner, then you shouldnt really be doing php development as root.

what you can do is make all the files have Read/Write/Execute but do not do this for a production environment.

sudo chmod -R 777 /var/www/

use it on 777 to do your development.. when you are happy with your code.. i highly reccomend you recursively change the ownership back to the web user and set the permissions to 755. Use the same command above but replace 777 with 755.

---

### Post by louis vitton on 2012-01-05
Thank you for your reply i have tried what you suggested but it has not worked is it possible that the php file is trying to write the cache using illegal or not allowed characters and that is why it is erroring?

---

### Post by Lars Noodén on 2012-01-05
> **dazman19 said:**
> your web server should be running as a user called www-data 

so all the files in the web folder should be owned by www-data.

if your web directory was say... /var/www/
then you would generally make all the files owned by www-data,

sudo chown -R www-data:www-data /var/www/ 

you dont want them owned by root... 


That would enable visitors to write to your web directories.  The web server only needs read permission to function.

> **dazman19 said:**
> 
if you are editing them and they are changing to root as the owner, then you shouldnt really be doing php development as root.


Agreed, don't do regular work as root.  It is too easy for accidents to become big and/or permanent.

> **dazman19 said:**
> 

what you can do is make all the files have Read/Write/Execute but do not do this for a production environment.

sudo chmod -R 777 /var/www/


That also would enable visitors to write to your web directories.  It's very dangerous even temporarily. Please, for safety's sake, change it back.

```

sudo chown -R root:root /var/www

sudo find /var/www -type d -exec chmod u=rwx,g=rx,o=rx

sudo find /var/www -type f -exec chmod u=rw,g=r,o=r 

```

> **dazman19 said:**
> 

use it on 777 to do your development.. when you are happy with your code.. i highly reccomend you recursively change the ownership back to the web user and set the permissions to 755. Use the same command above but replace 777 with 755.

We can find a safer way.

---

### Post by Lars Noodén on 2012-01-05
Here is a way, if your script is running as www-data and not running as another user:

```

chown -R root:www-data /var/www/api 

sudo find /var/www/api -type d -exec chmod u=rwx,g=rxs,o=rx \;

sudo find /var/www/api -type f -exec chmod u=rw,g=r,o=r \;

```

Take a look at [suExec](http://httpd.apache.org/docs/2.3/suexec.html) if you would like your script to run as a different user than www-data.

---

### Post by louis vitton on 2012-01-05
> **Lars Noodén said:**
> Here is a way, if your script is running as www-data and not running as another user:

```

chown -R root:www-data /var/www/api 

sudo find /var/www/api -type d -exec chmod u=rwx,g=rxs,o=rx

sudo find /var/www/api -type f -exec chmod u=rw,g=r,o=r

```Take a look at [suExec]("http://httpd.apache.org/docs/2.3/suexec.html") if you would like your script to run as a different user than www-data.

I tried your commands above the first one worked well thank you but the second and third failed due to this error on my server.
" find: missing argument to `-exec' "

Thank you all also for this ongoing assistance and your time, I have been searching the internet since i had this issue with out much luck on how to really resolve it.

---

### Post by Lars Noodén on 2012-01-05
I fixed the typos.  They should work now.  Thanks for catching that.

---

### Post by louis vitton on 2012-01-05
> **Lars Noodén said:**
> I fixed the typos.  They should work now.  Thanks for catching that.
No worry's thank you for the help but it still wont run. I am still receiving the same error as before.
if i go to /var/www/api could i run it on the directory itself without the find or -exec components?

---

### Post by Lars Noodén on 2012-01-05
That would work, too.

---

### Post by louis vitton on 2012-01-05
> **Lars Noodén said:**
> That would work, too.

Sorry its late here, what would be the commands to run in at /var/www/api.

---

### Post by volkswagner on 2012-01-05
Is it possible that some of the directories already exist and don't have the correct permission?

```
ls -alt /var/www/api/.pheal-cache
```

if that does exist move down the line

```
ls -alt /var/www/api/.pheal-cache/public/
```


if that does exist move down the line

```
ls -alt /var/www/api/.pheal-cache/public/public
```

... etc.

---

### Post by louis vitton on 2012-01-05
> **volkswagner said:**
> Is it possible that some of the directories already exist and don't have the correct permission?

```
ls -alt /var/www/api/.pheal-cache
```if that does exist move down the line

```
ls -alt /var/www/api/.pheal-cache/public/
```
if that does exist move down the line

```
ls -alt /var/www/api/.pheal-cache/public/public
```... etc.

I sorta thought this would have to happen. There are a large number of directorys i will have to make is there a way i can allow php to do this for me as required and automate the whole process as people access the website?

---

### Post by dazman19 on 2012-01-05
yes but you would not write it that way. Use recursion in php to operate on the file system directories, dont write code like if($dirname == "xyz") because if you add more directories later you will have to change your code

---

### Post by louis vitton on 2012-01-05
> **dazman19 said:**
> yes but you would not write it that way. Use recursion in php to operate on the file system directories, dont write code like if($dirname == "xyz") because if you add more directories later you will have to change your code
Thank you the php is a pre writen framework for the eve online api called pheal otherwise i would try and do that i am only learning php still at this stage so didnt want to make my own file cache system. 

If i create the diretorys manually then the php can just try and write the xml files to the correct locations. What should my;

Owner be? Root?
group? www-data? with write access to the folders/directory s.
and have all the folders with just read acess?

Sorry about this warping my head around it
Thanks for the help everyone also :)


PS. Could i give www-data rights to create folders by assigning it to a group such as root? This is prob a major security issues though?

---

