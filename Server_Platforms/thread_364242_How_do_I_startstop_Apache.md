---
title: "How do I start/stop Apache?"
date: 2007-02-18
forum: Server Platforms
---

### Post by mjpatey on 2007-02-18
Hello, 

I'm very new to running a web server... never done it before.  I followed a very simple Apache tutorial, and with a little tweaking and help from a knowledgeable friend, got my server up and running.

My question is, how do I stop Apache from running?  And what do I do to restart it?  It seems that it's running by default everytime I boot into Ubuntu, and though I understand that would usually be the desired default behavior for someone running a webserver, it's not what I want.

I want my server to be up and running only occasionally, when I want to serve large files to business clients.  Aside from that, I don't want Apache running.

For some reason, simply typing "apache2" into a terminal causes the following error message:
> 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

I was kind of hoping that would start the server, but it seems it's always running.

Thanks for any help you may have!

-Mark

---

### Post by colyn on 2007-02-18
I'm fairly new to Ubuntu myself and just recently got my webserver up and running.

If I am correct to start apache go to a terminal and type sudo /etc/init.d/apache2 start and to stop sudo /etc/init.d/apache2 stop. You will be asked for your password.

---

### Post by istrebitjel on 2007-02-18
Try

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
or
sudo /etc/init.d/apache2 restart

---

### Post by mjpatey on 2007-02-18
Great!  Thank you, all... I just created launchers for those commands after verifying that they worked like a charm.

The "restart" option didn't seem to work for me (gave me an error about no existing "pid", whatever that is!), but the other two do exactly what I'd hoped.

Thanks again!

-Mark

---

### Post by istrebitjel on 2007-02-18
Mark, restart gave you that error, because apache wasn't yet running....
If it's currently running and you want a config change to take effect, you can use it, instead of first stopping and then starting.

---

### Post by balbir97 on 2007-02-27
> **istrebitjel said:**
> Try

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
or
sudo /etc/init.d/apache2 restart


Hi can u tell how can i check the status of a service..
as I used to do this in Red Hat for getting the status of a service

su -
/etc/init.d/apache status

---

### Post by undertakingyou on 2007-03-16
Another way is to use this```
sudo /usr/sbin/apache2ctl
``` and use it with start stop restart.

 I think force-start too, not sure about that.

---

### Post by pogush on 2008-04-28
Hey i got this msg:
```
sudo: /etc/init.d/apache2: command not found
```
why?
thx

**Update:** solved, i had files installed to another folder :P

---

