---
title: "Ubuntu Server 9.10 cannot open display"
date: 2009-11-13
forum: Server Platforms
---

### Post by Calanque on 2009-11-13
Hey everyone, first of all applogies, I'm a complete noob when it comes to linux andf therefore ubuntu. I have installed ubuntu server 9.10 and trying to work my way throught the terminal commands.
 
I have installed lamp-server and phpmyadmin, also gedit and gedit-plugins. However whenever I run this command to change the conf file for proftpd I can (gedit:7769): Gtk-WARNING **: cannot open display
 
Am I doing something wrong?

---

### Post by undecim on 2009-11-13
If you installed the server edition, you don't have a graphical display, and so you can't use graphical apps.

If you want to use those apps, the only way you can is to set up X11 forwarding with ssh.

Take a look at [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) for more information about that.

If you need to edit files with the command line, however, you can use "nano filename" where filename is the file you want to edit.

---

