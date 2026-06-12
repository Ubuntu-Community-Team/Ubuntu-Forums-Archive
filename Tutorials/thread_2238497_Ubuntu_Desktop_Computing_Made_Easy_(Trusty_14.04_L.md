---
title: "Ubuntu Desktop Computing Made Easy (Trusty 14.04 LTS)"
date: 2014-08-08
forum: Tutorials
---

### Post by TrakerJon on 2014-08-08
[SIZE=3]**Ubuntu Desktop Computing Made Easy** (Trusty 14.04 LTS)[/SIZE]

**Kubuntu Desktop** [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)
**Ubuntu Gnome** Desktop [http://ubuntugnome.org/download](http://ubuntugnome.org/download)
**Ubuntu Desktop** [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Download your desired flavor of Ubuntu 14.04, burn the .iso file to a blank disk and then install it on your "Trusty" computer. Next, update the operating system by searching for Software & Updates and launching the application. Under the Other Software tab check the two boxes for Canonical partners and reload when prompted. Once the changes have been made launch the Software Updater and install all available updates. After rebooting, in Software & Updates under the Additional Drivers tab, enable the appropriate one(s) for your system (if desired).

Note: If you check the box to include 3rd party software during the installation this will give you most of the multimedia codecs you'll need (more are listed below). Some of the available drivers can produce undesired results when installing "Additional Drivers" (if in doubt ask or search on the forum). If you're installing Ubuntu within a virtual machine 3D Acceleration can cause application issues.


**Gnome Users**

Visit [https://extensions.gnome.org](https://extensions.gnome.org) click on the Installed extensions reference at the top of the page and turn on the desired options or search for a variety of others (a reboot may be required to enable options). When using Classic Gnome be aware that autoremove may cause issues when logging back into Gnome 3 (simply re-installing Gnome will recover lost extensions and other components).


**Email Clients**

Thunderbird and SpamAssassin are a good combination for a basic email client (Ubuntu Gnome includes Evolution by default)
sudo apt-get install thunderbird spamassassin xul-ext-calendar-timezones xul-ext-lightning

Note: This page will help you setup SpamAssassin [http://www.scls.info/technology/email/tb_junkfilter.html](http://www.scls.info/technology/email/tb_junkfilter.html)


**Tools and Utilities**

Synaptic Package Manager
sudo apt-get install synaptic

Cups-PDF for printing to PDF files
sudo apt-get install cups-pdf

Manage Users and Groups
sudo apt-get install gnome-system-tools

Gufw the GUI interface for Uncomplicated Firewall
sudo apt-get install gufw

Transmageddon converts most multimedia formats
sudo apt-get install transmageddon

AceoneISO2 is a CD/DVD image manipulator (use with .iso files
sudo apt-get install acetoneiso

Adaptive Readahead Daemon for faster application startup times
sudo apt-get install preload

K3b is a full-featured CD/DVD/Blu-ray burning and ripping application
sudo apt-get install k3b

Htop, SysInfo and HardInfo for system information and benchmarking
sudo apt-get install htop sysinfo hardinfo

Shutter for screen captures (VirtualBox users disable 3D Acceleration or your captures could be all in black)
sudo apt-get install shutter

Avidemux cross-platform video editor from the GetDeb repository [http://www.getdeb.net/updates/Ubuntu/14.04](http://www.getdeb.net/updates/Ubuntu/14.04)
sudo apt-get install avidemux2.6-qt

File Compression and Extraction
sudo apt-get install unace rar unrar p7zip-rar p7zip zip unzip sharutils uudeview mpack arj cabextract file-roller

Note: Use Archive Manager for manipulating these file types.


**Antivirus**

ClamAV
sudo apt-get install clamav clamtk

Operations available from a terminal session...

Update virus definitions: sudo freshclam
Scan files in your home directory: sudo clamscan
Scan files in an entire directory: sudo clamscan -r /<directory name>
Scan on the entire drive: sudo clamscan -r /

Update ClamTk [http://clamtk.sourceforge.net](http://clamtk.sourceforge.net)

Note: If you're having problems getting virus definition updates edit (sudo gedit /etc/clamav/freshclam.conf) with a location near you [http://www.clamav.net/mirrors.html](http://www.clamav.net/mirrors.html) (ex. add DatabaseMirror clamav.amerinoc.com after the last line). You can also manually download main.cvd, daily.cvd and bytecode.cvd files from [http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/) and sudo mv *.cvd /var/lib/clamav to update.


**Image Viewing, Graphics Manipulation and Illustration**

Pinta is a lot like MS Paint
sudo apt-get install pinta

Shotwell
sudo apt-get install shotwell

Inkscape for illustrations
sudo apt-get install inkscape

Dark Table
sudo apt-get install darktable

PhotoFilmStrip
sudo apt-get install photofilmstrip

Gimp for photo editing and graphics manipulation
sudo apt-get install gimp gimp-data gimp-data-extras gimp-gap gimp-plugin-registry libtiff-tools gimp-help-en icc-profiles glew-utils gimp-help-common gmic gimp-gmic gmic-zart libtiff-opengl

Note: Gimp Scripts [http://www.gimphelp.org/script28.shtml](http://www.gimphelp.org/script28.shtml)

Raw Therapee
sudo apt-get install rawtherapee libraw-bin ufraw ufraw-batch

Note: You can add gimp-ufraw for use with Gimp.


**Telnet, FTP, SSH, SFTP**

gFTP basic FTP client
sudo apt-get install gftp

FileZilla for FTP/SSH/SFTP
sudo apt-get install filezilla

PuTTY telnet and SSH
sudo apt-get install putty


**P2P Networking**

Azureus
sudo apt-get install azureus

Gnutella
sudo apt-get install gtk-gnutella

Frostwire from the GetDeb repository [http://www.getdeb.net/updates/Ubuntu/14.04](http://www.getdeb.net/updates/Ubuntu/14.04)
sudo apt-get install frostwire


**Multimedia Players**

Promoe
sudo apt-get install promoe

Kaffeine KDE Media Player
sudo apt-get install kaffeine

SMPlayer (excellent replacement for mplayer-gui) [http://smplayer.sourceforge.net/first-steps.php](http://smplayer.sourceforge.net/first-steps.php)
sudo apt-get install smplayer

Note: SMplayer works well in Firefox as a Windows video file alternative to totem-mozilla.

Audacious for streaming audio
sudo apt-get install audacious

Note: Audacious works well in Firefox as a Windows audio file alternative to totem-mozilla.

Gnome MPlayer
sudo apt-get install gnome-mplayer

VLC plays a wide variety of multimedia files
sudo apt-get install vlc

Amarok is a powerful music player with an intuitive interface
sudo apt-get install amarok


**Popular Multimedia Codecs and Tools**

sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer-tools libxine1-ffmpeg mencoder mpeg2dec vorbis-tools mpg321 mpg123 libflac++6 icedax lame nautilus-script-audio-convert libmad0 libjpeg-progs flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-0.7.4-dev libquicktime2

Edit MP3 and other media files
sudo apt-get install tagtool easytag id3tool id3v2

Installing libdvdcss for playing DVD's [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

Note: You may need to reboot.


**Reference**

GnomeFiles [http://gnomefiles.org](http://gnomefiles.org)
KDE-Look.org [http://kde-look.org](http://kde-look.org)
KDE-Apps.org [http://kde-apps.org](http://kde-apps.org)
NoobsLab [http://www.noobslab.com](http://www.noobslab.com)
Gnome-Look.org [http://gnome-look.org](http://gnome-look.org)
Deb-Multimedia [www.deb-multimedia.org](www.deb-multimedia.org)
OMG! Ubuntu [http://www.omgubuntu.co.uk](http://www.omgubuntu.co.uk)
Linux Compatible [http://www.linuxcompatible.org](http://www.linuxcompatible.org)
Samba [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
Trusty Wiki [http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty)
Wordnet [http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)
Ubuntu Manpage Repository [http://manpages.ubuntu.com](http://manpages.ubuntu.com)
GetDeb.net V2 [http://www.getdeb.net/updates/Ubuntu/14.04](http://www.getdeb.net/updates/Ubuntu/14.04)
Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)
Linux Command Directory [http://www.oreillynet.com/linux/cmd](http://www.oreillynet.com/linux/cmd)
Chmod Calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)
UbuntuGNOME [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/UbuntuGNOME](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/UbuntuGNOME)
Linux Commands - Practical Reference [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
Ultimate guide to Linux [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
Gnome / KDE Keyboard Shortcuts [http://www.novell.com/coolsolutions/tip/2289.html](http://www.novell.com/coolsolutions/tip/2289.html)



**HP Linux Imaging and Printing** [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

**TeamViewer** is one of the best remote support tools available (I recommend the 32/64bit Multiarch version) [http://www.teamviewer.com](http://www.teamviewer.com)


**Adding a Personal Package Archive (PPA) to your Ubuntu repositories**

sudo add-apt-repository ppa:<ppa name>
sudo apt-get update

You're now ready to install software from the PPA using sudo apt-get install <ppa name> or sudo apt-get upgrade.

Note: This is not an endorsement of any PPAs. Make sure you trust the PPA owner before installing their software.

Removing a Personal Package Archive (PPA) from your Ubuntu repositories
sudo apt-get install ppa-purge
sudo ppa-purge ppa:<ppa name>


Ubuntu Tweak is a powerful tool (use with caution)
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

Note: I only use Ubuntu Tweak to remove old install files with the janitor cleanup function.

Audacity is an Awesome Multi-track Audio Editor
sudo add-apt-repository ppa:audacity-team/daily
sudo apt-get update
sudo apt-get install audacity lame libmp3lame0

FFMpeg is a cross-platform solution to record, convert and stream audio and video.
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg

Blender for 3D Modeling and Rendering
sudo add-apt-repository ppa:irie/blender
sudo apt-get update
sudo apt-get install blender

OpenShot video editing
sudo add-apt-repository ppa:openshot.developers/ppa (remove the space after the colon)
sudo apt-get update
sudo apt-get install openshot frei0r-plugins

GNU Emacs text editor
sudo add-apt-repository ppa:cassou/emacs
sudo apt-get update
sudo apt-get install emacs24 emacs24-el emacs24-common-non-dfsg

Cinnamon Desktop
sudo add-apt-repository ppa:tsvetko.tsvetkov/cinnamon
sudo apt-get update
sudo apt-get install cinnamon

Oracle Java 7
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

Note: OpenJDK and the IceTea plugin may conflict with this installation, consider using one or the other.

LibreOffice
sudo add-apt-repository ppa:libreoffice/libreoffice-4-3
sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get install libreoffice libreoffice-java-common libreoffice-math libreoffice-gnome libreoffice-java-common libreoffice-pdfimport

ttf-mscorefonts-installer for popular fonts to be used with LibraOffice Writer (included with another well known editor)
sudo apt-get install ttf-mscorefonts-installer

Note: Be sure to accept the eula agreement (this often shows up behind the active window when installing from the Ubuntu Software Center).

Setting Default Page Margins in LibreOffice Writer

Launch LibreOffice Writer and select Page from the Format menu. Click on the Page tab and adjust the margins as desired (another well known editor uses 1" as the standard), click Apply then OK. From the File Menu select Save As Template, click on My Templates followed by the Save button. Name the template (I use Default) and click OK. If the template doesn't display in My Templates select Refresh from the menu that looks like a gear at the right. Now double-click on My Templates, highlight the template you created and click the "Set as default" button at the top (the gear menu at the right will let you reset this if needed).


**Microsoft Office Official Web Apps** (a necessary evil for some folks)
[https://docs.google.com/file/d/0ByQnaVw7riBQMjNCUFh4ZlM4Y0E/edit?usp=sharing](https://docs.google.com/file/d/0ByQnaVw7riBQMjNCUFh4ZlM4Y0E/edit?usp=sharing)


**Ubuntu Wallpaper**
sudo apt-get install ubuntu-wallpapers-trusty ubuntu-wallpapers-saucy ubuntu-wallpapers-raring ubuntu-wallpapers-quantal ubuntu-wallpapers-precise ubuntu-wallpapers-oneiric ubuntu-wallpapers-natty ubuntu-wallpapers-maverick ubuntu-wallpapers-lucid ubuntu-wallpapers-karmic gutsy-wallpapers feisty-wallpapers edgy-wallpapers


**Screensavers** (they used to include these)
sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
Now go to Startup Applications and add the following:
Name: xscreensaver
Command: xscreensaver –nosplash


**Chat Clients**

XChat is an IRC chat program that allows for multiple IRC channels (chat rooms) at the same time
sudo apt-get install xchat

Kopete is an instant messenger client supporting AIM, ICQ, Live Messenger, Yahoo, Jabber, and more
sudo apt-get install kopete

Pidgin is an easy to use and free chat client to connect to AIM, MSN, Yahoo, and more chat networks all at once
sudo apt-get install pidgin


**Productivity Applications**

Dia is similar to Microsoft® Visio
sudo apt-get install dia

Scribus is a desktop publishing application
sudo apt-get install scribus

Gnome Planner for Gantt charts and project plans
sudo apt-get install planner

OpenProj is a desktop replacement of Microsoft Project [http://sourceforge.net/projects/openproj/files/](http://sourceforge.net/projects/openproj/files/)

GanttProject is a tool for creating a project schedule with Gantt and resource load charts [http://ganttproject.biz/download](http://ganttproject.biz/download)


**Development Applications**

Meld is a visual diff and merge tool
sudo apt-get install meld

Alternative shells for Linux...
C, K, T, Z & Fish shells
sudo apt-get install csh ksh tcsh zsh fish

GEdit
sudo apt-get install gedit gedit-plugins gedit-developer-plugins

Note: GEdit Wiki [https://wiki.gnome.org/Apps/Gedit](https://wiki.gnome.org/Apps/Gedit)

OpenJDK
sudo apt-get install openjdk-7-jdk openjdk-7-jre icedtea-7-plugin

jEdit is a java based full featured editor (make sure you have Sun JRE installed)
sudo apt-get install jedit

BlueGriffon WYSIWYG Editor from the GetDeb repository [http://www.getdeb.net/updates/Ubuntu/14.04](http://www.getdeb.net/updates/Ubuntu/14.04)
sudo apt-get install bluegriffon

Essentials for Compiling from Source
sudo apt-get install build-essential checkinstall cdbs devscripts dh-make fakeroot libxml-parser-perl check

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages
sudo apt-get install geany

Vim, Gvim, and Cream may come in handy for file editing
sudo apt-get install vim-gnome vim-doc vim-scripts vim-gui-common vim-runtime cscope tclreadline cream

Bluefish is an editor for experienced web designers and programmers supporting many programming and markup languages
sudo apt-get install bluefish


**Known Issues**

Disable Apport at Boot to turn off error reporting 
sudo gedit /etc/default/apport
Change enabled=1 to enabled=0 save the file and close.


If Firefox windows open off screen or are too large to use, you may need to reset Firefox's controls and toolbars.

1. Close down Firefox completely: On the Firefox window, click the File menu then select Exit.
2. From a terminal window type: firefox -safe-mode
3. Firefox should start up with a Firefox Safe Mode dialog with options.
4. Check mark Reset toolbars and controls.
5. Click Make Changes and Restart to restart Firefox


Add Missing Privacy Settings in Ubuntu Gnome Desktop
sudo apt-get install activity-log-manager-control-center

Note: Activity Log Manager will show up under Accessories or by doing a search for the application.


All Startup Applications are not visible
cd /etc/xdg/autostart
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

Reverse changes...
sudo sed --in-place 's/NoDisplay=false/NoDisplay=true/g' *.desktop


The Tahoma font included with ttf-mscorefonts-installer doesn't install as expected (thank you Richard Neill for providing this fix).

Using gedit copy the script below and paste into a text file. Save the file as tahoma in your home directory, right click on the file and choose properties, under the permissions tab make the file executable and then run it from a terminal window by typing sudo ./tahoma 

echo "Installing Tahoma font"
cd /tmp
which cabextract >/dev/null || apt-get -y install cabextract
[ ! -f /usr/share/fonts/truetype/msttcorefonts/tahoma.ttf -o ! -f /usr/share/fonts/truetype/msttcorefonts/tahomabd.ttf ] &&
wget [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB) &&
cabextract -F 'tahoma*ttf' IELPKTH.CAB &&
mkdir -p /usr/share/fonts/truetype/msttcorefonts/ &&
mv -f tahoma*ttf /usr/share/fonts/truetype/msttcorefonts/  &&
chmod 644 /usr/share/fonts/truetype/msttcorefonts/tahoma*  &&
fc-cache && rm -f IELPKTH.CAB && echo "Installed Tahoma"
cd -


**Useful Commands**

Searching for Packages: sudo apt-cache search some_string
Show Package Info: sudo apt-cache showpkg xxx
Show Package Dependencies: sudo apt-cache depends xxx
Install: sudo apt-get install xxx
Re-Install: sudo apt-get --reinstall install xxx
Remove: sudo apt-get remove xxx
Remove All (configs too): sudo apt-get remove --purge xxx
Upgrade: sudo apt-get -u upgrade
Show Upgrades: sudo apt-show-versions -u
Show All Installed Packages: dpkg --list
Find Package by File Name: sudo apt-file search /bin/ping
Find filenames in a Package: sudo apt-file list xxx
Updating the apt-file Cache: sudo apt-file update
Info on Installed Package: aptitude show xxx
System Hardware Info: sudo lshw > hardware.txt
Clear bash history cat /dev/null > ~/.bash_history && history -c && exit

Clean up your system and free up space with sudo apt-get clean and sudo apt-get autoremove

If you're curious (like me) or have the need to know uname -a && cat /etc/*release in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.

More to come...

Friends,

I'm more than willing to include your favorite applications (this is your post as much as mine). I do ask that you keep the description brief and on a general level with the degree of difficulty at a minimum (for new users) when making recommendations. I started posting "Ubuntu Desktop Computing Made Easy" a while back (mainly out of frustration) while trying to get my computer to perform as expected without hours of setup, search and configuration. The primary goal of this post is to make it "easy" for anyone to setup an Ubuntu Desktop Computer with everything they need or want within a short period of time ensuring the overall experience is an enjoyable one.

Note: This post can be found on Google by searching for Ubuntu Desktop Computing Made Easy. If you would like to link to this post or publish it elsewhere please give credit where credit is due.

Kind regards,

TrakerJon

---

### Post by TheFu on 2014-08-08
Nice.

Other options for learning: 
* [http://ubuntuguide.org/](http://ubuntuguide.org/)
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) - is for Windows people moving to Linux

I'd suggest that there is NO NEED to pick a distro based only on the GUI installed. Swapping a GUI is really easy on Ubuntu ... or almost any Linux. There must be 30 different choices for a GUI on Linux, probably more.  **The GUI is NOT the OS.** The 2nd link above explains nicely why that is.

Be cautious running GUI programs with sudo.  Programs that store preferences might save them as root in your personal HOME directory.  Understanding file permissions and remembering that Linux is multiuser is very important.

---

### Post by TrakerJon on 2014-08-08
Added the links...noticed a couple that needed updating, thanks!

TrakerJon

---

