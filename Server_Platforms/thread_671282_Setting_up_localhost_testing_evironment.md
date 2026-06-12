---
title: "Setting up localhost testing evironment"
date: 2008-01-18
forum: Server Platforms
---

### Post by frotzed on 2008-01-18
I'm somewhat competent with Ubuntu in general but I need some help with this.  I do a lot of web design on the side so I need to set up a localhost environment where I can create websites locally which can then be uploaded to a public server.

I've been using XAMPP on Ubuntu Gutsy but someone just told me that this is not a good idea.  That the better alternative is to just install LAMP via the repositories and go from there. 

I have 2 questions:

1. To install XAMPP I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

How would I go about uninstalling XAMPP completely?  Is everything contained within /opt/LAMPP?  Do I just remove that dir?

2. Once I install LAMP via the ubuntu repositories, how do I get to the point where I put files in my /home/sites directory and they are available by going to [http://localhost?](http://localhost?)

I ask #2 because from following the tutorial I linked, I've made it so all my development sites are contained within the /home/sites directory.

Any help would be much appreciated.  I'd like to take whatever I can learn here and write up a tutorial and I plan on linking anyone who helps me out with this. (that's bribery ;)  )

---

### Post by Vinno on 2008-01-18
Answering your question 2: When you have apache2 installed, just edit the default file --> /etc/apache2/sites-enabled/default

First few lines, you need to edit document root.

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        **DocumentRoot /var/www/**
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>

```
to e.g DocumentRoot /home/sites/

Then restart apaceh2--> sudo /etc/init.d/apache2 restart

---

### Post by frotzed on 2008-01-18
And that will then deliver a secure development environment?

---

### Post by fearevilleet on 2008-01-18
The sites would be running off your local box and not going onto the internet. If you are worried about other people viewing your sites while your are developing them you can always protect your directory's with an htaccess file.

---

### Post by frotzed on 2008-01-18
Thank you :)

---

### Post by wheezer on 2008-01-18
> **frotzed said:**
> 
I'd been using XAMPP on Ubuntu Gutsy but someone just told me that this is not a good idea.  That the better alternative is to just install LAMP via the repositories and go from there. 
)

Ok, I just need a simple server for doing prototype pages.  I used to use XAMPP and it set up everything for me, and it worked fine,  But now I am in  a new Gutsy install and trying to get ANY Apache running. So forgive me linux-stupids, but my questions are:

1) Why is XAMPP not a good idea?  Is it ok for my needs, or should I just continue hacking this out. It configures many things for me, including phpmyadmin, right?

2) Assuming I should continue without XAMPP, I have installed apache2 via synaptic and tried to start it, but got these errors.  Can someone explain each to me? 

matte@fatcat:~$ /etc/init.d/apache2/start 

open: Permission denied
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 24692?) not running
install: cannot change owner and/or group of `/var/lock/apache2': Operation not permitted
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

PS
I did not configuration at all, assuming apache would run with defaults. I will replace my virtual hosts later, but right now, just want a simple setup.

---

### Post by Vinno on 2008-01-18
You got to run that apache2 restart command as root. --> sudo /etc/init.d/apache2 start

---

### Post by frotzed on 2008-01-22
OK, Vinno, another goofy question.  Since I'm up and running with this LAMP configuration should I be stopping Apache when I'm not actively using it?  Does it use resources if it's just sitting there?

---

### Post by FakeOutdoorsman on 2008-01-22
Make sure to take a look at the Ubuntu Wiki page on [Apache, MySQL, and PHP]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by frotzed on 2008-01-22
> **FakeOutdoorsman said:**
> Make sure to take a look at the Ubuntu Wiki page on [Apache, MySQL, and PHP]("https://help.ubuntu.com/community/ApacheMySQLPHP").

I read through that and couldn't find anything regarding CPU or RAM usage.  I'm only wondering if it would be in my best interest to stop the servers when I'm not actively using them.

---

### Post by Vinno on 2008-01-23
> **frotzed said:**
> I read through that and couldn't find anything regarding CPU or RAM usage.  I'm only wondering if it would be in my best interest to stop the servers when I'm not actively using them.

The cpu/ram usage of apache nodes isnt really much (well nothing really when its not handling request), it just stays asleep waiting for a request to be given. Not really worth starting and stopping, the hassle outweighs it.

---

### Post by frotzed on 2008-02-08
Thanks.

---

