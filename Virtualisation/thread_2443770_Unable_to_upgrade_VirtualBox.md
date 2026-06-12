---
title: "Unable to upgrade VirtualBox"
date: 2020-05-20
forum: Virtualisation
---

### Post by satimis on 2020-05-20
Hi all,

VirtualBox 6.0
Host OS - Ubuntu 18.04

This is a spare desktop PC, having NOT been run for about a month.  On starting VirtualBox I'm asked to upgrade to a new version of VirtualBox. On clicking to accept it finally a warning popup```

The network operation failed with the following error: 
During network request: SSL authentication failed.

```
This is NOT the first time I'm asked to upgrade VirtualBox on this PC but it is my first time encountering this problem.

I have been searching a while on Internet discovering several links having similar problem.  Please advise how to fix it.

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2020-05-20
What version of VirtualBox are you trying to upgrade to?
Does it work for you to manually download the new version from the official website, [FONT=Courier New]apt-get purge[/FONT] the existing VirtualBox, then install the new version?

---

### Post by SeijiSensei on 2020-05-20
Follow the procedure described here

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

to add Oracle's repository to your system.  Next remove your current virtualbox installation with

```
sudo apt purge virtualbox
```

then install VB 6.1 with

```

sudo apt update
sudo apt install virtualbox-6.1

```

Your system will upgrade VB automatically when needed just like it updates software in the Ubuntu repositories.

After you've finished and VB works as expected, install the Extension Pack: [https://download.virtualbox.org/virtualbox/6.1.8/Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.8/Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack)

---

### Post by satimis on 2020-05-22
> **SeijiSensei said:**
> Follow the procedure described here

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

to add Oracle's repository to your system.  Next remove your current virtualbox installation with

```
sudo apt purge virtualbox
```

then install VB 6.1 with

```

sudo apt update
sudo apt install virtualbox-6.1

```

Your system will upgrade VB automatically when needed just like it updates software in the Ubuntu repositories.

After you've finished and VB works as expected, install the Extension Pack: [https://download.virtualbox.org/virtualbox/6.1.8/Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.8/Oracle_VM_VirtualBox_Extension_Pack-6.1.8.vbox-extpack)

Hi,

Thanks for your advice.

Performed following steps:-

$ sudo nano /etc/apt/sources.list
That line is already there but being commented out.
Un-comment that line

Reboot PC

$ sudo apt purge virtualbox```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'virtualbox' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Very strange to me?  Virtual Box is running on this PC

$ sudo dpkg -l | grep virtualbox```

ii  virtualbox-6.0                             6.0.22-137980~Ubuntu~bionic                      amd64        Oracle VM VirtualBox

```

Is it a test-built version?  How to remove it?  Thanks

Regards
satimis

---

### Post by satimis on 2020-05-22
> **halogen2 said:**
> What version of VirtualBox are you trying to upgrade to?
Does it work for you to manually download the new version from the official website, [FONT=Courier New]apt-get purge[/FONT] the existing VirtualBox, then install the new version?
Thanks for your advice.

Running version 6.0
Upgrade it to version 6.1

Please see my reply to SeijiSensei's above.  Tks

Regards
satimis

---

### Post by ajgreeny on 2020-05-22
You will need to run ***sudo apt purge virtualbox-6.0*** to remove the version you already have.

Or simply run ***sudo apt install virtualbox-6.1*** (assuming you really do have the VBox repos enabled as you say) and it will remove version 6.o and install 6.1 in its place.

Ypou might find using synaptic gives you a much clearer view of what you already have installed and what will happen when you try to add version 6.1.

---

### Post by satimis on 2020-05-22
> **ajgreeny said:**
> You will need to run ***sudo apt purge virtualbox-6.0*** to remove the version you already have.

Or simply run ***sudo apt install virtualbox-6.1*** (assuming you really do have the VBox repos enabled as you say) and it will remove version 6.o and install 6.1 in its place.

Ypou might find using synaptic gives you a much clearer view of what you already have installed and what will happen when you try to add version 6.1.
Hi,

Thanks for your advice.

Performed following steps
- install synatic package manager
- start synatic package manager

On search, found virtualbox 6.1

Please see attached file "screenshot_synaptic.png" 

What will be next step?
Do I need to select "volatility?

Whether following tutorial is applicable ?

SynapticHowto
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2020-05-22
The package virtualbox-6.0 must have come from Oracle's website. The packages there have a version number attached to distinguish them from the version in the repositories which is always called just "virtualbox."

