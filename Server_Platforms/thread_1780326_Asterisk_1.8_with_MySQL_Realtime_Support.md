---
title: "Asterisk 1.8 with MySQL Realtime Support"
date: 2011-06-11
forum: Server Platforms
---

### Post by ryazkhan on 2011-06-11
First of all let me say that this is not the only way to accomplish this, and there is not assurance that it will work for you. It did worked for me so I thought to share with community

Lets make yourself root otherwise you have to use sudo with each command(s) and have to type password in most cases
> sudo su
Update the system and apply updates if there are any
> apt-get update
apt-get upgrade
Install all dependencies
> sudo apt-get install python-software-properties -y
Import public key
> sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 175E41DF
Add repository so we can download asterisk 1.8
> sudo add-apt-repository "deb [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) `lsb_release -cs` main"
sudo add-apt-repository "deb-src [http://packages.asterisk.org/deb](http://packages.asterisk.org/deb) `lsb_release -cs` main"
Update repository and install any update if needed
> apt-get update
apt-get upgrade
Install Asterisk 1.8
> sudo apt-get install asterisk-1.8 -y
Install DAHDI
> sudo apt-get install asterisk-dahdi -y
That is it, we have sucessfully installed Asterisk 1.8
Next part is to install LAMP package
> apt-get install mysql-server mysql-client apache2 php5 libapache2-mode-php5 phpmyadmin php5-mysql -y
Once done, restart all services or restart system
> service asterisk restart
service mysql restart
service apache2 restart
Enjoy your new system and have fun with it
I have scripted the whole process, feel free to download it
> wget [http://cns.selfip.net/articles/conf/asterisk.sh](http://cns.selfip.net/articles/conf/asterisk.sh)
In next part we are going to set asterisk up for MySQL realtime
In this example, I am going to create two accounts and going to set them up so they can make/receive calls from each other. Both accounts will have voice mailboxes as well. I am using internal as my default context, feel free to change any setting
So lets start
Edit sip.conf file
> nano /etc/asterisk/sip.conf
Add the following lines in it, the file is pretty long and has broad settings but everything is commented out of the box. Following line will set up basic operation to start and then later on you can go through the file and set the option(s) you need. You can add these lines right after [general] tag
> context=internal
rtcachefriends=yes
disallow=all
allow=ulaw
allow=ilbc
Save the file and exit
Now we need to edit extensions.conf file so all use in internal context can make/receive calls
> nano /etc/asterisk/extensions.conf
Add the following line right after [general] tag, again the file have broad settings but this will setup the basic context[internal]
> [internal]
switch => Realtime/@
You can also add MySQL table name where all extensions are located i.e. switch => Realtime/@extensions
Save the file and exit out of it
Next we need to tell asterisk to look for MySQL database for users information
Edit extconfig.conf file
> nano /etc/asterisk/extconfig.conf
Add the following lines in it, I would just add them at the end of the file
> sipusers => mysql,asterisk,users ; SIP user
sippeers => mysql,asterisk,users ; SIP peers
extensions => mysql,asterisk,extensions ; SIP extensions
voicemail => mysql,asterisk,voicemails ; SIP voicemailboxes
queues => mysql,asterisk,queues ; SIP queue
queue_members => mysql,asterisk,queue_members ; SIP queue members
Now we need to tell asterisk to connect to MySQL to get all informations
So edit res_config_mysql.conf file
> nano /etc/asterisk/res_config_mysql.conf
Our database for this example is asterisk so add/append the following in that file 
> [asterisk]
dbhost = localhost
dbname = asterisk
dbuser = mysqluser
dbpass = mysqlpass
dbport = 3306
dbsock = /var/run/mysqld/mysqld.sock
requirements=warn ; or createclose or createchar
Adjust dbuser and dbpass to your settings, this is mysql user privilage account. You can always use root for testing if you are not sure about the account
Okay at this point our asterisk box is ready and all configured !
Lastly we need to create database in mysql
So connect to mysql and create database, first import the asterisk.sql script to create database and its related tables
> wget [http://cns.selfip.net/articles/conf/asterisk.sql](http://cns.selfip.net/articles/conf/asterisk.sql)
Now connect to mysql and create the database and its table using asterisk.sql script, replace mypassword with your root's password
> mysql -u root -pmypassword
source asterisk.sql;
All done!

Configure hard/soft sip phones and have fun !
As always feel free to [[COLOR="Blue"]email[/COLOR]]("mailto:ryazkhan@gmail.com") me if you have any question(s). Sorry for any typo

You can also access this article via my [[COLOR="Blue"]website[/COLOR]]("http://cns.selfip.net/articles/astrk.php") and via my [[COLOR="Blue"]blog[/COLOR]]("http://ryazkhan.blogspot.com/2011/06/asterisk-18-with-mysql-realtime-support.html")

---

### Post by aik2ka4 on 2011-07-04
:KS

thank you for such a quick and easy setup. :D

only one thing should be changed in case of problem when trying to connect to mysql, use the below command and then enter you password

mysql --user=root --pass mysql 

-> Enter you password here when asked

I have few questions

- we have installed phpmyadmin, why is that and how to access it. :p
- Do we have Asterisk GUI, or how can we add with this installation ? :o 

:o :o :o

---

### Post by aik2ka4 on 2011-07-04
and

can you help fixing this problem ?

res_config_mysql.c: **Table queue_members** not found in database.  This table should exist if you're using realtime.

Thanks

---

### Post by ryazkhan on 2011-07-06
Hi aik2ka4,

Sorry for being late, to connect to  mysql you can use> mysql -u root -p Above will prompt you for password, you can also type the password right in command
> mysql -u root -pyourpasswordNotice there is no space between -p and yourpassword

phpmyadmin is nice gui to access mysql database. You can access it via [http://yourip/phpmyadmin](http://yourip/phpmyadmin) and user is root and password would be your password

This installation does not comes with Asterisk GUI, I have not really played with it, like command line, my experience with GUI's are not so great :). So would not be able to help here regarding that, sorry 
*res_config_mysql.c: Table queue_members not found in database. This table should exist if you're using realtime* simply mean you are missing one table so create it and you will be all set. Creating table is much easy via phpmyadmin. If you have used my sql script to create database then the table would be there, login to phpmyadmin and double check it :)

Hope it will help, let me know if you have any question(s). Feel free to email me

---

### Post by rubylaser on 2011-07-06
First of all, thank you for taking the time to write this up :) The following are some personal feelings I have from running Asterisk at home / work for a few years now.

[FreePBX]("http://www.freepbx.org/") makes managed Asterisk much easier for the average person. I used to install my own Asterisk/Freepbx on top of Debian, now I skip all the setup, and download [PBX in a Flash]("http://pbxinaflash.net/"), and be ready to go in a couple of minutes.

---

### Post by ryazkhan on 2011-07-06
rubylaser,

Thank you for your kind words, appreciated 

I values you feeling and agree with you, I did start to use that but my setup get complicated and those functions were not in PBX like using encrypted passwords, make complicated and hard to guess user names, assigning them extensions in such way that would be very hard to guess, and try not to store clear passwords in files etc..

There are all kind of people out there, I don't like that somebody will break into my phone line and start to abuse it :) so I try all weird but secure settings to make sure that it will take years to guess things out or crack things out, as you may know that VoIP has lot of fears around it :(

So I quite it and started to use command line and then MySQL, however I am in process of writing an Asterisk admin (GUI) keeping above mentioned things in mind ;)

---

### Post by xdonie11 on 2012-02-02
i always have this problem every time i login my sip


WARNING[6435]: config.c:2256 find_engine: Realtime mapping for 'sippeers' found to engine 'mysql', but the engine is not available

i followed the tutorials..pls help me i really need this to work..

thanks!!!

---

### Post by tcrichton on 2012-04-08
Hi ryazkhan,

Thanks for your great post for getting asterisk 1.8 direct from the digium repos.

There is one typo in the LAMP apt-get cmd

apt-get install mysql-server mysql-client apache2 php5 libapache2-**mode**-php5 phpmyadmin php5-mysql -y

Replace with 

apt-get install mysql-server mysql-client apache2 php5 libapache2-**mod**-php5 phpmyadmin php5-mysql -y

Thanks again,

Tristan.

---

### Post by janiali on 2012-04-09
> **ryazkhan said:**
> First of all let me say that this is not the only way to accomplish this, and there is not assurance that it will work for you. It did worked for me so I thought to share with community
 
Lets make yourself root otherwise you have to use sudo with each command(s) and have to type password in most cases
 
Update the system and apply updates if there are any
 
Install all dependencies
 
Import public key
 
Add repository so we can download asterisk 1.8
 
Update repository and install any update if needed
 
Install Asterisk 1.8
 
Install DAHDI
 
That is it, we have sucessfully installed Asterisk 1.8
Next part is to install LAMP package
 
Once done, restart all services or restart system
 
Enjoy your new system and have fun with it
I have scripted the whole process, feel free to download it
 
In next part we are going to set asterisk up for MySQL realtime
In this example, I am going to create two accounts and going to set them up so they can make/receive calls from each other. Both accounts will have voice mailboxes as well. I am using internal as my default context, feel free to change any setting
So lets start
Edit sip.conf file
 
Add the following lines in it, the file is pretty long and has broad settings but everything is commented out of the box. Following line will set up basic operation to start and then later on you can go through the file and set the option(s) you need. You can add these lines right after [general] tag
 
Save the file and exit
Now we need to edit extensions.conf file so all use in internal context can make/receive calls
 
Add the following line right after [general] tag, again the file have broad settings but this will setup the basic context[internal]
 
You can also add MySQL table name where all extensions are located i.e. switch => Realtime/@extensions
Save the file and exit out of it
Next we need to tell asterisk to look for MySQL database for users information
Edit extconfig.conf file
 
Add the following lines in it, I would just add them at the end of the file
 
Now we need to tell asterisk to connect to MySQL to get all informations
So edit res_config_mysql.conf file
 
Our database for this example is asterisk so add/append the following in that file 
 
Adjust dbuser and dbpass to your settings, this is mysql user privilage account. You can always use root for testing if you are not sure about the account
Okay at this point our asterisk box is ready and all configured !
Lastly we need to create database in mysql
So connect to mysql and create database, first import the asterisk.sql script to create database and its related tables
 
Now connect to mysql and create the database and its table using asterisk.sql script, replace mypassword with your root's password
 
All done!
 
Configure hard/soft sip phones and have fun !
As always feel free to [EMAIL="ryazkhan@gmail.com"][COLOR=blue]email[/COLOR][/EMAIL] me if you have any question(s). Sorry for any typo
 
You can also access this article via my [[COLOR=blue]website[/COLOR]]("http://cns.selfip.net/articles/astrk.php") and via my [[COLOR=blue]blog[/COLOR]]("http://ryazkhan.blogspot.com/2011/06/asterisk-18-with-mysql-realtime-support.html")
 
 
great guide for asterisk . thanks , 
 
is it possible to installed Asterisk 1.6 with the same tutorial ?

---

### Post by ryazkhan on 2012-05-09
> **janiali said:**
> great guide for asterisk . thanks , 
 
is it possible to installed Asterisk 1.6 with the same tutorial ?

Probably not, best way for 1.6 with MySQL real time would be to install it from source and then install addons from source code as well. Take a look [[COLOR="Blue"]this[/COLOR]]("http://www.touchkanology.com/asterisk-1-6-2-9-quick-install-guide.html") and [[COLOR="Blue"]this[/COLOR]]("http://www.touchkanology.com/asterisk-realtime-1-4-x-with-mysql.html") to compile and install asterisk and addons from source and configure asterisk for MySQL realtime

---

