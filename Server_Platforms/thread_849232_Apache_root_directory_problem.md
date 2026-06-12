---
title: "Apache root directory?? problem"
date: 2008-07-04
forum: Server Platforms
---

### Post by caseyann on 2008-07-04
Hello,
Just a little background...I'm taking a PHP/MySQL scripting class at my university. Our textbook gave me very good instructions for compiling and installing the packages. Which were basically the same instructions found at [http://httpd.apache.org/docs/2.2/]("http://httpd.apache.org/docs/2.2/") 

I've installed MySQL 5.0, Apache 2.2, and PHP5 and everything works perfectly except for where files are located in Apache. As per the instructions during the ./configure stage we did --prefix=/usr/local/apache while configuring apache so my files are all located under that directory tree. When I tested apache with the traditional test.php file I had to place the file in /usr/local/apache/htdocs for it to be found. So like I said working perfectly.

My instructor told us to add the following directories to /htdocs/students/boesen/scripting/ then there are several directories for each chapter we are going to be studying.

So here's my problem...if the .php file is in /htdocs it displays just fine in my browser. If I put the .php file in the boesen directory and go to [http://localhost/students/boesen/filename.php](http://localhost/students/boesen/filename.php) it works just fine. I want to know how I can leave the .php files in /htdocs/students/boesen/scripting/chapter_we_are_working_on instead of having to move them to /htdocs/students/boesen

Sorry for the long post...thought the background might be helpful in this situtation :)

I would really appreciate any help!!

---

### Post by mbeach on 2008-07-04
from what I'm reading files in 
/htdocs/students/boesen
are served up as php files, so I belive there should be no reason (other than perhaps a permissions issue) that files in 
/htdocs/students/boesen/scripting/chapter3
don't get passed off to php.  What happens when you try?

---

### Post by caseyann on 2008-07-04
Just like you thought! I get a permissions error saying I don't have the permissions to access on this server. 

Do you know how to fix it?

Thanks for the help!

---

### Post by mbeach on 2008-07-04
It depends on which user owns the files, I'll assume "boesen" owns the files, and they are in the "boesen" group.  You can determine this with an "ls -la" at the command prompt when in that directory.  

Apache is likely running as www-data.  You are probably wanting to edit these files as boesen, and this is not likely a machine being used for production use, so it might be enough to simply do the following in a terminal on one file, then on the whole bunch if it actually works:

cd /htdocs/students/boesen/scripting
sudo chmod o+r somephpfile.php

then browse to that file and see if 'works'

if it does, then you may want to 
sudo chmod -R o+r * in that some folder which will do all the files from there downward in the directory try [WARNING - use caution with this one].

Get it working on one file first, then chmod the others.  I'm not able to test if o+r is all you need, perhaps the directory needs execute permissions or something as well - maybe someone else can advise on that.  I'll try to take a look tonight sometime.

mb.

---

### Post by caseyann on 2008-07-05
MB,
Yes you're right this is only for developement. I'm taking a class to learn PHP/MySQL.

OK here goes, this is what I have:
drwxr-xr-x 15 root root  4096 2008-06-27 12:27 apache

after installing apache I changed the ownership of htdocs so I could access it. I may have done this wrong though. Just divorced windoze June 1st :)

I used chown -R caseyann htdocs (boesen is for school, caseyann is regular user)
and this is what I have:
drwxr-xr-x  3 caseyann root  4096 2008-07-04 06:17 htdocs

everything under htdocs is owned by caseyann root

drwxr-xr-x 3 caseyann root 4096 2008-07-04 08:15 students
drwxr-xr-x 3 caseyann root 4096 2008-07-05 08:05 boesen
drwxr-xr-x 2 caseyann root 4096 2008-07-04 06:18 ch02
drwxr-xr-x 2 caseyann root 4096 2008-07-05 05:11 ch03
drwxr-xr-x 2 caseyann root 4096 2008-07-04 15:12 ch04
drwxr-xr-x 2 caseyann root 4096 2008-07-05 08:04 ch05

All files inside the chapters are also the same caseyann root

Should I change it back then try your suggestion?

Thanks again MB!

Caseyann

---

### Post by mbeach on 2008-07-06
Well, normally, what I'd suggest is utilizing virtual hosts because to me it seems to be the way which you'll end up going at some point, but it tends to cause a little confusion when starting off.  What it easily allows though is for you to have a folder in your home directory for a particular project you are working on (like a php/mysql lesson), which contains files owned by you (so they are easily edited), with a corresponding conf file in /etc/apache2/sites-available

I'm going to assume that apache is running as www-data.  Again, I'd suggest doing this on maybe one of the folders, then if it works, do it on all of them.

put yourself in the ch02 folder
cd to whereever htdocs is
cd htdocs/boesen/scripting/ch02
sudo chown caseyann:www-data *
sudo chmod o+r *

That will change the owner to caseyann and the group to www-data, and the chmod will make all of the files there readable by others.  Try to load the file from the browser then and see what happens.  

If that doesn't work then there must be something going on in one of your apache conf files to prevent the php files from being handed of to php.

In your example above, does browsing to the following work?:
[http://localhost/ch02](http://localhost/ch02)

---

