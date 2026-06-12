---
title: "Lamp in desktop edition"
date: 2008-07-21
forum: Server Platforms
---

### Post by jnw222 on 2008-07-21
How do i get a lamp server in Ubuntu desktop edition

---

### Post by theonegod on 2008-07-21
You can just toto the terminal and install the LAMP packages via apt-get that you need. You can also install the server edition with LAMP selected and then install the GUI after the fact.

---

### Post by jnw222 on 2008-07-21
i have a working desktop version and i need a clear tutorial to get the lamp packages

---

### Post by cariboo on 2008-07-21
Open a terminal Applications-->Accessories-->Terminal and type:

```
tasksel
```

This will open a text based Menu see attached screenshot:

Use the arrow keys to select LAMP then use the tab key to go to OK, hit enter and wait for the packages to download and answer the questions the installation ask during setup.

Note: it may seem that nothing is happening while the packages are being downloaded, just wait for it.

Note 2: When you select LAMP ht the space bar

Jim

---

### Post by tinny on 2008-07-22
There are a few ways to do this... here are two.

1.
```

sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql

```

2.
```

sudo tasksel install lamp-server

```

---

### Post by John P on 2008-07-22
This is my first post, I am completely new to Ubuntu and cannot seem to get my head around it. I have been using Windows for 12 years and Ubuntu appealed to me after reading many articles extolling its virtues.

I am using an old(ish) PC, 1.35Ghz Athlon, 768 Mb RAM and a 120 Gb HDD. This appears to be more than enough, especially as my original intention was to run a server. I have tried 8.04 but there were so many red screens during installation I gave up and went to 7.10 (Gutsy Gibbon). I have the desktop version running, but after reading this thread and wanting a server with a GUI, I decided to try it.

I tried the suggestion by cariboo907 to no avail. All I get with this suggestion is :

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied
tasksel: debconf failed to run


Trying tinny's suggestion results in this:

sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libapache2-mod-auth-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-auth-mysql has no installation candidate


I have only the desktop version installed, nothing else. Do I need to do something/install something before trying to install the LAMP server on the PC?

I really would appreciate any help/advice to get me going.

Regards

John P

---

### Post by Stunts on 2008-07-22
installing with:

```
sudo tasksel
```

did the trick for me.

I'm also expermienting with this.

---

### Post by John P on 2008-07-22
Thanks, stunts!

It's nice to have a reply from someone who is experimenting too! LOL

Honestly, I reckon one needs a university degree to work some of the things out!

I am just crazy about computers, determined not to let them beat me. I usually spend around 12 - 16 hours a day on mine and trying out new things is challenging, but interesting.

John P

---

### Post by John P on 2008-07-22
Tried that, stunts.......

sudo tasksel
[sudo] password for john:
tasksel: aptitude failed (100)
john@arandar-desktop:~$ 


Hmmmmmm..............

---

### Post by tinny on 2008-07-22
> **John P said:**
> Tried that, stunts.......

sudo tasksel
[sudo] password for john:
tasksel: aptitude failed (100)
john@arandar-desktop:~$ 


Hmmmmmm..............

Before doing anything update or install related on Ubuntu I do the following.
```

sudo apt-get clean
sudo apt-get update

```

Try running tasksel like this...

```

sudo apt-get clean
sudo apt-get update
sudo tasksel install lamp-server

```

> 
Trying tinny's suggestion results in this:

sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql
[sudo] password for john:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libapache2-mod-auth-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache2-mod-auth-mysql has no installation candidate

Opps...
These are some **old** instructions that ive used in the past...

Have a look at this. Looks like a nice intro type tutorial for seting up a LAMP server on Hardy (8.0.4)
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Simple_LAMP_server_Setup](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Simple_LAMP_server_Setup)

Here's the summary of the article

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install apache2 php5 mysql-server-5.0 phpmyadmin

