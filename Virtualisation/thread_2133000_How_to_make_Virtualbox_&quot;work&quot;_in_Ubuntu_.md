---
title: "How to make Virtualbox &quot;work&quot; in Ubuntu 12.10"
date: 2013-04-06
forum: Virtualisation
---

### Post by afz12 on 2013-04-06
FYI, I recently added Ubuntu 12.10 as dual boot with Mint Cinammon on my notebook and found that Virtualbox would not work. Some posts suggested the following code for the terminal

sudo apt-get install dkms build-essential linux-headers-generic
sudo /etc/init.d/vboxdrv setup

Apparently this worked for some people but it did not work for me! If this happens to you, I found that adding the following lines in a terminal finally got Virtualbox to go

  	 	 	 	   sudo apt-get install linux-headers-3.5.0-17-generic

sudo /etc/init.d/vboxdrv setup

  
Good luck!

---

### Post by Derxst on 2013-04-10
I found the issue only occurs when installing from the Software Center. If it is installed from a package downloaded from VirtualBox.org, the issue doesn't occur.

---

### Post by afz12 on 2013-04-10
Thanks for the observation Derxst. I don't recall if I istalled using the .deb installer or not? In any case, I wonder if USB support worked automatically for you. I had to open a terminal and add

sudo usermod -a -G vboxusers myname

this updates the groups file in /etc directory, so that the last line reads

vboxusers:x:125:myname

This may require a restart for it to take effect.

Alternatively, there may be some hardware dependent behavior going on. Lately I am finding Ubuntu 12.10 to be a bit "flakey" at startup - sometimes it just hangs. Linx Mint always boots up fine, as do earlier Ubuntu versions e.g. 3.5.0-17-generic. However, this hp dv6 i5 notebook shouldn't be all that old a model yet!

---

