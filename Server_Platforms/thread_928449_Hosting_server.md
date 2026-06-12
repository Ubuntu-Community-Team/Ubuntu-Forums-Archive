---
title: "Hosting server"
date: 2008-09-24
forum: Server Platforms
---

### Post by wattaman on 2008-09-24
Hello!
Please help me with this if you can:
I've recently rented a hosting server runnuing on Ubuntu (7, I think). I've tried to change the Webmin's username&pass and now I can't login to add my sites. The hosting company will charge me with 70$/hour, if I ask for their help - I can't afford that.
So what I want to do is:
1. Access my Ubuntu server remotelly, through my browser and not through the comand line (I'm a noob in SSH)
2. Upgrade Webmin to the latest version
3. Upgrade Ubuntu to the latest version
OR, at least, uninstall and reinstall Webmin somehow, maybe it will work the next time. Again, don't know about SSH too much. I've tried to upgrade it using with WinScp command prompt a 'sudo' command, but I got errors.

Anyway, I'm thinking that if I have remote access to server through a visual interface (like windows) I'll find out by myself, sooner or later, but don't know how or if is possible with Ubuntu.

Please help me with this. I can't pay you, probably, but I can advertise your sites on mine pages :) if I get it work.
Thank you!

---

### Post by volkswagner on 2008-09-24
If you are a not comfortable with the command line, get more experience with the server you have.  If it ain't broke don't fix it.

To reset the webmin password
[http://www.webmin.com/faq.html]("http://www.webmin.com/faq.html")

I am not a fan of the risk involved with upgrading a distro (especially if I don't have physical access to the box).  I would prefer a clean install.

If you can get your webmin password reset, upgrading webmin can be done within the webmin interface.

From within Webmin >webmin>webmin configuration>upgrade webmin
select "Latest version from www.webmin.com"
and click "upgrade webmin"

The folks here will help you get joy from the command line interface!
This noob is living proof.

---

### Post by wattaman on 2008-09-24
M8, this is gold. I've browsed the webmin site up and down and missed that everytime.
Thank you very much! I swear I'd kiss you if you were here. Maybe is better you arent, :)

So, other things: can I, somehow, access the server remotelly without the command line? A graphical interface maybe?
Cause I want to upgrade the Ubuntu, too, and also check the servers settings (as much as I understabd them) but through the command line I'm lost everytime.
Thaks again!

---

### Post by windependence on 2008-09-24
> **wattaman said:**
> M8, this is gold. I've browsed the webmin site up and down and missed that everytime.
Thank you very much! I swear I'd kiss you if you were here. Maybe is better you arent, :)

So, other things: can I, somehow, access the server remotelly without the command line? A graphical interface maybe?
Cause I want to upgrade the Ubuntu, too, and also check the servers settings (as much as I understabd them) but through the command line I'm lost everytime.
Thaks again!

This is a perfect example of why when you are running a server you should not rely on GUI tools. I am in no way picking on you in particular, but this kind of thing can be ridiculously simple from the CLI as can many other tasks. 

Don't be afraid! Most all configuration files done at the command line in a *nix operating system are just plain text, easily human readable files and you don't have to use VI to edit them either. I get the idea you are intimidated by the CLI. Please try to think about the CLI as your friend because it really can get you out of a jam.

We are all here to help if you want to learn a little CLI or whatever else. :)

-Tim

---

### Post by volkswagner on 2008-09-24
Webmin should suffice for the interface.  You can do a lot with it.

May I ask why you are intent on upgrading Ubuntu?

As I stated, folks here can most often walk you through the command line.  Along with most how-to's are written to install/configure via the command line.  To get any more of a graphical interface, you will probably need a desktop installed and VNC into the machine.  

You should know, most all configuration changes will be done by editing some config file (apache, mysql, postfix, proftp, etc).  It could be a waste installing a GUI, when you still need to edit config files anyway.

I prefer nano as my editor.  Since I am newbie, it is the easiest for me.  Using vi has powerful, yet very specific commands/procedures. 

Even within Webmin, you will be editing config files.  The difference is you are guided on how to get there.

What are your plans for the server?

---

### Post by wattaman on 2008-09-24
K.
I want to upgrade mainly because I can not set my server using Webmin to host my site. If there's another way to put my site on the again _fast_ I'd like to know it, please.
However, from my noob point of view I've discover that:
- my server came with no sendmail, postfix or qmail and that why I can't use the virtualmin to configure the site to work (need them);
- I can't install those 3 above; sendmail gives me an *Failed to install module from [ftp://ftp.sendmail.org/pub/sendmail/sendmail.8.14.0.tar.gz](ftp://ftp.sendmail.org/pub/sendmail/sendmail.8.14.0.tar.gz) : Module sendmail-8.14.0 is missing a module.info file*
- I can't install anything, including the update, using the command of WinScp cause it always bumps me the message "*Host has not answered for 15 seconds... Abort*"
- I can't even start Apache... *Failed to start apache*

Btw, I've found that I have the 6.06.1 version. The Webmin managed to upgrade by itself to the latest version. Except those, everything is in dark for me. In fact I was even thinking to temporarly host my domain on a free hosting server, at least one page to let the members know what happen to their site... if you can imagine that :) ..paying for dedicated server but using a free hosting service
So, thank for the help, any other information is more then welcome, but please, understand that I'm a noob and my primary objective right now is to put my site online - that's why I'm asking here for help. Some sort of idiots guide to...etc.
Btw, I was trying to use putty to update ubuntu (hopefully to get rid of that 15 seconds mesasge from WinScp), but as it starts, putty tries to log me in using my computer username. How can I change that?
Thx!


Later that day:
- Can't install qmail, too. The same error as sendmail: *Failed to install uploaded module : Module netqmail-1.06 is missing a module.info file*. Now I'm downloading postfix but I doubt it would do much more.
Yap... same module.info missing error. Have no ideea if this is missing from my Ubuntu or from the modules packages.

---

### Post by volkswagner on 2008-09-26
> Btw, I was trying to use putty to update ubuntu (hopefully to get rid of that 15 seconds mesasge from WinScp), but as it starts, putty tries to log me in using my computer username. How can I change that?

How else would you like to log in?
The easiest way to install stuff located in the repositories is via the command line.

What steps are you using to install?

What is you sources.list look like?

```
sudo nano /etc/apt/sources.list
```

Mine looks like this.  Notice where the # is missing.  This is called uncommented out, so these lines will be used.  Lines starting with # are ignored.

```
#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

To install postfix, it is as simple as this.

Get updates and install updates, these may take a while.
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Install postfix.
```
sudo apt-get install postfix

```

---

### Post by Francewhoa on 2009-06-29
I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing Virtualmin, Webmin & Usermin.

---

