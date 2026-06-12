---
title: "My adventures on linux"
date: 2016-05-21
forum: The Cafe
---

### Post by kwanbis on 2016-05-21
**GOODBYE WINDOWS: ADVENTURES ON LINUX**

NOTE: I CONSIDER MYSELF SSR BEGINNER IN LINUX, SO I ACCEPT SUGGESTIONS FOR IMPROVEMENT, CHANGES OR FIXES!

[HR][/HR]
**INTRODUCTION**

I&#8217;ve been mostly a Windows since Windows 95 till Windows 10. And I consider myself a highly advanced at that.

I have also used other OSes: DOS, OS/2, AIX and even from time to time, Linux itself and OSX. But the constant abusive practices by Microsoft where enough for me so I decided to finally move to Linux.

And this is my tale of the experience, with the hope that it help others, and maybe even helps the community understand issues that people coming from Windows might encounter.

Finally, I would like to add that this is wrote from the point of view of a Windows user that is trying to migrate to Linux. Not from the point of view of a seasoned Linux user, and so I would try to be as less technical as possible.

[HR][/HR]
**CHOOSING A DISTRO**

Unless you are a highly advanced user and are planning on rolling your own distribution of Linux, using Linux usually means choosing a distro.

There many distros to choose from, being the most populars: Debian/Ubuntu/Mint and RedHat/Fedora/CentOS.

In my case, I choose Ubuntu, as it has one of the most active and helpful communities and it has a very good release cycle. In fact, I choose Ubuntu 16.04, which is a LTS (long term release) version, which means it would be supported for 5 years.

[HR][/HR]
**INSTALLING UBUNTU**

Installation is very simple. You only boot from a USB or CD drive, and you have the option to install or try it, so I choose install it. And for normal users that should be it.

But in my case, after installing Ubuntu it wouldn&#8217;t boot. The problem was that I have a HDD on my ThinkPad T520, that is the original hard drive, and where there was a CD, I now have second drive, an SSD, to which I installed Ubuntu.

So even though I installed Ubuntu to the SSD drive, which is the &#8220;second&#8221; physical drive, GRUB is copied to the &#8220;first&#8221; physical drive, the hard drive. 

Anyway, I fixed it by first running lsblk in the terminal to see which disk (sda or sdb) Ubuntu was installed on, and then I runned:

sudo grub-install /dev/sdb
sudo update-grub

And all was fine.

[HR][/HR]
**CHOOSING A GUI (DESKTOP MANAGER)**

In Linux there are many GUIs or Desktop Managers (DMs), being the most populars: Unity, Cinnamon, KDE, GNOME2, GNOME3, MATE, LXDE and Xfce.

You can install Ubuntu and then add one or all DMs or you can download a Ubuntu flavor. For example, Kubuntu is the Ubuntu flavor that comes with KDE installed by default instead of Unity. Or there is Ubuntu MATE, which comes with MATE installed by default instead of Unity.

For me, the best thing was to install normal Ubuntu, which uses Unity, and then add Cinnamon.

[HR][/HR]
**UNITY**

Unity is the Linux version of the OSX interface. I like it but with some caveats:

The launcher vertically to the left makes no sense to me. I moved it to the bottom.
The launcher is too big. I made the launcher smaller (33).
I made the the menus to show on the windows title bar and always visible.

With all those three changes, the launcher looks much better, much more OSX like.

But there is a fourth issue I wasn&#8217;t able to resolve: The launcher is too rigid, too dead. It has no life like the OSX dock.

[HR][/HR]
**CINNAMON**

Cinnamon is the Linux version of the Windows interface. An I LOVE it. I&#8217;m using it right now. It is so logical to me that I don&#8217;t miss the Windows interface at all. It is even better than Windows 8 and 10 Start menu.

To add Cinnamon to 16.04 you just open a terminal and type:

sudo add-apt-repository ppa:embrosyn/cinnamon
sudo apt-get update
sudo apt-get install cinnamon cinnamon-core

After that, when login in, we can select which desktop manager to use, Unity or Cinnamon, just by clicking on a small button near our username.

[HR][/HR]
**COOLNESS FACTOR**

Using Linux feels oh sooooooooo soooooooo sooooooooo cool.

It is incredible to stare at the creation of thousands and thousands of hackers while at the same time realising that all of that is free software.

Also the &#8220;freedom&#8221; of choice you experiment on Linux, is unparalleled in any other OS, with the exception probably of the *BSDs.

[HR][/HR]
**CUSTOMIZING CINNAMON**
Although what I'm about to tell is totally optional, it helped me be more comfortable with Ubuntu.

In Cinnamon, you can right click on the "start menu" button, and select "Configure".

There I was able to change the accelerator combination to Control-ESC just like the Windows one, and deleted the deactivation one. So now I can Control-ESC to show the menu, and ESC to close it.

Also, the fonts and with of the menu is too small for me. To change it I had to open one config file with the command:

sudo gedit /usr/share/cinnamon/theme/cinnamon.css

There I searched for the following text and I changed the font size to 10pt and the height to 28px.

```
#panel {
	color: #ffffff;
	background-color: #555555;
	font-size: 10pt;
	font-weight: normal;
	height: 28px;
}

```

After saving and restarting, all was nicer for me!

[HR][/HR]
**LINUX "REGISTRY"**
One very important difference between Linux and Windows is that in Windows, you have "the registry", a special database where all the configuration options are written and read from.

In Linux, there is not such a thing. Everything is done in text files, like the one I for Cinnamon config.

This is much simpler and I like it better.

[HR][/HR]
**SOFTWARE INSTALLATION**

Any operating system is basically useless without software. And even though Ubuntu comes with a broad selection of preinstalled apps, LibreOffice and Firefox, one of the first things you would like to do is install software.

Ubuntu provides thouthands of software packages all easily installable through &#8220;Ubuntu Software&#8221;. All those applications reside, and are maintained, on Ubuntu (Cannonical) servers, on what is called the (official) repositories (or just repos).

Repositories are folders residing on servers which hold one or more application packages. That way, you can just tell Ubuntu to connect to a repository and install a specific package without you first having to have the .deb file on your machine.

Ubuntu provides four official repositories:

MAIN: Canonical-supported free and open-source software.
UNIVERSE: Community-maintained free and open-source software.
RESTRICTED: Proprietary drivers for devices.
MULTIVERSE: Software restricted by copyright or legal issues.

To enable all or any of them, you can use the application &#8220;Software & Updates&#8221; and select one or more of the repositories. So, once you have the repositories added, Software & Updates would ask you if you want to reload the information. Say yes.

Once that is done, you can use the Ubuntu Software application to search and install more applications just by selecting them and choosing install. Now, if the selection is not enough, you can even use Ubuntu Software to install the old Ubuntu Software Center which appears to have more apps.

