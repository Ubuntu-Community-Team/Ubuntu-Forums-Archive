---
title: "Installing apache modules"
date: 2005-12-28
forum: Server Platforms
---

### Post by Dagur on 2005-12-28
Hi,

I'm trying to use mod_scgi. I did 
[FONT="Courier New"]sudo apt-get install libapache2-mod-scgi python2.4-scgi[/FONT]
  and then I created a symbolic link 
[FONT="Courier New"]ln -s /etc/apache2/mods-available/scgi.load /etc/apache2/mods-enabled/scgi.load[/FONT]

then I added 
[FONT="Courier New"]SCGIMount / 127.0.0.1:8882[/FONT]
 to my site configuration and restarted apache, but I got this:


[FONT="Courier New"]Syntax error on line 8 of /etc/apache2/sites-enabled/000-default:
Invalid command 'SCGIMount', perhaps mis-spelled or defined by a module not included in the server configuration
[/FONT]

What am I doing wrong?

---

