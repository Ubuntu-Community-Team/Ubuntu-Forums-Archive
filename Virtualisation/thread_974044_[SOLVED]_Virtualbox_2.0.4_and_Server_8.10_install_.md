---
title: "[SOLVED] Virtualbox 2.0.4 and Server 8.10 install problems"
date: 2008-11-07
forum: Virtualisation
---

### Post by borpin on 2008-11-07
Hi,

Trying to install Virtualbox 2.0.4 on a fresh install of 8.10 server.  Had a few bad starts but now cannot recomplie the kernel as there is no source.

In detail.
Updated the source for the virtualbox package as per [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and then 
tried to install virtualbox using aptitude. Of course what I actually wanted was to do was 'sudo aptitude install virtualbox-2.0'.

So I now have 2.0.4 installed, but I have an error in that DKMS cannot find the source for kernel 2.6.27-7-server in order (I think) to compile the vboxdrv.  Any ideas how to fix this?

Cheers

---

### Post by remy06 on 2008-11-07
hi

i just managed to get virtualbox installed on my intrepid.
I downloaded from sun the package and ran the deb installer,encountered some errors so I ran
```
sudo apt-get -f install
```

it will download some other files and continue with the installation after that.the wizard will also prompt if u want to compile the kernel for virtualbox.

After that everything seems to be fine.Can open virtualbox except it unable to access usb subsystem error.

---

### Post by borpin on 2008-11-10
OK solved it by starting from scratch with a fresh install of 8.10 and installing virtualbox-2.0 first time.  I not sun have intrepid disto now anyway.

Cheers

---