Just search for Ubuntu Software Center and it should appear with the option to install it. Once installed it, you can use it to search and install more apps. And if you need more apps, you can install another application called Synaptic Package Manager, that would allow you to install even more apps.

If you are feeling a little overwhelm, please don&#8217;t. Just think of Ubuntu Software, Ubuntu Software Center and Synaptic as application markets like Google&#8217;s Play Store, Apple&#8217;s App Store, etc. As you can see, Linux is all about choice and freedom.

Now, what happens if you want to use one application that is not listed on the official repositories? Well, you can add unofficial repositories to your machine, and install such apps from there!

To do so, you need to know the repository URL and add it to your machine&#8217;s repo list by using the &#8220;Software & Updates&#8221; app. Under the other repositories tab, you just add the URL of the repo, close the app, at which point it would ask you to update information about available software.

Once that is done, Ubuntu Software, Ubuntu Software Center and Synaptic would have additional software to install, including the one you wanted!

Now, you might think, if I have to add the respo information, why don&#8217;t I just go to a website to download the software and install it like it is done in Windows? What is the advantage of the repos?

The main advantage of the repos is that for all the software installed through repos, Ubuntu can check for updates and tell you whenever there is a new version available. Just like Microsoft does with Windows Update, you can do for your whole system.

Now, one warning with unofficial repos. You have to be sure that the unofficial repo you are adding is a safe one, and that it is not a malicious one. Just like you have to make sure when you download any software from the internet to install in Windows.

[HR][/HR]
**REPO MANAGEMENT THROUGH COMMAND LINE**

As you would probably notice, hackers love to type. Typing allows you to easily automate things so you would see a lot of instructions to install software through the command line.

For example, to enable the official repos, you can use this four commands on a terminal window:

sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository restricted
sudo add-apt-repository multiverse

After that, you need to tell Ubuntu to update the new information by using:

sudo apt-get update
sudo apt-get upgrade

so that all the information on available packages from the newly enabled repositories gets updated.

To install software from the repositories through the command line, you can run a command with the form:

sudo apt-get package_name.

For example, to install GNOME3 from the official repo, you just type:

sudo apt-get install ubuntu-gnome-desktop

That line tells apt-get to install the gnome desktop. It is called with sudo so that it gets admin rights.

To add a repository to the system you run a command like this:

sudo add-apt-repository respository_url

For example, to install MATE Desktop Environment, you just type:

sudo add-apt-repository [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu)
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mate-dock-applet

The first commands adds the repository to the ones available on the system.
The second command reads all available packages from all the repositories on the system, including the one just added on the previous command.
The third command upgrades the system with the list of packages.
The fourd command installs MATE.

Anyway, I don&#8217;t want to complicate things much more, but there is also a special type of repository, called the PPA. A PPA is just a repository hosted on Launchpad servers. For all intent and purposes, the only difference is how you add them to your repositories list.

Let's assume that I want to install Cinnamon on my machine. This is contained in the official repositories but there is also a PPA maintained by the original developers that&#8217;s useful, for instance, if you're interested in getting new releases quicker. To add the PPA I would type:

sudo add-apt-repository ppa:embrosyn/cinnamon
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install cinnamon cinnamon-core

The first commands adds the PPA repository to the ones available on the system.
The second command reads all available packages from all the repositories on the system, including the one just added on the previous command.
The third command upgrades the system with the list of packages.
The fourd command installs CINNAMON.

[HR][/HR]
**INSTALLING FROM FILES**

Now, it appears that the only way to install something in Linux is by using repositories. Nothing further from the truth.

In Windows you can to install an application by means of a special file, an installer. Installers are either especial .EXE files or .MSI files that takes care of copying the required files to one or more folders in your hard drive, creating icons, etc.

In Ubuntu, to install an application you can also use an installer. Installers in Ubuntu are files with either an .SH or .DEB extension (actually I believe there are more options, but those are the most common ones as far as I understand). The installer again takes care of copying the required files to one or more folders, creating icons, etc. Think of .SH/.DEB files as the .EXE/.MSI of the Linux world.

To install using a .DEB file, you simply download it, and then double click on it, and it should open one of the many install managers.

Or you can use the command:

sudo apt install ./deb_file_name

For example, let's say I want to install Google Chrome.

You first go to the website and download the .DEB

You can double click the google-chrome-stable_current_amd64.deb file, or type:

cd Downloads
sudo apt install ./google-chrome-stable_current_amd64.deb

In the case of .SH files, as far as I understand the only way to do it is from the command line.

For example, to install JDownloader2, you download the file JD2Setup_x64.sh and then run:

cd Downloads
sh JD2Setup_x64.sh

And that's it. The installer application should start.

[HR][/HR]
**REPLACING WINDOWS APPS**

I use quite a bit of apps on Windows, and so I want to find the best replacement for them. The apps I use the most are: Firefox, Chrome, Chromium, Opera, Total Commander, UltraEdit, JDownloader2, Eclipse, Skype, Paint Shop Pro 7, VLC, WinRAR, Evernote, Google Drive, Flux, Microsoft Project and NOD32.

**FIREFOX**: Firefox is the default browser in Ubuntu, so there is no need to install it. But I wanted to migrate my tabs and extension to Ubuntu, so I runned it once, and then I copied my profile to my /home/user/.mozilla folder, and all was fine.

**CHROME**: Chrome is available to install from the Chrome website. Just download the .deb and install it.

**CHROMIUM**: Chromium is available on the official repos, so it was just a matter of: sudo apt install chromium-browser.

**OPERA**: Opera can also be downloaded from their official website and installed easily.

**TOTAL COMMANDER**: The best TC replacement I found is Double Commander. Easily installable through a repo.

**ULTRAEDIT**: UltraEdit is available in a .deb file so it is easy to install.

**JDOWNLOADER2**: JDownloader2 is java based, and there is a .SH installer on their website.

**SKYPE**: Skype can be installed from the 3RD PARTIES repos. It is not the best client, but it works.

**PAINT SHOP PRO 7**: For me the best version of PSP is version 7. But in linux we have GIMP, which is easily installable from the official repos.

**VLC**: VLC can be installed from the repos.

**WINRAR**: The best replacement so far is the B1 Archiver. Free and very good.

**EVERNOTE**: Evernote has no official Linux client. So I migrated myself to Simplenote, which is very similar and has a official .deb file to do the installation.

**GOOGLE DRIVE**: Sadly Google Drive has no official client. So DROPBOX for the time being. They had a very good client.

**FLUX**: Flux can be replaced by Redshift, available from the official repos.

**ECLIPSE**: Eclipse can also be installed by downloading a file.

**MICROSOFT PROJECT**: I&#8217;m running Project 2010 using WINE.

