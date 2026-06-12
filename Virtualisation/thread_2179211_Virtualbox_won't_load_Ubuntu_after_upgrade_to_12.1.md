---
title: "Virtualbox won't load Ubuntu after upgrade to 12.10"
date: 2013-10-07
forum: Virtualisation
---

### Post by BBB3000 on 2013-10-07
I have a dualboot setup with Windows 7 as my host CPU on Hard drive #1 and an Ubuntu partition on Hard drive #2. I installed VirtualBox (v4.2.18) on the Windows 7 OS and had everything working with this configuration. I decided to upgrade from Ubuntu 12.04 to 12.10 and that broke everything, starting with the boot loader. I believe the Grub --> Grub2 upgrade broke my boot loader. I was able to recover from this and I have both OSes booting individually. 

However, Virtualbox (run from Windows 7) does not work. The grub boot loader menu shows up, I select Ubuntu, and then I get black screen forever.

In order to get Ubuntu 12.04 to work with Virtualbox on Windows 7 I had to follow these steps:
[COLOR=#1155CC][FONT=Arial][U][http://merx3.wordpress.com/2012/08/29/booting-an-existing-ubuntu-instalation-from-virtualbox-while-using-windows/](http://merx3.wordpress.com/2012/08/29/booting-an-existing-ubuntu-instalation-from-virtualbox-while-using-windows/)
[http://www.neowin.net/forum/topic/784138-howto-boot-existing-ubuntu-partition-using-virtualbox-inside-windows/](http://www.neowin.net/forum/topic/784138-howto-boot-existing-ubuntu-partition-using-virtualbox-inside-windows/)
[/U][/FONT][/COLOR]

When I redid all of these steps from scratch after the Ubuntu 12.10 upgrade I was no longer able to boot. 

I also tried purging Virtualbox from my Ubuntu install and reinstalled it but that did not help. I also tried creating a new virtual machine. 

I have done a ton of research online and in the forums. Nothing seems to work. 

Any ideas?

---

### Post by BBB3000 on 2013-10-07
I have an update. I mentioned that the GNU Grub boot loader does appear. Well I have these options:

Ubuntu
Advanced options for Ubuntu

Under Advanced options for Ubuntu are the following:

Ubuntu, with Linux 3.5.0-41 generic
Ubuntu, with Linux 3.2.0-31 generic

If I select "Ubuntu, with Linux 3.2.0-31 generic" Ubuntu actually boots! However, it feels REALLY slow and says "Loading initial ramdisk" as it is booting. The 3.5 version however fails to load.

Am I close?

---

