---
title: "A useful post-installation script for Ubuntu 16.04 LTS."
date: 2016-06-16
forum: The Cafe
---

### Post by michal-klekowicki on 2016-06-16
Hello everyone:)


I installed Ubuntu 16.04 LTS not long ago.


Before the installation I decided to write a script that would speed up the process of installing codecs, commonly used programs (VLC Media Player, GIMP, Inkscape, Audacious, BleachBit, Skype, Steam, Chrome and more) and doing the basic config.


Itappears to be a useful tool so I decided to share it on GitHub with some comments and a README file (in English and in Polish).

Im more or less new to being active on this forum (however I did post a few years ago) so I decided that posting something useful will be a nice touch:)


Usage of the scripts via the terminal (with download):


```
wget https://raw.githubusercontent.com/M-Klekowicki/Post-Installation-Script-for-Ubuntu-16.04-LTS-ENG-PL/master/English/1_spi_INTEL_AMD_ENG.sh


sudo bash 1_spi_INTEL_AMD_ENG.sh

```



or (if you are an NVIDIA user):


```
wget https://raw.githubusercontent.com/M-Klekowicki/Post-Installation-Script-for-Ubuntu-16.04-LTS-ENG-PL/master/English/1_spi_NVIDIA_ENG.sh


sudo bash 1_spi_NVIDIA_ENG.sh

```



The script for cleaning the system after installing all the packages (also makes some useful tweaks):


```
wget https://raw.githubusercontent.com/M-Klekowicki/Post-Installation-Script-for-Ubuntu-16.04-LTS-ENG-PL/master/English/2_spi_Con_Sp.sh


bash 2_spi_Con_Sp.sh

```



Details and the README file with a detailed description of what exactly thescript is doing (I _**strongly**_ advice to read it before using):


[https://github.com/M-Klekowicki/Post-Installation-Script-for-Ubuntu-16.04-LTS-ENG-PL](https://github.com/M-Klekowicki/Post-Installation-Script-for-Ubuntu-16.04-LTS-ENG-PL)


The scripts themselves are also full of comments that can help with understanding the code if someone is completely new to bash or the command line as a whole.




**Nvidia users will need to additionally install the correct driver version for their GPU (allegedly the newest stable version:  sudo apt-get install nvidia-361)**

---

### Post by QIII on 2016-06-16
*Moved to **The Cafe***.

This post was not in response to a support request.

It is important to remember that what you think are good packages to install may not be for others.  Further, some users my attempt this without knowing what it does - and find out too late that has had unintended effects.

---

### Post by michal-klekowicki on 2016-06-16
> **QIII said:**
> *Moved to **The Cafe***.

This post was not in response to a support request.

It is important to remember that what you think are good packages to install may not be for others.  Further, some users my attempt this without knowing what it does - and find out too late that has had unintended effects.

Good point:) The question of the preferred packages (naturally the script is based on my preferences) is addressed in the readme that's why I advised to read it before using the script. The script is also quite easy to modify which is also addressed in the readme. I encourage to modify the script and the packages to ones liking. Maybe someone will find it useful. Suggestions for creating a more universal script also appreciated:) Thanks for moving the thread:)

---

### Post by horsebox2 on 2017-02-13
I checked it out, its pretty good, I started my own post installation script also but don't have anywhere near enough time to complete it. We should setup a system where we can all contribute bits and pieces so together we make a decent post installation script. Like for eample, I made a script which rearranges the Unity launcher icons, it gets rid of the useless ones, and adds only applications from a list (which the user can add to). It also checks to make sure the application is actually installed first. Its not very useful by itself, but as part of a complete post installation tool, it would make a good addition. Heres the best post install script I found:
[https://github.com/snwh/ubuntu-post-install](https://github.com/snwh/ubuntu-post-install)

It uses whiptail to create nice menus. But its severely lacking, I added my own additions to it, but its sloppy. Maybe hes open to letting people contribute to the script, that'd be the way to go.

---

### Post by horsebox2 on 2017-02-13
Take a look at this:
[https://github.com/webpro/dotfiles](https://github.com/webpro/dotfiles)

What there should be is an installation/configuration repository that plugs into a tool that will run these scripts for you. Kind of like puppet does for vagrant, but much more. So you select actually what tools you want, what repos you need, what environment variables you want, what packages you need for the tools, how the tools should be configured etc.

---

### Post by oi0i0io on 2017-08-30
this will get everything the average user beeds:
modified HowToUbuntu's amazing trusty tahr tutorial

```
#!/bin/bash

echo "Downloading GetDeb and PlayDeb" &&
wget [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb) [http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb) &&

echo "Installing GetDeb" &&
sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb &&

echo "Installing PlayDeb" &&
sudo dpkg -i playdeb_0.3-1~getdeb1_all.deb &&

sudo add-apt-repository -y ppa:videolan/stable-daily


sudo add-apt-repository -y ppa:gnome3-team/gnome3-staging


sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp


sudo add-apt-repository -y ppa:gnome3-team/gnome3


sudo add-apt-repository -y ppa:webupd8team/java


sudo add-apt-repository -y ppa:webupd8team/y-ppa-manager


sudo add-apt-repository -y ppa:paulo-miguel-dias/pkppa



echo 'deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
echo 'deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
wget -O - [http://download.videolan.org/pub/debian/videolan-apt.asc|sudo](http://download.videolan.org/pub/debian/videolan-apt.asc|sudo) apt-key add -

##########################
#                                                    #
#                 INSTALL                        #
#                                                    #                                           
##########################


sudo apt-get update && sudo apt full-upgrade --force-yes && sudo apt-get install -y synaptic vlc gimp gimp-data gimp-plugin-registry gimp-data-extras y-ppa-manager bleachbit openjdk-8-jre oracle-java8-installer flashplugin-installer unace unrar zip unzip p7zip-full p7zip-rar sharutils rar uudeview mpack arj cabextract file-roller libxine2-ffmpeg mencoder flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview libmpeg3-2 mpeg3-utils mpegdemux liba52-dev mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac-dev totem icedax lame libmad0 libjpeg-progs libdvdcss2 libdvdread4 libdvdnav4 ubuntu-restricted-extras ubuntustudio-font-meta edubuntu-fonts pithos mpv gnome-mplayer gnome-mpv bleachbit unity-tweak-tool git perl bzr subversion python3 python3 dispcalgui argyll arandr hddtemp tlp tlp-rdw powertop crda lm-sensors rtkit watchdog bootchart gparted gpart makebootfat unetbootin nautilus-admin ruby powerline fslint liquidprompt screen tmux terminator unicode figlet toilet lolcat fortunes-off ascii cowsay gedit-plugins bluefish winefish qt4-default adwaita-qt --force-yes

 
if [[ $(getconf LONG_BIT) = "64" ]]
then
    echo "64bit Detected" &&
    echo "Installing Google Chrome" &&
    wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb) &&
    sudo dpkg -i google-chrome-stable_current_amd64.deb &&
    rm -f google-chrome-stable_current_amd64.deb
else
    echo "32bit Detected" &&
    echo "Installing Google Chrome" &&
    wget [https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb) &&
    sudo dpkg -i google-chrome-stable_current_i386.deb &&
    rm -f google-chrome-stable_current_i386.deb
fi


echo "Cleaning Up" &&
sudo apt-get -f install &&
sudo apt-get autoremove &&
sudo apt-get -y autoclean &&
sudo apt-get -y clean


#END#
```

---

