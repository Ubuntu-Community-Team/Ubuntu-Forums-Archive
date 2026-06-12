---
title: "What applications would you install on your fresh Intrepid Ibex? :)"
date: 2008-10-30
forum: The Cafe
---

### Post by wersdaluv on 2008-10-30
'Nuff said.

---

### Post by wersdaluv on 2008-10-30
I'll start. I just listed this on my Tomboy notes and I'm about to run the live CD in a while and get rid of this Hardy.
Gnome-do
Dropbox
Picasa
Google Desktop
Stardict
Compiz-git
Alarm Clock
AWN
Conky
Screenlets
Crossover
Wine
Frozen Bubble
Second Life
Cheese
Kooka
Okular
Empathy
Abiword
Startup Manager
VLC
KTTS
Festival
Ccsm 
emerald theme manager
qgtkstyle
qt4 settings
bootup manager
dohickey project
gparted
VirtualBox

---

### Post by hessiess on 2008-10-30
Awesome WM
conky
blender
LaTeX

---

### Post by jimi_hendrix on 2008-10-30
a tilling wm, what i need for programming (gvim, interpreters and compilers), battle for wesnoth, compiz fusion

---

### Post by cardinals_fan on 2008-10-30
dwm
vim
notecase
kazehakase
opera
vimperator
conky
hsetroot
urxvt
xpad
consonance
emelfm2
clex
scrot
leafpad
alpine
gtk-theme-switch(2)
gqview
google earth
n_v14
fruit

---

### Post by tbroderick on 2008-10-30
beagle (remove tracker)
banshee (remove rhythmbox)
epiphany (remove firefox)
liferea
gnome-mplayer
easytag
ccsm

---

### Post by wersdaluv on 2008-10-30
> **tbroderick said:**
> beagle (remove tracker)
banshee (remove rhythmbox)
epiphany (remove firefox)
liferea
gnome-mplayer
easytag
ccsm
Wow. You'll ditch Firefox for Epiphany. Hehe. I'm wondering why. I would be more understandable if you'll replace it with Opera.

---

### Post by jimi_hendrix on 2008-10-30
> **wersdaluv said:**
> Wow. You'll ditch Firefox for Epiphany. Hehe. I'm wondering why. I would be more understandable if you'll replace it with Opera.

