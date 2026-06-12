---
title: "Ubuntu server too pure ????"
date: 2007-02-09
forum: Server Platforms
---

### Post by HW_Hack on 2007-02-09
I'm a noob just learing and figuring things out - recently ran Fedora Core 6 as a file server for awhile - it was ok. Thought I would try Ubuntu server since I like Ubuntu on the desktop .... I got the 2 drive RAID 1 setup ok - but was a bit puzzled after logging in at ...... well nothing. Just the cursor and a prompt  ........   pretty bare environment. 

At least with Fedora they give you a bare-bones Xwindow environment and a basic browser to use. The command line is fine ----- I just want to be able to have multiple windows as I set things up  etc. 

Am I missing something obvious in the install ---------  I see someone here has indicated you need to load    gnome-core and xorg.xserver

---

### Post by ehowell on 2007-02-09
No, you're not missing anything, the server version does not install a Desktop environment (not necessary in most server cases...)

However, I DID want to run the server version with a desktop, so I installed Xfce (Xubuntu desktop) because the machine was older. 

You can install any of the three main desktop environment flavors (KDE, Gnome, Xfce) easily using aptitude.

sudo aptitude update
sudo aptitude install xubuntu-desktop

substitute kubuntu-desktop for kde or ubuntu-desktop for gnome.

It's recommended to use aptitude as it makes it easier to uninstall it later if you want to switch.

Depending on your hardware you may want a lighter desktop environment, then you can try out something like fluxbox ([Fluxbuntu]("http://fluxbuntu.org"))

