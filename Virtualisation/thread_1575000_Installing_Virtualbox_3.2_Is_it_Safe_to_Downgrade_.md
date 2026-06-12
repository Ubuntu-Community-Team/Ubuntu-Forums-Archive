---
title: "Installing Virtualbox 3.2: Is it Safe to Downgrade Certain Qt packages?"
date: 2010-09-15
forum: Virtualisation
---

### Post by navneeth on 2010-09-15
Hi. I want to install the PUEL version of Virtualbox on Lucid. I added their repo, although when I try to install it APT throws some dependency issues up at me.

```
navneeth@home:~$ sudo apt-get install virtualbox-3.2 dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-3.2: Depends: libqt4-opengl (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

```

Now, this error has been reported umpteen times on the Internet, as a search for *virtualbox libqt4-opengl ubuntu* would show. The problem is, I have not found a solution in any of those threads so far. However, I did find someone somewhere mention that using **aptitude** instead of **apt-get** solved the problem for him. Here's what I get when I use aptitude

```
navneeth@home:~$ sudo aptitude install virtualbox-3.2 dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  libqt4-opengl 
The following NEW packages will be installed:
  dkms virtualbox-3.2 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.9MB of archives. After unpacking 98.6MB will be used.
The following packages have unmet dependencies:
  libqt4-opengl: Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 is installed.
                 Depends: libqtgui4 (= 4:4.6.2-0ubuntu5) but 4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 is installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
libqt4-dbus [4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 (now) -> 4:4.6.2-0ubuntu5 (lucid)]
libqt4-network [4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 (now) -> 4:4.6.2-0ubuntu5 (lucid)]
libqt4-xml [4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 (now) -> 4:4.6.2-0ubuntu5 (lucid)]
libqtcore4 [4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 (now) -> 4:4.6.2-0ubuntu5 (lucid)]
libqtgui4 [4:4.7.0~beta1+git20100522-0ubuntu1~lucid1~ppa1+appmenu20100722 (now) -> 4:4.6.2-0ubuntu5 (lucid)]

Score is -100

Accept this solution? [Y/n/q/?]  

```


I would like to know if it is safe to proceed with this way of installing VirtualBox? Will downgrading to the stable versions of those library files cause any problem? How can I find out if some important software component or application is dependant on those beta versions (without actually downgrading, of course)?

Any and all help will be appreciated.

---

### Post by navneeth on 2010-09-15
Well, never mind. I searched about the beta packages and I think they were remnants from the time I tried Unity for a short while -- a really short while. Anyway, using aptitude installed Vbox without a hitch and my system seems all right.

---

### Post by albatroz2k on 2010-10-04
I am also getting the following error messages when running
this command: sudo apt-get install virtualbox-3.2
In summary, I can´t install virtualbox.org

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8 is to be installed
E: Broken packages

> **navneeth said:**
> Well, never mind. I searched about the beta packages and I think they were remnants from the time I tried Unity for a short while -- a really short while. Anyway, using aptitude installed Vbox without a hitch and my system seems all right.

---

### Post by navneeth on 2010-10-04
Did you try using **aptitude** instead of **apt-get**?

---