lately ive been using opera because its faster than FF (my FF seems bloated :()

---

### Post by hellion0 on 2008-10-30
I'd install XMMS, mpg123, mplayer, irssi and centerim.

---

### Post by chris4585 on 2008-10-30
I'm going to see if this script will work 100%

```
#!/bin/bash
sudo apt-get update
sudo apt-get remove --purge rhythmbox tomboy gnome-games gnome-games-data pidgin pidgin-data gnome-utils ekiga example-content evolution evolution-common evolution-data-server evolution-webcal tracker f-spot eog
echo Done removing unneeded packages
sleep 3;
sudo apt-get install alien serpentine qps compizconfig-settings-manager emerald beagle gwenview quodlibet thunderbird xchat ksnapshot emesene amsn bmpx apturl ubuntu-restricted-extras lastfm startupmanager htop bitlbee cowsay toilet ud irssi conky youtube-dl ffmpeg audacious audacity
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Now making a desktop icon to your home
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type boolean "true"
sleep 3;
echo Everything is removed and installed, have a good day
```

there's probably some new stuff I'm leaving out but meh :D

---

### Post by Npl on 2008-10-30
Its more of a question what do I leave on my fresh installation. I wrote that script when I installed a daily build some weeks ago, havent tried if its work on the release yet as Im not yet converting my Hardy-installation:

(after that, opera & flashplayer get installed, but that are other scripts)

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

#Ubuntu restricted extras
installdeps=(libdvdcss msttcorefonts gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdnav4 libdvdread3 unrar default-jre rpm unrar unace p7zip-full lha)

# remove useless bloat
removedeps=(firefox-3.0-branding totem-mozilla firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support ubufox libdeskbar-tracker libtracker-gtk0 tracker tracker-search-tool tracker-utils compiz-core compizconfig-backend-gconf compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper libdecoration0 compizconfig-backend-gconf libcompizconfig0 ekiga evolution evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal example-content f-spot libart2.0-cil libflickrnet2.1.5-cil libgconf2.0-cil libgdiplus libglade2.0-cil libglib2.0-cil libgmime2.2-cil libgnome-keyring1.0-cil libgnome-vfs2.0-cil libgnome2.0-cil libgtk2.0-cil libgtkhtml3.16-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil mono-common mono-gac mono-jit mono-runtime tomboy libpurple-bin libpurple0 libsqlite0 pidgin pidgin-data pidgin-otr reiserfsprogs sqlite transmission-common transmission-gtk wv)
# and some leftover configfiles
removefiles=(~/.mozilla)

sudo apt-get remove ${removedeps[@]}
sudo apt-get install ${installdeps[@]}
```

---

### Post by cariboo on 2008-10-30
I should really build a script for this:

Deluge
Thunderbird
Listen
Vlc
Streamtuner
Streamripper
Liferea
Drapes
Ubuntu-restricted extras
Pysol
Kphotoalbum
Hugin
Filezilla
Grsync
Acrobat
Libdvdcss2
TVtime
Htop

Jim

---

### Post by etnlIcarus on 2008-10-31
As I do a command-line install:

xserver-xorg
Xfce4.6 Beta

As for apps:

**Network:**
Firefox
Thunderbird
Lifrea feed reader
Xchat IRC
Emesene MSN via SVN
Deluge torrent from official site, not the old repo version

**Multimedia:**
VLC player
Gnomad 2
Streamtuner
Xfburn
Gnome-mplayer

**Graphics:**
Gimmage from site as it's not in the repos
The Gimp

**Accessories:**
DOSbox
XArchiver
Galculator

That's pretty much all the important bits.

---

### Post by toupeiro on 2008-10-31
I usually always add these.  There are more, but this short list comes to mind without much thought.  Amarok would be on there as well except this time I'm giving Kubuntu Ibex a spin, so its already there for me,

NVidia driver (latest)
sysvconfig
PostgreSQL
pg-admin
streamtuner
audacious
jack
rosegarden
ardour
Wine (latest)

---

### Post by legolas_w on 2008-10-31
> **wersdaluv said:**
> I'll start. I just listed this on my Tomboy notes and I'm about to run the live CD in a while and get rid of this Hardy.
Gnome-do
Dropbox
Picasa
Google Desktop
Stardict
Compiz-git
Alarm Clock
AWN
Conky
Screenlets
Crossover
Wine
Frozen Bubble
Second Life
Cheese
Kooka
Okular
Empathy
Abiword
Startup Manager
VLC
KTTS
Festival
Ccsm 
emerald theme manager
qgtkstyle
qt4 settings
bootup manager
dohickey project
gparted
VirtualBox



Would you share the command for installing them with us?
Thanks

---

### Post by legolas_w on 2008-10-31
> **cardinals_fan said:**
> dwm
vim
notecase
kazehakase
opera
vimperator
conky
hsetroot
urxvt
xpad
consonance
emelfm2
clex
scrot
leafpad
alpine
gtk-theme-switch(2)
gqview
google earth
n_v14
fruit

Hi
Would you share the command for installing them with us.
Thanks

---

### Post by chucky chuckaluck on 2008-10-31
i'd do a command line installation and add...

screen
dvtm
mc
cplay
streamripper
htop
elinks
cdcd

then, i'd add X and the following...

opera
gimp
gcolor2
mplayer
urxvt
dwm
dmenu
scrot

i'm perfectly happy with nano, so i'd just use that for any editing.

---

### Post by Vince4Amy on 2008-10-31
I've installed:

Google Earth
OpenOffice.org 3
WINE
aMSN
Mozilla Thunderbird
Flash
Exaile
Extreme Tux Racer
CCSM
Tuxtype
Pysol
Filezilla
A Bunch of Codecs and mplayer mozilla plugin

---

### Post by bigbrovar on 2008-11-01
> **chris4585 said:**
> I'm going to see if this script will work 100%

```
#!/bin/bash
sudo apt-get update
sudo apt-get remove --purge rhythmbox tomboy gnome-games gnome-games-data pidgin pidgin-data gnome-utils ekiga example-content evolution evolution-common evolution-data-server evolution-webcal tracker f-spot eog
echo Done removing unneeded packages
sleep 3;
sudo apt-get install alien serpentine qps compizconfig-settings-manager emerald beagle gwenview quodlibet thunderbird xchat ksnapshot emesene amsn bmpx apturl ubuntu-restricted-extras lastfm startupmanager htop bitlbee cowsay toilet ud irssi conky youtube-dl ffmpeg audacious audacity
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Now making a desktop icon to your home
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type boolean "true"
sleep 3;
echo Everything is removed and installed, have a good day
```

there's probably some new stuff I'm leaving out but meh :D

i modified your script to my taste 
```

#!/bin/bash
sudo apt-get update
sudo apt-get remove --purge  tomboy ekiga evolution evolution-common evolution-data-server evolution-webcal  f-spot 
echo Done removing unneeded packages
sleep 3;
sudo aptitude install alien   compizconfig-settings-manager thunderbird xchat   amsn lastfm startupmanager htop cowsay irssi youtube-dl ffmpeg audacity libdvdcss2 vlc libdvdcss2 ubuntu-restricted-extras w32codecs amarok cheese virtualbox ffmpeg gparted wine zdesktop nautilus-actions nautilus-clamscan nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-wallpaper soundconverter soundkonverter-amarok pidgin-encryption pidgin-lastfm pidgin-libnotify pidgin-mpris pidgin-musictracker postgresql ssh skype audacity opera gthumb thinkfinger-tools  libpam-thinkfinger startupmanager mousepad irssi cbrpager comix k9copy k3b libk3b2-extracodecs aptoncd
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Everything is removed and installed, can i live in peace now

```

---

### Post by wersdaluv on 2008-11-01
> **legolas_w said:**
> Would you share the command for installing them with us?
Thanks
Installed em one by one :D hehe

---

### Post by Jim! on 2008-11-01
Opera
Wine
Virtual Box
Banshee
Kaffeine
Open Office 3
Alien Arena 
Conky
VLC
+ Codecs,etc

---

### Post by billgoldberg on 2008-11-01
p7zip-full, codecs, flash, banshee, wine+pokerstars, epiphany-webkit and plugins, emesene, bluefish editor, gnome-alsamixer, gftp, frostwire, mediatomb, pytube, xchat, ssh, adobe reader and vlc is what is installed atm besides the stardard stuff.

---

### Post by graabein on 2008-11-01
Quod Libet and Ex Falso for music. VLC for video.

---

### Post by totfit on 2008-11-01
> **wersdaluv said:**
> 'Nuff said.

Mint Elyssa. The new X killed graphics acceleration capabilities for my nVidia card, because there are no longer drivers that will work. Tried and newer ATI card I had and though the drivers took, it didn't work either. So, for me 8.10 was a downgrade. Second update I have done over the short few years with Ubuntu that has made things worse for me rather than better. Course it is not the only distro that has had new releases that killed things for people. Oh well, may be less of a fanboy these days.

---

### Post by tromort on 2008-11-01
edited Chris's script :p

```
#!/bin/bash
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
echo Done adding medibuntu to sources list
sleep 3; 
sudo apt-get remove --purge rhythmbox tomboy gnome-games gnome-games-data ekiga example-content evolution evolution-common evolution-data-server evolution-webcal tracker f-spot
echo Done removing unneeded packages
sleep 3;
sudo apt-get install alien fusion-icon compizconfig-settings-manager emerald beagle apturl ubuntu-restricted-extras lastfm startupmanager conky youtube-dl ffmpeg gmusicbrowser vlc stopwatch thunar rpm unrar unace p7zip-full gparted wine nautilus-open-terminal nautilus-script-audio-convert nautilus-wallpaper pidgin-themes pidgin-extprefs pidgin-guifications pidgin-hotkeys gnome-art                                                                                                                                
echo Done installing packages
sleep 3;
sudo apt-get install libdvdcss msttcorefonts gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdnav4 libdvdread3 default-jre flashplugin-nonfree w64codecs
echo Done installing restricted packages
sleep 3;
sudo apt-get install gtk2-engines-blueheart gtk2-engines-cleanice gtk2-engines-geramilk gtk2-engines-magicchicken gtk2-engines-murrine gtk2-engines-mythbuntu gtk2-engines-nodoka gtk2-engines-pixbuf gtk2-engines-qtcurve gtk2-engines-qtpixmap gtk2-engines-sapwood gtk2-engines-thingeramik gtk2-engines-uubntulooks gtk2-engines-wonderland gtk2-engines-xfce gtk-engines-chtheme gtk-engines-begtk gtk-engines-eazel gtk-engines-geramik gtk-engines-mist gtk-engines-mono gtk-engines-qtpixmap gtk-engines-thingeramik gtk-engines-thinice gtk-engines-xenophilia
echo Done installing gtk-engines
sleep 3; 
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Now making a desktop icon to your home
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type boolean "true"
sleep 3;
echo Everything is removed and installed, have a nice day
```

---

### Post by billgoldberg on 2008-11-01
> **tromort said:**
> edited Chris's script :p

```
#!/bin/bash
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
echo Done adding medibuntu to sources list
sleep 3; 
sudo apt-get remove --purge rhythmbox tomboy gnome-games gnome-games-data ekiga example-content evolution evolution-common evolution-data-server evolution-webcal tracker f-spot
echo Done removing unneeded packages
sleep 3;
sudo apt-get install alien fusion-icon compizconfig-settings-manager emerald beagle apturl ubuntu-restricted-extras lastfm startupmanager conky youtube-dl ffmpeg gmusicbrowser vlc gscrot stopwatch thunar rpm unrar unace p7zip-full gparted wine nautilus-open-terminal nautilus-script-audio-convert nautilus-wallpaper pigin-themes pidgin-extprefspidgin-guifications pidgin-hotkeys ubuntu-tweak gnome-art                                                                                                                                
echo Done installing packages
sleep 3;
sudo apt-get install libdvdcss msttcorefonts gsfonts-x11 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdnav4 libdvdread3 default-jre flashplugin-nonfree w64codecs
echo Done installing restricted packages
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Now making a desktop icon to your home
gconftool-2 --set /apps/nautilus/desktop/home_icon_visible --type boolean "true"
sleep 3;
echo Everything is removed and installed, have a nice day
```

Why use a script when you can just put it in one big command with && and select, middle click it in the terminal?

I'm sure it's easier and faster for people to do that than to open the script from the terminal.

But using a script sounds more "tech savvy", doesn't it?

:p

---

### Post by Grant A. on 2008-11-01
I should probably clarify this: I use Kubuntu Intrepid Ibex, not ubuntu to make this list make more sense.

Firefox (Konqueror is much too slow and bloated for my tastes. Btw, synaptic and ubuntu software sources installed themselves along with FireFox on Intrepid, has anyone else noticed this?)
Gimp
Inkscape
The Mana World (tmw as it is known by the *buntu repositories)
Thunderbird
IDLE v2.5 (<3)
GParted
Irssi (Let's put it this way, you couldn't PAY ME to use konversation)

Here's the code if you guys want to install these:

```

sudo apt-get install gimp firefox thunderbird gparted irssi idle inkscape tmw

```

---

### Post by etnlIcarus on 2008-11-01
> Firefox (Konqueror is much too slow and bloated for my tastesFirst time I've heard this one.

---

### Post by Grant A. on 2008-11-01
> **etnlIcarus said:**
> First time I've heard this one.

I will admit, it is a strange comment, but try loading a web page in Konqueror and then in FireFox, you will see quite the speed difference in FireFox's favor.

---

### Post by tromort on 2008-11-01
> **billgoldberg said:**
> Why use a script when you can just put it in one big command with && and select, middle click it in the terminal?

I'm sure it's easier and faster for people to do that than to open the script from the terminal.

But using a script sounds more "tech savvy", doesn't it?

:p

;) it sure does, and I need a way to remember what to remove/install. Ofcourse 1 big line with &&'s could work but this looks a bit more organized :p

---

### Post by jomiolto on 2008-11-01
Here's a list of the things I've already added (just made a fresh installation last night):

[LIST]
[*]vim
[*]mplayer
[*]vlc
[*]thunderbird
[*]eclipse
[*]irssi
[*]rxvt-unicode-lite
[*]ruby1.8
[*]valgrind
[*]texlive
[*]openjdk-6-jdk
[*]netbeans
[*]lua50
[*]wesnoth-all
[*]doxygen
[*]graphviz
[*]cvs
[*]highlight
[*]lltag
[*]p7zip-full
[*]rar
[*]links
[/LIST]

(Just applications listed, not libraries, fonts, etc.)

I'm trying to keep it light (and not end up with 2300 installed packages), but I'll probably end up adding a lot more :)

---

### Post by Ralob on 2008-11-02
Wine
FBReader
Okular
Logjam
VMWare
KTorrent
Pidgin
Firefox 3
Open Office 3
K3b
Exaile
Last.fm Player
SMPlayer
Gnomad 2
Tellico/Alexandria 
Peazip

---

### Post by alanjackson on 2008-11-26
Which repository did you find rxvt in?

---

### Post by tom66 on 2008-11-26
Inkscape
Adblock (FF)
Opera (for testing)
Wine
Glade
Lampp for web server
php5-cli
irb (for ruby)

---

### Post by chris4585 on 2008-11-26
> **bigbrovar said:**
> i modified your script to my taste 
```

#!/bin/bash
sudo apt-get update
sudo apt-get remove --purge  tomboy ekiga evolution evolution-common evolution-data-server evolution-webcal  f-spot 
echo Done removing unneeded packages
sleep 3;
sudo aptitude install alien   compizconfig-settings-manager thunderbird xchat   amsn lastfm startupmanager htop cowsay irssi youtube-dl ffmpeg audacity libdvdcss2 vlc libdvdcss2 ubuntu-restricted-extras w32codecs amarok cheese virtualbox ffmpeg gparted wine zdesktop nautilus-actions nautilus-clamscan nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-wallpaper soundconverter soundkonverter-amarok pidgin-encryption pidgin-lastfm pidgin-libnotify pidgin-mpris pidgin-musictracker postgresql ssh skype audacity opera gthumb thinkfinger-tools  libpam-thinkfinger startupmanager mousepad irssi cbrpager comix k9copy k3b libk3b2-extracodecs aptoncd
sleep 3;
sudo apt-get upgrade
sleep 3;
echo Done upgrading
sleep 3;
echo Everything is removed and installed, can i live in peace now

```

cool looks like you're installing ffmpeg twice though

---

### Post by shadowdude1794 on 2008-11-26
Songbird
VLC 
Filezilla
Thunderbird
Nvidia drivers
Ubuntu tweak 
Phun
I'm missing a bunch... but that's all I can remember.

---

### Post by Corfy on 2008-11-27
Here are a few of my favorites:

Scribus
Inkscape
VLC Player
KompoZer
Bibletime
Celestia
SuperTux
LinCity-NG
Wormux
FileZilla
SeaMonkey
gLabels
GnuCash
ClamAV
KeePassX
Avidemux

---

### Post by ubuntu27 on 2008-11-28
Let's see... ALL OF THE FALLOWING IS IN THE RESPOSITORY

[gnome-do ]("http://do.davebsd.com/") (Dosn't need introduction :P If you don't know about this app, visit its website)

gbrany  (Brain Trainer educational game)

mastermind (Code Breaker game)

[gjiten]("http://gjiten.sourceforge.net/")  (Japanese Dictionary for Gnome)

[gtk-recordMyDesktop]("http://recordmydesktop.sourceforge.net/about.php") (What the name says. It records everything you do in a Video)

[Qalculate!]("http://qalculate.sourceforge.net/") (A powerful calculator)

[Comix]("http://comix.sourceforge.net/")  (Comic or Manga Viwer)

---

