---
title: "Unable to install virtualbox additions on Ubuntu Mate"
date: 2016-12-01
forum: Virtualisation
---

### Post by peter1897 on 2016-12-01
I installed Ubuntu Mate 14.04.2 x32 on virtualbox but i am not able to install the guest addition. I copy vboxlinuxadditions.run to the home folder and run it but i get 'Building the main Guest Additions module &#8230;fail!'. How to install the additions?

---

### Post by peter1897 on 2016-12-01
In the log file there are these two lines but i don't know what they mean:
```
/opt/VBoxGuestAdditions-5.0.30/src/vboxguest-5.0.30/build_in_tmp: 62: 
/opt/VBoxGuestAdditions-5.0.30/src/vboxguest-5.0.30/build_in_tmp: make: not found
```

---

### Post by peter1897 on 2016-12-01
I installed 'make' and 'gcc' and was able to install the additions. I guess that was the problem, though some items on the top and bottom panes appear displaced.

---

### Post by SeijiSensei on 2016-12-01
The guest additions compile some modules from source so you need to have the gcc compiler available.  Try running "sudo apt-get install build-essential" then see if the modules install for you.

---

### Post by peter1897 on 2016-12-01
Thanks, i installed the build-essentials.
Do i have to run other commands like: virtualbox-guest-x11, virtualbox-guest-dkms, virtualbox-guest-utils, or it is not necessary?

---

### Post by SeijiSensei on 2016-12-02
I can't help with that because I don't use the version of VirtualBox that ships with Ubuntu.  Instead I use Oracle's own repository via the method described here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

