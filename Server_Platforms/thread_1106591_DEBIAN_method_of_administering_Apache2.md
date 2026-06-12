---
title: "DEBIAN method of administering Apache2"
date: 2009-03-25
forum: Server Platforms
---

### Post by aajax on 2009-03-25
I've just installed Ubuntu Server and have discovered that it offers a pretty elaborate facility for administering Apache2 that appears to be peculiar to DEBIAN.  Insofar as I've found the DEBIAN influence on such things to be far ahead of anything I might invent, I'd really like to learn how the developers of these mechanisms intend them to work before I start hacking away and undoing worthy features.

Is there a recommended reference for gaining knowledge of the DEBIAN specific administration mechanisms for Apache2?

---

### Post by mrsteveman1 on 2009-03-26
What do you mean debian specific? Most platforms have an apache2ctl program of some kind even if it isn't named the same, and most platforms separate out some configuration sections into separate files and directories by using Include lines in the main apache2.conf file.

What is specific to debian that you need help with?

---

### Post by volkswagner on 2009-03-26
Before hacking away check out the sticky.

[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

Particular [apache]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") info is found in the above via the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html").


Enjoy

---

### Post by aajax on 2009-03-26
> **mrsteveman1 said:**
> What do you mean debian specific? Most platforms have an apache2ctl program of some kind even if it isn't named the same, and most platforms separate out some configuration sections into separate files and directories by using Include lines in the main apache2.conf file.

What is specific to debian that you need help with?

Maybe I'm mistaken but I think apache2.conf is itself DEBIAN specific.  Apache documentation refers to httpd.conf as the default main configuration file.  From what I can tell everything in /etc/apache2 is DEBIAN specific.  None of this stuff is described in Apache documentation.  While the Apache documentation describes the directives it doesn't say anything about the apparent objectives behind the design of /etc/apache2.  While the README.Debian file mentions the set of config files it doesn't offer any insight into the purpose for using such a structure.  I'd love to know the rationale for choosing to do things this way.  I'm thinking it affects where different directives ought to be placed.

> **volkswagner said:**
> Before hacking away check out the sticky.

[http://ubuntuforums.org/showthread.php?t=1046738](http://ubuntuforums.org/showthread.php?t=1046738)

Particular [apache]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") info is found in the above via the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html").


Enjoy

Thanks, that looks like just the kind of answer I was looking for!

---

### Post by mrsteveman1 on 2009-03-26
> **aajax said:**
> Maybe I'm mistaken but I think apache2.conf is itself DEBIAN specific.  Apache documentation refers to httpd.conf as the default main configuration file.  From what I can tell everything in /etc/apache2 is DEBIAN specific.  None of this stuff is described in Apache documentation.  While the Apache documentation describes the directives it doesn't say anything about the apparent objectives behind the design of /etc/apache2.  While the README.Debian file mentions the set of config files it doesn't offer any insight into the purpose for using such a structure.  I'd love to know the rationale for choosing to do things this way.  I'm thinking it affects where different directives ought to be placed.

Things are segmented into discrete locations, for instance module configurations are kept in /etc/apache2/mods-available, and when they are enabled a symlink is made from /etc/apache2/mods-enabled to the mods-available directory, same with the sites-available and sites-enabled, those are vhosts.

The purpose is to avoid having to edit the main config just to enable vhosts or change them, and to make them easier to read and find.

httpd.conf is simply a place to put custom general directives for the server, the syntax of config options however is no different than any other apache2 installation.

Suse does something very similar, redhat probably does too. I'm not sure i've ever seen a Linux machine where the entire configuration was held in one file.

---

