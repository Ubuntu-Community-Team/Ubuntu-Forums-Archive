---
title: "Converting desktop to server"
date: 2008-04-19
forum: Server Platforms
---

### Post by kslat3r on 2008-04-19
Hey guys,

I currently have a box running X, Gnome etc. but I want to convert it to a server installation with no login prompt, just CSI based programs.

What is the best way to go about this apart from a complete reinstall? I tried removing the ubuntu-desktop package but it seems this is just a reference package as it did nothing.

Regards,

Ed

---

### Post by andguent on 2008-04-19
The biggest difference between the desktop and the server is simply what software is installed.

To temporarily shut off the graphical layer (it will start next reboot), try: **sudo /etc/init.d/gdm stop**

To disable the graphical layer, try: ** sudo chmod a-x /etc/init.d/gdm**
If you want to revert that later, just: ** sudo chmod a+x /etc/init.d/gdm**

I'm sure others will have a more complete way of reclaiming all of that space that Firefox & OpenOffice take up. Those are my quickies. :)

---

### Post by calc on 2008-04-19
If you can somehow get a list of what is installed on the server install, you can remove all the packages not installed on the Ubuntu server version, which would among other things would probably get rid of GDM and X.

---

### Post by FakeOutdoorsman on 2008-04-20
Here is a list of packages from the command-line install of Ubuntu Gutsy from the alternate disc.  This is the bare minimum you can get (at least with the alternate disc).  Add "openssh-server" and "linux-image-2.6.22-14-server" and you'll basically have a base server install to build from.

---

### Post by joeabiraad on 2008-04-20
well I guess you will need to install the following also 
PHP, MySQL, Perl , Apache  , sendmail/qmail/...

---

### Post by haemphyst on 2008-04-20
> **andguent said:**
> The biggest difference between the desktop and the server is simply what software is installed.

If this is the case, and I was looking to build an Ubuntu Server, but KEEP the desktop, what would I remove, and what would I install additionally?

---

### Post by andguent on 2008-04-20
It really all depends on what you want to do with the server. If you want to setup file sharing, install samba. If you want to setup a web server, install apache2. Mysql & PHP often go along with apache, but they aren't required. There are thousands of other server type things to install.

Maybe the best question is: What do you want to do with the computer? 

Having the desktop software installed will tie up some disk space and possibly some memory, but that really isn't a big deal if using it for a home server.

---

