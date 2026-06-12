---
title: "Trouble with phpmyadmin"
date: 2006-03-02
forum: Server Platforms
---

### Post by raghus on 2006-03-02
How do I install phpmyadmin on a Ubuntu Server
The sudo apt-get install worked great for apache2, mysql and php5. php5 works great via apache2. I'd like to install phpmyadmin to start playing with the database but when I do a

sudo apt-get install phpmyadmin, I have an error "E: couldn't find package phpmyadmin". 

I looked in the /var/lib/dpkg/info directory and there is no phpmyadmin in there..

Where do I go from here?

---

### Post by jon_gunnar on 2006-03-02
[QUOTE=raghus]How do I install phpmyadmin on a Ubuntu Server
The sudo apt-get install worked great for apache2, mysql and php5. php5 works great via apache2. I'd like to install phpmyadmin to start playing with the database but when I do a

sudo apt-get install phpmyadmin, I have an error "E: couldn't find package phpmyadmin". 

I looked in the /var/lib/dpkg/info directory and there is no phpmyadmin in there..

Where do I go from here?[/QUOTE]

At least on my amd64 phpmyadmin  is in universe,you have enabled that?

jon@localhost:~$ apt-cache search phpmyadmin
phpmyadmin - set of PHP-scripts to administrate MySQL over the WWW

jon@localhost:~$ apt-cache show phpmyadmin
Package: phpmyadmin
Priority: extra
Section: universe/web

---

### Post by jmudanimal on 2006-03-02
edit "/etc/apt/sources.list" to look at the "universe" component.  Right now your apt-get is looking at your E: drive (probably a cd)

---

### Post by raghus on 2006-03-02
Thanks! Looks like editing that file worked - will post my results if all goes well   - or not

---

### Post by raghus on 2006-03-13
Whoever else comes back to look at this - yes! editing the file worked like a charm

---

### Post by ej159 on 2007-04-14
To conclude this is fixed by commenting in the universe source in the source list and doing an apt-get update.

---

### Post by foxholeunder on 2007-08-07
Thought I would chip in my two cents...

I also had troubles with not finding phpmyadmin while installing a LAMP server on my Sun Microsystems Ultra10 - running Ubuntu-6.06-server-sparc edition.

I then had troubles installing it on my old power-pc then the i386 version as well. 

The lesson I learned is that all versions of Ubuntu that are server appear to require enabling the universe repository in /etc/apt/sources.list 

I imagine that this has something to do with security as only the core Ubuntu repositories are enabled by default. Although I could not tell you if this is the actual reason.

All my previous en devours into running servers on Ubuntu have co-mingled with my desktop. It has only been recently that I have acquired extra hardware in which to run true dedicated servers.

---

### Post by marmott2334 on 2007-10-15
Hi all!

I tried installing phpmyadmin and followed all the steps you say in this post. I have edited the sources.list file as you say in this post, but I still get a message

E:unable to find package phpmyadmin

The sources.list file I have is

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Suggestions please??

---

### Post by don durito on 2007-10-19
> **marmott2334 said:**
> Hi all!

I tried installing phpmyadmin and followed all the steps you say in this post. I have edited the sources.list file as you say in this post, but I still get a message

E:unable to find package phpmyadmin

The sources.list file I have is

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**uncheck those sharpes**
[B]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
[/B]

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Suggestions please??

save and exit and you have the multiverse and universe repos enabled

---

### Post by kevmaster on 2007-10-20
I see you're using dapper. I think you could just replace your sources list with this text:

```
deb http://nl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
```

I always find it easer to read. Maybe change the *nl.* (Netherlands) mirror with your country.

And then don't forget to run a:
```
sudo aptitude update
```

phpmyadmin should now be in your list.

---

### Post by gbeepc on 2008-04-14
after i included the universe repositories i was still having problems.  however, when i rant the "sudo aptitude update", a lot more got updated than just my phpmyadmin packaget but it did the trick for me and permitted the full install of phpmyadmin.

---

### Post by Iulita on 2008-06-05
Having some problems as well with installing phpmyadmin. Once I try to install with

sudo apt-get install phpmyadmin      

I receive the following error:

Setting up phpmyadmin (4:2.10.3-1ubuntu0.2) ...
invoke-rc.d: unknown initscript, /etc/init.d/apache not found.

Currently using apache2, php5 and with mysql already installed.

Any ideas what goes wrong? thanks ^^

---

