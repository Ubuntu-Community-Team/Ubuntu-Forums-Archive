---
title: "How to enable open as root in Nemo on Ubuntu Studio 13.10 x64"
date: 2013-11-10
forum: Tutorials
---

### Post by metalf8801 on 2013-11-10
In order for "Open as Root" to work in Nemo (a fork of Nautilus) on Ubuntu 13.10 you need to install gksu 

Description: If you install Nemo one of the option you should have when you right click a file or a folder is "Open as Root". However, clicking on Open as Root doesn't do anything if you don't have gksu installed and gksu is not installed by default in Ubuntu Studio 13.10 64 bit 

All you need to do is open the Ubuntu Software Center, search for gksu, and click install or type the following into the command line 
sudo apt-get install gksu 




This was only tested on Ubuntu Studio 13.10 64 bit 
[it looks like the steps are a little different for Ubuntu 13.04]("http://askubuntu.com/questions/295442/nemo-open-as-root-ubuntu-13-04")

---

