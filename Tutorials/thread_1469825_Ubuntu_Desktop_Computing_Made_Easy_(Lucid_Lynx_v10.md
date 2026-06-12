---
title: "Ubuntu Desktop Computing Made Easy (Lucid Lynx v10.04)"
date: 2010-05-02
forum: Tutorials
---

### Post by TrakerJon on 2010-05-02
This is the Lucid Lynx post (Karmic Koala can be found at  [http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)). Enjoy and share!

This documentation is intended for folks that would like to add additional programs and applications to their Ubuntu Lucid Lynx installation (the best release yet) for a better overall experience with very little effort. Please keep in mind older computers may have video performance issues due to high CPU usage and increased memory requirements. This post is oriented towards 32 bit systems (although I have included some 64 bit references). There are other posts that are specific to 64 bit systems, especially if you're having difficulties with codecs.

Recommended: Pentium 4 or higher processor with 1Gb SDRAM, 256Mb graphics card, 10/100 Ethernet card and 20Gb hard disk.

The easiest way to perform most of these installs is to copy and paste from this post into a terminal window (found in Applications > Accessories).

**Start by going to System > select Administration > select Software Sources > Check the appropriate boxes under the Ubuntu Software, Third-Party Software and Updates tabs > Close and Reload**

Install all available Ubuntu updates at this point (there may be an update notification icon on the task bar). Reboot after updating your system and then install as many of the following as you wish.

If you're having slowness issues with the default repository go to System > select Administration > select Software Sources > Ubuntu Software tab > Download from: drop down menu > select Other > click Select Best Server and  when it finishes the query click Choose Server > Close and Reload.

**Many of these installations require access to the Medibuntu Repository and enabling some additional software sources.** Directions are on this site: **[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)** or  simply do the following from a terminal window:

[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]

If you're having problems with the main Medibuntu Repository manually enter a mirror site's URLs in System > Administration > Software Sources > Other Software. Click close and choose reload (you might get an error message). Then from a terminal prompt run run **sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring** followed by **sudo apt-get update**.

Mirror 1:

deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free

Mirror 2:

deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free
deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) lucid free non-free

Mirror 3:

deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free
deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) lucid free non-free

**Codecs, plug-ins and accessories...** are needed for playing various multimedia formats (see above before attempting to install).

**sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libavcodec52 libavformat52 libavutil49 libcdaudio1 libdc1394-22 libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 sox tagtool twolame vorbis-tools build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf zlib1g-dev libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libsdl-image1.2 jack-tools jackd libjackasyn0 qjackctl libjack0 libdirac-encoder0 libdirac-decoder0 cpp-4.3 diffutils-doc gecko-mediaplayer krb5-multidev libffado2 libkadm5clnt-mit7 libkadm5srv-mit7 raptor-utils jackd-firewire**

**Note:** I've run into a variety of issues when installing the bundled codec packages ubuntu-restricted-extras and non-free-codecs, I don't recommend them. I've included MPlayer, Gnome Mediaplayer, Gecko Mediaplayer, Jackd, EasyTAG and Audio Tag Tool accessories for convenience. The C and C++ libraries are to resolve some dependencies you may encounter. 

Adobe Flash
**sudo apt-get install flashplugin-nonfree flashplugin-installer**

The latest Sun Java JRE
**sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc odbcinst**

Kaffeine - KDE Media Player
**sudo apt-get install kaffeine**

Amarok is a powerful music player for Linux with an intuitive interface.
**sudo apt-get install amarok**

Ardour, SoundKonverter, LMMS, Jokosher and AcidRip for multimedia recording, editing, conversions, mixing, etc.
**sudo apt-get install ardour soundkonverter jokosher lmms acidrip**

K9Copy, K3b and DeVeDe when you need DVD, CD, VCD and VCD writer software (requires libdvdcss2)
**sudo apt-get install k9copy k3b devede**

OpenShot - The Video Editor for Linux
**sudo apt-get install openshot frei0r-plugins**


**GetDeb** is another repository you definitely will want. Follow the **"How to Install Apps from GetDeb"** instructions before attempting to install the following eleven applications. **[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)**

If you're having problems with the primary repository this is the mirror site information for System > Administration > Software Sources
**deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps**
**deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps**

If you get a public key error, run this command from a terminal session and then retry.
**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 46D7E7CF**

