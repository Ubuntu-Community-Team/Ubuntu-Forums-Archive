---
title: "Permission error 403 problem"
date: 2010-06-24
forum: Server Platforms
---

### Post by danielbujor on 2010-06-24
Hi guys ! Noob with linux. I switched from opensuse yesterday and i'm trying to configure the personal pc. In opensuse was pretty easy because i only needed to use the yast.

Now:
I've got 403 error
[PHP]Forbidden

You don't have permission to access / on this server.

Apache/2.2.14 (Ubuntu) Server at ros Port 80[/PHP]
/etc/apache2/sites-available/ros
[PHP]<VirtualHost 127.0.0.2:80>
        ServerAdmin admin@ros
        ServerName ros
	ServerAlias ros
        DocumentRoot /home/daniel/Public/ros      
        <Directory /home/daniel/Public/ros/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>[/PHP]

The /etc/hosts file 
[PHP]127.0.0.2	ros www.ros[/PHP]
 Also in /var/log/apache2/error.log
[PHP][Thu Jun 24 11:32:20 2010] [crit] [client 127.0.0.2] (13)Permission denied: /home/daniel/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable[/PHP]

I have chown the /home/daniel/Public/ros folder with the following command [PHP]chown -R daniel:www-data /home/daniel/Public/ros[/PHP]
Thank you !

---

### Post by Ryan Dwyer on 2010-06-24
Do you have a .htaccess file at /home/daniel/.htaccess? What are its permissions?

What are the permissions of the files in /home/daniel/Public/ros/?

---

### Post by danielbujor on 2010-06-24
> **Ryan Dwyer said:**
> Do you have a .htaccess file at /home/daniel/.htaccess? What are its permissions?

What are the permissions of the files in /home/daniel/Public/ros/?

Q.1: No, I don't have a .htaccess in /home/daniel/
Q.3: "ls -lt" command in ~/Public returns:
[PHP]
total 4
drwxr-xr-x 2 www-data www-data 4096 2010-06-24 15:02 ros
[/PHP]

---

### Post by danielbujor on 2010-06-24
**DONE**

I asked at ServerFault ( [http://tiny.cc/4jeuo](http://tiny.cc/4jeuo) ) and someone helped me with [PHP]chmod +x /home/daniel[/PHP]. Thanks anyway !
Dan

---