**NOD32**: That is the good thing about Linux. No need for antivirus, just common sense.

[HR][/HR]
**WINDOWS LEGACY**

As most of the users that could migrate to linux, I have NTFS partitions and drivers.

It is very cool that linux can &#8220;see&#8221; those partitions and make them available under the file manager.

Even though ubuntu shows all the NTFS partitions under the file manager, they are not &#8220;mounted&#8221; till you first open them. If Ubuntu knows and understands the NTFS partitions, why don&#8217;t we just mount them right away? Is it because of point 1? I don&#8217;t know.

[HR][/HR]
**FORMATING A HARD DRIVE**

For whatever reason, some things are very different in Linux. For example, in Windows I would just go and format a hard drive or partition, and I would own that partition.

Not so in Linux. I used Gparted to format the NTFS partition to EXT4, and after doing so, I was not able to copy files to it.

It turns out that GParted format it and gives &#8220;ownership&#8221; to the &#8220;sudo&#8221; user. So I had to run a command on the terminal to change the ownership to mine:

sudo chown -R $USER:$USER /media/kwanbis/ssdpartition

And all was fine. But as simple as the fix was, I wonder why doesn&#8217;t gparted asks me if I want to &#8220;own&#8221; the partition?

[HR][/HR]
**TRACKPOINT SETUP**

I&#8217;m running Ubuntu on a ThinkPad. ThinkPads are some of the best business laptops and they are known for the little joystick that resides between the G, H and B, and that is called the TrackPoint.

In Windows you can easily change the sensitivity and speed of the trackpoint very easily, but for some known reason to me, that is VERY complicated in linux.

I was able to change it by running a command on a terminal windows, you have to:

1) Find the device path of your trackpoint by running the following in a terminal:
find /sys/devices/platform/i8042 -name name | xargs grep -Fl TrackPoint | sed 's/\/input\/input[0-9]*\/name$//'

In my case this returns /sys/devices/platform/i8042/serio1/serio2 but if is different for you, you should use what is returned instead.

2) If you want to change the sensitivity of the trackpoint, you can try this command on a terminal window: 

echo 255 | sudo tee /sys/devices/platform/i8042/serio1/serio2/sensitivity

That command would set a sensitivity of 255, which should be the most sensible, but if it is too sensitive to you, you can start trying with numbers less than 255.

3) If you also want to change the speed of the trackpoint, you can use this command on a terminal window:

echo 100 | sudo tee /sys/devices/platform/i8042/serio1/serio2/speed

That would set a speed of 100. You can try different numbers, from 0 to 255, till you find the one you like best.

Now, you must think, this is very easy. And it is the truth. The problem is that I haven&#8217;t been able to automate all that so far, so I have to do it each time I reboot the machine.

I don&#8217;t get why such a popular line of machines, the ThinkPads, do not have a simple way of doing this. By the way, there are some DELLs and TOSHIBAs that also have trackpoint, so it would be helpful not only for LENOVOs.
 
[HR][/HR]
**RENAMING THE PC**

During the installation, you choose a user, and by default Ubuntu gives the PC a user-pc name, so in my case it was kwanbis and kwanbis-Thinkpad-T520, so in the terminal I would see something like: kwanbis@kwanbis-ThinkPad-T520, and since I wanted to have kwanbis@T520, I had to rename the PC.

In Linux, you do so by editing this two files and changing the name where it says 127.0.0.1.

gksu gedit /etc/hostname
gksu gedit /etc/hosts

Gksu calls su for graphical programs, as both files hostname and hosts are owned by su.

[HR][/HR]
**PRINTER INSTALLATION**
I have an Epson L355. At first Ubuntu told me there was no driver installed.

So, what I did was:

sudo apt-get install printer-driver-escpr

Then I opened the printers application, then the ADD button, and even though the L355 was not listed, the L455 was, so I selected that and voila!



[HR][/HR]
**ALL MY COMMANDS**

This is all the commands I type to setup Ubuntu from 0 to hero.

SAVE GRUB IN DISK B
sudo grub-install /dev/sdb
sudo update-grub

SET ALL REPOSITORIES
sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository restricted
sudo add-apt-repository multiverse

UPDATE UPGRADE
sudo apt-get update && sudo apt-get upgrade

INSTALL CINNAMON
sudo add-apt-repository ppa:embrosyn/cinnamon
sudo apt update
sudo apt-get install cinnamon

FIX LOGOUT IN CINNAMON
gsettings set org.cinnamon.desktop.session settings-daemon-uses-logind true
gsettings set org.cinnamon.desktop.session session-manager-uses-logind true
gsettings set org.cinnamon.desktop.session screensaver-uses-logind false

INSTALL NUMIX THEME
sudo apt-get install numix-gtk-theme

REBOOT
sudo reboot

INSTALL GDEBI
sudo apt-get install gdebi

INSTALL SYNAPTIC
sudo apt-get install synaptic

INSTALL CHROMIUM
sudo apt-get install chromium-browser

INSTALL VLC
sudo apt-get install vlc browser-plugin-vlc

INSTALL OKULAR (PDF VIEWER)
sudo apt-get install okular

INSTALL REDSHIFT (FLUX FOR LINUX)
sudo apt-get install redshift redshift-gtk

INSTALL SHUTTER (SCREEN CAPTURE)
sudo apt-get install shutter

INSTALL GIMP (PAINT)
sudo apt-get install gimp

INSTALL CAFFEINE
sudo apt install caffeine

INSTALL CALIBRE EBOOK READER/MANAGER
sudo apt-get install calibre

INSTALL 7ZIP COMMAND LINE
sudo apt-get install p7zip-full

INSTALL DROPBOX
sudo apt install nautilus-dropbox

INSTALL UBUNTU RESTRICTED EXTRAS
sudo apt install ubuntu-restricted-extras
sudo apt install libavcodec-extra

INSTALL ALIEN (CONVERT FROM RPM TO DEB)
sudo apt-get install alien   

INSTALL OPEN JAVA
sudo apt install icedtea-8-plugin openjdk-8-jre

INSTALL OPEN JAVA JDK
sudo apt install openjdk-8-jdk

INSTALL ORACLE JAVA
sudo add-apt-repository ppa:webupd8team/java
sudo apt update
sudo apt install oracle-java8-installer

INSTALL MAKE
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt update
sudo apt install ubuntu-make

ENABLE PARTNERS FOR SKYPE
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"

INSTALL SKYPE (LAST LINE FIXES SKYPE LOOK)
sudo apt-get install skype
sudo apt install gtk2-engines-murrine:i386 gtk2-engines-pixbuf:i386

INSTALL FFMPEG
sudo add-apt-repository ppa:djcj/hybrid
sudo apt-get update
sudo apt-get install ffmpeg

