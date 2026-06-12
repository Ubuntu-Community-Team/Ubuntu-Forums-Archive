---
title: "Vbox install problem"
date: 2007-11-29
forum: Virtualisation
---

### Post by boxer1028 on 2007-11-29
I am new to ubuntu. Just installed 7.10 on my server, witch i am using as my desktop. I am trying to install vbox so i can integrate a virtual OS (xp). The download name is 'virtualbox_1.5.2-25...ntu_gutsy_i386.deb'. Once download is complete the package installer reads "error: Dependency is not satisfiable:libqt3-mt". I went to the debian page and downloaded some  packages. So far I have downloaded 'libqt-mt_3.3.3.7-4_i386.deb' & 'libaudio2_1.8-4_i386.deb'. Even after these packages are installed I still receive the vbox error when trying to install. What can I do?

Dell PowerEdge 1300 | pentinium III | 32bit

---

### Post by OmahaVike on 2007-11-29
have you tried to pop open a terminal and type this in?

```

sudo apt-get install libqt3-mt

```

---

### Post by jba6511 on 2007-11-29
virtualbox is also in the repositories although it has no usb support. Could always try installing this way using synaptic so that ubuntu will manage the dependencies for you.

---

### Post by dirkdekker on 2007-12-01
Hi, just a question about your installation:
Where did you find the installation software for the poweredge like drivers etcetera??

---

### Post by gb64 on 2007-12-01
If you go to the VirtualBox website and get the line for the repository, you can add that to your Synaptic repositories or /etc/apt/sources.list. For example, using 7.10, you would use the line :  
**deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free**
Also, download the innotek public key for apt-secure  from the same page and add to the Certificate page in Synaptic. If you mark the repository checked, each time you reload Synaptic it will be aware of the latest VirtualBox. You can download and install just like any other package.
In addition, that package, unlike the separate OSE version, does support USB. You may need to do some reading to properly use USB.

---

### Post by boxer1028 on 2007-12-01
Hi DirkDekker, I whent to debians website and downloaded it. Why do you ask?

---

