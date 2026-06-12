---
title: "Installation scripts for everything"
date: 2008-05-20
forum: The Cafe
---

### Post by 22flames on 2008-05-20
Hello and thank you for visiting my installation thread in this thread i will post scripts that will help you download and install various programs and applications some of these scripts will download and install beta programs so please handle with care thank you. Request are taken.

**BEFORE USING**

EX- Ok so if you are here you probably are new to Ubuntu Linux. To use any of these scripts go to applications, than accessories, than Terminal. Enter all of the commands separately. Enjoy 

[B][SIZE="4"]Multimedia Scripts[/SIZE] 
[/B]

[SIZE="3"]Using an iPod Touch 3g 2g or 1st gen on Ubuntu[/SIZE]

**What this is About**

For the past couple of days I have been working a little script that allows you to use your iPod Touch or iPhone on Ubuntu in Rythmbox or Banshee. I will post the source of the script and a download link to it as well below please give me credit if you steal this and if you want to know more about the process go to my site ianmarmour.com and read the post. 

**How to Use**

[COLOR="Red"]PSSSSSSSSSSSSSSSSSSSSSS - THERE WILL BE AN ERROR AT START JUST PRESS ENTER [/COLOR]

Copy the script below into your terminal or click the download link below and download it from the file sharer of your choice. Once you have it downloaded save it into your home folder than go into a Applications/Accessories/Terminal and run the command ```
chmod +x IpodTouch3gInstaller.sh
``` Than type ```
./IpodTouch3gInstaller.sh
``` That will initiate the installer.

```


#!/bin/bash
# init
function pause(){
   read -p “$*”
}
# other stuff
pause 'Press any key to continue…'
# other stuff

#Tells the user why they need to enter password.
echo Please type in your password so the installer can run as Root.

#Add's ifuse dev repo.
sudo add-apt-repository ppa:pmcenery/ppa

#Updates your sources.
sudo apt-get update

#Installs all needed dependancys and packages
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1** usbmuxd

#Make the iPod's mount directory
sudo mkdir /mnt/ipod

#Gets the custom fuse.conf file from my webserver.
sudo wget http://22flames.sqweebs.com/fuse.conf 

#Moves the custom fuse.conf file to your etc folder.
sudo mv fuse.conf /etc/

#Tells the User what to do
echo Please click on system than administrator than users and groups than click the lock than mange groups than find fuse and tick the box next to your name and close the user settings box.

#reads and gives the option to reboot than waits for input
read -p "When your ready to restart your computer press enter."

#Reboots the computer

sudo reboot 


```

!!Click Here to Download the Script and Run it Easily[http://www.multiupload.com/3SHEQB4A53]("http://www.multiupload.com/3SHEQB4A53")!!

[SIZE="3"]Entertainer[/SIZE]

OUTDATED- THIS SCRIPT DOES NOT COMPLY WITH THE LATEST RELEASES PLEASE GO TO [STARTUPGUIDE]("http://wiki.entertainer-project.com/wiki/StartUpGuide?") for help on this thanks.

EX- This program is very similar to windows media player this script will download and install all of the dependency and installation tools and the program to get you started if you want to run this program from the applications menu you will have to set the entertainer back end to run at startup and than make a new menu entry in the media section of your applications menu if you want a tutorial on how to do this please just comment and ask thank you for your time.PS- You may copy and paste into the terminal if you wish.:)


```
#!/bin/bash

sudo apt-get install python-notify python-feedparser python-pyvorbis python-pyogg python-eyed3 python-pysqlite2 python-gtk2 python-glade2 python-clutter python-pyvorbis python-imaging python-pyinotify python-imdbpy python-cairo-dev gtk-doc-tools python-cddb subversion

svn checkout http://entertainer-media-center.googlecode.com/svn/trunk/ entertainer

cd entertainer

cp cfg ~/.entertainer -R

cd src

echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo "" 

echo ""This will run the config so you can tell it where all of your media is""

echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""

./entertainer-content-management.py

./entertainer-backend.py

./entertainer-frontend.py

echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""
echo ""

echo "  if you want to use this as a media player just go to system preferences sessions startup programs and click add than navigate to your home and than click view hidden files than find .entertainer than click on it than click 
```


[SIZE="3"]Adobe Flash Player 10[/SIZE] 

EX- This is a beta and not all features work correctly so be careful. Also once the adobe installer starts just go through that ps that part is not mine all rights of that go to adobe.

```
#!/bin/bash

sudo apt-get remove flashplugin-nonfree
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz

cd ~/desktop 

tar zxvf flashplayer10_install_linux_051508.tar.gz

cd install_flash_player_10_linux

sudo ./flashplayer-installer
```



[SIZE="3"]DVD Playback[/SIZE]