INSTALL DOUBLE COMMANDER
sudo add-apt-repository ppa:alexx2000/doublecmd
sudo apt-get update
sudo apt-get install ./doublecmd-gtk

INSTALL WINE AND PLAYONLINUX
sudo add-apt-repository -y ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.8 winetricks playonlinux

INSTALL QUPZILLA BROWSER
sudo add-apt-repository ppa:nowrep/qupzilla
sudo apt-get update
sudo apt-get install qupzilla

INSTALL SUBLIME TEXT
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer

INSTALL TOR BROWSER
sudo add-apt-repository ppa:webupd8team/tor-browser
sudo apt-get update
sudo apt-get install tor-browser

INSTALL TELEGRAM
sudo add-apt-repository ppa:atareao/telegram
sudo apt update
sudo apt install telegram

INSTALL CHROME
wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
sudo apt-get install ./google-chrome-stable_current_amd64.deb

INSTALL VIBER
wget -c [http://download.cdn.viber.com/cdn/desktop/Linux/viber.deb](http://download.cdn.viber.com/cdn/desktop/Linux/viber.deb)
sudo apt-get install ./viber.deb

INSTALL B1 ARCHIVER
Download .deb
sudo apt-get install ./b1freearchiver_current_stable_amd64.deb

INSTALL VIVALDI
Download .deb
sudo apt-get install ./vivaldi-XXXXX_amd64.deb

INSTALL SIMPLENOTE
Download .deb
sudo apt-get install ./simplenote-1.0.0.deb

INSTALL OPERA
Download .deb
sudo apt-get install ./opera-stable_37.0.2178.32_amd64.deb.deb

INSTALL MKVTOOLNIX
wget -q -O - [https://www.bunkus.org/gpg-pub-moritzbunkus.txt](https://www.bunkus.org/gpg-pub-moritzbunkus.txt) | sudo apt-key add -
sudo sh -c 'echo "deb [http://www.bunkus.org/ubuntu/xenial/](http://www.bunkus.org/ubuntu/xenial/) ./" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install mkvtoolnix mkvtoolnix-gui

INSTALL SYSTEM-WIDE UNRAR
sudo apt-get update
sudo apt-get install build-essential
(Download UnRAR source code from [http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm))
(Extract the downloaded file into a new directory)
(Open terminal and navigate to that directory)
make -f makefile lib
sudo make install-lib

INSTALL VIRTUALBOX
wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -
echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
sudo apt-get update
sudo apt-get install virtualbox-5.0

NOTE: one common question is how to resize a VDI. To do so, you need to use this command: vboxmanage modifyhd YOUR_HARD_DISK.vdi --resize SIZE_IN_MB. For example: vboxmanage modifyhd "Windows 7 x64.vdi" --resize 51200 (to make my vdi 50GB).


[HR][/HR]
**PACKAGE MANAGERS (ADVANCED TOPIC)**

Package Managers are used to automate the process of downloading, installing, upgrading, configuring, and removing applications from a computer. Ubuntu has two basic package managers: dpkg and apt.

DPKG is the base of the package management system in Ubuntu. It is used to install, remove, and provide information about .deb packages. It includes dpkg, dpkg-deb, dpkg-split, dpkg-query, dpkg-statoverride, dpkg-divert, dpkg-trigger, update-alternatives and start-stop-daemon.

In general you won&#8217;t use DPKG. Instead, you would more usually use APT.

APT is a higher level, read: easier to use, command line package manager for downloading, installing, removing, upgrading, updating and auto removing packages. If necessary, APT automatically gets and installs additional packages upon which the desired application depends on. APT uses repositories in order to find software and resolve dependencies. 

For example, if I want to install app SupperApplication, and SupperApplication needs SuperAdditionalLibrary, APT would install both without the user needing to know.

Like I said, APT is a command line tool, meaning you have to type what you want on a terminal window. You open a terminal window by holding ALT+CTRL+T, and then you type the commands, starting by &#8220;sudo&#8221; and then the apt-get command that you want to run. For example: &#8220;sudo apt-get update&#8221;, whithough quotes. The list of usual APT commands follow.

sudo apt-get update: is used to resynchronize the package index files from the sources specified in /etc/apt/sources.list.

sudo apt-get upgrade: is used to install the newest versions of all packages currently installed on the system. Under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version.

sudo apt-get dist-upgrade: is used to upgrade and also to intelligently handle changing dependencies with new versions of packages. Apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less Both issues have a middle level of dificulty, but I don&#8217;t expect important ones if necessary. APTITUDE has a smarter dist-upgrade feature called full-upgrade.

sudo apt-file: is a command that allows you to find which package includes a specific file, or to list all files included in a package. It is packaged separately from the main APT utilities.

sudo apt-config: is the APT Configuration Query program. apt-config dump shows the configuration.

[HR][/HR]
**APT CONFIGURATION FILES**

APT configuration files are located in:

/etc/apt/sources.list: Locations to fetch packages from.
/etc/apt/sources.list.d/: Additional source list fragments.
/etc/apt/apt.conf: APT configuration file.
/etc/apt/apt.conf.d/: APT configuration file fragments.
/etc/apt/preferences: version preferences file. This is where you would specify "pinning", i.e. a preference to get certain packages from a separate source or from a different version of a distribution.
/var/cache/apt/archives/: storage area for retrieved package files.
/var/cache/apt/archives/partial/: storage area for package files in transit.
/var/lib/apt/lists/: storage area for state information for each package resource specified in sources.list
/var/lib/apt/lists/partial/: storage area for state information in transit.

[HR][/HR]
**GRAPHICAL INTERFACES**

Since people in general like GUI the best, there are many package managers that are more user friendly. The most known ones in Ubuntu are SYNAPTIC, Ubuntu Software Center and Ubuntu Software (GNOME Software). Ubuntu Software is the default now in Ubuntu. 

There is also APTITUDE, which is an advanced and much less user friendly graphical package manager.

GDEBI is an APT tool which can be used in command-line and on the GUI. GDebi can install a local .deb file via the command line like the dpkg command, but with access to repositories to resolve dependencies.

**TO BE CONTINUED...**

---

### Post by QIII on 2016-05-21
Not a support request.

*Moved to the **Cafe**.*

---

### Post by kwanbis on 2016-05-21
> **QIII said:**
> Not a support request.

*Moved to the **Cafe**.*
Thanks, I wasn't sure where to post it.

---

### Post by mastablasta on 2016-05-22
> **kwanbis said:**
> 
There many, many, many,  I would actually say too many, distros to choose from, being the most populars: Debian/Ubuntu and RedHat/Fedora.

Actually Ubuntu, Mint, OpenSUSE are more aimed at "home user" than RedHat or Debian.



> The problem is that I have a HDD on my ThinkPad T520, that is the original hard drive, and where there was a CD, I now have second drive, an SSD, to which I installed Ubuntu.
...
I believe this two problems should be fixed, if we want Linux to appeal to a broader audience.

would the broader audience complicate their windows install like that? i dont' think so. you get a no OS PC (single or multiple disk) you slect the OS drive format it and install the OS to it.
what you were doing is advance settings and there is a menu for that in install where you can choose where to install GRUB as well as various other settings. this is true for fiel systems as well. you don't install some other file system to windows PC and then talk about how it is not supported that well.


> I believe that good defaults are very important, and this 5 points should be considered  to be more like OSX and/or Windows.

there are many desktop options and windows managers in linux. Unity (used in Ubuntu) is just one of them. feel free to chose. if you want a "traditional desktop" there are XFCE (used in Xubuntu), KDE (used in Kubuntu) and Cinamon (used and develope din Mint). you can even get full windows 7 look using ZorinOS. Or you can get no hardware acceleration, windows xp liek look using LXDE (Lubuntu) or for win98 fo with only IceWM. there are also tabbed widnows managers like i3. basically so many options. windows has just one look and maybe some fallback/lwo grpahics mode per version.

i am not sure anyone tried to replicate the gloriuous windows 8 tiles look in linux. or windows 10 start menu with ads and unnecessary apps next to programs - a good design indeed!?

as for Unity there is a reason for it's looks and behaviour - see Ubuntu mobile, Ubuntu phones and tablets and read about convergence (which was the goal  before windows10). it will all make sense to you then.

> 1) accessing NTFS files makes the system very slow. VERY. So bad that it impacted browsing, downloading, watching videos. At first I didn’t realize it was the NTFS writing and the performance of the system was terrible, to the point that I thought how can Canonical release such a horrible release!

But after converting those partitions to Ext4, everything runs so smooth. Maybe it is a problem with this version of Ubuntu? I don’t know.

fragmented NTFS maybe? drive with disk errors? 
who knows why, but of 2 things i am sure:
1. NTFS works just fine for me.
2. since it is not a supported file system and a closed source one at that i doubt one can expect even this much from Linux. in other words use fully supported file system for a smooth ride.

another thing you can't run chkdsk in linux to fix any erros on NTFS disk. 

and there are far more advanced system available on linux such as btrfs and ZFS which offer disk images among other things - mostly an overkill for home user.

> 2) Even though ubuntu shows all the NTFS partitions under the file manager, they are not “mounted” till you first open them. If Ubuntu knows and understands the NTFS partitions, why don’t we just mount them right away? Is it because of point 1? I don’t know.

