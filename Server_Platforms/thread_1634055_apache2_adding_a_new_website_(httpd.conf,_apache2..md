---
title: "apache2 adding a new website (httpd.conf, apache2.conf, sites-available)"
date: 2010-11-30
forum: Server Platforms
---

### Post by killboymota on 2010-11-30
im spending a lot of time trying to resolve this issue. 

I could setup my server today using LAMP. Even could upload the whole php files via ftp. I could get the Phpmyadmin app to work properly. And i could browse the files correctly. But it seem like mod_rewrite wasn't active. So i used a2enmod write to activate it. Well, here all my problems began. 
I was connected directly to my server and suddenly i couldn't browse anything. 
I tried a few tutorials on the forum but most of them doesn't work. [Here's one]("http://library.linode.com/web-servers/apache/installation/ubuntu-10.04-lucid"). 
I made a lot of changes and i'm totally confused right now. 

Could somebody point me some good tutorials? oh please guide me in this darkness path...

---

### Post by tad1073 on 2010-11-30
look at the command you entered "a2emod write"
it should be a2emod rewrite

---

### Post by eeffoc on 2010-11-30
> **tad1073 said:**
> look at the command you entered "a2emod write"
it should be a2emod rewrite

Fairly certain that it should be a2enmod.

***EDIT***
OP has the correct syntax for the aforementioned command, although as Tad stated: a2enmod rewrite should be applied.

---

### Post by killboymota on 2010-11-30
okay, i did that (my mistake) i used a2enmod rewrite.

But now everything is not working.

* Starting internet superserver inetd                                   [ OK ]                     
 * Starting NTP server ntpd                                              [ OK ]                     
 * Starting ftp server proftpd                                                   - warning: unable t
o determine IP address of '_none_'                                                                  
 - error: no valid servers configured                                                               
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'                                                    [fail]                     
 * Starting web server apache2                                                  apache2: Syntax error on line 241 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/website.com: No such file or directory        

I get root@(none) all the time...
in line 241 is the path to /etc/apache2/apache2.conf. To be honest, i tried removing apache2 and reinstalling but this didn't work. Maybe it's an external file i have to edit?

---

### Post by killboymota on 2010-11-30
when i try to start apache i've got this problem.

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Syntax error on line 241 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/website.com.conf: No such file or directory

Line 241 seems to be okay.

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

After that there's nothing.

---

### Post by James78 on 2010-11-30
Is the site actually enabled though? The config should be in /etc/apache2/sites-available/website.com.conf

So if it's in there, just do a

```
sudo a2enmod website.com.conf
sudo service apache2 reload
```

---

### Post by uRock on 2010-11-30
Related threads merged.

---

### Post by killboymota on 2010-11-30
root@(none):~# sudo nano /etc/apache2/apache2.conf
root@(none):~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                ... waiting                                                            [ OK ]
[B]root@(none):~# a2enmod userdir
Enabling module userdir.[/B]
Run '/etc/init.d/apache2 restart' to activate new configuration!
root@(none):~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                ... waiting (98)Address already in use: make_sock: could not bind to address 178.79.145.87:80
no listening sockets available, shutting down
Unable to open logs
                                                                        [fail]

now the problem began enabling a2enmod userdir.. how can i remove it?

---

### Post by killboymota on 2010-11-30
i fixed it. Using [This Thread]("http://ubuntuforums.org/showthread.php?t=1563379"). I added ServerName myserver.com at the end of apache2.conf. I erased the userdir mod.

Now i can see my site live.

But i cannot browse all directories... each time i click a link to a page (php) it says **not found**!

---

