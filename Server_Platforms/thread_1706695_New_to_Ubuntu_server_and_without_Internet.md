---
title: "New to Ubuntu server and without Internet"
date: 2011-03-14
forum: Server Platforms
---

### Post by Rui Esteves on 2011-03-14
Hi,
I am just starting with the Linux world and decided to use Ubuntu server as OS for the OpenNebula project that I am preparing.
My machine is not connected to the Internet (I have a sand box for my experiments).
I installed correctly the Ubuntu 10.04.2 Server i386 from a CD, but now I need to install the packages ([http://opennebula.org/documentation:rel2.0:notes](http://opennebula.org/documentation:rel2.0:notes))

[LIST]
[*] **libsqlite3-dev**
[*] **libxmlrpc-c3-dev**
[*] **scons**
[*] **g++**
[*] **ruby**
[*] **libopenssl-ruby**
[*] **libssl-dev**
[/LIST]
1- Using "sudo aptitude", I can only find the ruby and libopenssl-ruby packages. How can I get the others without Internet access?
2- Selecting the ruby and libopenssl-ruby packages, it tries to download them and fails. How can I get them without the Internet access?
3- The OpenNebula documentation says: 
"If apparmor is active (by default it is), you should add $ONE_LOCATION/var to the end of /etc/apparmor.d/libvirt-qemu[FONT=monospace]
[/FONT]owner /path-to-one-location/var/** rw,"
As I cannot find this file, I suppose that it will appear after the installation of those packages. Am I correct?

Thank you in advance.

---

### Post by HugoSerrano on 2011-03-14
Hello Rui!

You can dowload them from another PC.

[http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages)

Then you can install the packages with the command:
sudo dpkg -i "package.deb"

Cumprimentos! ;-)

---

### Post by Rui Esteves on 2011-03-14
Thanks Hugo

I went through the several packages that I need and downloaded all those ".deb" files. I burned them into a CD and put it in the server.
But when I try to dpkg each one of them, it says "no such file or directory". Do I need to copy them to any specific directory in the server hard disk?

Obrigado

---

### Post by HugoSerrano on 2011-03-14
humm... you need to be on the folder where you got the debs, or specify all the way.

ex: dpkg -i /media/cdrom/debfolder/package.deb

Complete with "tabs" to got sure that you don't got typos in the way.

---

### Post by Rui Esteves on 2011-03-14
Thanks! it is working perfectly

Obrigado :D

---

### Post by HugoSerrano on 2011-03-14
:-D nice!

Now just flag this threat as Solved.

De nada!

---

