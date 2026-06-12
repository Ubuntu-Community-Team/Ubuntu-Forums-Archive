---
title: "bible software please help"
date: 2011-07-19
forum: Ubuntu Christian Edition
---

### Post by revpaul on 2011-07-19
i am unable to use Xiphos or get esword to run wine crashes on install and this is what i get in terminal was working until today when system asked to update. 

when using sudo apt-get install xiphos

The following packages have unmet dependencies.
  xiphos: Depends: xulrunner-1.9.1 but it is not installable
E: Broken packages

when using wget -q [http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc](http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc) -O- | sudo apt-key add - && sudo wget [http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_i386.list](http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/karmic_i386.list) -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce


The following packages have unmet dependencies.
  ubuntu-ce: Depends: xiphos but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

any help please to get this running again.

---

### Post by Maheriano on 2011-07-19
sudo apt-get install xulrunner-1.9.1
sudo apt-get install wine-christian repos

---

### Post by revpaul on 2011-07-19
> **Maheriano said:**
> sudo apt-get install xulrunner-1.9.1
sudo apt-get install wine-christian repos
Package xulrunner-1.9.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xulrunner-1.9.1 has no installation candidate


E: Couldn't find package wine-christian

---

### Post by revpaul on 2011-07-20
solved 
1st un-install old xiphos-data will not update with old data file
2nd un-install samba4 
restart and install xiphos works fine.

---

