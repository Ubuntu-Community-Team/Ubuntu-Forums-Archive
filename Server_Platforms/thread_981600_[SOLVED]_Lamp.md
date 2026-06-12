---
title: "[SOLVED] Lamp"
date: 2008-11-13
forum: Server Platforms
---

### Post by quikone8 on 2008-11-13
Is it possible to install LAMP after the server is up and running?  I would like to set up a blog server.  If not, I have noticed that Apache is on my machine but it does not seem to be listening to any ports.  Plus I can't figure out how to restart it or get into it.  Can I force a reinstall?  Is there an operating interface or GUI that works well with Apache?  

I am running 8.04 as a Citadel Mail server at this time on a Dell 2900 server.

Thanks for the help

---

### Post by hictio on 2008-11-13
> 
Is there an operating interface or GUI that works well with Apache?


Try [Webmin](http://www.webmin.com/)

---

### Post by quikone8 on 2008-11-13
> **hictio said:**
> Try [Webmin](http://www.webmin.com/)

Thanks, I will give webmin a try, anyone have ideas on the other issues?

---

### Post by cariboo on 2008-11-13
If you want to install the lamp server, at the prompt type:

```
sudo tasksel
```

You should see a menu that looks like the attached screenshot.

If you have apache installed but not running, you can start it by typing at the prompt:

```
sudo /etc/init,d/apache2 start
```

If you don't get a notice that apache is already running, it should start. To find out, point your web browser to your server, you should see a page the says:

```
It Works!
```

Jim

---

### Post by quikone8 on 2008-11-14
> **cariboo907 said:**
> If you want to install the lamp server, at the prompt type:

```
sudo tasksel
```

You should see a menu that looks like the attached screenshot.

If you have apache installed but not running, you can start it by typing at the prompt:

```
sudo /etc/init,d/apache2 start
```

If you don't get a notice that apache is already running, it should start. To find out, point your web browser to your server, you should see a page the says:

```
It Works!
```

Jim

I have tried to run sudo tasksel about three times, each time I get the following error; aptitude failed (100)

Any ideas

---

### Post by CrucifiedEgo on 2008-11-14
After searching the forums a bit -- try running sudo aptitude update to update your package lists, and then run the tasksel again.

ref: [http://ubuntuforums.org/showthread.php?t=514551](http://ubuntuforums.org/showthread.php?t=514551)

---

### Post by quikone8 on 2008-11-14
> **CrucifiedEgo said:**
> After searching the forums a bit -- try running sudo aptitude update to update your package lists, and then run the tasksel again.

ref: [http://ubuntuforums.org/showthread.php?t=514551](http://ubuntuforums.org/showthread.php?t=514551)

Same error

---

### Post by quikone8 on 2008-11-14
> **quikone8 said:**
> Is it possible to install LAMP after the server is up and running?  I would like to set up a blog server.  If not, I have noticed that Apache is on my machine but it does not seem to be listening to any ports.  Plus I can't figure out how to restart it or get into it.  Can I force a reinstall?  Is there an operating interface or GUI that works well with Apache?  

I am running 8.04 as a Citadel Mail server at this time on a Dell 2900 server.

Thanks for the help

 Re: Add LAMP to Ubuntu Server the "right way"
The command to use is:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

this is exactly what the installer does, so it can't get easier than that.



Alan

BTW;  Thanks to everyone who helped solve this, I really did not want to rebuild the system.

---

