---
title: "Ubuntu 9.1 and phpbb3"
date: 2010-01-06
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-06
how do i install this? or rather how do i even start, i am new to ubuntu and have no idea where to start, phpbb only shows me stuff on windows installs

---

### Post by bluedrakonis on 2010-01-06
just a quick update i just figured out how to get it installed, but anything that shows what i may need to do to set it to run a website off of ubuntu9.1 and appache 2 is appreciated

---

### Post by firefly2442 on 2010-01-07
Well, since you got phpbb3 working I'm guessing you already installed a webserver (Apache2 I bet), PHP5, and MySQL.

If you haven't this guide should get you started:

[http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

I'm also guessing this is a personal computer of yours.

Once this is all setup you should be able to figure out your IP address and then have a friend try to go to the IP address and see if they can view your server.  If not, you probably have a router which you may need to fiddle with to get the routing/firewall working.

Maybe you can give some more details as to what you want to do with the server or what isn't quite working at the moment and we can help with more specific advice.

Hope you get it working.  Have fun. :)

---

### Post by bluedrakonis on 2010-01-07
sorry i had followed a guide and installed apache2, php5, mysql. i got phpbb3 to install as far as apt-get but when i try to run the install through a browser i cant get to it says not found, i have ispconfig 3 setup and working on it, i also have squirrel mail setup, the idea is to host a website or a few and to host some forums as well as run a mail server off of a personal pc

---

### Post by bluedrakonis on 2010-01-07
just a ran the php.test file and that is working, ill let you all know about the rest as i go through it

---

### Post by bluedrakonis on 2010-01-07
just another update, i can access phpmyadmin, is their something i supposed to setup with these before i can install phpbb3?

---

### Post by firefly2442 on 2010-01-07
So you installed phpbb3 through the apt-get repository and not by downloading it from their website and installing manually?

I would suggest installing it manually because I believe the version in the repository is a little old.

