---
title: "how did my system automatically update to 16.04?"
date: 2015-11-22
forum: Ubuntu Development Version
---

### Post by Psy8cho on 2015-11-22
Dear Ubuntu users,

How did my system automatically update to 16.04? I did not do this myself? and I did not went through an installation procedure as I did when I updated from 15.04 to 15.10.
I first noticed it when I added a ppa and it resulted in a xenial main... 
Also it could not find the piece of software I was looking for, so I manually changed it to wily main, however it still can't find it. Is this also a result of beeing on 16.04?

I searched how to check my version and used the following
```
lsb_release -a
```
output:
```
[FONT=monospace][COLOR=#000000]No LSB modules are available.[/COLOR]
Distributor ID: Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:        16.04
Codename:       xenial[/FONT]
```

KInfoCenter also shows Kubuntu 16.04

Muon Update Manager settings
Kubuntu Software: all checked (now turned source code off, just to be safe)
Other Software: Canonical Partners (now xenial distro, under edit), some ppas
Updates: Important security updates, Recommended updates, Unsupported updates (turned off now to be safe), show new distribution releases: normal releases

Also no errors seemed to have happened, and everything seems to be working fine (other than the normal 15.10 bugs). I would suspect some errors in a development branch?

Am I really on the development branch? I don't want to be on the development branch. What do I do now and how did this happen?

---

### Post by kansasnoob on 2015-11-22
Would you mind posting your .bash_history? It's in home as a hidden dot file:

```
lance@lance-desktop:~$ ls -a
.              .dbus       .gnupg           .mozilla_OLD  .thunderbird
..             Desktop     .gphoto          Music         .thunderbird_OLD
.adobe         .dmrc       .gstreamer-0.10  .nv           .thunderbird_OLDER
**[COLOR="#FF0000"].bash_history[/COLOR]**  Documents   .gvfs            Pictures      Videos
.bash_logout   Downloads   .hplip           .pki          .Xauthority
.bashrc        .fltk       .ICEauthority    .profile      .xsession-errors
.cache         .gconf      .local           Public        .xsession-errors.old
.compiz        .gksu.lock  .macromedia      .ssh
.config        .gnome      .mozilla         Templates

```

It would be interesting to see how this could have happened.

---

### Post by grahammechanical on 2015-11-22
I do not think that update manager is programmed to upgrade us to a development branch. It is programmed to notify us of next available releases whether LTS or interim depending on the setting. It would not upgrade without our authorisation. But there are commands that a user can run that would do this.

```
update-manager -d
```

or

```
do-release-upgrade -d
```

It is the -d switch that upgrades to the development branch.

Regards.

---

### Post by sgage on 2015-11-22
> **kansasnoob said:**
> Would you mind posting your .bash_history? It's in home as a hidden dot file:

```
lance@lance-desktop:~$ ls -a
.              .dbus       .gnupg           .mozilla_OLD  .thunderbird
..             Desktop     .gphoto          Music         .thunderbird_OLD
.adobe         .dmrc       .gstreamer-0.10  .nv           .thunderbird_OLDER
**[COLOR="#FF0000"].bash_history[/COLOR]**  Documents   .gvfs            Pictures      Videos
.bash_logout   Downloads   .hplip           .pki          .Xauthority
.bashrc        .fltk       .ICEauthority    .profile      .xsession-errors
.cache         .gconf      .local           Public        .xsession-errors.old
.compiz        .gksu.lock  .macromedia      .ssh
.config        .gnome      .mozilla         Templates

```

It would be interesting to see how this could have happened.

Something exceedingly odd is going on here. What program do you use to update your system? But no program should have offered you an upgrade to a development version, much less just gone and done it automatically. Much more information needed.

---

### Post by sgage on 2015-11-22
What do you see if you type 'uname -r' in a term?

What ppa did you last add that seemed to bring this on?

An upgrade from Wily to Xenial would take some time - the downloading and the installations - did you not notice anything strange going on?

Look at /etc/apt/sources.list - does it show all xenial entries, or wily?

