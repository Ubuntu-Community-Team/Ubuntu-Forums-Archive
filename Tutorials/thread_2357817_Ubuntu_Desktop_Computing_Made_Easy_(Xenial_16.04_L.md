---
title: "Ubuntu Desktop Computing Made Easy (Xenial 16.04 LTS)"
date: 2017-04-06
forum: Tutorials
---

### Post by TrakerJon on 2017-04-06
**Ubuntu Desktop Computing Made Easy (Xenial 16.04 LTS)**

Kubuntu Desktop [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)
Ubuntu Gnome Desktop [http://ubuntugnome.org/download](http://ubuntugnome.org/download)
Ubuntu Desktop [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

It's been a good while since my last forum post and there have been some interesting developments...let's get started.

First, download your chosen flavor of Ubuntu, burn the .iso file to a blank disk, and install it on a designated computer. If you check the box to include 3rd party software during the installation this will give you some of the multimedia codecs available but you'll most likely need more (listed below). Please keep in mind that if you intend to dual boot with Windows you will encounter some challenges. I've had the best results simply installing Ubuntu and only the software needed for daily use (including security software and browser Add-ons). The more physical RAM the better and graphics memory is a plus as well...hard drive size can be whatever is available but I suggest starting with at least 20Gb.

The official installation recommendation can be found here: [https://help.ubuntu.com/community/Installation/SystemRequirements#Recommended_Minimum_System_Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Recommended_Minimum_System_Requirements")

Next, update the operating system by searching for Software & Updates and launching the application. Under the Other Software tab check the first box for Canonical Partners, click close, and reload when prompted. Once the changes have been made launch the Software Updater and install all available updates. After rebooting, in Software & Updates under the Additional Drivers tab, enable the appropriate one(s) for your system (if desired). Some of the available drivers can produce unwanted results when installing them (if in doubt ask or search on the Ubuntu Forum). Note: If you're installing Ubuntu within a virtual machine 3D Acceleration can cause application issues.

The majority of these applications are referenced being installed from a terminal window so that the overall process can be seen. Keep in mind, even though applications are installed with sudo, launching them with sudo can have unintended consequences. It's typically advised to launch them from the application icon or by typing the application name only from a command line prompt in a terminal window...enjoy! 

**Gnome Users**

Visit [https://extensions.gnome.org](https://extensions.gnome.org) and install the browser extension referenced at the top of the page and the extensions repository: 
sudo apt-get install chrome-gnome-shell

The following Gnome Shell extensions I find extremely helpful... 
Applications Menu, Places Status Indicator, User Themes, Window List, Workspace Indicator, OpenWeather, and Extentions 

**Email Clients**

Geary
sudo apt-get install geary

Thunderbird
sudo apt-get install thunderbird 

Claws
sudo apt install claws-mail claws-mail-tools

**Tools and Utilities**

Gdebi Package Installer
sudo apt-get install gdebi

Synaptic Package Manager
sudo apt-get install synaptic

Cups-PDF for printing to PDF files
sudo apt-get install cups-pdf

Manage Users and Groups
sudo apt-get install gnome-system-tools

Parcellite lightweight GTK+ clipboard manager
sudo apt-get install parcellite

Smb4K Advanced Network Neighborhood Browser
sudo apt-get install smb4k

Gufw the GUI interface for Uncomplicated Firewall
sudo apt-get install gufw

Unity Tweak Tool is a settings manager for the Unity desktop
sudo apt-get install unity-tweak-tool

AceoneISO2 is a CD/DVD image manipulator (use with .iso files
sudo apt-get install acetoneiso

Adaptive Readahead Daemon for faster application startup times
sudo apt-get install preload

Htop, SysInfo and HardInfo for system information and benchmarking
sudo apt-get install htop sysinfo hardinfo

RecordMyDesktop to record programs and games
sudo apt-get install recordmydesktop

File Compression and Extraction
sudo apt-get install ark unace rar unrar p7zip-rar p7zip zip unzip sharutils uudeview mpack arj cabextract file-roller

Note: Use Archive Manager or Ark for manipulating these file types

HP Linux Imaging and Printing [http://hplipopensource.com/hplip-web/install_wizard/index.html]("http://hplipopensource.com/hplip-web/install_wizard/index.html")

Protect your privacy, defend yourself against network surveillance and traffic analysis [https://www.torproject.org]("https://www.torproject.org/")

VPN One Click offers a secure connection to the internet away from the prying eyes of your provider [https://www.vpnoneclick.com]("https://www.vpnoneclick.com/")

TeamViewer is one of the best remote support tools available (get the 32/64bit Multiarch version) [https://www.teamviewer.com/en/download/linux]("https://www.teamviewer.com/en/download/linux/")

**Graphics Editors**

Pinta is a lot like MS Paint
sudo apt-get install pinta

Inkscape vector graphics editor
sudo apt-get install inkscape

Krita is a powerful painting and image editing program
sudo apt-get install krita

Pixlr Editor offers a host of powerful image editing features from any computer with an internet connection [https://pixlr.com/editor](https://pixlr.com/editor)

Gimp for photo editing and graphics manipulation
sudo apt-get install gimp gimp-data gimp-data-extras gimp-gap gimp-plugin-registry libtiff-tools gimp-help-en icc-profiles glew-utils gimp-help-common gmic gimp-gmic gmic-zart libtiff-opengl

**Multimedia Tools**

Openshot for video editing
sudo apt-get install openshot

PhotoFilmStrip
sudo apt-get install photofilmstrip

Flowblade is also a nice movie editor
sudo apt-get install flowblade

Darktable photo workflow application
sudo apt-get install darktable

Kdenlive KDE Non-Linear Video Editor
sudo apt-get install kdenlive

Blender is a versatile 3D creation application
sudo apt-get install blender

Audacity is an Awesome Multi-track Audio Editor
sudo apt-get install audacity lame libmp3lame0

digiKam manages your photos like a professional
sudo apt-get install digikam

Transmageddon converts most multimedia formats
sudo apt-get install transmageddon

Commonly used media codecs and fonts for Ubuntu
sudo apt-get install ubuntu-restricted-extras

Note: Choose "Yes" to the EULA

WinFF will convert most any video file that FFmpeg will convert
sudo apt-get install winff 

K3b is a full-featured CD/DVD/Blu-ray burning and ripping application
sudo apt-get install k3b

Shutter for screen captures (VirtualBox users disable 3D Acceleration or your captures could be all in black)
sudo apt-get install shutter

XnView MP cross-platform media browser, viewer and converter [http://www.xnview.com/en/xnviewmp/#downloads]("http://www.xnview.com/en/xnviewmp/#downloads")

**Antivirus**

ClamAV
sudo apt-get install clamav clamtk

Operations available from a terminal session...

Update virus definitions: sudo freshclam
Scan files in your home directory: sudo clamscan
Scan files in an entire directory: sudo clamscan -r /<directory name>
Scan on the entire drive: sudo clamscan -r /

Update Clamtk and get Addons [https://dave-theunsub.github.io/clamtk]("https://dave-theunsub.github.io/clamtk/")
Sourceforge [https://sourceforge.net/projects/clamtk]("https://sourceforge.net/projects/clamtk/")

**Telnet, FTP, SSH, and SFTP**

gFTP basic FTP client
sudo apt-get install gftp

FileZilla for FTP/SSH/SFTP
sudo apt-get install filezilla

PuTTY telnet and SSH
sudo apt-get install putty

**Multimedia Players**

Kaffeine KDE Media Player
sudo apt-get install kaffeine

Audacious for streaming audio
sudo apt-get install audacious

Gnome MPlayer
sudo apt-get install gnome-mplayer

VLC plays a wide variety of multimedia files
sudo apt-get install vlc

Amarok is a powerful music player with an intuitive interface
sudo apt-get install amarok

The full install of Adobe Flash Player can be acquired at [https://get.adobe.com/flashplayer]("https://get.adobe.com/flashplayer/")

Note: Choose "Yes" when prompted to allow the additional resources

SMPlayer (excellent replacement for mplayer-gui) [http://smplayer.sourceforge.net/first-steps.php](http://smplayer.sourceforge.net/first-steps.php)
sudo apt-get install smplayer

**Spotify for Linux**

Add the Spotify repository signing key to be able to verify downloaded packages
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886

Add the Spotify Repository
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt-get update
sudo apt-get install spotify-client

**Chat Clients**

Sky Linux (Lync and Skype for Business) [https://tel.red/linux.php]("https://tel.red/linux.php")

Kopete is an instant messenger client supporting AIM, ICQ, Live Messenger, Yahoo, Jabber, and more
sudo apt-get install kopete

XChat Gnome is an IRC chat program that allows for multiple IRC channels (chat rooms) at the same time
sudo apt-get install xchat-gnome

Pidgin is an easy to use and free chat client to connect to AIM, MSN, Yahoo, and more chat networks all at once
sudo apt-get install pidgin

**Office and Productivity**

Okular PDF Viewer
sudo apt-get install okular

Dia is similar to Microsoft® Visio
sudo apt-get install dia

Scribus is a desktop publishing application
sudo apt-get install scribus

Gnome Planner for Gantt charts and project plans
sudo apt-get install planner

LibreOffice
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get install libreoffice libreoffice-java-common libreoffice-math libreoffice-gnome libreoffice-java-common libreoffice-pdfimport

OpenProj is a desktop alternative to Microsoft Project® [http://sourceforge.net/projects/openproj/files]("http://sourceforge.net/projects/openproj/files/")

**Development Applications**

Meld is a visual diff and merge tool
sudo apt-get install meld

Alternative shells for Linux...
C, K, T, Z & Fish shells
sudo apt-get install csh ksh tcsh zsh fish

GEdit
sudo apt-get install gedit gedit-plugins gedit-developer-plugins

Note: GEdit Wiki [https://wiki.gnome.org/Apps/Gedit](https://wiki.gnome.org/Apps/Gedit)

Eclipse
[https://howto-ubuntunew.blogspot.com/2016/09/how-to-install-eclipse-ide-on-ubuntu.html]("https://howto-ubuntunew.blogspot.com/2016/09/how-to-install-eclipse-ide-on-ubuntu.html")

GNU Emacs text editor
sudo add-apt-repository ppa:cassou/emacs
sudo apt-get update
sudo apt-get install emacs24 emacs24-el emacs24-common-non-dfsg

jEdit is a java based full featured editor (make sure you have Sun JRE installed)
sudo apt-get install jedit

Essentials for Compiling from Source
sudo apt-get install build-essential checkinstall cdbs devscripts dh-make fakeroot libxml-parser-perl check

Geany is a fast and lightweight IDE (Integrated Development Environment) for programming in various languages
sudo apt-get install geany

Vim, Gvim, and Cream may come in handy for file editing
sudo apt-get install vim-gnome vim-doc vim-scripts vim-gui-common vim-runtime cscope tclreadline cream

BlueGriffon WYSIWYG Editor from the GetDeb repository [http://www.getdeb.net/updates/Ubuntu/16.04/?q=bluegriffon](http://www.getdeb.net/updates/Ubuntu/16.04/?q=bluegriffon)
sudo apt-get install bluegriffon

Bluefish is an editor for experienced web designers and programmers supporting many programming and markup languages
sudo apt-get install bluefish

**Ubuntu Wallpaper**
sudo apt-get install ubuntu-wallpapers-xenial ubuntu-wallpapers-wily ubuntu-wallpapers-vivid ubuntu-wallpapers-utopic ubuntu-wallpapers-trusty ubuntu-wallpapers-saucy ubuntu-wallpapers-raring ubuntu-wallpapers-quantal ubuntu-wallpapers-precise ubuntu-wallpapers-oneiric ubuntu-wallpapers-natty ubuntu-wallpapers-maverick ubuntu-wallpapers-lucid ubuntu-wallpapers-karmic gutsy-wallpapers feisty-wallpapers edgy-wallpapers

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


If you installed the Kubuntu Desktop (sudo apt-get install kubuntu-desktop) and the cursor in Gnome won't change back to the default.
sudo update-alternatives --config x-cursor-theme

Note: There will be several choices (/usr/share/icons/default/index.theme). Selecting one with a manual mode worked for me.

nVidia graphics drivers can cause a (black screen) problem after installing the Kubuntu desktop as well. Removing them and restarting will help you troubleshoot.
sudo apt-get remove --purge nvidia-*


**Browser Security**

I recommend installing the following Add-ons to Firefox or Chromium and setting your default search engine to DuckDuckGo.
Disconnect, Adblock Plus and HTTPS Everywhere

**Reference**

NoobsLab [http://www.noobslab.com](http://www.noobslab.com)
Gnome-Look.org [http://gnome-look.org](http://gnome-look.org)
Deb-Multimedia [www.deb-multimedia.org](www.deb-multimedia.org)
OMG! Ubuntu [http://www.omgubuntu.co.uk](http://www.omgubuntu.co.uk)
Linux Compatible [http://www.linuxcompatible.org](http://www.linuxcompatible.org)
Samba [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
Trusty Wiki [http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty)
Wordnet [http://wordnetweb.princeton.edu/perl/webwn](http://wordnetweb.princeton.edu/perl/webwn)
Ubuntu Manpage Repository [http://manpages.ubuntu.com](http://manpages.ubuntu.com)
GetDeb.net V2 [http://www.getdeb.net/updates/Ubuntu/16.04](http://www.getdeb.net/updates/Ubuntu/16.04)
Ubuntu PPA Search [https://edge.launchpad.net/ubuntu/+ppas](https://edge.launchpad.net/ubuntu/+ppas)
UbuntuFree.com [https://www.ubuntufree.com/apps-for-ubuntu/](https://www.ubuntufree.com/apps-for-ubuntu/)
Linux Command Directory [http://www.oreillynet.com/linux/cmd](http://www.oreillynet.com/linux/cmd)
Chmod Calculator [http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)
Ubuntu Release Notes [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
Linux Commands - Practical Reference [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
Bash Reference Manual [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
Ultimate guide to Linux [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
Gnome / KDE Keyboard Shortcuts [http://www.novell.com/coolsolutions/tip/2289.html](http://www.novell.com/coolsolutions/tip/2289.html)

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

Clean up your system and free up space with sudo apt-get clean && sudo apt-get autoremove

If you're curious (like me) or have the need to know uname -a && cat /etc/*release in a terminal window will tell you the kernel version and release date, the distro id/release/codename/description.

If you were already running Ubuntu 16.04 LTS and have installed all available security patches, bug fixes, and app updates then you&#8217;re now running Ubuntu 16.04.2 LTS or higher. However, in some cases, for the hardware support improvements of the Linux Kernel 4.8 and the associated benefits you&#8217;ll need the following update to receive them. You&#8217;ll also be able to upgrade to newer versions of the stack as they&#8217;re released (every 6 months until Ubuntu 16.04.5).

sudo apt install --install-recommends xserver-xorg-hwe-16.04


More to come...

Friends,

I'm more than willing to include your favorite applications and programs (this is your post as much as mine). I do ask that you keep the description brief and on a general level with the degree of difficulty at a minimum when making recommendations (mainly for new users). I started posting "Ubuntu Desktop Computing Made Easy" a while back (mostly out of frustration) while trying to get my computer to perform as expected without hours of setup, search and configuration. The primary goal of this post is to "make it easy" for anyone to setup an Ubuntu Desktop Computer with everything they need within a short period of time ensuring their overall experience is an enjoyable one.

Note: This post can be found on Google by searching for Ubuntu Desktop Computing Made Easy. If you would like to link to this post or publish it elsewhere please give credit where credit is due.

Kind regards,

TrakerJon

---

### Post by TheFu on 2017-04-06
Mostly good, but a few dangerous things - **don't use sudo with any GUI program**. It can have unintended repercussions. I've seen where someone wasn't able to run any gnome programs because they used sudo with some GUI program on their first login causing the ~/.config/ directory to be owned by root, preventing any other GUI program from creating settings/subdirs under there.

---

### Post by TrakerJon on 2017-04-07
Noted, thanks for the comment. 

Cheers,

Traker

---

### Post by TheFu on 2017-04-07
> sudo gedit /etc/default/apport
instead, use 
```
 sudoedit /etc/default/apport
```
sudoedit never runs any editor as root - but as the normal userid. Only the copy-out and copy-back use elevated privileges.  It honors the EDITOR environment variable, so it works correctly on both servers and desktops.

Using sudo -H /path/to/gui-program is another option.  The GUI version of sudo (different on different DEs) is on the way out, soon to be deprecated, but for now, it is an option. gks.... something. I don't use it.

---

### Post by TrakerJon on 2017-04-07
Good eye but we may need to include a tutorial on how to use sudoedit ;)

Cheers,

Traker

---

