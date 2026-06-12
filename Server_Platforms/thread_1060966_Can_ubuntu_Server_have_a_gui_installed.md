---
title: "Can ubuntu Server have a gui installed"
date: 2009-02-05
forum: Server Platforms
---

### Post by tegralens on 2009-02-05
I have installed 8.10 server but I thought I might have an option to install like kde or gnome but I did not have that option.  Is there anyway to do it.  I ask because I am new to the linux world I I find it easier to use gui type like kde instead of using the shell.  So is there a way.  I know that Fedora does have a gui options to install.

Never mind I found the answer here I will try it.

[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

---

### Post by ibutho on 2009-02-05
You can install a GUI. If you don't really need all the functions something like KDE or GNOME, it maybe best not to install ubuntu-desktop or kubuntu-desktop. You could just install gnome-core (with gdm) or kde-core.

---

### Post by netztier on 2009-02-05
> **tegralens said:**
> I have installed 8.10 server but I thought I might have an option to install like kde or gnome but I did not have that option.  Is there anyway to do it.  I ask because I am new to the linux world I I find it easier to use gui type like kde instead of using the shell.  So is there a way.  I know that Fedora does have a gui options to install.

Never mind I found the answer here I will try it.

[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html](http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html)

Great you found the solution - which personally, I consider a non-solution. While you *can* install a GUI or desktop environment on a server, I believe that you should not.

Next thing you're likely going to ask is: "How can I get a remote-desktop style connection to my server's GUI?" and you'll need another service to run on that server with yet again it's own configuration and security problems. This probably is the main reason for *not* delivering a GUI by default with Ubuntu server.

[LIST]
[*]Ubuntu's stance on GUI-on-server is:  [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)
[*]The Ubuntu server guide: [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)
[/LIST]

regards

Marc

---

### Post by jerrrys on 2009-02-05
might want to look at this
[http://ubuntuforums.org/showthread.php?t=898328](http://ubuntuforums.org/showthread.php?t=898328)

---

