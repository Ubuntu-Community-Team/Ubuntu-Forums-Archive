---
title: "How to install drivers form binary in ubuntu 12.04"
date: 2012-09-26
forum: Tutorials
---

### Post by mack_guy911 on 2012-09-26
i write a simple not geeky for simple user to get helped like me in a simple way to install nvidia drivers from binary in ubuntu hope you people like it.

----------------------------------------------------------------------------

step 1. download driver which works best with your system or new one i installed 275.43 one choose what best work on your system .....

and save it to Downloads folder.

step 2. right click on it properties and make is executable

or

chmod + x NVIDIA-Linux-x86_64-275.43.run (what is your driver version)

step 3. type in terminal

$gksudo gedit /etc/modprobe.d/blacklist.conf

#blacklist nouveau and other nvidia modules

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivat

step 4. uninstall if any nvidia installed before by

sudo apt-get --purge remove nvidia-*


also for some more nvidia commands please check

to uninstall current nvidia driver

# sudo apt-get --purge remove nvidia-current

to remove nouveau (althoe its not needed)

# sudo apt-get --purge remove xserver-xorg-video-nouveau

to remove form ubuntu x-swat/x-updates ppa

# sudo ppa-purge ppa:ubuntu-x-swat/x-updates && sudo apt-get install nvidia-current


after removing any previously install nvidia reboot your system


step 5: just before installing make sure "gcc gcc++ make" are already installed.


step 6 after reboot you need to kill xserver since init 3 is now not available so you need to stop GDM to do that open terminal type:


#sudo service lightdm stop

and then press Alt Crt +F2 and login

username :

password :

sudo su and switch to root mode and now here in root mode give path of your downloads folder

# cd Downloads

after that type sudo sh NVIDIA...........and install the driver (pressing Tab button give entire path)

Downloads# sudo sh NVIDIA-Linux-x86_64-275.43.run

hit

Enter/Return button and install your driver

thats all.

---

