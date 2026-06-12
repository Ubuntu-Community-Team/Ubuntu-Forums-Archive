---
title: "Yet Another Apache2 Won't Start"
date: 2007-08-15
forum: Server Platforms
---

### Post by Peter108 on 2007-08-15
Well, I installed it, but that's about as far as I've gotten. Per below:
[LIST]
[*]apache2 is in /etc/init.d
[*][COLOR="Blue"]sudo apache2 start [/COLOR]returns "command not found"
[*]per the ps cmd, the process isn't running
[*]even though there's an entry for it in rc2.d
[*]the access and error logs are empty, timestamped with the install date
[/LIST]

So clearly I'm unclear on a major concept, but, as a noob, I'm dam*ed if I know what it is.  Ideas?


[FONT="Courier New"]
[COLOR="Blue"]peter@cosmo:/etc/init.d$ ls -al | more
total 372
<snip>
-rwxr-xr-x   1 root root 4351 2007-01-15 10:10 apache2
<snip>

peter@cosmo:/etc/init.d$ sudo apache2 start
sudo: apache2: command not found

peter@cosmo:/etc/init.d$ ps awx | grep apache
 6182 pts/0    S+     0:00 view apache2.conf
 6676 pts/1    R+     0:00 grep apache

peter@cosmo:/etc/init.d$ ls -al /etc/rc2.d/*apache*
lrwxrwxrwx 1 root root 17 2007-08-14 21:30 /etc/rc2.d/S50apache2 -> ../init.d/apache2

peter@cosmo:/etc/init.d$ ls -al /var/log/apache2
total 8
drwxr-xr-x  2 root root 4096 2007-08-02 14:01 .
drwxr-xr-x 12 root root 4096 2007-08-14 21:27 ..
-rw-r-----  1 root adm     0 2007-08-02 14:01 access.log
-rw-r-----  1 root adm     0 2007-08-02 14:01 error.log
peter@cosmo:/etc/init.d$ [/COLOR][/FONT]

Cluelessly,

---

### Post by HermanAB on 2007-08-15
Uhmmm... The Ubuntu initialization system is somewhat different from Redhat so, I don't know the details.  However, what is clear is that you are trying to use the wrong command to start Apache, which is why it says 'command not found'.

On a Redhat system the command is 'service httpd start', but gawd knows what the command is on Ubuntu.  However, you should be able to activate Apache using the Application, System, Services GUI-pointy-clicky-thingy.

Anyhow, I'm installing Apache2 now on Xubuntu on VMware with Synaptic to see how it is done, since you got me kinda intrigued now.  
If you can't get going, send me a private message later.

Cheers,

Herman

---

### Post by conjur3r on 2007-08-15
Start apache either one of two ways:

Using ubuntu's startup script
# sudo /etc/init.d/apache2 start

Using the apache tool
# sudo apache2ctl start

---

### Post by conjur3r on 2007-08-15
> **Peter108 said:**
> 
[FONT="Courier New"]
[COLOR="Blue"]peter@cosmo:/etc/init.d$ ls -al | more
total 372
<snip>
-rwxr-xr-x   1 root root 4351 2007-01-15 10:10 apache2
<snip>

peter@cosmo:/etc/init.d$ sudo apache2 start
sudo: apache2: command not found


This should be (note ./ in front of apache2 which tells it to execute the script located in the current folder)

peter@cosmo:/etc/init.d$ sudo **./**apache2 start

---

### Post by NewbieNik on 2007-08-15
conjur3r,

Not sure about the ./ thought was just to run bin or sh files. Apache2 is a service that once installed can be run, stopped or restarted by
sudo /etc/init.d/apache2 start (or stop or restart)
Might be wrong and apologies if I am, but that was my understanding.

---

### Post by az on 2007-08-15
What does 
dpkg -l|grep apache
show?

---

### Post by Peter108 on 2007-08-15
[FONT="Fixedsys"]
peter@cosmo:/etc/init.d$ dpkg -l | grep apache
ii  apache2-utils                    2.2.3-3.2build1                        utility programs for webservers
ii  apache2.2-common                 2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  libapache2-svn                   1.4.3dfsg1-1ubuntu1                    Subversion server modules for Apache


peter@cosmo:/etc/init.d$ ./apache2 start
No apache MPM package installed
peter@cosmo:/etc/init.d$ [/FONT]

So the ./ made a difference, and now I find that I seem to be missing the MPM package.  Searched in synaptic package manager using that string (and or a combo of apache and mpm), but came up empty.  So not sure what the MPM package is.

---

### Post by cobaltcopy on 2007-08-15
try

```

apt-get install apache2-mpm-common

```

---

### Post by Peter108 on 2007-08-15
Doesn't look good....

```
peter@cosmo:/usr/src/linux-headers-2.6.20-16-generic$ sudo apt-get install apache2-mpm-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]E: Couldn't find package apache2-mpm-common[/COLOR]
peter@cosmo:/usr/src/linux-headers-2.6.20-16-generic$ 
```

---

### Post by az on 2007-08-15
sudo apt-get install apache2

---

### Post by Peter108 on 2007-08-15
sudo apt-get install apache2

was the first thing I did way back when, but doing it again got me the missing MPM module.   Live and learn.

Now if I run apache2 start, it simply does nothing.  And if I run apache2ctl start, I get what you see below.  Indeed, no such file exists.  Is there a default httpd.conf file or skeleton out there I can start with?

```
peter@cosmo:~$ sudo /etc/init.d/apache2 start
peter@cosmo:~$ sudo apache2ctl start
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory
peter@cosmo:~$ 

```

All right, looks like I need to go do some homework before I can even get to step one w/ this baby (i.e., accessing [http://localhost's](http://localhost's) index.html).  Probably should have posted this in the noob forum.  Thanks!

---

### Post by cobaltcopy on 2007-08-15
I seem to be having the exact same problem as you...I completely removed all traces of apache2 and reinstalled, but there are still massive problems.

---

### Post by az on 2007-08-16
> **cobaltcopy said:**
> I seem to be having the exact same problem as you...I completely removed all traces of apache2 and reinstalled, but there are still massive problems.

Did you delete /etc/apache2 before reinstalling the packages?  Because if you did that, there is no reason there would be a configuration problem with apache2 after you reinstall.

Peter108, you clearly have problems with your apache2 configs.  They are not the out-of-the-box ones.

---

### Post by conjur3r on 2007-08-16
Installing and running apache shouldn't be as hard as this.  It should just simply be

# sudo apt-get install apache2
# sudo apache2ctl start

The package has everything it needs to start.  Sometimes it's good to start on a fresh clean slate so to remove it, go:

# apt-get purge apache2

Then reinstall.

---

### Post by conjur3r on 2007-08-16
> **NewbieNik said:**
> conjur3r,

Not sure about the ./ thought was just to run bin or sh files. Apache2 is a service that once installed can be run, stopped or restarted by
sudo /etc/init.d/apache2 start (or stop or restart)
Might be wrong and apologies if I am, but that was my understanding.

You can execute any file with the execute bit.  Whether or not it works is another matter.  The ./ specifies to execute the following script found in the current folder.

/etc/init.d/apache2 is a shell script.  It supports the start/stop/restart/reload/etc switches and interfaces with the apache binary(ies) accordingly.

---

### Post by Peter108 on 2007-08-16
I will do as you advise.  purge and reinstall.

---

### Post by Peter108 on 2007-08-16
Well, I'll purge and re-install as soon as I fix my network issues.  A [WHOLE 'nother story]("http://ubuntuforums.org/showthread.php?t=521458")

Also, if anyone has a favorite Apache noob site that helped them get off the ground, please share.  Thanks!

---

### Post by az on 2007-08-17
> **conjur3r said:**
> Installing and running apache shouldn't be as hard as this.  It should just simply be

# sudo apt-get install apache2
# sudo apache2ctl start

The package has everything it needs to start.  Sometimes it's good to start on a fresh clean slate so to remove it, go:

# apt-get purge apache2

Then reinstall.

Apache2 is started as part of the installation.  You don't need to start it by hand.

As well, to correct any configuration problems, you will need to get rid of the apache2 directory in /etc after you remove the package.  
sudo apt-get remove --purge
will only get rid of the debconf information (package management database).

And, there is no 
apt-get purge
command.

---

### Post by Peter108 on 2007-08-17
Thanks az for corrected syntax.   Also, re startup, that's what got me started here.  Even though /etc/rc2.d contains

```
lrwxrwxrwx   1 root root   17 2007-08-14 21:30 S50apache2 -> ../init.d/apache2

```

and /etc/init.d contains 

```
-rwxr-xr-x 1 root root 4351 2007-01-15 10:10 apache2

```

I could find no evidence that it was starting on bootup.  Then again I may have been grepping the wrong string.  I tried both
```

ps -eaf | grep apache*
```
and
```
ps -eaf | grep http*
```
What [COLOR="Red"]***is***[/COLOR] the correct way to confirm the apache processes are running?

---

### Post by Peter108 on 2007-08-17
Well, I've made a real mess here.  At first I tried to remove/purge.  But I botched the syntax and only removed.  I then thought, well, RE-install, then remove/purge.  I did both, THEN deleted /etc/apache2, THEN re-installed.

But the install, as shown below
a) doesn't start the process and
b) a tad worse, doesn't even create /etc/apache2

And now, even if I remove/purge, THEN mkdir /etc/apache2, THEN re-install, /etc/apache2 comes up empty.

Houston, we have a problem.

```
peter@cosmo:/etc$ [COLOR="Red"]sudo apt-get remove --purge apache2[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd apache2-mpm-worker
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101484 files and directories currently installed.)
Removing apache2 ...
peter@cosmo:/etc$ cd apache2
peter@cosmo:/etc/apache2$ cd ../
peter@cosmo:/etc$ apt-get install apache2
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
peter@cosmo:/etc$[COLOR="Red"] sudo apt-get install apache2[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/38.7kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 101482 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.3-3.2ubuntu0.1) ...
peter@cosmo:/etc$ cd apache2
peter@cosmo:/etc/apache2$ ls -al
total 8
drwxr-xr-x   2 root root 4096 2007-08-17 08:53 .
drwxr-xr-x 111 root root 4096 2007-08-17 08:53 ..
peter@cosmo:/etc/apache2$ 

```

---

### Post by AnRkey on 2007-08-19
Same problem here, no apache2 directory is created. I have the same problem with php5. Anyone have any idea's why this is?

---

### Post by Peter108 on 2007-08-19
AnRkey:
 
Odd, My e-mail notif (see below "code") of your message contains much more info than your post.  Neither one contains the attachment you mention.   Probably some forum intricacy I don't yet understand. ```
Here is the message that has just been posted:
***************
Same problem here as peter108. Apache dir had config files though, just no 
apache2.conf. I copied one from a working server that also was running feisty. I 
ran /etc/inid.d/apache2 start and got an error about a missing module and remove 
the module line from the apache2.conf file. The server I copied the file from 
must have had a module that my broken server did not have. Then I ran it and it 
worked. I have attached my apache2.conf file for you, hope that helps.

*_Question_*: Should the apache package on the repo not have recreated an 
apache2.conf?

AnRkey :cool:
```

---

### Post by Peter108 on 2007-08-19
Oh, it must have been a private message.  Just call me DUH.

---

### Post by AnRkey on 2007-08-19
> **Peter108 said:**
> AnRkey:
 
Odd, My e-mail notif (see below "code") of your message contains much more info than your post.  Neither one contains the attachment you mention.   Probably some forum intricacy I don't yet understand. ```
Here is the message that has just been posted:
***************
Same problem here as peter108. Apache dir had config files though, just no 
apache2.conf. I copied one from a working server that also was running feisty. I 
ran /etc/inid.d/apache2 start and got an error about a missing module and remove 
the module line from the apache2.conf file. The server I copied the file from 
must have had a module that my broken server did not have. Then I ran it and it 
worked. I have attached my apache2.conf file for you, hope that helps.

*_Question_*: Should the apache package on the repo not have recreated an 
apache2.conf?

AnRkey :cool:
```

I edited my post when i realised that apache2 was not fully working. It starts perfectly but does not work at all. Half the config files are missing. I don't know why the package does not recreate the files. My first thought is that I am not removing all of the packages and then deleting all the config files.

Any help here would be cool.

AnRkey

---

### Post by AnRkey on 2007-08-19
I tried the following...

sudo dpkg -P apache2
sudo dpkg -P php5

sudo apt-get install apache2
sudo apt-get install php5

Same propblem, some config files are there but now all.

typing apache2ctl returns /usr/sbin/apache2ctl: 102: /usr/sbin/apache2: not found

Any help would be cool.

AnRkey

---

### Post by AnRkey on 2007-08-21
OK I had a rough time with this but it's fixed now. Here is what I did to get my apache2 reinstalled with PHP.
```

sudo apt-get remove --purge apache2 apache2.2-common apache2-mpm-prefork
```

You can edit /var/lib/dpkg/info/apache2-mpm-prefork.prerm and comment out the call to invoke-rcd to look like this if the above remove and purge fails due to apache2 not stopping...

```
# /usr/sbin/invoke-rc.d apache2 stop
```
instead of this...
```
/usr/sbin/invoke-rc.d apache2 stop
```

Then I reinstalled apache2 like this

```
sudo apt-get install apache2
```

PHP was giving me problems so I removed it by purging it too like this

```
apt-get remove --purge php5 php5-common libapache2-mod-php5
```

and then i installed php5 from scratch with...

```
sudo apt-get install php5 libapache2-mod-php5 php5-mysql
```

Thanks goes to Infinity in #ubuntu-server on irc.freenode.org

---

### Post by doctorfilter on 2008-04-13
> **conjur3r said:**
> 
Using the apache tool
# sudo apache2ctl start

This did the trick in Ubuntu 7.10.
Much appreciated.
:)

---

