---
title: "virtualbox mouse capture dies on 9.04 64."
date: 2009-06-03
forum: Virtualisation
---

### Post by extendedping on 2009-06-03
Hi all new user (first day ubuntu) here. love everything but I wanted to use virtual box to keep my centos (redhat) very basic skills up to date. anyway I am running 9.04 64 bit version and took the virtualbox and virtualbox guest additions packages from the apt repo. I tested my centos 5.3 disk then fired it up and itstalled it with no issues. I gave it almost a gig of memory. installed the guest additions and mouse was working seamlessly. unfortunately after bout 5 minutes the mouse simply does not work at all any more in centos. I tried rebooting the vm multiple times, and its always the same. works for bout 5 minutes then stops. also I reinstalled centos into virtual box a second time. any guidance would be greatly appreciated. the strange thing is each time I bring the vm up it works fine for a few minutes...I have checked it bout 10 times total. btw virtual box worked fine on fedora 10 running centos 5.3 installed from the same media.

---

### Post by Gausian on 2009-06-03
does the right-Ctrl button bring it back?

---

### Post by extendedping on 2009-06-03
no, I can toggle it back and forth (green to grey) and hovering the mouse over desktop items shades them but I cannot capture. it happened again just tested. only this time it never captured where before it did for like 5 minutes. I guess I am dropping virtualbox and trying vmware though I hated their web interface.

---

### Post by extendedping on 2009-06-03
suggestions apart from dumping virtual box?

---

### Post by extendedping on 2009-06-08
k guess I will read up on qemu and then if that does not work I am back to being a fedora user since all visualization stuff worked there. would be a shame as since they took away the root login its basically a ubuntu copy now anyway but I do need to run multiple machines hassle free :(

---

### Post by axel206 on 2009-06-08
Which version of Virtualbox are you using?

Also check this guide:
[How to fix mouse pointer integration in Ubuntu 9.04 installed on VirtualBox](http://www.my-guides.net/en/content/view/157/26/)

---

### Post by bodhi.zazen on 2009-06-08
That sounds odd. Mouse integration is working for me.

Host Fedora 11
Guests - all, including Ubuntu 8.10, 9.04, and 9.10 (alpha).

Did you install the VirtualBox Additions in the guest ? Are you on the latest version of virtualbox (from the Sun site) and are your guests up to date ?

---

### Post by extendedping on 2009-06-10
> **bodhi.zazen said:**
> That sounds odd. Mouse integration is working for me.

Host Fedora 11
Guests - all, including Ubuntu 8.10, 9.04, and 9.10 (alpha).

Did you install the VirtualBox Additions in the guest ? Are you on the latest version of virtualbox (from the Sun site) and are your guests up to date ?

yes I took the additions, I also did a complete reinstall of ubuntu and this time took the vbox from sun's site (the "proprietary" one this time) and after bout a half hour working on centos 5.3 and after which was all yum updated, it just froze again. after working for at least a half hour. btw after knocking down ubuntu I went back to fedroa (this time v 11) and have to say I could not stick with it. oh my system just stopped booting yesterday for no reason I could see (black screen not even giving the opportunity to go to single mode) so I am definitely away from that crap system for good. now I just need to understand what other options ubuntu offers (xen qemu etc) cause I really don't understand that stuff. oh well time to start reading. hey don't mind if I call the product from now on virtuallox. thats about what it is good for as far as I'm concerned.

---

### Post by extendedping on 2009-06-11
well I got kvm working with the graphical virt-manager, I had to log into the desktop as root to get that working no sudo virt-manager or su - virtmanager would allow the machine to be networked. bye bye fedora bye bye virtualbox. oh the install of the centos guest is considerably faster on kvm then on virtualbox, that I noticed immediately.

---

