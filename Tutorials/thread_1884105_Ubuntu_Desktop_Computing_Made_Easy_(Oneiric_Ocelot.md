---
title: "Ubuntu Desktop Computing Made Easy (Oneiric Ocelot v11.10)"
date: 2011-11-20
forum: Tutorials
---

### Post by TrakerJon on 2011-11-20
This is the Oneiric Ocelot post (Maverick Meerkat can be found at **[http://ubuntuforums.org/showthread.php?t=1883992](http://ubuntuforums.org/showthread.php?t=1883992)**). Enjoy and share...there will be a few updates to come.

This documentation is intended for folks that would like to add additional programs and applications to their Ubuntu Oneiric Ocelot installation for a better overall experience with very little effort. Please keep in mind older computers may have video performance issues due to high CPU usage and increased memory requirements. This post is oriented towards 32 bit systems (although most work on 64 bit systems a few of them may have to be forced to install). 

**Recommended:** Pentium 4 or higher processor with 1Gb of memory, 256Mb graphics card, 10/100 Ethernet card and 20Gb hard disk.

The easiest way to perform most of these installs is to copy and paste the commands from this post into a terminal window found in Applications > Accessories.

Many people still prefer the Gnome shell over the new Unity shell (I agree with them for the most part), so if you're one of those ol' Gnomes this post begins by catering to you.
**sudo apt-get install gnome-session-fallback**

You'll need the Gnome Tweak Tool for various setting changes found in Applications > Other > Advanced Settings after install.
**sudo apt-get install gnome-tweak-tool**

Log off select Gnome or Gnome Classic and then log back in.
**Note:** You now have to use Alt [right-click] to the change upper and lower panels in Gnome Classic. 

Go to Applications > System Tools > System Settings > Software Sources Check the appropriate boxes under the Ubuntu Software, Third-Party Software and Updates tabs > Close. Then Applications > Other > Update Manager and install Ubuntu updates at this point. Reboot after updating and install as many of the following as you wish.

If you're having slowness issues with the default repository go to Applications > System Tools > System Settings > Software Sources > Ubuntu Software tab > Download from: drop down menu > select Other > click Select Best Server and when it finishes the query click Choose Server > Close and Reload.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** or simply do the following from a terminal window:

[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]

If you're having problems with the main Medibuntu Repository manually enter a mirror site's URLs in System > Administration > Software Sources > Other Software. Click close and choose reload (you might get an error message). Then from a terminal prompt run run **sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring** followed by **sudo apt-get update**.

The "everything but the kitchen sink" approach still applies (as in my previous posts) when installing codecs to meet the demands of everyday usage. Unfortunately, when you try to single out or load them individually something breaks or doesn't work as expected. You can always back out players or applications you don't need by using a remove command (ex. **sudo apt-get remove gecko-mediaplayer gnome-mplayer tagtool easytag**) or by simply hiding them in the menus.

**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-gnonlin freepats gstreamer-dbus-media-service gstreamer-tools gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnomevfs gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-sdl libiptcdata0 w32codecs libdvdcss2 cpp-4.4 cvs debhelper debian-keyring dh-make diff-doc diffutils-doc g++-4.4 g++-4.4-multilib g++-4.6-multilib g++-multilib gcc-4.4 gcc-4.4-base gcc-4.4-doc gcc-4.4-multilib gcc-4.6-multilib gcc-multilib gettext gettext-doc html2text intltool-debian lib64gcc1 lib64gomp1 lib64mudflap0 lib64quadmath0 lib64stdc++6 libc6-amd64 libc6-dev-amd64 libfftw3-dev libgcc1-dbg libiodbc2 libmail-sendmail-perl libpq5 libqt3-mt libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql libstdc++6-4.4-dbg libstdc++6-4.4-dev libstdc++6-4.4-doc libsys-hostname-long-perl libunistring0 mplayer-doc nas po-debconf sidplay-base xsidplay cdrkit-doc comerr-dev easytag easytag-aac faac faad ffmpeg ffmpeg2theora flac fping gcc-4.4-locales gecko-mediaplayer gnome-mplayer gnutls-bin gnutls-doc guile-1.8 guile-1.8-doc guile-gnutls icedax id3tool id3v2 krb5-multidev ladspa-sdk lame lib64gcc1-dbg lib64stdc++6-4.4-dbg liba52-0.7.4-dev libao-common libao4 libavcodec-extra-53 libavdevice53 libavfilter-extra-2 libavformat-extra-53 libavifile-0.7c2 libavutil-extra-51 libc6-dbg libconfig++8 libcurl3-dbg libcurl4-gnutls-dev libdirac-decoder0 libdiscid0 libffado2 libflac++6 libgcrypt11-dev libgcrypt11-doc libggi-target-emu libggi-target-monotext libggi-target-terminfo libggi-target-x libggi2 libggimisc2 libgii1 libgii1-target-x libgnutls-dev libgnutlsxx26 libgomp1-dbg libgpg-error-dev libgssrpc4 libid3-3.8.3c2a libidn11-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkdb5-5 libkrb5-dev libldap2-dev liblzo2-2 libmudflap0 libmudflap0-4.4-dev libmudflap0-dbg libmusicbrainz3-6 liboggkate1 libopenjpeg2 libraptor1-doc libswscale-extra-2 libtagc0 libtasn1-3-dev libvo-aacenc0 libvo-amrwbenc0 libxml++2.6-2 libxss1 vorbis-tools zlib1g-dev gxine libaudio-scrobbler-perl libconfig-inifiles-perl liblrdf0 liblrdf0-dev libmpeg3-1 libmpg123-0 libraptor1 libraptor1-dev libsox-fmt-all libsox-fmt-alsa libsox-fmt-ao libsox-fmt-base libsox-fmt-ffmpeg libsox-fmt-mp3 libsox-fmt-oss libsox-fmt-pulse libsox1b libxine1 libxine1-bin libxine1-console libxine1-doc libxine1-ffmpeg libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 mplayer-skins raptor-utils sox tagtool twolame xine-ui**

Adobe Flash and Icedtea Java Plugins can now be found in the Ubuntu Software Center

Oracle/Sun Java Runtime Environment and Plugin (after removing Icedtea Java Plugin and OpenJDK Java Runtime from the Ubuntu Software Center):
**sudo add-apt-repository ppa:ferramroberto/java**
**sudo apt-get update**
**sudo apt-get install gsfonts-x11 java-common odbcinst odbcinst1debian2 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc**

**Note:** I've run into problems when installing the bundled codec packages ubuntu-restricted-extras and non-free-codecs, I don't recommend installing them. I realize this is a lot of stuff but rather than trying to advise or troubleshoot on a variety of issues this will cover most multimedia problems that can occur, especially when most people just want things to work without having to play seek and find.


Kaffeine - KDE Media Player
**sudo apt-get install kaffeine**

Amarok is a powerful music player for Linux with an intuitive interface.
**sudo apt-get install amarok**

Ardour, SoundKonverter, LMMS, Jokosher and AcidRip for multimedia recording, editing, conversions, mixing, etc.
**sudo apt-get install ardour soundkonverter jokosher lmms acidrip**

K9Copy, K3b and DeVeDe when you need DVD, CD, VCD and VCD writer software (requires libdvdcss2)
**sudo apt-get install k9copy k3b devede**

OpenShot - The Video Editor for Linux
**sudo apt-get install openshot**


**GetDeb** is another repository you definitely will want. Follow the "How to Install Apps from GetDeb" instructions before attempting to install the following eleven applications. **[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**

VLC (VideoLAN Client) is a portable multimedia player capable of reading most audio and video formats.
**[http://www.getdeb.net/software/VLC](http://www.getdeb.net/software/VLC)**
**sudo apt-get install vlc**

Audacious2 is the very innovative Audio Replacement for XMMS
**[http://www.getdeb.net/software/Audacious](http://www.getdeb.net/software/Audacious)**
**sudo apt-get install audacious**

Transmageddon supports almost any format as its input and can generate a very large host of output files.
**[http://www.getdeb.net/software/Transmageddon](http://www.getdeb.net/software/Transmageddon)**
**sudo apt-get install transmageddon**

Audacity is a cross-platform multitrack audio editor.
**[http://www.getdeb.net/software/Audacity](http://www.getdeb.net/software/Audacity)**
**sudo apt-get install audacity**

AceoneISO2 is a CD/DVD image manipulator for Linux (used primarily with .iso files).
**[http://www.getdeb.net/software/AcetoneISO](http://www.getdeb.net/software/AcetoneISO)**
**sudo apt-get install acetoneiso**

Azureus can be handy for things not found with Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Azureus](http://www.getdeb.net/software/Azureus)**
**sudo apt-get install azureus**

Shutter is a feature-rich screenshot program.
**[http://www.getdeb.net/software/Shutter](http://www.getdeb.net/software/Shutter)**
**sudo apt-get install shutter**

PDF MOD is a simple tool for modifying PDF documents.
**[http://www.getdeb.net/software/PDFMod](http://www.getdeb.net/software/PDFMod)**
**sudo apt-get install pdfmod**

KompoZer is a complete web authoring system.
**[http://www.getdeb.net/software/Kompozer](http://www.getdeb.net/software/Kompozer)**
**sudo apt-get install kompozer**


Gnutella is a lot like Limewire or Morpheus (see Firewalls and avast! sections below before using).
**sudo apt-get install gtk-gnutella**

Streamripper will allow you to download internet radio station broadcasts.
**sudo apt-get install streamripper**

**Streamtastic** is the java based gui for Streamripper.
Download the stable version from **[https://code.launchpad.net/streamtastic/+download](https://code.launchpad.net/streamtastic/+download)**

**Notes:** Install Streamripper and then create a folder in your home directory called Streamtastic. Create a sub folder of Streamtastic called downloads. Download Streamtastic and extract the files into the Streamtastic folder. Launch the Streamtastic.sh file from a command prompt (user@ubuntu-desktop:~/Streamtastic$ ./Streamtastic.sh) and when prompted point the download destination to your downloads folder. Select the station you would like to listen to and right-click on the reference to play and/or record. You can play and record at the same time, you'll be prompted to select a player (if you've installed amarok or vlc they're in /usr/bin). If you need to edit the configuration file to change the path to your player or download preferences, it can be found in a hidden .streamtastic folder in your home directory.
If you have folder permissions issues do the following:
**sudo chown -R username:username ~/Streamtastic (put in your "username")**
**sudo chmod -R 700 ~/Streamtastic**


Various compression/extraction and encoding/decoding utilities...
**sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils uudeview mpack lha arj cabextract file-roller libuu0**

**PeaZip** is a Cross-platform file and archive manager. Features include volume spanning, compression, authenticated encryption. Supports 7Z, 7-Zip sfx, ACE, ARJ, BZ2, CAB, CHM, CPIO, DEB, GZ, ISO, JAR, LHA/LZH, NSIS, OOo, PAQ/LPAQ, PEA, QUAD, RAR, RPM, split, TAR, Z, ZIP. I use the GTK2 version by downloading the .deb from: 

**[http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)**


Clam Antivirus (to be listed as Virus Scanner in Applications > Accessories) **[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)**

**sudo apt-get install clamav clamtk**

Operations available from a terminal session...

Update virus definitions: **sudo freshclam**

Scan files in your home directory: **sudo clamscan**

Scan files in an entire directory: **sudo clamscan -r /<directory name>**

Scan on the entire drive: **sudo clamscan -r /**


Bootup Manager is a nice utility to enable or disable running services.
**sudo apt-get install bum menu menu-l10n**


Email, VoIP and Text Chat

Thunderbird and SpamAssassin for email.
**sudo apt-get install thunderbird spamassassin**

**Note:** In Thunderbird go to Tools > Add-ons and add the Lightning extension if you would like a calendar along with your email.

Kopete is an instant messenger client supporting AIM, ICQ, Live Messenger, Yahoo, Jabber, and more.
**sudo apt-get install kopete**

XChat is an IRC chat program that allows for multiple IRC channels (chat rooms) at the same time.
**sudo apt-get install xchat**

Pidgin is an easy to use and free chat client to connect to AIM, MSN, Yahoo, and more chat networks all at once.
**sudo apt-get install pidgin**


Popular fonts for OpenOffice and other word processing applications.
**sudo apt-get install ttf-mscorefonts-installer mplayer-fonts ttf-xfree86-nonfree xfs cabextract ttf-liberation ttf-mscorefonts-installer**

Fonts, fonts and more fonts (pick and choose).
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts equivs ttf-sil-gentium gnome-specimen bsd-mailx dctrl-tools devscripts diffstat dput libapt-pkg-perl libauthen-sasl-perl libdevel-symdump-perl libio-pty-perl libio-stringy-perl libipc-run-perl libparse-debcontrol-perl libpod-coverage-perl libterm-size-perl libtest-pod-perl lintian patchutils postfix wdiff**

**Note:** Postfix is is associated with some of these fonts, be careful not to modify Postfix configurations if required for email purposes, otherwise select "no configuration" when prompted.

I typically don&#8217;t use Arabic and Asian fonts, to remove them from a terminal window type:
**sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei ttf-kacst-one ttf-khmeros-core**

**Note:** Add them by simply using install instead of remove.


HP printer driver issues? **[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)**


Adobe still makes one of the best .pdf viewers.
**sudo apt-get install acroread acroread-fonts**

PDFedit is editor for manipulating PDF documents.
**sudo apt-get install pdfedit**

**Note:** Print to PDF by installing cups-pdf from the Ubuntu Software Center.

AbiWord is a fast and easy to use word processing program.
**sudo apt-get install abiword**

gLabels is a program for creating labels and business cards for the GNOME desktop environment.
**sudo apt-get install glabels glabels-data**

iSpell comes in handy when spell checking documents from a terminal window
**sudo apt-get install ispell iamerican spell**

Wordnet is a comprehensive word database maintained by Princeton University
**sudo apt-get install wordnet tcl8.5 tk8.5 wordnet-base wordnet-gui**

The web interface for Wordnet is [http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)

FBReader is an e-book reader for various platforms.
**sudo apt-get install fbreader**

Dia is similar to Microsoft® Visio.
**sudo apt-get install dia**

GanttProject is a tool for creating a project schedule with Gantt and resource load charts.
**[http://ganttproject.biz/download](http://ganttproject.biz/download)**

Gnome Planner for Gant charts and project plans.
**sudo apt-get install planner**

OpenProj is a desktop replacement of Microsoft Project.
**[http://sourceforge.net/projects/openproj/files/](http://sourceforge.net/projects/openproj/files/)**

Scribus is a desktop publishing application.
**sudo apt-get install scribus**

Inkscape and Skencil for illustrations.
**sudo apt-get install inkscape**

Pinta is a lot like MS Paint
**sudo apt-get install pinta**

Gimp is an incredible image editing application.
**sudo apt-get install gimp gimp-data gimp-data-extras gimp-gap gimp-plugin-registry libbabl-0.0-0 libblas3gf libgegl-0.0-0 libgfortran3 libgimp2.0 libglew1.5 libgtkglext1 liblapack3gf liblqr-1-0 libtiff-tools gimp-help-en icc-profiles glew-utils libtiff-opengl freeglut3 gimp-help-common libglewmx1.5 gmic gimp-gmic libgraphicsmagick++3 libgraphicsmagick3**

Guvcview is a V4L2 video viewer and capture software for the linux UVC driver (think webcam).
**sudo apt-get install guvcview**

Comix is a customizable image viewer specifically designed to handle comic books (but also serves as a generic viewer).
**sudo apt-get install comix**

Byzanz records your desktop and saves to animated GIF files (great for tutorials) that are viewable in any web browser.
**sudo apt-get install byzanz**

**Note:** Byzanz is a panel applet and not listed in Applications, add it by right-clicking the panel and selecting Add to Panel > Desktop Recorder. Desktop effects have to be turned off to use Byzanz. More information is available by typing man byzanz-record from a terminal window.

Xara Xtreme is a user friendly vector graphics drawing program.
**sudo apt-get install xaralx xaralx-examples**

Blender is open source software for 3D modeling, animation, rendering, interactive creation and playback.
**sudo apt-get install blender**

webKam is simple webcam application **[http://code.google.com/p/webkam-kde4/downloads/list](http://code.google.com/p/webkam-kde4/downloads/list)**

Elltube is a YouTube downloader and converter **[http://sourceforge.net/projects/elltube/files/](http://sourceforge.net/projects/elltube/files/)**


Install screensavers (why they didn't include these I have no idea)
**sudo apt-get remove gnome-screensaver**
**sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra**
Now go to Applications > Other > Startup Applications and Add the following:
Name: **xscreensaver**
Command: **xscreensaver &#8211;nosplash**


If you program in C\C++ languages you&#8217;ll need Build-Essential packages.
**sudo apt-get install build-essential**

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages.
**sudo apt-get install geany**

Bluefish is an editor for experienced web designers and programmers supporting many programming and markup languages.
**sudo apt-get install bluefish**

Eclipse is an awesome open-source IDE for Java, C/C++, Python, etc... **[http://blog.sudobits.com/2011/10/02/how-to-install-eclipse-ide-on-ubuntu-11-10/](http://blog.sudobits.com/2011/10/02/how-to-install-eclipse-ide-on-ubuntu-11-10/)**

Vim, Gvim and Cream may come in handy for file editing (gedit works good too).
**sudo apt-get install vim-doc cscope vim-gnome vim-gui-common vim-runtime emacsen-common tclreadline cream**

Gedit (Text Editor in Accessories) is installed by default but the plugins are not...
**sudo apt-get install gedit-plugins**

**Note:** Enable Gedit plugins in Edit > Preferences > Plugins.
The Gedit wiki is at **[http://live.gnome.org/Gedit](http://live.gnome.org/Gedit)**

jEdit is a java based full featured editor (make sure you have Sun JRE installed).
**sudo apt-get install jedit**

Meld is a visual diff and merge tool.
**sudo apt-get install meld**

gFTP is a generic FTP client (port 21 is typical and consider file permissions when uploading).

**sudo apt-get install gftp gftp-common gftp-gtk gftp-text**

Filezilla is a full featured FTP client
**sudo apt-get install filezilla**


Remmina is a great remote desktop client for system administrators and travelers.
**sudo apt-get install remmina**


Convert .rpm files to .deb **[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)**
**sudo apt-get install alien**

Htop, SysInfo and HardInfo for referencing system information and benchmarking.
**sudo apt-get install htop sysinfo hardinfo**

The Synaptic Package Manager
**sudo apt-get install synaptic**

Fish (the applet, not the shell) is a fun animated panel applet that tells fortunes.
**sudo apt-get install fortune-mod fortunes-min librecode0**

**Note:** Add the panel applet by right-clicking the panel and selecting Add to Panel > Fish.

Stellarium is a free open source planetarium for your computer.
**sudo apt-get install stellarium**

**Note:** The users guide for Stellarium can be found at **[http://softlayer.dl.sourceforge.net/project/stellarium/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf](http://softlayer.dl.sourceforge.net/project/stellarium/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf)**

Glipper is a clipboard manager for the GNOME panel.
**sudo apt-get install glipper**

**Note:** If Clipboard manager does not appear in the panel applet menu, in a terminal window cd /usr/lib/glipper then run ./glipper It should allow you to add it as a panel applet at this point. The keyboard shortcut is <Ctrl><Alt>c

GNOME Commander is a "two-pane" graphical filemanager for the Gnome desktop environment.
**sudo apt-get install gnome-commander**

Add some useful features to Nautilus...
**sudo apt-get install libapr1 libaprutil1 libsvn1 nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-collection-svn nautilus-script-manager nautilus-scripts-manager nautilus-wallpaper subversion**

**Note:** Nautilus will display a two pane view by pressing F3 (thanks Paresh!).

NTFS Configuration Tool mounts NTFS drives (2000/XP/2003/Vista).
[B]sudo apt-get install ntfs-config
gksudo ntfs-config[/B]

**Note:** Found in System > Administration.

luckyBackup...a powerful, fast and reliable backup & sync tool **[http://luckybackup.sourceforge.net/download.html](http://luckybackup.sourceforge.net/download.html)**

Partimage system backup, instructions can be found at: **[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)**
**sudo apt-get install partimage**

KDE Partition Manager allows you to manage your disks, partitions and file systems:
**sudo apt-get install partitionmanager**

Note: Documentation can be found at **[http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html](http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html)**

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions.
**sudo apt-get install gparted dmraid jfsutils kpartx xfsprogs reiserfsprogs reiser4progs ntfsprogs libdmraid1.0.0.rc16 libparted0**

**Note:** Documentation can be found at **[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)**

Reconstructor will help you create your own Ubuntu based distribution **[http://www.reconstructor.org/wiki/reconstructor](http://www.reconstructor.org/wiki/reconstructor)**


Defrag (or fidefrag I should say)

[B]sudo apt-get install bzr python-psyco bzrtools python-paramiko
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>[/B]

**Note:** It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin


Google Earth install: **[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)**


Rainy days or a lot of time to kill? Frozen Bubble is a very addictive game.
**sudo apt-get install frozen-bubble fb-music-high frozen-bubble-data libmikmod2 libsdl-console libsdl-gfx1.2-4 libsdl-mixer1.2 libsdl-net1.2 libsdl-pango1 libsdl-perl libsdl-ttf2.0-0 libsmpeg0**

Kids in the house? Childsplay, GCompris and TuxPaint.
**sudo apt-get install childsplay childsplay-alphabet-sounds-bg childsplay-alphabet-sounds-en-gb python-numpy python-pygame python-sqlalchemy gcompris gcompris-sound-en tuxpaint tuxpaint-config gnucap gcompris-data libgnet2.0-0 libnetpbm10 netpbm tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default libfltk1.1 glchess libportmidi0 python-gtkglext1 python-opengl**


Firewalls

Internet security is important these days and firewalls can be quite complex, hopefully the following will help...use only one of these two applications and please read all of the documentation first. Most people are already behind a broadband router configured to give you "TruStealth" protection on the internet...check your current protection at the Sheilds Up! link below before being too concerned.

ufw ("uncomplicated firewall" included with Ubuntu), by default is set to "allow" all network traffic, the wiki instructions are at **[https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw)** then sudo ufw enable the firewall at system startup.

Personally I would rather use the gui interface for ufw...
**sudo apt-get install gufw**

Check your firewall protection at Sheilds Up! (click Proceed and use the All Service Ports option).
**[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)**

Wireshark is a full featured network protocol analyzer.
**sudo apt-get install wireshark**

Simple file encryption using GnuPG

From a terminal window in the directory where the file is stored:
**gpg -c <filename>** (encrypts, prompts twice for pass-phrase, creates <filename.gpg>)
**gpg <filename.gpg>** (decrypts, prompts for pass-phrase)

**Notes:** The source file can be deleted or moved after encryption. Sometimes when decrypting the pass-phrase prompt will pop-up behind the pinentry window. Type man gpg from a terminal window for more options. If you would like more advanced file encryption with keys and signatures visit **[http://www.gnupg.org/documentation/howtos.en.html](http://www.gnupg.org/documentation/howtos.en.html)** for more information.


The Oneiric wiki can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)**

The Natty wiki can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)**

The Maverick wiki can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)**

The Lucid wiki can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)**

The Karmic wiki can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)**

The UNR (Ubuntu Netbook Remix) wiki is here **[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)**

Ubuntu Manpage Repository **[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)**

The Ubuntu Pocket Guide can be found at **[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)**

Ubuntu Desktop Essentials **[http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials](http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials)**

ListOfOpenSourcePrograms **[https://help.ubuntu.com/community/ListOfOpenSourcePrograms](https://help.ubuntu.com/community/ListOfOpenSourcePrograms)**

Top 10 Gnome Shell Themes **[http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html](http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html)**

Best 100 Open Source Applications **[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)**

Best 50 Ubuntu Opensource Applications For Design And Developing **[http://blog.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html](http://blog.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html)**

GetDeb software site for Ubuntu and Debian **[http://www.getdeb.net/](http://www.getdeb.net/)**

Gnome Desktop software site **[http://www.gnomefiles.org/](http://www.gnomefiles.org/)**

Linux App Finder **[http://linuxappfinder.com/](http://linuxappfinder.com/)**

KDE-Apps.org **[http://www.kde-apps.org/](http://www.kde-apps.org/)**

Ubuntu PPA Search **[https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)**

Ubuntu Games **[https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)**

Cool wallpaper and more **[http://www.kde-look.org/](http://www.kde-look.org/)**

Gnome/KDE Keyboard Shortcuts **[http://www.novell.com/coolsolutions/tip/2289.html]("http://www.novell.com/coolsolutions/tip/2289.html")**


If Firefox windows open off screen or are too large to use, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox


Samba stuff
**sudo apt-get install cifs-utils keyutils ldb-tools libauthen-sasl-perl libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl libgssapi-perl libjcode-pm-perl libldb1 libnet-ldap-perl libpam-smbpass libsmbclient-dev libtevent0 libunicode-map-perl libunicode-map8-perl libunicode-maputf8-perl libunicode-string-perl libuser1 openbsd-inetd python-central python-libuser samba samba-dbg samba-doc samba-doc-pdf samba-tools smbfs smbldap-tools swat system-config-samba winbind libxml-sax-perl libfile-copy-recursive-perl update-inetd libxml-namespacesupport-perl libxml-sax-expat-perl**

Once Samba is installed you can setup a very basic shared folder as follows:

You&#8217;ll need to create Samba passwords with this command:

**sudo smbpasswd -a USERNAME**

Make a backup copy of the original smb.conf file, in case you make an error:

**sudo cp /etc/samba/smb.conf ~**

Add a share to the very end of the file:

**sudo gedit /etc/samba/smb.conf**

[mystuff]
path = /home/USERNAME/mystuff
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes

(There should be no spaces between the lines, and note also that there should be a single space both before and after each of the equal signs.)

Save the file and restart samba with these commands:

**sudo restart smbd**
**sudo restart nmbd**

Use this command from a terminal window to check that your smb.conf doesn&#8217;t contain any syntax errors: testparm

Don't forget to create your shared folder and modify the permissions as needed. You may also have to allow specific IP address TCP/UDP access through your firewall as well. Keep in mind if security is an issue to read up a lot more on the topic.


The Ubuntu Samba Wiki **[https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")**


How to setup remote access **[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)**


Alternative shells for Linux...

C, K, T, Z & Fish shells
**sudo apt-get install csh ksh tcsh zsh fish xsel zsh-doc**

Bash Reference Manual **[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)**

chmod calculator **[http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)**


Adding a Personal Package Archive (PPA) to your Ubuntu repositories

Note: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

**Open your terminal and enter the following**:

**sudo add-apt-repository ppa:<ppa name>**
**sudo apt-get update**

You're now ready to install software from the PPA using **sudo apt-get upgrade** in the terminal.

Some popular PPA's are...

**sudo add-apt-repository ppa:shutter/ppa**

**sudo add-apt-repository ppa:jonoomph/openshot-edge**


Collection of useful commands...
---------------------------------------------------------------
Searching for Packages: **apt-cache search some_string**
Show Package Info: **apt-cache showpkg xxx**
Show Package Dependencies: **apt-cache depends xxx**
Install: **apt-get install xxx**
Re-Install: **apt-get --reinstall install xxx**
Remove: apt-get remove xxx
Remove All (configs too): **apt-get remove --purge xxx**
Upgrade: **apt-get -u upgrade**
Show Upgrades: **apt-show-versions -u**
Show All Installed Packages: **dpkg --list**
Find Package by File Name: **apt-file search /bin/ping**
Find filenames in a Package: **apt-file list xxx**
Updating the apt-file Cache: **apt-file update**
Info on Installed Package: **aptitude show xxx**
System Hardware Info: **sudo lshw > hardware.txt**

Linux Command Directory **[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)**

Linux Commands - A practical reference **[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)**

Clean up your system and free up space with **sudo apt-get clean** and **sudo apt-get autoremove**

If you're curious (like me) or have the need to know **uname -a && cat /etc/*release** in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.


Ok, about wine...in most cases a free to use Linux program will work just as well as apps on that other well known operating system. I don't recommend it but for the folks that like wine this wiki should help **[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)**

Wine Application Database (AppDB) **[http://appdb.winehq.org/](http://appdb.winehq.org/)**


To my friends...

I'm more than willing to include your favorite applications, this is your post as much as mine. I do ask that you keep the description brief and on a general level, with the degree of difficulty at a minimum (for new users) when making recommendations. I started posting "Ubuntu Desktop Computing Made Easy" a while back, mainly out of frustration I had getting my computer to perform as expected without hours of setup, search and configuration. The primary goal of this post is to make it "easy" for anyone to setup an Ubuntu Desktop Computer with everything they need or want in a short period of time, ensuring the overall experience is an enjoyable one.

**Note:** This post can be found very quickly by doing a Google search on Ubuntu Desktop Computing Made Easy. If you would like to link to this post or publish it elsewhere I do request that you obtain permission and give credit where credit is due.

Regards,

-TrakerJon

Dell GX270 3.2GHz Pentium 4 w/ 2Gb SDRAM using NVIDIA GeForce 6200 AGP w/ 256Mb video.

[COLOR="White"]Enable Personal File Sharing - gnome-user-share is a session service that exports the contents of a Public folder in your home directory, so they can be accessed from other computers on the network. Refer to the Personal File Sharing Manual from Help within the application for additional information.
**sudo apt-get install apache2.2-bin libapache2-mod-dnssd libaprutil1-dbd-sqlite3 libaprutil1-ldap**[/COLOR]

[COLOR="White"]Additional Gnome Shell Extensions (warning these are unstable)
**sudo apt-get install gnome-shell-extensions-workspace-indicator gnome-shell-extensions-alternative-status-menu gnome-shell-extensions-apps-menu**[/COLOR]

---