there is a reason for that. for example : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

> And all was fine. But as simple as the fix was, I wonder why doesn’t gparted asks me if I want to “own” the partition?

because the "user" using gparted and that created the partition was admin/sudo?
plus security issue and multiuser os. read more here as it wa salready debated and explained by soem very security oriented members: [http://ubuntuforums.org/showthread.php?t=2165411](http://ubuntuforums.org/showthread.php?t=2165411)

also note how you do not own anything outside /home folder on your root file system.

> **TRACKPOINT SETUP**
I’m running Ubuntu on a ThinkPad. ThinkPads are some of the best business laptops and they are known for the little joystick that resides between the G, H and B, and that is called the TrackPoint.

In Windows you can easily change the sensitivity and speed of the trackpoint very easily, but for some known reason to me, that is VERY complicated in linux.

probably because Lenovo or whoever made their trackpoint devide didn't provide linux drivers and GUI for managing the device.  So Lenovo will know best why they didn't provide the drivers in a propper way.

 if you had fully supported touchpad then your experience would be same as in windows.

> During the installation, you choose a user, and by default Ubuntu gives the PC a user-pc name, so in my case it was kwanbis and kwanbis-Thinkpad-T520, so in the terminal I would see something like: kwanbis@kwanbis-ThinkPad-T520, and since I wanted to have kwanbis@T520, I had to rename the PC.

In Linux, you do so by editing this two files and changing the name where it says 127.0.0.1.

gksu gedit /etc/hostname
gksu gedit /etc/hosts

i am preety sure there is a GUI for that. anyway remember that the OS has it's roots in servers and that desktop was added only later on. windows wnet the other way trying to mangle desktop os into their windows server. and if i am not mistaking at one point they even had to rethink thew whole server thing. and even now linux as server is far more advanced security wise than windows.

---

### Post by coldraven on 2016-05-22
> But I have noticed two things:

1) accessing NTFS files makes the system very slow.
I have been using a 1TB external USB drive formatted NTFS for years with no problems and no slow down. Maybe you had too many bad sectors or some other sort of errors.

---

### Post by kwanbis on 2016-05-22
> **mastablasta said:**
> Actually Ubuntu, Mint, OpenSUSE are more aimed at "home user" than RedHat or Debian.
You are correct. But notice I didn't say otherwise ;) In fact, I believe Fedora is very user friendly, maybe as much as Ubuntu et all?

> **mastablasta said:**
> would the broader audience complicate their windows install like that? i dont' think so. you get a no OS PC (single or multiple disk) you slect the OS drive format it and install the OS to it. What you were doing is advance settings and there is a menu for that in install where you can choose where to install GRUB as well as various other settings. this is true for fiel systems as well. you don't install some other file system to windows PC and then talk about how it is not supported that well.
What I believe is that the linux installer should have the intelligence to at leas ask, "hey dude, you are installing Linux on drive B, so, do you want the bootloader in drive A or B? Honestly I don't believe what I did is that advanced. I just replaced my CD drive with an SSD drive. I agree is not something a beginner would do, but not such a weird thing.

> **mastablasta said:**
> there are many desktop options and windows managers in linux. Unity (used in Ubuntu) is just one of them. feel free to chose. if you want a "traditional desktop" there are XFCE (used in Xubuntu), KDE (used in Kubuntu) and Cinamon (used and develope din Mint). you can even get full windows 7 look using ZorinOS. Or you can get no hardware acceleration, windows xp liek look using LXDE (Lubuntu) or for win98 fo with only IceWM. there are also tabbed widnows managers like i3. basically so many options. windows has just one look and maybe some fallback/lwo grpahics mode per version.
I have tried them all. XFCE, KDE, Cinamon, LXE, GNOME2 and 3. The one that looked more polished to me are Unity, GNOME 3 and KDE.

GNOME3 is too different for me, at least for now. And KDE looks over engineered somehow. This is why I settled on Unity, which in general I like, but I believe those 4 suggestions are good ones. Of course they are just that, suggestions. 

> **mastablasta said:**
> i am not sure anyone tried to replicate the glorious windows 8 tiles look in linux. or windows 10 start menu with ads and unnecessary apps next to programs - a good design indeed!?
I don't like windows 8 or 10 start menus at all. I like Unity because it looks like the apple doc, even though I believe it is a little too dead.

