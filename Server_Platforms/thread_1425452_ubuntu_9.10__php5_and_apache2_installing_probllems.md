---
title: "ubuntu 9.10  php5 and apache2 installing probllems"
date: 2010-03-09
forum: Server Platforms
---

### Post by hockey97 on 2010-03-09
Hi, I have webmin and installed apache2 and php5 and LAMP etc fine. I just did a clean install of ubuntu 9.10 after the computer crashed and had ubuntu 9.04.  

I backed up my server files like website files and mysql database and apache configs and website configs. 

I then tried to replace the files installed with the backed up ones. mysql went out. Then apache2 gave me a error saying that the config files isn't installed properly. 

I googled around and someone told me  to put in terminal to  use a terminal comppand to purge apache2 and many files associated to apache 2 and php5 to get rid of all of it even the devepndancies. 

Well when I ran it ubuntu desided to delete more then what I ask. It deleted ubuntu-desktop and much more. I installed ubuntu-desktop back and other files that I can remeber got deleted by accident. 

now when I try to install apache 2 or php5 I get this error in synptic package manager.

here is the error: ```
E: apache2.2-common: subprocess installed post-installation script returned error exit status 1
E: apache2-mpm-prefork: dependency problems - leaving unconfigured
E: libapache2-mod-php5: dependency problems - leaving unconfigured
E: php5-mysql: dependency problems - leaving unconfigured
E: php5-gd: dependency problems - leaving unconfigured
E: php5-ffmpeg: dependency problems - leaving unconfigured
E: php5-geoip: dependency problems - leaving unconfigured

```

I would like to know what I can do to fix this?

is there a way in terminal  that I can type a command to fix the problem. 

Or should I just install the dependancies and how do I know what ones apache2 and php5 depends on?

thanks for the help in advance.

---

### Post by hockey97 on 2010-03-09
ok, I just fixed the problem.  


If anyone gets this problem here is how you fix it. Or atleast how I did it.


first run in terminal this: ```
sudo apt-get --purge remove apache2.2-common
```


This will delete all apache2 stuff. Read what the terminal spits out while deleting. I notice that I had my backup files in  /etc/apache2 in the folders were it's like sites-enabled. The terminal dosen't delete those files. So I chmodded them to 777 and just deleted the folders inside apache2 folder at that /etc/apache2 location. 


once you get that. THen you run this code in terminal:```
sudo apt-get install apache2 apache2-mpm-prefork apache2.2-common libapache2-mod-php5 php5
```

it will install everything and hopefully you won't get any errors.

What was happening with me was that when I go to uninstall the files it wasn't uninstalling all of apache2 and the dependencies. So when I went to reinstall it would create some weird conflicts to existing config filess.

Now it works....yayhhh...lol :) 

Thanks for your time reading this.

---

