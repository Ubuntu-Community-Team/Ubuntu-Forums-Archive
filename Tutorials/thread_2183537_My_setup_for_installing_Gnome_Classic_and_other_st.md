---
title: "My setup for installing Gnome Classic and other stuff on 12.04"
date: 2013-10-25
forum: Tutorials
---

### Post by psfal on 2013-10-25
**After a new Ubuntu 12.04 installation (If you don't know how to open a terminal, this is not for you, same for understanding basic commands)**

sudo apt-get update && sudo apt-get upgrade -y


**#reboot machine**


[B]#Do Distribution Upgrade
[/B]
sudo apt-get update && sudo apt-get dist-upgrade -y


**#reboot machine**


**#Enable DVD playback** [http://www.liberiangeek.net/2013/10/heres-enable-dvd-playback-ubuntu-13-10/](http://www.liberiangeek.net/2013/10/heres-enable-dvd-playback-ubuntu-13-10/)

sudo apt-get install ubuntu-restricted-extras && sudo apt-get install libavformat-extra-53 -y libavcodec-extra-53 -y libdvdread4 -y && sudo /usr/share/doc/libdvdread4/install-css.sh && sudo apt-get install vlc -y


**#reboot machine**


**#Update to Kernel 3.11.6** (If you want to upgrade from the Kernel that comes with Ubuntu 12.04) [http://www.liberiangeek.net/2013/10/upgrade-linux-kernel-3-11-6-ubuntu/](http://www.liberiangeek.net/2013/10/upgrade-linux-kernel-3-11-6-ubuntu/)

[B]#For 32bit machines
[/B]sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove && cd /tmp && wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106-generic_3.11.6-031106.201310181453_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106-generic_3.11.6-031106.201310181453_i386.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106_3.11.6-031106.201310181453_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106_3.11.6-031106.201310181453_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-image-3.11.6-031106-generic_3.11.6-031106.201310181453_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-image-3.11.6-031106-generic_3.11.6-031106.201310181453_i386.deb) && sudo dpkg -i *.deb && sudo update-grub2


[B]#For 64bit machines
[/B]sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove -y && cd /tmp && wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106_3.11.6-031106.201310181453_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-headers-3.11.6-031106_3.11.6-031106.201310181453_all.deb) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-image-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.6-saucy/linux-image-3.11.6-031106-generic_3.11.6-031106.201310181453_amd64.deb) && sudo dpkg -i *.deb && sudo update-grub2


**#reboot machine**


[B]#Remove old Kernels
[/B]
sudo apt-get purge linux-image-3.?.? (Put in appropriate Kernel #s) (BE SURE OF WHAT KERNELS YOU'RE REMOVING)


[B]#Remove Headers associated with removed Kernels
[/B]
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove -y


**#Install Gnome Classic** [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

sudo add-apt-repository ppa:caffeine-developers/ppa -y && sudo add-apt-repository ppa:webupd8team/themes -y && sudo apt-get update && sudo apt-get install gnome-panel -y indicator-applet indicator-applet-session -y shiki-colors-metacity-theme -y caffeine -y && gsettings set org.gnome.desktop.screensaver lock-enabled false && gsettings set com.ubuntu.update-notifier auto-launch false && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && sudo apt-get update && sudo apt-get upgrade -y


**#log out of account**


**#login to Gnome Classic (no effects)**


[B]#Remove Unity Desktop
[/B]
sudo apt-get autoremove unity -y


**#Disable pain in the a$$ "System Problem Detected" error messages that mean nothing** [http://www.pctips.in/2012/10/stop-annoying-system-problem-detected.html](http://www.pctips.in/2012/10/stop-annoying-system-problem-detected.html)

sudo gedit /etc/default/apport
#Change the last line of the file from 'enabled=1' to 'enabled=0'
#Save and close the file.
sudo service apport stop


**#reboot machine**

#Install gparted, unetbootin, chromium, imagewriter, asunder from software center (or whatever stuff you like to use)

**#Install Wine 1.6** [http://www.liberiangeek.net/2013/07/wine-1-6-released-how-to-install-upgrade-in-ubuntu/](http://www.liberiangeek.net/2013/07/wine-1-6-released-how-to-install-upgrade-in-ubuntu/)

sudo add-apt-repository ppa:ubuntu-wine/ppa -y && sudo apt-get update && sudo apt-get install wine1.6 -y


**#Install Virtualbox 4.3** [http://www.liberiangeek.net/2013/10/virtualbox-4-3-released-windows-mac-linux/](http://www.liberiangeek.net/2013/10/virtualbox-4-3-released-windows-mac-linux/)

sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" >> /etc/apt/sources.list' && wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install virtualbox-4.3 -y


**#Install latest LibreOffice** [http://www.liberiangeek.net/2013/07/libreoffice-4-1-0-final-released-for-windows-mac-os-x-and-linux-systems/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+LiberianGeek+%28Liberian+Geek%29](http://www.liberiangeek.net/2013/07/libreoffice-4-1-0-final-released-for-windows-mac-os-x-and-linux-systems/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+LiberianGeek+%28Liberian+Geek%29)

sudo add-apt-repository ppa:libreoffice/ppa -y && sudo apt-get update && sudo apt-get dist-upgrade -y


**#Install clicompanion** (A helper for teaching command-line) [https://help.ubuntu.com/community/clicompanion](https://help.ubuntu.com/community/clicompanion)

sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies -y && sudo apt-get update; sudo apt-get install clicompanion -y


**#Install Netflix Desktop** (Watch your Netflix streaming video) [http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux](http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux)

sudo add-apt-repository ppa:ehoover/compholio -y && sudo apt-get update && sudo apt-get install netflix-desktop -y


**#Install latest Google-Chrome** [http://www.liberiangeek.net/2013/10/daily-ubuntu-tips-install-google-chrome-browser/](http://www.liberiangeek.net/2013/10/daily-ubuntu-tips-install-google-chrome-browser/)

**#For 32bit machines**
cd /tmp && wget [https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb) && sudo dpkg -i google-chrome*; sudo apt-get -f install -y


[B]#For 64bit machines
[/B]
cd /tmp && wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb) && sudo dpkg -i google-chrome*; sudo apt-get -f install -y

**#reboot machine**

**#Install HPLIP 3.13.10** (If your printer is too new for the HPLIP preinstalled in Ubuntu) [http://www.liberiangeek.net/2013/10/daily-ubuntu-tips-hplip-3-13-10-driver-released/](http://www.liberiangeek.net/2013/10/daily-ubuntu-tips-hplip-3-13-10-driver-released/)

wget [http://prdownloads.sourceforge.net/hplip/hplip-3.13.10.run](http://prdownloads.sourceforge.net/hplip/hplip-3.13.10.run) && sh hplip-3.13.10.run

#After HPLIP install, you'll always get a "System tray not found" error on login, this is connected to HPLIP. Close it and disregard, it only happens when you login, it won't come back after you close it until your next login.

---

### Post by ibjsb4 on 2013-10-25
How bout showing us a pic of your desktop.

---

### Post by psfal on 2013-10-25
> **ibjsb4 said:**
> How bout showing us a pic of your desktop.

There's no utility on this forum for uploading an image from my computer without jumping through hoops. My desktop looks and behaves like a Gnome 2.0 desktop from Ubuntu 10.04 with 2 displays (extended desktop), CPU frequency scaling applets, System Monitor applets, and Weather Report applets in the panel up top on the primary display...

---

