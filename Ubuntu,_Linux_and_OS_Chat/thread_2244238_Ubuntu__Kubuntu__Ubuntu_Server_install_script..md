---
title: "Ubuntu / Kubuntu / Ubuntu Server install script."
date: 2014-09-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2014-09-14
Hell of a time getting the de test to work right. Worked on this most of the night. Enjoy.

```
#!/bin/bash#Tadaen Sylvermane
#Ubuntu Installer


##### begin script #####


### user functions ###


minecraft() { # setup minecraft
  clear && read -p "enter path to minecraft source folder..." mcopt1
  if [[ -d "$mcopt1" ]] ; then
    # make shortcut for menus
    if [[ ! -d "/home/$USER/.local/share/applications" ]] ; then
      mkdir -p "/home/$USER/.local/share/applications"
    fi
    if [[ -f "$mcopt1/Minecraft.desktop" ]] ; then
      cp "$mcopt1/Minecraft.desktop" "/home/$USER/.local/share/applications"
    fi
    # insert resource packages
    if [[ ! -d "/home/$USER/.minecraft/resourcepacks" ]] ; then
      mkdir -p "/home/$USER/.minecraft/resourcepacks"
    fi
    if [[ -d "$mcopt1/resource" ]] ; then
      for i in "$mcopt1/resource"/* ; do
	cp -r "$i" "/home/$USER/.minecraft/resourcepacks"
      done
    fi
  else	
    read -p "folder doesn't exist. try again? ( y / n )"  mcopt2
    if [[ "$mcopt2" == [Yy] ]] ; then
      minecraft
    else
      usermenu0
    fi
  fi
}


### root functions ###


upgrade() { # full updates
  clear && echo "copying cache into place if it exists... standby."
  [[ -d "$1" ]] && find "$1" -iname '*.deb' -exec rsync -ru {} "$2" \;
  apt-get update
  apt-get -y dist-upgrade
  reboot
}


software() { # local and repo package installation
  apt-get update
  apt-get -y install $(cat "$1")
  if [[ $(pgrep kwin) || $(pgrep unity) ]] ; then
    [[ -d "$2" ]] && find "$2" -iname '*.deb' -exec dpkg -i {} \;
    apt-get -fy install
  fi
  apt-get autoremove
  apt-get autoclean
  rootmenu1 "$1"
}


themes() { # insert icons and themes
  # $1 is folder of tar.gz files | $2 is destination
  [[ -d "$1" ]] && find "$1" -iname '*.tar.gz' -exec tar -xf {} -C "$2" \;
}


addserver() { # add server mount to /etc/fstab
  clear && read -p "enter remote location ( ip / folder ) --> " asopt0
  clear && read -p "enter mountpoint ( /path/to/mount ) --> " asopt1
  clear && read -p "enter mount type... nfs or cifs (samba) --> " asopt2
  clear && read -p "enter options field for /etc/fstab --> " asopt3
  clear && read -p "enter dump field for /etc/fstab --> " asopt4
  clear && read -p "enter pass field for /etc/fstab --> " asopt5
  clear && echo "Your /etc/fstab entry is as follows...
$asopt0	$asopt1	$asopt2	$asopt3	$asopt4	$asopt5"
  echo
  read -p "is this correct? (y / n) --> " asopt6
  if [[ "$asopt6" == [Yy] ]] ; then
    read -p "are you absolutely sure? (y / n) --> " asopt7
      if [[ "$asopt7" == [Yy] ]] ; then
	if [[ ! -d "$asopt1" ]] ; then
	  mkdir -p "$asopt1"
	fi
	echo "
# my server entry
$asopt0	$asopt1	$asopt2	$asopt3	$asopt4	$asopt5" >> /etc/fstab
      else
	echo "try again..."
	rootmenu1
      fi
  else
    echo "try again..."
    rootmenu1
  fi
}  


printhelp() { # basic help printout
  clear && echo "basic overview of the folder requirement for this script.
the script will work without these but they greatly improve function and speed of installation.
sourcefolder/cache is obvious. backup your /var/cache/apt/archives/*.deb files here.
sourcefolder/configs contains your software list to be installed at fresh installation.
these must be named ubuntu, kubuntu, or server. those are the only supported versions at the moment.
sourcefolder/debs is again fairly obvious. non repo debs are kept here such as google-chrome.
sourcefolder/icons and themes are self-explanatory. inside each is a kubuntu and ubuntu directory.
put the icon tar.gz or theme tar.gz files in the proper places respectively.


the minecraft installer function is basic and first in the script so you can see it easily. minecraftsourcefolder/resource = resource packs, not compressed. i usually keep everything else in the minecraft source folder without subdirectories.


that is all you need. this script is designed for those of us who re-install regularly.
those of us who keep backups of our cache and software lists and burn through it.


i hope you enjoy this script and i hope it saves you some time. thank you for using it.


this script is provided as is and i am not held resposible for whatever damage you
may do to your system by using this script.


tadaen sylvermane...
 


when finished press q to exit the script."
  read -p " --> " phopt0
  if [[ "$phopt0" == [Qq] ]] ; then
    exit 0
  else
    printhelp
  fi
}


### menus ###


rootmenu0() {
  rootmenu1() {
    clear && echo "ATTENTION! run as non-privileged user for more options"
    echo "$1"
    echo "1) upgrade fresh installation"
    echo "2) install packages & software"
    echo "3) install themes"
    echo "4) add a server mount to /etc/fstab"
    echo "9) exit installer"
    echo
    read -p "enter your selected number --> " rmopt0
    if [[ "$rmopt0" == 1 ]] ; then
      upgrade "$debfolder/cache" /var/cache/apt/archives
    elif [[ "$rmopt0" == 2 ]] ; then
      software "$debfolder/configs/$1" "$debfolder/debs"
      rootmenu1 "$1"
    elif [[ "$rmopt0" == 3 ]] ; then
      if [[ $(pgrep kwin) || $(pgrep unity) ]] ; then
	themes "$debfolder/icons/$1" /usr/share/icons
	themes "$debfolder/themes/$1" /usr/share/themes
	echo "themes installed"
	sleep 1
	rootmenu1 "$1"
      else
	clear && echo "this is pointless on a server. try again."
	sleep 2
	rootmenu1 "$1"
      fi
    elif [[ "$rmopt0" == 4 ]] ; then
      addserver
      rootmenu1 "$1"
    else
      echo "thank you for using the script."
      sleep 1
      exit 0
    fi
  }
  clear && read -p "enter path to source folder --> " debfolder
  if [[ -d "$debfolder" ]] ; then
    if pgrep kwin ; then
      rootmenu1 kubuntu
    elif pgrep unity ; then
      rootmenu1 ubuntu
    else
      rootmenu1 server
    fi
  else
    echo "folder doesn't exist. check location & try again..."
    exit 1
  fi
}
 
usermenu0() {
  usermenu1() {
    clear && echo "ATTENTION! run as root/sudo for more options"
    echo
    echo "1) setup minecraft"
    echo "9) exit installer"
    echo
    read -p "enter your selected number --> " umopt0
    if [[ "$umopt0" == 1 ]] ; then
      minecraft
      usermenu1
    else
      echo "thank you for using the script."
      sleep 1
      exit 0
    fi
  }
  if [[ $(pgrep kwin) || $(pgrep unity) ]] ; then
    usermenu1  
  else
    clear && echo "for server purposes you need to run as root / sudo."
    sleep 1
    exit 0
  fi  
}


clear && echo "welcome to your *buntu installer."
echo "this script requires a config folder pre-assembled and in a certain format."
read -p "press y to begin, h for a small help printout --> " mainopt0
if [[ "$mainopt0" == [Yy] ]] ; then
  if [[ "$USER" == root ]] ; then
    rootmenu0
  else
    usermenu0
  fi
elif [[ "$mainopt0" == [Hh] ]] ; then
  printhelp
else
  echo "maybe next time."
  sleep 1
  exit 0
fi
```

---

