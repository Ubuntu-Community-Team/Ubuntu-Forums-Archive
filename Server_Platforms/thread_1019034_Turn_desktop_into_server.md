---
title: "Turn desktop into server"
date: 2008-12-22
forum: Server Platforms
---

### Post by zkab on 2008-12-22
When I started with Ubuntu I installed 7.04 Desktop edition at a computer and been upgrading it (now running 8.10 Desktop) but would like to run Server Edition instead on that computer. I understand there are differences in desktop and server kernel meaning I just can't remove the desktop software to get a server version.

I have right now 'linux-image-2.6.27-11-generic' running.
Can I just install 'linux-image-2.6.27-11-server' and then reboot the computer into that server kernel and start to remove:

   linux-image-2.6.27-11-generic
   ubuntu-desktop
   gnome-session
   openoffice.org
   ...

What more to remove to get rid of desktop software that occupies disk space?

---

### Post by beno1990 on 2008-12-22
If you're a novice user setting up a server platform, I'd advise you to do a fresh install of Ubuntu Server Edition, because otherwise you'll have to install the LAMP stack from scratch, among other pieces of software, which come with the server edition.

However, if you really don't want to do a fresh install, you can remove the old kernel image at the same time you install the new one without rebooting; the kernel image is in RAM and doesn't need to be read from the hard disk unless you reboot.

Most GUI software which comes with Ubuntu desktop edition will be uninstalled when you uninstall the Gnome desktop, because these programs depend on the X server (GUI interface) to function.

However, this might not uninstall all of their libraries and such which the programs install automatically as dependencies, so you might have to check your installed package lists and remove any libraries you don't need anymore.

But overall, I'd say, unless there are files on that computer which you want to retain when you convert it to a server and can't backup, just make a fresh install of Ubuntu server edition.

---

### Post by zkab on 2008-12-22
I can't make a fresh install ...
You mentioned the issue with LAMP stack ... the software that are already installed now - like Apache/MySQL/Perl/Python - I guess they will not be removed when installing linux-image-server.
The reason why I wanted to boot into the server kernel was to keep my desktop kernel so I could reboot that one ... if something goes wrong with the server installation.

---

### Post by gcbzzzz on 2009-01-03
yeah, i'd like to know more about that too.


something very debian like, that would install the server meta package and then remove the desktop ones that aren't needed by the server. such as:

apt-get install ubuntu-server
apt-get --purge ubuntu-desktop

but i can't seem to find out which is the main meta package for a server install without doing a full install and then checking myself.

---

### Post by zkab on 2009-01-04
After a lot of thinking and preparing ... I went for a fresh install of Ubuntu Server Edition ... it works OK and it was pretty easy to get all the data working.
I recommend to install a fresh Ubuntu Server Edition ... :D

---

