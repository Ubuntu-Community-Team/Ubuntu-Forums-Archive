---
title: "Startx on linux ubuntu server 32 (9.04) ?"
date: 2009-09-08
forum: Server Platforms
---

### Post by Jackzenth on 2009-09-08
Hi i am veryyyyyyyyyyyyy much a linux newbie (please dont ask me why i am using a SERVER build!!)

In simple step by step plain english i need to resolve thisissue:

# startx
The program 'startx' is currently not installed. You can install it by typing:
sudo apt-get install xinit
-bash: startx: command not found

Obviously i then went on the try installing "xinit:

# sudo apt-get install xinit
[sudo] password for malcolm:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xinit not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or is only available from another source
However the following packagees replace it:
    x11-common
E: Package xinit has no installation candidate

What can i do? I really need to get the startx working, i am far to new to linux to be able to use pure terminal.

---

### Post by d_liebscher on 2009-09-08
Hi,

the simplest way to get an GUI is to install an desktop package. The favorites are Gnome, KDE or XFCE. 

Just to go for one for now, you can install another later, if you want.

To install Gnome type:

```
sudo apt-get install ubuntu-desktop
```KDE is

```
sudo apt-get install kubuntu-desktop
```and for XFCE you can use

```
sudo apt-get install xubuntu-desktop
```after installing this metapackage, which contains all necessary packages just reboot:
```
sudo reboot
```and your grafical user interface will ask you for login. 

Daniel

---

### Post by windependence on 2009-09-08
Ubuntu server does not have a GUI by default because servers do not need a GUI to properly admin them and they are a security risk. Canonical has left off the GUI from the server product for this reason:

> **No X server by design**

  By design, Ubuntu Server Edition does not include an X server or any graphical desktop applications. This is a deliberate choice as we believe that most servers should be serviced remotely, are safer without the addition of code that needs direct communication from user space to hardware, and should not be used as a desktop by their administrator. 
 [INDENT] 	 	"*So I applaud the Ubuntu team&#8217;s common sense (and courage) in keeping the X Window System out of the default installation of Ubuntu Server.*"
	--Mick Bauer in April 2008 Linux Journal - "Security Features in Ubuntu Server"   	
 [/INDENT]

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

Now, being that you are so new to Linux, you may not be aware that for home server use, the desktop version is perfectly fine and will run any application you need for that platform. It also comes with a GUI for those who are challenged by the command line. There is no need to run the server edition unless you are running virtualization or a server with high loads. You can still run Apache, MySQL and PHP on the desktop version without any issues. You can certainly install the GUI packages on the server edition, but that 's kinda defeating the whole reason they left it out in the first place.

-Tim

---

