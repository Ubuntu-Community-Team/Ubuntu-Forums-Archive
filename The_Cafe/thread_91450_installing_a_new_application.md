---
title: "installing a new application"
date: 2005-11-17
forum: The Cafe
---

### Post by phil123 on 2005-11-17
GMorning. Im starting out with Linux and I need to install Gnucash. I followed the instructions and I downloaded and installed the extra applications it asked for. Now it gives an error message and asks for something called ltdl.h which it describes as a --libtool. However I cannot find and download this from anywhere. Can somebody help. I am running Ubuntu on Hoary Hedghog and I thought it had all the lib tools neccessary already from Synaptic packages. Baby talk only please!
Phil123

---

### Post by Brunellus on 2005-11-17
go to System > Adminstration > synaptic package manager.  Wait for synaptic to start up.  


Then search for "gnucash".   Highlight it, click accept, and confirm the changes.  

gnucash should be up and running.


IN GENERAL:  for most of your software needs, use synaptic (or its command-line equivalent, apt).  It finds the software you need, plus all its dependencies, and installs them.  

it really is that easy.

---

### Post by phil123 on 2005-11-17
Thanks for that! But, no Gnucash on Hoary Synaptic packages. Maybe it will be on the Breezy CDs - when they arrive.
Phil123+

---

### Post by Brunellus on 2005-11-17
you probably haven't enabled Universe or Multiverse yet.  

Follow the directions on this excellent wikipage:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Hit "refresh" when you're done doing that, then follow my initial directions.

---

### Post by varunus on 2005-11-17
phil,

Windows and Ubuntu have different ways of installing software.  Windows uses a very decentralized system; each program has its own installer, and users get them individually.

Ubuntu, however, decided to use the "Debian" way; it has a centralized repository that contains everything.  16,000+ packages, installabe with a couple of clicks and from one place.  The only issue arises if there's a program that you don't have a package for; this doesn't come up very often.

Some Linux distros use the Windows way of installing, but not that many anymore; its a lot easier to be able to have one place and one program that can install and set up everything the user needs.

And like Brunellus said, enable "Universe" and "Multiverse."  Ubuntu uses specific locations on the net to hold programs called repositories.  By default, only the stock ubuntu installation packages are enabled in Synaptic (the package manager.)  Universe and Multiverse will contain other applications that people may want/need.

You can also add custom repositories to Ubuntu if you find one on the internet.  For example WINE, a windows interface layer for linux that lets you run some windows programs, maintains their own repository that you can add to synaptic.  There are also repositories available for OpenOffice.org.  Also, if you do want to get a program the windows way, try and find a .deb package of it.  These can be installed using a tool called "dpkg" and integrate with ubuntu's system.

If you do want a program that ubuntu doesn't have in any of its many repositories, you can use the program "checkinstall" to make an ubuntu package from it (though, this requires compiling from source, so post back here if you want a primer on that).

---

### Post by aysiu on 2005-11-17
Look at the two links in my sig.

---

### Post by phil123 on 2005-11-19
Thanks for your replies. This has opened a door!
Phil123

---

