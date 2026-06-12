---
title: "no internet access, how to update"
date: 2007-10-15
forum: Server Platforms
---

### Post by externalsupport on 2007-10-15
I have got a webserver that is situated  in the secure segment of our network, the server has no access either to the internet to get updates or to the internal network so that I can set up some kind of update server. 

Is there any way that I can download updated packages onto a server our internal netword and then push these updates to the webserver?

Here's hoping :confused:

Ste

---

### Post by netlogic on 2007-10-15
yes, research aptoncd

---

### Post by externalsupport on 2007-10-15
Thanks

Will do

ste

---

### Post by ruibernardo on 2007-10-15
Yes, APTonCD would do, if this was a Ubuntu Desktop. Ubuntu Server doesn't have a graphical environment, and running APTonCD on a Ubuntu Desktop to upgrade a Ubuntu Server will not find the upgrades for the Ubuntu Server kernel, for example.

This is the kind of problem that I'm trying to solve with a script I've made a few days ago. You can take a look at it on this thread: [Howto: NoNetDebs - upgrade Ubuntu without Internet (or with low-bandwidth connection)]("http://ubuntuforums.org/showthread.php?t=572819").

You will need a a little file from your Ubuntu Server (/var/lib/dpkg/status, copy it to a USB pen), a LiveCD or a K/X/Ubuntu Desktop connected to the Internet and then install the packages "dialog" and "debootrap" to be able to run the nonetdebs script on this connected Ubuntu.

It will create a chroot, where it copies the status file, and then you select "Upgrade". This will show which packages are available for upgrade based in the packages you have installed on the not-connected box. Select "download" and download these files to the USB stick (or create an ISO file to burn them to a CD).

Go back to you Ubuntu Server, plug the USB pen and mount it. Go to the directory in the pen where you saved the packages and run "./nonetrepos" from it. This will add a new repository (the USB pen) to your sources.list. Then install the packages.

```
sudo apt-get update
sudo apt-get upgrade --allow-unauthenticated

```You can use nonetdebs to install new packages too. More info on that thread.

---

