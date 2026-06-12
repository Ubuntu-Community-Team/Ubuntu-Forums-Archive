---
title: "problem with sharing my hard drive with vbox"
date: 2008-05-15
forum: Virtualisation
---

### Post by Zidoud on 2008-05-15
I recently upgraded to linux 8.04 and i am having trouble trying to get my hard drive to share with my vbox. help please.

---

### Post by Zidoud on 2008-05-16
sorry let me a little more informative, i installed the file sharing program from the add/remove programs tab but if i dont have internet then it doesnt work. how can i fix it. thank you for all help!

---

### Post by bodhi.zazen on 2008-05-16
You need to either setup internet access with virtualbox and then use a network share prototcol (samba, NFS, FTP, http ...), share a usb device, or install the guest additions and use a shared folder. This second option is on available on the open source addition.

[http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/](http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/)

---

### Post by rune0077 on 2008-05-16
Far the easiest way is to just install the guest edition, then go to the settings of your virtual-system, go to Shared Folders, click the add-button and select the folder you want to share.

---

### Post by Zidoud on 2008-05-26
Cool thank you very much! I still have a problem though when i go to read stuff on my external hard drive(Western Digital) i cant view that it is pluged in on my vbox but i can see it in linux. the only way i can see any of the files is to take the file out of the hard drive and put it in the shared folder? The vbox dies recognize my usb mouse though!

---

