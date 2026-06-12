---
title: "Downloading Security Updates Prior to Installation"
date: 2010-05-06
forum: Security
---

### Post by yeehi on 2010-05-06
How can we download the important Ubuntu security updates prior to installing Ubuntu so that we can remain off line during the installation process and get patched up before going on line to get the other updates?

Once Ubuntu has been installed, what commands would you give to apply the downloaded security updates?

Thank you!

---

### Post by cariboo on 2010-05-06
Synaptic Package Manager, apt-get and aptitude all allow you to download the files only.

Synaptic has a check box on the window where you confirm what you want install.

apt-get uses the -d option.

Aptitude, uses the -d option.

For more info check the respective man pages.

---

### Post by bodhi.zazen on 2010-05-06
> **cariboo907 said:**
> Synaptic Package Manager, apt-get and aptitude all allow you to download the files only.

Synaptic has a check box on the window where you confirm what you want install.

apt-get uses the -d option.

Aptitude, uses the -d option.

For more info check the respective man pages.

Honestly I would use the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It is a net install and will download and install the latest packages via apt-get. IMO you can trust the net install as much as a full install as it uses apt. IMO if you trust apt for updates you can trust apt for net installs.

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

My second recommendation would be AptOnCD

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by yeehi on 2010-05-06
Thank you for helping me with this, everyone.

Why isn´t there a 64-bit PC (x86) version of the minimal CD?
Would we be able to do this minimal installation from a flash drive, too? 
Do the minimal installations permit encryption of partitions during installation?

---

### Post by bodhi.zazen on 2010-05-06
> **yeehi said:**
> Thank you for helping me with this, everyone.

Why isn´t there a 64-bit PC (x86) version of the minimal CD?
Would we be able to do this minimal installation from a flash drive, too? 
Do the minimal installations permit encryption of partitions during installation?

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso)

I am not sure about encryption, I would guess from the size of the iso not.

It would not take you very long to find out =)

---

### Post by EJeanmaire on 2010-05-06
> **yeehi said:**
> How can we download the important Ubuntu security updates prior to installing Ubuntu so that we can remain off line during the installation process and get patched up before going on line to get the other updates?

Once Ubuntu has been installed, what commands would you give to apply the downloaded security updates?

Thank you!

You could download the latest software / security sources files from computer A on the internet from the Ubuntu repo, and then load them onto the unpatched computer.  Then run package manager and have it check your versions of installed software vs the updated list.  Then use apt to generate a list of packages to be installed (there is a tutorial for this somewhere. ) then fetch EACH package from the internet on computer A.... transfer them to unpatched computer, then dpkg -i them!

---

### Post by wojox on 2010-05-06
I use the mini.iso's all the time. Their great cause they have triggers for everything ubuntu you would want. 

There is a 64-bit PC (x86) version of the minimal CD

You will be able to encrypt your home directory at the end if you choose.

---

