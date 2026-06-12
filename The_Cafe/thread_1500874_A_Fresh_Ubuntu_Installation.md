---
title: "A Fresh Ubuntu Installation"
date: 2010-06-03
forum: The Cafe
---

### Post by tufcamman on 2010-06-03
Hey everyone, just for fun, I'd like to know what some of you do every time you install a fresh copy of Ubuntu Desktop.  I've developed a few steps that have become the first things I do every time after I log in for the first time.

1) install medibuntu and ubuntu-restricted-extras
2) resize all fonts to 8pt and set background image
3) install vim-gtk, build-essential
4) setup my .vimrc and install vim addons (w00t!!! NERDTree)
4) change ~/.config/user-dirs.dirs to all lowercase letters, and then change the folder names under my home directory (I hate capital letters :p)
5) task-sel install lamp-server and mail-server, change apache2 to run as my user, and create my ~/public_html folder and make it default
And now, I install gimp, since 10.04 at least.

At this point, I'm ready to go.  So anyway, does anybody else have a routine to personalize their ubuntu?

---

### Post by shaka_zulu on 2010-06-03
Check all updates in Synaptic. 
Install and set up compiz. 
Install Inkscape, Blender and Chrome.

---

### Post by howefield on 2010-06-03
This isn't really a support thread...

There are a few other bits and pieces such as configuring all applications and such like, but my routine is something like this

> 1. Install Lucid.
2. sudo apt-get update and install updates.
3. Install nvidia/proprietary drivers. (also dvb tuner driver)
   a) sudo rm /etc/X11/xorg.conf
   b) gksu nvidia-settings
   c) /etc/X11/xorg.conf
4. Change the scrollbar width - gedit ~/.gtkrc-2.0
5. Create PDF folder in home directory.
6. Change appearance / wallpaper / fonts ect.
7. echo "deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) `lsb_release -cs` main" | sudo tee -a /etc/apt/sources.list && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CD30EE56
8. Add partner repository to sources.list.
9. sudo apt-get install gimp kdenlive k3b k9copy winff lame oggconvert audacity flac wine gftp xchat compizconfig-settings-manager kaffeine xtightvncviewer gparted devede cups-pdf synergy samba miro ripperx gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg libxine1-plugins libxine1-all-plugins unrar rar p7zip p7zip-full p7zip-rar sun-java6-jre sun-java6-plugin sopcast-player kompozer filezilla skype
10. Configure volume level.
11. Put archive manager icon & configuration editor icon on menu.
12. Remove confirmation from Shutdown button & ensure buttons/menus have icons.
13. Configure evolution. 
14. Remove startup options, bluetooth, print queue, and evolution alarm ect.
15. Set up printer for network and default settings.
16. Debs: chrome, dropbox, frostwire, libdvdcss2, opera, teamviewer, w64codecs.
17. Configure firefox options / add bookmarks / flash / noscript.
18. Clear recent documents & sudo apt-get clean.
19. Image with Clonezilla.
20. Reboot and enjoy :-)

---

### Post by SunnyRabbiera on 2010-06-03
For most users I suggest
Step 1: Install Ubuntu Tweak (as it helps with medibuntu)
Step 2: Install ubuntu restricted extras
Step 3: Install libdvdcss, VLC, gecko-mediaplayer, smplayer
Step 4: Enable getdeb when its back up
Step 5: sit back, and enjoy

---

### Post by NightwishFan on 2010-06-03
On Ubuntu I generally install Exaile and gstreamer fluendo mp3 plugins. As of 10.04, I used Rhythmbox instead, since I do not like the new Exaile. Other applications I use are gufw for firewall, and boot up manager for disabling unneeded services.

---

### Post by lovinglinux on 2010-06-03
1 - make a backup of my personal settings folders (just to be safe)
2 - make a backup of some system configuration files needed for tvtime and lirc
3 - make a backup of installed applications and third party repositories with [Umarks](http://umarks-extension.blogspot.com/)
4 - reboot and install a command-line only system
5 - boot into the new system, install xorg, kdm, kde-minimal, kdeplasma-addons and firefox
6 - install restricted drivers
7 - reboot and log into KDE, launch Firefox and install previous applications and repositories with [Umarks](http://umarks-extension.blogspot.com/)
8 - restore tvtime and lirc config files
9 - configure anything that looks different, but usually there is no need, since I use a separate home partition
10 - Go to Ubuntu forums to read all the complaints from people who upgraded instead of doing a clean install

---

### Post by mikewhatever on 2010-06-03
I remove a couple of things I don't use - compiz, evolution, tomboy, etc.

---

### Post by Hman242 on 2010-06-03
I remove all programs I don't use, install restricted extras, install flash, install Java, install all of the programs I use which I've put on a list, installed restricted drivers, and then I reboot. After rebooting I'll install the Shiki them and rearrange my panels and such to my liking.

---

