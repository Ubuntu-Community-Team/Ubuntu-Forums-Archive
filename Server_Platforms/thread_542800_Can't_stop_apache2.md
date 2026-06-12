---
title: "Can't stop apache2"
date: 2007-09-04
forum: Server Platforms
---

### Post by Andrey Ponomarev on 2007-09-04
I have apache2 that's started on boot.

Some days ago I've got a problem with shutdown my computer: apache don't want to stop!

I've tried to stop it manually in several ways:
```
sudo /usr/sbin/apache2 -k stop
sudo /usr/sbin/apache2 stop
sudo apache2ctl stop

```
**update:**
```
sudo /usr/sbin/apache2ctl -k graceful-stop
sudo /etc/init.d/apache2 stop

```
Every command is executed endlessly. The only way that helps is killing process

I've tried to reinstall apache2 but the problem remains.

Does anybody have any suggestions?

---

### Post by ticopelp on 2007-09-04
Have you tried 

```
/usr/sbin# ./apachectl -k graceful-stop
```

---

### Post by Andrey Ponomarev on 2007-09-04
I don't have apachectl, but I tried
```
cd /usr/sbin
./apache2ctl -k graceful-stop
```
It doesn't help

---

### Post by GigaVolt on 2007-09-04
killall apache2

---

### Post by Andrey Ponomarev on 2007-09-04
> **GigaVolt said:**
> killall apache2

Yes, this helps to kill all apache's processes. But if I forget to kill apache, then my computer freeze during shutdown. Actually it can't shutdown while apache is running

---

### Post by NewbieNik on 2007-09-04
wow, calm down guys....all you need

sudo /etc/init.d/apache2 stop

---

### Post by Andrey Ponomarev on 2007-09-04
> **NewbieNik said:**
> wow, calm down guys....all you need

sudo /etc/init.d/apache2 stop

I just forgot to mention this. It also doesn't work.

---

### Post by crazybeard on 2007-11-05
> **Andrey Ponomarev said:**
> I just forgot to mention this. It also doesn't work.

I am new to Ubuntu but not to linux.  I completed an install of Ubuntu 7.10 last week and was building a website locally for work only to find out that apache2 is a bit different then apache (earlier).

However, the problem this user is experiencing is real and a big one.

Trying to stop fails by telling you that apache isn't running.  Trying to start tells you that the port is not available.  This is explained by checking ps where one finds apache is already running.

Executing any apache2ctl command results in that command running continuously in the background.  If one isn't paying attention the machine starts to thrash.

killall apache does work, but this is a lousy way to stop a process.  

Since I am at work right now, I haven't the time to run around and find the solution.  Has anyone else found what to do about this? (I am thinking the apachectl2 script needs to be tweaked).

cbm

---

### Post by Railsbuntu on 2007-11-05
Hi,

I have the same type of problem. here is my thread: 

My problem is that maybe, another server (in my case it might be citadel) is using the same port as apache.

---

### Post by crazybeard on 2007-11-06
Well, I did discover my apache was trying to use 127.0.1.1 as the server name.  I have no idea how that got there since I installed using the ubuntu add/remove application.  I don't recall being asked for this info, but it seems it must be somewhere.  ifconfig shows everything set up correctly on that end.

So I added "ServerName 127.0.0.1" to my etc/apache2.conf file and everything worked fine.   I can't grasp how apache started in the first place with that info since it failed when I tried to start it by hand.

Frankly, I would have never noticed it except that I thought cgi's were configured wrong and went looking through the httpd.conf to see if it was set up correctly (httpd is, of course, empty now and everything is in apache2.conf - a change I wasn't aware of).   HTML access worked but cgi didn't.  Turned out I made a silly mistake in my perl script.  But all that to say that in the process of fooling with things, I tried to restart my apache server to reread the conf file and that is when the problem showed up.

If I think about it tonight I'll try to reproduce the problem.

Anyone know off hand where else apache would be finding the server name?

cbm

---

### Post by MJN on 2007-11-06
> **crazybeard said:**
> Well, I did discover my apache was trying to use 127.0.1.1 as the server name. I have no idea how that got there since I installed using the ubuntu add/remove application. I don't recall being asked for this info, but it seems it must be somewhere.
 
Have you got that address listed in /etc/hosts? In particular, if it's a mapping for your /etc/hostname then it likely chose it from here.
 
> So I added "ServerName 127.0.0.1" to my etc/apache2.conf file and everything worked fine.
 
This directive really ought to be going inside your /etc/sites-available/default file, particularly if you're going to be running multiple sites (even if not this file maintains the 'default' site options, even if it's the only one).
 
Mathew

---

