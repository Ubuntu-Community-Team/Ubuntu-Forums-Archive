---
title: "Teamviewer 12.0.x on Ubuntu Gnome 17.04"
date: 2017-04-14
forum: Ubuntu Development Version
---

### Post by macu on 2017-04-14
Hi, I cannot install teamviewer 12.0.x on Ubuntu Gnome 17.04 (not upgrading, clean install). I wanted to use gdebi to install it like in another versions and dependences on libc6:i386 cannot allowed to install that. When i want to install it i get this messages:

```

sudo apt install -y libc6:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cpu-checker : Depends: msr-tools but it is not going to be installed
 libc6 : Breaks: libc6:i386 (!= 2.24-9ubuntu2) but 2.24-7ubuntu2 is to be installed
 libc6:i386 : Depends: libgcc1:i386 but it is not going to be installed
              Breaks: libc6 (!= 2.24-7ubuntu2) but 2.24-9ubuntu2 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

---

### Post by Paddy Landau on 2017-04-14
Do you have 32-bit or 64-bit?

I downloaded version 12.0.76279 onto a reasonably fresh 17.04 (64-bit). Right-click > install (I used Gdebi).

It automatically installed 32 dependencies and completed successfully, and I was able to run TeamViewer without a hitch. I didn't have to install anything extra.

Do you want to try doing what I did?

---

### Post by macu on 2017-04-14
Hi, of course, I have 64bit Ubuntu Gnome 17.04....i have downloaded teamviewer_12.0.76279_i386.deb (from teamviewer web site - there is written, that it is multirich...so I belive that what there is written). 
Do you have Ubuntu or Ubuntu Gnome? Because it seams it is problem with Ubuntu Gnome dependences, i looked into synaptic and i can see, i have libc6 installed....but when i want to install teamviewer (or skype 4.3.x) from Canonical partner repository, it writes missing dependences libc6:i386.

edit: so thx for "kick me"....I just have reinstalled libc6 in synaptic and voila...it works...I have TV installed and it's working correctly...:) thx :)

---

### Post by Paddy Landau on 2017-04-14
Cool, glad that you got it working :)

---

### Post by izznogooood on 2017-04-15
I was going tu suggest a "sudo apt -f install"

---

