---
title: "Server Installation Help Needed"
date: 2006-12-25
forum: Server Platforms
---

### Post by petersfreeman on 2006-12-25
I have been using the desktop version of Ubuntu Edgy Eft for about a month and really like it.  I installed it but had help from a person who has a lot of Linux expertise.  I decided to install Ubuntu Server (6.10) on an Intel box and make it a LAMP server.  The installation went well and completed without a hitch.  I re-booted and at a command line interface, logged in.

I was surprised as I expected a graphical interface just like the Desktop version of Edgy Eft.  My intent was to replace the XAMP setup I had running under Windows (I was running a web server under Windows using Apache, MySQL and PHP) for a LAMP setup.

Because I am at a command line interface, I am not sure what to do next.  I want to set up my web server and setup Joomla again and all the other things I need to do to make it work.

Can somebody help me by first telling me if there is a graphic user interface and if so, how do I start it, and second, where is there information I can read that will help me understand this server installation.

Thank you,

Peter

---

### Post by cilynx on 2006-12-25
Ubuntu server is pretty much Ubuntu desktop w/o the desktop.  Just install the normal version and you'll be just fine to set up and run your tools.

To install the GUI from the command line and avoid reinstall:
```

sudo apt-get install ubuntu-desktop

```

---

### Post by mscman on 2007-01-03
> **cilynx said:**
> Ubuntu server is pretty much Ubuntu desktop w/o the desktop.  Just install the normal version and you'll be just fine to set up and run your tools.

To install the GUI from the command line and avoid reinstall:
```

sudo apt-get install ubuntu-desktop

```
While nothing cilynx said is wrong, I strongly advise using the command:
```
 sudo aptitude install ubuntu-desktop
```as opposed to using apt-get. This will allow you to remove the entire desktop installation at a later point in time if you so choose. It will also install all recommended packages instead of just the required dependencies.

Aptitude does a better job at handling dependencies and keeping track of installations than apt-get.

---

### Post by cilynx on 2007-01-04
I'll second that .  I'm not really used to telling people to use aptitude as I'm used to the fine turning that you can get from apt-get.  Aptitude does indeed do a better job of handling dependency tracking and conflict resolution.

---

### Post by rth on 2007-01-05
Just to be clear, that package will give you *everything* that is in the regular Ubuntu 6.10, including OpenOffice, image viewers, media players, etc., etc.

A more minimal graphical desktop can be had with this:
```
sudo apt-get install gnome-applets gnome-control-center gnome-icon-theme gnome-menus gnome-panel gnome-session gnome-terminal metacity nautilus gdm x-window-system-core gnome-nettool gnome-system-tools gedit
```

Regardless of which way to go, you should be able to issue a "sudo reboot" (or is it "sudo restart" ? I forget off the top of my head) command and it will prompt you to login with a GUI interface. You could try a "startx" or "sudo startx" command before rebooting as well...

---

