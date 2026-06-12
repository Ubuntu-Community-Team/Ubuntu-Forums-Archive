---
title: "KDE installed then install LAMP from server CD"
date: 2006-12-01
forum: Server Platforms
---

### Post by ubuntumaybe on 2006-12-01
Hi,

I have KDE installed and I want to install the LAMP server from the server CD. When I boot with the server cd and I attempt to install LAMP it want to create new partitions. How do I install LAMP from KDE? I do not have broadband. Thanks.

---

### Post by Iowan on 2006-12-04
Your 3 day old post looks lonely...
I have installed neither LAMP nor KDE, but it may be easiest to install LAMP from the CD, then install KDE over that.

At very least, I'll give your post a bump...

---

### Post by ubuntumaybe on 2006-12-06
Hi,

 THanks for your repsonse. Since I have spent the time installing the KDE and do not want to go through the same process I was hoping that there was an easy way of installing LAMP from the CD. Of course I know that nothing is easy in Ubuntu. I have checked the cd and I see that there is a folder with all the required packages. I have tried to install but I keep getting dependencies problem messages. It would have been nice if the cd had a Install to Desktop initial section but that would have made too much sense. THanks

---

### Post by PanzerMKZ on 2006-12-11
add the server cd to the sources.list  then apt-get what you need.  



Panzer

---

### Post by ubuntumaybe on 2006-12-18
Hi,

I ran the apt-cdrom add command and added the packages to the list. I manages to install lamp and I already had phpmyadmin on the windows partition. The problem is that the install of the server packages added a couple of entries into the menu.lst. I have been trying to install the gnome from the dapper live cd but I have been receiving errors about package not found. Since I do not have broadband I cannot download the alternative cd. Is there a way of installing the gnome desktop from the dapper live cd?

---

### Post by az on 2006-12-18
> **ubuntumaybe said:**
> The problem is that the install of the server packages added a couple of entries into the menu.lst. I have been trying to install the gnome from the dapper live cd but I have been receiving errors about package not found. 

Those entries are not the problem.  The problem is that there are no packages available on the cds.

> **ubuntumaybe said:**
> 


Since I do not have broadband I cannot download the alternative cd. Is there a way of installing the gnome desktop from the dapper live cd?

No, there is not.  The live cd is not a like the alternate cd.  The alternate cd installs stuff from a repository on the cd.  The live cd is just a running system on disk.  The apps are not packaged, they are installed there.

The live cd contains a small repository on it (apart from the live session) that contains a few tools - that's why you can add the live cd as a repository, but it is only a very small one and does not contain any packages that are used in the live session.

---

### Post by pppetter on 2006-12-18
@ubuntumaybe
You say that ubuntu doesn't make sense. But actually all this does make sense. 
First of all, Ubuntu server edition is, just as Ubuntu and Kubuntu, a system of it's own. U.S.E. is not designed as an add-on for Ubuntu or Kubuntu. This is the reason why it, at startup, will go roughly through the same process as the Ubuntu or Kubuntu, and want's a partition of it's own.

Now, you said that your installation of the server packages from the cd created new entries in your menu.lst. If this is the case, you have probably managed to install the server edition of the kernel, which is optimized for server use only, and not your server slash desktop use, and will propably make your daily use of the computer a bit slower if you use it. I recommend that  you either just not use them or you could remove them with your favourite package-handler. Their name will start with linux-image and end with -server. 

Lastly. As I stated earlier, each version...Ubuntu, Kubuntu, Server Edition and so fourth, are designed to be different systems, and each one is designed to be fast and easy to install. Therefore, just as "azz" said, the desktop versions are Live-CDs, and thus you cannot install whichever package from these cds. May I also add that if you get a hold of the alternate cd, I wouldn't recommend you to install gnome on the same partition as kde unless you are sure of what you are doing, or have a friend that can help you out with that.


So, actually, I do think that using Ubuntu and the other versions is very simple - if you use them for the purpose they have been created. ;)

---

### Post by az on 2006-12-18
> **pppetter said:**
> 
Lastly. As I stated earlier, each version...Ubuntu, Kubuntu, Server Edition and so fourth, are designed to be different systems, and each one is designed to be fast and easy to install. Therefore, just as "azz" said, the desktop versions are Live-CDs, and thus you cannot install whichever package from these cds. 

LAMP is just a bunch of packages.  No, you don't want to run a server kernel on a desktop, but installing the LAMP stack will not fetch the server kernel unless you specifically install the linux-server kernel package.

To install the LAMP stack on any Ubuntu computer:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Those package will run on a desktop system or a server system.  They do not conflict with any of the packages you have installed on a desktop system (Ubuntu, Kubuntu, Xubuntu, Edubuntu...)

Read:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by PanzerMKZ on 2006-12-19
ok help me with this one.  Why is it not good to run the server kernel as a deskop.  Right now I currently only run servers.


Panzer

---

