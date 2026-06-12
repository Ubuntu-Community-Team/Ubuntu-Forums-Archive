---
title: "post your scripts"
date: 2010-09-27
forum: The Cafe
---

### Post by limestone on 2010-09-27
Share scripts or tiny programs that you have written or maybe just using.
My script is an install script that auto-installs stuff for me after fresh core-Debian install.
:)

```

#!/bin/bash
aptitude install -R xorg gnome-core gnome-keyring gnome-screensaver gnome-media network-manager-gnome gnome-themes gconf-editor pulseaudio-module-x11 slim system-config-printer evince file-roller gcalctool iceweasel empathy transmission totem rhythmbox sudo totem-mozilla telepathy-butterfly rhythmbox-plugins gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly flashplugin-nonfree

echo "Copying prefs.js to /etc/iceweasel/profile ..."
cp prefs.js /etc/iceweasel/profile
echo "Copying gnome.png to /usr/share/backgrounds ..."
cp gnome.png /usr/share/backgrounds
echo "Copying blue.jpg to /usr/share/backgrounds ..."
cp blue.jpg /usr/share/backgrounds

echo "Setting metacity-button-layout ..."
gconftool-2 -t str --set /apps/metacity/general/button_layout ":minimize,maximize,close"
echo "Setting background ..."
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/gnome.png"

echo "Running aptitude clean ..."
aptitude clean
echo "Running aptitude autoclean ..."
aptitude autoclean

echo "System was successfully installed"

```

---

### Post by VCoolio on 2010-09-27
This may bring some useful ideas. I run this on downloaded theme/icon package/skin and then choose where to install (needs zenity). You could make a nautilus script out of it (then replace $1 with $NAUTILUS_SELECTED_URIS). I'm sure it can be done better, but it helps.
```
#!/bin/bash

destination=$(zenity --list --radiolist --width="270" --height="350" --text "Where to install Theme?" --title "Destination ..." --column "Pick" --column "Destination" TRUE "$HOME/.themes/" FALSE "/usr/share/themes" FALSE "$HOME/.e/e/themes" FALSE "$HOME/.icons/" FALSE "/usr/share/icons/" FALSE "$HOME/.emerald/themes/" FALSE "$HOME/.mplayer/skins/" FALSE "$HOME/.cairo-clock/theme/")

if [[ "$1" == *.tar.gz* ]]; then
    case $destination in
        /usr*) gksudo "tar xf $1 -C $destination";;
        $HOME*) tar xf $1 -C $destination;;
    esac
else
    case $destination in
        /usr*) gksudo "mv $1 $destination";;
        $HOME*) mv $1 $destination;;
    esac
fi

```

---

### Post by Bachstelze on 2010-09-27
Shell script running in cron to alert me when a new revision of x264 is out by sending me an email with the git output, version information and a source tarball attached:

```
#!/bin/bash

cd /home/firas/software/x264
git pull &> ../git.txt || exit 1

if ! grep -q "Already up-to-date." ../git.txt; then
        bash version.sh >> ../version.txt
        echo >> ../git.txt
        cat ../version.txt >> ../git.txt
        revision=`head -n 1 ../version.txt | egrep -o "r[0-9]+M?"`
        cd ..
        tar czf x264-$revision.tar.gz x264
        mutt -s "New x264 revision: $revision" -a x264-$revision.tar.gz -- firas@fkraiem.org < git.txt
        rm x264-$revision.tar.gz git.txt version.txt
else
        rm ../git.txt
fi

```

---

