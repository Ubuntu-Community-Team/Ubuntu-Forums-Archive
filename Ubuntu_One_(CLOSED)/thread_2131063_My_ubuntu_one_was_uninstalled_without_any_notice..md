---
title: "My ubuntu one was uninstalled without any notice."
date: 2013-03-31
forum: Ubuntu One (CLOSED)
---

### Post by hakperest on 2013-03-31
I am using LinuxMint Nadia 64bit KDE version with Ubuntu one. I am using turkish version so today I noticed that UBUNTU ONE is disapeared automatically, without my any operation or command (I think it is about update).
I am trying to reinstall with these commands:
```
sudo rm -rf ~/.local/share/ubuntuone
rm -rf ~/.cache/ubuntuone
rm -rf ~/.config/ubuntuone
mv ~/Ubuntu\ One/ ~/UbuntuOne_old/``
sudo apt-get autoremove
sudo apt-get remove --purge ubuntuone-control-panel-gtk ubuntuone-client ubuntuone-client-proxy

sudo apt-add-repository ppa:ubuntuone/stable
sudo apt-get update
sudo apt-get install ubuntuone-control-panel-gtk ubuntuone-client ubuntuone-client-proxy
```
but this error message is appears as I am running commands in terminal
```
Package ubuntuone-control-panel-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ubuntuone-control-panel-qt

E: Package 'ubuntuone-control-panel-gtk' has no installation candidate


```

---

### Post by stinkeye on 2013-03-31
Ubuntu One switched to a Qt interface by default, replacing the old GTK version in 12.04.

---

### Post by hakperest on 2013-03-31
> **stinkeye said:**
> Ubuntu One switched to a Qt interface by default, replacing the old GTK version in 12.04.
```
huseyin@huseyin-GA-MA770-UD3 ~ $ **sudo apt-get install ubuntuone-control-panel-qt**
[sudo] password for huseyin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntuone-control-panel-qt : Depends: ubuntu-sso-client-qt (>= 4.1.90) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

huseyin@huseyin-GA-MA770-UD3 ~ $ **sudo apt-get install ubuntu-sso-client-qt**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-sso-client-qt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

