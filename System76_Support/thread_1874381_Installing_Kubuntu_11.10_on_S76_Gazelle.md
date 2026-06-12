---
title: "Installing Kubuntu 11.10 on S76 Gazelle"
date: 2011-11-03
forum: System76 Support
---

### Post by mgolden on 2011-11-03
I just got a new S76 Gazelle Pro.  Specs are 16GB ram, 120GB Sata3 SSD drive.  I have never been a big fan of of the Gnome desktop, but was willing to take a look at it.  Well, after a few minutes, and after hearing about all the troubles people were having with it, (not only on S76 hardware, I should add) I just decided to blow it out and install Kubuntu.  I got the amd64 desktop disk and used that.

I will describe below what I did to install everything.  I found that the install was quite clean, and pretty much everything worked right out of the box.  The only two things I have noticed as problems in the end are:

*) The camera LED doesn't turn on.
*) I can't seem to plug in a monitor using the DVI cable, only VGA.  I am still looking into this and seeing if it is a hardware problem.  (I hope not.)

I should also say that I use my machine for Ruby on Rails development, and this is why I installed so much techy stuff.  Obviously you may find that you need other things.

My machine has 16GB of ram, and with an SSD drive it's probably not the best idea to use for swapping anyway, so I manually partitioned and did not make swap.  This is particular to my configuration, so YMMV.

Herewith the instructions - hope someone finds them useful:

*) Install from liveCD.  Leave UNCHECKED the box about updates during
  installation.  Reboot, do updates on first login.  Go to K > System >
  Additional Drivers and get the NVIDIA accelerated graphics driver, post
  release updates.  (This appeared not to be optional for the i386 version.)

*) Edit /etc/fstab [only need if you have an SSD]
  Comment out the swap line if the disk was partitioned with swap.
  Add noatime,discard to the / partition.  Reboot.

*) In the package manager, make sure that the partners repository is selected 

*) Add the system76 repostitory, as per
    [http://ubuntuforums.org/showthread.php?t=1141563](http://ubuntuforums.org/showthread.php?t=1141563)
  In the package manager search for system76 and install the system76 driver

*) sudo apt-get install
  lynx konqueror digikam apache2 okular konq-plugins
  mplayer umbrello rails ruby git emacs rar unrar
  gitk rubygems-doc mysql-server vlc tcsh gksu
  lame sox libsox-fmt-all traceroute wireshark

*) For sending in debug reports, sudo apt-get install
  kde-workspace-dbg

*) Start kmix, Settings > Change Master Channel... > internal sound
  K > System Settings > Default Applications > Web Browser > Firefox
  I also use Konqueror as a file manager rather than Dolphin

*) [No longer needed: Create file to /etc/apt/sources.list.d/skype.listi
  containing:
   # Skype
   deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free ]
  Then sudo apt-get install skype

