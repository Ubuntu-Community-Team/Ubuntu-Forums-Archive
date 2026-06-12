---
title: "Problem with apt-get"
date: 2006-11-16
forum: Repositories &amp; Backports
---

### Post by vod_ska on 2006-11-16
Hey!

On my last apt-get upgrade I get this message:

S'està llegint la llista de paquets... Error!
E: Problem parsing dependency Depends
E: S'ha produït un error durant el processament de libimlib2-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages
E: No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat

It's catalan. It says that couldn't open package list.

Anyone?

---

### Post by vod_ska on 2006-11-20
I've changed my repositories, but I still have problems.

Don't know what to do ...

E: /var/cache/apt/archives/libpng12-dev_1.2.8rel-5.1ubuntu0.1_i386.deb: files list file for package `libgtk2-trayicon-perl' is missing final newline

---

### Post by buckrodgers on 2006-12-22
try this:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
sudo gedit /var/lib/dpkg/status #look for the broken package and remove that package.
sudo rm /var/cache/apt/*.bin
sudo apt-get upgrade
sudo apt-get -f install

```

---

### Post by grendo on 2007-08-24
Hi,
  I am new to ubuntu and had a similar problem after trying to install java.  anyway while trying to fix the /var/lib/dpkg/status file I noticed a backup directory in /var/lib/dpkg/backups.  And to my relief there was a backup of the status file in there.  so I just copied that over the top of the /var/lib/dpkg/status file, did a apt-get update and everything was back to normal.  now before I install anything I do a backup of /var/lib/dpkg/status before.

hope this helps

---

### Post by iSam24 on 2007-08-27
E: Dynamic MMap ran out of room
E: Error occurred while processing curl (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

i get that message whenever i try to install nearlly anything help please

---

### Post by zWaR on 2007-08-29
Hi,

i am having this problem myself, but with package xcalc:
 files list file for package `xcalc' is missing final newline

Since xcalc is crucial x server component i cannot simply uninstall it... 

The bug is extremly annoying! I have seen it first during the installation process and since then it is cousing nothing but trouble - i am not able to install anything with apt-get, cannot upgrade distro, nothing. Everytime i run apt-get instal some-package i see the error message above.

Any suggestions? I am using kubuntu feisty (7.04-desktop-i386).

---

