---
title: "How to use old computer as web server?"
date: 2006-06-20
forum: Server Platforms
---

### Post by Axever on 2006-06-20
So I have a Dell Dimension XPS T650r computer with no important files currently running Ubuntu 6.06, Dapper Drake Desktop.


It Has:

12.74 Gigs of HD
Around 1/4 a Gig of Ram
A working ADSL Connection and Network Card
One DVD Drive

What would be the best way to convert this computer into a Dedicated Web server for a website? I Have read a few guides and looked around the forums but all documentation i could find was way above my head... I am not very experienced with computers but i can follow directions and will learn quickly. Is there a guide somewhere geared more towards beginners? or can someone walk me through it?

Thanks!

---

### Post by kthakore on 2006-06-20
Well first get the ubuntu server ISO cds from [http://www.ubuntu.com/download]("http://www.ubuntu.com/download"). I haven't actually installed this cd ( hoping some one else can fill this in for me). But once thtat is done, I would sugest looking into LAMP. I believe you can use apt to install it by typing this in to the terminal 

```
sudo apt-get install ubuntu-lamp
```

once this is done you might want to set up a FTP server to put files in you web folder located at 

```
/var/www
```

finally I suggest you install samba and connect your web server to your production computer, but this is only optional. 

All this info can be found at [http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

(p.s. it won't talk about LAMP, but you can look at the Apache HTTP server, MySQL, FTP server, Mail server, DCHP, and Samba or reference on how  to customize)


once you have finished this make sure you contact me here and i will show you how to harden the serve (aka make it more secure)

---

### Post by Axever on 2006-06-20
Thanks for the reply, but I am really new to linux and servers in general, so your going to have to be alot more specific. Once i have the Lamp Server installed via using the server edition disc and selecting Lamp Server Install, what exactly do i do? how do i set up a ftp server? How do I run it, How do I add Web Pages/ Files?!? 

Sorry for being so hopeless, but I would really like to learn my way around Linux and get this server up and running, but none of the guides i can find on the internet are aimed towards 'Noobs', and instead expect the reader to have a moderate level of knowledge in this area.

*sigh

---

### Post by mrcowcow on 2006-06-20
I would reccomend setting up a ftp server by doing *sudo apt-get install vsftpd* and configuring it using the guide [here](http://www.netadmintools.com/art355.html). This will set up a ftp server that allows you access to every file on the server. From there you can use a ftp client to get to /var/www, where the website files are stored. Upload files to here, and you will be able to access them by typing the servers ip address in the address bar of a web brower.

---

### Post by IYY on 2006-06-21
Just make sure that your ISP allows this. Many ISPs (mine included) don't allow their clients to run HTTP servers.

---

### Post by kthakore on 2006-06-21
oh i am really sorry! My mistake. But the guide provided above is good. Also check out the link I gave you [http://easylinux.info/](http://easylinux.info/) Ubuntu_dapper

---

### Post by houstonbofh on 2006-06-21
The server side can be a bit complex.  Using the server cd and choosing the LAMP option is probably best.  However, you will then be sitting at a CLI with no hint of what to do next.  Considering your system memory, I would then "apt-get install xbuntu-desktop."  This will give you a much more familiar setting.  You can now install ssh-server and an FTP server of your choice.  It is also a much easier way for the new Unix user to "wonder around" and find stuff.  At this point you will have a highly configurable Apache server with a mysql database back end, and php and perl on the backend.

---

### Post by Axever on 2006-06-22
OKay thanks Houstonbofh. But after i have installed the LAMP Server via the CD, and used 'sudo apt-get install xbuntu-desktop', and type in my password, i get an error like "E: Couldn't find Package xbuntu-desktop"

Should i just try 'apt-get install ubuntu-desktop' ??

---

### Post by herald on 2006-06-23
As the Operator in Houston alluded, working from a command line is tough, but either way, you're going to have to do at least some of it.  Unfortunately, there was a typo in there and the package you're looking for is xubuntu-desktop.

Regardless, the first thing many howto's will have you do is open a terminal window, so you're right back to the command line.  As you claim you are very new, I'd attack things in this order:

First, make sure the apache2 package is installed.  You'll need to look for howtos on installing an Apache2 server.  Apache is vastly different than Apache2 and ubunto only ships with Apache2 so make sure you know the difference.  You'll basically be editing a file in /etc/apache2/sites-available/default.  You'll need to learn how to use VirtualHosts to work with this file.  The default path where all your content goes (leaving the default is fine here) is /var/www/
Manually create an index.html file once you think the server is running and point your web browser to [http://localhost](http://localhost) to test.  Once you can see your content, start attacking the FTP server.
As was mentioned, use vsftpd.  It's very good for beginners because most of the common gaping security holes in FTP are taken care of in vsftp already.  Get it working so that you can FTP to your box and upload files.  Then, you'll need to learn a lot about Linux File Systems and Security.  Stuff like groups, chmod and chown.  Once you've gotten that far, you'll be well on your way and can start learning how to program PHP and working with databases such as MySQL.  In case you were wondering LAMP stands for:

Linux (the operating system)
Apache (the web server)
MySQL (the database server)
PHP/PERL (the dynamic web programming language)

See how the first letter spell LAMP?  Neat!  I must say starting from a Linux newbie to building an entirely functional LAMP server is not a quick nor easy task, so don't expect to have it running in 2 days.  PHP alone took me 6 months to learn, and then there's the Database part of it on top of that!  But, don't get frustrated, ask lots of questions, and have FUN!  Good luck.

---

