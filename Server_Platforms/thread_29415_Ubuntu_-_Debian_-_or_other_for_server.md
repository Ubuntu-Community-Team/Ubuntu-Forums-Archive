---
title: "Ubuntu - Debian - or other for server"
date: 2005-04-24
forum: Server Platforms
---

### Post by sbaker33 on 2005-04-24
I am longtime Windows admin trying to learn Linux.  I have been playing with the desktop for a few months now and I am now wanting to learn more about the server side of things.  Ubuntu is, for me, the best desktop distribution I have found so I have installed Ubuntu using the "server" option in setup and I am trying to work through a samba tutorial.  I would then like to do the same with Apache, etc.

Here is the problem: a number of the steps and commands used in the tutorial do not appear to be available in Ubuntu such as chkconfig and lpadmin.  Is this because the tutorial is out of date?  Is this because Debian doesn't included such tools?  Or is this something Ubuntu specific?

What is the best distribution for learning Linux server administration?  Not necessarily the easiest but the most "standard" so knowledge will transfer regardless of distro.  Which distribution is most "complete" and ready for deployment within small/medium environments.

Thanks

---

### Post by tomchuk on 2005-04-24
Looks like you're using a Red Hat specific tutorial. chkconfig is a RH tool to add the necessary symlinks in /etc/rc?.d/ for services to be started and stooped at boot, shutdown, or runlevel change. You can install the curses tool "rcconf" to enable and disable services with control scripts in /etc/init.d/

There should be plenty of Debian/Ubuntu specific guides detailing what you want to do. For instance the [Ubuntu WiKi](http://www.ubuntulinux.org) has a [page](http://www.ubuntulinux.org/wiki/SettingUpSamba) on Samba setup.

As far as a "standard" distro - Red Hat is pretty standard for hosting, but in my experience not as good as Debian-based distros for the flexibility to do whatever you want to do. There are some great guides on the Gentoo site for a number of things. Most of the general principles and specific information regarding configuration files should transfer to Ubuntu fine. The important thing is to understand what you're doing, not just copy commands, I find the Gentoo docs much better than those scattered around the Internet for explaing things, not just listing commands. Ubuntu does a few things to make it a smoother desktop distro that might throw you for a loop when trying to configure things like CUPS for example. I'd go with stock Debian for a box that you're doing a minimial install on, then adding one or two services.

Also Don't forget man! Once you have a general understanding of what you need to do and what information you need to do it, 99% of the time man will answer your question faster than google.

---

### Post by sbaker33 on 2005-04-24
The guide I am using is off the samba web site and is the HOWTO posted there.  It doesn't mention a specific distribution but I like it a lot because it gives specific scenarios and then walks through how to implement samba to solve the issues, much better than a simple series of commands or configuration options.

Another problem I run into with "googling" for an answer to problems is that in many cases the instructions are a number of years old and **very** out of date even searching on the Debian web site can result in a lot of false directions...

Part of the issue is that I am trying to do everything from the command line.  I could breeze through a lot of this with GNOME or KDE installed.  But then I don't learn the UI and not the underlying files etc. that are actually being modified.  

Do most Linux admins install a GUI like GNOME?  Seems to me that leaving out the GUI would improve performance.

---

### Post by az on 2005-04-24
"Here is the problem: a number of the steps and commands used in the tutorial do not appear to be available in Ubuntu such as chkconfig and lpadmin. Is this because the tutorial is out of date?"

Most of the documentation you will find about apache will be for apache 1.3  Ubuntu uses apache2 which is the next generation.  It works quite well, but it has a lot of differences.  It is easier to use, but a lot of the apache1.3 tricks you will find on the web will not apply.  You should install the documentaion packages that go along with what you want like apache-doc or samba-doc.

dpkg -L samba-doc
(this will list the files in the installed package so you know where to go to read them.)



"Is this because Debian doesn't included such tools? Or is this something Ubuntu specific?"

Debian does not include many server tools.  Well, not as much as other distributions.  That does not mean that it is automatically more difficult to use.  The command-line can be extremely friendly and often, a more straightforward way of getting things done.  Debian is the distribution of choice for many server system administrators.  Your milage may vary.


"What is the best distribution for learning Linux server administration?"

Debian or slackware.  FedoraCore?  They are all well documented.  It depends.


"Not necessarily the easiest but the most "standard" so knowledge will transfer regardless of distro. Which distribution is most "complete" and ready for deployment within small/medium environments."

Hmmm.  Not an easy question to answer when one of the big benefit of open-source software is that you have a wide choice of ways of getting things done.  If you stick to the basic tools, you will do fine.  If you learn how to configure apache by using a third-party application, you will be lost without it.

A good rule of thumb is that if you stick to non-proprietary tools, you will alwya be able to get them working on your system.  Even if they do not have prebuild packages in the distribution, you would be able to compile them youself, if you need to.

Hope that helps.

---

### Post by tomchuk on 2005-04-24
[QUOTE=sbaker33]The guide I am using is off the samba web site and is the HOWTO posted there.  It doesn't mention a specific distribution but I like it a lot because it gives specific scenarios and then walks through how to implement samba to solve the issues, much better than a simple series of commands or configuration options.[/QUOTE]

Looks like a great guide, it also doesn't look too distro specific. I'd just roll with it, you'll have to do a little more reading regarding configuring CUPS and adding services to runlevels (although dpkg does this for you, you shouldn't have to do anything).