EX-runs a script on your system so you can play commercial dvds PS needs a dvd drive 

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```



[SIZE="3"]System Audio Fix[/SIZE]

EX- Stops firefox from locking up if you try to run more than one type of audio at the same time as flash

```
sudo apt-get install libflashsupport
```


[SIZE="3"]Firefox Alternative Flash Fix[/SIZE]

EX- This is for those of you that have problems with Firefox going to flash pages and stopping it deletes the old flash plug in and uses a flash plug in from the old Netscape browsers it is only a temporary  fix until the new one comes out.
```

wget [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb

sudo apt-get remove --purge flashplugin-nonfree

sudo apt-get install flashplugin-nonfree

```


[SIZE="3"]Enable Mp3, DVD, Adobe Flash[/SIZE]

EX- Read the name 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs
```


[SIZE="3"]Acetone ISO[/SIZE] 

EX- This program will allow you to make iso backups of movies,games,music,disks,operating systems etc... it will also let you mount and use all of these :) very helpfull.

```
wget [http://internap.dl.sourceforge.net/sourceforge/acetoneiso2/acetoneiso2_20080508-1_i386.deb](http://internap.dl.sourceforge.net/sourceforge/acetoneiso2/acetoneiso2_20080508-1_i386.deb) 

sudo dpkg -i acetoneiso2_20080508-1_i386.deb

```
PS- **BY POSTING THIS I AM NOT ENDORSING PYRATING IN ANY WAY**


[SIZE="3"]Songbird Media Player[/SIZE]

EX- This media player is still very beta but does support good ipod, and media player integration and looks so much like itunes you would not believe it it has a built in browser and many good features i highly recommend this good piece of software.

```
sudo wget http://www.getdeb.net/download/2808/0

sudo dpkg -i songbird_0.6.0~getdeb1_i386.deb
```


**[SIZE="4"]Customization Scripts[/SIZE]**

[SIZE="3"]COMPIX fullscreen fix[/SIZE]

EX- so have you ever got a full screen bug in compiz i sure have heres a fix for it that helped me tons.

```
gconftool-2 --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows --type bool 0
```

[SIZE="3"]NEW COMPIZ INSTALL SCRIPT[/SIZE]

EX- This is just the easy way to do the same thing as BELOW i RECOMMEND THIS METHOD.

1. Open up a Terminal and type

```
sudo gedit /etc/apt/sources.list

```

2. Add this line to the bottom of that file

```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

3. Save and exit back to the terminal

4. Enter this command and wait

```
sudo apt-get install compizconfig-settings-manager
```


[SIZE="3"]Extra Plugins [/SIZE]

EX- If you used the above script you probably wont have all of the plugins for the newest compiz fusion these are just a few extras.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

mkdir ~/compizplugins

cd ~/compizplugins

git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2

git clone git://anongit.compiz-fusion.org/users/warlock/freewins

git clone git://anongit.compiz-fusion.org/users/pafy/screensaver

cd ~/compizplugins/atlantis2

make

make install

cd ~/compizplugins/freewins

make

make install

cd ~/compizplugins/screensaver

make

make install


```

REBOOT COMPUTER or PRESS CTRL ALT BACKSPACE.



[SIZE="3"]Compiz Fusion from Git[/SIZE]

EX- Why do you ask do i need this well i will tell you this is a script that will let you download all of the new compiz and install it as well as the new emerald and all of the themes this can mess up your system if you stop it mid way so please if you start it just let it run all of the way though this is a very cool script if you let it do its thing and once its done you will have to restart your system thank you. This script and the removal script came from Martje_001 ubuntu thread thank you.

```

#!/bin/bash

wget http://www.xs4all.nl/~mgj1/downloads/compiz-git-newest.tar.gz

tar xzf compiz-git-newest.tar.gz

cd compiz-git

./compiz-git install
```


[SIZE="3"]Removing Compiz Fusion from Git[/SIZE]

EX- If for some reason this doesent work for you just uninstall compiz from the repos and run this than reinstall copiz from repos

```
sudo compiz-git --uninstall

sudo apt-get remove compiz-git

sudo mv /etc/apt/sources.list /etc/apt/sources.list1

sudo apt-get update

sudo cp /etc/apt/sources.list1 /etc/apt/sources.list

sudo apt-get update
```

Or

EX- this is dirty and will leave traces like the icons for compiz settings manager in the system menu and you will have to delete yourself

