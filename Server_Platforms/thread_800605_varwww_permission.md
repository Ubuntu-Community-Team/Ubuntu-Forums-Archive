---
title: "/var/www permission"
date: 2008-05-20
forum: Server Platforms
---

### Post by Yoguess on 2008-05-20
Hi,

I have setup a 8.04 server with gnome to serve my website

after setting up the static IP and all I could see the test page "It Works!"

I then tried to copy my website to /var/www/ where there was an index.html (test).  I found out I didnt have permission to write to /www 

so I did "chown -R user /var/www"  GREAT
It allowed me to copy the website to /www directory.

now when I try to access my site [http://localhost](http://localhost) it times out.  I think it it because of the chown permission, How do I set the original permission for /var/www???????

---

### Post by Yoguess on 2008-05-20
or it could be the port??

how do i get apache to listen on port 8080 instead of 80

---

### Post by windependence on 2008-05-20
> **Yoguess said:**
> or it could be the port??

how do i get apache to listen on port 8080 instead of 80

You can specify it in the httpd.conf file.

Generally speaking, you want to set your permissions to 755.

-Tim

---

### Post by Yoguess on 2008-05-20
how do i enter the command with what user?
chown -R user 755 /var/www ????

cuz its still not working
i had changed the port# on server and the router before it broke

help

---

### Post by windependence on 2008-05-20
> **Yoguess said:**
> how do i enter the command with what user?
chown -R user 755 /var/www ????

cuz its still not working
i had changed the port# on server and the router before it broke

help

chmod 755 /var/www

-Tim

---

### Post by cdtech on 2008-05-20
You just want to issue the command "sudo chmod -R 755 /var/www" with no user.

The owner and group have the permission to change or edit files (if givin the right to).

Sample of my /var/www/:
drwxr-xr-x 6 ###### ####      4096 2008-04-22 02:00 wp-content/
-rwxr-xr-x 1 ###### ####       851 2008-04-22 02:00 wp-cron.php*
-rwxr-xr-x 1 ###### ####       120 2008-04-22 02:00 wp-feed.php*
drwxr-xr-x 4 ###### ####      4096 2008-04-22 02:00 wp-includes/
-rwxr-xr-x 1 ###### ####      1525 2008-04-22 02:00 wp-links-opml.php*
-rwxr-xr-x 1 ###### ####     16654 2008-04-22 02:00 wp-login.php*

Notice the 755.....

I use a made up user as the owner of my site which gives that user all the rights to my web server.

If you want to give a user owner rights then you change it with the command "sudo chown -R user /var/www"

The group would be "sudo chgrp -R group /var/www"

---

### Post by Yoguess on 2008-05-20
tried the commands no luck

website still wont come up
i tried restarting apache and the server

when it was working i was unable to copy my website to /var/www
after i changed the permission i could copy to it but site doesnt work.  So is it possible to keep the website somewhere in /home and point apache to that directory after a fresh install???

or should i just try to fix this setup??

---

### Post by cdtech on 2008-05-20
Did you set up your Document root?

sudo pico /etc/apache2/sites-available/default

NameVirtualHost *
<VirtualHost *>
        ServerAdmin user@localhost

        DocumentRoot /var/www/yourdir
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/yourdir/>

---

### Post by ntalamai on 2008-05-20
> **Yoguess said:**
> 
i had changed the port# on server and the router before it broke

help

You can change the port apache is listening to, by:
```
sudo gedit /etc/apache2/ports.conf
```

Change this: Listen 80
to this: Listen 8080

The other posts, the command regarding permissions should work:
"sudo chmod -R 755 /var/www"

---

### Post by lunatinker on 2008-05-20
[http://ubuntuforums.org/showthread.php?t=801216](http://ubuntuforums.org/showthread.php?t=801216)
i posted a similar issue with different solution.
i am not sure is applies to your case, but feel free to look to
/etc/hosts and my solution (suppied by an old feisty issue that
may still be around or ... not)... =)

---

### Post by Yoguess on 2008-05-20
no it didnt work

Can someone tell me if it is possible to keep the website somewhere in /home and point apache to that directory after a fresh install??? If yes, how?

---

### Post by lunatinker on 2008-05-21
Changin DOCUMENT ROOT:
[http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux#Create_document_root](http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux#Create_document_root)
 ( #Create_document_root tagged for halfway down page )
Virtual Hosts are also covered, but you are only asking about the easier docroot. read about permissions in the same link following virtual host setup explained... cheers.
more appropriate to changing to /home/~(username)/www is:
[http://ubuntuforums.org/showthread.php?t=18964](http://ubuntuforums.org/showthread.php?t=18964)
"..The solution is to change the DocumentRoot in  /etc/apache2/sites-available/default change /var/www/ to /home/username/public_html.."
and/or
That thread also talks about [http://localhost/~username/](http://localhost/~username/)
or not using the tilde ( ~ )

---

### Post by Yoguess on 2008-05-21
Thank You Lunatinker for the information
I finally got everything working.  I am using DYNDNS service to get my public address to map my domain XXXXXX.selfip.com

Since my ISP blocks port 80 I am using port 8080 and so my domain becomes XXXXXX.selfip.com:8080

is there a way to hide the port # to its XXXXXX.selfip.com

---

### Post by DaveyG on 2008-05-22
> **Yoguess said:**
> Thank You Lunatinker for the information
I finally got everything working.  I am using DYNDNS service to get my public address to map my domain XXXXXX.selfip.com

Since my ISP blocks port 80 I am using port 8080 and so my domain becomes XXXXXX.selfip.com:8080

is there a way to hide the port # to its XXXXXX.selfip.com

Possibly.. In your router, you would have port forwarding..
I'm using a Belkin, if you are too you can the CP by going to 192.168.2.1 (or sometimes 192.168.1.1)
choose 'Port Forwarding' or 'DNS Servers' then forward all requests from 80 to 8080...

If your not using a Belkin router.. Please specify the Make and Model :)

#Davey

---

### Post by Yoguess on 2008-05-22
I have linksys (WRT54GS) router and I already have setup the port forwarding to Apache2 on port 8080, which is why i have to use 808 in the url.

or are you trying to say i can change apache to port 80 and have the router forward from port 8080 to 80 or something?? im lost

---

### Post by DaveyG on 2008-05-22
No, sorry.. I meant, have Apache to listen to 8080 whilst having the Url set up as domain:80 rather than domain:8080. The router will be forwarding all port 80 requests to 8080..

I'm not sure it will work though as your ISP blocks ports 80.. :|

---

### Post by hvc123 on 2008-05-22
chown -R www-data:www-data /var/www/* 
chmod -R 755 /var/www/*

this will give your web user (apache2) access to the files.

---

### Post by Yoguess on 2008-05-22
Thank You very much guys.

I have figured out a way to fix my port # in url problem.
I use dyndns.com service for my url so i just created a second host which redirected to the first:
site.selfip.com:8080 points to my IP xx.xx.xx.xx
sitex.selfip.com points to site.selfip.com:8080

this gave me my last problem (I hope)
how do i ftp to my server to that specific directory in my /home/user/public_html to make changes using dreamweaver?

---

