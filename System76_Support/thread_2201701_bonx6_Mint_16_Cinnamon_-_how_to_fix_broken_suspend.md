---
title: "bonx6 Mint 16 Cinnamon - how to fix broken suspend"
date: 2014-01-25
forum: System76 Support
---

### Post by robjective on 2014-01-25
I'm not sure if it is something that is specific to my machine or my upgrade path, but when I moved from Mint 15 to Mint 16, suspend would no longer work; neither when closing the lid, nor when selecting it from the shutdown menu.  When trying to resume, it would freeze at the login screen.

Changing drivers through the Driver Manager only made things worse.

I didn't figure this out on my own.  See the links below for reference.

This is for the 64 bit version.  Check the links for the 32 bit.  It will update the kernel, then the video drivers.

[INDENT]sudo apt-get purge nvidia-current
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb)
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)
sudo dpkg -i linux-headers-3.13.0-*.deb linux-image-3.13.0-*.deb
sudo apt-repository ppa:xorg-edgers/ppa
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
apt remove --purge xserver-xorg-video-nouveau libdrm-nouveau1
[/INDENT]

Sources:
[URL="http://ubuntuhandbook.org/index.php/2014/01/linux-kernel-3-13-install-in-ubuntu-linux-mint/"]http://ubuntuhandbook.org/index.php/2014/01/linux-kernel-3-13-install-in-ubuntu-linux-mint/
[/URL]
[http://community.linuxmint.com/tutorial/view/1277]("http://community.linuxmint.com/tutorial/view/1277")

---

### Post by gary19 on 2014-02-10
Had the same symptoms after upgrading to Mint 16 32-bit.

Updating the package:      linux-firmware    from 1.116 to 1.116.1   fixed it all.

(Currently, when using Mint's update manager, you will need to view _all levels_ of updates - at the moment this package is 
in the Level 5 nasty-dangerous category !)

Gary

---