```
sudo rm -rf /etc/compiz* > /dev/null 2>&1

sudo rm -rf /etc/xdg/compiz* > /dev/null 2>&1

sudo rm -rf /home/*/.compiz* > /dev/null 2>&1

sudo rm -rf /home/*/.gconf/apps/compiz* > /dev/null 2>&1

sudo rm -rf /root/.compiz* > /dev/null 2>&1

sudo rm -rf /usr/bin/compiz* > /dev/null 2>&1

sudo rm -rf /usr/bin/bcop > /dev/null 2>&1

sudo rm -rf /usr/bin/ccsm > /dev/null 2>&1

sudo rm -rf /usr/bin/emerald* > /dev/null 2>&1

sudo rm -rf /usr/bin/fusion-icon > /dev/null 2>&1

sudo rm -rf /usr/bin/gtk-window-decorator > /dev/null 2>&1

sudo rm -rf /usr/etc/compiz* > /dev/null 2>&1

sudo rm -rf /usr/etc/gconf/schemas/compiz* > /dev/null 2>&1

sudo rm -rf /usr/include/compiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/compiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/emerald* > /dev/null 2>&1

sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/libdecoration* > /dev/null 2>&1

sudo rm -rf /usr/lib/libemerald* > /dev/null 2>&1

sudo rm -rf /usr/lib/libcompiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/pkgconfig/compiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/pkgconfig/emerald* > /dev/null 2>&1

sudo rm -rf /usr/lib/pkgconfig/libcompiz* > /dev/null 2>&1

sudo rm -rf /usr/lib/pkgconfig/libdecoration* > /dev/null 2>&1

sudo rm -rf /usr/lib/pkgconfig/libemerald* > /dev/null 2>&1

sudo rm -rf /usr/share/compiz* > /dev/null 2>&1

sudo rm -rf /usr/share/bcop* > /dev/null 2>&1

sudo rm -rf /usr/share/ccsm* > /dev/null 2>&1

sudo rm -rf /usr/share/emerald* > /dev/null 2>&1

sudo rm -rf /usr/share/pkgconfig/bcop.pc > /dev/null 2>&1

sudo rm -rf /usr/local/bin/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/bin/bcop > /dev/null 2>&1

sudo rm -rf /usr/local/bin/ccsm > /dev/null 2>&1

sudo rm -rf /usr/local/bin/emerald* > /dev/null 2>&1

sudo rm -rf /usr/local/bin/fusion-icon > /dev/null 2>&1

sudo rm -rf /usr/local/bin/gtk-window-decorator > /dev/null 2>&1

sudo rm -rf /usr/local/etc/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/etc/gconf/schemas/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/include/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/emerald* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/libcompiz* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/libdecoration* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/libemerald* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/pkgconfig/emerald* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/pkgconfig/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/pkgconfig/libcompiz* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/pkgconfig/libdecoration* > /dev/null 2>&1

sudo rm -rf /usr/local/lib/pkgconfig/libemerald* > /dev/null 2>&1

sudo rm -rf /usr/local/share/compiz* > /dev/null 2>&1

sudo rm -rf /usr/local/share/bcop* > /dev/null 2>&1

sudo rm -rf /usr/local/share/ccsm* > /dev/null 2>&1

sudo rm -rf /usr/local/share/emerald* > /dev/null 2>&1

sudo rm -rf /usr/local/share/pkgconfig/bcop.pc > /dev/null 2>&1

sudo rm /usr/local/share/locale/*/LC_MESSAGES/*compiz*.mo > /dev/null 2>&1

sudo rm /usr/share/locale-langpack/*/LC_MESSAGES/compiz* > /dev/null 2>&1


sudo rm /usr/lib/window-manager-settings/libcompiz.so > /dev/null 2>&1

sudo rm /usr/lib/window-manager-settings/libcompiz.a > /dev/null 2>&1

sudo rm /usr/lib/window-manager-settings/libcompiz.la > /dev/null 2>&1

sudo rm /usr/local/lib/python2.5/site-packages/compiz* > /dev/null 2>&1
```


If you need any help here is the original forum [http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218)


 
[SIZE="3"]Mac Fonts
[/SIZE]
EX- This script will download and move the mac fonts to your fonts directory so you say i ran it and my fonts are still the same you have to right click your desktop go to change desktop background than click fonts and change the fonts to the mac fonts okay ps they include AppleGaramond Aquabase LITHOGRL Lucida GrandeLucida Maclucon MacGrand.

```
#!/bin/bash

wget http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz

tar zxvf macfonts.tar.gz

sudo mv macfonts /usr/share/fonts/

sudo fc-cache -f -v


```


[SIZE="3"]gDesklets[/SIZE]

EX- Much the same as Screenlets but for those of you who want to try it heres the code.

```
sudo apt-get install gdesklets gdesklets-data
```



**[SIZE="4"]Office Scripts[/SIZE]**


[SIZE="3"]Open Office 3 beta[/SIZE]

