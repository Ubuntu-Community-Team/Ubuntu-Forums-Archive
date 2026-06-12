---
title: "Just to get the general idea.."
date: 2010-01-03
forum: Server Platforms
---

### Post by Tuliku on 2010-01-03
Hi, here some questions just to get the idea of how Ubuntu server works.
I'm about to install ubuntu server 9.10 on a very old pentium 4 desktop, with 2 gb ram, 80 gb disk.
According to what i was reading i the last weeks, it should be more then enough for a light home server.
I will put there some files as storage, host 2 or 3 domains, and have there a few small mysql db instances.
Maybe even roundcube mail or something like that.
Again, nothing serious, it is just to test and play, it does not need to be 24/7 up and running.

The idea is to make the following partitions:
1gb = /boot
22 gb = /
55 gb = /home
2 gb = swap

To get an idea of how it works, here some questions:
1. Would the above mentioned partitions be a good layout ? Any suggestions / recommendations ?
2. If i create 3 additional (test) users, and i want to restrict each user to 10 gb diskspace each, how is that set up ? Or only noticeable through monitoring how much they use ?
3. If i create for each user one db instance, where is this instance saved ? In their home folder ? /home/user1 ? Or somewhere else ?

My other questions have been answered already with the help of google and this forum, just for the above i could not find some info that made sense to me.

Thanks in advance, i might come back with some more.
Tuliku

---

### Post by HermanAB on 2010-01-03
1. That'll work.
2. Read up on quotas.
3. /var/somewhere

---

### Post by BkkBonanza on 2010-01-03
I wouldn't waste 1 GB on /boot. 100 MB is fine generally, though you could add a bit more if you like. Not much will ever get put in there: some config files and kernel images is mostly all.

I haven't used disk quotas, and if you're the only person using the system then it's not really needed, but if you want some info on setting it up, here is a link,

[http://linux.aldeby.org/disk-quota-management.html](http://linux.aldeby.org/disk-quota-management.html)

As far as I know (in mysql) the databases are created in one location (by default /var/lib/mysql/data) but you add users (in mysql) to control usage rights and access. There may be another way to set it up so data is stored in /home for each user but I haven't run into it.

edit: It occurred to me that if you wanted to keep db data in users home space so it is tied into disk quotas then you could use symlinks to achieve that. You would need a simple db creation script so that when a new db is added it first adds a symlink for the db name to the /home/username/data directory and then has mysql add the db. The script would look something like,

#!/bin/bash
# $1 is username, $2 is <dbname>
mkdir /home/$1/data/$2
ln -s /var/lib/mysql/data/$2 /home/$1/data/$2
mysql -u admin -p xxx "create database $2;grant privilages ... "

Of course, you would have to tailor the mysql command to your exact needs  but this is the rough idea and it would be called form your control panel.

---

### Post by Tuliku on 2010-01-04
Thanks very much, the info looks very helpful.
I will be able tomorrow to try this stuff out.

My pentium 4, 2.8 ghz, 2gb ram, seem to have some hardware error, exactly after 10 minutes it always shuts down.
I tried also with WinXp, and even Win98, but no go.

So i pulled out another old pentium 4, 1.6 Ghz, 1.2 gb ram, but it refused to install from USB flash disk. When installed from CD it was installing fine...almost.
Every time it stopped with the installation, or half way, or just before the end... it just hanged... Disk maybe to be (80gb) ?
In the other p4 the same disk worked fine.

Even swapped the processor from the first one to the second one, but the second one did not coop with that.

I mentioned this to a colleague of mine, and he offered his old pc, which he will bring tomorrow.
So.. tomorrow i can continue again :-)

---

### Post by fancypiper on 2010-01-04
Also, I wouldn't recommend over 15 GB for /.  I have found a range of 5-15 GB works well, depending on software.  If you want to run apache, perhaps you should consider a separate /var (or /var/www) partition for your web site.

With separate /home and /var partitions, you wont lose your data with new installs or distro hopping.

---

### Post by Tuliku on 2010-01-08
Thanks thanks,

So, i got from my colleague his very first pc (in total he has 7 now..) 
It's a Athlon XP 1800+ (thoroughbred core), 200 GB disk, 1 GB ram.
Completely cleaned the whole thing, removed huge layers of dust :-) and added 1 GB ram, added my own 80 GB disk, added 2 ventilators, inserted on every ventilation hole some special cloth for keeping dusk from going in.

Installed Ubuntu 9.10 32bit server, all went well.
Partitions look like:
/boot - 500 mb - primary
/ - 20 gb - logical
/home - 20 gb - logical
/var - 20 gb - logical
* remaining unused disk spaces
SWAP - 4 gb

The 80 GB disk is still untouched, i guess i will use if for making backups etc.