*) Get google chrome from [http://www.google.com/chrome/index.html](http://www.google.com/chrome/index.html)
  Then, dpkg -i google-chrome-stable_current_amd64.deb
  This will probably have an error and you will have to use apt-get install
  to get some other packages.  Once you do this chrome will install itself.

*) Install the libdvdcss2 so you can play DVDs.  You can do this by simply
    sudo apt-get install libdvdread4  [probably already installed]
    sudo /usr/share/doc/libdvdread4/install-css.sh
  Also install the medibuntu repository, as
    sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
  See:
    [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
    [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)
  Note that I disabled the medibuntu repository after adding it.  (In muon,
  under Settings > Configure Software Sources)

*) Oog - installing java is a real pain:  I tried this:
  [http://www.twm-kd.com/linux/install-oracle-java-sdk-in-ubuntu-11-10/](http://www.twm-kd.com/linux/install-oracle-java-sdk-in-ubuntu-11-10/)
  These two required installing new source repositories, but
  they didn't work.
  [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)
  [http://www.unixmen.com/linux-tutorials/1951-install-oracle-java-7-in-ubuntu-1110](http://www.unixmen.com/linux-tutorials/1951-install-oracle-java-7-in-ubuntu-1110)

*) Now go to [www.aptana.com](www.aptana.com) and download Aptana Studio 3. Unzip
  the file and move the new directory to /usr/local/aptana-studio-3.  Set up
  the K menu using the K menu editor.
  (Be sure to check "only show in KDE" due to this bug:
  [https://bugs.kde.org/show_bug.cgi?id=283658](https://bugs.kde.org/show_bug.cgi?id=283658)
  You can then edit ~/.local/share/applications and remove the line
    OnlyShowIn=
  You probably want to move the file
    ~/.local/share/applications/Aptana\ Studio\ 3.desktop
  to /usr/share/applications so it is accessible to all users.
  Be sure to chown to root:root and chmod to 644.

*) The 11.04 version of mysql-workbench has a bug and won't work.  If a 
  newer version is available use that.  Otherwise, install ppa:olivier-berten/misc
  as package source and sudo apt-get install mysql-workbench-gpl
  Disable this repository as above once the package is installed.

*) There may be a conflict between the version of kdenlive and digikam.
  See: [http://kubuntuforums.net/forums/index.php?topic=3118584.0](http://kubuntuforums.net/forums/index.php?topic=3118584.0)
    [http://www.kdenlive.org/forum/mlts-sdl-module-not-found-0](http://www.kdenlive.org/forum/mlts-sdl-module-not-found-0)
  Open muon and add
    [http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu](http://ppa.launchpad.net/sunab/kdenlive-svn/ubuntu) oneiric main 
  and then install kdenlive
  Disable this repository as above after the software is installed.

*) Install Cisco VPN client:
   See [http://www.unfoldingcode.com/2011/08/how-to-install-cisco-vpn-client-on.html](http://www.unfoldingcode.com/2011/08/how-to-install-cisco-vpn-client-on.html)

*) It may be useful to fix any errors in .desktop files.  This can be done
  manually by simply running 
    kbuildsycoca4 --noincremental
  and then looking at what errors there are.  Also, see
    [http://forums.opensuse.org/english/other-forums/development/programming-scripting/452482-fixmime-fix-invalid-mime-entries-sloppy-desktop-files.html](http://forums.opensuse.org/english/other-forums/development/programming-scripting/452482-fixmime-fix-invalid-mime-entries-sloppy-desktop-files.html)

*) To get the latest version of the nvidia drivers, add
    [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) oneiric main
  in muon to see if there are updates of nvidia-current or any related
  graphics drivers or libraries.

---

### Post by vanhenryjr on 2011-11-03
Great post. I have Kubuntu 11.04 on an older desktop at home and Ubuntu 11.04 on my gazelle pro. I have considered going all Kubuntu for aesthetic reasons (and the fact that I sometimes leave my laptop at work and suffer from whip lash when I go home and use the Kubuntu set up).

I guess one thing holding me back is I am scared I may need a lot of help at some time and feel the safety of the greater numbers of Ubuntu users. How is Kubuntu working for you? What are the chances that it will not be supported as long as Ubuntu?

thanx
van

---

### Post by vanhenryjr on 2011-11-03
Mods, any way you can make the first post in this thread (not mine) a sticky? Nice to have one like this for all to see for a while.

??

---

### Post by isantop on 2011-11-03
[QUOTE=mgolden;11420330
*) The camera LED doesn't turn on.
*) I can't seem to plug in a monitor using the DVI cable, only VGA.  I am still looking into this and seeing if it is a hardware problem.  (I hope not.)[/QUOTE]

Actually, there isn't a Camera LED on the Gazelle. The indicator for whether the camera is on or not is in the Device Menu, in Unity (If the camera is on, there will be a webcam entry. If not, the webcam entry will be missing)

As for your graphics issues, I'm guessing that the problems are due to the Nvidia driver. Have you tried the Non-Post-release-updates version? I've heard the normal one is more stable, at least for the AMD drivers.

---

### Post by mgolden on 2011-11-04
@vanhenryjr:

I have been using Kubuntu for years.  I don't think that there is any chance of it disappearing any more or less than Ubuntu.  I have always preferred KDE to Gnome.  Nowadays I hear nothing but griping about how Gnome has gotten worse and worse, so I haven't been inclined to switch.

Many people left KDE when the 4.0 version was released.  Largely this was because of a nomenclature problem - it wasn't really a .0, it was more like a beta test.  However, it is now two years old and seems pretty usable to me.

Most of the sorts of problems you run into on kubuntu are the same ones as one runs into on ubuntu, so most of the help you'll need is the same.  The difference between ubuntu and kubuntu is the applications, not the kernel or the device drivers.

@isantop:

So far as I can tell, there is nothing in KDE that indicates that the camera is on.  I see a little hole next to the camera which I thought was the led.  I guess not.

As for the graphics issues - yes, they are caused by the driver.  I have made some progress toward straightening it out, and will make another post when I do.

---

### Post by mgolden on 2011-11-10
I have installed a somewhat cleaned up version of this set of instructions on my web server here:

[http://mitchgolden.com/computers/kubuntu-11.10.txt](http://mitchgolden.com/computers/kubuntu-11.10.txt)

---

### Post by PcMojo on 2011-11-10
I just went to download Kubuntu 11.10 and didn't see a version specific to AMD.  I thought there used to be one under Alt Cd, but all I saw was the text only installer.  Am I missing something? (wouldn't be the first time!) 
Also, the 32 bit is listed as recommended. Is that just because newer folks might not know which to download and it's a better one-size-fits all? Or are there more, as Bill Gates used to say, "undocumented features" in the 64 bit version?

---

### Post by isantop on 2011-11-11
> **PcMojo said:**
> I just went to download Kubuntu 11.10 and didn't see a version specific to AMD.  I thought there used to be one under Alt Cd, but all I saw was the text only installer.  Am I missing something? (wouldn't be the first time!) 
Also, the 32 bit is listed as recommended. Is that just because newer folks might not know which to download and it's a better one-size-fits all? Or are there more, as Bill Gates used to say, "undocumented features" in the 64 bit version?

Intel and AMD processors both share the same architectures, so anything that works for Intel *will* also work equally well on AMD (There are a couple of exceptions, when you start getting into highly specialized optimizations and virtualization extensions, but otherwise, they're identical). 

As for the 32-bit recommendation, it is a better choice for people who don't know what to choose (it *will* run on 99% of PC's built within the last decade). That said, I always recommend 64-bit, particularly if you have a System76 computer. The only 32-bit only computer we've ever sold was the original Starling Netbook. Every other machine has been 64-bit capable, and the benfits will almost always outweigh the drawbacks, if there even are any anymore.

---

### Post by PcMojo on 2011-11-13
Thanks for the info!

---

### Post by troyvit on 2011-12-02
I did this:

sudo apt-get install kubuntu-desktop

from here:

[http://kitara.nl/2011/06/14/how-to-switch-between-gnome-and-kde-on-ubuntu/](http://kitara.nl/2011/06/14/how-to-switch-between-gnome-and-kde-on-ubuntu/)

I'm sick of Unity's bugs. The interface seemed livable, but bugs centered around its widgets and focus were just weak, and there is no usable multi-clipboard in gnome that I can find. Glipper needs constant restarts to function and it seemed the best of them. Maybe I should have tried Gnome's classic interface before fleeing back to KDE but sometimes you just have to cut your losses.

The one thing I can say is that for some reason claws-mail is more beautiful in Gnome than it is in KDE. I'll miss that.

I kept GDM as my display manager (big mistake) and the system wouldn't boot (stopping system V runlevel compatibility). I had to manually log in using:

alt+ctrl+f1

Then I started KDM, which allowed me to log in.

Then I ran:

sudo dpkg-reconfigure kdm

which allowed me to select kdm as the default.

Fonts were messed up, ctrl+shift+Backtab doesn't send you marching through desktops in reverse, but it's always been like that. It's nice being back with the familiar annoying bugs instead of newer, stupider ones.

---

### Post by mgolden on 2011-12-05
Maybe you had the same problem with fonts I did - they were all too big.  This I fixed by going to the Settings > System Settings > Application Appearance > Fonts and setting Force Fonts DPI to 120.  I think this might be another issue with the nVidia driver.

---