---

### Post by sgage on 2015-11-22
> **grahammechanical said:**
> I do not think that update manager is programmed to upgrade us to a development branch. It is programmed to notify us of next available releases whether LTS or interim depending on the setting. It would not upgrade without our authorisation. But there are commands that a user can run that would do this.

```
update-manager -d
```

or

```
do-release-upgrade -d
```

It is the -d switch that upgrades to the development branch.

Regards.

That is my understanding. Though I'm not at all familiar with KDE/Kubuntu update tools...

---

### Post by Psy8cho on 2015-11-22
Thnx for all the quick responses! I will do my best to answer all questions. I am fairly new to Linux, but I am doing my best.

I have run ```
sudo do-release-upgrade -m desktop -f DistUpgradeViewKDE -d
``` before, but this was to help me go from 15.04 to 15.10. I checked my .bash_history and I have only ran it once. Also back then I went through a whole procedure, which failed at first using the normal method in Muon and I think that's why I used the terminal version to complete the failed upgrade. So that -d means development branch? So I should nerver run it with -d?

uname -r output:
```
[FONT=monospace][COLOR=#000000]4.2.0-19-generic[/COLOR][/FONT]
```

/etc/apt/sources.list shows xenial everywhere unfortunately...
I did once try to use proprietary drivers from the wily-proposed, because I am having issues with that. However this did not work and I reverted all changes. Right now it's commented in sources.list

Which ppa I added doesn't really matter because I already saw the Kubuntu 16.04 before that in KInfoCenter. I think I saw it yesterday already so nothing to do with today. I did noticed something strange this morning. Yesterday it just booted normally, however this morning my boot got stuck on the splash screen which it does when my video driver is beeing annoying. I have to run 'aticonfig --initial' to fix this. However I did see an update coming by of flgrx, so maybe it was just that. Anyone interessted in fixing my [driver issue]("http://ubuntuforums.org/showthread.php?t=2298637&p=13372107#post13372107") :)

.bash_history

