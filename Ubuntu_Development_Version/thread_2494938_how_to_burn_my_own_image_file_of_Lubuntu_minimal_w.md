---
title: "how to burn my own image file of Lubuntu minimal with my adds?"
date: 2024-02-01
forum: Ubuntu Development Version
---

### Post by oui on 2024-02-01
as the refractatools (soureforge) does not work, it would be ideal, I am looking for an other way to secure my fresh installation (with the daily ISO from 30th January from 24.04 Noble, installations option «minimal»! After that, I did do the steps in my .bash_history (cleaned from the divers wrong steps...) I add at the end of this message.

this installation is a bit under 6 GB, includes a lot of stuff for children and youth people, simple tools like abiword ans gnumeric for beginner, but also mhwaveedit, nted to learn music and writing, marble and merkaartor for geography, also local geography, it is in my eyes important, kturtle and ucb-logo (the language for what Brian Harvey spends very generous his magistrally books gratis on the web), and  use simple tools also being adequate in CLI installations for those beginning to discover deeply Linux (ranger/granger-gui, nano, sorry, without gui, no gui for nano at ubuntu repository, clex without gui, links CLI mode only, also without gui.

it seems to work very good, about fantastic! it is beautiful with extreme smart look....

.... and testing versions HAVE TO evolve and I am afraid of actualizations bringing problems :guitar:

how to make an ISO file for CD of the image from my so perfect installation with other tools as refractasnapshot (but so simple and so effective to use ):P )?

Cleaned content of my actual .bash_history:
```
#
# installations history and created links to help using linux linux in the terminal (fm pad snap web term txt)
# my installation uses /etc/apt/apt.conf! read it!!!
# https://sourceforge.net/projects/refracta/files/tools/
# https://sourceforge.net/projects/kompozer/files/current/0.7.10/kompozer-0.7.10-i386.deb/download
# language packs: https://kompozer.sourceforge.net/l10n/langpacks/kompozer-0.8b3/ or
# https://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/ + hunspell !
# 
#
sudo apt update
sudo apt install luakit > i0a
sudo apt install epiphany-browser > i0b
sudo apt install epiphany-browser luakit > i0c
sudo ln -s /usr/bin/pcmanfm-qt /usr/bin/fm
sudo ln -s /usr/bin/luakit /usr/bin/web
sudo ln -s /usr/bin/qterminal /usr/bin/term
sudo apt install epiphany-browser luakit mplayer mplayer-gui clex deborphan didiwiki ranger l3afpad abiword > i3base
sudo ln -s /usr/bin/abiword /usr/bin/txt
sudo ln -s /usr/bin/l3afpad /usr/bin/pad
sudo apt install abiword clex deborphan didiwiki epiphany-browser gimagereader gimp gnumeric gparted granule hunspell kdenlive kturtle l3afpad lame luakit marble-qt marble-plugins merkaartor mgp mhwaveedit mplayer mplayer-gui nted osmo ranger tesseract-ocr ucblogo > i04
sudo pad /etc/grub.d/40_custom
sudo update-grub
sudo term
# installation from refractasnapshot.deb refractainstaller.deb and compozer.deb (all available at sourceforge) and from xvidcap i686 loadable by amd64 from old puppy forum from user fred, live debian specialist ;-) 
sudo apt install /home/f/*deb
# divers fonts and hunspell for other languages are added manually in /usr/share as the new versions as regular installation would grown the installation heavily!
sudo ln -s /usr/bin/refractasnapshot /usr/bin/snap
sudo snap
#
# templates
#
setxkbmap us intl
xrandr -o left
xrandr -o normal
alsamixer
#
# real begin of the usual bash_history !
#

sudo update-grub
```

---

### Post by jbicha on 2024-02-01
You could try this:

[https://discourse.ubuntu.com/t/image-iso-builder-for-ubuntu-debian-based-distributions/42083](https://discourse.ubuntu.com/t/image-iso-builder-for-ubuntu-debian-based-distributions/42083)

---

### Post by oui on 2024-02-03
thank you very much! very interesting! I would have questions. Where is the right point to ask? Here (where I am old user) or discourse (where I am not user yet) etc?

---

