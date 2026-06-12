---
title: "Converting Desktop to server 14.0.4"
date: 2015-11-07
forum: Server Platforms
---

### Post by Sean_Woods on 2015-11-07
[FONT=arial]Quick question on a box that I am working on. Looks like Ubuntu 14.0.4 desktop is installed on this box I would like to covert it to server, but I am fearing my current packages may not recover. I am currently running Observium, Unfi controller, and teamspeak on this box. If I run the commands below will I have to setup these services again?

[/FONT]```
# install the 'tasksel' package so we can remove the desktop image       
sudo apt-get install tasksel

# remove the desktop image
sudo tasksel remove ubuntu-desktop

# tell tasksel to start the server image setup
sudo tasksel install server

# update
sudo apt-get update

# install the server images
sudo apt-get install linux-server linux-image-server

# remove lightdm
sudo apt-get purge lightdm

# remove all packages no longer required (~400 MB) sudo apt-get autoremove
```[COLOR=#FFFFFF][FONT=arial]
[/FONT][/COLOR]

---

### Post by TheFu on 2015-11-07
Make a full system backup.
Test.
See how it works.

I've don't know anything about your list of important programs. If they have a GUI, removing the desktop will likely remove them as well. That is the rough delineation.

Server vs desktop isn't some big difference on Unix like it is on Windows. You can load any GUI programs onto "Server" and do some minor config.

If I were you and didn't want a GUI anymore, I'd consider 2 options.
a) backup everything I need, do a fresh "server" install, then restore the server specific configs and data. This is a basic skill that every admin needs anyway.
b) Disable the GUI at boot and simply never use it again. All this costs is storage. Resources will not be taken if X/Windows doesn't start.

I only install "server" on my systems. Don't have a package named linux-server installed on any of them. Don't recall when that change happened  - 4-6 yrs ago.

---

### Post by Sean_Woods on 2015-11-08
If by GUI youre referring to a desktop environment then no they do not. This box is headless and I control it via SSH. Just a little info on the apps that is install on this box.

Ufifi controller: This is a HTTPS site hosted on this box that allows me to control the access points on multiple site that I support.

Observium: This is an SNMP monitoring tool that uses port 80, again this is a site hosted on the box.

Teamspeak 3: A voice application that users connect to via tcp and udp, but no gui.

---

### Post by mastablasta on 2015-11-09
tasksel shouldn't be used to remove things.

---

### Post by moebob24 on 2015-11-09
Can't you just add additional packages to the existing box? SSH, Apache, or whatever you are trying to host on the server?

---

