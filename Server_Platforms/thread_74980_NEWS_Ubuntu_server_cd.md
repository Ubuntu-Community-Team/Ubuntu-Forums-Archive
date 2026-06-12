---
title: "NEWS: Ubuntu server cd"
date: 2005-10-13
forum: Server Platforms
---

### Post by UbuWu on 2005-10-13
An ubuntu server cd will soon be available from [http://releases.ubuntu.com/ubuntu-server/](http://releases.ubuntu.com/ubuntu-server/) which will make Ubuntu even more attractive for use on the server. It will include a bunch of server applications in place of the desktop (only the server boot option, though, you don't get a huge bunch of servers installed by default). Great news!

---

### Post by jasmuz on 2005-10-13
On my book, that ROCKS!

---

### Post by theQmaster on 2005-10-17
Okay - that's good news but I have a question - if I already run a server how do  I minimize the footprint of the things I don't need ?

Can I start the current instance in server mode ? ( It's Hoary )

---

### Post by shakin on 2005-10-17
This won't be useful for a real server until Ubuntu adopts a longer security support cycle with 6.04. Personally, I think it's more than a bit insane to put a distro on a server if it's only going to get 18 months of security support. 6.04 will get five years of support on the server.

---

### Post by theQmaster on 2005-10-18
[QUOTE=shakin]This won't be useful for a real server until Ubuntu adopts a longer security support cycle with 6.04. Personally, I think it's more than a bit insane to put a distro on a server if it's only going to get 18 months of security support. 6.04 will get five years of support on the server.[/QUOTE]

So what would be your recomandation then ?
Go with debian ? Don't I have to pay to do that ?

Really what's my best bet
- to have production server 
- to be secure
- to be easy to configure and update/maintain
- to support postgresql 7.4.7 

I know people here, in Ubuntu forums, are saying that Ubuntu may not be the right way as server.

---

### Post by UbuWu on 2005-10-18
[QUOTE=theQmaster]Okay - that's good news but I have a question - if I already run a server how do  I minimize the footprint of the things I don't need ?

Can I start the current instance in server mode ? ( It's Hoary )[/QUOTE]

Did you install with the server option? Then it should be pretty minimal already.

---

### Post by mcewen98 on 2005-10-18
[QUOTE=theQmaster]So what would be your recomandation then ?
Go with debian ? Don't I have to pay to do that ?

Really what's my best bet
- to have production server 
- to be secure
- to be easy to configure and update/maintain
- to support postgresql 7.4.7 

I know people here, in Ubuntu forums, are saying that Ubuntu may not be the right way as server.[/QUOTE]

No, debian is free, [http://www.debian.org/distrib/](http://www.debian.org/distrib/)

I dont' see what is wrong with using ubuntu on a home server, as long as you don't mind upgrading at least every 18 months, and don't worry too much about breakage from the apt-get dist-upgrade process.  For a production business server, probably debian would be better.

---

### Post by theQmaster on 2005-10-18
Alright, now the "harm" is done - I have ubuntu as server and I'd like to get the most of the machine.

1. How to do I optimize ubuntu to get close in perfomance with debian.
2. If 1. is not possible, is it possible to move from ubuntu to debian directly, without wiping everything off ? I already have everything installed and I dont want redo it all.


I think at boot time there is an expert/server mode - am I wrong ?

theQMaster

---

### Post by hagen00 on 2005-10-19
[http://releases.ubuntu.com/ubuntu-server/]("http://releases.ubuntu.com/ubuntu-server/")

I see that the server edition is now out. Does this mean there will be longer support for this edition? I really see now how the Ubuntu desktop edition is less than ideal for a server. I'm really hesitant to do a dist-upgrade from Hoary to Breezy, thinking that stuff might get broken. 

Are you guys who are running Ubuntu as a server going to switch to the server edition asap?

---

### Post by thtan on 2005-10-19
Y is ubuntu desktop version less prefered then a server version? Does the server version offered anything more advance?

How bout Debian? How is it powerful and useful then ubuntu as a server? Any practical examples?

I'm a newbie with these stuffs. Hope some1 can help answering. Thanks.

---

### Post by UbuWu on 2005-10-19
[QUOTE=hagen00]
I see that the server edition is now out. Does this mean there will be longer support for this edition? 
[/QUOTE]
No, the next version (dapper/6.04) will be supported for a longer period of time. For this version (5.10/breezy) it will be the usual 18 months.

> 
Are you guys who are running Ubuntu as a server going to switch to the server edition asap?

No need to switch, it is the same as if you have installed from the regular cd's with the server option.

---

### Post by UbuWu on 2005-10-19
[QUOTE=thtan]Y is ubuntu desktop version less prefered then a server version? Does the server version offered anything more advance?
[/QUOTE]

For a server you usually don't need/want a full desktop, so yes, the server installation is most often preferred then. The iso available for download only installs all basic stuff to get a running system, then you can add anything you want yourself. On the server cd there are a lot of additional useful programs for servers.

---

### Post by UbuWu on 2005-10-19
It has been officially announced now:
> 
The Ubuntu team is proud to announce Ubuntu 5.10 Server, the first
release of Ubuntu designed especially for server environments.
Like the standard desktop Ubuntu, it occupies a single CD.  However, 
it is distinguished by the following features:

 * Includes server-oriented kernels with out-of-the-box
   automatic support for multiprocessor systems
 * Includes a wide variety of popular server applications
   such as apache, mysql, postgresql, php, zope, openldap,
   bind, samba, all on the single CD, ready for installation
 * A slim default installation, occupying just 400 megabytes:
   add only the software you need, for a clean, maintainable
   configuration.
 * Provides no desktop environment (GNOME, KDE, etc.) by default
 * Safe and text-oriented boot mode for better clarity and
   infinite justice on boot.

The default installation is secure by design, with no network ports 
active
after installation and access to free security updates activated.  
Network
services are activated only when explicitly installed.

As always, it's supported with regular releases, a commitment to
security updates for 18 months after each release and professional
technical support from many companies around the world.

For more information about the new features shared with Ubuntu 5.10,
see the Ubuntu 5.10 announcement at

[http://lists.ubuntu.com/archives/ubuntu-announce/2005-October/000038.html](http://lists.ubuntu.com/archives/ubuntu-announce/2005-October/000038.html)


To Get Ubuntu 5.10 Server
-------------------------

Download Ubuntu 5.10 here (choose the mirror closest to you):

  Europe:
    [http://se.releases.ubuntu.com/ubuntu-server/5.10/](http://se.releases.ubuntu.com/ubuntu-server/5.10/)

  United Kingdom:
    [http://releases.ubuntu.com/releases/ubuntu-server/5.10/](http://releases.ubuntu.com/releases/ubuntu-server/5.10/)

  Rest of the World:
    [http://releases.ubuntu.com/releases/ubuntu-server/5.10/](http://releases.ubuntu.com/releases/ubuntu-server/5.10/)

Please download using Bittorrent if possible.

Feedback and Helping
--------------------

If you would like to help shape Ubuntu, take a look at the list of 
ways you can participate at

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)

Your comments, bug reports, patches and suggestions will help ensure
that our next release is the best release of Ubuntu ever.  Please 
report bugs through Launchpad:

  [http://launchpad.net/distros/ubuntu/+bugs](http://launchpad.net/distros/ubuntu/+bugs)

If you have a question, or if you think you may have found a bug but 
aren't sure, first try asking on the #ubuntu IRC channel on Freenode, 
on the Ubuntu Users mailing list, or on the Ubuntu forums:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)


More Information
----------------

You can find out more about Ubuntu on our website, IRC channel and 
wiki.
If you're new to Ubuntu, please visit:

  [http://www.ubuntu.com/](http://www.ubuntu.com/)


To sign up for future Ubuntu announcements, please subscribe to 
Ubuntu's 
very low volume announcement list at:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-- 
 - mdz

---

### Post by needplants? on 2005-10-20
So I'm a little confused.  I just got the 5.04 cd, is the server option good enough for a production server?

is the desktop ok for a home server?

---

### Post by jamesstansell on 2005-10-21
[QUOTE=needplants?]So I'm a little confused.  I just got the 5.04 cd, is the server option good enough for a production server?

is the desktop ok for a home server?[/QUOTE]
Based on the reading I've done, it appears that the ubuntu-server iso doesn't have any packages on it that you couldn't download and install from the breezy repositories.  It appears to me to be mostly like kubuntu - you can install KDE from a CDROM or you can download and install kubuntu-desktop from the network, but the packges are the same.

Someone please correct me if I'm wrong.

-james.

---

### Post by mcewen98 on 2005-10-21
[QUOTE=needplants?]So I'm a little confused.  I just got the 5.04 cd, is the server option good enough for a production server?

is the desktop ok for a home server?[/QUOTE]

I use ubuntu for my home server and have been quite happy with it.  It's pretty easy to set up and there's lots of places to get information when you're stuck.  Since I often also run desktop applications, I did the normal installation with gnome.

Using the server install option on a production machine might be ok, but be prepared to upgrade to the newer version in 18 months (or whatever the support cycle is), because you will no longer recieve security updates.  I would probably use the stable version of debian, since that should have a longer shelf life.  Or wait for the 6.04 version of ubuntu as somebody else said, will have 5 years of support and updates.

---

