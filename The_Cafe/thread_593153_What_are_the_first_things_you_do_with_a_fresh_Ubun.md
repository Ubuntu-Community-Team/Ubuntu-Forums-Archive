---
title: "What are the first things you do with a fresh Ubuntu Gutsy install?! :)"
date: 2007-10-26
forum: The Cafe
---

### Post by wersdaluv on 2007-10-26
Many people does not keep their Ubuntu vanilla. I want to know what you do with your fresh Ubuntu Gutsy. 

:guitar:

---

### Post by PurposeOfReason on 2007-10-26
Install fluxbox. I don't use fluxbuntu, not too sure why. Then I get conky because it's a must.

---

### Post by wersdaluv on 2007-10-26
As for me, I

[LIST]
[*]stop tracker from running
[*]install Basket Notepads
[*]use clearlooks
[*]remove the "ubuntu" value for libnotify
[*]use the History and libnotify plugins for Pidgin
[*]remove the Deskbar applet and the User Switcher applet (they're good but I want a lighter desktop. the deskbar is just too heavy for me :P and the User Swithcer is useless since I am the only user)
[*]set alt+space  as "run command"
[*]set F9 as the shortcut for "minimize window"
[*]set F10 as the shortcut for "maximize window"
[*]set Alt+F10 as shortcut for "make window fullscreen"
[*]set alt+z as "play/pause"
[*]set alt+x as "previous track"
[*]set alt+v as "next track"
[*]install Stardict
[*]install K3b
[*]setup my Pocket PC syncing with multisync
[*]add "force quit" to panel
[*]add synaptic's, and terminal's shortcut to panel
[*]use a wallpaper from desktopography
[*]install Skype
[*]install Xchat
[*]install stumbleupon firefox addon
[*]install Ubuntu Restricted Extras
[/LIST]

I'll add more.. 

:KS

---

### Post by osxcapades on 2007-10-26
> **PurposeOfReason said:**
> Install fluxbox. I don't use fluxbuntu, not too sure why.

I believe Fluxbuntu has yet to release a stable distribution.

---

### Post by Flying caveman on 2007-10-26
Get online and watch porn: You know, just to see if all the multimedia stuff is installed correctly.:)

---

### Post by Can+~ on 2007-10-26
[LIST]
[*]install build-essentials
[*]install ati driver <lots of stuff> enable compiz
[*]install banshee
[*]pimp out the interface with emerald, change the panels bgs, and install snow-apple icons... and get a new background.
[*]kill tracker :mad:
[*]etc.
[/LIST]

---

### Post by santiagoward2000 on 2007-10-26
The first thing I did was installing all the restricted drivers and Compiz-Fusion (I use Xubuntu, it doesn't come with Compiz).

---

### Post by thelocust on 2007-10-26
Break it. Don't ask me how.

---

### Post by santiagoward2000 on 2007-10-26
> **thelocust said:**
> Break it. Don't ask me how.

:lolflag: OK, I won't. But I'm really curious...

---

### Post by Anessen on 2007-10-26
Disable tracker (I don't get why this is a default)

Install my favourite Firefox extensions (Adblock, Foxmarks, Stumbleupon, TOR button, Download Statusbar)
Install nVidia drivers
Set up dual monitors
Install TOR
Install Amarok
Set up Pidgin
Install Build-Essential
Customise the interface
Customise the Gnome Terminal
Install Conky

---

### Post by Billy_McBong on 2007-10-26
[COLOR="Blue"]the first thing i do is customize the panel(s) to the way i like it

enable extra repos 
i install favorite programs/extensions/plugins
disable recent documents
customize compiz fusion[/COLOR]

---

### Post by professor fate on 2007-10-26
I work on the sound card.

---

### Post by Crashmaxx on 2007-10-27
Remove tracker, then get any codecs and media players I want, then install Swiftfox and the needed extensions.

---

### Post by Spr0k3t on 2007-10-27
Remove mono, mono related applications, and tracker.
Change the background
Change the icons (more tango than human)
Remove the lower panel
Remove parts of the upper panel
Configure dual head
Install my custom emerald theme.

I always add these applications, looking for more to choose from.
AcidRip
Wormux
FrozenBubble
OpenArena
PPR
Warzone2100
XMoto
InkScape
Deluge
XChat
weechat
links2
Ex-Falso
Quod Libet
VLC

The key here, removing mono.  To me, not having mono installed is critical.  Not because the implementation is bad, but rather due to where the framework originates from.

---

### Post by Martje_001 on 2007-10-27
```
#! /bin/bash
# Systeem updaten
gksudo "apt-get update"
sudo apt-get -y upgrade

# Programma's installeren
sudo apt-get -y install amarok inkscape myspell-nl mozilla-thunderbird filezilla filezilla-locales language-pack-gnome-nl language-pack-gnome-nl-base language-pack-kde-nl language-pack-kde-nl-base language-pack-nl language-pack-nl-base language-support-nl miro ubuntu-restricted-extras audacious audacity
#wget http://www.frostwire.com/download/?os=ubuntu
#sudo dpkg -i frostwire*.deb

# Programma's verwijderen
sudo apt-get -y remove ekiga rhythmbox tomboy pidgin

# Instellingen aanpassen
wget -c http://www.xs4all.nl/~mgj1/Flower-100.jpg
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/$USER/Flower-100.jpg"
gconftool-2 --type int --set /apps/panel/toplevels/bottom_panel_screen0/background/opacity "11497"
gconftool-2 --type int --set /apps/panel/toplevels/top_panel_screen0/background/opacity "11497"

# Opruimen
sudo apt-get -y autoremove
sudo apt-get clean
rm frostwire*.deb

# Meldingen weergeven
zenity --info --text="Geselecteerde programma's zijn geinstalleerd, uw systeem is up-to-date, en aanpassingen zijn gemaakt."
```
:D

---

### Post by Spike-X on 2007-10-27
Do it over, because I always fook something up.

---

### Post by jayaramk on 2007-10-27
whats that tracker... everyone's talking about tracker... what does it do?? and how do i disable it??? 
is it about the indexing tracker??? how to disable it??

---

### Post by jayaramk on 2007-10-27
and me initially i install

banshee
bluefish
vlc
open arena
liferea fedd reader
LAME server

---

### Post by RebateFX on 2007-10-27
1) create ~/.config/xserver-xgl/disable because on my ATI based laptop, 3D GL Desktop stuff sux. At least if I want to play a video anyway. :/

2) Enable restricted repositories and add the extra ones with cool stuff.

