---
title: "Problem installing Virtualbox Extension Pack in 18.04"
date: 2018-04-28
forum: Virtualisation
---

### Post by entropy1 on 2018-04-28
I installed Virtualbox with synaptic. Then I tried to install virtualbox-ext-pack and got the error:
```
E: virtualbox-ext-pack: installed virtualbox-ext-pack package post-installation script subprocess returned error exit status 1
```

The "Details panel" of the attempted installation said:

```
Preconfiguring packages ...
Selecting previously unselected package virtualbox-ext-pack.
(Reading database ... 200435 files and directories currently installed.)
Preparing to unpack .../virtualbox-ext-pack_5.2.10-3_all.deb ...
License has already been accepted.
Unpacking virtualbox-ext-pack (5.2.10-3) ...
Setting up virtualbox-ext-pack (5.2.10-3) ...
virtualbox-ext-pack: downloading: http://download.virtualbox.org/virtualbox/5.2.10/Oracle_VM_VirtualBox_Extension_Pack-5.2.10.vbox-extpack
The file will be downloaded into /usr/share/virtualbox-ext-pack
Hash mismatch Oracle_VM_VirtualBox_Extension_Pack-5.2.10.vbox-extpack: expected 8c31bc1d0337e6668e0d9140defc6deaf265087f855783dd09b873a064a70703, or wrong accept-license key
dpkg: error processing package virtualbox-ext-pack (--configure):
 installed virtualbox-ext-pack package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up virtualbox-ext-pack (5.2.10-3) ...
virtualbox-ext-pack: downloading: http://download.virtualbox.org/virtualbox/5.2.10/Oracle_VM_VirtualBox_Extension_Pack-5.2.10.vbox-extpack
The file will be downloaded into /usr/share/virtualbox-ext-pack
Hash mismatch Oracle_VM_VirtualBox_Extension_Pack-5.2.10.vbox-extpack: expected 8c31bc1d0337e6668e0d9140defc6deaf265087f855783dd09b873a064a70703, or wrong accept-license key
dpkg: error processing package virtualbox-ext-pack (--configure):
 installed virtualbox-ext-pack package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 virtualbox-ext-pack

```

Any suggestions on how to resolve this?

---

### Post by drakuel on 2018-04-28
I am getting the same issue, run a lot om vm's for testing but now got this error too.

---

### Post by alboc on 2018-04-28
me too.

There is a similar in 
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ext-pack/+bug/1767402](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ext-pack/+bug/1767402) 
with a workaround

---

### Post by SeijiSensei on 2018-04-28
I suggest using the version of VirtualBox distributed from the Oracle repositories.  You can add that version to your sources list, and VB will update the same way everything else on your system does.  

See the instructions at: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

I never have problems with version incompatibilities using Oracle's repository.

---

### Post by entropy1 on 2018-04-28
Thanks, alboc, your method worked perfectly.

---

### Post by LHammonds on 2018-04-30
When I was documenting the latest developer release of 18.04 last week, I found that installing dkms, rebooting and then installing the guest extensions directly from the CD worked for me.

I documented the steps I took here: [Installing Ubuntu Server - Software Configurations](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p618)

LHammonds

---

### Post by d-roe on 2018-05-03
> **SeijiSensei said:**
> I suggest using the version of VirtualBox distributed from the Oracle repositories.  You can add that version to your sources list, and VB will update the same way everything else on your system does.  

See the instructions at: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

I never have problems with version incompatibilities using Oracle's repository.

In this instance I am still getting the same error with the package from the oracle repos when trying to install on 18.04

---

### Post by LHammonds on 2018-05-03
> **d-roe said:**
> In this instance I am still getting the same error with the package from the oracle repos when trying to install on 18.04
Are you using VirtualBox 5.2.8 and did you install the version that came with it?

---

### Post by lotfy_it on 2018-05-08
Worked with me too

---

### Post by SeijiSensei on 2018-05-08
> **d-roe said:**
> In this instance I am still getting the same error with the package from the oracle repos when trying to install on 18.04

The current version of VirtualBox 5.2 for 18.04 in the Oracle repo is 5.2.10-122088~Ubuntu~bionic.

```

$ dpkg -s virtualbox-5.2
Package: virtualbox-5.2
Status: install ok installed
Priority: optional
Section: contrib/misc
Installed-Size: 162658
Maintainer: Oracle Corporation <info@virtualbox.org>
Architecture: amd64
Version: 5.2.10-122088~Ubuntu~bionic

```

I recall having an architecture problem when I first started using the repo for 18.04.  I solved it by editing /etc/apt/sources.list.d/virtualbox.list to read

```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian bionic contrib
```

adding the "[arch=amd64]" parameter then running "sudo apt update" and "sudo apt install virtualbox-5.2".

---

### Post by SeijiSensei on 2018-05-11
VirtualBox updated in the past few days to 5.2.12-122591~Ubuntu~bionic.

---