EX- for those of you that like to be on the cutting edge here is open office suns latest creation. To add this to your system menu you must right click applications than go to edit menu, go down to office, than click add, thank in command use this /opt/openoffice.org3/program/soffice, than make a name and comment than start it you will have to register then there you go.

```
wget http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=3.0.0beta

tar xzf ~/Desktop/OOo_3.0.0beta_20080429_LinuxIntel_install_en-US_deb.tar.gz -C ~/Desktop/

sudo dpkg -i ~/Desktop/BEA300_m2_native_packed-2_en-US.9301/DEBS/*.deb

rm -r ~/Desktop/BEA300_m2_native_packed-2_en-US.9301/

rm -r ~/Desktop/OOo_3.0.0beta_20080429_LinuxIntel_install_en-US_deb.tar.gz
```


[SIZE="3"]Open Office 2.4 transitions[/SIZE]

EX- This is for you fancy people and it will let you have cool transition effects in Open Office 2.4
```

sudo apt-get install openoffice.org-ogltrans
```


**[SIZE="4"]System Tools Scripts[/SIZE]**

[SIZE="3"]Ubuntu 8.10 Intrepid Ibix[/SIZE]

EX- the new ubuntu yes this is a beta but it fun to try note there still are bugs so dont blame me but if you want to try and btw dont stop the update install during the middle.

```
update-manager -d
```


[SIZE="3"]LXDE[/SIZE]

EX- while i have never tried this myself before now i have found that this is quite cool however installing is close to lg3d but... this one is a tad more difficult.

```
sudo gedit /etc/apt/sources.list
```

than add these lines at the very bottom

```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
``` 

Save and close

than 

```
sudo apt-get update
```

Now finally 

```
sudo aptitude install lxde
```

ok well your done now simply switch the session from the login screen of ubuntu.


[SIZE="3"]WIFI For Windows[/SIZE]

EX- sence i myself had issues with this i am posting a script for all oh you to get you belkin or other wireless cards working. The driver file should be on the disk you got with your card. ok here it goes

```
sudo apt-get install ndiswrapper-common

sudo apt-get install ndiswrapper-utlis-1.9

sudo apt-get install ndisgtk
```

once you do that than go to system prefernces and at the bottem there will be windows wireless drivers. Just located yours this may take some playing around and it might not work but its worth a shot please dont comment to much for help its pretty self explanitory.


[SIZE="3"]Virtual Box 2.0
[/SIZE]
EX- This well let you run other operating systems from within ubuntu such as windows or other linux os systems. So very helpfull. And also free. 

```
sudo wget http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb

sudo dkpg -i virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i385.deb

```

[SIZE="3"]Project Looking Glass[/SIZE]

EX- SORRY EVERYONE for the confusion and ive fix it now just try this is should work. Well ive played with the idea of using this for a while but one of the users commented and so i will show you how to install this easily.

```
 sudo apt-get install lg3d-core

```

Once you have done that than log out and click on sessions and change it to lg3d and there you go log in and have fun man.

[SIZE="3"]KDE 4.1[/SIZE] 

EX- Will let you use all your KDE stuff in Ubuntu aka different and cool. This will not install any kde applications in ubuntu so will not harm your current install.

Add this by going to system,administration,Sources,Third Party,Add. Then type this

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```
 
Then enter in the Terminal.

```
sudo apt-get install gtk-qt-engine-kde4
```


[SIZE="3"]Clean your Cache[/SIZE] 

EX- This will take your computers cache memory and wipe it allowing more disk space only really usefull if you are tight on space on your hardrive.

```
sudo apt-get autoclean
```


[SIZE="3"]Launchy[/SIZE]

EX- Quick launcher for windows and Ubuntu. Amazing saves time. Configure for better usage.

```
sudo wget http://downloads.sourceforge.net/launchy/launchy_2.1.1-1_i386.deb?modtime=1217200545&big_mirror=0

sudo dpkg -i launchy_2.1.1-1_1386.deb



```

[SIZE="3"]Flyback[/SIZE]

EX- This program is just like timemachine for mac it will backup all of your computer data it is reccomended that you have an external harddrive for this it took some of these instructions from ubuntu unleashed thank you and here they are. to run just go to applications system than flyback.

```
#!/bin/bash

sudo apt-get install python python-glade2 python-gnome2 python-sqlite3 rsync python-pysqlite2

wget http://ubuntu-debs.googlecode.com/files/flyback.tar.gz

tar zxvf flyback.tar.gz

cd flyback

./install
```


[SIZE="3"]GuFw[/SIZE]

EX- So im sure if you guys followed the hardy release you would have noticed that they installed this brand new great firewall in hardy .....yahhhhhh.....right....sure. Ok if it was me i thought the old one was fine bc it had a gui and all that. This new firewall is capable of numiourus new things though so out with the old and in with the new. This is a tool for those of you who arent terminal jockys and dont like the bleeping black dot, its a config gui for the new uncomplicated firewall.

```
sudo wget http://launchpad.net/gui-ufw/main/0.0.7/+download/gufw_0.0.7-all.deb