3) Install Pidgin, Skype, Minbar, Zekr, GoogleEarth, Metatrader4 under WINE and a load of other stuff

4) Install Enemy Territory and get frag happy :D

---

### Post by Onyros on 2007-10-27
Add me to the "Disable Tracker" list.

I get the idea, but it REALLY shouldn't be enabled by default.

---

### Post by gn2 on 2007-10-27
After installing 7.10 on my laptop the first thing I did was replace it with 7.04 because it just would not work properly.

Toshiba Portege 3440CT, other similar laptops have the same problems.

---

### Post by beercz on 2007-10-27
login

---

### Post by stomponthis on 2007-10-27
Compiz, AWN, and give everything a nice look :-)
and then install aps, nvidia drivers etc etc
Pretty normal stuff :-P

---

### Post by weatherman on 2007-10-27
enable medibuntu repository and install libdvdcss

---

### Post by syxbit on 2007-12-04
```

#!/bin/sh
#
#

echo *****removing junk*****
sudo apt-get remove -y evolution evolution-common pidgin pidgin-data
#note, i only remove pidgin cause i compile the latest version
#i do however permanently delete evolution!

echo *****copying*****
#cp sources.list /etc/apt/sources.list
cp bashrc /home/syxbit/.bashrc
cp T61.xorg.conf /etc/X11/xorg.conf
cp face /home/syxbit/.face

echo *****installing*****
apt-get -y update
apt-get -y upgrade
aptitude install -y brasero audacious listen nvidia-glx-new vlc tagtool mozilla-thunderbird dict compizconfig-settings-manager
aptitude install -y qalculate-gtk htop sleuthkit md5deep openssh-server unrar emerald msttcorefonts subversion

echo *****installing nautilus scripts*****
aptitude install -y nautilus-actions nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-wallpaper



echo *****installing compiling stuff*****
aptitude install -y build-essential autoconf libtool automake gettext
apt-get build-dep pidgin

echo *****extras*****
#sudo aptitude install -y sun-java6-jre sun-java6-plugin sun-java6-fonts

echo *****codecs*****
aptitude install -y ubuntu-restricted-extras
#aptitude install -y gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-extracodecs 
#dpkg -i w32codecs_20061022-0.0_i386.deb libdvdcss2_1.2.9-1_i386.deb


#echo *****restore*****
#rm -R ~/.mozilla ~/.mozilla-thunderbird ~/.purple
#cp -R ../backup/.mozilla
#cp -R ../backup/.mozilla-thunderbird
#cp -R ../backup/.purple


echo *****cleaning*****
sudo aptitude autoclean -y
sudo aptitude clean -y
#source ~/.bashrc


#find and replace with regular expressions
# replaces 'no' with 'yes' in the file /etc/default/rcS
#perl -p -i -e 's/UTC=yes/UTC=no/' /etc/default/rcS


#fix grub
sudo perl -p -i -e 's/timeout\t+10/timeout\t\t3/' /boot/grub/menu.lst
sudo perl -p -i -e 's/#hiddenmenu/hiddenmenu/' /boot/grub/menu.lst

```

---

### Post by DasCrushinator on 2008-01-11
> **wersdaluv said:**
> As for me, I

