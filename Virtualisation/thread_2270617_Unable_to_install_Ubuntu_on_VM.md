---
title: "Unable to install Ubuntu on VM"
date: 2015-03-24
forum: Virtualisation
---

### Post by satimis on 2015-03-24
Hi all

Host - Ubuntun 14.04 64bit
VM to be installed - ubuntu 14.04 64bit
VirtualBox

Settings
Controller IDE -> ubuntu-14.04.2-desktop-amd64.iso

Start -> I can select "Language"
-> either clicking "Try Ubuntu without installing" or "Install Ubuntu" it died automatically after a while.

I have tried the whole afternoon without a breakthrough.  Also I have checked md5sum

Pls help.  Thanks

Regards
satimis

---

### Post by TheFu on 2015-03-25
Follow the instructions at virtualbox.org to 
* get the current Oracle .deb file - [http://askubuntu.com/questions/540829/how-to-install-virtualbox-on-ubuntu-14-04](http://askubuntu.com/questions/540829/how-to-install-virtualbox-on-ubuntu-14-04)
* setup the correct userids and groupids if the installation above doesn't automatically
then make a new VM with good performance settings following this: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

Lots of others have asked the same question in this sub-forum here. More detailed answers are there.

---

### Post by satimis on 2015-03-26
> **TheFu said:**
> Follow the instructions at virtualbox.org to 
* get the current Oracle .deb file - [http://askubuntu.com/questions/540829/how-to-install-virtualbox-on-ubuntu-14-04](http://askubuntu.com/questions/540829/how-to-install-virtualbox-on-ubuntu-14-04)
* setup the correct userids and groupids if the installation above doesn't automatically
then make a new VM with good performance settings following this: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

Lots of others have asked the same question in this sub-forum here. More detailed answers are there.
Hi,

Thanks for your advice and links.

Problem solved after upgrading to the extension pack on;
[http://download.virtualbox.org/virtualbox/4.3.26/Oracle_VM_VirtualBox_Extension_Pack-4.3.26-98988.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.26/Oracle_VM_VirtualBox_Extension_Pack-4.3.26-98988.vbox-extpack)

Regards
satimis

---

### Post by TheFu on 2015-03-26
Thanks for changing the thread title to (SOLVED), but please use the "Thread Tools" at the top to mark the entire thread that way. It will show up in the list better that way.

---

