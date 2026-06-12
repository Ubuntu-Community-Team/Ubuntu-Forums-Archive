---
title: "About the version of VBoxGuestAddition to be used"
date: 2018-05-13
forum: Virtualisation
---

### Post by satimis on 2018-05-13
Hi all,

Host - Ubuntu 16.04 desktop
Guest - Ubuntu 18.04 desktop
VirtualBox

Please advise which version of Guest Addition is suitable for Ubuntu 18.04?  

I have tried following versions;
VBoxGuestAdditions_5.1.2.iso (download on Oracle website)
VBoxGuestAdditions_5.2,2.iso (download on Oracle website)
VBoxGuestAdditions_5.2.10-122088.iso (download on Ubuntu website)

None of them can work for me.

Thanks

Regards
satimis

---

### Post by cruzer001 on 2018-05-13
You don't get to choose.

You must install the version that matches your vBox verison.

---

### Post by satimis on 2018-05-13
> **cruzer001 said:**
> You don't get to choose.

You must install the version that matches your vBox verison.
Hi,

The version is;
Version 5.2.2 r119230 (Qt5.6.1)

GuestAddition 5.2.2 can't work here.  On reboot a black screen is resulted.  I have tried several days without a solution.

Regards
satimis

---

### Post by cruzer001 on 2018-05-13
I suggest removing 5.2.2 and installing [s]5.2.10[/s] **5.2.12** from the virtuabox site.

---

### Post by ajgreeny on 2018-05-13
It's now version 5.2.12, but otherwise I fully agree with cruzer001 and suggest you keep to the newest version available.

There was, incidentally, a known problem with the guest-additions from the early 5.2 versions of VBox which would not allow a display of some Linux distros, particularly if you chose to use a 3D display in the VM settings.  That problem has now gone with the most recent 5.2 VBox versions.

---

### Post by SeijiSensei on 2018-05-13
I suspect I've suggested this to you before, but the best way to ensure that everything matches up is to follow the procedure described here:

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by satimis on 2018-05-13
> **ajgreeny said:**
> It's now version 5.2.12, but otherwise I fully agree with cruzer001 and suggest you keep to the newest version available.

There was, incidentally, a known problem with the guest-additions from the early 5.2 versions of VBox which would not allow a display of some Linux distros, particularly if you chose to use a 3D display in the VM settings.  That problem has now gone with the most recent 5.2 VBox versions.
Hi,

Yes, you're right.

After de-select [Enable 3D Acceleration], GuestAddition 5.2.2 works on Ubuntu 18.04 desktop

satimis

---

### Post by satimis on 2018-05-13
> **SeijiSensei said:**
> I suspect I've suggested this to you before, but the best way to ensure that everything matches up is to follow the procedure described here:

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)
Hi,

Thanks for your link.

I haven't upgraded VirtualBox to its latest version yet.  My previous planning was waiting for Ubuntu 18.04 published.  Then I will purchase a new 1TB SSD to make a clean installation of Ubuntu 18.04.  Now it seems to me that there are some problems on this new LTS version Ubuntu.  I'll delay my planning.


I'll perform following steps to upgrade VirtualBox to its latest version

Host-Ubuntu 16.04 desktop

1)
Step-1

Uncomment following line on /etc/apt/sources.list```

deb https://download.virtualbox.org/virtualbox/debian Xenial contrib

```

Remark: (current sources.list)
&#10219; cat /etc/apt/sources.list```

deb http://hk.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial universe
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://hk.archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-security universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-security universe
deb http://hk.archive.ubuntu.com/ubuntu/ xenial-security multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ xenial-security multiverse

# deb http://download.virtualbox.org/virtualbox/debian xenial contrib 
# disabled on upgrade to xenial

```

Please advise any other lines which I need to comment them out on this file ?

2)
Step-2```

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

```

3)
Step-3```

sudo apt-get update
sudo apt-get install virtualbox-5.2.12

```

Please advise any steps missed?  Thanks in advance

Regards
satimis

---

### Post by SeijiSensei on 2018-05-14
I put the "deb" line for VirtualBox in a separate file called "virtualbox.list"  in /etc/apt/sources.list.d/.  You can put it in sources.list, but I prefer to leave that untouched.  Files with .list extensions in /sources.list.d/ are appended to the entries in sources.list when running "apt update".  Other packages that rely on PPAs or third-party repositories drop files in that directory as well.

Otherwise that looks fine except you want to use
```
sudo apt install virtualbox-5.2
```
not 5.2.12.

You don't need to use "apt-get" anymore either.  Just "apt" is sufficient. (I think that was true for 16.04 as well.)

For some reason, I have an architecture conflict with VirtualBox.  I use
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib
```

Without the arch parameter, I get a "doesn't support architecture 'i386'" error with "apt update". That may be an issue unique to me though.

---

### Post by satimis on 2018-05-14
> **SeijiSensei said:**
> I put the "deb" line for VirtualBox in a separate file called "virtualbox.list"  in /etc/apt/sources.list.d/.  You can put it in sources.list, but I prefer to leave that untouched.  Files with .list extensions in /sources.list.d/ are appended to the entries in sources.list when running "apt update".  Other packages that rely on PPAs or third-party repositories drop files in that directory as well.

Otherwise that looks fine except you want to use
```
sudo apt install virtualbox-5.2
```
not 5.2.12.

- snip -


The version of VirtualBox I'm running is```

VirtualBox Graphical User Interface
Version 5.2.2 r119230 (Qt5.6.1)
Copyright © 2017 Oracle Corporation and/or its affiliates. All rights reserved.

```

The suggested version on;
VirtualBox
Download VirtualBox for Linud Hosts on;
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)```

virtualbox-5.2_5.2.12-122591_Ubuntu_xenial_amd64.deb

```

Downgrade the version to "virtualbox-5.2"?

Regards
satimis

---

### Post by ajgreeny on 2018-05-14
> **satimis said:**
> The version of VirtualBox I'm running is```

VirtualBox Graphical User Interface
Version 5.2.2 r119230 (Qt5.6.1)
Copyright © 2017 Oracle Corporation and/or its affiliates. All rights reserved.

```

The suggested version on;
VirtualBox
Download VirtualBox for Linud Hosts on;
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)```

virtualbox-5.2_5.2.12-122591_Ubuntu_xenial_amd64.deb

```

Downgrade the version to "virtualbox-5.2"?

Regards
satimis
That will not be a downgrade of VBox but an upgrade from 5.2.2 to 5.2.12; it is the way the repo versions show that can be confusing along with the name of the VBox package, which is just 5.2 whichever point version it is.

---

### Post by SeijiSensei on 2018-05-14
Oracle uses "virtualbox-X.Y" to differentiate its package from the "virtualbox" package in the Ubuntu repositories.  X and Y are the major and minor release numbers.

---

