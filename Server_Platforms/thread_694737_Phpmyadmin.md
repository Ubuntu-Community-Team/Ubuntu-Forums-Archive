---
title: "Phpmyadmin"
date: 2008-02-12
forum: Server Platforms
---

### Post by DorZki on 2008-02-12
hello all,
i've installed the UBUNTU server version, and i can't find PHPMYADMIN, please help me...

---

### Post by ikonia on 2008-02-12
1.) why have you installed the server version, if your a new user to ubuntu you may want to consider using the desktop version, it works just as well as server as using the server version, but much more friendly and with packages aimed torwards the home users desktop PC and home server.

2.) I think the package you want is in the universe repo, as you don't have the desktop gui enabled you'll have to edit your /etc/apt/sources.list manually to uncomment the universe repo line.

I'd strongly suggest using the desktop version thought.

---

### Post by DorZki on 2008-02-12
first of all thanks for helping me! :)
secondly, I've used the desktop version, but it's just to much heavy, and i want to use the server version :P, i installed the Webmin as my GUI.

the thing i want to do is to make a shortcut of the folder "phpmyadmin" ( as i recall it's in the path /etc/phpmyadmin ), inside the folder /var/www
so I'll be able to reach phpmyadmin via web access.

---

### Post by ikonia on 2008-02-12
again, I'd strongly advise you to use the desktop version - the only different your mentioning is the actual desktop, to which something like xubuntu will be a more light weight alternative.

On a side note, webmin is NOT a good or secure tool, it is full of exploits and a common source of attack for machines placed on the internet, hence why ubuntu doesn't package it up and support it.

you don't need a short cut you need a symlink using the "ln" command ln -s for a symlink. 

You may also want to look at how apache handles "sites-available" and "sites-enabled" in your document root.

---

### Post by freymann on 2008-02-12
> **DorZki said:**
> the thing i want to do is to make a shortcut of the folder "phpmyadmin" ( as i recall it's in the path /etc/phpmyadmin ), inside the folder /var/www
so I'll be able to reach phpmyadmin via web access.

 Um, if you've installed phpmyadmin, I believe you "get there" with your web browser by going to:

[http://your.local.machine/phpmyadmin/](http://your.local.machine/phpmyadmin/)

 This is done by an "alias" command added to your apache configuration, when phpmyadmin was installed.

 I'm a bit confused as to why you want a shortcut? what is the shortcut for?

---

### Post by mattc908 on 2008-02-12
This should help step by step guide..

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by DorZki on 2008-02-13
> **freymann said:**
> Um, if you've installed phpmyadmin, I believe you "get there" with your web browser by going to:

[http://your.local.machine/phpmyadmin/](http://your.local.machine/phpmyadmin/)

 This is done by an "alias" command added to your apache configuration, when phpmyadmin was installed.

 I'm a bit confused as to why you want a shortcut? what is the shortcut for?

@ikonia - how do i use this command to do so?
@freymann - the problem is it dosen't :\, and this is very strange....
@mattc908 - thanks for the guied :)

---

### Post by freymann on 2008-02-13
> **DorZki said:**
> @ikonia - how do i use this command to do so?
@freymann - the problem is it dosen't :\, and this is very strange....
@mattc908 - thanks for the guied :)

 I'm not sure which release of ubuntu you are using. I'm at 7.10, and when I installed phpmyadmin, it created a symlink for me.

 In the directory: /etc/apache2/conf.d

 I have a symlink that looks like this:

 phpmyadmin.conf -> ../../phpmyadmin/apache.conf

 which is telling me that the file I need to include lives in 

 /etc/phpmyadmin/apache.conf

 So, you need to create this symlink, as you stated in your initial message...

 Open up your terminal and type:

```

 cd /etc/apache2/conf.d

 sudo ln -s /etc/phpmyadmin/apache.conf phpmyadmin.conf

 sudo /etc/init.d/apache2 restart

```

---

### Post by DorZki on 2008-02-13
```
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
root@devisionstudio:~# cd /etc/apache2/conf.d
root@devisionstudio:/etc/apache2/conf.d# ln -s /etc/phpmyadmin/apache.conf phpmy                                                                             admin.conf
root@devisionstudio:/etc/apache2/conf.d# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                             grep: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
 * We failed to correctly shutdown apache, so we're now killing all running apac                                                                             he processes. This is almost certainly suboptimal, so please make sure your syst                                                                             em is working as you'd expect now!
apache2: Syntax error on line 292 of /etc/apache2/apache2.conf: Could not open c                                                                             onfiguration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
                                                                         [fail]
```

i get an error....

---

### Post by freymann on 2008-02-13
> **DorZki said:**
> 
# cd /etc/apache2/conf.d
# ln -s /etc/phpmyadmin/apache.conf phpmy                                                                admin.conf


 I guess you need to ensure that 

/etc/phpmyadmin/apache.conf

 exists.

---

### Post by Rick Z on 2008-02-15
After following up the tips in this post, I am able to install phpmyadmin without any problems.  I have one question about the SSL.  How do I enable phpmyadmin so that when user open up http:// it will redirect to https://

Thanks.

---

### Post by DorZki on 2008-02-16
where can i download PHPMYADMIN for my server?

---

### Post by freymann on 2008-02-16
> **DorZki said:**
> where can i download PHPMYADMIN for my server?

 System > Administration > Synaptic Package Manager

 search for it and install.

---

### Post by faulkes on 2008-02-16
> **freymann said:**
> System > Administration > Synaptic Package Manager

 search for it and install.

The Server Edition does not ship with X installed, so it's unlikely he would have a gui installed to do so.

iirc

```

sudo apt-get install phpmyadmin

```

Faulkes

---

