---
title: "Apache 2 Virtual Hosts"
date: 2007-03-23
forum: Server Platforms
---

### Post by CaptainCandy on 2007-03-23
Can anyone who knows how to setup Virtual Hosts on Apache 2 running on the Ubuntu LAMP install, read this little lot and tell me where I am going wrong? I have thrown loads of time at it, exhusted all my printed material, and am at my wits end. I am convinced it is something patheticaly stupid I am doing wrong, so if you have any experience of this please help a man on the edge :)

I am trying to get two sites working: [www.ydnac.ath.cx](www.ydnac.ath.cx) & [www.bristolcar-vanhire.ath.cx](www.bristolcar-vanhire.ath.cx) on a little server I have setup at home to use for testing. It is hooked-up to the net via my router for people out there in internet land to test the apps I am going to be developing on it.

When I had just the one site [www.ydnac.ath.cx](www.ydnac.ath.cx) everything was fine. It could be seen on the net no problem, so I know all that side of things is fine. It's just getting a second site going that is blowing my mind. Oh BTW I am a newbie to Linux, LAMP and all, coming from a MS background.

On running apache2 reload I get this:-

briansnr@ubuntu:~$ /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                        [Fri Mar 23 09:48:54 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Mar 23 09:48:54 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
httpd not running, trying to start
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

Here is the stuff I think you will need to help me (if you need more just let me know what you want, and I will get it for you):-


briansnr@ubuntu:~$ cd /etc/apache2/sites-enabled
briansnr@ubuntu:/etc/apache2/sites-enabled$ ls
000-default  bristolcar-vanhire  ydnac-ath-cx  ydnac.ath.cx

briansnr@ubuntu:/etc/apache2/sites-enabled$ cat bristolcar-vanhire
ServerAdmin [email]brian01792@msn.com[/email]
<VirtualHost *:80>
DocumentRoot /var/www/bristolcar-vanhire
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/bristolcar-vanhire/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
ServerName [www.bristolcar-vanhire.ath.cx](www.bristolcar-vanhire.ath.cx)
</VirtualHost>

briansnr@ubuntu:/etc/apache2/sites-enabled$ cat ydnac-ath-cx
NameVirtualHost *:80
ServerAdmin [email]brian01792@msn.com[/email]
<VirtualHost *:80>
ServerName [www.ydnac.ath.cx](www.ydnac.ath.cx)
DocumentRoot /var/www/ydnac-ath-cx
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/ydnac-ath-cx/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
</VirtualHost>

briansnr@ubuntu:/etc/apache2/sites-enabled$ cd ..
briansnr@ubuntu:/etc/apache2$ ls
apache2.conf           httpd.conf           mods-enabled     sites-enabled
apache2.conf.original  httpd.conf.original  ports.conf       ssl
conf.d                 magic                README
envvars                mods-available       sites-available

briansnr@ubuntu:/etc/apache2$ cat httpd.conf
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
Listen 80
NameVirtualHost *:80
<VirtualHost *:80>
        DocumentRoot /var/www/ydnac-ath-cx
        ServerName [www.ydnac.ath.cx](www.ydnac.ath.cx)
</VirtualHost>

<VirtualHost *:80>
        DocumentRoot /var/www/bristolcar-vanhire
        ServerName [www.bristolcar-vanhire.ath.cx](www.bristolcar-vanhire.ath.cx)
</VirtualHost>

briansnr@ubuntu:/etc/apache2$

---

### Post by Brazen on 2007-03-23
You should not edit your httpd.conf and you should not edit anything in sites-enabled.  The only place you should add and edit files is in the /etc/apache2/sites-available directory.  You need to return your httpd.conf to it's original content, and move the files from sites-enabled/ to sites-available/ and then use the a2ensite command to enable your sites.

Also, whenever you post code, put it like this:

[REMOVEMEcode]your code here[REMOVEME/code]

Of course, remove the REMOVEME.  This makes it much easier to read and make sense out of your posted code.

You should probably also read this: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

---

### Post by CaptainCandy on 2007-03-23
Thanks for getting back to me. I had made a backup copy of httpd.conf which I have popped back into place, so that is as it was. When I made my post, I had inadvertantly changed to the /etc/apache2/sites-enabled directory instead of /etc/apache2/sites-available to undertake the cat to show what was in those files. Interestingly; I have just checked and the /etc/apache2/sites-enabled and /etc/apache2/sites-available contain identical files. Should I be deleting those found in /etc/apache2/sites-enabled? Having returned my httpd.conf to it's original state i am still getting:-

 * Reloading apache 2.0 configuration...                                                                                     [Fri Mar 23 13:31:41 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
httpd not running, trying to start
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

when trying to restart. Any ideas?

---

### Post by Brazen on 2007-03-23
So you must have done it right and used a2ensite after creating your sites in /etc/apache2/sites-available.  If you do ```
cd /etc/apache2/sites-enabled
ls -l
```then you will see that those are not actually files, but are actually symlinks that point to the files in /etc/apache2/sites-available, which is how a2ensite sets it up.

Have you posted the contents of EVERY file in /etc/apache2/sites-available?  It would also be useful if you go ahead and post the results of the code block I put above (the ls -l in sites-enabled, and also in sites-available) just to double check things.

---

### Post by CaptainCandy on 2007-03-23
Once again thanks for getting back to me. I have tried loads since your last post all to no avail. The most interesting site I found on the subject was [http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/apachebasic.htm](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/apachebasic.htm) which made me think it was port 80 causing the problem. So went through the whole lot replacing 80 with 8080 but still there was the (13): make_sock: could not bind to address [::]:80 problem. So I have put it all back to 80 now as shown in the cats below.

```

briansnr@ubuntu:/etc/apache2/sites-available$ ls -l
total 12
-rw-r--r-- 1 root root  379 2007-03-23 21:10 bristolcar-vanhire
-rw-r--r-- 1 root root 1143 2006-09-27 17:54 default
-rw-r--r-- 1 root root  354 2007-03-23 21:10 ydnac-ath-cx
briansnr@ubuntu:/etc/apache2/sites-available$ cd ../sites-enabled
briansnr@ubuntu:/etc/apache2/sites-enabled$ ls -l
total 0
lrwxrwxrwx 1 root root 36 2007-03-14 18:08 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 47 2007-03-23 17:48 bristolcar-vanhire -> /etc/apache2/sites-available/bristolcar-vanhire
lrwxrwxrwx 1 root root 41 2007-03-23 17:41 ydnac-ath-cx -> /etc/apache2/sites-available/ydnac-ath-cx
briansnr@ubuntu:/etc/apache2/sites-enabled$ cd ../sites-available
briansnr@ubuntu:/etc/apache2/sites-available$ cat ydnac-ath-cx
ServerAdmin brian01792@msn.com
<VirtualHost 192.168.2.4:80>
ServerName www.ydnac.ath.cx
DocumentRoot /var/www/ydnac-ath-cx
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/ydnac-ath-cx/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
</VirtualHost>
briansnr@ubuntu:/etc/apache2/sites-available$ cat bristolcar-vanhire
ServerAdmin brian01792@msn.com
<VirtualHost 192.168.2.4:80>
DocumentRoot /var/www/bristolcar-vanhire
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/bristolcar-vanhire/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
ServerName www.bristolcar-vanhire.ath.cx
</VirtualHost>
briansnr@ubuntu:/etc/apache2/sites-available$

```

I have also placed the following at the bottom of the apache2.conf file

```

# Added By Me
Listen 80
NameVirtualHost 192.168.2.4:80

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*
briansnr@ubuntu:/etc/apache2$

```

Sorry to be a pain, but your assistance is realy apreciated.

Cheers

Bri

---

### Post by pppetter on 2007-03-24
Hi there!

Keep apache2.conf and your virtualhost files apart! Don't put 
> NameVirtualHosts
In your apache2.conf, and put it in the right place, namely your virtualhost files - apache2.conf is for server settings, not virtualhost settings. I believe that the error msg you got is there becouse you don't have any virtualhosts in your apache2.conf, and you don't have them there becouse they shouldn't be there. :)
Another tip is to put > * Instead of the ip and port, in case you somewhere, sometime change it - then you won't have any trouble.

So you virtualhost files need to contain this information:
> NameVirtualHost *
<Virtualhost *>
ServerName Yourservername
DocumentRoot Yourdocumentroot
</VirtualHost>
You may _if you want to_ put other stuff in there.

Last, but not least, restart apache using
> sudo /etc/init.d/apache2 restart

I have a hangover, and that's why my text is so lame and stuff like that. Sorry.

EDIT: This is just my idea of why ONE of the error messages is there - I may be wrong, but the things I have written about is still true.

---

### Post by CaptainCandy on 2007-03-24
Thanks for that. I have removed my additions to the apache2.conf, and made the alterations you have recomended. However I nog get:-
```

briansnr@ubuntu:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...                                   [Sat Mar 24 14:40:14 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Sat Mar 24 14:40:14 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
briansnr@ubuntu:/etc/apache2/sites-available$

```

Here are the cats of my sites available
```

briansnr@ubuntu:/etc/apache2/sites-available$ cat ydnac-ath-cx
ServerAdmin brian01792@msn.com
Listen 80
NameVirtualHost *
<VirtualHost *>
ServerName www.ydnac.ath.cx
DocumentRoot /var/www/ydnac-ath-cx
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/ydnac-ath-cx/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
</VirtualHost>
briansnr@ubuntu:/etc/apache2/sites-available$ cat bristolcar-vanhire
Listen 80
NameVirtualHost *
ServerAdmin brian01792@msn.com
<VirtualHost *>
ServerName www.bristolcar-vanhire.ath.cx
DocumentRoot /var/www/bristolcar-vanhire
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
<Directory /var/www/bristolcar-vanhire/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
</VirtualHost>

```
If you would prefer I can open up OpenSSH for you to have a dig around yourself if you like. There is nothing sensative on this server, only some crap test stuff so I don't care who has a look around. Just email me and I will hit you back with the IP and login details. I am realy desperate to get some work done, and this is holding me back big style. Thanks for all your help.

---

### Post by GSMD on 2007-04-28
It doesn't really matter where you put **NameVirtualHost** and any of the other directives; that config file separation offered buy Ubuntu is solely for usability matters.
I'm facing the same warning message on my Dapper => Feisty upgraded VPS while on Feisty that's been installed from scratch there's no such issue.
For now I just commented 
it out.

---

### Post by grogoreo on 2007-04-28
It seems the problem is that there's no connection between the request of port 80 and the listening of apache since it can't bind the address.
On my configuration I put everything to do with the virtual host inside the tag <VirtualHost> but you seem to have some bits outside. Also, you don't specify a log which is helpful to diagnose problems. An example, which is based off mine:
```

<VirtualHost *:80>
        # Server Settings
        ServerAdmin brian01792@msn.com
        ServerName ydnac.ath.cx
        ServerAlias ydnac.ath.cx www.ydnac.ath.cx

        DocumentRoot /var/www/ydnac-ath-cx
        <Directory />
                Options FollowSymLinks
                #AllowOverride None
        </Directory>
        <Directory /var/www/ydnac-ath-cx>
                Options Indexes FollowSymLinks MultiViews
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error-ydnac-ath-cx.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access-ydnac-ath-cx.log combined
        ServerSignature On

</VirtualHost>

```
In /etc/apache2/ports.conf I just have:
```

Listen 80

```

---

