---
title: "My installation experience of Hardy (not much difference from gutsy)"
date: 2008-06-27
forum: Testimonials &amp; Experiences
---

### Post by guiliker on 2008-06-27
This is my experience of how to get a hassle free working Hardy Heron from the ubuntu-8.04-alternatei386.iso file available from [http://releases.ubuntu.com/8.04/](”http://releases.ubuntu.com/8.04/”)

**Hardware:**
Motherboard: Intel Desktop DQ965CO
Form Factor: MicroBTX (10.40x10.50inches)
Processor: E6300 1.86GHz L2=2MB FSB=1066 BIOS=4462
RAM: 1GB
Chipset: Express DQ965
Audio: 6-channel (5.1) SigmaTel STAC9227 audiocodec
Video: Intel GMA 3000
LAN: Intel 82566DM Gigabit Ethernet Controller

So on to the Software!!!

**Open Terminal and type:**
```
sudo gedit /etc/apt/sources.list
```
Copy and paste following in the end of the file the below:
```
## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main 
```
save the document and close, then in Terminal type:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
```
in order to receive the appropriate key. 

Finally in Terminal type one command at a time:
```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
sudo apt-get install gstreamer0.10-pitfdll
sudo apt-get install w32codecs
sudo apt-get install libdvdcss2
sudo apt-get install sun-java6-plugin
sudo apt-get install flashplugin-nonfree
sudo apt-get install liblame0
sudo apt-get install mozilla-plugin-vlc
sudo apt-get install vlc-plugin-pulse
sudo apt-get install mozilla-firefox-adblock
sudo apt-get install msttcorefonts
sudo apt-get install rar unrar
sudo apt-get install p7zip-full
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter libflashsupport
sudo apt-get install compizconfig-settings-manager fusion-icon
sudo apt-get install dvdrip dvdauthor
sudo apt-get update
sudo apt-get upgrade
```

This could take some time as the “upgrade” command will install ALL software updates since the initial release.

To add the better **totem-xine player** as default totem player 
Open Terminal and type:
```
sudo apt-get install totem-xine
sudo update-alternatives --config totem
```
choose 2 when asked.

Installing **Adobe Reader** instead of Evince, Xpdf or Document Viewer
Open terminal and type:
```
sudo apt-get install acroread
sudo apt-get install acroread-plugins acroread-escript mozilla-acroread
```

Go to any .pdf file and right click. Select Properties>Open With and select “Adobe Reader” all .pdf files will automatically open with Adobe Reader from now on with a double click.

**Installing Real Player 11 Gold and Configuring Mozilla Plugin for Firefox 3.0 browser.**
Download Real Player 11 Gold from: [http://www.real.com]("http://www.real.com") to the Desktop

Open terminal and type: 
```
cd ~/Desktop
chmod 770 RealPlayer11GOLD.bin
sudo ./RealPlayer11GOLD.bin
```
Use the following default installation directory during the installation: 
```
/opt/real/RealPlayer
```
The installer will copy the files and create menu shortcuts. Then type the following in Terminal: 
```
cd /usr/lib/firefox-addons/plugins
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/. 
```
Open Firefox and type about:plugins in the address bar. Scroll down and look for the following entry. 
```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
File name: /opt/real/RealPlayer/mozilla/nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008
```
If found, your Real Player Plugin is installed properly! 
Delete RealPlayer installer file from Desktop.

**Change the splash screen colour **
Originally a brownish colour to match the Ubuntu theme, it does not quite fit with other themes and you might want to change it. 
Open Terminal and type:
```
sudo gedit /etc/gdm/gdm.conf
```
About two-thirds of the way down you will see the lines: 
```
BackgroundColor=#dab082
GraphicalThemedColor=#dab082[/CODE}
Change it to what you like. For all black, use hexadecimal code: 
[CODE]BackgroundColor=#000000
GraphicalThemedColor=#000000
```
for other codes see [here](”http://www.berthou.com/us/2007/10/15/hexadecimal-color-conversion-cube/”) or google...
Save the file and close.

**Enabling NUM LOCK at boot** 
The Default behavior is for the NUM LOCK key to be off. To switch on:

Open Terminal and type:
```
sudo apt-get install numlockx
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
sudo gedit /etc/gdm/Init/Default
```

Scroll down to the end of the file, and above the line that says "exit 0" add the following: 
```
if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx on 
fi
```
Save the file and close.
Next time you reboot, your NUM LOCK should default to "on." 

IF you dual boot like me with WinXP Pro Sp3 (for the time being at least) then you may want to **automount your Windows Partition** to the Desktop, if so this is how:

Open Terminal and type:
```
 sudo apt-get install ntfs-config
```

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). And then run the program from Applications > System Tools

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Enjoy your automounted NTFS Drives courtesy of [Joeb454](”http://ubuntuforums.org/showthread.php?t=785263”)

IF you want to test other Operating Systems or still want Windows without dual-booting then **VMWare** could be the solution.

Get VMWare Server serial number(s) from [http://register.vmware.com/content/registration.html](”http://register.vmware.com/content/registration.html”)

Make sure that the numbers on the web download command (wget) match the latest build! Visit [here](”http://www.vmware.com/download/server/”) to check. X.X.X before the dash refer to version number and XXXXX refer to the build number.

Open Terminal and type:
```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd
mkdir vmware
cd ~/vmware
wget http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz 
tar -vxzf Vmware-server-1.0.6-91891.tar.gz
cd vmware-server-distrib
sudo ./vmware-install.pl
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

Follow the default options is mainly the best policy unless you know otherwise. Entering the serial number when required. For screenshots have a look at [http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](”http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html”)

After some updates and an upgrade to the Kernal VMWare Server needs to be reconfigured:
```
cd ~/vmware
sudo vmware-config.pl
```

To remove VMWare Server:
Open Terminal and type:
```
sudo vmware-uninstall.pl
```

Issues with VMWare Server that I've experienced:

USB automounts

Open Terminal and type:
```
sudo mount -t usbfs none /proc/bus/usb
sudo gedit /etc/fstab
```

Copy + Paste the following:
```
usbfs  /proc/bus/usb  usbfs  auto  0  0
```
Save and close the file.

For info refer to: [http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823](”http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823”)

To **share files** between your Host Ubuntu machine and your Guest WinXP, this is what I've done.

Followed the video at: [http://www.youtube.com/watch?v=EP8aXu7iSsg&feature=related](”http://www.youtube.com/watch?v=EP8aXu7iSsg&feature=related”) this has been the most successful way I've found in Hardy, for me at least.

However on the install of Samba I received the following message within the Terminal:
```
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------

The following line will be added to your /etc/inetd.conf file:



#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd



If you are indeed using xinetd, you will have to convert the

above into /etc/xinetd.conf format, and add it manually. See

/usr/share/doc/xinetd/README.Debian for more information.

-----------------------------------------------------------
```

So I did the following:

Open Terminal and type:
```
sudo gedit /etc/inetd.conf
```

Copy + Paste the following into the file:
```
#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
```

Save the file and close

Returning to Terminal, type:
```
sudo apt-get install xinetd
cd ~/vmware
sudo vmware-config.pl
```

selecting options to reconfigure the subnets

I like the **Mac4Lin themes** and this is how I got them to work in Hardy

In your Home directory create a folder to place all the files in and download the following:
All four files from: [http://sourceforge.net/projects/mac4lin](”http://sourceforge.net/projects/mac4lin”)
The Shere-Khan-X mouse theme from:[http://www.gnome-look.org/content/show.php/Shere+Khan+X?content=57588](”http://www.gnome-look.org/content/show.php/Shere+Khan+X?content=57588”)

On the right click menu select “extract here”on all 3 of the tar.gz files from mac4lin
Go to Preferences > Appearance > Install
Select the folder where you downloaded the files to > Mac4Lin_v0.4 > GTK Metacity Theme and highlight all 4 installation files and select Open
Then select “Install”
Select the folder where you downloaded the files to > Open the Shere_Khan_X tar.gz installation file
Select “Customise” and select the themes on each menu
You may need to log out and log in

**For AWN** 

NOTE: if you do install AWN and get rid of the gnome-applets then the command F2+Alt that some tutorials/fixes/forum posts will not work!!!

Open a Terminal and type:
```
sudo apt-get install awn-manager-trunk awn-extras-applets-trunk libawn0-dbg-trunk 
```

Then follow the tips at [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](”http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml”)

I have encountered a bug with the volume applet details of which can be seen here [https://bugs.launchpad.net/awn-extras/+bug/243017/](”https://bugs.launchpad.net/awn-extras/+bug/243017/”)


IF you chose to use **grub** at installation you can find it useful to change the grub time (I have 30 seconds)or delete old entries.

Open Terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
make changes, save and close.
WARNING any changes made to this and you don't know what you're doing could lead to grub failure!!!
for screenshots have at look at [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](”http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/”)


instructions compiled from: 
1. [http://ubuntuguide.org/wiki/Ubuntu:Hardy](”http://ubuntuguide.org/wiki/Ubuntu:Hardy”)
2. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](”http://ubuntuguide.org/wiki/Ubuntu:Gutsy”)
3. [http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](”http://packages.ubuntu.com/hardy/ubuntu-restricted-extras”)

---

### Post by wolfen69 on 2008-06-27
nice write up. however, i myself would not bother doing the codecs one at a time. ```
sudo apt-get install mozilla-mplayer vlc
``` gives me all the codecs. plus i remove totem and totem-mozilla. but to each his/her own. i'm sure some people will find your write up useful. good job.

---

### Post by guiliker on 2008-06-27
Thanks for your comment wolfen69. I have used mplayer before in Gutsy but I don't think it's any better than totem-xine. My preference is VLC but unfortuneatly you can never manage with just ONE media player!

---

### Post by guiliker on 2008-06-27
Something I forgot!

It makes things a bit simpler when looking for networked files/folders/drives if the Samba workgroup is changed from the default “workgroup” (may be a hangover from the pre-XP days?!?) to “MSHOME” or whatever your workgroup is in your other OS.

Open Terminal and type: 
```
sudo gedit /etc/samba/smb.conf
```

Edit the line: 
```
workgroup = WORKGROUP
```

Change it to the name of your actual workgroup name. For example, my workgroup is MSHOME, so I changed the line to: 
```
workgroup = MSHOME
```

Save the file and close.
```
sudo /etc/init.d/samba restart
```
or do a manual machine restart.

ALSO BIGGIE which I can't believe I forgot to write up! Hardy doesn't seem able to “find” a working driver for my monitor. I get a default screen of 1280x768 @60 (or something very similar) which is too slow a refresh rate and is just hard to read. On attempting the code ```
sudo dpkg-reconfigure xserver-xorg
``` I'd read that that it would “re-find” the correct drive but alas nothing. Instead I manually compiled the X configuration for the chipset as above with a Belinea 10-17-28 17” LCD monitor.

This is how:

Open Terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```

I replaced the sections entitled “Device”, “Monitor” and “Screen” so they had the following information:

```
Section "Device"

	Identifier	"Intel Corporation 82Q963/Q965 Integrated Graphics Controller" 

	Boardname	"Intel 965" 

	Busid		"PCI:0:2:0" 

	Driver		"i810" 

	Screen	0 

	Vendorname	"Intel" 

EndSection



Section "Monitor"

	Identifier	"Belinea10172" 

	Vendorname	"Belinea" 

	Modelname	"Belinea 10 17 28" 

	Horizsync	30.0-83.0 

	Vertrefresh	50.0-77.0 

  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync 

  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync 

  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync 

  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync 

  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync 

  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync 

  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync 

  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync 

  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync 

  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync 

  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync 

  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync 

  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync 

  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync 

  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync 

  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync 

  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync 

  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync 

  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync 

  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync 

  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync 

	Gamma	1.0 

EndSection



Section "Screen"

	Identifier	"Default Screen" 

	Device		"Intel Corporation 82Q963/Q965 Integrated Graphics Controller" 

	Monitor		"Belinea10172" 

	Defaultdepth	24 

	SubSection "Display" 

		Depth	24 

		Virtual	1280	1024 

		Modes		"1280x960@60"	"1280x1024@60"	"1280x1024@75"	"1280x960@75"	"1152x864@75"	"1400x1050@60"	"1024x768@60"	"1400x1050@75"	"1024x768@70"	"1600x1200@65"	"1024x768@75"	"1600x1200@60"	"832x624@75"	"1792x1344@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60" 

	EndSubSection 



EndSection

```

I think that's it! All I want to do now is to understand samba, look into playing games like Diablo 2 and Divine Divinity on Ubuntu through virtualisation and to work out why the “restart” just hangs on sigkill rather than actually restarting the machine.

---

### Post by wolfen69 on 2008-06-27
thanks for taking the time to write all that. this is what makes the ubuntu community great.

---

