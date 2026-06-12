---
title: "Ubuntu Server Customized Installaton"
date: 2009-10-21
forum: Server Platforms
---

### Post by chrnoaria on 2009-10-21
Hi,
 
I have recently finished compiling a new ubuntu server working as voip and media streaming using asterisk and fms. I want to know if there is a way to make a custom installation disc from this server so I can install it to another server without redo all the steps required, cause the whole process take quite a long time to completed.

---

### Post by cariboo on 2009-10-21
There are sevral tools available to make an image of your server. I have used both [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") and [Clonezilla]("http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php"), with excellent results.

---

### Post by chrnoaria on 2009-10-21
I have tried using remastersys, but the ISO generated can't be used for installation nor as live-cd. I wonder which step I have gone wrong.

---

### Post by Lars Noodén on 2009-10-21
I was looking through the Ubuntu packages for DebianLive, which is what I thought to suggest:
[http://wiki.debian.org/DebianLive](http://wiki.debian.org/DebianLive)

and did not find it, but found live-magic:
[http://packages.ubuntu.com/jaunty/live-magic](http://packages.ubuntu.com/jaunty/live-magic)



Another way, is to make a script to install the packages, users, and groups you added.  Then have a tar-ball for the directories and files you made or changed.  Put both inside another tarball or even your own APT package.  

The result is you do a quick default installation with the 'CLI' option.  Then log in and run the script.  Works very well and is nice and small.

---