Downloading now many tutorials and articles on howto do stuff, and tonight and in the weekend i'll be playing around with this server :-)

Thanks for the input, screenshots i can attach of the hardware if someone is interested :-)

---

### Post by Tuliku on 2010-01-09
Ok, I'm slowly progressing, and it is quite fun i might say, but some more help is needed..

I've installed Webmin and the Gnome Desktop Manager according to this article:
[http://www.ubuntugeek.com/3171.html]("http://www.ubuntugeek.com/3171.html")

I chose this line, the stripped version
```
sudo aptitude install --no-install-recommends ubuntu-desktop
```

The below is what i see when i log in and try to start "gdm":

```
  System information as of Sat Jan  9 04:21:52 CST 2010

  System load:    0.26              Swap usage:  0%     Users logged in: 0
  Usage of /home: 1.0% of 18.34GB   Temperature: 34 C
  Memory usage:   4%                Processes:   100

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Jan  8 19:52:40 2010 from 192.168.1.3
**dwb@server:~$ gdm**

** (gdm-binary:1734): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.24" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:1734): WARNING **: Could not acquire name; bailing out
**dwb@server:~$ sudo gdm**

** (gdm-binary:1736): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:1736): WARNING **: Could not acquire name; bailing out
**dwb@server:~$**
```

I've google those error messages but no luck at all.
Does anyone know what is needed to make the desktop environment work ?

[COLOR="Gray"](Yes, i should use command line, but VI is still a big mystery although i use it. Therefore i thought of installing this stripped desktop enviroment so it allows me to use gedit etc.)[/COLOR]

---

### Post by BkkBonanza on 2010-01-09
Probably that messge indicates a dependency missing because of the shortcut --no-install-recommends.

You could try "aptitude show gdm" which will list dependencies and maybe figure out what other package needs to be there. Or maybe just install gdm will fix up whats missing.

Edit: another thing I just ran across suggests starting gdm like this,

sudo /etc/init.d/gdm start

---

### Post by Tuliku on 2010-01-09
Thanks, but no success.

Trying to install the whole ubuntu desktop:```

dwb@server:~$ sudo apt-get install ubuntu-desktop
[sudo] password for dwb:
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Trying to install only gdm:
```
dwb@server:~$ sudo apt-get install gdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Using this command: "sudo /etc/init.d/gdm start"
```
dwb@server:~$ sudo /etc/init.d/gdm start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start gdm

```
Following up on the advice in the error message:
```
dwb@server:~$ start gdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.20" (uid=1000 pid=1696 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
dwb@server:~$
```

Any other idea's ?
Btw, i installed also "gedit" and "gparted", and when i try to start them i get the same error:
```
dwb@server:~$ gparted

(gpartedbin:1829): Gtk-WARNING **: cannot open display:
dwb@server:~$ gedit

(gedit:1830): Gtk-WARNING **: cannot open display:
dwb@server:~$
```

---

### Post by BkkBonanza on 2010-01-09
Are you at the console on the server or logged in via ssh?

---

### Post by Tuliku on 2010-01-09
SSH....
Don't tell me i cant run it from my pc through SSH... :-)

---

### Post by BkkBonanza on 2010-01-09
Ya, you can but you have to run X forwarding on ssh.
Instead of just ssh to your server you have to use -X option (and any other options you need).

ssh -X user@server gdm

This runs the X server which gdm needs to run on top of.

---

### Post by Tuliku on 2010-01-09
Still noluck :(:(
```
dwb@dwb:~$ ssh -X dwb@192.168.1.1 gdm
dwb@192.168.1.1's password: 

** (gdm-binary:2264): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.30" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2264): WARNING **: Could not acquire name; bailing out
dwb@dwb:~$
```

What is this configuration file which is mentioned in the error message ?
Do i need to add my user account to some higher group, although i have full sudo access ?

--- Edit ---
Damn, looks like a bug:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/398253](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/398253)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/482841](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/482841)

Shall i give up on Gnome, and try another gui ?
Any that you can recommend ?

---

### Post by BkkBonanza on 2010-01-09
I'm not sure why that is. The only thing I can see different from the server guide for doing this is that they describe using "sudo apt-get install ubuntu-desktop".

See here,
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

I'm sorry, I have no idea if that matters or why. I have heard that aptitude and apt-get can be out of sync causing dependency problems - maybe something like that is happening?

---

### Post by Tuliku on 2010-01-10
I'll leave the gui part for what it is now.
Continued with the setting up as a webserver, and success :-)
In the end it wasn't that difficult, once i managed to add my user account to have access to /var/www
And my VI skills are up to the level where i can without issue's open and edit a file and close it again :-0

Further i will play more with all the possibilities, as the search button here gives lot's of interesting idea's and "howto's".

---

