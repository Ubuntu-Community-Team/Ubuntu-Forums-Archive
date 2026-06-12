---
title: "can't install synaptic in hoary"
date: 2005-04-03
forum: Repositories &amp; Backports
---

### Post by paulle on 2005-04-03
i can't install synaptic in hoary.
every time i tried it, i get the following message:

root@yoyo:/home/chris # apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstabledistribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely thatthe package is simply not installable and a bug report againstthat package should be filed.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-5-3.3 but it is not installableE: Broken packages

any ideas? :confused:

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=paulle]i can't install synaptic in hoary.
every time i tried it, i get the following message:

root@yoyo:/home/chris # apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstabledistribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely thatthe package is simply not installable and a bug report againstthat package should be filed.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-5-3.3 but it is not installableE: Broken packages

any ideas? :confused:[/QUOTE]
 synaptic is installed by default so this is the response you should have : 

sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So you're having an dependies issue. You could try to figure it out on your own. But first let's try the easy way :

sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntu-base ubuntu-desktop
sudo apt-get dist-upgrade

---

### Post by paulle on 2005-04-03
i tried it out, but it doesn' work.
here is my output:

root@yoyo:/home/chris # apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@yoyo:/home/chris # apt-get install ubuntu-base
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-base has no installation candidate
root@yoyo:/home/chris # apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-base has no installation candidate

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=paulle]i tried it out, but it doesn' work.
here is my output:

root@yoyo:/home/chris # apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@yoyo:/home/chris # apt-get install ubuntu-base
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-base has no installation candidate
root@yoyo:/home/chris # apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-base is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-base has no installation candidate[/QUOTE]
 that means you have a wrong sources.list .. replace/change it

---

### Post by paulle on 2005-04-03
here is my sources.list. it worked before and i can't find out what's wrong with it.

 #############Ubuntu Hoary##############
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

##############Backports ##############
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras universe
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras multiverse
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras restricted
# deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
# deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

---

### Post by ubuntu_demon on 2005-04-03
1) you are missing (hoary) main
2) you have already uncommented hoary-updates
3)If you have used this repository to upgrade from warty to hoary you are now running warty and hoary mixed.

add main, uncomment hoary-updates and :

sudo apt-get update
sudo apt-get install -f
sudo apt-get install ubuntu-base ubuntu-desktop
sudo apt-get dist-upgrade

---

### Post by paulle on 2005-04-03
it worked.  thanks a lot

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=paulle]it worked.  thanks a lot[/QUOTE]
 np :)

---

