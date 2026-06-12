---
title: "how to install vmware on ubuntu 12.04"
date: 2012-09-29
forum: Virtualisation
---

### Post by syednasirraza on 2012-09-29
hi
plz guide in detail how can i install vmware on my laptop-ubuntu 12.04..
which vmware version is recomended for it.
can sum1 provide link to donwload vmware source
and installation guide/steps to follow for installation
PLZ GUIDE IN DETAIL AS I M TOTALLY NEW TO LINUX AND DONT KNOW MUCH ABOUT VMWARE

---

### Post by daslinkard on 2012-10-05
Maybe this [tutorial]("http://*********************.com/2012/06/08/how-to-install-vmware-player-in-ubuntu-12-04/") can help you get started....

---

### Post by jingaling on 2012-10-05
For a noob I would recommend VirtualBox over VMware in Ubuntu. It's available in the Ubuntu software centre, just search for it and click install.

We can literally write a book on VM's so it's not really viable to give you a detailed guide on VM's, how they work and how to set them up. I would recommend you look at the VirtualBox wiki, particularly the end user docs (link below) that should get you started.

[https://www.virtualbox.org/wiki/End-user_documentation](https://www.virtualbox.org/wiki/End-user_documentation)

However, if you have a specific requirement please let us know and I'm sure we will be able to help somehow. Asking wild blanket questions on how to use something like VM's isn't really viable though. We need specifics :)

---

### Post by daslinkard on 2012-10-05
Refugegeek....just want to say....nice pic....I love the coffee cup!!

---

### Post by jingaling on 2012-10-05
Ha ha thanks daslinkard

---

### Post by syednasirraza on 2012-10-11
thanks alot jinglaing for to the point guidance..... i have got it installed from software centre....
the only query still left is why it was saying when i was  trying to download/install that::::
**The action would require the installation of packages from not authenticated sources**.............
although when i tried a couple of times,, and clicked **repair **button,,, it allowed me to install....
secondly , my requirement was just to learn using vmware know how initially and then i want to install different OS onto for learning, like RHEL, and Windows.... still i dont know if i m messing up here by adding my questions or should i generate a new thread for this...since i have no idea on next how to install e.g red hat linux on it,,, where from to get source for that,, etc etc

---

### Post by newb85 on 2012-10-11
Well, before you can install an OS, you must first create a machine in Virtualbox to run it on.

If you click the "New" button, it will run a wizard for setting up the machine.  At the second step, you have to input the name and OS type.  Beyond that, the defaults will probably suffice.  Before running the new machine, though, you will probably want to click the settings on the right side of the main window and adjust the RAM, graphics memory, CPU, etc.  (The defaults are rather meager for modern OSes.)

When you first run the machine, it will ask for install media, and by default it will select your host machine's CD drive (assuming you have one).  Alternatively, you may simply choose a .iso file you have on the HD.

Beyond that, it should be pretty much the same as installing on a real machine.

---

### Post by newb85 on 2012-10-11
By the way, Red Hat is an enterprise OS.  You have to register (and maybe even pay...) to download it.

The non-enterprise version would be Fedora.
[http://fedoraproject.org/]("http://fedoraproject.org/")

---

### Post by nothingspecial on 2012-10-12
*Thread moved to **Virtualisation**.*

---

### Post by CaptainCat on 2013-04-16
How long does the process usually take when you create a new virtual machine? I have been stuck at 0% for around a half an hour when creating a windows 8 device.

---

