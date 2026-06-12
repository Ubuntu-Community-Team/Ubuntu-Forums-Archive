---
title: "My Breezy setup sequence that worked..."
date: 2005-11-21
forum: Testimonials &amp; Experiences
---

### Post by flatliner2005 on 2005-11-21
Step 1:
    Partitioned 20Gb Disk as follows:
    Partition 1     Primary     455Mb      reiserfs     /           bootflagon
    Partition 5     Logical      7Gb          reiserfs     /usr
    Partition 6     Logical      2.6Gb       reiserfs     /var
    Partition 7     Logical      1.12Gb     swapfile
    Partition 8     Logical      463Mb      reiserfs     /tmp
    Partition 9     Logical      7.04Gb     reiserfs     /home

Step 2:
Installed Ubuntu from the CD

Step 3:
After everything is installed, setup X.
(I edited the .inf monitor driver on Windows and recorded the Horiz and Vert Sync ranges).
Log out of Ubuntu X desktop
Press CTRL + ALT + F1 to switch to console
Login
```
sudo dpkg-reconfigure xserver-xorg
```
Configured X to work with my Nvidia card and Monitor and Microsoft Internet Keyboard (microsoftinet).
```
sudo killall gdm
sudo gdm &
``` <<I did this to start gdm as a background process
so I could log out of the console later (too security conscious to leave a console session logged on).

Step 4:
Configure APT sources. I personally like Main, Restricted, Universe and Multiverse setup for my repositories. Depending on your view of using non-free software, you may choose to do things differently here:

```
sudo nano -w /etc/apt/sources.list
```

My sources.list looks like:

```
deb http://gb.archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main universe multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main universe multiverse restricted
deb http://security.ubuntu.com/ubuntu breezy-security main universe multiverse restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main universe multiverse restricted
```

Run Synaptic Package Manager
Select Settings from the menu
Select Repositories
Check Binary and Source for Breezy, Updates, Security Updates all say:
    Officially supported
    Community maintained (Universe)
    Non-free (Multiverse)
    Restricted copyright

Click OK
Reload
Exit

Wait for Update Manager to update and then apply all updates.

Step 5:
Install the optimised version of the kernel for my machine:
I have an AMD Athlon 2500XP (Barton core).

Start Synaptic
Search 'linux-image'
Select linux-image-k7
Apply

