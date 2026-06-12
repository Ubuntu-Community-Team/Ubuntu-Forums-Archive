---
title: "[SOLVED] virtualbox"
date: 2007-10-28
forum: Virtualisation
---

### Post by j d on 2007-10-28
tried to install virtualbox got answer
the package virtualbox needs to be reinstalled
but I cant find an archive for it
j d
also i get the same answer when i want to use synaptic
and also with update manager

---

### Post by aysiu on 2007-10-28
Close Synaptic. Close Update Manager. Close Add/Remove.

Open a [terminal](http://www.psychocats.net/ubuntu/termina) and paste in these commands ```
wget -c http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
sudo apt-get -f install
``` If you get any error messages, copy and paste them back here.

---

### Post by j d on 2007-10-29
jan@jan-desktop:~$ wget -c [http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb](http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
jan@jan-desktop:~$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
dpkg: error processing virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
jan@jan-desktop:~$ sudo apt-get -f install

j d but i got ubuntu 7.04 not gutsy thank you

---

### Post by aysiu on 2007-10-29
```
Error parsing proxy URL http://:8080/: Invalid host name.
``` Sounds as if you have some kind of network configuration issue. I don't know much about proxy settings, unfortunately.

---

### Post by gb64 on 2007-10-29
You can go to the Virtualbox website and download the pckg for 7.04. It's still available. Then follow the rest of the instructions with the correct filename you downloaded. Or, you can get the right name, and edit the instructions and still use wget.

But, you still seem to have a proxy or network problem. Can't help on that.

Go to: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by bodhi.zazen on 2007-10-29
Innotec now maintains a repo for Virtual Box :

[http://doc.gwos.org/doku.php/doc:office:virtualbox#ubuntu_host](http://doc.gwos.org/doku.php/doc:office:virtualbox#ubuntu_host)

---

### Post by j d on 2007-11-04
solved thank you j d

---

