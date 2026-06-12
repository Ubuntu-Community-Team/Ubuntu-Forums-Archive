---
title: "Ubuntu Desktop useful serverwise?"
date: 2006-08-03
forum: Server Platforms
---

### Post by oblivian on 2006-08-03
Hi,
I hope this isn't a question asked to death, but here goes:

I am about to set up a Linux/Ubuntu LAMP, FTP and mail server (Postfix and Cyrus). I downloaded the server installation of Ubuntu. Is the Desktop version of Ubuntu inferior to the server version (serverwise) or has it just more add-ons, GUI, etc. I am kinda n00bish on Linux and have only set up desktop configs, and only experimentet a bit with servers, however I have set up a lot of Windows server configurations (Apache, MySQL, PHP, etc). The machine is an Intel P4 3.4GHz, 1GB RAM, 300GB HD.

Would you guys recommend me going for the Desktop version and add neccesary components later?

Please advice,

Obi

---

### Post by Jose Catre-Vandis on 2006-08-03
The Ubuntu Server CD will give you just that, with options to install LAMP (Apache, php,mysql) to help get you going. The default leaves you with a command line, which if you are newish to Linux can be a bit daunting. The usual response to installing the desktop to a server is about performance overhead, but by installing the desktop it allows you to see your way around and learn things, along with the command line interface. After a while you will be happy working at the command line and can turn off the desktop. Given your config, your server shouldn't have any problems running a gui :-)

It is probably best to do server install and then add the desktop to it, rather than installing the desktop version and then adding server capabilities. You might also try installing one of the lighter desktops, e.g. Xubuntu. To do this:

Run the Server CD and install (I would suggest the LAMP install)
once you are at the command line, type the following:

Gnome
```
sudo apt-get install ubuntu-desktop
```
or 

XFCE
```
sudo apt-get install xubuntu-desktop
```
or

KDE
```
sudo apt-get install kubuntu-desktop
```

and follow the prompts. You can install all three if you wish

HTH (and is correct with regards to the server install)

---

### Post by inthewayboy on 2006-08-03
I was just looking at another thread like this:

[http://www.ubuntuforums.org/showthread.php?t=227365](http://www.ubuntuforums.org/showthread.php?t=227365)

And while it mirrors the suggestions, a user posted in the thread what may be a better solution.

See, when you do the ubuntu-desktop it looks like it adds not only the desktop but several other packages that just aren't necessary. While I haven't tried it yet I do like the idea of only installing the bare minimum in regards to this since it's already extra overhead as is.

I think it's like the third post on the thread...good luck!

---

### Post by oblivian on 2006-08-04
> **Jose Catre-Vandis said:**
> It is probably best to do server install and then add the desktop to it, rather than installing the desktop version and then adding server capabilities. You might also try installing one of the lighter desktops, e.g. Xubuntu. To do this:

Run the Server CD and install (I would suggest the LAMP install)
once you are at the command line, type the following:

Gnome
```
sudo apt-get install ubuntu-desktop
```

Thanks for the info, just what I needed to know. BTW, when installing (apt-get) ubuntu-desktop, does it install all the extra features, like OpenOffice, themes, games and all that comes with the desktop PC, or just the Gnome shell? And is it as easy to uninstall as to install? Also, I was under the impression that you can run the server in different run modes (like services/daemons only), so if you install all the extra features of the Desktop version it just takes HD space, not RAM or realtime resources?

Thanks for your help!

---

### Post by oblivian on 2006-08-04
> **inthewayboy said:**
> And while it mirrors the suggestions, a user posted in the thread what may be a better solution.

Thanks man, I'll take a look at it! :)

---

### Post by scxtt on 2006-08-04
save yourself a headache - if you want to use a GUI **and** have a server, just install the standard version then install any server packages you want (apache, mysql, etc.) ... in this day-in-age HDD space really isn't an issue, so if you're not comfortable setting up a server in CLI - don't ...

---

### Post by Jose Catre-Vandis on 2006-08-04
Also, have a look at this thread about running a headless server, which also has some help about switching the gdm on and off

[http://www.ubuntuforums.org/showthread.php?t=174900](http://www.ubuntuforums.org/showthread.php?t=174900)

---

