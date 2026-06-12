---
title: "Virtual Machine on Ubuntu SERVER"
date: 2009-01-02
forum: Virtualisation
---

### Post by dbrine on 2009-01-02
is it possible to run vmware/ virtual machines on a Ubunut SERVER not the desktop. I have a win03 machine VM in Ubuntu desktop which is great BUT I prefer to lose the desktop.

---

### Post by dcstar on 2009-01-02
> **dbrine said:**
> is it possible to run vmware/ virtual machines on a Ubunut SERVER not the desktop. I have a win03 machine VM in Ubuntu desktop which is great BUT I prefer to lose the desktop.

Virtual machines run in anything, you only need a graphical desktop to access them locally. The local desktop is irrelevant to the VM's operation.

---

### Post by dbrine on 2009-01-03
THanks for the quick reply. I've been trying to find out how but no luck yet... Anyone have any good resources on doing this?

---

### Post by HermanAB on 2009-01-04
If you don't want X running, just change to runlevel 3:
$ sudo init 3

Cheers,

Herman

---

### Post by dbrine on 2009-01-04
is there a complete guide/ docs that someone an point me to. I don't want to keep bugging people. 

Thanks for the reply.

---

### Post by dbrine on 2009-02-01
??

---

### Post by seachnasaigh on 2009-02-01
Ubuntu server (any version) deploys without the X-window system (in other words, there is no GUI). You'll need to install that to run VMWare servers (which more-or-less require a GUI) and then switch your runlevel to 5 to administer them (normal command-line runlevel is 3). 

You'll need to:
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 
for starters; remember to set your repositories to universe and multiverse before doing this, or the packages won't be there.

There are lots of threads on this forum for doing just that; that command is the basics. From there set your runlevel and you should be able to administer your VMWare servers. 

Cheers!

--ckr

---

### Post by dbrine on 2009-02-19
how to do you change to runlevel 5?

---

### Post by seachnasaigh on 2009-02-19
Fairly straightforward, but with some caveats.

On a normal Ubuntu system:
sudo telinit 5
... and supply your password.

If you want it to be the default, you'd need to edit /etc/inittab:
id:5:initdefault:
That would be either as root or sudo, your preference.

There are some risks with this command. Do not set telinit S or 0 or 1 unless you know what you're doing. See:
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

Cheers.

--ckr

---

### Post by seachnasaigh on 2009-02-20
I think I see what you want to do, but I'm not sure. So let me give you my experience.

Basically, you want a Windows VM running under VMWare or something similar, you want it running on an Ubuntu server, and you want to administer it remotely (i.e., you do not want a monitor/keyboard/mouse on the server itself). 

If that is the case, I have interpreted what you want to do, then your steps are:

1) Either install Ubuntu on the server with the standard desktop Ubuntu or install Ubuntu Server and install the supplemental X11 packages as described above.

2) Enable SSH to the server and make sure that whatever client you have (Windows, Mac, Linux) has an X-client running. Linux does this by default; Mac is a grey area; Windows, you need to install an X client like CigWin/X. If you're on a Windows machine, you need an SSH client as well (PuTTY or SecureCRT for example) that can do native SSH and X-11 port forwarding.

3) If you opt for a runlevel 3 server type install, you'll need to do a startx from the command line on your SSH client to get X11 going; if you use a runlevel 5 install that already runs a GUI, then you do not need that step. X11 must be running on the server to get X11 port forwarding to the client (regardless of client).

4) On the client, if X11 is running, start your SSH session and type gnome-session at the prompt. On the client, if X11 is not running, type startx at the prompt. You do not necessarily need to be root to do this (in fact, it may throw error messages if you are). 

That should give you a desktop remotely. 

There are a LOT of config files associated with this process; it is not always quite as simple as portrayed here. It should be, but it isn't. If this process does not result in a desktop for you, there is a fair amount of troubleshooting involved to get it to work, far beyond what I could put in one post. 

I've done this a number of times on servers with Ubuntu and Fedora and RedHat. It's always worked, but with a small amount of tweak/patience/reading. man pages are a godsend. The desktop may not "jump" out at you (at first you may see just the toolbars, kind of in the edges of your client window). Click on one of them and the desktop should construct itself. Be aware that the X11 forwarding is somewhat dependent upon your connexion speed; if you're on a dialup, forget it. If you're on a LAN at 100BASET, it should be fine. 

YMMV
Cheers.

--ckr

---

