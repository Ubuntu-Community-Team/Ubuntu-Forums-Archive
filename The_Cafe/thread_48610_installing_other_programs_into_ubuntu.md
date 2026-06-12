---
title: "installing other programs into ubuntu"
date: 2005-07-13
forum: The Cafe
---

### Post by kaybel on 2005-07-13
hello all,

will really appreciate your help with these. i have just finished reading a lot about Ubuntu linux distro, and is seriously considering moving over to it from fedora.
Actually i'm looking for a light weight linux distro i can use for my development purpose ( i develop various softwares using Java language, PHP, Jython and Python.) my questions are:

1. can i download and install other applications like java,php,jython,Tomcat etc into Ubuntu, apart from the default applications it comes with. if yes how can an alien application be installed, is it same as in fedora or any new thing.

2. what is the basic difference between KUbuntu and Ubuntu.

3. is ubuntu great for networking purposes and does it support wireless usb adapters, usb flash drives and usb hard disks.

4. Is it possible by any way other than using VMWare, to install Ubuntu inside a windows system without dual booting.

5. can Ubuntu dual boot with windows xp.


thanks alot for your kind replies.

kaybel

---

### Post by jasmuz on 2005-07-13
Hello:

1- Yes, you can download and install extra applications.

2-The diference between Ubuntu and Kubuntu, is that Ubuntu is the supported project wich comes with Gnome as the interface, and Kubuntu is a fork of the original project with KDE as the interface.

3-So far general networking is good under Ubuntu, Wireless usb adapters are recognized in most part or are used under ndiswrapper, it does recognize without a hitch my flash drive, and it does support usb HD as long as you dont boot from it.

4-I dont know if there is another method besides Wmware to install Ubuntu under Windows

5-Yes, Ubuntu can do dual boots.

Take care.!

---

### Post by Kvark on 2005-07-13
1. To install something...

Open the Synaptic Package Manager (under System -> Administration in the menues)...
Use the sections or the search function to navigate the huge list of programs...
Put checkboxes for the programs you want...
Click apply and you are done!

But configure the package managers sources first by doing this:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)


In the very rare cases when a program is not in that list. Download it and type "sudo alien --install /path/filename".

---

### Post by aysiu on 2005-07-13
[QUOTE=kaybel]
1. can i download and install other applications like java,php,jython,Tomcat etc into Ubuntu, apart from the default applications it comes with. if yes how can an alien application be installed, is it same as in fedora or any new thing. [/quote] Before you do any weird alien unpacking or downloading .debs or .tar.gzs, at least look to see if the applications you're looking for are in the Ubuntu repositories. You can always enable extra repositories if you need them. The only non-Synaptics I've installed are Firefox and Thunderbird, and that's only because I like the "real" icons for those, not the Debian ones.

> 
2. what is the basic difference between KUbuntu and Ubuntu. Only the default desktops (KDE and Gnome, respectively). Everything else is the same underneath. You could even use Ubuntu and download KDE, and it would be similar to using Kubuntu.

> 
3. is ubuntu great for networking purposes and does it support wireless usb adapters, usb flash drives and usb hard disks. Wireless is always a little tricky with Linux, but USB stuff, sure.

> 
4. Is it possible by any way other than using VMWare, to install Ubuntu inside a windows system without dual booting. If you don't want to dual boot, your best options are to either not install it (use the live CD and play around to see if Ubuntu's what you want) or to just get rid of Windows completely. I find dual-boots a lifesaver.

> 
5. can Ubuntu dual boot with windows xp.  Yes. Almost any Linux distro can.

---

### Post by poofyhairguy on 2005-07-13
I explained the process pretty good here:

[http://www.ubuntuforums.org/showpost.php?p=211999&postcount=3](http://www.ubuntuforums.org/showpost.php?p=211999&postcount=3)

---

### Post by gruffy-06 on 2006-09-17
CoLinux is one example replacement of VMware (any product). It allows Windows & Linux (or 2 Linux kernels) to run together at native speed.

Most methods give unprivileged access to the host, which decreases performance. CoLinux guests uses block devices on the host to allow direct access to resources.

You can run currently Debian and Gentoo through CoLinux.

Xen is also available. It provides excellent performance in x86 virtual machines.

This method uses paravirtualization, which modifies the host and guest kernel to increase performance to reduce overhead. In other words, you need an Xen-enabled kernel running on both the host and guest.

openSUSE and Fedora have Xen kernels of their distros. You may need to go into further development to create an Xen-enabled kernel for Ubuntu. You can use it in both Ubuntu and Kubuntu.

Full virtualization is another Xen technique on virtualization-enabled hardware, such as Intel's advanced processors. Only an Xen-enabled kernel needs to run on the host. Then any OS, like Windows or whatever, will be able to run unmodified.

The disadvantage of both these methods is that they're extremely difficult to set up

WARNING: Use at your own risk!

[www.cl.cam.ac.uk/Research/SRG/netos/xen/]("http://www.cl.cam.ac.uk/Research/SRG/netos/xen/")
[www.colinux.org](www.colinux.org)

--Gruffy-- :)

---

### Post by 3rdalbum on 2006-09-17
On Fedora, you can probably find RPMs for a whole heap of programs. Ubuntu's native package format, DEB, is less common. If you install the Alien package, you can convert your RPMs to DEBs.

```

sudo apt-get install alien
alien newpackage.rpm

```

Then you can just double-click the new .deb package and install it.

Although .debs are more difficult to come by than RPMs, there are probably more repositories for Ubuntu than for Fedora. WINE, DVDStyler, Compiz and the Mezzo desktop project have repositories for Ubuntu, so when you add them to /etc/apt/sources.list you can download the latest packages directly from their developers.

---

### Post by Reshin on 2006-09-17
./configure
make
sudo make install

[IMG]http://www.vesabbs.com/images/smilies/smoker.gif[/IMG]

---