sudo dpkg -i gufw_0.0.7-all.deb 
```

[SIZE="3"]Guake[/SIZE]

EX- Lets you use extended terminal things such as multiple file types. It will let you run multiple scripts at once and let you edit multiple things.

```
sudo wget http://guake-terminal.org/releases/0.3/guake_0.3-1_i386.deb

sudo dpkg -i guake_0.3-1_i386.deb
```


[SIZE="3"]Check G-Mail[/SIZE]

EX- Allows you to check your gmail from an icon.

```
sudo apt-get install checkgmail
```



**[SIZE="4"]GAME[/SIZE]**


Wormux

EX- This will allow you to download and install the game wormux from source and play wormux online wormux is alot like the game worms but with computer logos like the penguin from linux have fun.

```
wget -O - http://download.gna.org/wormux/wormux-0.8.tar.bz2 | tar xj -C ~

sudo apt-get install build-essential libxml++2.6-dev libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsdl-gfx1.2-dev libsdl-net1.2-dev libcurl3-dev gettext

cd ~/wormux-0.8

./configure

make

sudo make install
```

For UNINSTALL

```

cd ~/wormux-0.8

sudo make uninstall
```


Maplestory 

EX- Sorry but this is not a script this is more of something very very usefull for help. One of my friends told me about maplestory i played it on windows got addicted etc... Than i got only on ubuntu no dual boot. So i thought crap i cant play maple because of gameguard OK here is how you get maple to work in ubuntu.PS WILL NEED A COPY OF WINDOWS 98 OR HIGHER

1. Go to the vmware site

2. Download the vmware entire for windows

3. Install by extracing to folder on home directory of desktop

4. Put the extracted folder in your home folder

5. Open up a terminal window

6. use the command cd to switch into the vmware directory EX- sudo cd vmware.0.06

7. Once in the folder use ./installer.sh or a similar command to run the insaller

8. Now go through the instller

8. Go to your applications menu and click vmware 

9. Install windows in VMWARE 

10. Install the vmware extras

11. Enable 3d acceleration

12. Download Maple client from Nexon

13. Start

14. Enjoy

... If you need help PM this is complicated.


WIIMOTE


EX- This will allow you to use your nintendo wii mote without modifcations on ubuntu as a mouse or keyboard have personally tested works very well

```
sudo wget http://getdeb.net/download/2887/0

sudo dkpg-i xwii_2.5-01~getdeb1_i386.deb
```

PS- When you want to run the program type xwii in the terminal it will ask for a number for a config chose the according one than press the red point on the back of your wii mote flashlights,lighters,and candles work for the sensor bar have fun.

**Internet**


Google Chrome

EX- Well for the last few months i have been busy with work and getting a new computer and gaming and such. I am now on windows and ubuntu and i have used Google chrome on windows. I thought it wouldn't be great but i like it. I have used it and i am an avid Firefox fan and will never leave but i use Google Chrome a lot and as of now there is no way to use it in Linux but using wine or a virtualiser so without further ado here is how to get Google chrome in ubuntu.

```

sudo wget http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb

