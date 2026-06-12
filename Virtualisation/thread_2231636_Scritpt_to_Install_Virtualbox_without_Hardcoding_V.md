---
title: "Scritpt to Install Virtualbox without Hardcoding Version"
date: 2014-06-26
forum: Virtualisation
---

### Post by TJSL on 2014-06-26
I am attempting to create a robust script to install Virtualbox without hardcoding the version number. I would like to have this capability so that I do not install an old version of Virtualbox when I run the script in the future (or need to manually update the script to the correct version). Is this possible? Side note: I see that the file "LATEST.TXT" in [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/) contains the most recent version number. How can I use this to accomplish the above?

#Installation script containing hardcoded version number
sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install virtualbox-4.2 -y -f #Hardcoded version number
wget [http://download.virtualbox.org/virtualbox/4.2.0/Oracle_VM_VirtualBox_Extension_Pack-4.2.0.vbox-extpack](http://download.virtualbox.org/virtualbox/4.2.0/Oracle_VM_VirtualBox_Extension_Pack-4.2.0.vbox-extpack) #Hardcoded version number
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.2.0.vbox-extpack --replace

---

### Post by TJSL on 2014-06-27
This appeard to work. I would welcom suggestions for improvement.


#!/usr/bin/env bash

echo "==> Installing virtualbox"
sudo sh -c "echo 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) '$(lsb_release -cs)' contrib non-free' > /etc/apt/sources.list.d/virtualbox.list"
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install curl
LATEST_VERSION=$(curl [http://download.virtualbox.org/virtualbox/LATEST.TXT](http://download.virtualbox.org/virtualbox/LATEST.TXT))
major=`echo $LATEST_VERSION | cut -d. -f1`
minor=`echo $LATEST_VERSION | cut -d. -f2`
sudo apt-get install virtualbox-$major.$minor dkms -y

echo "==> Installing virtualbox Extensions"
version=$(vboxmanage -v)
var1=$(echo $version | cut -d 'r' -f 1)
var2=$(echo $version | cut -d 'r' -f 2)
file="Oracle_VM_VirtualBox_Extension_Pack-$var1-$var2.vbox-extpack"
wget http://download.virtualbox.org/virtualbox/$var1/$file -O /tmp/$file
sudo VBoxManage extpack install /tmp/$file --replace
rm /tmp/$file

---

### Post by TheFu on 2014-06-28
Use full paths to all programs to avoid getting the wrong tool. Normally, people set those into environment variables at the top.
At this point, you may want to review the ABSG for more ideas.  I know it always helps me.

---

