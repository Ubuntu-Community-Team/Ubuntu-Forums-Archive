---
title: "Installing Qt/Embedded on Ubuntu 9.04 64-bit"
date: 2009-07-30
forum: Ubuntu Dev Link Forum
---

### Post by Menyus on 2009-07-30
Need help with completing the installation and running of Qt for Embedded Linux 4.5.2. Following the instructions in INSTALL, I completed the building, make and make-install steps for the ARM architecture but I am stuck on step 4, Environment variables.

First, my question is, where is the .profile file where I'm supposed to extend/export the PATH variable?

Second, when I try to run the demos and examples, I get a bunch of "Failure to open ..." messages and "Cannot access directory ..." warnings, and the build process terminates with the following error message in red:

Exited with code 5.
Error while building project examples
When executing build step 'QMake'

Any help is appreciated,

---

### Post by stulluk on 2009-08-28
> **Menyus said:**
> Need help with completing the installation and running of Qt for Embedded Linux 4.5.2. Following the instructions in INSTALL, I completed the building, make and make-install steps for the ARM architecture but I am stuck on step 4, Environment variables.
 
First, my question is, where is the .profile file where I'm supposed to extend/export the PATH variable?
 
Second, when I try to run the demos and examples, I get a bunch of "Failure to open ..." messages and "Cannot access directory ..." warnings, and the build process terminates with the following error message in red:
 
Exited with code 5.
Error while building project examples
When executing build step 'QMake'
 
Any help is appreciated,
 
Hi, I am experiencing the same problems on jaunty 32 bit.
 
First of all, the ".profile" file is in your home folder ( or if you login as root, it is in the "root" folder )
 
So, you may edit it in 2 way:
 
gedit /home/.profile
 
or
 
gedit /root/.profile
 
Secondly, I stuck in exactly same point with you. After ./configure, make, and make install sequence, I got "/dev/fb0 : no such device" error. This means that, our framebuffer is not installed correctly...
 
I am still investigating why it does not install correctly, but I think I will gonna find it..
 
Regards

---