```

---

### Post by John P on 2008-07-23
Thanks tinny,

I believe I have followed your advice to the letter and I got the first two to work, but the install commands brought back this:

john@arandar-desktop:~$ sudo apt-get install apache2 php5 mysql-server-5.0 phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  apache2: Depends: apache2-mpm-worker (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.4-3ubuntu0.1) but it is not going to be installed
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.45-1ubuntu3.3) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
  phpmyadmin: Depends: php5-mcrypt but it is not installable or
                       php4-mcrypt but it is not installable
E: Broken packages
john@arandar-desktop:~$

Any help will be greatly appreciated.

John

---

### Post by neilevan814 on 2008-07-23
I used this tutorial

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Neil

I could send you more tutorial links if this helps
Also if you follow from one of the other members' responses, I had problems with the taskel method so i just installed the individual packages as it is listed to do in the Dapper Drake install section

---

### Post by tinny on 2008-07-23
> **John P said:**
> Thanks tinny,

I believe I have followed your advice to the letter and I got the first two to work, but the install commands brought back this:

john@arandar-desktop:~$ sudo apt-get install apache2 php5 mysql-server-5.0 phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  apache2: Depends: apache2-mpm-worker (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.4-3ubuntu0.1) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.4-3ubuntu0.1) but it is not going to be installed
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.45-1ubuntu3.3) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
  phpmyadmin: Depends: php5-mcrypt but it is not installable or
                       php4-mcrypt but it is not installable
E: Broken packages
john@arandar-desktop:~$

Any help will be greatly appreciated.

John
This works on my machine (Ubuntu Hardy Desktop)

Do you have the "restricted", "universe" and "multiverse" repositories setup?

Here is my /etc/apt/sources.list file (contains my setup repositories). You could try using my config. Or setup these repositories from System > Administration > Software Sources. Then try the install again...
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

---

### Post by John P on 2008-07-23
Tinny,

I have the "restricted", "universe" and "multiverse" repositories setup, and I also included the Canonical (sp)? one.

I then installed the LAMP server and it seemed to work, it took a fair time to do whatever it was doing, but the dialogue box hung at 100%. I left it quite some time then decided to close it.

The only sources.list I could find was sources.list.save and it has this inside it:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe

In my etc folder I now have folders for 'apache2', 'mysql', 'php5' and 'webmin'. Does this mean they have installed (I downloaded webmin 1.420 and installed from the downloaded file), and if webmin is installed, do I need to configure it in any way.

Please excuse me if you or someone has pointed me in the direction for this, but I have a neurological disorder and one of its symptoms is I have trouble even remembering what I did five minutes ago!](*,)

John P

---

### Post by John P on 2008-07-23
I must have done something right! I now have Webmin working which has opened up a whole array of things I need to learn about! Much of it is totally beyond my comprehension, but the Internet is full of solutions for such needs if one knows where to look.

I have decided that running a server to host websites is a truly professional matter, and as such I am going to endeavour to learn the professional way. By that I mean I am going to set up another computer (2.2 GHz Dual Core AMD, 2 Gb Memory and 250 Gb HDD) and try my utmost to have it running sweetly without a GUI!

I've nothing better to do and I am going to allow myself 12 months to learn the management of a server.

One thing I would like to ask is, what would be the best eBook to get a hold of that would take me through it from start to finish?

Recommendations greatly appreciated!

Regards

John P

---

### Post by tinny on 2008-07-23
> **John P said:**
> I must have done something right! I now have Webmin working which has opened up a whole array of things I need to learn about! Much of it is totally beyond my comprehension, but the Internet is full of solutions for such needs if one knows where to look.

I have decided that running a server to host websites is a truly professional matter, and as such I am going to endeavour to learn the professional way. By that I mean I am going to set up another computer (2.2 GHz Dual Core AMD, 2 Gb Memory and 250 Gb HDD) and try my utmost to have it running sweetly without a GUI!

I've nothing better to do and I am going to allow myself 12 months to learn the management of a server.

One thing I would like to ask is, what would be the best eBook to get a hold of that would take me through it from start to finish?

Recommendations greatly appreciated!

Regards

John P

Good on you!

Just a quick tip...

Having a server installation for learning on doesn't require you to have alot of resources at all, or even a dedicated machine.

Have a look at setting up VMware Server on your desktop machine.

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

This will allow you to have a server installation running in Virtualization (On your desktop). This will also allow you to backup the virtual images very easily so that you have something to go back too should everything go bad (as it frequently does when learning something) 

BTW: The sources.list file is in your /etc/apt/ folder

---

### Post by John P on 2008-07-23
> Have a look at setting up VMware Server on your desktop machine.

Now then, Tinny, you are trying to make my decision making even MORE difficult! LOL

I have enough computers to have a dedicated one and I would prefer it, if I ever get it set up correctly, to just sit in a corner and tick over without any 'interference' from me! I run a weather website from here and that is on a dedicated machine and that is how I would rather it be.

Strangely enough, I could not load Ubuntu 8 (Hardy Heron?) onto the smaller machine, but it seems to be loading nicely on the one I mentoned in my previous post as I write this reply.

I shall try and find a good 'book' to take me through from start to finish and just take my time. Having said that, I have learned a LOT today and thanks go to you and the others who have taken the time to reply to my posts.

Best wishes

John P

---

### Post by tinny on 2008-07-23
> **John P said:**
> Now then, Tinny, you are trying to make my decision making even MORE difficult! LOL

I have enough computers to have a dedicated one and I would prefer it, if I ever get it set up correctly, to just sit in a corner and tick over without any 'interference' from me! I run a weather website from here and that is on a dedicated machine and that is how I would rather it be.

Strangely enough, I could not load Ubuntu 8 (Hardy Heron?) onto the smaller machine, but it seems to be loading nicely on the one I mentoned in my previous post as I write this reply.

I shall try and find a good 'book' to take me through from start to finish and just take my time. Having said that, I have learned a LOT today and thanks go to you and the others who have taken the time to reply to my posts.

Best wishes

John P

Yeah there is sooooooooooo much to learn with computers. :)

You should start a new thread "cant install Ubuntu Server 8.0.4".

The minimum system requirments for Ubuntu Server are:

128 RAM
~1GB HD

Have you seen the Ubuntu Server documentation?
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Stunts on 2008-07-24
Hi John P!

Sorry that what worked for me didn't work for you...
But hey, at least you are learning something!
The fact that it went smooth for me means that I didn't learn all that much.
But it's great to see that you will keep insisting on it!
Best of luck to you!!!

---

### Post by John P on 2008-07-24
Hi Stunts,

I am determined to make it all work for me, but maybe my determination should be read as 'stubborn'! LOL

I have all the time in the world and Tinny has pointed me towards a guide to server configuration, so with patience I shall do it!

As for me learning, to learn one needs to remember............... that's where my problems start! LOL

Best wishes and good luck with all you aspire to!

John P

---

### Post by jnw222 on 2008-07-25
thanks

---

### Post by BinaryDigit on 2008-07-25
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)   is a great resource to install a lamp server!! Thanks!!!  I normally had so much trouble in other versions of linux to set up a webserver :(

---

### Post by sidrit on 2008-08-10
Here it is done on Hardy.

[http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/]("http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/")

Hope it helps.

---

### Post by Trevor_Miles on 2008-08-14
I'm a newbie to and am running into a different buy similar problem:

trevor@BigOne:~$ sudo apt-get clean
sudo: unable to resolve host BigOne
[sudo] password for trevor: 

BigOne is the name of the machine on which I am running Ubuntu

Any help would be greatly appreciated.

---

### Post by Stunts on 2008-08-14
Trevor, try to post your issue in a new thread in absolute beginner's talk.
You'll get an answer there faster then here.
And by people far more experienced then me.

---

### Post by windependence on 2008-08-14
What is the output of :

```
hostname -f
```

-Tim

---