> Another problem I run into with "googling" for an answer to problems is that in many cases the instructions are a number of years old and **very** out of date even searching on the Debian web site can result in a lot of false directions...

One thing people don't like about Debian is how little it evolves, it's ancient init system, stubborn placement of config files, etc. However, it does mean that 6 year old literature isn't likely to differ to much from your brand new Hoary box as far as config file locations. You've probably hit upon some differences between apache-1-3 and apache-2 and samba-2 and samba-3 which are quite different.

> Part of the issue is that I am trying to do everything from the command line.  I could breeze through a lot of this with GNOME or KDE installed.  But then I don't learn the UI and not the underlying files etc. that are actually being modified.

Smart move, if you can do everything with just an editor (vi is on every major unix system) you have some seriously portable skills. Relying on Red Hat wizards will get you nowhere as far as learning what you are doing.

> Do most Linux admins install a GUI like GNOME?  Seems to me that leaving out the GUI would improve performance.

Performance and security. X on a server is usually though of in the same vein as logging in as root. Same with having a compiler installed.

---

### Post by venzen on 2005-04-25
My recommendation is to use Ubuntu in server mode and via the command line.

In this way you get a debian based server without the hassles of Debian stable release which oinstalls older (very stable) versions of, say, Apache - yet doesn't allow newer server packages unless you upgrade to Debian unstable (which is by definition unsuitable for a production server)!

I don't want to slate other distro's but in my opinion you cannot beat Debian for things like its no-frills, rock-solid core and the apt package manager. With Ubuntu you get the best of Debian in an up-to-date & well-supported distribution.

Just keep hacking at the command-line - this will benefit you immeasurably after 3 - 6 weeks when the learning curve evens out. Google for Debian specific HOWTO's and tutorials... when you see RH specific commands like 'chkconfig' and 'service' just remember that you can restart any daemon or server with the following:
```
~$ sudo /etc/init.d/apache2 restart
```
Of course, you can replace 'apache2' with 'networking' or 'mysql' or whatever...
By googling for 'startup scripts' you will quickly find how to enable/disable the scripts under /etc/init.d (this relates to the RH command 'chkconfig').

So just stick with it - you made a good choice to install Ubuntu server!

---

### Post by defkewl on 2005-04-25
[QUOTE=sbaker33]I am longtime Windows admin trying to learn Linux.  I have been playing with the desktop for a few months now and I am now wanting to learn more about the server side of things.  Ubuntu is, for me, the best desktop distribution I have found so I have installed Ubuntu using the "server" option in setup and I am trying to work through a samba tutorial.  I would then like to do the same with Apache, etc.

Here is the problem: a number of the steps and commands used in the tutorial do not appear to be available in Ubuntu such as chkconfig and lpadmin.  Is this because the tutorial is out of date?  Is this because Debian doesn't included such tools?  Or is this something Ubuntu specific?

What is the best distribution for learning Linux server administration?  Not necessarily the easiest but the most "standard" so knowledge will transfer regardless of distro.  Which distribution is most "complete" and ready for deployment within small/medium environments.

Thanks[/QUOTE]
 For Linux server IMHO it goes to RHEL or Debian.
But not Fedora since Fedora is a Beta distro of RHEL

---