```
sudo sufirefox
sudo apt-get
sudo apt-get update
hostname
hostname Rik
sudo hostname Rik
hostname
help vi
vi
kate
cd /etc/hostname
cd /etc
help
clear
help
info bash
gedit
kate hostname
sudo kate hostname
kate hostname
~
cd ~
sudo kate /etc/hostname
clear
bash
sudo kate /etc/hosts
alias resetcolors='konsoleprofile colors=LinuxColors'
reset
set background=light
ls
sudo apt-get sakura
sudo apt-get pantheon
sudo apt-get install pantheon
sudo apt-get install sakura
kate ~/.bashrc
reset
sudo apt-get install sakura
sakura
logout
exit
help logout
restart
help restart
help mv
mv ~/.kde ~/.kde.old
mv ~/.cache ~/.cache.old
help shutdown
shutdown -r now
ls
cd .cache
ls
cd ..
ls
ls-a
help ls
info ls
ls -a
clear
ls -a
kquitapp plasmashell
plasmashell &
cd .kde
ls -a
cd ~/.config
ls -a
cp -i plasma* ~/plasma-config-backup/
cp -i -r plasma* ~/plasma-config-backup/
cp -i -r plasma* ~/plasma-config-backup/backup-2015-10-04
pwd
shutdown -r now
plasmashell
ls
cd plasma-config/
ls
ls - a
ls -a
info mkdir
help mkdir
cd ~
cd .config/plasma
cd .config/plasma/
ls -a
cd .config
ls -a
find . -name "plasma*"
find -name "plasma*"
cd .
ls -a
cd .
cd ..
cd .config
find -name plasma-localerc
ls -a
find plasma*
plasmashell
rm plasma-org.kde.plasma.desktop-appletsrc 
mv plasma* ~/plasma-config/
plasmashell
ls -a
cp plasma-org.kde.plasma.desktop-appletsrc ~/plasma-config/
ls -a
plasmashell
cd plasma-config/
ls -a
mv -i * ~/.config/
ls -a
cp * ~/.config/
ls -a
cd ..
mv plasma-config plasma-config-backup
ls
cd plasma-config-backup/
ls
ls -a
cd plasma-workspace/
ls -a 
cd ..
ls -a
touch location.txt
echo '/home/.config' > location.txt
cat location.txt 
ls
mkdir backup-2015-10-04
mv !(location.txt) backup-2015-10-04/
rm backup-2015-10-04/
rm -r backup-2015-10-04/
mv !(location.txt) backup-2015-10-04/
ls
mkdir backup-2015-10-04
ls
cd backup-2015-10-04/
ls
help apt-get
info apt-get
info apt-get remove sakura
apt-get remove sakura
sudo apt-get remove sakura
kate ~/.baschrc
cat ~/.baschrc
ls -a
cat ~/.baschrc
cat ~/.bashrc
kate ~/.baschrc
kate ~/.bashrc
ls
ls -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc
ls -a
ls
sudo blkid
clear
sudo blkid
clear
sudo blkid
sudo vi /etc/fstab
sudo kate /etc/fstab
sudo blkid
cd /usr/X11R9
cd /usr/
ls
ls -a
cd ~/ect
cd /ect
cd /ect/
cd ..
cd etc
cd ..
cd /etc/
cd /usr/
cd /etc/
clear
ls -a
clear
ls -a
cd x11
cd X11
ls -a
sudo kate xorg.conf
/sbin/lsmod | grep fglrx
/sbin/lsmod | grep radeon
-`lscpi | grep VGA'
lscpi | grep VGA
lspci | grep VGA
lspci
cd ~
xrandr
lspci | grep VGA
arandr
cd /home/rik/
cd /home/rik/.config/autostart
ls -a
cd etc/X11
cd /etc/X11
ls -a
sudo kate xorg.conf
cd /usr/bin
ls -a
cd aticonfig
kate aticonfig
fglrxinfo
lspci -vvnn | grep VGA
clear 
lspci -vvnn | grep VGA
lshw -C video
clear
lshw -C video
sudo lshw -C video
clear
lspci | grep VGA
sudo kate /etc/X11/xorg.conf
aticonfig --lsa
sudo amdcccle
sudo kate /etc/X11/xorg.conf
steam
sudo apt-get install steam
sudo apt-get install conky
sudo apt-get install flashplugin-installer
sudo apt-get install skype
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo add-apt-repository "deb http://archive.canonical.com/ubuntu $(lsb_release -sc) partner"
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install skype
skype
steam
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade
sudo aptitude
skype
sudo do-release-upgrade -m desktop -f DistUpgradeViewKDE -d
sudo apt-get install fglrx-updates
sudo dpkg --configure -a
sudo apt-get install fglrx-updates
sudo apt-get update
cd /var/lib/dpkg/updates
ls
remove *
rm *
sudo rm *
ls
ls -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-updates
sudo aticonfig --initial
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-updates
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-updates
sudo aticonfig --initial
dmesg | grep fglrx
ubuntu-drivers devices
ubuntu-driver list
ubuntu-drivers list
cp /media/rik/Backup/Linux /media/rik/RIK_USB/Linux -v
sudo cp /media/rik/Backup/Linux /media/rik/RIK_USB/Linux -v
sudo cp /media/rik/Backup/Linux /media/rik/RIK_USB/Linux -vr
sudo service lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u
sudo reboot
ubuntu-drivers devices
ubuntu-drivers list
ubuntu-drivers autoinstall
sudo ubuntu-drivers autoinstall
sudo kate /etc/apt/sources.list
touch /etc/apt/preferences.d/proposed-updates
sudo touch /etc/apt/preferences.d/proposed-updates
sudo kate /etc/apt/preferences.d/proposed-updates
sudo apt-get upgrade -s
sudo apt-get update
sudo apt-get upgrade -s
sudo install fglrx-updates/wily-proposed fglrx-amdcccle-updates/wily-proposed fglrx-updates-core/wily-proposed
sudo kate /etc/apt/preferences.d/proposed-updates
sudo apt-get update
sudo apt-get upgrade -s
sudo install fglrx-updates/wily-proposed fglrx-amdcccle-updates/wily-proposed fglrx-updates-core/wily-proposed
sudo kate /etc/apt/preferences.d/proposed-updates
sudo kate /etc/apt/sources.list
sudo apt-get install fglrx-updates/wily-proposed fglrx-amdcccle-updates/wily-proposed fglrx-updates-core/wily-proposed
sudo kate /etc/apt/sources.list
sudo apt-get install flashplugin-installer
sudo apt-get install pepperflashplugin-nonfree
fglrxinfo
fglrxinfo
sudo apt-get update
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bakhybrid
cd /etc/X11
ls
ls -a
cd ..
cd /
cd ~
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
sudo reboot
sudo apt-get install p7zip-full
kate usr/share/ati/fglrx-install.log
cd usr/share/ati/
cd usr
kate /usr/share/ati/fglrx-install.log
sudo apt-get install linux-headers-4.2.0-17-generic
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot lib32gcc1
cd /media/rik/Backup
cd Linux
ls
cd drivers
ls
7z x amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.zip
ls
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
ls
ls -a
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
ls -a
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo apt-get install dh-make dh-modaliases execstack libc6-i386 lib32gcc1
sudo apt-get install linux-headers-generic
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo apt-get update
sudo apt-get upgrade
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudosh ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
ls
sh AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo sh AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo sh AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run --buildpkg Ubuntu/wily
ls
ls -a
sudo sh ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run --buildpkg Ubuntu/wily
sudo dpkg -i fglrx_*.deb
ls
sudo apt-get install -f
sudo apt-get update -fix-missing
sudo apt-get update-fix-missing
sudo apt-get update -fix -missing
sudo dpkg -configure -a
sudo apt-get update &#8211;fix-missing
sudo apt-get --fix-broken install
sudo dpkg --configure -a 
sudo sh ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run --buildpkg Ubuntu/wily
ls
cd fglrx-install.hKvj6p/
ls
cd packages/
ls
cd Ubuntu/
ls
ls -a
cd ..
cd..
cd ..
ls
rm fglrx-install.*
rm fglrx-install.* -r
ls
chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo chmod +x AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run 
sudo sh AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run
sudo apt-get install linux-headers-$(uname -r)
kate /usr/src/linux/include/linux
cd /usr/src/linux/include/linux
cd /usr/src/linux/include/
cd /usr/src
ls
ls -a
cd linux-headers-4.2.0-17
ls
cd inlcude
cd ..
cd linux-headers-4.2.0-17-generic/
ls
cd include
ls
cd linux
ls
kate version.h
lspci | grep VGA
sudo apt-get install xserver-xorg-video-intel
ls
cd /etc
ls
cd X11
ls
kate xorg.conf
kate xorg.conf.original-0
kate xorg.conf.original-1
kate xorg.conf.bak
kate xorg.conf.10122015 
kate xorg.conf.11092015 
kate xorg.conf.bakhybrid 
sudo apt-get install mesa-utils 
sudo apt-get remove mesa-utils 
cat /etc/X11/xorg.conf
lspci
clear
lspci
cd /usr/share/X11
ls
cat xorg.conf.d
cd xorg.conf.d/
ls
cat 50-synaptics.conf 
glxinfo | grep -i "Direct Rendering"
sudo apt-get install mesa-utils 
glxinfo | grep -i "Direct Rendering"
glxgears
cd /etc/X11/
ls
X -configure
sudo X -configure
sudo reboot
mono
sonar
mono
ls
gparted
sudo apt-get install gparted
gparted
sudo gparted
skype
sudo apt-get update
sudo apt-get upgrade
sudo mount -t "ntfs" -ro
blkid
blkid help
help blkid
info blkid
sudo kate /etc/fstab
sudo fdisk -1
clear
sudo fdisk -1
sudo blkid
clear
sudo blkid
sudo fdisk -l
id
sudo mkdir /media/rik/Backup
sudo mount -a
sudo blkid
clear
sudo blkid
sudo fdisk -;
sudo fdisk -l
sudo mount -o remount,rw /dev/sdc1 /media/rik/Backup
dmesg | grep hfs
dmesg | grep ntfs
sudo apt-get update
cp /home/rik/Pictures/Wallpapers/600255.jpg /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/splash/images/
sudo cp /home/rik/Pictures/Wallpapers/600255.jpg /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/splash/images/
sudo cp /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/splash/Splash.qml /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/splash/Splash.qml.bak
sudo cp /home/rik/Pictures/Wallpapers/600255.jpg /usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/components/artwork/background.jpg
/usr/share/plasma
cd /usr/share/plasma
cd look-and-feel/org.kde.breeze.desktop/
ls -a
cd contents/
ls
cd splash
ls
sudo kate Splash.qml 
vbeinfo
sudo update-grub
sudo kate /etc/default/grub
sudo update-grub
sudo kate /etc/default/grub 
cd /etc/default/
ls
ls -a
sudo update-grub2
cd /boot/grub
ls
cd x86_64-efi/
ls
cd ..
clear
ls
cat grub.cfg
clear
cat grub.cfg
clear
kate grub.cfg
sudo kate /etc/default/grub 
cat /etc/default/grub
sudo update-grub
sudo kate /etc/default/grub 
sudo update-grub
cat /etc/default/grub 
sudo kate /etc/initramfs-tools/conf.d/splash
cd /etc
ls
cd .local
cd initramfs-tools/
ls
cd conf.d
ls
ls -a
cd ~
ls
cd ~/Downloads/
cd ~/Downloads && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
ls
ls -a
~/Downloads/.dropbox-dist/dropboxd
dropbox
sudo apt-get install nautilus-dropbox
sudo apt-get install deluge-web
deluge-web
deluge
sudo apt-get install deluged
sudo kate ~/.config/deluge/webui06.conf
cd /etc/profile
cd /etc/deluge
cd ~/.config/deluge
ls -a
cd ..
ls
cd ~/.config/deluge
ls
cat web.conf
ls
cd ssl
ls
cat daemon.cert
cat daemon.pkey
cd ..
ls
cat core.conf
ls
ls -a
cat auth
cat web.conf
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
sudo apt-get remove kodi
kodi
cd /home
cd ~
cd /home/rik
plex
plexhometheater
plexmediaserver
sudo service plexmediaserver start
sudo /etc/init.d/plexmediaserver start
cd /etc/init.d
ls
sudo service plexmediaserver start
lsb_release -a 
skype