I rarely muck around with GUI package managers.  I much prefer using the command line.
```

sudo apt update
sudo apt install virtualbox-6.1

```

When you run "update" you should see the Oracle repository in the list.

---

### Post by satimis on 2020-05-22
> **SeijiSensei said:**
> The package virtualbox-6.0 must have come from Oracle's website. The packages there have a version number attached to distinguish them from the version in the repositories which is always called just "virtualbox."

I rarely muck around with GUI package managers.  I much prefer using the command line.
```

sudo apt update
sudo apt install virtualbox-6.1

```

When you run "update" you should see the Oracle repository in the list.
Agreed, I usually install and/or upgrade packages on Terminal, running command lines.

This is my 1st time running synaptic to install/upgrade package.  It is just for interest as well as for learning this software.

$ sudo apt update | grep virtualbox```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Hit:8 https://download.virtualbox.org/virtualbox/debian bionic InRelease

```

Regards

---

### Post by ajgreeny on 2020-05-22
The main reason I suggested using synaptic was because it gives you a clearer idea of all the package versions for virtualbox that are available, and allows you to see where they're from if you use the Origin filter in the left pane.

I'm not running bionic now and can't remember but I think the bionic repos from Oracle have both versions 6.0 and 6.1; Ubuntu's own repos had version 5 only if I remember correctly.
Focal now has versions 6.0 and 6.1 in its own repos and both are also from the Oracle repos,  but the Oracle repo version is slightly ahead of the Ubuntu version and I have always found it to work better particularly when using the guest additions package also direct from Oracle.

I have no idea what that volatility package is or what it has to do with virtualbox.  Did it show up when you searched for virtualbox in synaptic?
It is not even in the repos for focal so I've no idea what it is or what it does, but I do not think you need to install it.

---

### Post by satimis on 2020-05-23
> **ajgreeny said:**
>  - snip -

I have no idea what that volatility package is or what it has to do with virtualbox.  Did it show up when you searched for virtualbox in synaptic?
It is not even in the repos for focal so I've no idea what it is or what it does, but I do not think you need to install it.
cat /etc/apt/sources.list | grep deb
```

deb http://hk.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic universe
deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://hk.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
#deb http://download.virtualbox.org/virtualbox/debian bionic contrib
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib
deb-src http://download.virtualbox.org/virtualbox/debian bionic contrib
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Start Synaptic
pls see attached file "screenshot_synaptic_01.png"

Search virtualbox 6.1
pls see attached file "screenshot_synaptic_02.png"

Regards

---

### Post by ajgreeny on 2020-05-23
I am still uncertain why that volatility package shows up when you search in synaptic for virtualbox, though a search has shown that the volatility package is suggested package of ***lime-forensics-dkms***, so this is all very strange.

Are you doing the search by ***Name*** only or ***Description and Name***?

A final thought has just come to me.
As you do seem to have the Oracle repositories showing in your sources.list file but are still having problems I wonder if you ran the two commands to add the security keys for the repos without which you will have problems.

Try running the following in terminal, making sure you include the final - in each command as shown at the Oracle VBox site at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the ***Debian based Linux distributions*** section.
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```

---

### Post by satimis on 2020-05-23
> **ajgreeny said:**
>  - snip -
Are you doing the search by ***Name*** only or ***Description and Name***?

Description and Name

Tried again.  Please refer to following screenshots attached to this posting;
screenshot_find_01.png
screenshot_search_result_01.png

screenshot_find_02.png
screenshot_search_result_02.png

> 
- snip -
Try running the following in terminal, making sure you include the final - in each command as shown at the Oracle VBox site at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the ***Debian based Linux distributions*** section.
```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```
$ wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
[sudo] password for satimis: ```

OK

```

$ wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -```

OK

```

Regards

---

### Post by SeijiSensei on 2020-05-23
"OK" is the normal response when the key is added to the keyring.

---

### Post by ajgreeny on 2020-05-23
So now you should be able to update to VBox-6.1.8

---

### Post by satimis on 2020-06-19
> **ajgreeny said:**
> So now you should be able to update to VBox-6.1.8
Yes.

Sorry for late reply.  This is a spare PC, seldomly used.  Just upgraded VirtualBox to the latest version

```

VirtualBox Graphical User Interface
Version 6.1.10 r138449 (Qt5.9.5)
Copyright © 2020 Oracle Corporation and/or its affiliates. All rights reserved.

```

I'll upgrade VirtualBox to the latest version running on other PCs later.

Thanks

Regards

---

