---
title: "VMware: how to install tools??!"
date: 2008-02-09
forum: Virtualisation
---

### Post by nikolas68 on 2008-02-09
....i'm very confused. I've been trying to install the tools for 2 days!
I've been following the directions from VMware wiki and the ones from our forum. Both of them they talk of a VMware tools installation virtual CD (never made one!) that should appear when i go to VM>Install VMware tools ....nothing appears...
AND WHERE is this VMware Tools TAR file??? If it was included in the originally downloaded file VMware-server-1.0.3-44356.tar.gz....then i've  deleted it.
any help??

---

### Post by csat on 2008-02-09
> **nikolas68 said:**
> ....i'm very confused. I've been trying to install the tools for 2 days!
I've been following the directions from VMware wiki and the ones from our forum. Both of them they talk of a VMware tools installation virtual CD (never made one!) that should appear when i go to VM>Install VMware tools ....nothing appears...
AND WHERE is this VMware Tools TAR file??? If it was included in the originally downloaded file VMware-server-1.0.3-44356.tar.gz....then i've  deleted it.
any help??

That's really tricky...  Without having any media cd or dvd into cd/dvd reader just click twice over cd/dvd address and it opens showing needed files so that you can copy to your /home folder and perform all tasks like untar and install.  I also spend several days until find how to open it LOL

---

### Post by nikolas68 on 2008-02-09
> **csat said:**
> That's really tricky...  Without having any media cd or dvd into cd/dvd reader just click twice over cd/dvd address and it opens showing needed files so that you can copy to your /home folder and perform all tasks like untar and install.  I also spend several days until find how to open it LOL


...my brain is fuming....where is the cd/dvd addresses that i should click twice??

---

### Post by nikolas68 on 2008-02-09
....can't find the cd/dvd addresses....

---

### Post by csat on 2008-02-09
> **nikolas68 said:**
> ....can't find the cd/dvd addresses....

You start VMware and put your application to run too.  Click both control + alt keyboard to change your cursor and go top screen at the vmware tools menu.  There ask it to install vmware tools.  It simply seems not be done anything but it had in fact.  Try find your /media/cdrom using Nautilus and click on it or it is shown on your desktop.

I am writing this by heart since not using VMware anymore but that is the way you should look for it.  When this virtual cd/dvd is opened you should copy two files into a folder located in your /home/user.  There will be two files.  One is tar.gz and other I guess is rpm that you'll not use.

So.  The tricky action is this only works if your application is also running.

---

### Post by popch on 2008-02-10
.. in other words:

While the virtual machine is running where you want the tools installed, use the menu*** Virtual Machine / Install VMWare tools*** (or similar; I am not at the machine which has VMWare installed).

This will mount a 'virtual CD' in the CD drive of your virtual machine.

Go into your virtual machine. When running Windows in the VM, you ought to find the mounted virtual CD in ***my Computer***. When running Linux, it depends on your distribution where newly mounted CDs are shown.

And it will only work if there is a virtual CD drive defined for your virtual machine.

---

### Post by csat on 2008-02-10
> **popch said:**
> .. in other words:

While the virtual machine is running where you want the tools installed, use the menu*** Virtual Machine / Install VMWare tools*** (or similar; I am not at the machine which has VMWare installed).

This will mount a 'virtual CD' in the CD drive of your virtual machine.

Go into your virtual machine. When running Windows in the VM, you ought to find the mounted virtual CD in ***my Computer***. When running Linux, it depends on your distribution where newly mounted CDs are shown.

And it will only work if there is a virtual CD drive defined for your virtual machine.

Thanks for giving another view solution!

---

