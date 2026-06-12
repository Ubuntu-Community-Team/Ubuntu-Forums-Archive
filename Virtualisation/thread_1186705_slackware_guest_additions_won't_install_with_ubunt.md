---
title: "slackware guest additions won't install with ubuntu 8.04 host"
date: 2009-06-13
forum: Virtualisation
---

### Post by Dustin2128 on 2009-06-13
when I drag the file into konsole, I get the following:```
virtualbox 2.2.4 guest additions installation
please install gnu make
please install the build and header files for your current linux kernel
.
The current kernel version is 2.6.27.7-smp
Please install the GNU compiler
This system does not seem to have support for OpenGL direct rendering.
VirtualBox requires linux 2.6.27 or later for this. Please see the log file /var/log/vboxadd-install.log if your guest uses linux 2.6.27 and you still see this message. 
Problems were found which would prevent the Guest Additions from installing. 
Please correct these problems and try again.
root@slack:~#
```

---

### Post by andrew.46 on 2009-06-13
Hi Dustin2128,

As I have mentioned on another thread it sounds like you have done a *partial* install of Slackware. The best and easiest way to install Slackware is to utilise the *full* option on installation when installing packages. The option left to you with your current installation is to pick out the required packages by using pkgtool as root but if it is early days in your installation I would advise reinstalling and using the full option.

BTW don't forget to run adduser and operate from this account rather than the root account.

All the best,

Andrew

---

### Post by Dustin2128 on 2009-06-13
I *did*use the full installation.....

---

### Post by Dustin2128 on 2009-06-13
oh well, it is in the "early days" of the install, so I'll check and see if I screwed up somewhere

---

