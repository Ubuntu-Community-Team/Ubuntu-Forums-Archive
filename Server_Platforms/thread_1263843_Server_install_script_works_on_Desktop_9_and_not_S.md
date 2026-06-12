---
title: "Server install script works on Desktop 9 and not Server 9"
date: 2009-09-11
forum: Server Platforms
---

### Post by dragonfly7358 on 2009-09-11
I used the following script to set up a server on ubuntu desktop 9.04 by runing:
 
> . install.sh  
> #!/bin/sh/
#install.sh
sudo aptitude install apache2 -y
sudo aptitude install php5 -y
sudo aptitude install libapache2-mod-php5 -y
sudo /etc/init.d/apache2 restart
sudo aptitude install php5-curl -y
sudo aptitude install php5-gd -y
sudo aptitude install php-pear -y
sudo aptitude install php5-mcrypt -y
sudo /etc/init.d/apache2 restart
sudo chown -R drone /var/www
sudo chmod -R 777 /var/www
 
I have recently installed a fresh copy of ubuntu server 9.04. When I run the above command I get the following error:
> "Couldn't Find package apache2"
 
If I run the first command outside of the script:
> sudo aptitude install apache2 -y
 
The install goes as expected. Any ideas on what I can check?

---

### Post by cariboo on 2009-09-11
Wouldn't it just be easier to use tasksel?

```
sudo tasksel
```

Unless no one has access to your sever, setting the permissions of /vaw/www to world read/writable and ownership to your user is not a very good idea, as that means anyone can change index.html

---

### Post by dragonfly7358 on 2009-09-11
What I have done so far:
Install a basic server version. Remastersys to make an iso. Burned using unetbootin to USB drive. 
 
At this point I have a non-persitent server installation active like a live-cd on a usb drive. On boot I have a script that will get an external script, marks for executing, and runs the script. 
 
This is the script I mentioned above. I am happy to change it, but I need to be able to download a file, that can be executed. What I need this file to do is install apache, php, some extra php modules, then run a php file (which the script will need to download).
 
This is my second week working with linux.
 
I will read into tasksel, the machine(s) will be isolated and not have any user interaction.

---

### Post by dragonfly7358 on 2009-09-11
I have changed the file I am running to 
 
>  
#!/bin/sh
sudo tasksel install apache2^

 
When I run the script I get no output.

---

### Post by wojox on 2009-09-11
At the top put 

```
sudo aptitude update
```

---

### Post by dragonfly7358 on 2009-09-11
I get a list of options and an error "This aptitude does not have Super Cow Powers". Then the apache message cannot be found, thank you for working through this with me.

---

### Post by cariboo on 2009-09-11
When you run tasksel it presents you with a menu of installation tasks. Once the menu is up select LAMP, and all the packages you are trying to install via your script will be install automatically, and the porper permissions and ownership will be applied.

---

### Post by dragonfly7358 on 2009-09-11
I would like lamp sans m. I also won't be able to configure at the system, again the script will need to have the instructions for installing the needed components. I will look into the packages listed in tasksel and try the commands directly.

---

### Post by dragonfly7358 on 2009-09-11
Tried the following script

> #!/bin/sh
sudo aptitude update
sudo tasksel install lamp-server

Back to the super cow message. I am currently logged in as a user and not root.

---

### Post by wojox on 2009-09-11
Try this:

```
#!/bin/bash
#######################################################################
# Ubuntu-Server-Setup
#######################################################################
echo "[*] Installing Apache2 and PHP5"
sudo apt-get -y install apache2 php5 libapache2-mod-php5
echo "[*] Restarting Apache2"
sudo /etc/init.d/apache2 restart
echo "[*] Installing Curl, GD, Pear, and Mcrypt"
sudo apt-get -y install php5-curl php5-gd php-pear php5-mcrypt
echo "[*] Restarting Apache2"
sudo /etc/init.d/apache2 restart
echo "[*] Changing the owner + mode"
sudo chown -R drone /var/www
sudo chmod -R 777 /var/www 
```

---

### Post by dragonfly7358 on 2009-09-11
I will try your solution next.
Here is something funky I discovered.

> #!/bin/sh
sudo apt-get install apache2

When I place this in an html file on a remote server:
wget (a)
sh (a)
It can't find the package.

If I create a file locally:
pico (b) 
sh (b)
It will run and do the install correctly.

---

### Post by dragonfly7358 on 2009-09-11
Same old error messages about cows.

---

### Post by dragonfly7358 on 2009-09-11
ls -l . shows the following:
a (remote)   -rw-r--r-- 1 drone root
b (local)    -rw-r--r-- 1 drone drone

chown drone:drone a changed permissions:
a (remote)   -rw-r--r-- 1 drone drone
b (local)    -rw-r--r-- 1 drone drone

---

### Post by dragonfly7358 on 2009-09-11
> diff a b:
< #!/bin/sh
< sudo apt-get install apache2
---
> #!/bin/sh
> sudo apt-get install apache2

If I copy b to c and diff b c I get 0 differences. The remote file (a) was created on a windows server.

---

### Post by cariboo on 2009-09-11
It sounds like you either have a connectivity problem or a permission problem. When you run sudo apt-get update do you get any output on the screen? I got the super cow error earlier today, because I wasn't using sudo properly.

---

### Post by dragonfly7358 on 2009-09-11
If I run it from the console directly: no errors
Directly: no errors
a (remote sh file): errors
b (local sh file): no errors

---

### Post by dragonfly7358 on 2009-09-11
Looks like if create a file the file in linux, and then transfer to windows I can make changes and then I can run that file from windows. Strange, but it works perfectly now! Thank you all very much.

---