> **mastablasta said:**
> as for Unity there is a reason for it's looks and behaviour - see Ubuntu mobile, Ubuntu phones and tablets and read about convergence (which was the goal  before windows10). it will all make sense to you then.
Really? Didn't Microsoft already proved how terrible that Idea is? 

> **mastablasta said:**
> fragmented NTFS maybe? drive with disk errors?  who knows why, but of 2 things i am sure:
1. NTFS works just fine for me.
2. since it is not a supported file system and a closed source one at that i doubt one can expect even this much from Linux. in other words use fully supported file system for a smooth ride.
Weird that you mention it. Are you running 16.04? My disk seems to be perfect. I don't see any issues with it.

> **mastablasta said:**
> there is a reason for that. for example : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
Sorry. I don't get it. What is the reason why I get the NTFS partition listed and accessible though a link, but not mounted by default?

> **mastablasta said:**
> because the "user" using gparted and that created the partition was admin/sudo? plus security issue and multiuser os. read more here as it wa salready debated and explained by soem very security oriented members: [http://ubuntuforums.org/showthread.php?t=2165411](http://ubuntuforums.org/showthread.php?t=2165411) also note how you do not own anything outside /home folder on your root file system.
The user using gparted is admin/sudo because there is no other option, or I'm wrong? I mean. It wasn't such an issue, but again, wouldn't it be easier for Gparted to ask me: "do you want sudo to own this partition or do you want to own it"?

> **mastablasta said:**
> probably because Lenovo or whoever made their trackpoint devide didn't provide linux drivers and GUI for managing the device.  So Lenovo will know best why they didn't provide the drivers in a propper way. If you had fully supported touchpad then your experience would be same as in windows.i am preety sure there is a GUI for that. anyway remember that the OS has it's roots in servers and that desktop was added only later on. windows wnet the other way trying to mangle desktop os into their windows server. and if i am not mistaking at one point they even had to rethink thew whole server thing. and even now linux as server is far more advanced security wise than windows.
Linux is great. And each day that passes by I like it more. But I still believe it is overly complicated the trackpoint configuration, and there are many, many, many subsystems that are not supported on linux by the vendor and are properly supported by linux anyway. Maybe I should start  sending letters to Lenovo or Synaptics so that they write a proper driver, or I might even try to write a configuration tool if I ever understand how to modify it.

By the way, any suggestions on how to automate that each time I login this command:

 echo 255 | sudo tee /sys/devices/platform/i8042/serio1/serio2/sensitivity

gets executed automatically and without the sudo password?

Thanks for all your comments! ;)

---

### Post by kwanbis on 2016-05-22
> **coldraven said:**
> I have been using a 1TB external USB drive formatted NTFS for years with no problems and no slow down. Maybe you had too many bad sectors or some other sort of errors.
Like I just replied to mastablasta, that is very weird. My hard drive is perfect, no errors. I tried actually with two hard drives. One connected directly and one trhough USB. Are you also using 16.04?

By the way, any suggestions on how to automate that each time I login this command:

 echo 255 | sudo tee /sys/devices/platform/i8042/serio1/serio2/sensitivity

gets executed automatically and without the sudo password?

Thanks for your kind words.

---

### Post by izznogooood on 2016-05-22
To have an easier time with NTFS (and SDcards etc)

sudo apt install exfat-utils

As for the Unity bar on the side, this makes perfect sense in the modern time of wide-screens. If you look at the totality of Unity it focuses your mouse movements on the left side. Besides i use a lot of keyboard shortcuts making unity far better and faster (for me) than any other DM. But i agree with you on the size, I´m not THAT far sighted yet ;) (Looking at my father outreaching his arms trying too read the phone I imagine its bound to happen in due time :D )

There are many different DM´s. If you like mac you should look in to: [http://www.makeuseof.com/tag/8-power-docks-for-your-linux-machine/](http://www.makeuseof.com/tag/8-power-docks-for-your-linux-machine/)

The problem you have now is not the software it self, its the overwhelming freedom om choice (of every aspect of your system) :D

---

### Post by mastablasta on 2016-05-23
> **kwanbis said:**
> 
What I believe is that the linux installer should have the intelligence to at leas ask, "hey dude, you are installing Linux on drive B, so, do you want the bootloader in drive A or B? Honestly I don't believe what I did is that advanced. I just replaced my CD drive with an SSD drive. I agree is not something a beginner would do, but not such a weird thing.
grub should go where the system is and does go if using defautl install. in advanced version you can choose where you want it. 

> 
GNOME3 is too different for me, at least for now. And KDE looks over engineered somehow. This is why I settled on Unity, which in general I like, but I believe those 4 suggestions are good ones. Of course they are just that, suggestions. 
all have themse available and XFCE and KDE are known for being very customizable so you can make your own look or load the one (theme) you want.

> 
Really? Didn't Microsoft already proved how terrible that Idea is? 
it's not terrible. latest ubuntu tablet - the only issue it seems to have (based on reviews) is that it is not responsive enough when running multiple apps. you plugin th ekeboard it behavs as desktop runnign deksotp aapps., unplug it and you have touch interface.

> 
Weird that you mention it. Are you running 16.04? My disk seems to be perfect. I don't see any issues with it. nope 14.04.4 - 16.04 will go live on .1 release. maybe not even then. quite happy with 14.04 for now.


> Sorry. I don't get it. What is the reason why I get the NTFS partition listed and accessible though a link, but not mounted by default?
read again. you could corrupt (not saying it will 100% happen) your system windows partition if all NTFS were automounted. it is best to leave themunmounted and let the user decide if they need them to be mounted or if they will mount them. after all it is them takign the risk. data partitions are another matter, but how is OS going to know which one is data and which one OS? user will tell it.
> 
The user using gparted is admin/sudo because there is no other option, or I'm wrong? I mean. It wasn't such an issue, but again, wouldn't it be easier for Gparted to ask me: "do you want sudo to own this partition or do you want to own it"?
it has to be sudo who can format it. sudo owns it when formating is done and then after format is done, sudo decides who else will have access to it. a dialog after formating is finished migth make sense for deskotp. though GUi is just a visual representation of CLI. maybe they oculd ad dit but this is something that should go on gparted wishlist. feel free to suggest it to them. i think it might make sense.


 > Maybe I should start  sending letters to Lenovo or Synaptics so that they write a proper driver, or I might even try to write a configuration tool if I ever understand how to modify it. yes, just don't spam them.

> By the way, any suggestions on how to automate that each time I login this command:

 echo 255 | sudo tee /sys/devices/platform/i8042/serio1/serio2/sensitivity

gets executed automatically and without the sudo password?


create a script and run it on boot. for example: [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)

---

### Post by kwanbis on 2016-05-23
> **izznogooood said:**
> To have an easier time with NTFS (and SDcards etc) sudo apt install exfat-utils
Thanks, I already have it installed. Sadly it makes no difference on the performance.

> **izznogooood said:**
> As for the Unity bar on the side, this makes perfect sense in the modern time of wide-screens. If you look at the totality of Unity it focuses your mouse movements on the left side. Besides i use a lot of keyboard shortcuts making unity far better and faster (for me) than any other DM. But i agree with you on the size, I´m not THAT far sighted yet ;) (Looking at my father outreaching his arms trying too read the phone I imagine its bound to happen in due time :D )
I don't know. Maybe is that I'm too old and I have been using tasbars and docks on the bottom al my life, but to the left it makes no sense for me. I like unity so far, and moving the bar to the bottom I like it betteer. But my point is, us hackers and geeks have no problem changing the bar. If the bar was on the bottom, and you wanted it on the left side, you just knew or find out how to move it.