[LIST]
[*]remove the "ubuntu" value for libnotify
[*]use the History and libnotify plugins for Pidgin
[/LIST]

I'll add more.. 

:KS

How do you do these things?

---

### Post by Perpetual on 2008-01-11
1. Fix usplash.conf so it doesn't take 3 minutes to boot.
2. Disable sounds.
3. Change Software Sources to include backports.
4. Install powertop, startupmanager, compizconfig-settings-manager.
5. Install Firefox addons - TabMixPlus, Download Statusbar.
6. Aptitude Update.
7. Install Codecs, Flash & Java.

Then it's about how I need it so that I can get going.

---

### Post by nikoPSK on 2008-01-11
Install awn and awn curves,
Set up my audigy to be used as default
install tvtime and configure drivers from my pvr
change my background
add my other hard drive to fstab
configure my accounts (IM) on pidgin
Install inkscape
Install avatar-factory
Install wine
Install audacity
Configure totem for dvd playback
Install deluge and xchat
Configure compiz to my needs.


This takes about half an hour. plus the install of gutsy so about an hour an a half total on an lfs install to get it to my liking.

---

### Post by Lobinho on 2008-01-28
What is tracker?

---

### Post by Martje_001 on 2008-01-28
> **Lobinho said:**
> What is tracker?
The most useless piece of software on earth if you ask me ;). It indexes your email and files to 'speed up' your searches. Well.. that whole tracker-thing can't find anything for me :/

---

### Post by FuturePilot on 2008-01-28
Some have had problems like that with Tracker
[http://ubuntuforums.org/showthread.php?t=583134]("http://ubuntuforums.org/showthread.php?t=583134")
Happened to me once.
This fixed it though
```
killall trackerd
trackerd -v 2 -R
```
Forces a re-index.

---

### Post by wilsonmuse on 2008-01-28
> **gn2 said:**
> After installing 7.10 on my laptop the first thing I did was replace it with 7.04 because it just would not work properly.

Toshiba Portege 3440CT, other similar laptops have the same problems.

Exact same process for me, except on a Compaq Presario R3000

---

### Post by ingvildr on 2008-01-28
Install all updates and install nvidia graphics driver
reboot
Remove the top gnome panel and configure the bottom panel to have things like the menu bar and tomboy
Make it so there is only one virtual desktop
Install the compiz settings manager and set only a few plugins such as alt-switcher and minimize effects
Install deluge from website
Install tango-generator + generate theme :)
Use the gummygilouche gtk style plus grab the clearlooks metacity theme from svn which fixes some compiz related bugs
Then just add libdvdcss and codecs to play mp3's

---

### Post by fatality_uk on 2008-01-28
Get on with some work! Seeing as I don't have to ffaff about usually finding CD's for every bit of hardware that I have installed. ;)
Ubuntu 1 : Windows 0

---

### Post by sailor2001 on 2008-01-28
ever since it was beta, haven't finished installing apts..always something I haven't seen before.......

---

### Post by GamingMazter on 2008-01-28
I first tried Ubuntu just because of the effects but then started to love it and changed permanently from Vista. Vista was just way too buggy and got about 100 viruses every day (literally). Anyway...basically what I'm saying is the first thing I did was set up my graphic effects!

---

### Post by LaRoza on 2008-01-28
Copy my home directory from my other installation and instantly transfer all configurations and settings.

Then install Opera.

---

### Post by kernelCompile on 2008-01-28
> **wersdaluv said:**
> Many people does not keep their Ubuntu vanilla. I want to know what you do with your fresh Ubuntu Gutsy. 

:guitar:

Just started wtih Kubuntu. The first thing I did was set the root password, and modify the sudoers file to require the root password for root access.

I also modified startup scripts to make runlevel 3 console only and allow the runlevel to be set at the boot prompt. I left the default runlevel at 2 though. I don't insist that **everything** be just like other Linux distros, but I do like to be able to boot to the console to do a quick edit and reboot when I'm tweaking sutf. It makes it a lot quicker if I don;t have to wait for the GUI to start up.

---

### Post by kernelCompile on 2008-01-28
> **thelocust said:**
> Break it. Don't ask me how.

If you knew how, you'd stop doing it, wouldn't you?

---

### Post by nat6138 on 2008-01-29
Install Hardy.

---

### Post by MadsRH on 2009-02-25
> **nat6138 said:**
> Install Hardy.

I know it's a bit late, but that's just funny! :lolflag:

Great answer!

---

### Post by Grant A. on 2009-02-25
> **MadsRH said:**
> I know it's a bit late, but that's just funny! :lolflag:

Great answer!

Apparently necromancy is the first thing you do with a fresh Hardy install. ;)

---

### Post by ArtF10 on 2009-02-25
> **MadsRH said:**
> I know **it's a bit late**, but that's just funny! :lolflag:

Great answer!

Dear sir, you are in possession of **[COLOR="Magenta"]good[/COLOR] thread digging** abilities.

---

