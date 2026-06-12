---
title: "Problems with virtualbox ose"
date: 2010-04-18
forum: Virtualisation
---

### Post by sudhanshu1990 on 2010-04-18
Hi there,
I have ubuntu 9.10 installed on my system..yesterday I installed VirtualBox Ose on my system with Windows XP as guest....(Actually I switched from vmware as xp was running too slow on it and I needed to work on Visual Studio 2008)....Now Visual Studio working fine but OSE doesn't support my Usb drive....So there is no way I can exchange data b/w my host and guest.....
Is there any work around possible....
  Can I connect my host with guest through some sort of network..if Yes then how??

  Can I use WINE to install VS 2008 express edition...

---

### Post by ajgreeny on 2010-04-18
You will need to use the PUEL version of VirtualBox direct from Oracle in order to get USB enabled.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by wilee-nilee on 2010-04-18
As suggested the puel version is supposed to enable usb use. If you want to have a share file make a folder named share in linux. Then open up XP right click on computer then map network drive and it is pretty self explanatory from there. XP will find the share folder in Linux and now you can just go to computer in XP and you will see a network drive with the share name.

---

### Post by Morbius1 on 2010-04-18
You can access a usb drive from a guest OS in virtual box OSE as long as the host is linux:

_LINUX HOST_
Using the VBox application create a Shared Folder to /media:
Folder Path: /media
Folder Name: hostmedia ( or whatever you choose )

_WinXP GUEST_
Open My Computer

Select Tools
Select Map Network Drive
Drive: Select an available Drive Letter
Folder: Select Browse. You will notice that there is a listing titled VirtualBox Shared Folders. Within that will be the shared folder "hostmedia" you created above.
check Reconnect at login

Every time you boot into the WinXP guest your shared folder created from /media will show up as a drive letter. Within that will be any usb device mounted on the linux host . 

There's also a side benefit. You'll always know who is in charge of the mounted / unmounted device - it's always the host.

---

