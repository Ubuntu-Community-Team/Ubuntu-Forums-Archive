---
title: "Create bootable iso from extracted files of linux Ubuntu"
date: 2014-11-13
forum: Virtualisation
---

### Post by jimmyh1972 on 2014-11-13
Hi
I have a folder containing files of some Ubuntu distro - the folder contains the following:  vmlinuz , initrd.img , isolinux.bin , boot.cat , isolinux.cfg
how can I create a bootable iso image to run it on a virtualBox?
I tried mkisofs but when i tested it on Vbox there was a message "no bootable medium found..."
thank's ahead
Jimmi

---

### Post by sudodus on 2014-11-13
You can compare with what there is in a full Ubuntu system on a CD/DVD/USB drive or in an ISO file. There are several more directories and files than those you listed.

Please tell us with more details what you want to do and why. That would make it easier to help you.

-o-

One way to create an ISO file for a boot CD/DVD/USB drive is to start with this link

[http://willhaley.com/blog/create-a-custom-debian-live-environment/](http://willhaley.com/blog/create-a-custom-debian-live-environment/) 

The following links show what can be made with it

[https://help.ubuntu.com/community/9w/Manual](https://help.ubuntu.com/community/9w/Manual)
[http://torios.org/](http://torios.org/)

It is also possible to use ***Remastersys*** or some fork of it (but I have not used Remastersys myself, so I don't know the details).

---