This was originally in another thread as well ([http://ubuntuforums.org/showthread.php?t=331509](http://ubuntuforums.org/showthread.php?t=331509))

Good luck!

---

### Post by kerry_s on 2007-02-09
yeah, ubuntu server is no gui. You can add it->

sudo su

nano /etc/apt/sources.list

comment out the cdrom & uncomment all the repos

apt-get update

apt-get dist-upgrade

apt-get install x-window-system-core  gdm (your choice of desktop)

you can install DE which comes with all the bells and whistles or keep it minimal and install a WM instead. I prefer->

apt-get install x-window-system-core gdm fluxbox emelfm leafpad synaptic


look around and select what ever you want to use, the choice is up to you. server is basically a starting point to make what ever setup you want.

---

### Post by SuperMike on 2007-02-09
(soapbox)
What does Canonical plan to do with Ubuntu Server? Make us all have to type command line stuff all the time for adding, removing, modifying users, password settings, DNS, netcard settings, runlevel editing, and so on? I sure hope not. Yeah, I'm a big fan of non-GUI servers, but at least with Suse I can go through Yast to accomplish things fast. Some may say do it all at command line, but when you've added your 25th user into a proper place in the LDAP directory and set their password settings just right, you may be ready to kick Ubuntu Server to the curb. Some may say, "Well, I just use Webmin with the vTiger interface for it," but not in my office you wouldn't -- the net admins only want app tier services to run SSH, PostgreSQL traffic, and mail. Only the the web tier servers may run SSH and web server stuff. So Canonical or the Debian community should come up with something else to help speed up repetitive admin chores that Lan Managers have to do on a regular basis. Also think about when I go on vacation and I have to walk a rookie through doing LDAP user/group security over the phone with nothing but command line -- that won't work well.
(/soapbox)

---

### Post by Brazen on 2007-02-10
> **SuperMike said:**
> (soapbox)
What does Canonical plan to do with Ubuntu Server? Make us all have to type command line stuff all the time for adding, removing, modifying users, password settings, DNS, netcard settings, runlevel editing, and so on? I sure hope not. Yeah, I'm a big fan of non-GUI servers, but at least with Suse I can go through Yast to accomplish things fast. Some may say do it all at command line, but when you've added your 25th user into a proper place in the LDAP directory and set their password settings just right, you may be ready to kick Ubuntu Server to the curb. Some may say, "Well, I just use Webmin with the vTiger interface for it," but not in my office you wouldn't -- the net admins only want app tier services to run SSH, PostgreSQL traffic, and mail. Only the the web tier servers may run SSH and web server stuff. So Canonical or the Debian community should come up with something else to help speed up repetitive admin chores that Lan Managers have to do on a regular basis. Also think about when I go on vacation and I have to walk a rookie through doing LDAP user/group security over the phone with nothing but command line -- that won't work well.
(/soapbox)

Walking rookies through the command line is super easy, you just tell them the exact commands to type in, instead of trying to explain where they need to click, what menu to look for or whatever.

Ubuntu server is meant for the die-hard server admins who only work with command line.  They already have a solution for people like you -- it's called Ubuntu Desktop.  Around here I don't allow GUI on our servers.  I have to think about resource usage, especially when we use VMWare ESX Server virtualization to tweak every bit of resource usage out of our hardware.  Plus security, more software installed and running means more vulnerabilities.  And once you get comfortable with the command line, you'll be amazed at how much faster it can be than doing things the gui way, especially at repetitive tasks.

When Ubuntu no longer has a stripped down server version is when Ubuntu will no longer be on my (and many other's) servers.  I guess the serious server admins will just go back to Debian then (granted, many of them will have never left).

---

### Post by tturrisi on 2007-02-10
fyi-
DON'T install a window manager, ie. gdm, xdm, or such.  You don't need a window manager for anything except gui logins.  Else at every boot you will have to login using it and it will automatically take you to the gui desktop.  Without a window manager you always boot to the shell and login and if need gui then use the command startx.  Most all package installs, reconfigures, updating is done from the shell anyway, and you can even boot the system and never login yet all your servers will be up & running.  This is most secure too.

On servers that I want a gui on I use:
apt get install x-window-system fluxbox nedit emelfm

The only gui apps needed for server are a text editor & a file manager (nedit & emelfm).

---

### Post by Enverex on 2007-02-10
> **SuperMike said:**
> (soapbox)
What does Canonical plan to do with Ubuntu Server? Make us all have to type command line stuff all the time for adding, removing, modifying users, password settings, DNS, netcard settings, runlevel editing, and so on? I sure hope not. Yeah, I'm a big fan of non-GUI servers, but at least with Suse I can go through Yast to accomplish things fast. Some may say do it all at command line, but when you've added your 25th user into a proper place in the LDAP directory and set their password settings just right, you may be ready to kick Ubuntu Server to the curb. Some may say, "Well, I just use Webmin with the vTiger interface for it," but not in my office you wouldn't -- the net admins only want app tier services to run SSH, PostgreSQL traffic, and mail. Only the the web tier servers may run SSH and web server stuff. So Canonical or the Debian community should come up with something else to help speed up repetitive admin chores that Lan Managers have to do on a regular basis. Also think about when I go on vacation and I have to walk a rookie through doing LDAP user/group security over the phone with nothing but command line -- that won't work well.
(/soapbox)

Then use the Ubuntu DESKTOP distro. Servers do not need, nor should they have GUIs, it's a waste of machine resources which could be much better used in other places. SSH and standard terminals are all you should need to use it, possibly 'screen' if you need to keep reconnecting to a live session.

---

### Post by Brazen on 2007-02-11
> **Enverex said:**
> ...
SSH and standard terminals are all you should need to use it, possibly 'screen' if you need to keep reconnecting to a live session.

Oh man I love screen.  I use it especially when I'm running a long script from and ssh session.  That way if my workstation, network connection, or ssh session dies for any reason, my script keeps running along happily.  In addition, I can check on it from work and then later from home if the script is still running.

---

### Post by nix4me on 2007-02-11
pure servers SHOULD be command line only.  The gui is a waste of resources for a true server.

Servers are made to work, not look good.

nix4me

---

### Post by jorgerosa on 2007-04-10
Can this help you? (For me... I still praying... [-o<  ...but im not pure, so why should be my PC??? By the way, in future, should exist any server in the world without GUIs??? I think no... but its just me...)
Web-based: [http://ubuntuforums.org/showthread.php?t=405574&highlight=guis+for+server](http://ubuntuforums.org/showthread.php?t=405574&highlight=guis+for+server) --- Discuss: [http://ubuntuforums.org/showthread.php?t=401151&highlight=guis+for+server](http://ubuntuforums.org/showthread.php?t=401151&highlight=guis+for+server)

---

