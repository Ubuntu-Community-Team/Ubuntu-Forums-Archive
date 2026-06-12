---
title: "Ubuntu in VirtualBox is far from stable"
date: 2019-06-21
forum: Virtualisation
---

### Post by j2ee on 2019-06-21
I just try it for like an hour then already seeing some unstable stuff like the screen just freeze or lag for no reason. Not practical at all.

---

### Post by Claus7 on 2019-06-21
Hello,

sometimes things are not working so well in cases where the virtualbox version is old enough and the guest OS is pretty new. This is also a matter of hardware and how much resources you have allocated to each OS. Unfortunately, most of the latest OS are more resource hungry, especially if browsers are used at the same time. I was able to notice such behavior in low specs machine when browsers had more than a couple of tabs open.

Regards!

---

### Post by ajgreeny on 2019-06-21
It's more than a year since I tried Ubuntu with the gnome desktop in VBox but even when I did so it was fairly slow and not really very usable, largely, I believe because the gnome desktop requires more resources than VBox can manage easily.
I have found that the same is true of Cinnamon DE.

Have a look at something with a lighter DE, eg Ubuntu-mate or Xubuntu with xfce4, and you will probably find it works very well.

---

### Post by cruzer001 on 2019-06-21
> **j2ee said:**
> I just try it for like an hour then already seeing some unstable stuff like the screen just freeze or lag for no reason. Not practical at all.
Hold on here :)

Assign 2core and 3G of ram to your guest system.  Also do not turn on 3d.  
I currently have win10 hosting ubuntu and ubuntu hosting ubuntu.  Been working for me for years using vBox.

I forgot
Set video ram to 128M (thats the max).

---

### Post by TheFu on 2019-06-21
vbox on Windows is extremely stable, though slow when compared to other Linux-hosted hypervisors.
I found it unstable in 1 attempt on Linux, but that could have easily been my OS customizations causing the issues.  It did crash and take the entire hostOS down. Locked up hard.  But that was around 2010.  I switched to KVM + libvirt+virt-manager immediately after that issue. Using the exact same machine, KVM has been rock solid all these years.
Anyways, tune the vbox settings for best performance.  [https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) - yes, that is from 2012, but all the same settings and ideas still apply.

---

### Post by cruzer001 on 2019-06-21
I have to confess KVM is the ultimate way to go, but vBox will get the job done for the daily user.

TheFu has given you an excellent link.

---