I believe Linux/Ubuntu has already conquered us, the advanced user, but now we need to grow our user base. We are at 2 or 3% of the desktop market. That is too little. We need to be at 15% or more. That way, companies like adobe would port their soft to our OS, and that would be great.

Experience has shown me, or at least I see it that way, that normal people go with the defaults. So the defaults should be as "normal-user-friendly" as possible.

> **izznogooood said:**
> There are many different DM´s. If you like mac you should look in to: [http://www.makeuseof.com/tag/8-power-docks-for-your-linux-machine/](http://www.makeuseof.com/tag/8-power-docks-for-your-linux-machine/)
I know! That is good. I'm already ok with the dock the way it is. But I would take a look anyway.

> **izznogooood said:**
> The problem you have now is not the software it self, its the overwhelming freedom om choice (of every aspect of your system) :D
And that is always good for us ;)

---

### Post by Linuxratty on 2016-05-24
Over my 12 years of using Linux, I've found I enjoy tweaking the appearance and the more i can tweak,the happier I become.
That being said,for me,the most fun desktops are MATE and XFCE.
 You mentioned Fedora..Well,ages ago I used it and I found it to be *very* user friendly. I honestly
could not tell much difference between it and Ubuntu. It was solid as a rock and easy to set up the way I liked it.
 I never had a moments problem with it. 
 But I always end up back with Ubuntu,although Manjaro is on my other box since I wanted 
to see what it's like using a rolling release that is user friendly.It's working out nicely.

---

### Post by user1397 on 2016-05-25
> **Linuxratty said:**
> Over my 12 years of using Linux, I've found I enjoy tweaking the appearance and the more i can tweak,the happier I become.
That being said,for me,the most fun desktops are MATE and XFCE.
 You mentioned Fedora..Well,ages ago I used it and I found it to be *very* user friendly. I honestly
could not tell much difference between it and Ubuntu. It was solid as a rock and easy to set up the way I liked it.
 I never had a moments problem with it. 
 But I always end up back with Ubuntu,although Manjaro is on my other box since I wanted 
to see what it's like using a rolling release that is user friendly.It's working out nicely.
I always end up back with ubuntu as well.  I tried manjaro not too long ago, but was a bit disappointed with a major issue I faced right after installation.  It was some error where I couldn't sync the repos correctly, and even though I was kindly told to go to their wiki page which did fix the issue, I thought welp, this isn't as user friendly as I thought it might be, so back to ubuntu it was.  

I keep switching between unity, plasma 5, xfce, and mate...I can't decide what I like best hehe.  I don't like gnome very much. Right now I'm leaning more towards xfce I think.

---

### Post by Lancro on 2016-05-25
> **user1397 said:**
> I always end up back with ubuntu as well.  I tried manjaro not too long ago, but was a bit disappointed with a major issue I faced right after installation.  It was some error where I couldn't sync the repos correctly, and even though I was kindly told to go to their wiki page which did fix the issue, I thought welp, this isn't as user friendly as I thought it might be, so back to ubuntu it was.  

I keep switching between unity, plasma 5, xfce, and mate...I can't decide what I like best hehe.  I don't like gnome very much. Right now I'm leaning more towards xfce I think.

6 years in the linux thing, I always finished with ubuntu at the end too, but Unity was a great deception for me, to have to take out Unity every install was making me feel a little stupid in my choice, so I didnt left Ubuntu at 100%, I went to mint 3 years ago, and the way they polish it, and Cinnamon, has taken my heart. But I started in this forum, with Ubuntu 10.10, so I always have a place in my heart for it. Customizing the system is nice, but if you have to change almost everything, maybe you are not in the right distro.

---

### Post by elliotn on 2016-05-27
Good thread to read

---

### Post by Linuxratty on 2016-05-27
I don't want to put all my eggs  one basket,which is why I have a different distro on each box.
That does sound unfortunate.

---

### Post by Omar_Jair on 2016-05-27
i used linux for a little while now, must say that i started using debian but the only problem is that it's stability has a very high cost, packages are outdated as hell but performance is quite good. About ubuntu, i mostly like its repositories, they are very recent packages but not too bleeding edge, the only thing that makes me have issues is the Performance.

---

### Post by mastablasta on 2016-05-28
@omar_jair if you think Debian has outdated packgaes what would you say about my windows XP? :P

and like in windows you should be able to add backports and install newer apps on stable. although that could make it less stable.

---

### Post by izznogooood on 2016-05-28
I add the developer repositories of the apps i want up to date.

---

### Post by kwanbis on 2016-05-30
> **mastablasta said:**
> grub should go where the system is and does go if using defautl install. in advanced version you can choose where you want it.
Exactly. So if I install to sdb, why is GRUB on sda?

> **mastablasta said:**
> all have themse available and XFCE and KDE are known for being very customizable so you can make your own look or load the one (theme) you want.
I actually moved to Cinnamon which I LOVE!

> **mastablasta said:**
> it's not terrible. latest ubuntu tablet - the only issue it seems to have (based on reviews) is that it is not responsive enough when running multiple apps. you plugin th ekeboard it behavs as desktop runnign deksotp aapps., unplug it and you have touch interface.
Not terrible != Great ;)

> **mastablasta said:**
> nope 14.04.4 - 16.04 will go live on .1 release. maybe not even then. quite happy with 14.04 for now.
It was actually the application I use to manage files, Double Commander. Nautilus has no problems.

> **mastablasta said:**
> read again. you could corrupt (not saying it will 100% happen) your system windows partition if all NTFS were automounted. it is best to leave themunmounted and let the user decide if they need them to be mounted or if they will mount them. after all it is them takign the risk. data partitions are another matter, but how is OS going to know which one is data and which one OS? user will tell it.
Maybe then ask the user which partitions to automount at install time or at least provide a user friendly way of choosing it?

