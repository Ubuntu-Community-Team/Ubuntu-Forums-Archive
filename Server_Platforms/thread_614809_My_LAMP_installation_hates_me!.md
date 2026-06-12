---
title: "My LAMP installation hates me!"
date: 2007-11-16
forum: Server Platforms
---

### Post by enchance on 2007-11-16
LAMP doesn't work! Installed LAMP in Gutsy desktop through
```
$ sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql
```

but I couldn't get it to run. I keep getting an error after running "http://localhost/oodles":

```
Forbidden

You don't have permission to access /oodles/ on this server.

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80
```

What should I do? Or better yet--How do I uninstall it??? :(

---

### Post by thegnuguru on 2007-11-16
Is the directory your trying to access a symlink?

---

### Post by enchance on 2007-11-16
Sorry, but what's a symlink? My files are saved in "/var/www/"

---

### Post by enchance on 2007-11-16
I tried some things to make it work (without changing any of my previous changes) but still nothing:
1. **FAILED**: Changed the permissions of /var/www to drwxr-x--x (chmod 751)
2. **FAILED**: Changed the permissions of /var/www/oodles to drwxr-xr-- (chmod 754)
3. **FAILED**: Added "ServerName localhost" to /etc/apache2/apache2.conf
4. **FAILED**: Added "ServerName localhost" to /etc/apache2/httpd.conf
5. **FAILED**: Typed "sudo chown -R $USER:$USER /var/www"

I also ran  "sudo netstat -plant | grep LISTEN" to see if apache2 was running and it was as you can see from below:
```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4762/mysqld         
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4896/smbd           
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     5183/apache2        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4686/cupsd          
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4896/smbd 

```

I don't know what I'm gonna doooo! :(

Worst comes to worst, how do I uninstall? Or should I have installed the server edition instead of desktop? If I do install the server ed. can I still run my eyecandy like compiz-fusion and other stuff?

---

### Post by wolfear on 2007-11-16
Posted a reply in your other thread before I saw this one. Hope it helps.

---

### Post by enchance on 2007-11-16
> **wolfear said:**
> Posted a reply in your other thread before I saw this one. Hope it helps.

Saw it, I don't think I'm that adventurous yet. What if I uninstall it and install it again?

---

### Post by wolfear on 2007-11-17
Rather than post in 2 thread, I'll just consolidate here:

From the other thread:

From what I understand, you were wanting to changs the document root due to permission problem.
That doesn't fix your underlying issue.
It just moves it to another directory and then you just have a whole different set of problems.

Get the permission corrected first using the default setup, and the rest is smooth sailing.

Setting the correct permissions is a WHOLE lot easier than mucking around in random config files.

I'm no wizard, but I've worked with apache a bit on my own local server setups.

if things have gotten way out of whack, reinstalling might be easier than trying  to undo everything that has gotten changed, but generally things can be sorted out without resorting to that.

On a side note...did you restart apache after you made the changes?

---

### Post by enchance on 2007-11-20
I finally got it! The permissions for the folder need to be **drwxr-xr-x** or **-rwxr-xr-x** if it is a file. So it *was* a permissions problem after all!

To change permissions of all your files, go to your root folder and type
```

sudo chmod 755 -Rfv foldername
```
What this will do is change the permissions for the folder and all its files/folders inside it. I have 2 sites in my root, hence I separated each one into its own folder. All I have to do is run the command 2x.

I found the solution by making a folder in the www directory using the terminal and then looking at its permissions. Finally! :KS

---

### Post by wolfear on 2007-11-21
> **enchance said:**
> I finally got it! The permissions for the folder need to be **drwxr-xr-x** or **-rwxr-xr-x** if it is a file. So it *was* a permissions problem after all!

To change permissions of all your files, go to your root folder and type
```

sudo chmod 755 -Rfv foldername
```
What this will do is change the permissions for the folder and all its files/folders inside it. I have 2 sites in my root, hence I separated each one into its own folder. All I have to do is run the command 2x.

I found the solution by making a folder in the www directory using the terminal and then looking at its permissions. Finally! :KS

Glad you got it figured out.
Since this is a local desktop/server you are working with, you can make life a bit easier by:
```

sudo adduser YOURUSERNAME www-data
sudo chown -R www-data:www-data /var/www 
sudo chmod -R g+rw /var/www

```

Either way, glad it's working now.

---

### Post by enchance on 2007-11-21
> **wolfear said:**
> 
```

sudo adduser YOURUSERNAME www-data
sudo chown -R www-data:www-data /var/www 
sudo chmod -R g+rw /var/www

```

Either way, glad it's working now.

What does this do? I remember seeing www-data in apache.conf, I think. And yes, I'm running a local server I installed through Synaptic.

---

### Post by wolfear on 2007-11-24
Sorry for the delay. We had the whole holiday thing going.

What that does is add your user (the name you log in with) into the www-data group.

Then it gives read/write permissions to your /var/www directory to group members (i.e- you) while keeping everyone else out.

By doing this, you can make changes in the /var/www folder without running into the permissions problems and you don't have to lower the permissions on the directory.


I use this setup myself on my local server as I do a lot of development work and it would be a huge PITA to have to mess with the permissions on a "per directory" basis in /var/ww

---

### Post by enchance on 2007-11-24
> **wolfear said:**
> 

What that does is add your user (the name you log in with) into the www-data group.

Then it gives read/write permissions to your /var/www directory to group members (i.e- you) while keeping everyone else out.

By doing this, you can make changes in the /var/www folder without running into the permissions problems and you don't have to lower the permissions on the directory.


Oh, I see. Yeah, this would really help me out a lot. Thanks wolfear!

---

### Post by wolfear on 2007-11-24
Your welcome.

---

