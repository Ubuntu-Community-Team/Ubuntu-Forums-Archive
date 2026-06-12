---
title: "Configuring UBUNTU as a SERVER"
date: 2005-04-01
forum: Server Platforms
---

### Post by gabs247 on 2005-04-01
I am looking for some help on configuring my system. Unfortunately, I'm going in reverse order, as I didn't use the custom installation, and now I'm trying to remove my overheads :?

Basically, I have set up DNS, FTP, WEB, DB and MAIL services, but I have GNOME being started initially. I wanna make it possible to start the system into a prompt based session, and have the option to start-up a lightweight windowing interface session. So, I'm trying to determine what I should uninstall from the basic UBUNTU installation.

If that makes sense, can anyone help me out? I'm still a newbie, I'm trying to set up a secure linux server which will enable me to host multiple websites with associated ftp/mail services   8-[ 

Thanks in advance,
gabs

---

### Post by ubuntu_demon on 2005-04-01
[QUOTE=gabs247]I am looking for some help on configuring my system. Unfortunately, I'm going in reverse order, as I didn't use the custom installation, and now I'm trying to remove my overheads :?

Basically, I have set up DNS, FTP, WEB, DB and MAIL services, but I have GNOME being started initially. I wanna make it possible to start the system into a prompt based session, and have the option to start-up a lightweight windowing interface session. So, I'm trying to determine what I should uninstall from the basic UBUNTU installation.

If that makes sense, can anyone help me out? I'm still a newbie, I'm trying to set up a secure linux server which will enable me to host multiple websites with associated ftp/mail services   8-[ 

Thanks in advance,
gabs[/QUOTE]
 Okay only do the following of you understand what it does and ar not willing to do a reinstall.

sudo apt-get update
sudo apt-get install ubuntu base
sudo apt-get install debfoster

and remove everything (including ubuntu desktop) except ubuntu-base in this way :

sudo pico /var/lib/debfoster/keepers
and change the file to this :

```

debfoster
ubuntu-base
xfce

```

Also include other packages that you want to use. Be sure not to forget the ones you have already configured because all packages that are not listed will be removed completly (including configuration files)

then do :

sudo debfoster -f

from the manpage of debfoster :
> 
     -f, --force
             Don’t ask anything and assume ‘no’ as the answer to all questions.  It also installs any packages that seem to be missing, thus forcing your
             system to comply with the debfoster database.  Can have ‘interesting’ results if you’re not careful.


Now everything will be removed from your system except the packages you have selected (ubuntu-base,debfoster,xfce and maybe others)

I've only used xfce once for a couple of minutes. So for xfce problems and installation I'm not much of use :)

**EDIT :**
You might also want to include xserver-xorg in the keepers file since you need an X-server for xfce obviously.

If you decide to do it and this is your only box. It would be handy to keep a live-cd aside in case you can't get xfce up.

---

### Post by fdoving on 2005-04-02
I'd strongly recommend to do a clean server install.. and install the needed software.. instead of removing unneeded. That's the way i install even my desktop system.. much more control.

Do a backup of the config files..

---

### Post by ubuntu_demon on 2005-04-02
[QUOTE=fdoving]I'd strongly recommend to do a clean server install.. and install the needed software.. instead of removing unneeded. That's the way i install even my desktop system.. much more control.

Do a backup of the config files..[/QUOTE]
 I agree. that's why I said : " Okay only do the following of you understand what it does and ar not willing to do a reinstall."

---

### Post by fdoving on 2005-04-02
yeah.. I can just second that.. despite the power of apt-get it's easier and better to reinstall a clean server install.
though.. you can learn alot from the messing arround with apt-get. :)

---

### Post by Rottweiler on 2005-04-04
[QUOTE=fdoving]I'd strongly recommend to do a clean server install.. and install the needed software.. instead of removing unneeded.[/QUOTE]Here's another vote. Less risky and you'll have a more realistic idea of what is installed.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=Rottweiler]Here's another vote. Less risky and you'll have a more realistic idea of what is installed.[/QUOTE]
 true

But if you have used debfoster a lot (like me) then it's also a very viable option.I just did it myself because I wanted to strip my server more down to the things I really use.

see this post :

[http://www.ubuntuforums.org/showpost.php?p=116092&postcount=7](http://www.ubuntuforums.org/showpost.php?p=116092&postcount=7)

---

### Post by HungSquirrel on 2005-04-05
Does debfoster keep dependencies, too?  I'm thinking of using it to clean up my system a bit as my / partition is getting a bit full, but I don't want it to keep the things in keepers but not their deps, thus breaking my system.

---

### Post by ubuntu_demon on 2005-04-05
[QUOTE=HungSquirrel]Does debfoster keep dependencies, too?  I'm thinking of using it to clean up my system a bit as my / partition is getting a bit full, but I don't want it to keep the things in keepers but not their deps, thus breaking my system.[/QUOTE]
 debfoster makes a list of orphaned packages (ie. packages that aren't used or needed by other packages) All packages that you put in the keepers file are kept and its dependencies also.

for more information about debfoster do :
man debfoster

In order to use debfoster it's best if you first make sure you have ubuntu-base and ubuntu-desktop installed (unless you'll want xfce instead of gnome)

sudo apt-get update
sudo apt-get install ubuntu-base ubuntu-desktop

and then run debfoster and type i for info, h for help, p for purge, y for remove and n for not remove

to see the list of packages that I wanted for my internet-gateway see :
[http://www.ubuntuforums.org/showpost.php?p=116092&postcount=7](http://www.ubuntuforums.org/showpost.php?p=116092&postcount=7)

for a system clean this is also nice :
sudo apt-cache clean (cleans your apt-get cache this can be a lot of space if you never do apt-get clean)

deborphan --find-config (to find leftover configuration files)
deborphan -a (to find all orphans only remove things you are sure about)

---

