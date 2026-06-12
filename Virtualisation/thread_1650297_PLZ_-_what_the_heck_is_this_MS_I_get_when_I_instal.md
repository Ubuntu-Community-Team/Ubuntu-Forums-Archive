---
title: "PLZ - what the heck is this MS I get when I install vmware workstation 7 ???!!!"
date: 2010-12-21
forum: Virtualisation
---

### Post by Objectivity on 2010-12-21
[SOLVED] Hi folks, I installed vmware work station and on final step which was >> &quot; BEFORE YOU CAN RUN VMWARE, SEVERAL MODULES MUST BE COMPILES AND LOADED INTO THE RUNNNG KERNEL &quot; I click on &quot; INSTALL &quot; and then got this DAMN error : Unable to build kernel module. See log file /tmp/vmware-root/setup-15968.log for details. I HATE IT ! I remember on windows it was easy just 2 clicks ! here seems over 40000 clicks. Please help.

---

### Post by bodhi.zazen on 2010-12-21
Do tell, what is in the log file (what error message) ?

It really does not help to compare to Windows as this results in flame wars.

---

### Post by Objectivity on 2010-12-22
> **bodhi.zazen said:**
> Do tell, what is in the log file (what error message) ?

It really does not help to compare to Windows as this results in flame wars.

   HI ! Bodhi ... it is you again :- )  You are indeed active here.   Forget about it ! I installed VIRTUAL BOX instead and works fantastic. I think it even works better than vmware.     By the way, the only think I would like to know is this :   HOW can I clone my xp in it ?  I installed xp in it and would like to clone it and use the clone one instead.  On vmware was easy ! here a bit confusing. On vmware I had an option to go with FULL CLONE ! here I don;t see such option.   Regards,  Objectivity:-({|=

---

### Post by Objectivity on 2010-12-22
> **bodhi.zazen said:**
> Do tell, what is in the log file (what error message) ?

It really does not help to compare to Windows as this results in flame wars.


 Budi ...

 Let me REINSTALL vmware and give the error log ! BECAUSE it would be helpful to others.

 I remember I did search on google about my problem and could not fine anything regarding this. So, it would be nice if we address that.

 I will get back to you as soon as I install vmware.

---

### Post by NightwishFan on 2010-12-22
It would help if you compressed said log to .tar.gz, and posted here for us helper drones to peruse and perhaps aid you in your plight. I too recommend Virtualbox though have no idea how to clone images.

Virtualbox has to compile as well to work so obviously you have headers and dkms compiled and working. Perhaps for the vmware image you need certain development files or the build-essential. Linux has many different versions and is different by design, and thus requires to compile modules and drivers. It is no problem when done nearly transparently like virtualbox and Nvida.

---

### Post by Objectivity on 2010-12-22
> **bodhi.zazen said:**
> Do tell, what is in the log file (what error message) ?

It really does not help to compare to Windows as this results in flame wars.

 ok here it is ... the log file ...

 Dec 22 08:13:39.713: app-139729608242944| Log for VMware Workstation pid=3554 version=7.0.1 build=build-227600 option=Release
Dec 22 08:13:39.713: app-139729608242944| The process is 64-bit.
Dec 22 08:13:39.713: app-139729608242944| Host codepage=UTF-8 encoding=UTF-8
Dec 22 08:13:39.713: app-139729608242944| Logging to /tmp/vmware-root/setup-3554.log
Dec 22 08:13:39.823: app-139729608242944| modconf query interface initialized
Dec 22 08:13:39.824: app-139729608242944| modconf library initialized
Dec 22 08:13:39.840: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.843: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.847: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.854: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.859: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.876: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.878: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.879: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.881: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.883: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.891: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.892: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.893: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.895: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.896: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.898: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.903: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.921: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.922: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.924: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.925: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.926: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.928: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.933: app-139729608242944| Your GCC version: 4.4
Dec 22 08:13:39.955: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.956: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.958: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.959: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:39.960: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:40.175: app-139729608242944| Trying to find a suitable PBM set for kernel 2.6.35-23-generic.
Dec 22 08:13:40.175: app-139729608242944| Building module vmmon.
Dec 22 08:13:40.175: app-139729608242944| Extracting the sources of the vmmon module.
Dec 22 08:13:40.182: app-139729608242944| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Dec 22 08:13:41.856: app-139729608242944| Failed to compile module vmmon!

---

### Post by bodhi.zazen on 2010-12-22
VMWare is always interesting to try to install, which is why many people are migrating to VBox or KVM.

At any rate, you can try this :

[http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/](http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/)

You could also try posting to the VMWare mailing list or forums (it they have one).

---

### Post by Objectivity on 2010-12-22
> **bodhi.zazen said:**
> VMWare is always interesting to try to install, which is why many people are migrating to VBox or KVM.

At any rate, you can try this :

[http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/](http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/)

You could also try posting to the VMWare mailing list or forums (it they have one).


 Thank you Budhi. I will try this now and see what happens ...

 YEAH ! Vbox was SO SO SO easy to install indeed and works just as good as vmware. The only thing I am trying to figure out is how to clone.  YOU ROCK .=D>

---

### Post by Objectivity on 2010-12-22
> **bodhi.zazen said:**
> VMWare is always interesting to try to install, which is why many people are migrating to VBox or KVM.

At any rate, you can try this :

[http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/](http://pario.no/2010/10/02/installing-vmware-workstation-7-1-1-64-bit-on-ubuntu-10-10/)

You could also try posting to the VMWare mailing list or forums (it they have one).


 ((( WOW YOUR LINK WORKED ))) 

I will post the whole thing in here in case that link removed ...

This is what I did accordion to that link ...

In Terminal  I typed :

 cd /tmp
 wget [http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash](http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash)
 sudo chmod +x vmware7.1.1-patch-kernel-2.6.35.bash
 sudo ./vmware7.1.1-patch-kernel-2.6.35.bas

then ...

sudo vmware-modconfig --console --install-all

DONE.

My Vmware worksation version number is :

VMware-Workstation-Full-7.0.1-227600.x86_64

It is 64 bit version for my 64 bit Ubuntu You are using Ubuntu 11.04
                - the Natty Narwhal - released in April 2011 and supported until October 2012.


\\:D/

---

