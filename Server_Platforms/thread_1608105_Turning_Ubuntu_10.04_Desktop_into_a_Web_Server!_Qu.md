---
title: "Turning Ubuntu 10.04 Desktop into a Web Server! Questions!!!!!!!!"
date: 2010-10-28
forum: Server Platforms
---

### Post by bloodhacker2 on 2010-10-28
Hey guys I have a few questions about turning a Ubuntu 10.04 desktop into a server.
Ok, so let me start off with my goal. I am using this machine for hosting only 1 website using joomla, php, mysql, and apache. I want a desktop version because I don’t like the black and white terminal. 

At this point I have successfully installed all Ubuntu 10.04 desktop and all updates.

When searching around for this solution, I found that I could run the command “sudo apt-get install ubuntu-server” and get all the features the server edition has. When running this command it comes back telling me that it cannot be found.
I also found that both the server and desktop edition are the same but the desktop edition comes with all the extras that I will need to delete.
I also found out that I will need to use lamp on the server to get php and all the other server stuff, but I also found that some people recommended that I install the server apps using the synaptic search.
My question is, what route should I take to turn this ubuntu 10.04 desktop into a dedicated web server. (Not Test Server).  Remember, I would like to stay with the desktop and not black and white terminal.

Thanks for all the help guys..

---

### Post by mainerror on 2010-10-28
> **bloodhacker2 said:**
> Hey guys I have a few questions about turning a Ubuntu 10.04 desktop into a server.
Ok, so let me start off with my goal. I am using this machine for hosting only 1 website using joomla, php, mysql, and apache. I want a desktop version because I don’t like the black and white terminal. 

At this point I have successfully installed all Ubuntu 10.04 desktop and all updates.

When searching around for this solution, I found that I could run the command “sudo apt-get install ubuntu-server” and get all the features the server edition has. When running this command it comes back telling me that it cannot be found.
I also found that both the server and desktop edition are the same but the desktop edition comes with all the extras that I will need to delete.
I also found out that I will need to use lamp on the server to get php and all the other server stuff, but I also found that some people recommended that I install the server apps using the synaptic search.
My question is, what route should I take to turn this ubuntu 10.04 desktop into a dedicated web server. (Not Test Server).  Remember, I would like to stay with the desktop and not black and white terminal.

Thanks for all the help guys..

If you prefer a GUI for you server and already have the desktop version installed then you can simply use Synaptics to install the packages you need.

You'll need all the sutuff you've listed and you'll also need bind if you are going to host the name service for you domain too.

Install apache2, mysql, bind and you should be good to go.

---

### Post by bloodhacker2 on 2010-10-28
Question, do you recommend that i use LAMP on the server or just DL the apache and mysql?

---

### Post by david.garceau on 2010-10-28
I like LAMP myself, it just makes things pretty easier to configure, there are numerous tutorials out there on how to set it up also. Good luck.


[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

---

### Post by SeijiSensei on 2010-10-28
> **bloodhacker2 said:**
> Question, do you recommend that i use LAMP on the server or just DL the apache and mysql?

You need that "P," too.  Apache doesn't know how to talk to databases; you need to write scripts for that purpose.  The most common scripting language is _P_HP which has a full array of functions to interact with MySQL (and other) databases.

---

### Post by hawk2010 on 2010-10-28
Here is what you should do
 
sudo apt-get install apache2 php5 mysql-server php5-mysql

That should get your web server installed with php and MySQL support

---

### Post by bloodhacker2 on 2010-10-29
> **david.garceau said:**
> I like LAMP myself, it just makes things pretty easier to configure, there are numerous tutorials out there on how to set it up also. Good luck.


[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

I like the tut, but what about using LAMP as a live server and not test?

---

### Post by bloodhacker2 on 2010-10-29
ok i got lamp successfully installed. Do you guys think i should install webmin?

---

### Post by eric_1982 on 2010-10-29
I am not sure if the webmin package is maintained in the repositories any more. You can manually install it if you would like. 

[http://www.unixmen.com/linux-distributions/4-ubuntu/1213-install-webmin-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1213-install-webmin-in-ubuntu-1010-maverick-meerkat)

If you do set it up I would recommend locking it down so it can only be accessed on your internal network IP range. I often see bots come around and scan for that port (1000) as well as the phpmyadmin directory. 

You may want to look at what functionality it will offer and if it is would be useful. By installing it you are opening another opportunity for some one to find there way in. 

I personally don't find webmin that useful, but maybe that is just me. I think most people feel more comfortable with it, when the only other choice is the command-line.

---

### Post by bloodhacker2 on 2010-10-29
ok so i got everything set up and now im on the joomla part. lol all i need to do is move the folder to /var/www/

But, its telling me i dont have permission to do that, could you give me a little info on how to move that folder over?

---

### Post by david.garceau on 2010-10-29
extract it to a folder on your desktop

sudo nautilus

copy the folder on your desktop

paste it into /var/www/


> **bloodhacker2 said:**
> ok so i got everything set up and now im on the joomla part. lol all i need to do is move the folder to /var/www/

But, its telling me i dont have permission to do that, could you give me a little info on how to move that folder over?

---

### Post by jbruced on 2010-10-29
I did the same thing. I put links to all the folders(in my home folder) I wanted to serve in the www directory using sudo cp.

The links are in the right place to be seen and served by the apache server, and the permissions in your home folder allow you to change your web files without worrying about permission issues.

Works good for me, hope it helps.

---

