---
title: "Vmware server 2 on ubuntu 9.4 Server x64"
date: 2009-05-21
forum: Virtualisation
---

### Post by 3xtron on 2009-05-21
Hi do anyone know how to install Vmware server 2 on a fresh installed Ubuntu server whitout graphical interface (X).

I have tried to google but i only get 1M of libraries i have to install.

I want to install minimal of unnessasary libraries.

It would really help me. Im tired of all the bugs in Citrix XenServer.

---

### Post by stefangr1 on 2009-05-21
This should not go any different than installinging it on a normal system (with x). You get and unrar vmware server 2 + serial, install the headers of your running kernel and some necessary compiler stuff, and then run the ./vmware-install.pl .

If you mean by minimal install that you want to install vmware without anything else, that's not possible as it needs other programs to build. You 'could' however remove those afterwards (...).

---

