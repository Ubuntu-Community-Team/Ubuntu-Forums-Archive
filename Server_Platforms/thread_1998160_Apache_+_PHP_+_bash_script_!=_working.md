---
title: "Apache + PHP + bash script != working"
date: 2012-06-06
forum: Server Platforms
---

### Post by nw68868 on 2012-06-06
I have a webcam running on my web server of a goldfish in a tank. I want to have a link on the webpage interact with an Arduino. One thing will be to open a hacked toy backhoe bucket in order to put food into the tank.

I am running a headless Lubuntu based 12.04 server so i thought the easiest way to do this is with a shell script so i wrote:
```

#! /bin/bash
echo -n "1" > /dev/ttyACM0
```

For debugging right now all that does is turn on an LED and that is fine. I have a 100uf capacitor in between reset and ground of the Arduino to keep the connection alive (overkill but it works). When i run the shell script life is good and it words great.

So i wrote a simple PHP script that runs this shell script:
```

  <h3>Feeding the Fish</h3>

<?
exec('sh feed.sh');
?>
```

When i run that from the command line it works great. So i put a link on the website to run it for me:
```

<li><a href="feed.php">Feed the Fish</a></li>
```

when i click the link nothing happens  

So i went back to the command line and checked and chmoded all the permission, and then ran
```

# sudo -u www-data php feed.php
```
to make sure apache could perform the task. It could not so i added www-data to the dialout goup using this:
```

# usermod -a -G dialout www-data
```
and now it it works fine.

Now i switch over to my browser and click the link and it works! So i reload the page and it works again! Then about a minute later i try and do a page reload and nothing happens. Igo back to the webpage and re-click the link. Nothing. 

That makes me think that it has something with me running
```

# sudo -u www-data php feed.php
```


which opens the connection and then it times out and apache cant re-open the connection.

any ideas?

---

### Post by lisati on 2012-06-06
*Thread moved to **Server Platforms**.*

When you're at the "root" prompt (indicated by the "#") you don't need to use "sudo".

You might want to use **chmod a+x** on the script file.

---

### Post by nw68868 on 2012-06-06
good point about the sudo, i cut and paste and most of the time i dont bother moving the curser to delete the unneeded sudo, it runs fine with it.

both the php and the shell script are chmoded to 777 for the debug

---

### Post by nw68868 on 2012-06-06
SOLVED!

Apache did not have suPHP pwers I installed using the follow process copied from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


> Installing suPHP
suPHP is a tool for executing PHP scripts with the permissions of their owners. It consists of an Apache module (mod_suphp) and a setuid root binary (suphp) that is called by the Apache module to change the uid of the process executing the PHP interpreter.

Note: suPHP enforces, security and helps avoid file permission problems under development environments with several users editing the site files, but it also demands more memory and CPU usage, which can degrade your server performance under certain circumstances. 

To only install suPHP. use any method to install the package
```
# aptitude install libapache2-mod-suphp
```

Enable this module by doing
```
# sudo a2enmod suphp
```

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to edit this file
```
sudo nano /etc/apache2/mods-available/php5.conf
```

or
```
gksu "gedit /etc/apache2/mods-available/php5.conf"
```

make a new empty line at the top of the content, then add

```
<Directory /usr/share>
# make a new empty line at the bottom of the content, then add
</Directory>
```

save changes

For security reasons we need to specify to suPHP what are the document paths allowed to execute scripts, use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to edit this file
```
# sudo nano /etc/suphp/suphp.conf
```

or
```
gksu "gedit /etc/suphp/suphp.conf
```

find the value "docroot" and specify the document path of your site files, for example:

docroot=/var/www/
that value restrict script execution only to files inside "/var/www/"


docroot=/var/www/:${HOME}/public_html
that value restrict script execution only to files inside a custom home folder for each configured user inside "/var/www/:${HOME}/public_html"

for this tutorial we are going to use this value


docroot=/home/user/public_html/
which is the same Apache directory directive set before in this document

save changes

to restart Apache, type in your terminal
```
# sudo /etc/init.d/apache2 restart
```


---

