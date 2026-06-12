---
title: "running windows 7 ultimate in virtualbox"
date: 2015-09-17
forum: Virtualisation
---

### Post by nashtrik on 2015-09-17
I have Win-7 Ultimate on partition C of my hard drive and Ubuntu 14.04 64 bit on partition F. Windows was initially installed and I installed Ubuntu later on. Upon booting, the Ubuntu login is the default and I can scroll down to Windows if I want to.Can I run Win in virtualbox under Ubuntu ? How ?
P.S :- I can mount the windows partition under Ubuntu [sda2] and can access all the files whereas under windows, the ubuntu files are not visible.

---

### Post by yancek on 2015-09-17
You can download and install VirtualBox from the Software Center on Ubuntu or go to their site to get a newer version.   The link below gives a guideline on installing it on Ubuntu and putting a windows 7 system in VirtualBox.

[http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box](http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box)

>  I can mount the windows partition under Ubuntu [sda2] and can access  all the files whereas under windows, the ubuntu files are not visible. 		

That's standard and expected behavior by windows and a business decision by microsoft.  A default windows system has never been able to do that although there is some third party software that might work

---

### Post by v3.xx on 2015-09-17
And the OP has the necessary hardware to run vBox?

What cpu are you running and how much ram do you have?

---

### Post by QIII on 2015-09-17
*Moved to **Virtualisation***

---

### Post by nashtrik on 2015-09-18
Thanks for the reply..to put it more appropriately,can an already installed Win7 be run in virtualbox under Ubuntu? The tutorial  shows first to install virtualbox and then INSERT the win7 cd to install it whereas Win7 is already installed on my system[ its an authentic version] and I don't have the CD.There are 4 partitions of the Hard drive[500 GB], Win in on drive C [referred to as sda2  (35 GB) volume by Ubuntu], D & E drives contain music and video files and the F drive hosts ubuntu. The RAM is 1 GB and the processor is 64 bit Dual core. Any further suggestions? Thanks

---

