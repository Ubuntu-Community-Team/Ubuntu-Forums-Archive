---
title: "Apache Web Server"
date: 2009-08-27
forum: Server Platforms
---

### Post by kcp601 on 2009-08-27
Hi everyone,
I have just installed ubuntu server edition. I have also installed apache webserver. However in the default.cfg configuration file have set the directory for my sites files. But when i type localhost in the browser it comes up with 404 the page you requested cannot be found even though i have created an index.html file. I have also instlalled php my admin and that works fine. can anyone help. The exact contents of my default.cfg file is below. Thanks in advance! p.s. i am fairly new to this so if it's obvious im sorry! And my default.cfg file path on my machine is /etc/apache2/sites-avalible/ Thanks 

-------------------------------------------DEFAULT.CFG--------------------------------------------------------------------
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/kieren/public_html/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/kieren/public_html/
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /home/kieren/public_html/cgi-bin/
    <Directory "/home/kieren/public_html/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
-------------------------------------------------DEFAULT.CFG-----------------------------------------------------------

---

### Post by nhanquy on 2009-08-27
The file name should be default not default.cfg (?)
Also do you have the directory /home/kieren/public_html/ ? check permission, .....

---

### Post by kcp601 on 2009-08-28
Thank's and yes i have reolved the .cfg bit & yes the directory does exist and the permissions are correct. I just don't know why it won't work. Go to [B][http://tinyurl.com/86zx2](http://tinyurl.com/86zx2)

If it doesnt work (it should work when it comes up with 404 and the apache server stuff at the bottom) then please could you help me out with the port forwarding and getting it set up as i dont really understand the subnet mask & broadcast settings ect. Thank's sorry again if the answers staring me in the face!
[/B]

---

### Post by denver on 2009-08-28
Every folder in that path:

/home/kieren/public_html/

must have correct permissions, not just public_html.

If public_html has correct permissions, but the parrent does not, then it will fail. Make sure all the folder in that path have at least Read and Execute permissions.

That includes /home and /home/kieren . Also, Apache2 runs under user www-data and group www-data. Make sure that it is allowed to get to your public_html.

EDIT: [http://tinyurl.com/86zx2](http://tinyurl.com/86zx2) --> seems to lead to 192.168.2.3. That is your internal LAN private address. That need to be your public IP address.

---

### Post by kcp601 on 2009-08-28
Hi thanks for your reply. Now i did the permissions bit as you sugested and thats done. But it still doesn't seem to work. This bit of your reply i didn't get

That includes /home and /home/kieren . Also, Apache2 runs under user www-data and group www-data. Make sure that it is allowed to get to your public_html.

Where exactly is this located?

EDIT: [http://tinyurl.com/86zx2](http://tinyurl.com/86zx2) --> seems to lead to 192.168.2.3. That is your internal LAN private address. That need to be your public IP address.

And how would i get a public i.p. adress.

Sorry if it's blatantly obvious!:)

---

### Post by kcp601 on 2009-08-29
Hi everyone, sorry for the double post but i thought it would be more useful here.
I have just installed ubuntu server edition. I have also installed apache webserver. However in the default configuration file have set the directory for my sites files. But when i type localhost in the browser it comes up with 404 the page you requested cannot be found even though i have created an index.html file. I have also instlalled php my admin and that works fine. can anyone help. The exact contents of my default file is below. Thanks in advance! p.s. i am fairly new to this so if it's obvious im sorry! And my default file path on my machine is /etc/apache2/sites-avalible/ Thanks 

-------------------------------------------DEFAULT--------------------------------------------------------------------
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/kieren/public_html/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/kieren/public_html/
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /home/kieren/public_html/cgi-bin/
    <Directory "/home/kieren/public_html/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
-------------------------------------------------DEFAULT-----------------------------------------------------------

And also does anyone know how i can get a static i.p. adress! Thank's

---

### Post by zemon_ on 2009-08-29
Have you rebooted the system and restarted apache after changing the configuration.

```
reboot
```

```
/etc/init.d/apache2 restart
```

---

### Post by phantasmik on 2009-08-29
Do you want to configure your Server box to have a local static IP address?

or were you referring to having a static IP address from your ISP?

I may be able to point you in the right direction for either, let me know

---

