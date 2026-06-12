---
title: "Virtualbox OSE Won't Install"
date: 2008-08-06
forum: Virtualisation
---

### Post by kevin11951 on 2008-08-06
if i follow the tutorial here: [https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy](https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy)) 

im running ubuntu 8.04.1 32bit

i get as far as the first command and then:

```
ksoviero@ksoviero-laptop:~$ sudo apt-get install -f virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages
ksoviero@ksoviero-laptop:~$ 
```

---

### Post by Elfy on 2008-08-06
I'm guessing that it still in proposed, I think that the -20 kernel still is. You know that USB support is in the PUEL version and not OSE - just checking :)

---

### Post by jblackhall on 2008-08-06
I believe this is probably because there is some sort of update to virtualbox-ose that's been building (or something) in the repositories.  Since I've already got it installed, an update shows up in my Update Manager, but it's greyed out and not selectable.  My suggestion would be to wait a day or 2 and try again.  Hopefully by that point the updated package will have finished building (or whatever's going on) and you'll be able to install it just like you tried to.  

As the previous poster stated, you can also get virtualbox PUEL (personal use and evaluation license) if you want USB support.  That one isn't available in the repos but is available through the VBox website.

If it's something you can't wait a few days for, then I'd suggest grabbing the newest PUEL version.  It should work fine.  Well, unless you're trying to boot the Intrepid kernel, heh.

---

### Post by Victormd on 2008-08-06
Go with the PUEL, you can download it from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). It's very straight forward to install, simply download, double-click and you're done...

---

### Post by wolfen69 on 2008-08-06
try
```
sudo apt-get install -f
```
also, do you have all repos enabled?

---

### Post by svaens on 2008-08-07
I also have this problem at the moment. 
As far as I can tell, yes, virtualbox has been built with 
2.6.24-20-generic
which is not yet available on the repo. 

I wonder how I can get my hands on an older version of virtualbox from the repository ?? This would solve it, until the new kernel is released for us.

---

### Post by Aetherius on 2008-08-07
i had a similar issue, apt-get install -f (as stated above) fixed it just fine.

Switched to the non-free version of VBox anyway, easier usb support :)

---

### Post by dje on 2008-08-07
great guide [here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html"), it's *always* worked for me, use the PUEL version as it has USB support and other features unless you specifically want the open source one ;)

dje

---

### Post by Elfy on 2008-08-07
> use the puel version as it has usb support and other features unless you specifically want the open source one+1

---

### Post by kevin11951 on 2008-08-07
FIXED IT!!! i manually installed virtualbox-ose-modules-2.6.24-19-generic through synaptic, and it worked! 

i did want the open source version specifically btw.

---