Step 6:
Reboot! (who said you didn't need to reboot in Linux!!!)

Step 7:
After rebooting into Ubuntu using the k7 version of the 2.6 kernel I uninstalled the old one (I like my system clean, however this is not required).

Step 8:
Install the NVidia drivers

Start Synaptic
Search nvidia
Select linux-restricted-modules-2.6.12-9-k7, nvidia-glx, nvidia-kernel-common, nvidia-settings.
Apply
Exit

Start Terminal
sudo dpkg-reconfigure xserver-xorg
Change "nv" driver to "nvidia"
De-select GLCore and dri
Select glx
Leave the rest as it was

Now you can either stop and restart the X server (see step 3 above) or simply reboot.

Step 9:
Install Java (Sun)

Download Java 1.5 for Linux [here](http://java.com/en/download/linux_manual.jsp).
Save to /home/your_username_here
Start Terminal
```
cd /home/your_username_here
sudo cp jre-1_5_0_05-linux-i586.bin /usr/local
cd /usr/local
sudo chmod a+x jre-1_5_0_05-linux-i586.bin
sudo ./jre-1_5_0_05-linux-i586.bin
```

To activate in Firefox:
```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so .
sudo update-alternatives --config java
```
Select the Sun version of java when it asks you to (/usr/local/jre1.5.0_05/bin/java).
NOTE: Make sure that you put a space and then the . after .so in the above example. The . says that you want the symbolic link created in the current directory.

Open Firefox and visit [here to test everything is working ok](http://java.com/en/download/help/testvm.xml)

Step 10:
Add FlashPlayer support:
Now, depending on your views of non-free software, this can be achieved one of two ways. The first method is to install the non-free version. To do this you must have MULTIVERSE repositories enabled in APT (see Step 4).

Start Synaptic
Search "flash"
Select flashplugin-nonfree
Apply
Exit

Close all existing open Firefox windows. Open a new window and visit [here to check that the installation is working correctly](http://www.macromedia.com/go/flashplayerversion)

The second method is to install gplflash. As I didn't perform this I will not attempt to describe it, however there is an excellent HOWTO at [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-29ce85c5f75a6380ed26f1e828c343e54074d6e0](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-29ce85c5f75a6380ed26f1e828c343e54074d6e0)

AND FINALLY.....
Step 11:
How to install the greatest browser on earth - Opera (well IMHO anyway!)

First shoot off to the Opera.com website and download the Ubuntu Breezy version. [http://www.opera.com/download/?platform=linux](http://www.opera.com/download/?platform=linux)
Save to /home/your_username_here directory.

Then using dpkg, install
```
sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
```
You may get messages saying that there are unsatified dependencies. If so, fire up Synaptic and select Edit from the menu, then Fix Broken Packages. Click Apply and wait.

Opera is now partially installed. The following information is a direct reproduction of what is shown at [https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera](https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera). I only show it here to show exactly what I did to get my system up and running how I wanted it. If the authors of [https://wiki.ubuntu.com](https://wiki.ubuntu.com) object, I will of course remove.

To add the Opera icon to the main GNOME 'Applications' menu:
```
sudo gedit /usr/share/applications/opera.desktop
```
Paste the following into the GEdit window:
```
[Desktop Entry]
Encoding=UTF-8
Name=Opera Web Browser
GenericName=Web Browser
Comment=Simply the Best Internet Experience
Exec=opera %u
Terminal=false
MultipleArgs=true
Type=Application
Icon=/usr/X11R6/include/X11/bitmaps/opera.xpm
Categories=Application;Network
MimeType=text/html;image/gif;image/jpeg;image/png
```
Click File, then Save, then Quit.

Start Terminal
```
mkdir ~/.opera
gedit ~/.opera/filehandler.ini
```

Paste the following into the GEdit window:
```
Opera Preferences version 2.0
; Do not edit this file while Opera is running
; This file is stored in UTF-8 encoding
[Settings]
Default File Handler=gnome-open ,1
Default Directory Handler=gnome-open ,1
```
Click File on the menu, then Save, then Quit

At this point I differ to the Wiki. Choose which ever method works for you.
Next is to install the various different motif packages.

Start Synaptic
Search for "motif"
Scroll down and select lesstif2, libmotif3 and motif-clients
Click Apply
Exit

Now, the "operamotifwrapper-3" error.... (found at [http://www.ubuntuforums.org/showthread.php?t=74667](http://www.ubuntuforums.org/showthread.php?t=74667))
Start Terminal
```
sudo nano -w /etc/ld.so.conf
```
Add the following line:
```
/usr/X11R6/lib
```
Press CTRL+X, then press 'y' and then press Enter to save.

NOTE: I tried the above using gedit and the process failed. After deleting the ld.so.conf file and starting again with nano, it worked! Anyone care to guess why?

Next, back at the terminal:
```
sudo ldconfig
```

Go fire up Opera from the GNOME Applications / Internet menu.
If all is good, Opera SHOULD fire up.
To enable Java in Opera:
In the Tools, Preferences menu, go Advanced Tab, and select Content.
Press the 'Java Options' button.
If you have installed Java in the same place I did, enter /usr/local/jre1.5.0_05/lib/i386/ in the box and click Validate Java Path to check.
Java should now be working! To check, visit [here to test everything is working ok](http://java.com/en/download/help/testvm.xml)

Flash should already be enabled (Opera is using Firefox plugins!). To check visit [here to check that the installation is working correctly](http://www.macromedia.com/go/flashplayerversion)

I hope this is helpful to someone.

---

### Post by Irony on 2005-11-22
Good stuff. It would go well in Tips and Tricks sections.

---

