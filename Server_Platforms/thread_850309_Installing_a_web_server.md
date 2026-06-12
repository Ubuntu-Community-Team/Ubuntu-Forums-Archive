---
title: "Installing a web server"
date: 2008-07-05
forum: Server Platforms
---

### Post by prap19 on 2008-07-05
Hi
        I have downloaded **Apache2.2.9 tar file**.The instalation guide asks me to copy the tar file in **/usr/local/directory**.but i am not able to do it because it says I don't have any rights since i am not in root.Also  I tried to do in my own directory.This is what i did:
I unzipped the tar file of Apache(its name being httpd-2.2.9.tar.bz2) in my own directory.Then using terminal i connected directory by 'cd' then did ./configure.
After that it does lots of checking and then i did '**make**' and after lots of procedure i did 'make install'.These were the instructions given in the LINUX FOR YOU magazine in one of the articles regarding setting up web servers.But then how do i know my server has started,
Then anyone could anyone guide me with **PHP5.2.6** installation in short word. I also want to install MySQL.I wanted one more advice which databse platform is better **MySQL or SQlLite**.I dont know the difference.Thank you for the efforts for reading these.Please help i hav tried almost all the sources and i am a newbie in linux and have installed **UBUNTU_8.04**

---

### Post by scragar on 2008-07-05
why not just install apache etc from the repo's? go to Application>accessories>terminal
and enter:
```
sudo apt-get install apache2 mysql-server php5-mysql
```
you can then copy anything you want to be accessable to the /var/www directory, it will ask for the mysql root password as well, install mysql-admin if you want to manage mysql easier.

---

### Post by prap19 on 2008-07-05
I did all this things that u have mentioned(but not the MySQLadmin).After that how to make a PHP file in www directory.It is not showing me any option to create since it is in root directory.How to get the rights of root?

---

### Post by scragar on 2008-07-05
I'm guessing this is a localhost where nothing needing high security is going right(because if not these tips are way too insecure, you should use sudo instead:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) ):
Chown the www folder
```
sudo chown -R **USERNAME** /var/www
```

of you can make /var/www a public folder:
```
sudo chmod 777 /var/www
```



make a note of there 3 commands somewhere as well, they start/stop/restart apache:```
sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 restart
```, rather essential basics I think.

---

### Post by jesushero on 2008-07-05
> **scragar said:**
> why not just install apache etc from the repo's? go to Application>accessories>terminal
and enter:
```
sudo apt-get install apache2 mysql-server php5-mysql
```
you can then copy anything you want to be accessable to the /var/www directory, it will ask for the mysql root password as well, install mysql-admin if you want to manage mysql easier.

I agree to that! Don't do it with a tar file unless there's a specific reason for doing so! The repositories are there to make your life easier! However, if you're running the Desktop version, I'd say go through Synaptic Package Manager (system > administration) to avoid the terminal if you're not that familliar with it.. Search for apache2, and download it.. If running the server version of ubuntu with no gui, run:

```
sudo apt-get install apache2 mysql-server php5-mysql
```

It will ask for your password to "perform administrative tasks".. 

When installed, type in a terminal:

```
sudo nano /etc/apache2/apache.conf
``` 

and edit the configuration file. ctrl-X to exit and y to save, followed by enter to accept the default filename. It is pretty easy to figure out.

Then go to /var/www/ 

This is your [http://127.0.0.1/](http://127.0.0.1/) 

(where 127.0.0.1 is to be replaced with your public broadcast IP for global internet access)

If you want to add a folder such as [http://127.0.0.1/folder/](http://127.0.0.1/folder/) 
just add /var/www/folder/ 

There is a default index.html file in /var/www/ if you install apache2 from the repositories. Just edit this, this is your start page!

---

### Post by cariboo on 2008-07-05
Do not change the user in /var/www it should only be root or www-data. To copy files to /var/www use either:

```
gksu nautilus
```

or in a terminal:

```
sudo cp <file> /var/www
```

Jim

---

### Post by prap19 on 2008-07-05
Thanks for the advice.
But still i am not able to start apache.Because when i restart my apache with command i get the following error.

 [COLOR="Black"][B]* Restarting web server apache2                                                Syntax error on line 1 of /etc/apache2/conf.d/fqdn.save.1:
Invalid command 'exit', perhaps misspelled or defined by a module not included in the server configuration[/B][/COLOR]
                                                                         [COLOR="Red"][fail][/COLOR]



I feel this is because before posting my query in this forum i had edited thi file but i wasnt able to exit.So i typed exit in it but no help then i closed the terminal window to exit.Probably this could have been saved automatically.So what can i do now?

---

### Post by cariboo on 2008-07-05
Open up the file with a command line editor like nano and edit the file. Nano is the default editor installed eg:

```
sudo nano /etc/apache2/conf.d/fqdn.save.1
```

or just delete the file and start all over again.

Jim

---

### Post by prap19 on 2008-07-06
Ya it has worked.I am extremely Thank you to all of you!!

Thanks to cariboo907,jesushero,scragar:guitar:

---

### Post by prap19 on 2008-07-07
Hey can anyone tell how to make MySql start.Also i downloaded phpMyadmin from synaptic.But it is not giving me option for create database a cross appears near it and says [COLOR="Red"]NO PRIVILEGES[/COLOR].What mistake i may i have done??
Plz tell me.

---

### Post by zakirs on 2008-07-07
well did u login ast root for mysql???

---

### Post by scragar on 2008-07-07
```
sudo apt-get install php5-mysql mysql-server
```

that should be enough to get mysql working, you may need to edit the config file
[http://www.aota.net/PHP_and_MySQL/phpmyadmin.php4](http://www.aota.net/PHP_and_MySQL/phpmyadmin.php4)

---

### Post by prap19 on 2008-07-07
Its is working now.Thank you very much 

:guitar:

---