```

---

### Post by kansasnoob on 2015-11-23
I think this is probably what got you to Xenial:

```
sudo do-release-upgrade -m desktop -f DistUpgradeViewKDE -d
```

I've never used that many suffixes though. In fact I always use the GUI so if I want to go from latest stable to dev I'll run:

```
update-manager -d -c
```

Regardless you're now running a pre-alpha unstable OS. In the future you should be more cautious and ask for details about what commands do before jumping in head first.

---

### Post by Psy8cho on 2015-11-23
But I only ran that command once when I was upgrading from 15.04 to 15.10. If what you're saying is true then I will always upgrade automatically to the next version? so how do I turn this off? or how do I revert back to 15.10?

---

### Post by zika on 2015-11-23
By using -d switch You've forced/requested to upgrade to devel-version.
(Use manual: ```
man do-release-upgrade
```... )

---

### Post by Psy8cho on 2015-11-23
Ok either I don't understand the implications and the command I used or I am not explaining this very well :P
I only ran that command once when I was upgrading from 15.04 to 15.10, that was ..-10-2015 and I upgraded to 15.10 back then. How can it happen that whithout my consent and without running this command again, I end up in 16.04 nearly 2 months later?

If this really happened this way I need to know how to disable this, otherwise, without my consent, I will again upgrade to 16.10... without doing anything...

---

### Post by kansasnoob on 2015-11-23
Where did you find that command?

---

### Post by grahammechanical on 2015-11-23
If 15.10 was already released at the time you ran that command, then the only development version available was Xenial Xerus (16.04). I cannot speak for Kubuntu but as far as Ubuntu is concerned there is no visual difference between the released 15.10 and the development branch of 16.04. I suspect that the same is true of Kubuntu Xenial Xerus.

Running the command with sudo forced you to authorise the action.

Regards.

---

### Post by Psy8cho on 2015-11-23
well yes 15.10 was already released, so I guess that is my problem... thnx for helping me find a logical explaination for this! :)

OK so I have googled downgrading. So it seems this is somewhat possible, but might also bring a lot of problems with it. What should my next move be? Is it best to stay at 16.04 (until release), but somehow set it up in a way I only receive updates from wily and then set it back? Because nothing seems broken yet, I would like to keep it that way. Because now I am afraid of using 'sudu apt-get upgrade'.

---

### Post by sgage on 2015-11-23
> **Psy8cho said:**
> well yes 15.10 was already released, so I guess that is my problem... thnx for helping me find a logical explaination for this! :)

OK so I have googled downgrading. So it seems this is somewhat possible, but might also bring a lot of problems with it. What should my next move be? Is it best to stay at 16.04 (until release), but somehow set it up in a way I only receive updates from wily and then set it back? Because nothing seems broken yet, I would like to keep it that way. Because now I am afraid of using 'sudu apt-get upgrade'.

If I were you, I would without question backup my data and do a clean install of Wily, then restore my data. It's really quite easy. You are proposing rather fiddly scenarios (only receive updates from wily? what does that even mean in the context of xenial?, and it's so much simpler to just do a clean install. 

Or just stick with xenial and come along for the ride :KS

---

### Post by kansasnoob on 2015-11-23
I use Ubuntu GNOME so don't know much about Kubuntu but just a bit of googling leads me to believe that the suffixes you used may have edited a configuration file related to "DistUpgradeViewKDE". That's why I'd like to know where you learned that command. The source of the problem could be helpful in avoiding this again.

---

### Post by Psy8cho on 2015-11-23
@kansasnoob yes you're right, I would like to find the source of the problems as well. However I can't find out where I found that command. :( I might have found it in Kubuntu itself, when upgrading the distro in gui you have to give permissions and it shows the command. I think I copy pasted that.

@sgage yes I have been wondering about how much settings and stuff linux holds in it's /home directory. It's on a seperate partition from / so I should be good. So what all would I have to 'redo' in the senario of reinstalling Kubuntu wily? Because I have quite a lot of settings in the KDE desktop environment. If it would be deleted, how do I back it up and put it back?

---

### Post by matt_symes on 2015-11-23
Hi

```
-f DistUpgradeViewKDE
```

I'm pretty sure that this does an unattended upgrade for a system so you don't get asked any questions, no prompts.

Pretty similar to an unattended install using a preseed file.

Maybe that's what happened to upgrade your system :)

Kind regards

---

### Post by kansasnoob on 2015-11-24
> **matt_symes said:**
> Hi

```
-f DistUpgradeViewKDE
```

I'm pretty sure that this does an unattended upgrade for a system so you don't get asked any questions, no prompts.

Pretty similar to an unattended install using a preseed file.

Maybe that's what happened to upgrade your system :)

Kind regards

Aha! So you wouldn't be presented with a prompt telling you it'll upgrade X# of packages, install X# of packages, remove X# of packages, etc, etc. Scary stuff.

---

### Post by zika on 2015-11-24
[http://www.youtube.com/watch?v=pQ2dI_B_Ycg](http://www.youtube.com/watch?v=pQ2dI_B_Ycg)

---

### Post by matt_symes on 2015-11-24
> **zika said:**
> [http://www.youtube.com/watch?v=pq2di_b_ycg](http://www.youtube.com/watch?v=pq2di_b_ycg)

lol

---

