---
title: "Newbie - Adding KDE/Gnome to Ubuntu server"
date: 2008-12-16
forum: Server Platforms
---

### Post by ron2580 on 2008-12-16
Hi Guys,

I am rather new to linux and I am used to working on ubuntu desktop,

I have got a older server that I plan to use as a file server and a DHCP/DNS server at a later stage.

But i cant do a thing on the server in CLI... HELP!

I would love a short run though of adding KDE 3.x Or even Gnome, just so i could start to set the server up?

Oh plz plz plz help...

Ron

---

### Post by Ferret-Simpson on 2008-12-16
Installing a desktop onto the server won't help you set it up, believe me I did the same thing.

Command Line is easy when you get to now it - and it will be your main tool with Ubuntu server, so you'd better start early! :) It's just not possible to administer Ubuntu Server fully graphically out of the box. Howtoforge has some great getting starteds on setting up a server in Ubuntu, they should give you a head start. Other than that:

sudo: Godmode - you'll need this command to do anything advanced.
apt-get update: This gets the latest package information
apt-get upgrade: Updates you to the latest version of the system.
nano: A great command line text editor. Real easy to use.
apt-get install <packagename>: Speaks for itself, no?

So, to update and install Windows Authentication?

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install likewise-open
```

To set static IP's, you need to edit the file /etc/network/interfaces

with a set of options such as this:

auto eth0
iface eth0 inet static
   address 192.168.0.10
   netmask 255.255.255.0
   gateway 192.168.0.1

---

### Post by .nedberg on 2008-12-16
To install a full KDE/Kubuntu desktop
```
sudo apt-get install kubuntu-desktop
```
Gnome/Ubuntu
```
sudo apt-get install ubuntu-desktop
```
More light weight, better for servers and old computers
```
sudo apt-get install xubuntu-desktop
```

---