**VLC** (VideoLAN Client) is a portable multimedia player capable of reading most audio and video formats.
**[http://www.getdeb.net/software/VLC](http://www.getdeb.net/software/VLC)**
**sudo apt-get install vlc**

**Audacious2** is the very innovative Audio Replacement for XMMS
**[http://www.getdeb.net/software/Audacious](http://www.getdeb.net/software/Audacious)**
**sudo apt-get install audacious**

**Songbird** is a desktop Web player, digital jukebox and Web browser mash-up.
**[http://www.getdeb.net/software/Songbird](http://www.getdeb.net/software/Songbird)**
**sudo apt-get install songbird**

**Transmageddon** supports almost any format as its input and can generate a very large host of output files.
**[http://www.getdeb.net/software/Transmageddon](http://www.getdeb.net/software/Transmageddon)**
**sudo apt-get install transmageddon**

**Audacity** is a cross-platform multitrack audio editor.
**[http://www.getdeb.net/software/Audacity](http://www.getdeb.net/software/Audacity)**
**sudo apt-get install audacity**

**AceoneISO2** is a CD/DVD image manipulator for Linux (used primarily with .iso files).
**[http://www.getdeb.net/software/AcetoneISO](http://www.getdeb.net/software/AcetoneISO)**
**sudo apt-get install acetoneiso**

**Azureus** can be handy for things not found with Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Azureus](http://www.getdeb.net/software/Azureus)**
**sudo apt-get install azureus**

**Frostwire** is similar to Gnutella (see Firewalls and avast! sections below before using).
**[http://www.getdeb.net/software/Frostwire](http://www.getdeb.net/software/Frostwire)**
**sudo apt-get install frostwire**

**Shutter** is a feature-rich screenshot program.
**[http://www.getdeb.net/software/Shutter](http://www.getdeb.net/software/Shutter)**
**sudo apt-get install shutter**

**PDF MOD** is a simple tool for modifying PDF documents. 
**[http://www.getdeb.net/software/PDFMod](http://www.getdeb.net/software/PDFMod)**
**sudo apt-get install pdfmod**

**KompoZer** is a complete web authoring system. 
**[http://www.getdeb.net/software/Kompozer](http://www.getdeb.net/software/Kompozer)**
**sudo apt-get install kompozer**


Gnutella is a lot like Limewire or Morpheus (see Firewalls and avast! sections below before using).
**sudo apt-get install gtk-gnutella**

Streamripper will allow you to download internet radio station broadcasts.
**sudo apt-get install streamripper**

**Streamtastic** is the java based gui for Streamripper.
Download the stable version from **[https://code.launchpad.net/streamtastic/+download]("https://code.launchpad.net/streamtastic/+download")**

**Notes:** Install Streamripper and then create a folder in your home directory called Streamtastic. Create a sub folder of Streamtastic called downloads. Download Streamtastic and extract the files into the Streamtastic folder. Launch the Streamtastic.sh file from a command prompt (user@ubuntu-desktop:~/Streamtastic$ ./Streamtastic.sh) and when prompted point the download destination to your downloads folder. Select the station you would like to listen to and right-click on the reference to play and/or record. You can play and record at the same time, you'll be prompted to select a player (if you've installed amarok or vlc they're in /usr/bin). If you need to edit the configuration file to change the path to your player or download preferences, it can be found in a hidden .streamtastic folder in your home directory.
If you have folder permissions issues do the following:
**sudo chown -R username:username ~/Streamtastic** (put in *your* "username")
**sudo chmod -R 700 ~/Streamtastic**

**Shoutcast** is a good place to shop for internet radio stations. **[http://www.shoutcast.com/](http://www.shoutcast.com/)**


**Compiz, Emerald and Screenlets**

The default Ubuntu display setup lets you choose from None, Normal or Extra. Make it more configurable with the CompizConfig Settings Manager...found in System > Preferences after installing the following:

**sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-fusion-plugins-extra libcompizconfig0 compizconfig-settings-manager python-compizconfig fusion-icon mesa-utils screenlets libtidy-0.99-0 python-chardet python-evolution python-feedparser python-gtkmozembed python-rsvg python-utidylib xfconf libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 emerald libemeraldengine0 gnome-art gnome-splashscreen-manager libart2-ruby1.8 libatk1-ruby1.8 libcairo-ruby1.8 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgnome2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8 ruby ruby1.8 startupmanager gnome-splashscreen-manager libatk1-ruby1.8 libcairo-ruby1.8 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8 libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8 ruby ruby1.8**

**Notes:** Make sure you enable Visual Effects "**Extra**" (right click on your desktop, choose change Desktop Background and click on the Visual Effects tab) before adusting Compiz settings. Reset Compiz defaults by going into CCSM > Preferences > Profile & Backend > Click Reset to defaults.


Various compression/extraction and encoding/decoding utilities...
**sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils uudeview mpack lha arj cabextract file-roller libuu0**

**PeaZip** is a Cross-platform file and archive manager. Features include volume spanning, compression, authenticated encryption. Supports 7Z, 7-Zip sfx, ACE, ARJ, BZ2, CAB, CHM, CPIO, DEB, GZ, ISO, JAR, LHA/LZH, NSIS, OOo, PAQ/LPAQ, PEA, QUAD, RAR, RPM, split, TAR, Z, ZIP. 

**[http://sourceforge.net/search/?type_of_search=soft&words=peazip](http://sourceforge.net/search/?type_of_search=soft&words=peazip)**

Note: You'll have to create a menu item for PeaZip, in Applications > Accessories by right-clicking Applications, choosing Edit Menus, selecting Accessories, click New Item and enter in the Name: PeaZip Command: peazip and Comment: File Compression and Extraction Utility. Click the Launcher icon and you'll see peazip.png, highlight and click the Open button then close.


**Clam Antivirus** (to be listed as Virus Scanner in Applications > Accessories) **[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)**

**sudo apt-get install clamav clamtk**

Operations available from a terminal session...

Update virus definitions: **sudo freshclam**

Scan files in your home directory: **sudo clamscan** 

Scan files in an entire directory: **sudo clamscan -r /<directory name>** 

Scan on the entire drive: **sudo clamscan -r /** 


**Email, VoIP and Text Chat**

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
**sudo apt-get install ttf-larabie-straight ttf-larabie-deco xfonts-terminus-dos xfonts-terminus xfonts-terminus-oblique xfonts-mona tv-fonts ttf-tuffy ttf-sjfonts ttf-georgewilliams ttf-fifthhorseman-dkg-handwriting ttf-essays1743 ttf-opensymbol ttf-mgopen ttf-freefont ttf-dustin ttf-dejavu-extra ttf-dejavu-core ttf-dejavu ttf-bpg-georgian-fonts equivs ttf-sil-gentium gnome-specimen bsd-mailx dctrl-tools devscripts diffstat dput libapt-pkg-perl libauthen-sasl-perl libdevel-symdump-perl libio-pty-perl libio-stringy-perl libipc-run-perl libparse-debcontrol-perl libpod-coverage-perl libterm-size-perl libtest-pod-perl lintian patchutils postfix wdiff**

**Note:** Postfix is is associated with some of these fonts, be careful not to modify Postfix configurations if required for email purposes, otherwise select "no configuration" when prompted.

I typically don&#8217;t use Arabic and Asian fonts, to remove them from a terminal window type:
**sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei**

**Note:** Add them by simply using install instead of remove.

**HP printer driver issues? [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)**

Adobe still makes one of the best .pdf viewers.
**sudo apt-get install acroread acroread-fonts**

PDFedit is editor for manipulating PDF documents.
**sudo apt-get install pdfedit**

Printing to PDF is a little tricky, first install the PDF print driver.
**sudo apt-get install cups-pdf**
Then create the default "PDF" save to folder in your home directory (ex. \home\<user name>\PDF)
Lastly, change the permissions on the following folder and file...
**sudo chmod 755 /usr/lib/cups/backend**
**sudo chmod 700 /usr/lib/cups/backend/cups-pdf**

AbiWord is a fast and easy to use word processing program.
**sudo apt-get install abiword**

gLabels is a program for creating labels and business cards for the GNOME desktop environment.
**sudo apt-get install glabels glabels-data**

iSpell comes in handy when spell checking documents from a terminal window
**sudo apt-get install ispell iamerican spell**

Wordnet is a comprehensive word database maintained by Princeton University
**sudo apt-get install wordnet tcl8.5 tk8.5 wordnet-base wordnet-gui**

The web interface for Wordnet is **[http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)**

FBReader is an e-book reader for various platforms.
**sudo apt-get install fbreader**

Dia is similar to Microsoft® Visio.
**sudo apt-get install dia**

GanttProject is a tool for creating a project schedule with Gantt and resource load charts.
**[http://ganttproject.biz/download.php](http://ganttproject.biz/download.php)**

Gnome Planner for Gant charts and project plans.
**sudo apt-get install planner**

**OpenProj** is a desktop replacement of Microsoft Project.
**[http://sourceforge.net/projects/openproj/files/]("http://sourceforge.net/projects/openproj/files/")**

Scribus is a desktop publishing application.
**sudo apt-get install scribus**

Inkscape and Skencil for illustrations.
**sudo apt-get install inkscape**

Gimp is an incredible image editing application.
**sudo apt-get install gimp gimp-data gimp-data-extras gimp-gap gimp-plugin-registry libbabl-0.0-0 libblas3gf libgegl-0.0-0 libgfortran3 libgimp2.0 libglew1.5 libgtkglext1 liblapack3gf liblqr-1-0 libtiff-tools gimp-help-en icc-profiles glew-utils libtiff-opengl freeglut3 gimp-help-common libglewmx1.5**

Byzanz records your desktop and saves to animated GIF files (great for tutorials) that are viewable in any web browser.
**sudo apt-get install byzanz**

**Note:** Byzanz is a panel applet and not listed in Applications, add it by right-clicking the panel and selecting Add to Panel > Desktop Recorder. Desktop effects have to be turned off to use Byzanz. More information is available by typing man byzanz-record from a terminal window.

Xara Xtreme is a user friendly vector graphics drawing program.
**sudo apt-get install xaralx xaralx-examples**

Blender is open source software for 3D modeling, animation, rendering, interactive creation and playback.
**sudo apt-get install blender**

**webKam** is simple webcam application **[http://code.google.com/p/webkam-kde4/downloads/list](http://code.google.com/p/webkam-kde4/downloads/list)**

**Elltube** is a YouTube downloader and converter **[http://elltube.sourceforge.net/download](http://elltube.sourceforge.net/download)**

If you program in C\C++ languages you&#8217;ll need Build-Essential packages.
**sudo apt-get install build-essential **

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages.
**sudo apt-get install geany**

Bluefish is an editor for experienced web designers and programmers supporting many programming and markup languages.
**sudo apt-get install bluefish**

Eclipse is an awesome open-source IDE for Java, C/C++ and Python.
**[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/")**

**Note:** Eclipse is available from the repositories but limits you to java development by default, I recommend the manual install referenced above. If you are "fortunate" enough to develop apps in C/C++ this link should help as well... **[http://www.eclipse.org/cdt/downloads.php](http://www.eclipse.org/cdt/downloads.php)**

Vim, Gvim and Cream may come in handy for file editing (gedit works good too).
**sudo apt-get install vim-doc cscope vim-gnome vim-gui-common vim-runtime emacsen-common tclreadline cbrowser cream**
 
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

Convert .rpm files to .deb **[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)**
**sudo apt-get install alien**

Htop, SysInfo and HardInfo for referencing system information and benchmarking.
**sudo apt-get install htop sysinfo hardinfo**

Fish (the applet, not the shell) is a fun animated panel applet that tells fortunes.
**sudo apt-get install fortune-mod fortunes-min librecode0**

**Note:** Add the panel applet by right-clicking the panel and selecting Add to Panel > Fish.

Stellarium is a free open source planetarium for your computer.
**sudo apt-get install stellarium**

**Note:** The users guide for Stellarium can be found at **[http://softlayer.dl.sourceforge.net/project/stellarium/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf]("http://softlayer.dl.sourceforge.net/project/stellarium/Stellarium-user-guide/0.10.2-1/stellarium_user_guide-0.10.2-1.pdf")**

Glipper is a clipboard manager for the GNOME panel.
**sudo apt-get install glipper**

**Note:** If Clipboard manager does not appear in the panel applet menu, in a terminal window cd /usr/lib/glipper then run ./glipper It should allow you to add it as a panel applet at this point. The keyboard shortcut is <Ctrl><Alt>c

**GNOME Commander** is a "two-pane" graphical filemanager for the Gnome desktop environment.
**sudo apt-get install gnome-commander**

Add some useful features to Nautilus...
**sudo apt-get install libapr1 libaprutil1 libsvn1 nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-collection-svn nautilus-script-manager nautilus-scripts-manager nautilus-wallpaper subversion**

**Note:** Nautilus will display a two pane view by pressing F3 (thanks Paresh!).

NTFS Configuration Tool mounts NTFS drives (2000/XP/2003/Vista).
**sudo apt-get install ntfs-config**
**gksudo ntfs-config**

**Note:** Found in System > Administration.

**luckyBackup**...a powerful, fast and reliable backup & sync tool **[http://luckybackup.sourceforge.net/download.html](http://luckybackup.sourceforge.net/download.html)**

Partimage system backup, instructions can be found at: **[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)**
**sudo apt-get install partimage**

KDE Partition Manager allows you to manage your disks, partitions and file systems:
**sudo apt-get install partitionmanager**

**Note:** Documentation can be found at **[http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html](http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/index.html)**

GParted is the GNOME partition editor for creating, reorganizing and deleting disk partitions.
**sudo apt-get install gparted dmraid jfsutils kpartx xfsprogs reiserfsprogs reiser4progs ntfsprogs libdmraid1.0.0.rc16 libparted0**

**Note:** Documentation can be found at **[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)**

**Reconstructor** will help you create your own Ubuntu based distribution **[http://www.reconstructor.org/wiki/reconstructor](http://www.reconstructor.org/wiki/reconstructor)**


**Defrag** (or fidefrag I should say)

**sudo apt-get install bzr python-psyco bzrtools python-paramiko**
**bzr branch lp:fidefrag**
**cd fidefrag/src**
**sudo python fidefrag.py -d /<directory name>**

**Note:** It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin


**Google Earth** install: **[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)**


Rainy days or a lot of time to kill? Frozen Bubble is a very addictive game.
**sudo apt-get install frozen-bubble fb-music-high frozen-bubble-data libmikmod2 libsdl-console libsdl-gfx1.2-4 libsdl-mixer1.2 libsdl-net1.2 libsdl-pango1 libsdl-perl libsdl-ttf2.0-0 libsmpeg0**

Kids in the house? Childsplay, GCompris and TuxPaint.
**sudo apt-get install childsplay childsplay-alphabet-sounds-bg childsplay-alphabet-sounds-en-gb python-numpy python-pygame python-sqlalchemy gcompris gcompris-sound-en tuxpaint tuxpaint-config gnucap gcompris-data libgnet2.0-0 libnetpbm10 netpbm tuxpaint-data tuxpaint-plugins-default tuxpaint-stamps-default libfltk1.1 glchess libportmidi0 python-gtkglext1 python-opengl**


**Firewalls**

Internet security is important these days and firewalls can be quite complex, hopefully the following will help...use only one of these two applications and please read all of the documentation first. Most people are already behind a broadband router configured to give you "TruStealth" protection on the internet...check your current protection at the Sheilds Up! link below before being too concerned.

**ufw** ("uncomplicated firewall" included with Ubuntu), by default is set to "allow" all network traffic, the wiki instructions are at **[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)** then **sudo ufw enable** the firewall at system startup.

Personally I would rather use the gui interface for ufw...
**sudo apt-get install gufw**
 
**Firestarter** is quite easy to configure **[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)**
**sudo apt-get install firestarter menu**

Check your firewall protection at Sheilds Up! (click Proceed and use the All Service Ports option).
[**https://www.grc.com/x/ne.dll?bh0bkyd2**]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Wireshark is a full featured network protocol analyzer.
**sudo apt-get install wireshark**


**Simple file encryption using GnuPG**

From a terminal window in the directory where the file is stored:
gpg -c <filename> (encrypts, prompts twice for pass-phrase, creates <filename.gpg>)
gpg <filename.gpg> (decrypts, prompts for pass-phrase)

**Notes:** The source file can be deleted or moved after encryption. Sometimes when decrypting the pass-phrase prompt will pop-up behind the pinentry window. Type **man gpg** from a terminal window for more options. If you would like more advanced file encryption with keys and signatures visit **[http://www.gnupg.org/documentation/howtos.en.html](http://www.gnupg.org/documentation/howtos.en.html)** for more information.

Advanced file encryption with GNU Privacy Assistant (use with caution and knowledge)
**sudo apt-get install gpa**


**The Lucid wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)**

**The Karmic wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)**

**The Jaunty wiki** can be found here **[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)**

**The UNR (Ubuntu Netbook Remix) wiki is here [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)**

**Ubuntu Manpage Repository [http://manpages.ubuntu.com/]("http://manpages.ubuntu.com/")** 

**The Ubuntu Pocket Guide** can be found at **[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)**

**Ubuntu Desktop Essentials [http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials](http://www.techotopia.com/index.php/Ubuntu_Desktop_Essentials)**

**ListOfOpenSourcePrograms [https://help.ubuntu.com/community/ListOfOpenSourcePrograms](https://help.ubuntu.com/community/ListOfOpenSourcePrograms)**

**Best 100** Open Source Applications **[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)**

**Best 50** Ubuntu Opensource Applications For Design And Developing **[http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html](http://www.emmaalvarez.com/2007/12/top-best-50-ubuntu-opensource.html)**

**GetDeb** software site for Ubuntu and Debian [**http://www.getdeb.net/**]("http://www.getdeb.net/")

**Gnome Desktop software** site [**http://www.gnomefiles.org/**]("http://www.gnomefiles.org/")

**Linux App Finder [http://linuxappfinder.com/](http://linuxappfinder.com/)**

**KDE-Apps.org [http://www.kde-apps.org/](http://www.kde-apps.org/)**

**Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)**

**Ubuntu Games [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)**

**Cool wallpaper and more [http://www.kde-look.org/](http://www.kde-look.org/)**


**Maximus Issues** (windows always maximize when an application is launched)
If you have a Netbook and auto maximize windows is driving you crazy try this from a terminal window: type gconf-editor then go to Apps > Maximus > check no_maximize


If **Firefox windows open off screen or are too large to use**, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox


**Get your Trash Can and other desktop icons back**...

The default for new installed Ubuntu is clean desktop. So, for example, if you want to get your Trash Icon back you need to change the default setting.

**Step 1**. Run Desktop Configuration Editor

Open Application > Accessories > Terminal and type gconf-editor.

**Step 2**. Change the value for trash_icon_visible

After the Desktop configuration Editor is displayed, open apps > nautilus > desktop and click the value for trash_icon_visible. This also works for your computer, home and network icons.


**Setup Samba peer-to-peer with Windows [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)**

Install Samba stuff
**sudo apt-get install samba samba-common samba-tools smbclient swat samba-doc samba-doc-pdf smbfs libpam-smbpass libsmbclient libsmbclient-dev winbind samba-dbg libwbclient0 smbldap-tools ldb-tools keyutils libuser1 python-libuser system-config-samba libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl libjcode-pm-perl libldb0 libnet-ldap-perl libtevent0 libunicode-map-perl libunicode-map8-perl libunicode-maputf8-perl libunicode-string-perl libdigest-sha1-perl openbsd-inetd**

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

Save the file and restart samba with  this command:

**sudo service samba restart**

Use this command from a terminal window to check that your smb.conf doesn&#8217;t contain any syntax errors: **testparm**

Don't forget to create your shared folder and modify the permissions as needed. You may also have to allow specific IP address TCP/UDP access through your firewall as well. Keep in mind if security is an issue to read up a lot more on the topic.


**How to setup remote access [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)**


**Alternative shells for Linux**...

C, K, T, Z & Fish shells
**sudo apt-get install csh ksh tcsh zsh fish xsel zsh-doc**

**Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)**

**chmod calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)**


**Adding a Personal Package Archive (PPA) to your Ubuntu repositories**

Adding a PPA to Ubuntu takes no more than a couple of minutes.

**Step 1**: Copy the lines from the apt sources.list entries section of the PPA overview page. For example:

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main

**Step 2**: On your Ubuntu computer, open System > Administration > Software Sources.

**Step 3**: Click the Third Party Software tab.

**Step 4**: Click the Add button.

**Step 5**: Paste the individual lines copied in step 1 by clicking the Add Source button.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

**Adding the PPA's key to Ubuntu**

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't changed since Launchpad built it.

**Note:** This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

**Step 1**: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, *the portion after the slash*, e.g: 12345678.

**Step 2**: Open your terminal and enter:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 12345678

Replace 12345678 with the key id you copied in step 1.

**Step 3**: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from a PPA, using a tool such as apt-get in the Terminal or Synaptic.

**Chromium** (Google chrome)
**sudo apt-get install chromium-browser** (after repositories are added)

**deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main**
**deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5**

**Note:** If you hate underlines as much as I do, this extension for Chrome should help **[http://www.chromeextensions.org/appearance-functioning/no-underlined-links/]("http://www.chromeextensions.org/appearance-functioning/no-underlined-links/")**

**Compiz**

**deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 42C24D89**

**ClamAV**

**deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main** 
**deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5ADC2037**

**Shutter**

**deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 009ED615**

**FireFox**

**deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main**
**deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C713DA6**

**X Updates**

**deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main**
**deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main**

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9**


**Collection of useful commands...**
---------------------------------------------------------------   
**Searching for Packages:**             apt-cache search some_string      
**Show Package Info:**         apt-cache showpkg xxx             
**Show Package Dependencies:**     apt-cache depends xxx             
**Install:**             apt-get install xxx               
**Re-Install:**             apt-get --reinstall install xxx   
**Remove:**                     apt-get remove xxx                
**Remove All (configs too):**     apt-get remove --purge xxx
**Upgrade:**             apt-get -u upgrade
**Show Upgrades:**             apt-show-versions -u
**Show All Installed Packages:**    dpkg --list                       
**Find Package by File Name:**     apt-file search /bin/ping         
**Find filenames in a Package:**     apt-file list xxx                 
**Updating the apt-file Cache:**     apt-file update
**Info on Installed Package:**        aptitude show xxx
**System Hardware Info:**             sudo lshw > hardware.txt

**Linux Command Directory [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)**

**Linux Commands - A practical reference [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)**

Clean up your system and free up space with **sudo apt-get clean** and **sudo apt-get autoremove**

If you're curious (like me) or have the need to know **uname -a && cat /etc/*release** in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.


Ok, about **wine**...in most cases a free to use Linux program will work just as well as apps on that other well known operating system. I don't recommend it but for the folks that like wine this wiki should help **[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)**

**Wine Application Database (AppDB) [http://appdb.winehq.org/](http://appdb.winehq.org/)**


To my friends...

I'm more than willing to add your suggestions and reference your favorite applications, this is your post as much as mine. I do ask that you keep the description brief and on a general level and degree of difficulty minimal (for new users) when making recommendations. I started posting "Ubuntu Desktop Computing Made Easy" a while back (Gutsy Gibbon) mainly out of the frustration I had getting my workstation and personal computer to perform as expected (without hours upon hours of setup, search and configuration). It's my goal to make it "easy" for anyone to setup an Ubuntu Desktop Computer with everything they need or want, in a short period of time, ensuring the overall experience is an enjoyable one. 

**Note:** This post can be found very quickly by doing a Google search on Ubuntu Desktop Computing Made Easy. If you would like to link to this post or publish it elsewhere I do request that you obtain permission and give credit where credit is due.

Regards,

-TrakerJon

Dell GX270 3.2GHz Pentium 4 w/ 2Gb SDRAM using NVIDIA GeForce 6200 AGP w/ 256Mb video and MSI Wind Netbook U100 1.6GHz Intel Atom w/ 2Gb SDRAM using Intel Mobile 945GME Express video on Ubuntu 10.04

---

### Post by ublintu on 2010-05-04
Thank you for the new [B]Ubuntu Desktop Computing Made Easy!
[/B]

---

### Post by dino99 on 2010-05-04
need to be a sticky if you dont want it lost into the other so numerous threads  :confused:

---

### Post by mb_webguy on 2010-05-04
Nice, but I'd just like to point out that the large block of codecs and other extras can pretty much be reduced to:```
sudo apt-get install ubuntu-restricted-extras non-free-codecs
```The ubuntu-restricted-extras package also installs Flash, the Microsoft TrueType fonts, unrar, and the IcedTea Java plugin.

Also, some of the other somewhat scary-looking blocks could likewise be reduced due to them including a lot of dependencies that will otherwise be installed automatically.  For example, "sudo apt-get install gimp" will install GIMP and all of its dependencies.

---

### Post by TrakerJon on 2010-05-04
> **mb_webguy said:**
> Nice, but I'd just like to point out that the large block of codecs and other extras can pretty much be reduced to:```
sudo apt-get install ubuntu-restricted-extras non-free-codecs
```The ubuntu-restricted-extras package also installs Flash, the Microsoft TrueType fonts, unrar, and the IcedTea Java plugin.

Also, some of the other somewhat scary-looking blocks could likewise be reduced due to them including a lot of dependencies that will otherwise be installed automatically.  For example, "sudo apt-get install gimp" will install GIMP and all of its dependencies.


Unfortunately, if I did what you suggest about one third of the codecs I provided would then be unavailable to the end-user. I've also had problems in the past with those particular bundled codec packages, I would hate to pass that along to a new user to troubleshoot...or have them wandering around for the "one" missing codec they need.

In regard to Gimp, "sudo apt-get install gimp" doesn't install all the functionality that I've included with the install references provided. Why make people hunt for the additional functionality? It's all about "making it easy".

I respect your suggestions, your hearts in the right place, both good in theory but not always in practice.

Cheers!

---

### Post by dino99 on 2010-05-04
no one need to add confusion, only redirect new comers to Ubuntu Software Center, everything is clearly sorted, nobody under pressure be able to read and understand long bla-bla and be outdated in few months.

---

### Post by TrakerJon on 2010-05-04
> **dino99 said:**
> need to be a sticky if you dont want it lost into the other so numerous threads  :confused:

That's up to the powers that be...I agree with you completely. ;)

---

### Post by TrakerJon on 2010-05-04
> **ublintu said:**
> Thank you for the new **Ubuntu Desktop Computing Made Easy!**

My pleasure, please share with others when possible.

Cheers!

---

### Post by TrakerJon on 2010-05-04
> **dino99 said:**
> no one need to add confusion, only redirect new comers to Ubuntu Software Center, everything is clearly sorted, nobody under pressure be able to read and understand long bla-bla and be outdated in few months.

I see what you're saying but I typically update the post until the next official release is made to the public. There are often third party application and operating system updates that require such revisions. I also test new software all the time, many of which find their way on to the post as well.

Enjoy and share!

---

### Post by techunit on 2010-05-04
Could a moderator please make this a sticky. It is quite good and very well written. Good job. Placing it in the absolute beginners forum should do the trick.

---

### Post by TrakerJon on 2010-05-04
> **techunit said:**
> Could a moderator please make this a sticky. It is quite good and very well written. Good job. Placing it in the absolute beginners forum should do the trick.

Thank you for the good words, glad folks are checking it out.

Traker

---

### Post by Paresh on 2010-05-05
Good stuff here.

Gnome-Commander - Did you know that you can get a two pane view in nautilus by pressing F3.

Encryption - I like to use ecryptfs ```
sudo apt-get install ecryptfs-utils
```.  This gives you an encrypted private folder in your home directory and allows you to encrypt and mount removable media.  It's integrated into the filesystem as well, so you just treat it as a normal folder.

I also like to use etckeeper to automatically backup changes to /etc when editing config files.  It's usually the first thing I setup on a clean install.

Oh Yeah, +1 for the sticky

---

### Post by TrakerJon on 2010-05-05
> **Paresh said:**
> Good stuff here.

Gnome-Commander - Did you know that you can get a two pane view in nautilus by pressing F3.

Encryption - I like to use ecryptfs ```
sudo apt-get install ecryptfs-utils
```.  This gives you an encrypted private folder in your home directory and allows you to encrypt and mount removable media.  It's integrated into the filesystem as well, so you just treat it as a normal folder.

I also like to use etckeeper to automatically backup changes to /etc when editing config files.  It's usually the first thing I setup on a clean install.

Thank you for the suggestions, I'll definitely check out ecryptfs, it seems like it might be very useful. I'm a little hesitant to include etckeeper though, it my cause more harm than good for new users...that would probably fall under a "tips and tricks" Ubuntu Forum post.

Cheers and thanks again!

---

### Post by guisar on 2010-05-05
Definitely should be a sticky- great writeup and giving back to the Community (he took an Intro to Linux course from me and seeing this makes me very happy).

---

### Post by TrakerJon on 2010-05-05
> **guisar said:**
> Definitely should be a sticky- great writeup and giving back to the Community (he took an Intro to Linux course from me and seeing this makes me very happy).

Thanks Professor! :grin: That means a lot coming from you.
Regards to all your new students!

Traker

---

### Post by bill516 on 2010-05-05
This post by TrakerJon is enormously helpful, since it lists a number of things I have to do with each new Ubuntu release; e.g., install build-essentials and vim.  They are easy to forget until I learn once again that they are not there.

In the past I have done install Ubuntu restricted extras, added install w64 codecs and libdvdcss2 and gone my merry way.  Not with Lucid!  Until I hit TrakerJon's post I was one frustrated fellow.  My usual gambit just did not work.  You tube and NYTimes video were MIA until I found this thread.

May I make a suggestion?  Let's pull just that part of the post that specifies how to do the multi-media codec setup for Lucid and post it as a sticky such that people can find it easily.  Anyone new to Linux or to Ubuntu will appreciate it as will forgetful veterans like myself!

Then let's get to the heart of this matter, which is a downright silly way of dealing with the entire multimedia codecs issue.

In much of the world distribution of these things is not bound up in copyrighted intellectual property issues. Sadly that is not true in the United States.

We cannot ask Canonical to violate American law.  Fair enough.

So perhaps servers outside the United States carry an Ubuntu version with codecs that does not violate laws in that part of the world.

Meanwhile, American versions of Ubuntu -- as downloaded from U.S. based servers -- come with a "get your codecs here" button on the desktop.  We click. Canonical says "pay ___ dollars for the codecs you need/want."  So we pay or not as we choose and stop all this infernal nonsense.

My idea seems crude but the Software Center is a perfect vehicle for some solution such as this.

Might we at least think about it?

Meanwhile, let me thank TrakerJon for helping both my Lucid Lynx configuration and my blood pressure.  Well done!

---

### Post by TrakerJon on 2010-05-05
> **bill516 said:**
> This post by TrakerJon is enormously helpful, since it lists a number of things I have to do with each new Ubuntu release; e.g., install build-essentials and vim.  They are easy to forget until I learn once again that they are not there.

In the past I have done install Ubuntu restricted extras, added install w64 codecs and libdvdcss2 and gone my merry way.  Not with Lucid!  Until I hit TrakerJon's post I was one frustrated fellow.  My usual gambit just did not work.  You tube and NYTimes video were MIA ...

I know where you've been my friend...more than once I've been in the "it should work this way" scenario. One day I just started testing out all popular applications, add-ons and plugins out for myself. This is what works for me and I hope many others looking for an alternative to Windows® operating systems and Microsoft® applications. I've tested everything listed in this post on both my MSI Netbook and Dell GX270 with great success. Lucid seems to be stable with no big surprises so far, hopefully Ubuntu 10.04 LTS and all the associated apps will work for more people than ever before. 

Enjoy and share!

Traker

---

### Post by scouser73 on 2010-05-05
Excellent posting, this should definitely be a sticky.  I noticed that Songbird is in there, unfortunately the makers of Songbird aren't doing anymore builds for Linux so that could be removed; also I see you've included Bubble Shooter, this means I'm going to have to install it now lol. Nice work.

---

### Post by TrakerJon on 2010-05-05
> **scouser73 said:**
> Excellent posting, this should definitely be a sticky. I noticed that Songbird is in there, unfortunately the makers of Songbird aren't doing anymore builds for Linux so that could be removed; also I see you've included Bubble Shooter, this means I'm going to have to install it now lol. Nice work.


Glad you like the post. I haven't heard Songbird is being discontinued (they're still hiring C++ developers)? If nothing else it's been packaged for Lucid so we'll keep it for now. Yeah, Frozen Bubble is kind of hard to resist at times hahaha. Party on!

Traker

---

### Post by FacsimileSmiles on 2010-05-05
Hi, just wanted to say thank you.  I'm a brand-spankin'-new ubuntu user, and just upgraded to 10.4 from Karmic.  So far, every problem I've had has had a solution listed on this forum, and your post just opened up whole new vistas (*ahem!*) of what's available!  

Anyway, sorry for getting all gushy, it's just awesome.  Thank you.

---

### Post by Paresh on 2010-05-06
You can also try these:-
**pyrenamer**, a mass file renamer.
**stellarium** for any budding astronomers out there
**zenity** makes nice GUI dialogs for your scripts
**xautomation** allows you to simulate keypresses in scripts (possibly for advanced users)

---

### Post by philinux on 2010-05-06
Thread moved to installation and upgrades.

---

### Post by TrakerJon on 2010-05-06
> **FacsimileSmiles said:**
> Hi, just wanted to say thank you.  I'm a brand-spankin'-new ubuntu user, and just upgraded to 10.4 from Karmic.  So far, every problem I've had has had a solution listed on this forum, and your post just opened up whole new vistas (*ahem!*) of what's available!  

Anyway, sorry for getting all gushy, it's just awesome.  Thank you.

Glad to see that I can help folks that would otherwise be having difficulties. I've found it's far better to show people how to do the basics first before leaving them to figure out more advanced tasks or issues. New users (like I once was) need a foundation to build up from and hopefully this post provides that for them. Thank you for the good words and please share with friends and associates.

Regards,

Traker

---

### Post by TrakerJon on 2010-05-06
> **philinux said:**
> Thread moved to installation and upgrades.

Whooops! The powers that be have shuffled my post off to another support area....and back again. Still no sticky though ;)

---

### Post by TrakerJon on 2010-05-06
> **Paresh said:**
> You can also try these:-
**pyrenamer**, a mass file renamer.
**stellarium** for any budding astronomers out there
**zenity** makes nice GUI dialogs for your scripts
**xautomation** allows you to simulate keypresses in scripts (possibly for advanced users)

Paresh, your suggestions are great but a bit advanced for new users. I'd like to catch up with you in a couple of weeks and work on a advanced users post...something like "Ubuntu Advanced Desktop Computing Made Easy".

Cheers!

Traker

---

### Post by uncleV on 2010-05-06
Thank you!

+1 for sticky.

---

### Post by TrakerJon on 2010-05-06
> **uncleV said:**
> Thank you!

+1 for sticky.

You're very welcome and thank you for the sticky vote ;)

---

### Post by ublintu on 2010-05-06
"work on a advanced users post...something like "Ubuntu Advanced Desktop  Computing Made Easy".
Sounds good. It would be great.

---

### Post by Paresh on 2010-05-07
> **TrakerJon said:**
> Paresh, your suggestions are great but a bit advanced for new users. I'd like to catch up with you in a couple of weeks and work on a advanced users post...something like "Ubuntu Advanced Desktop Computing Made Easy".


Well, except for stellarium, I agree with you.  An advanced version sounds like a good idea.  Feel free to contact me when you're ready.

---

### Post by TrakerJon on 2010-05-07
> **Paresh said:**
> Well, except for stellarium, I agree with you.  An advanced version sounds like a good idea.  Feel free to contact me when you're ready.

Right on Stellarium, I just added it, nice application. I am interested in posting a more advanced Made Easy post at this point having posted a more or less a new users oriented post for the last three releases. I should have more time in late June, we'll catch up then and thanks.

Traker

---

### Post by GaryUK on 2010-05-09
TrakerJon,

Great work - I found this very informative and it filled in a lot of missing stuff especially medibuntu & multimedia (the complete multimedia how-to does not seem to have yet been updated for lucid).

May I suggest instead of Gantt Project something called Open Proj ?? I think it is a lot better at handling M$ Project mpp files than Gantt Project and so would therefore be more of use to relatively new Ubuntu converts.

I think it can be downloaded from here as a deb file:
[http://sourceforge.net/projects/openproj/files/](http://sourceforge.net/projects/openproj/files/)

Licensing is CPAL and there is an M$ version for those interested (M$ version proved most useful as my company do not give us all copies of M$ Project to use!!)

Once again, thanks for your work and Rock On !!

:guitar:

---

### Post by TrakerJon on 2010-05-09
> **GaryUK said:**
> TrakerJon,

Great work - I found this very informative and it filled in a lot of missing stuff especially medibuntu & multimedia (the complete multimedia how-to does not seem to have yet been updated for lucid).

May I suggest instead of Gantt Project something called Open Proj ?? I think it is a lot better at handling M$ Project mpp files than Gantt Project and so would therefore be more of use to relatively new Ubuntu converts.

I think it can be downloaded from here as a deb file:
[http://sourceforge.net/projects/openproj/files/](http://sourceforge.net/projects/openproj/files/)

Licensing is CPAL and there is an M$ version for those interested (M$ version proved most useful as my company do not give us all copies of M$ Project to use!!)

Once again, thanks for your work and Rock On !!

:guitar:


The multimedia codec section was updated today. The learning curve for OpenProj is a little more difficult than Gnome Planner but I'll be glad to include it in the post as well.

Cheers!

---

### Post by Hambombj on 2010-05-09
Traker Jon,

I would just like to say, Thank you!

What a great thread !

As a sort of Noob it has helped me no end.

I hope one day i can help other users as much as you have.

:) Ian

---

### Post by TrakerJon on 2010-05-09
> **Hambombj said:**
> Traker Jon,

I would just like to say, Thank you!

What a great thread !

As a sort of Noob it has helped me no end.

I hope one day I can help other users as much as you have.

:) Ian

Thanks Ian,

Everyone has to start somewhere, no worries. Enjoy and share, the rest will come with time and experience. Linux has come a long way since the late 90's, the more people get involved the better it gets.

Cheers!

Traker

---

### Post by n4lbl on 2010-05-10
I'm sorry if this sounds like "let no good deed go unpunished" but I'm struggling to follow your instructions.  My goal is to make videos from nytimes.com work in Firefox.  Youtube and some others already work.  

First I ran your large command that started 
[INDENT]sudo apt-get install freepats gstreamer-dbus-media-service gstreamer-tools..... [/INDENT] 
Almost everything was the latest version.  Most entries were set to "manually installed".  Did I do something wrong?  Does that mean that the Update Manager won't update these items?  I also got this message:  
[INDENT]Package w32codecs is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package w32codecs has no installation candidate [/INDENT] 
Is that important?

I followed the instructions for Java and got:  [INDENT]Package sun-java6-bin is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
However the following packages replace it: 
  sun-java6-jre 
E: Package sun-java6-bin has no installation candidate [/INDENT]

Reading the rest I didn't see anything that I understood would help.  Do you have the time to make any suggestions?

thanx,,,

---

### Post by TrakerJon on 2010-05-10
> **n4lbl said:**
> I'm sorry if this sounds like "let no good deed go unpunished" but I'm struggling to follow your instructions.  My goal is to make videos from nytimes.com work in Firefox.  Youtube and some others already work...


I'm going to assume that you don't have the Medibuntu Repositories setup in your System > Administration > Software Sources > Other Software.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources. Directions are on this site: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") or follow my post regarding the adding of mirror Medibutu repositories. 

I visited NY Times Online and was able to play audio and video with success both MP3 streams and Flash Videos. I use an nVidia graphics card w/ 256Mb video RAM and an Intel AC'97 Audio Controller hope that helps.

Cheers!

---

### Post by n4lbl on 2010-05-10
Thanks.  I 1) ran the commands for access to the Medibuntu Repository, 2) re-did the giant command for Codecs, plug-ins and accessories..., and 3) re-ran The latest Sun Java JRE commands.  It was obviously very different this time (!) but something remains wrong.  The symptom is that the video area on the screen is white with nothing to click on.

thanx,,,
   Alan

---

### Post by TrakerJon on 2010-05-10
> **n4lbl said:**
> Thanks.  I 1) ran the commands for access to the Medibuntu Repository, 2) re-did the giant command for Codecs, plug-ins and accessories..., and 3) re-ran The latest Sun Java JRE commands.  It was obviously very different this time (!) but something remains wrong.  The symptom is that the video area on the screen is white with nothing to click on.

thanx,,,
Alan

I have a feeling you installed the bundled codec packages ubuntu-restricted-extras and non-free-codecs before seeing my post (at the advice of someone else). Unfortunately, installing the bundled codecs does cause problems for a lot of folks. I haven't figured out how to fully recover from that yet (over looking some config files in my home folder no doubt) without a complete reinstall. You can try un-installing Flash from a terminal prompt **sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer** then and reinstalling **sudo apt-get install flashplugin-nonfree flashplugin-installer** ...after that if it still doesn't work you may want to consult a higher authority.

If you didn't install the bundled codecs simply install Flash **sudo apt-get install flashplugin-nonfree flashplugin-installer**

Good luck my friend!

---

### Post by Nesaskewatch on 2010-05-14
Boy!  This is a great list of cool stuff!

Thanks for making it easy!

Cheers!

---

### Post by TrakerJon on 2010-05-14
> **Nesaskewatch said:**
> Boy!  This is a great list of cool stuff!

Thanks for making it easy!

Cheers!

Enjoy and share!

Regards,

Traker

---

### Post by BuffaloX on 2010-05-15
Sun-Java is no longer in the repositories.
Which sucks because some crucial services don't work without it.
Like the official government approved danish "Digital Signature" and in some cases homebanking.

---

### Post by TrakerJon on 2010-05-16
> **BuffaloX said:**
> Sun-Java is no longer in the repositories.
Which sucks because some crucial services don't work without it.
Like the official government approved danish "Digital Signature" and in some cases homebanking.

I'm not sure what you mean...they were bought by Oracle but version 6 along with a recent update is available. Did you need some assistance in this regard? 

Traker

---

### Post by BuffaloX on 2010-05-16
> **TrakerJon said:**
> I'm not sure what you mean...they were bought by Oracle but version 6 along with a recent update is available. Did you need some assistance in this regard? 

Traker

Thanks, but I found a guide for installing Sun-Java on Lucid.

You say version 6 is available, and that may be true, but not in the Ubuntu 10.04 repositories.

I checked the Medibuntu packages, and it isn't mentioned on their homepage.
So I don't think it's included in any of the repositories you recommend adding to Ubuntu.

---

### Post by Rodney9 on 2010-05-16
Thank You !

---

### Post by TrakerJon on 2010-05-17
> **BuffaloX said:**
> Thanks, but I found a guide for installing Sun-Java on Lucid.

You say version 6 is available, and that may be true, but not in the Ubuntu 10.04 repositories.

I checked the Medibuntu packages, and it isn't mentioned on their homepage.
So I don't think it's included in any of the repositories you recommend adding to Ubuntu.

If you follow the instructions on this post for the Medibuntu Repositories you can install Sun Java Version 6 Update 20 and verify the installation at [http://www.java.com]("http://www.java.com")

After adding the Medibuntu repository of your choice, run the following command from a terminal session...

**sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc odbcinst**

Cheers!

Traker

---

### Post by TrakerJon on 2010-05-17
Just a side note...the Sun Java installation referenced above works for both Firefox and Google Chrome.

Traker

---

### Post by TrakerJon on 2010-05-17
I'm still testing Google Chrome, so far so good. It does appear to be faster like they claim at Google but some web sites still don't recognize it as an accepted secure browser. Everything comes with time I guess.

Party on!

Traker

---

### Post by TrakerJon on 2010-05-17
> **Rodney9 said:**
> Thank You !

You're very welcome.

Traker

---

### Post by Vi3GameHkr on 2010-05-18
After pasting the long block for codecs into Terminal, I come up with the error "E: Couldn't find package gstreamer0.10-pitfdll"

Either way, this looks like you spent some great deal of time putting it together, although the organization of the thread is a bit hard to follow (you have programs to modify PDFs in two different areas!) and find exactly what I need without reading the whole thing.

[EDIT] And have you checked out the packages that come with Ubuntu Studio?  I'm sure most of them are pretty good, although I guess Studio is geared towards more advanced users.

---

### Post by TrakerJon on 2010-05-19
> **Vi3GameHkr said:**
> After pasting the long block for codecs into Terminal, I come up with the error "E: Couldn't find package gstreamer0.10-pitfdll"

Either way, this looks like you spent some great deal of time putting it together, although the organization of the thread is a bit hard to follow (you have programs to modify PDFs in two different areas!) and find exactly what I need without reading the whole thing.

[EDIT] And have you checked out the packages that come with Ubuntu Studio?  I'm sure most of them are pretty good, although I guess Studio is geared towards more advanced users.

Many of these installations require access to the Medibuntu Repository and enabling some additional software sources (as referenced with the codecs install)...or verify that your Medibuntu Repository entry in Software Sources is correct. I just successfully un-installed and reinstalled the gstreamer0.10-pitfdll codecs without issue. 

Please note the GetDeb apps are grouped together to ensure that the GetDeb Repository is configured prior to installation of the listed apps. This is to make it easier for you not harder. ;) 

The post isn't that long or difficult to read if you have 15-20 minutes to spare...and if you have a fast internet connection and a moderately fast computer everything on this post can be installed in just under two hours. Imagine the time you would spend searching multiple posts otherwise. :)

Most of the apps in Ubuntu Studio you'll find listed here...and some others you might like even better.

Cheers!

Traker

---

### Post by TrakerJon on 2010-05-19
I'm sad to say I had to remove avast! antivirus due to ongoing issues with updates and program usage. I've referenced ClamAV and ClamTk until the folks at avast! acknowledge the problems and resolve them.

Remember to scan all downloads from questionable sources...

Regards,

Traker

---

### Post by Vi3GameHkr on 2010-05-24
Gah I added all three mirrors to my repository list, and selected all the source code repositories as well and I'm still getting that same error.

Is an antivirus as necessary in Ubuntu as it is in Windows?  I know it's a little bit easier to mess things up for good in Windows, and I don't keep any extremely confidential information on my computer.

---

### Post by TrakerJon on 2010-05-24
> **Vi3GameHkr said:**
> Gah I added all three mirrors to my repository list, and selected all the source code repositories as well and I'm still getting that same error.

Is an antivirus as necessary in Ubuntu as it is in Windows?  I know it's a little bit easier to mess things up for good in Windows, and I don't keep any extremely confidential information on my computer.

Well, you really only need one of the mirror sites, did you get the keyring? Paste this command into a terminal: **sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring** and get the keyring if you don't already have it. 

The error "E: Couldn't find package gstreamer0.10-pitfdll" seems like your system is trying to pull from a physical drive, possibly your CD/DVD drive? You might want to try un-checking that option in System > Administration > Software Sources > Ubuntu Software > Installable from CD-ROM/DVD (if it's currently checked).

Antivirus is necessary, yes...probably not as necessary as Windows but if you share files with Windows users or encounter a virus that does affect UNIX/Linux you'll be glad you have it installed. I strongly suggest you scan all questionable downloads.

Regards,

Traker

---

### Post by Vi3GameHkr on 2010-05-25
I am following the instructions very closely, and I have discovered that the heart of this error is the fact that the package simply isn't available for 64-bit machines.

Might want to put that in there.  [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258)

[EDIT] I'll take a few minutes to try to weed out the packages in the codecs block that aren't available on 64-bit and edit this post again when I'm done.

[EDIT] The following packages all reported unavailable, and I'm not quite sure that they are all not available on 64-bit, but the main difference between my laptop and desktop is that my laptop has 32-bit 10.04 installed and my desktop has 64-bit.  Both have 64-bit processors, and my laptop is able to install all of the codec packages no problem.

gstreamer0.10-pitfdll libopenspc0 w32codecs avifile-win32-plugin lib64gcc1 lib64gomp1 lib64stdc++6 libc6-amd64 libc6-dev-amd64

---

### Post by PhoenixDream on 2010-05-25
Thank you for this! I appreciate the time and effort that was put in putting this guide together!

Keep up the good work!

:guitar:

---

### Post by TrakerJon on 2010-05-25
> **Vi3GameHkr said:**
> I am following the instructions very closely, and I have discovered that the heart of this error is the fact that the package simply isn't available for 64-bit machines.

Might want to put that in there.  [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-pitfdll/+bug/172258)

[EDIT] I'll take a few minutes to try to weed out the packages in the codecs block that aren't available on 64-bit and edit this post again when I'm done.

[EDIT] The following packages all reported unavailable, and I'm not quite sure that they are all not available on 64-bit, but the main difference between my laptop and desktop is that my laptop has 32-bit 10.04 installed and my desktop has 64-bit.  Both have 64-bit processors, and my laptop is able to install all of the codec packages no problem.

gstreamer0.10-pitfdll libopenspc0 w32codecs avifile-win32-plugin lib64gcc1 lib64gomp1 lib64stdc++6 libc6-amd64 libc6-dev-amd64

Ahhh the devil is in the details. Yes, there are some ongoing issues with 64 bit systems relating to some of the available codecs but from your reply it looks like there are 64 bit packages also failing to install on your system. I'm not sure what you have going on there, it may be a corrupt install or bugs that need to be reported. This post is oriented towards 32 bit systems even though I have included some entries for both (in the large block of codec references).

Sorry it wasn't mentioned earlier, the w64codecs for Lucid can be found at **[http://packages.medibuntu.org/lucid/w64codecs.html](http://packages.medibuntu.org/lucid/w64codecs.html)** 

You may have to refer to other posts to resolve the issues you're having, I haven't started testing in a 64 bit environment yet.

Cheers!

Traker

---

### Post by TrakerJon on 2010-05-25
> **PhoenixDream said:**
> Thank you for this! I appreciate the time and effort that was put in putting this guide together!

Keep up the good work!

:guitar:

Thanks! Glad I could be of some help, please share whenever possible.

Traker

---

### Post by Vi3GameHkr on 2010-05-25
I doubt I'll run across more than one of the nonsupported libraries but I can figure something out when the time comes.  I might be getting a new hard drive this summer so I might just back up my personal files and wipe my system.  My windows install is a couple months over for some refreshment anyways and this isn't the first problem I've had with 64-bit.

---

### Post by TrakerJon on 2010-05-28
> **Vi3GameHkr said:**
> I doubt I'll run across more than one of the non-supported libraries but I can figure something out when the time comes.  I might be getting a new hard drive this summer so I might just back up my personal files and wipe my system.  My windows install is a couple months over for some refreshment anyways and this isn't the first problem I've had with 64-bit.

Sounds like a plan. You would be surprised how much you can find in the forums, give it a go.

Cheers!

Traker

---

### Post by TrakerJon on 2010-10-04
Just checking back, haven't needed to make any revisions in a good while. Are there any new apps you would like to include? Please post them for review and testing.

Regards,

Traker

---

### Post by Technotart on 2010-10-13
Remarkably useful and informative for a new..ish..bie.  Very many thanks.

---

### Post by n4lbl on 2010-10-14
After the agony of trying to solve problems piecemeal on 10.04 and discovering this thread I determined to look here first before going to 10.10.  TrakerJon, do you have any suggestions yet for 10.10??

thanx,,,

---

### Post by Rodney9 on 2010-10-14
Have the 64bit issues with some of the codecs etc been resolved yet ?

Also if you have installed the *bundled codec packages ubuntu-restricted-extras and non-free-codecs* can you remove them ? or is ok to install your codecs on top ?

---

### Post by TrakerJon on 2010-10-15
> **Technotart said:**
> Remarkably useful and informative for a new..ish..bie.  Very many thanks.

I'm glad I could help...I'm looking forward to the next release as well.

---

### Post by TrakerJon on 2010-10-15
> **n4lbl said:**
> After the agony of trying to solve problems piecemeal on 10.04 and discovering this thread I determined to look here first before going to 10.10.  TrakerJon, do you have any suggestions yet for 10.10??

thanx,,,


I haven't jumped into 10.10 just yet...but I'm considering the possibility within the next month...check back frequently. 

Cheers!

---

### Post by TrakerJon on 2010-10-15
> **Rodney9 said:**
> Have the 64bit issues with some of the codecs etc been resolved yet ?

Also if you have installed the *bundled codec packages ubuntu-restricted-extras and non-free-codecs* can you remove them ? or is ok to install your codecs on top ?


Since folks tend to use older 32 bit machines for Linux I haven't tried to tackle the 64 bit issues quite yet. I do know that installing the bundled restricted extras can cause issues on both and their removal doesn't always correct problems when manually installing codecs afterwards. My guess is there are some config files that don't get removed. If all else fails...wipe and reinstall carefully. VLC is a great media player by the way.

---

### Post by n4lbl on 2010-10-16
> **TrakerJon said:**
> I haven't jumped into 10.10 just yet...but I'm considering the possibility within the next month...check back frequently. 

Cheers!
Thanks.

---

### Post by TrakerJon on 2010-10-20
> **n4lbl said:**
> Thanks.

I tried to make an initial Ubuntu 10.10 post this morning but for some reason it is either being reviewed, has been rejected or lost in cyber space. I'll continue making revisions with the hope that it will show up sometime today.

:-k 

Traker

---

### Post by TrakerJon on 2010-10-20
Ok folks, while I'm waiting for the administrators to accept/deny my Ubuntu Maverick post ...these bits of info may come in handy.


**Maverick Meerkat**

There is a known issue with kernal update 2.6.35 (and the associated header files) causing a FATAL : MODPROBE error at startup. I recommend installing the kernal update (and the associated header files) after installing all other updates, it works for me this way. If you've already installed them (as a recommended security update), edit /etc/initramfs-tools/initramfs.conf (**sudo gedit /etc/initramfs-tools/initramfs.conf** in the console) and change the line MODULES=most to MODULES=dep. Then use Synaptic to reinstall initramfs-tools.

**Lucid Lynx and Maverick Meerkat**

There is a known concern with nVidia drivers and the Plymouth Logo at startup in Ubuntu see **[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)**

---

### Post by TrakerJon on 2010-10-21
Well, I guess the mods are a little backed up...Ubuntu Desktop Computing Made Easy (Maverick MeerKat 10.10) still hasn't showed up in the forum. Check back later folks!


Traker

---

### Post by TrakerJon on 2010-10-23
Ubuntu Desktop Computing Made Easy (Maverick Meerkat v10.10) can be found at [http://ubuntuforums.org/showthread.php?t=1602315](http://ubuntuforums.org/showthread.php?t=1602315)

Cheers!

Hopefully they will move it to this forum ;-)

---

### Post by opiumpoetry on 2011-03-10
[B]Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco bzrtools python-paramiko
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>[/B]

these instructions are not very precise.

the first line installs fidefrag.

but every time I run fidefrag, I get this:

[B]You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".[/B]

what does this mean?

---

### Post by TrakerJon on 2011-11-20
> **opiumpoetry said:**
> [B]Defrag (or fidefrag I should say)

sudo apt-get install bzr python-psyco bzrtools python-paramiko
bzr branch lp:fidefrag
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>[/B]

these instructions are not very precise.

the first line installs fidefrag.

but every time I run fidefrag, I get this:

[B]You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".[/B]

what does this mean?

You can ignore that message, it should install what you need just fine.

---