[http://ubuntuforums.org/showthread.php?t=40722](http://ubuntuforums.org/showthread.php?t=40722)

This link might help you.

---

### Post by bluedrakonis on 2010-01-07
ok im a complete newb at this OS, how do i download something from a website that isnt a tar , how would i download it and then install it, i have found nothing explaining this for us newbs

---

### Post by cariboo on 2010-01-07
Downloading files and extracting them works exactly the same way it does in Windows. Once you have the file downloaded and sitting in your download directory, open the file manager and double-click the file and the file archiver will walk you through extracting the file.

---

### Post by firefly2442 on 2010-01-07
The directory where you'll be putting the files for phpbb3 is:

/var/www/

You may need to change the permissions before copying the files there (or just copy them as root).

---

### Post by bluedrakonis on 2010-01-08
ok i downloaded it in /var/www/  and then unzipped the file but still no good

---

### Post by BkkBonanza on 2010-01-08
There are just so many possible things you may have done or not. We need more detail to be able to help...

For example, did you edit your httpd.conf to set the document root to /var/www ? Or is it elsewhere? 

If you plan on running more than one site I'd suggest putting the phpbb3 files into it's own directory rather than /var/www - eg. maybe /var/www/phpbb and then setting your doc root there for now.

Later you will want to add VirtualHost directives to your config, so you can host more than one site, but initially you may find that too much to handle and getting a first site going is easier if you just serve the one directory.

Next, when you go to your site what page do you get? And do you know where it is on your system? By setting your doc root correctly you should be able to get the phpbb install page showing.

---

### Post by bluedrakonis on 2010-01-08
ok how do i make the changes to the doc and create a folder for phpbb by itself. another site had me run 

 

ls -la /etc/apache2/conf.d/


the output is 

total 24
drwxr-xr-x 2 root root 4096 2010-01-06 19:45 .
drwxr-xr-x 7 root root 4096 2010-01-06 19:45 ..
-rw-r--r-- 1 root root   237 2009-11-12 17:52 apache2-doc
-rw-r--r-- 1 root root   269 2009-11-12 17:48 charset
lrwxrwxrwx 1 root root    45 2010-01-06 19:45 javascript-common.conf -> /etc/java script-common/javascript-common.conf
-rw-r--r-- 1 root root 2907 2009-11-12 17:48 localised-error-pages
lrwxrwxrwx 1 root root    28 2010-01-06 19:45 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root root 1481 2009-11-12 17:48 securit


if that helps any

---

### Post by BkkBonanza on 2010-01-08
If you used the Ubuntu LAMP package to install then there should be an apache2.conf in the directory you listed above. Since there isn't I can't really know what you've done so far. 

With the standard install the doc root is at /var/www - which means dropping phpbb3 into that directory should work. I thought since you had no success with that it meant your doc root was configured differently. But without a apache2.conf file I see that maybe you haven't even installed the needed software yet. Or perhaps you're following some other way of doing this. Either way, for me to help I need to know what you've done up til now. 

To run phpbb3 you need to have 3 components installed, Apache web server, PHP scripting language and MySql database. Usually under Ubuntu the simplest install is the LAMP package which includes all 3 at once. If you have installed something different let me know and I'll try to help from there.

I'd suggest this Ubuntu help page as well for getting your server going,

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by bluedrakonis on 2010-01-08
i can access the it works apache page, phpmyadmin, and the info.php page, i folowed this guide and set it up in this matter:

[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

---

### Post by BkkBonanza on 2010-01-08
Can you provide the output of,

ls -lsa /var/www

This will help understand the state of things now. I don't use ISPConfig but it should be fairly easy in ISPConfig to add a site for phpbb and point the site to a suitable directory like /var/www/phpbb - then you just need to get your phpbb files into that directory to work.

If you have multiple sets of files in the same directory then you are likely to have trouble. eg. the apache "it works" page in the same directory as phpbb may be stopping the phpbb default page from showing because the apache page has priority. This is just a guess on my part because I can't see what your directories contain.

Generally speaking each site should point to it's own directory underneath /var/www and the /var/www itself shouldn't be used for serving a site. It does by default and works fine with only one site but as soon as you have more it's better to organize them in subdirectories.

---

### Post by bluedrakonis on 2010-01-08
it gives me this:

total 2396
4 drwxr-xr-x 5 root root 4096 2010-01-08 05:54 .
4 drwxr-xr-x 16 root root 4096 210-01-06 21:21 ..
4 -rw-r--r-- 1 root root 177 210-01-06 19:44 index.html
4 -rw-r--r-- 1 root root 21 210-01-07 18:06 info.php
0 lrwxrwxrwx 1 root root 34 2010-01-06 21:22 ispconfig -> /usr/local/ispconfig/interface/web
4 drwxr-xr-x 13 root root 4096 2009-01-08 12:10 phpbb3
2364  -rw-r--r-- 1 root root 2416769 2009-11-17 16:51 phpbb-3.0.6.zip
4 drwxr-xr-x 3 root root 4096 2010-01-06 21:22 php-fcgi-scripts
4 -rw-r--r-- 1 root root 32 210-01-07 06:10 test.php
4 drwxr-xr-x 2 root root 4096 2010-01-06 50:46 webalizer
0 lrwxrwxrwx 1 root root 24 2010-01-06 21:14 webmail -> /usr/share/squirrelmail/


if you dont mind me asking what is all this info that it shows

---

### Post by BkkBonanza on 2010-01-08
These are the files in your /var/www directory. The index.html is the file giving you the "It works" page. I see that you have a phpbb3 directory which hopefully contains the files making up the phpbb site. There are several bits of info on each line representing a file or directory. The rwx- values indicate permissions, the number is a size value, date of creation and filename.

You do have a problem with permissions here. All these files are owned by root and have public read rights to allow Apache to use them. This is far from ideal and at some point you will want to fix this for security reasons. Ideally they should be owned by admin, in group apache (or www depending on your apache username) and have no public rights at all. This task is probably a bit complex right now so just leave it until you get other things sorted out.

At this time it appears you should be able to access your phpbb default page by going to "http://localhost/phpbb3". If not then check the files in /var/www/phpbb3. If nothing is there then you need to unzip the phpbb-3.06.zip file into that directory and then try to access it again.

You likely want that phpbb directory tied to it's own sitename and that can be done in ISPConfig. Then you can access phpbb with it's own name rather than as a subdirectory on the default (localhost) site.

---

### Post by bluedrakonis on 2010-01-08
thanks for the help guys, this system is touchy, i was going localhost/phpbb3, but when i tried localhost/phpBB3 it worked, but of course with all good news come some bad, it was unable to write the config file and now i must upload it from one computer to the server how would i do this?

---

### Post by BkkBonanza on 2010-01-09
Probably couldn't write the config because of your root ownership and permissions issue. I don't know why that tutorial wouldn't have you set these correctly. I didn't check the whole thing but they should definitely have a step setting correct ownership and permissions.

How you get that file to the server depends on how you are accessing your server. Are you logged in with ssh? Or some other way?

---

### Post by bluedrakonis on 2010-01-09
im using the program putty, using port 20, if you know a way to do it or have a prefered method please do tell, i am trying to learn as much as i can of this stuff

---

### Post by BkkBonanza on 2010-01-09
Putty in telnet mode or ssh mode? there is a big difference. hopefully ssh mode.
Since you're using Putty I expect you're doing it from a Windows system.

In that case I would recommend you use WinSCP, another Windows tool similar to Putty that has sftp capability as well as ssh. You can get it here,
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

You don't have to use that one but you do need some kind of secure file copying tool. There is other ways too but from Windows it's likely the easiest way to go. 

Once you have sftp or scp you can use it to copy the config file you have to the correct location on your server and set ownership and permissions on the file.

If I'm mistaken and you are on a Ubuntu desktop then you can use Nautilus (the default file manager) by simply entering into the address like so,

sftp://server_ip_or_name/var/www

Then you can browse to the correct location and drag/drop or paste the file there.

Since you do want to learn about how to do all this and from the questions you've asked I would recommend you take a break and read up on the Linux filesystem, ownership and permission topics. These are all core to being able to get what you want to work and without that udnerstanding you will be groping around in the dark.

I googled a bit and found these that may help. There's many more out there and some likely better even...

[http://www.hostingmanual.net/other/permissions.shtml](http://www.hostingmanual.net/other/permissions.shtml)
[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=225](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=225)

---

### Post by bluedrakonis on 2010-01-09
ill try that, but im on an ubuntu server, no gui

---

### Post by bluedrakonis on 2010-01-09
dud i just tried that proggy and i just have to say, **** this looks like it might everything alot easier, thanks, ill let you know how it goes after i play around with it awhile

---

### Post by bluedrakonis on 2010-01-09
that done the trick, now i just have to get everything configured to the way i like it
thanks guys

---

