---
title: "Need help with Virtualbox"
date: 2008-07-19
forum: Virtualisation
---

### Post by wsamh on 2008-07-19
I'm trying to install Virtualbox on ubuntu, and I keep getting this when I'm trying to start a virtua machine.


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

---

### Post by balaknair on 2008-07-19
Open a terminal and use this command to give your user access to the VirtualBox kernel.

sudo adduser $USER vboxusers

(replace USER with your user name)
Log out and log in again to update group membership.

For more tips, tweaks and fixes(or if you're using a version of Ubuntu other than Hardy Heron(8.04) try this page
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by wsamh on 2008-07-19
It did not work. It said "The group `vboxusers' already exists."

---

### Post by balaknair on 2008-07-19
I'm not sure just what went wrong there, but what the command posted above should do is add you as a user to the group vboxusers(which of course already exists since it's created when virtualbox is installed). 

Other commands which do the same thing

sudo gpasswd -a `whoami` vboxusers
or
sudo usermod -Gvboxusers -a `whoami`
or
sudo adduser $USER vboxusers

Taken from [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I suggest you refer to this page, it's got pretty detailed instructions on both installing and using VirtualBox.

Hope this is helpful.
All the best.

---

### Post by Vitamin-Carrot on 2008-07-19
Wot version if VB are you running ... you might want to grab the 1.6.2 deb from the website

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

if your running 8.04 there is a common issue where the vb available in the repos wont work after a kernel update

---

### Post by flytripper on 2008-07-19
alternatively add yourself to vboxusers using the gui system>admin>users and groups

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-07-29
Thank you balaknair it works, that fix my problem and I add my User to the Vboxusergroup! :D

Thanks!

---

