---
title: "Problem to upgrade VirtualBox"
date: 2015-11-13
forum: Virtualisation
---

### Post by satimis on 2015-11-13
Hi all,

OS Ubuntu 14.04 desktop 64bit
Current VirtualBox Version 4.3.32 r103443

I have
virtualbox-5.0_5.0.10-104061-Ubuntu-trusty_amd64.deb
Oracle_VM_VirtualBox_Extension_Pack-5.0.10-104061.vbox-extpack

download on Internet while I started VirtualBox Manager.  But I was unable to install it running Ubuntu Software Center.

Please advise whether there is another way to upgrade my current version to virtualbox-5.0_5.0.10-104061?

Thanks

Regards
satimis

---

### Post by ajgreeny on 2015-11-13
I use the VBox repos to keep it updated successfully which is certainly worth thinking about, and is described in detail at the Debian-based Linux distributions section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).

Simply run commands ```
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-5.0
```

I can't help with software-centre as I never use it (I've actually uninstalled it from my Xubuntu system) as I use synaptic if I want a GUI.
Installing VBox 5.0.10 will first remove the 4.3-32 version before installing 5.0.10.

You will need to double click on the extension-pack package in your download folder, whatever that is, to install it in VBox and then lastly add the guest-additions in each guest OS, just as you had to in upgrades of 4.3.##.

---

### Post by SeijiSensei on 2015-11-13
> **satimis said:**
> I have
virtualbox-5.0_5.0.10-104061-Ubuntu-trusty_amd64.deb
Oracle_VM_VirtualBox_Extension_Pack-5.0.10-104061.vbox-extpack

download on Internet while I started VirtualBox Manager.  But I was unable to install it running Ubuntu Software Center.
Did you try running dpkg?
```
sudo dpkg -i /path/to/virtualbox-5.0_5.0.10-104061-Ubuntu-trusty_amd64.deb
```

However, like ajgreeny, I always use the official Oracle repository rather than the Ubuntu one.

---

### Post by ajgreeny on 2015-11-13
If you have already installed VBox 5.0.10 but not yet installed the extension-pack, simply double click the extension-pack package in your download folder or wherever it is and it should be opened by VBox and installed.

I will repeat my recommendation to use the Oracle VBox repos, however, as I said before as it means the upgrades are done for you by the normal Ubuntu update procedures.

As a general rule I use gdebi to install any .deb packages that I have downloaded and know are safe to install, but are not from the repos or a trusted ppa.

I don't know software-centre but I thought that .deb packages were installed by that if they're not from the repos, but you have to ask the .deb file to be opened with SC; there is no point searching in SC in the usual way for a deb package that's not in the repos.

---

### Post by satimis on 2015-11-15
Hi all,

I'm prepared to install vituralbox-5.0 on repo as advised instead of the download package.

&#10219; apt-cache policy virtualbox-5.0```

virtualbox-5.0:
  Installed: (none)
  Candidate: 5.0.10-104061~Ubuntu~trusty
  Version table:
     5.0.10-104061~Ubuntu~trusty 0
        500 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib amd64 Packages

```
virtualbox-5.0 is on repo

&#10219; apt-cache policy virtualbox```

\virtualbox:
  Installed: (none)
  Candidate: 4.3.10-dfsg-1ubuntu5
  Version table:
     4.3.10-dfsg-1ubuntu5 0
        500 http://hk.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
     4.3.10-dfsg-1 0
        500 http://hk.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages

```

Whether perform following steps to remove the running Virualbox-4.3.32 and install the repo package virtualbox-5.0 ?

$ sudo apt-get remove virtualbox-4.3.32
$ sudo apt-get update
$ sudo apt-get install virtualbox-5.0

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-11-15
When I upgraded to 5.0 from the Oracle repository, it automatically removed the 4.3 version during installation.

---

### Post by satimis on 2015-11-15
> **SeijiSensei said:**
> When I upgraded to 5.0 from the Oracle repository, it automatically removed the 4.3 version during installation.
Hi,

My old version was installed on the package download on VirtualBox website.

Performed following steps;
$ sudo apt-get remove virtualbox-4.3
$ sudo apt-get update
$ sudo apt-get install virtualbox-5.0

install VirtualBox extension pack

Now problem solved.

Thanks

Regards
satimis

---