> **mastablasta said:**
> create a script and run it on boot. for example: [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)
I'm gonna try.

> **Linuxratty said:**
> Over my 12 years of using Linux, I've found I enjoy tweaking the appearance and the more i can tweak,the happier I become.
That being said,for me,the most fun desktops are MATE and XFCE.
That is the good thing of choice. I'm on cinnamon and happy (I already f*cked ubuntu 5 times :D)

> **Linuxratty said:**
> You mentioned Fedora..Well,ages ago I used it and I found it to be *very* user friendly. I honestly
could not tell much difference between it and Ubuntu. It was solid as a rock and easy to set up the way I liked it. I never had a moments problem with it. But I always end up back with Ubuntu,although Manjaro is on my other box since I wanted to see what it's like using a rolling release that is user friendly.It's working out nicely.
Nice. I would try once I have time.

> **user1397 said:**
> I always end up back with ubuntu as well.  I tried manjaro not too long ago, but was a bit disappointed with a major issue I faced right after installation.  It was some error where I couldn't sync the repos correctly, and even though I was kindly told to go to their wiki page which did fix the issue, I thought welp, this isn't as user friendly as I thought it might be, so back to ubuntu it was. I keep switching between unity, plasma 5, xfce, and mate...I can't decide what I like best hehe.  I don't like gnome very much. Right now I'm leaning more towards xfce I think.
I tried them all. And while I like things from each, I think graphically the best are Cinnamon, Unity and KDE. The others look too childish. 

> **Lancro said:**
> 6 years in the linux thing, I always finished with ubuntu at the end too, but Unity was a great deception for me, to have to take out Unity every install was making me feel a little stupid in my choice, so I didnt left Ubuntu at 100%, I went to mint 3 years ago, and the way they polish it, and Cinnamon, has taken my heart. But I started in this forum, with Ubuntu 10.10, so I always have a place in my heart for it. Customizing the system is nice, but if you have to change almost everything, maybe you are not in the right distro.
I wanted to try Mint, but after their security fiasco I'm not so sure. Also, I believe the best community is in Ubuntu. Maybe I'm wrong.

> **elliotn said:**
> Good thread to read
THANKS!

> **Linuxratty said:**
> I don't want to put all my eggs  one basket,which is why I have a dihttp://tehparadox.com/forum/f73/lost-s05-complete-720p-bluray-11592938/fferent distro on each box.
That does sound unfortunate.
I only have one working system now. But That is a good idea.

> **Omar_Jair said:**
> i used linux for a little while now, must say that i started using debian but the only problem is that it's stability has a very high cost, packages are outdated as hell but performance is quite good. About ubuntu, i mostly like its repositories, they are very recent packages but not too bleeding edge, the only thing that makes me have issues is the Performance.
That is why I choose Ubuntu LTS!

> **izznogooood said:**
> I add the developer repositories of the apps i want up to date.
Yep. That is why I do.

---

### Post by samuelfcampbell on 2017-05-20
Since 2011, various software has existed to write raw image files to USB flash drives.
I really felt good about my learning adventures with Linux: Mint, Mate, Linux Lite, Fedora, Ubuntu 64-bit version and Cinnamon thus far.
I started getting used these and found them all it to be *very* user friendly some capable of handling of the industrial size loads I try to operate with on my old Dell Laptops. Thanks to the free software, package, or application installation mechanism and the installer for the system itself. 
ie.. Playing games, Gaming Development software/Graphics and Video/Audio Players and Editors. **OpenShot** - a cross-platform video editor, with support for Linux, Mac, and Windows. This has proved to be easy to use,                    quick for me to learn, and surprisingly powerful as a video editor. I have no problem cutting, slicing, and editing any of my videos or even films. The **[Blender 2.78c]("https://www.blender.org/features/2-78/") Stable Release** application - I can use for creating [animated films]("https://en.wikipedia.org/wiki/Animation"), [visual effects]("https://en.wikipedia.org/wiki/Visual_effects"), art, [3D printed]("https://en.wikipedia.org/wiki/3D_printing") models, interactive 3D applications and [video games]("https://en.wikipedia.org/wiki/Video_game"). Blender's features include [3D modeling]("https://en.wikipedia.org/wiki/3D_modeling"), [UV unwrapping]("https://en.wikipedia.org/wiki/UV_mapping"), [texturing]("https://en.wikipedia.org/wiki/Texture_mapping"), [raster graphics editing]("https://en.wikipedia.org/wiki/Raster_graphics_editor"), [rigging and skinning]("https://en.wikipedia.org/wiki/Skeletal_animation"), [fluid and smoke simulation]("https://en.wikipedia.org/wiki/Fluid_simulation"), [particle]("https://en.wikipedia.org/wiki/Particle_system") simulation, [soft body]("https://en.wikipedia.org/wiki/Soft_body_dynamics") simulation, [sculpting]("https://en.wikipedia.org/wiki/Digital_sculpting"), [animating]("https://en.wikipedia.org/wiki/Computer_animation"), [match moving]("https://en.wikipedia.org/wiki/Match_moving"), [camera tracking]("https://en.wikipedia.org/wiki/Camera_tracking"), [rendering]("https://en.wikipedia.org/wiki/Rendering_(computer_graphics)"), [video editing]("https://en.wikipedia.org/wiki/Video_editing_software") and [compositing]("https://en.wikipedia.org/wiki/Compositing"). It further features an integrated [game engine]("https://en.wikipedia.org/wiki/Blender_Game_Engine")., I'll also have open a window with I**[COLOR=#6a6a6a]nkscape[/COLOR]**-0.92.1 - used to create or edit vector graphics such as illustrations, diagrams, line arts, charts, logos and complex paintings  While running other windows programs and working downloads, as I switch back and forth to terminal   all in different windows/workspaces at the same time. Some of my home work refers back to code names of the early as 2004 releases of **Ubuntu** like: **Warty Warthog**, **Hoary** **Hedgehog**,** Breezy Badger**, **Dapper Drake**,** Edgy Eft**. and **Feisty Fawn**. I wonder if anyone is running any of those **distros** these days? Also looking into the other **variations of the Ubuntu themes** like: **Kubuntu** the *KDE-based* version, **Ebuntu** for the classroom and **Xubuntu** light weight version based on the *Xfce desktop *my old desktop. I'm tempted to get another stack of disks or a hand full of flash drives and have a go of it.   

**Ubuntu **- the concept meaning something along the lines of humanity toward others or I am because we are. 
Wishing al many more adventures on **Linux** 
~ **Samuel F Campbell** :guitar:

---

### Post by lisati on 2017-05-20
[s]Thread closed for staff review.[/s]
This old thread can stay closed for now.

---