sudo dkpg-i cxchromium_0.9.0-1_i386.deb
```

---

### Post by radagast1155 on 2008-05-20
you are king!
Bow down to the king!

---

### Post by 22flames on 2008-05-20
thanks man :)

---

### Post by 22flames on 2008-05-20
:-k

---

### Post by meazz1 on 2008-05-20
this is very helpful.

thanks

---

### Post by PuppyFromHell on 2008-05-20
First, the terminal is supposed to close automatically when the compiz script is finished correct?  Second, how would I run compiz after installing using the script?

---

### Post by 22flames on 2008-05-21
No the terminal is not supposed to close. And all you do to use that compiz is restart and its all installed over the old compiz.Fist make sure the new compiz is installed by going to system and preferences and than see if emerald appears in the list. If so it is installed now if you want to customize the new features click on system preferences and ccsm or compiz configure settings manager click the plug ins you want and that click extra in your appearance tab.

---

### Post by 22flames on 2008-05-21
:confused:

---

### Post by NEUR0M4NCER on 2008-06-01
Hi 22flames, thank-you so much for this, installing as I type. One quick request though: could you post back on [ Ubuntu Automatic Extra 12 plugins](http://ubuntuforums.org/showthread.php?t=744394), 'cause I was keeping an eye out there for a Hardy script to get compiz-git. I only found this thread after checking your profile. Others might not be so determined :).

Thanks again!




**edit**
Also, I know you say not to stop the script until it's finished, but it might also be wise to point out that it can take some time to download the git stuff, with no visual representation of progress - just in-case people get over-eager and think it's not working.

---

### Post by NEUR0M4NCER on 2008-06-01
Hah hah... and another thing (are you annoyed with me yet?)!

Will compiz-git auto update like the rest of the programs installed via Synaptic, or do we need to keep tabs on Compiz' progress and run the script again when updates are available? Either's fine, but just so I know.

... sorry to keep bothering you :)

Kind regards

---

### Post by NEUR0M4NCER on 2008-06-01
Uh oh... another one.

Installed, all seemed to work well. Restarted, but no extra effects in CCSM - I know they *should* be there, I saw them fly past during install, but can't find them anywhere - any ideas?



p.s. Emerald themes have installed, just missing Compiz plugins.

---

### Post by krsna on 2008-06-01
Hey there,

First of all thanks for creating such an easy to use post. Secondly there is a little issue - or something i cannot understand - happening. Here is the response from Terminal:

> benjamin@mati:~$ #!/bin/bash
benjamin@mati:~$ 
benjamin@mati:~$ sudo apt-get install python-notify python-feedparser python-pyvorbis python-pyogg python-eyed3 python-pysqlite2 python-gtk2 python-glade2 python-clutter python-pyvorbis python-imaging python-pyinotify python-imdbpy python-cairo-dev gtk-doc-tools python-cddb subversion
Reading package lists... Done
Building dependency tree        
Reading state information... Done
python-notify is already the newest version.
python-gtk2 is already the newest version.
python-glade2 is already the newest version.
python-imaging is already the newest version.
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev docbook docbook-dsssl docbook-to-man
  docbook-xsl gettext gnome-common intltool jade libapr1 libaprutil1 libc6-dev
  libclutter-0.6-0 libclutter-cairo-0.6-0 libclutter-gst-0.6-0
  libclutter-gtk-0.6-0 libosp5 libostyle1c2 libpq5 libsp1c2 libsvn1 libtool
  linux-libc-dev m4 openjade patch sp
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc psgml docbook-defguide jadetex docbook-dsssl-doc xalan fop
  libsaxon-java libxalan2-java cvs gettext-doc glibc-doc manpages-dev gcj
  gfortran fortran95-compiler libtool-doc diff-doc python-pyogg-dbg
  python-pysqlite2-dbg python-pyvorbis-dbg db4.6-util subversion-tools
Recommended packages:
  automaken docbook-xsl-doc-html docbook-xsl-doc-pdf docbook-xsl-doc-text
  docbook-xsl-doc libltdl3-dev python-chardet python-utidylib
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev docbook docbook-dsssl docbook-to-man
  docbook-xsl gettext gnome-common gtk-doc-tools intltool jade libapr1
  libaprutil1 libc6-dev libclutter-0.6-0 libclutter-cairo-0.6-0
  libclutter-gst-0.6-0 libclutter-gtk-0.6-0 libosp5 libostyle1c2 libpq5
  libsp1c2 libsvn1 libtool linux-libc-dev m4 openjade patch python-cairo-dev
  python-cddb python-clutter python-eyed3 python-feedparser python-imdbpy
  python-pyinotify python-pyogg python-pysqlite2 python-pyvorbis sp subversion
0 upgraded, 41 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.5MB of archives.
After this operation, 73.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.


So what's going on? And why does it say abort when i choose Y? Well basically i'd like to be able to play medias on 8.4. Thanks for any past and future tips.

B.

---

### Post by NEUR0M4NCER on 2008-06-01
> **NEUR0M4NCER said:**
> Uh oh... another one.

Installed, all seemed to work well. Restarted, but no extra effects in CCSM - I know they *should* be there, I saw them fly past during install, but can't find them anywhere - any ideas?



p.s. Emerald themes have installed, just missing Compiz plugins.

... solved. Removed Compiz & Fusion Icon entirely, as-well as compiz-git, and re-ran the script. You should post a link to the specific thread where the instructions are, there are good tips in there if it doesn't work.

Cheers

---

### Post by 22flames on 2008-06-17
Sorry guys i have been on windows for a while ehhhhhhhhhhhhhhhhh... gaming and all that so this program will not automatically update the programs through the synaptic you will have to check using the script be reloading the script... and no im not annoyed with you and yes i will update my old thread i had no idea people were actully still checking that i dont :confused: so here i go

---

### Post by 22flames on 2008-06-17
i always listen to what people want and this is like my project and its supposed to be easy for people to use im getting my ubuntu on as i would say lol... i will link this to that thread if you think it is that important when i was first working on this thread i thought about that i had to use that form a few times to so i will

---

### Post by 22flames on 2008-06-18
Edit- Added The Site Link To Orginal Fourms

---

### Post by 22flames on 2008-06-18
Edit- Added More Scripts

---

### Post by 22flames on 2008-06-19
EDIT- Added GuFw firewall tool

---

### Post by 22flames on 2008-06-20
EDIT- Now taking requests

---

### Post by 22flames on 2008-07-03
EDIT- Maplestory in ubutnu guide

---

### Post by 22flames on 2008-07-10
Edit-wiimote On Ubuntu

---

### Post by gaiterin on 2008-07-19
For Gufw:
Hi!
The web changed to [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/) and Launchpad
You can download 0.0.6 version, but the 25 July 2008, will release the 0.0.7!
Best regards.

---

### Post by 22flames on 2008-07-25
Thank you for the update
:)

---

### Post by 22flames on 2008-07-25
Updated the GUFW to the LATEST VERSION

---

### Post by 22flames on 2008-07-25
EDIT- Check GMAIL

---

### Post by 22flames on 2008-07-29
Edit Added Lauchy Launcher

---

### Post by Diabolis on 2008-07-29
Great thread, even when I won't be using most of this scripts, many people will find them useful.

---

### Post by 22flames on 2008-08-01
Thank you i can always use feedback :).

---

### Post by 22flames on 2008-08-01
EDIT- Added cache cleaning.

---

### Post by 22flames on 2008-08-01
EDIT- Added more compiz STUFF AKA. PLUGINS

---

### Post by 22flames on 2008-08-01
EDIT- Added KDE in ubuntu.

---

### Post by 22flames on 2008-09-29
Well this thread has been inactive for quite a while i think i will start adding some more installation scripts right now i am working on a google chrome script.

---

### Post by newsman1970 on 2008-09-29
Great post, you are the best. Because a rookie like me needs all the help, I can get to learn Linux, and how to use terminal to get things done. 

Thank you very much,:D

Now I have a request, I have been using UBUNTU v8.04 LTS desktop edition for 4 days now but I been reading for almost 2 weeks now, and in the 4 days I had format my hard drive 4 times so far because I kept making mistake and messing up the installation.

Moreover, one of the mistakes I did was trying to install Project Looking Glass or LG3D,
In addition, I could not get it installed, so the question is how I do that and what do I need to install first (like Java) now if I need to install Java first how do I do that. And I read this on some other post that I need OpenGL and its dependency first (I messed up my installation doing it). Now if I need that how to do it.
I know that I am asking for too much, so I apologize for that, and I hope you understand that I am still a rookie but I am a very fast learner and a good student.

Thanks,:D

---

### Post by 22flames on 2008-10-02
:D thanks for the reply and i will start working on it immeditly

---

### Post by 22flames on 2008-10-02
well btw im done the instructions are under the system scripts and your welcome in advanced.

PS- make sure you change in the log in screen to the write shell.

---

### Post by 22flames on 2008-10-02
added virtual box 2.0 installer instructions :)

---

### Post by 22flames on 2008-10-02
added compiz full screen fix script

---

### Post by newsman1970 on 2008-10-06
thank you very much 22flames, you'r a great help.
i will try the lg3d tonight and i will let you know.

thanks,:KS:KS:KS:KS:KS

---

### Post by newsman1970 on 2008-10-08
**hi, i used all the code for the lg3d but i could not get it to work can you please help me out here, this is what I am getting:**

(Reading database ... 138752 files and directories currently installed.)
Preparing to replace lg3d-jdk 1.6.0+b104 (using lg3d_jdk1.6.0_i686.deb) ...
Unpacking replacement lg3d-jdk ...
Preparing to replace lg3d-java3d 1.5.0 (using lg3d_java3d_1.5.0_i686.deb) ...
Unpacking replacement lg3d-java3d ...
Preparing to replace lg3d-core 1.0.0 (using lg3d-core_1.0.0_i686.deb) ...
/usr/share/lg3d/bin/remove-lg-from-gdm: line 15: /bin/arch: No such file or directory
Success. LG has been removed as a gdm session.
Unpacking replacement lg3d-core ...
Setting up lg3d-jdk (1.6.0+b104) ...

Setting up lg3d-java3d (1.5.0) ...

Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core



[B]and can you please explain how to log out and got to session and change to lg3d and log in. i could not understand what you mean by that is it with terminal or i have to log out the computer.

thanks[/B],:(

---

### Post by 22flames on 2008-10-09
ok srry i went to deep without explaining it to you my bad.

#  run the Synaptic Package Manager from the System/Administration menu,
# click on the Reload button and then
# Search for lg3d and mark the lg3d-core package for installation.
# click on the Apply button to download and install 

ok now when thats done

logout of ubuntu 

in the bottem left hand corner it should say like shutdown restart etc click on the arrow and switch to switch session chose lg3d from those than log into ubuntu as you usually would .... TELL ME HOW IT GOES:)

---

### Post by 22flames on 2008-10-09
Also just a word of advice as a experienced user at these forms and on my own... ive tried lg3d and well its not great use compiz it looks and functions better than project looking glass ever will

but its up to you:) good luck either way

---

### Post by newsman1970 on 2008-10-09
thanks 22flames for your reply, i just want to tried for my self and most likley i will take your advice.

thanks,:KS:KS:KS:KS:KS

---

### Post by lisantir5 on 2008-10-10
Great stuff!  I was looking for a command for install .deb files when I came across this.  I bookmarked the page for later review.  You should write a Tips/Tricks guide.  Thank you for your contributions.

---

### Post by 22flames on 2008-10-10
well honestly thank you for the comment alot of people just read and than do nothing no post no comment nothing and comments like yours make this worthwhile

---

### Post by celticbhoy on 2008-10-10
Just want to add my thanx, and support for your efforts. I have used a couple of the scripts now, the only one I have had bother with is lg3d, but that was more for a look than anything else.

Cheers mate!

---

### Post by celticbhoy on 2008-10-10
Just to let you know I got the same errors as newsman, even with the synaptic fix.

---

### Post by 22flames on 2008-10-10
EDIT from popular demand i have reserched and now fixed the script for lg3d so all of you guys here it is have funnnn...:KS

---

### Post by 22flames on 2008-10-10
EDIT WINDOWS WIRELESS DRIVERS yep thats write wireless for all you users that dont have it workin here is a shot that worked for me give it a go and tell me what you think the drivers will be on your install disk or your manufacturers website DO NOT ASK ME FOR DRIVERS.

---

### Post by celticbhoy on 2008-10-10
Typical, just sorted my lg3d when you chipped in with the new script. I have'nt tried your new script, but if anyone still gets the same problem, download the latest core from this link :-

[https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb](https://lg3d-core.dev.java.net/files/documents/1834/84267/lg3d-core_1.0.1_dev_i686.deb)

then install - should sort the problem

---

### Post by celticbhoy on 2008-10-11
Any chance of something for lxde ???

---

### Post by 22flames on 2008-10-11
wow you certainly keep me busy ill start now :) 

btw the new script will work no matter what bc of the ubuntu repos but you must switch the SESSION on the login screen.

---

### Post by 22flames on 2008-10-11
Done and have fun but note be carefull with installing different sessions sometimes you can get more than you bargin for such as kde it will install all of the kde packages and than in turn will screw up your clean ubuntu. :) good luck whatever you chose though man.

---

### Post by 22flames on 2008-10-11
EDIT under system i put how to update to intrepid ibix be carefull it is still a beta and do not blame me for problems :)

---

### Post by 22flames on 2008-10-12
bump for people looking for my thread

---

### Post by celticbhoy on 2008-10-13
Thanx for the lxde script, but now for the biggie. Can you bang up a script that will install metisse ????

---

### Post by linuxlab on 2008-10-26
Way Kewl, cheers from New Zealand, this was most helpful and now resides in my foxmarks for future use (I install nix* alot)...

thank you

---

### Post by 22flames on 2008-10-26
thanks for the comments everyone i think i will be moving a maybe restarting this thread due to the new intrepid relase. So guys unless something new comes out other than request i probobly wont be addin.

---

### Post by 22flames on 2009-03-22
i figure im gona kick this bad boy back up to the top just so you all can use it (:

---

### Post by Layman's terms on 2009-03-24
22flames,

I'm one of the lead developers for Entertainer. The script that you've written uses very dated svn code that is unlikely to work on a current Ubuntu release. Would you mind updating the script, or at the very least, direct users straight to [http://wiki.entertainer-project.com/wiki/StartUpGuide?](http://wiki.entertainer-project.com/wiki/StartUpGuide?) Then your readers could benefit from some instructions straight from the source.

Thanks for taking the time to write these things up. I'm sure new users in the forums appreciate this kind of help.

---

### Post by 22flames on 2009-06-13
fixed entertainer sorry about that:p

---

### Post by 22flames on 2009-07-15
bump because i just go the new ubuntu and im going to start scripting again :p

---

### Post by 22flames on 2009-12-27
Bump for adding using an iPod touch on linux

---

### Post by tru infini on 2010-05-20
I have a quick question: My Ubuntu computer is hardly ever connected tot he internet and was wondering if you could post a tutorial on downloading programs onto a flash drive then telling the computer to install it from said flash drive so i can get my packages that way instead of lugging my tower across the valley to my friends work place to hook up to the internet to get the programs and updates that I need.

---

