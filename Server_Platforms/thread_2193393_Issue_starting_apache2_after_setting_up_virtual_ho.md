---
title: "Issue starting apache2 after setting up virtual host"
date: 2013-12-12
forum: Server Platforms
---

### Post by jesse3 on 2013-12-12
I have Ubuntu 13.04 (GNU/Linux 3.8.0-34-generic x86_64) installed on my system and I use this system as a media and smb server.
I wanted to be able to listen to my music on my server remotely. I talked with a friend who suggested to use an old program that is no long in the Debian repositories Gnump3d.
Which I believe is setup correctly, and can be accessed.
I have a really slow internet connection 700kbps - 1.2mbps Down, 192kbps or under. Up.
I've been able to listen to the music on my server remotely with my host name or using my local ip, but I've been having issues with skipping. Ie. replaying the same song without finishing or just skipping through the songs all together. 
In a sight walk through it was suggested to install apache2, which I did. Since I had been having issues with skipping, I attempted to down sample the mp3 tracks with lame, but it didn't improve.
So I found an article to use apache2 to rate limit [http://blog.edseek.com/archives/2008/08/08/rate-limit-gnump3d-with-apache-22-and-mod_bw/](http://blog.edseek.com/archives/2008/08/08/rate-limit-gnump3d-with-apache-22-and-mod_bw/), but I have never created a virtual host so I used this article to make the virtual host [https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts](https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts)
I completed the steps in the virtual host article, but when I tried to restart apache2 I get:

administrator@servermy:~$  sudo service apache2 restart
sudo: /var/lib/sudo writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
 * Restarting web server apache2        Action 'start' failed.
The Apache error log may have more information.
[fail]

So I looked in /var/log/apache2/error.log and found: 

Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/$/var/log/apache2/xxxxx.dyndns-ip.com_error.log/error.log.

I don't know what I have to do fix this????

---

### Post by houstonbofh on 2013-12-13
It is trying to place you log file in /etc...  You have 2 lines in your config file on one line, essentially.  Get the config file, and look for the /var/log/apache2/xxxxx.dyndns-ip.com_error.log/error.log line and fix your typo.

---

### Post by jesse3 on 2013-12-15
> **houstonbofh said:**
> It is trying to place you log file in /etc...  You have 2 lines in your config file on one line, essentially.  Get the config file, and look for the /var/log/apache2/xxxxx.dyndns-ip.com_error.log/error.log line and fix your typo.

I typed sudo nano /etc/apache2/sites-available/xxxxx.dyndns-ip.com
 Edited the lines to:
ErrorLog $ /var/log/apache2/xxxxxx.dyndns-ip.com_error.log

CustomLog $ /var/log/apache2/xxxxxx.dyndns-ip.com_access.log combined

Both files are in /var/log/apache2/

But I still get in the default error log

(2)No such file or directory: apache2: could not open error log file /etc/apache2/$/var/log/apache2/xxxxxx.dyndns-ip.com_error.log/error.log.
Unable to open logs

---

### Post by CharlesA on 2013-12-16
Post your entire virtualhost configuration please.

---

### Post by jesse3 on 2013-12-16
> **CharlesA said:**
> Post your entire virtualhost configuration please.

  GNU nano 2.2.6 File: ...c/apache2/sites-available/xxxxxx.dyndns-ip.com Modified 



_<VirtualHost *:80> 

    ServerAdmin [email]administrator@xxxxxx.dyndns-ip.com[/email] *



    DocumentRoot /var/www/xxxxxx.dyndns-ip.com/public_html 
    <Directory />

         Options FollowSymLinks

        AllowOverride None 

    </Directory>

     <Directory /var/www/>

         Options Indexes FollowSymLinks MultiViews *

        AllowOverride None 

        Order allow,deny 

        allow from all 

       </Directory>



      ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/ 
     <Directory "/usr/lib/cgi-bin">

             AllowOverride None 

         Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch 

          Order allow,deny 

              Allow from all 

        </Directory> 

 ErrorLog $ /var/log/apache2/xxxxxx.dyndns-ip.com_error.log

         # Possible values include: debug, info, notice, warn, error, crit, 
   
         # alert, emerg. 

CustomLog $ /var/log/apache2/xxxxxx.dyndns-ip.com_access.log combined 
</VirtualHost>

---

### Post by CharlesA on 2013-12-16
> **jesse3 said:**
> * GNU nano 2.2.6 File: ...c/apache2/sites-available/xxxxxx.dyndns-ip.com Modified *
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
_<VirtualHost *:80> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * ServerAdmin [email]administrator@xxxxxx.dyndns-ip.com[/email] * * * * * * * * * * * * * **
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * DocumentRoot /var/www/xxxxxx.dyndns-ip.com/public_html * * * * * * * * * **
* * * * <Directory /> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * * * * * Options FollowSymLinks * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * AllowOverride None * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * </Directory> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * <Directory /var/www/> * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * * * * * Options Indexes FollowSymLinks MultiViews * * * * * * * * * * * * * *
* * * * * * * * AllowOverride None * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * Order allow,deny * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * allow from all * * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * </Directory> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/ * * * * * * * * * * * * * * * * * * *
* * * * <Directory "/usr/lib/cgi-bin"> * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * AllowOverride None * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch * * * * * * * * **
* * * * * * * * Order allow,deny * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * Allow from all * * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * </Directory> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * ErrorLog [COLOR="#FF0000"]**$ **[/COLOR]/var/log/apache2/xxxxxx.dyndns-ip.com_error.log * * * * * * * * *
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * # Possible values include: debug, info, notice, warn, error, crit, * * * * **
* * * * # alert, emerg. * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * LogLevel warn * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* * * * CustomLog [COLOR="#FF0000"]**$ **[/COLOR]/var/log/apache2/xxxxxx.dyndns-ip.com_access.log combined * * *
</VirtualHost> * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
*

I hope nano is the one adding all those asterisks. Remove the character in red. Then restart apache2.

---

### Post by jesse3 on 2013-12-16
> **CharlesA said:**
> I hope nano is the one adding all those asterisks. Remove the character in red. Then restart apache2.

Changed the virtual host by removing $ but I get the same error

---

### Post by CharlesA on 2013-12-16
I'm guessing it has to do with the way you are referencing the log location.

I checked my old web server and this is what the virtualhost looks like:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName charlesa.net
        DocumentRoot /home/charles/site/charlesa.net/
        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

---

### Post by jesse3 on 2013-12-23
> **CharlesA said:**
> I'm guessing it has to do with the way you are referencing the log location.

I checked my old web server and this is what the virtualhost looks like:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName charlesa.net
        DocumentRoot /home/charles/site/charlesa.net/
        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

Backed up my virtual host file realized that I was missing a few lines at the top but that was there when I was having the issue before so I changed mine to yours but still had the same issue, I looked in the /etc/apache2 folder and seen $error.log. and $xxxxxx.dyndns-ip.com_error.log. 
So I removed both files and I got unable to open error log /etc/apache2/{APACHE_LOG_DIR}/error.log, so I changed the line to just line to just error.log then I got the same error msg as before.

---

### Post by CharlesA on 2013-12-23
Something in your apache config is messed up.

I guess you could purge and reinstall apache, but this would take the web server down until you get Apache set up again.

```
sudo apt-get purge apache2 apache2.2-common
```
```
sudo apt-get install apache2
```

---

### Post by jesse3 on 2013-12-31
> **CharlesA said:**
> Something in your apache config is messed up.

I guess you could purge and reinstall apache, but this would take the web server down until you get Apache set up again.

```
sudo apt-get purge apache2 apache2.2-common
```
```
sudo apt-get install apache2
```

So I did both of those commands, but still got the error msg. while installing even.
```
sudo apt-get remove apache2 apache2.2-common
``` then
```
sudo apt-get purge apache2 apache2.2-common
```
```
sudo apt-get install apache2
``` 
Still got same error during install. Then I did 
```
sudo apt-get update
``` then ```
sudo apt-get autoremove
``` 
Then rebooted and tried remove purge and install same error.

So finally I did remove, purge, and autoremove the rebooted to make sure no file where being used.

Then 
```
sudo rm -r /etc/apache2
``````
sudo rm -r/var/log/apache2
```
```
sudo apt-get install apache2
```

sudo service apache2 restart
sudo: /var/lib/sudo writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
 * Restarting web server apache2

---

### Post by CharlesA on 2013-12-31
Question: Why do you have /var/lib/sudo set to 775 as far as permissions go?

---

### Post by jesse3 on 2013-12-31
Uh, I don't know I didn't know it had changed how do I change that???

---

### Post by CharlesA on 2013-12-31
> **jesse3 said:**
> Uh, I don't know I didn't know it had changed how do I change that???

The permissions should look like this:

```
charles@Precise:~$ sudo ls -ld /var/lib/sudo
drwx------ 3 root root 4096 Jan  1  1985 /var/lib/sudo
charles@Precise:~$ sudo ls -l /var/lib/sudo
total 4
drwx------ 2 root charles 4096 Jan  1  1985 charles
charles@Precise:~$

```

```
sudo chmod 4700 /var/lib/sudo
```

Should fix it, but I would be worried if other files have had their permissions changed. Is this server accessible from the internet?

---

### Post by jesse3 on 2013-12-31
It is but I probly did it..

Before
```
sudo ls -ld /var/lib/sudo
sudo: /var/lib/sudo writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
drwxrwxr-x 3 root administrator 4096 Jan  1  1985 /var/lib/sudo
```

```
sudo ls -l /var/lib/sudo
sudo: /var/lib/sudo writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
total 4
drwxrwxr-x 2 root administrator 4096 Jan  1  1985 administrator
```

After

```
sudo ls -ld /var/lib/sudo
sudo: /var/lib/sudo/administrator writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
drws------ 3 root administrator 4096 Jan  1  1985 /var/lib/sudo
```

```
sudo ls -l /var/lib/sudo
sudo: /var/lib/sudo/administrator writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
total 4
drwxrwxr-x 2 root administrator 4096 Jan  1  1985 administrator
```

I can't seem to find how to get apxs2???

---

### Post by CharlesA on 2013-12-31
Oh, whoops.

It should be:

```
sudo chmod 40700 /var/lib/sudo/administator
```

---

### Post by jesse3 on 2014-01-01
Before
```
sudo ls -ld /var/lib/sudo
sudo: /var/lib/sudo/administrator writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
drws------ 3 root administrator 4096 Jan  1  1985 /var/lib/sudo
```

```
sudo ls -l /var/lib/sudo
sudo: /var/lib/sudo/administrator writable by non-owner (040775), should be mode 0700
[sudo] password for administrator: 
total 4
drwxrwxr-x 2 root administrator 4096 Jan  1  1985 administrator
```

After
```
sudo ls -ld /var/lib/sudo
drws------ 3 root administrator 4096 Jan  1  1985 /var/lib/sudo
```

```
sudo ls -l /var/lib/sudo
total 4
drws------ 2 root administrator 4096 Dec 31 23:08 administrator
```

Not drwx------ ?????

---

### Post by CharlesA on 2014-01-01
Looks like the sticky bit is set, but the previous command should have fixed that. Are you still getting those permissions errors when you use sudo?

---

### Post by jesse3 on 2014-01-01
No, after I entered that it stopped.
But I can't find a way to get apxs2???

---

### Post by CharlesA on 2014-01-01
> **jesse3 said:**
> But I can't find a way to get apxs2???

It looks like that is just used to manage modules. I think a2enmod/a2dismod do the same thing: [http://www.unixmen.com/how-to-enable-and-disable-apache-modules/](http://www.unixmen.com/how-to-enable-and-disable-apache-modules/)

---

