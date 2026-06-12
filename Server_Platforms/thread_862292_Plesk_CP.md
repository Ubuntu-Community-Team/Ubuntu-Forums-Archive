---
title: "Plesk CP"
date: 2008-07-17
forum: Server Platforms
---

### Post by kubapl on 2008-07-17
Hi. I can't seem to find a version of Plesk for ubunto server version 8.04 is there one thats out or will an older version do?

---

### Post by amenszer on 2008-07-17
Not sure if this is what you're looking for, but this guide may help:
[http://wiki.koshatul.com/Ubuntu_Plesk_Install]("http://wiki.koshatul.com/Ubuntu_Plesk_Install")

---

### Post by kubapl on 2008-07-17
would this work for 8.04?

---

### Post by amenszer on 2008-07-17
Not sure. Looks like the guide author did it with Dapper Drake. You can always try it with 8.04.

---

### Post by kubapl on 2008-07-17
yeah so I'm having a problem doing this step:
> Start the psa_installer
not sure what the command is suppose to be to start it up.

---

### Post by kubapl on 2008-07-17
Can I even run plesk on this server can someone check if my specs are good?
[http://kubapl.ath.cx/information.php](http://kubapl.ath.cx/information.php)

---

### Post by windependence on 2008-07-17
Having done many plesk installs I can tell you it is very picky about your platform. You MUST use a supported distribution or you will have problems later. Hardware is less important. Make sure you thoroughly read the Plesk install documentation. It is very good and the install is very easy to do, IF you read every question and answer it. 

If you need help, let me know.

-Tim

---

### Post by kubapl on 2008-07-17
Were can I find actual documentation?

---

### Post by windependence on 2008-07-17
Jeez, looks like they were bought by Parallels.

Main page:
[http://www.parallels.com/en/products/plesk/](http://www.parallels.com/en/products/plesk/)

Docs:

[http://www.parallels.com/en/products/plesk/docs/](http://www.parallels.com/en/products/plesk/docs/)

Installation guide:

[http://download1.swsoft.com/Plesk/Plesk8.4/Doc/en-US/plesk-8.4-unix-installation-guide/index.htm](http://download1.swsoft.com/Plesk/Plesk8.4/Doc/en-US/plesk-8.4-unix-installation-guide/index.htm)

Good luck!

-Tim

---

### Post by kubapl on 2008-07-17
Okay well Ive been reading and then fallowing the installation guild I did:
```

Set the execution permission for Auto-installer:

# chmod +x parallels_installer_v3.3.1_build080407.16_os_Ubuntu_6.06_i386

```

And then when I do the next step:
```

# Run the Auto-installer:

# ./parallels_installer_v3.3.1_build080407.16_os_Ubuntu_6.06_i386

```

I get an error:
```

parallels_installer_v3.3.1_build080407.16_os_Ubuntu_6.06_i386: line 1: syntax error near unexpected token 'newline'
parallels_installer_v3.3.1_build080407.16_os_Ubuntu_6.06_i386: line 1: '<HTML>'

```

I downloaded the Autoinstaller build 080407.16 for ubuntu

---

### Post by windependence on 2008-07-17
Are you using Ubuntu 6.06? If not, it won't work, trust me.

-Tim

---

### Post by kubapl on 2008-07-17
Yeah I'm using 8.04 (hardy heron)
Is there anything similar in power to plesk that would work or .  should I wait maybe they are making a version for 8.04 . .. or should I go back to 6.06
?

---

### Post by windependence on 2008-07-17
I would go back to 6.06. The latest and greatest isn't necessarily the best. Just after you install the OS, make sure you load all the latest updates and you will be fine. You do realize Plesk is paid software right?

-Tim

---

### Post by kubapl on 2008-07-17
Paid for there isnt a home free version?

---

### Post by windependence on 2008-07-17
Nope, no free version, just a trial that only lets you set up one domain.

You can try ISPconfig

CPanel is one of the most used but also is not free.

[Here]("http://www.howtoforge.org/perfect-server-ubuntu8.04-lts") is a tutorial that includes an optional ISPconfig install.

I don't use any of them, just set up my virtual hosts using a text editor, but then I don' have hundreds of them either. :)

-Tim

---

### Post by kubapl on 2008-07-17
Well maybe I should say what I want to accomplish and then you can recommend what I may want.

I'm a student of game development I work with C++ and opengl right now and I wanted to throw together a linux server box that would host a website that would let users download games and it would have a comment section. I'm already leaning towards using joomla as my content organizer since I've used it in the past and I loved it. Now you may be asking why don't you just pay for hosting? Well I had a spare computer collecting dust since I upgraded my main rig and I also am currently working on a multilayer game so I'll need a server side program that would handle the game. And Ive been working with linux for a week and a half now.

---

### Post by windependence on 2008-07-17
Joomla would be fine for this, and no, I am not going to ask you why you don't just host it somewhere, I host my own too. :)

Also, you may want to consider setting up a forum for your games. I use simple machines forum with TinyPortal. It even has a download section. Just an idea, but that way you can drop in on the board and get feedback.

-Tim

---

### Post by kubapl on 2008-07-17
Yeah I really like the deal with linux it seem to be soo much faster because I tried hosting with windows and not only did the mysql database crash every 2 days or so sometimes the website itself would be slow to respond.

BTW how do I install the browser side myphpadmin thingy

---

### Post by windependence on 2008-07-17
I think with Ubuntu there should be a package for that.

```
sudo apt-get install phpmyadmin
```

-Tim

---

### Post by kubapl on 2008-07-17
I just hope I wont have problems if I already installed these:
apt-get install mysql-server-5.0
apt-get install php5
apt-get install php5-mysql
apt-get install php5-cli php-pear php5-ldap php5-imap php5-gd\
    php5-mhash php5-odbc php5-ps

---

### Post by windependence on 2008-07-17
Well looks OK to me.

Good luck!

-Tim

---

### Post by hatoyu on 2008-11-27
Install Plesk 8.6 for ubuntu 8.04 server error when I start install

Errors were encountered while processing: /var/cache/apt/archives/psa_8.6.0-ubuntu8.04.build86080722.00_i386.deb E: Sub-process /usr/bin/dpkg returned an error code (1)

ERROR: An error occurred on attempt to install packages. Attention! Your software might be inoperable. Please, contact product technical support.

Yesterday I install successed at other server with no error .

---

