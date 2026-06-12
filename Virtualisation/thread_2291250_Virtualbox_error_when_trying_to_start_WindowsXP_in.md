---
title: "Virtualbox error when trying to start WindowsXP in virtualbox"
date: 2015-08-18
forum: Virtualisation
---

### Post by AbleTassie on 2015-08-18
I get the following error: "The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.  Please reinstall the kernel module by executing 

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

"
How do I fix this?

Thanks,

A.

---

### Post by bashiergui on 2015-08-18
The solution is in this thread
[http://askubuntu.com/questions/498900/vbox-on-14-04-kernel-driver-not-installed-rc-1908](http://askubuntu.com/questions/498900/vbox-on-14-04-kernel-driver-not-installed-rc-1908)

---

### Post by AbleTassie on 2015-08-18
**Thanks Bashiergui, I tried the fix below at the link you gave me, but it did not work, any other suggestions?**

 The fix for 14.04 is indeed different, but not that different:
  sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
  The install virtualbox-dkms command was actually failing applying the 13.10 fix. By fully purging the package things got back to normal.
  **Update** [17-01-2015]: In the latest iteration of this bug a restart to the system is required between the apt-get remove command and the second apt-get install.

---

### Post by AbleTassie on 2015-08-18
I also tried to execute **sudo/etc/init.d/vboxdrv setup** and **sudo /etc/init.d/vboxdrv setup** (with a space),  after the dkms commands above. But that did not help either, because the command did not execute.

A.

---

### Post by AbleTassie on 2015-08-20
I get the Terminal Error message below when I try to execute the last terminal command at the link you gave me


\Error! Bad return status for module build on kernel: 3.19.0-26-generic (x86_64)
Consult /var/lib/dkms/virtualbox/4.3.10/build/make.log for more information.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules   

             * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.

---

### Post by howefield on 2015-08-20
Thread moved to the "*Virtualisation*" forum.

---

### Post by Novitk on 2015-08-23
I have the same problem and I guess it's related to proprietary nvidia driver. I have no solution, but a workaround. Just remove everything related to Virtualbox. Then install the .deb file from Virtualbox site. It worked for me.

---

### Post by SeijiSensei on 2015-08-24
Or, better yet, follow the instructions for "Debian-based Linux distributions" and add the Oracle PPA to your system.  Then your version of VirtualBox will be automatically updated when new releases come out.

---

### Post by v3.xx on 2015-08-24
> **Novitk said:**
> I have the same problem and I guess it's related to proprietary nvidia driver. I have no solution, but a workaround. Just remove everything related to Virtualbox. Then install the .deb file from Virtualbox site. It worked for me.

This seems to be working for some people.

[http://ubuntuforums.org/showthread.php?t=2291832&p=13343902&viewfull=1#post13343902](http://ubuntuforums.org/showthread.php?t=2291832&p=13343902&viewfull=1#post13343902)

---

### Post by slickymaster on 2015-08-24
> **SeijiSensei said:**
> Or, better yet, follow the instructions for "Debian-based Linux distributions" and add the Oracle PPA to your system.  Then your version of VirtualBox will be automatically updated when new releases come out.

+1

---

### Post by AbleTassie on 2015-08-25
> **Novitk said:**
> I have the same problem and I guess it's related to proprietary nvidia driver. I have no solution, but a workaround. Just remove everything related to Virtualbox. Then install the .deb file from Virtualbox site. It worked for me.

Thanks to everybody,

Novitk, [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"), v3.xx, slickymaster,

I downloaded Virtualbox 5.0 from the Virtualbox website (ie., "Ubuntu 14.04 ("Trusty") / 14.10 ("Utopic") / 15.04 ("Vivid")  [AMD64]("http://download.virtualbox.org/virtualbox/5.0.2/virtualbox-5.0_5.0.2-102096%7EUbuntu%7Etrusty_amd64.deb")" from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) ) and checked the SHASUM256, which matched. But when I try to install the package with Gdebi package installer I get:

Error: Breaks existing package 'virtualbox' that conflict: 'virtualbox'. But the home/abletassie/virtualbox2/virtualbox-5.0_5.0.2-102096~Ubuntu~trusty_amd64.deb provides it via 'virtualbox'.

There is no other virtualbox installed as of now that I can see, but when I search under virtualbox in the home folder, I get many hits including:    virtualbox-qt_4.3.10-dfsg-1ubuntu5_amd64.deb which I think I downloaded, installed then uninstalled previously (path    

/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/var/cache/apt/archives/virtualbox-qt_4.3.10-dfsg-1ubuntu5_amd64.deb) 

AND

   virtualbox-dkms_4.3.10-dfsg-1ubuntu5_all.deb (path

   
/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/proc/self/fd/16/var/cache/apt/archives/virtualbox-dkms_4.3.10-dfsg-1ubuntu5_all.deb)                    



So it looks like there is some kind of conflict.

Any comments from anybody would be welcomed. Maybe I should do a clean install of Lubuntu again.                       

Thanks,

A.

---

### Post by slickymaster on 2015-08-26
In order to be able to upgrade Virtual Box to a higher major release you'll have to remove the kernel modules and applications of your older version first. Since this will not affect your existent virtual machines why don't you try to```
sudo apt-get purge virtualbox-4.3
```

---

### Post by AbleTassie on 2015-08-26
> **slickymaster said:**
> In order to be able to upgrade Virtual Box to a higher major release you'll have to remove the kernel modules and applications of your older version first. Since this will not affect your existent virtual machines why don't you try to```
sudo apt-get purge virtualbox-4.3
```

Hello Slickymaster,

When I try that terminal command I get back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package virtualbox-4.3
E: Couldn't find any package by regex 'virtualbox-4.3'

So it looks like there is no installed virtualbox 4.3, just files in the archives.

ANY SUGGESTIONS YOU OR ANYBODY ELSE HAS WILL BE WELCOMED.

Thanks,

A.

---

### Post by slickymaster on 2015-08-27
Can you please post back here the full output you get from```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install virtualbox-5.0
```

---

### Post by AbleTassie on 2015-08-27
> **slickymaster said:**
> Can you please post back here the full output you get from```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get install virtualbox-5.0
```

Thank you Slickymaster, here it is as well as a preliminary installation attempt result.

                    **    able@ableNotebook:~$ sudo apt-get autoclean **
 [sudo] password for able:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Del linux-libc-dev 3.13.0-61.100 [773 kB] 
 Del libpam-winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [25.9 kB] 
Del firefox-locale-en 40.0+build4-0ubuntu0.14.04.1 [677 kB] 
 Del samba 2:4.1.6+dfsg-1ubuntu2.14.04.8 [839 kB] 
 Del openssh-client 1:6.6p1-2ubuntu2.2 [564 kB] 
 Del python-samba 2:4.1.6+dfsg-1ubuntu2.14.04.8 [882 kB] 
 Del firefox 40.0+build4-0ubuntu0.14.04.1 [40.6 MB] 
 Del samba-common 2:4.1.6+dfsg-1ubuntu2.14.04.8 [157 kB] 
 Del winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [399 kB] 
 Del samba-vfs-modules 2:4.1.6+dfsg-1ubuntu2.14.04.8 [208 kB] 
 Del samba-dsdb-modules 2:4.1.6+dfsg-1ubuntu2.14.04.8 [219 kB] 
 Del chromium-codecs-ffmpeg-extra 43.0.2357.130-0ubuntu0.14.04.1.1092 [860 kB] 
 Del libnss-winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [12.3 kB] 
 Del samba-common-bin 2:4.1.6+dfsg-1ubuntu2.14.04.8 [488 kB] 
 
**able@ableNotebook:~$ sudo apt-get autoremove** 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be REMOVED: 
   gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers 
   hyphen-en-us libchromaprint0 libgsoap4 libgstreamer-plugins-bad1.0-0 
   libgstreamer-plugins-good1.0-0 libgtkglext1 libopencv-calib3d2.4 
   libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4 
   libopencv-flann2.4 libopencv-highgui2.4 libopencv-imgproc2.4 
   libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4 
   libopencv-video2.4 libqt4-opengl libreoffice-help-en-gb 
   libreoffice-help-en-us libreoffice-l10n-en-gb libreoffice-l10n-en-za libsbc1 
   libsrtp0 libtbb2 libvncserver0 mythes-en-au openoffice.org-hyphenation 
   virtualbox 
 0 upgraded, 0 newly installed, 31 to remove and 12 not upgraded. 
 After this operation, 153 MB disk space will be freed. 
 Do you want to continue? [Y/n] y 
 (Reading database ... 178368 files and directories currently installed.) 
 Removing gstreamer1.0-plugins-bad-faad:amd64 (1.2.4-1~ubuntu1) ... 
 Removing gstreamer1.0-plugins-bad-videoparsers:amd64 (1.2.4-1~ubuntu1) ... 
 Removing hyphen-en-us (2.8.6-3ubuntu2) ... 
 Removing libchromaprint0:amd64 (1.1-1) ... 
 Removing virtualbox (4.3.10-dfsg-1ubuntu5) ... 
  * Stopping VirtualBox kernel modules                                    [ OK ]  
 Removing libgsoap4:amd64 (2.8.16-2) ... 
 Removing libgstreamer-plugins-bad1.0-0:amd64 (1.2.4-1~ubuntu1) ... 
 Removing libgstreamer-plugins-good1.0-0:amd64 (1.2.4-1~ubuntu1) ... 
 Removing libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libgtkglext1 (1.2.0-3.1fakesync3) ... 
 Removing libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libqt4-opengl:amd64 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1) ... 
 Removing libreoffice-help-en-gb (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-help-en-us (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-l10n-en-gb (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-l10n-en-za (1:4.2.8-0ubuntu1) ... 
 Removing libsbc1:amd64 (1.1-2ubuntu2) ... 
 Removing libsrtp0 (1.4.5~20130609~dfsg-1) ... 
 Removing libvncserver0:amd64 (0.9.9+dfsg-1ubuntu1.1) ... 
 Removing mythes-en-au (2.1-5.4) ... 
 Removing openoffice.org-hyphenation (0.7.1) ... 
 Removing libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libtbb2 (4.2~20130725-1.1ubuntu1) ... 
 Processing triggers for libc-bin (2.19-0ubuntu6.6) ... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
                        
**able@ableNotebook:~$ sudo apt-get install virtualbox-5.0 **

 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Unable to locate package virtualbox-5.0 
 E: Couldn't find any package by regex 'virtualbox-5.0'


As an aside, I started to install virtualbox5.0 (using Gdebi package  installer) that I downloaded from the virtualbox website a couple days  ago ([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  ). The file is virtualbox-5.0_5.0.2-102096~Ubuntu~trusty_amd64.deb .  This time trying the installation I got no error when I started the  installation process, but a password dialogue box came up that warned  about trustworthiness & security. So I thought I'd wait a while to  see what people here, including Slickymaster say about the installation.

Thank you,

Able

---

### Post by slickymaster on 2015-08-28
> **AbleTassie said:**
> Thank you Slickymaster, here it is as well as a preliminary installation attempt result.

                    **    able@ableNotebook:~$ sudo apt-get autoclean **
 [sudo] password for able:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Del linux-libc-dev 3.13.0-61.100 [773 kB] 
 Del libpam-winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [25.9 kB] 
Del firefox-locale-en 40.0+build4-0ubuntu0.14.04.1 [677 kB] 
 Del samba 2:4.1.6+dfsg-1ubuntu2.14.04.8 [839 kB] 
 Del openssh-client 1:6.6p1-2ubuntu2.2 [564 kB] 
 Del python-samba 2:4.1.6+dfsg-1ubuntu2.14.04.8 [882 kB] 
 Del firefox 40.0+build4-0ubuntu0.14.04.1 [40.6 MB] 
 Del samba-common 2:4.1.6+dfsg-1ubuntu2.14.04.8 [157 kB] 
 Del winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [399 kB] 
 Del samba-vfs-modules 2:4.1.6+dfsg-1ubuntu2.14.04.8 [208 kB] 
 Del samba-dsdb-modules 2:4.1.6+dfsg-1ubuntu2.14.04.8 [219 kB] 
 Del chromium-codecs-ffmpeg-extra 43.0.2357.130-0ubuntu0.14.04.1.1092 [860 kB] 
 Del libnss-winbind 2:4.1.6+dfsg-1ubuntu2.14.04.8 [12.3 kB] 
 Del samba-common-bin 2:4.1.6+dfsg-1ubuntu2.14.04.8 [488 kB] 
 
**able@ableNotebook:~$ sudo apt-get autoremove** 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be REMOVED: 
   gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers 
   hyphen-en-us libchromaprint0 libgsoap4 libgstreamer-plugins-bad1.0-0 
   libgstreamer-plugins-good1.0-0 libgtkglext1 libopencv-calib3d2.4 
   libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4 
   libopencv-flann2.4 libopencv-highgui2.4 libopencv-imgproc2.4 
   libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4 
   libopencv-video2.4 libqt4-opengl libreoffice-help-en-gb 
   libreoffice-help-en-us libreoffice-l10n-en-gb libreoffice-l10n-en-za libsbc1 
   libsrtp0 libtbb2 libvncserver0 mythes-en-au openoffice.org-hyphenation 
   virtualbox 
 0 upgraded, 0 newly installed, 31 to remove and 12 not upgraded. 
 After this operation, 153 MB disk space will be freed. 
 Do you want to continue? [Y/n] y 
 (Reading database ... 178368 files and directories currently installed.) 
 Removing gstreamer1.0-plugins-bad-faad:amd64 (1.2.4-1~ubuntu1) ... 
 Removing gstreamer1.0-plugins-bad-videoparsers:amd64 (1.2.4-1~ubuntu1) ... 
 Removing hyphen-en-us (2.8.6-3ubuntu2) ... 
 Removing libchromaprint0:amd64 (1.1-1) ... 
 Removing virtualbox (4.3.10-dfsg-1ubuntu5) ... 
  * Stopping VirtualBox kernel modules                                    [ OK ]  
 Removing libgsoap4:amd64 (2.8.16-2) ... 
 Removing libgstreamer-plugins-bad1.0-0:amd64 (1.2.4-1~ubuntu1) ... 
 Removing libgstreamer-plugins-good1.0-0:amd64 (1.2.4-1~ubuntu1) ... 
 Removing libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libgtkglext1 (1.2.0-3.1fakesync3) ... 
 Removing libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libqt4-opengl:amd64 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1) ... 
 Removing libreoffice-help-en-gb (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-help-en-us (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-l10n-en-gb (1:4.2.8-0ubuntu1) ... 
 Removing libreoffice-l10n-en-za (1:4.2.8-0ubuntu1) ... 
 Removing libsbc1:amd64 (1.1-2ubuntu2) ... 
 Removing libsrtp0 (1.4.5~20130609~dfsg-1) ... 
 Removing libvncserver0:amd64 (0.9.9+dfsg-1ubuntu1.1) ... 
 Removing mythes-en-au (2.1-5.4) ... 
 Removing openoffice.org-hyphenation (0.7.1) ... 
 Removing libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1) ... 
 Removing libtbb2 (4.2~20130725-1.1ubuntu1) ... 
 Processing triggers for libc-bin (2.19-0ubuntu6.6) ... 
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
                        
**able@ableNotebook:~$ sudo apt-get install virtualbox-5.0 **

 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Unable to locate package virtualbox-5.0 
 E: Couldn't find any package by regex 'virtualbox-5.0'


As an aside, I started to install virtualbox5.0 (using Gdebi package  installer) that I downloaded from the virtualbox website a couple days  ago ([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  ). The file is virtualbox-5.0_5.0.2-102096~Ubuntu~trusty_amd64.deb .  This time trying the installation I got no error when I started the  installation process, but a password dialogue box came up that warned  about trustworthiness & security. So I thought I'd wait a while to  see what people here, including Slickymaster say about the installation.

Thank you,

Able
Can you please post back the exact "... password dialogue box came up that warned  about trustworthiness & security." warning you get? Maybe a screenshot of it.

---

### Post by AbleTassie on 2015-08-28
Slickymaster,

If you hit the "install package" button on the Gdebi Installer (after the file is loaded), the rectangular dialogue box comes up. I cannot take a screenshot, as most of the screen is "grayed out" and requires the user to select "cancel" or supply a password and click OK. The box is rectangular. There is a key image at the top left of the box with the words "You need to grant administrative rights to install software."  It goes on to say, "It is a security risk to install software packages manually. Install software from trustworthy software distributors only."

Thanks,

Able

---

### Post by SeijiSensei on 2015-08-28
Install the package from the command prompt with "sudo dpkg -i /path/to/virtualbox....deb".

---

### Post by AbleTassie on 2015-08-29
> **SeijiSensei said:**
> Install the package from the command prompt with "sudo dpkg -i /path/to/virtualbox....deb".

Thanks SeijiSensei,

Does Slickymaster agree with this recommendation?

Thanks,

Able

---

### Post by slickymaster on 2015-08-30
> **SeijiSensei said:**
> Install the package from the command prompt with "sudo dpkg -i /path/to/virtualbox....deb".

This ^^^

---

### Post by AbleTassie on 2015-08-30
> **SeijiSensei said:**
> Install the package from the command prompt with "sudo dpkg -i /path/to/virtualbox....deb".

This is what I get back if I run the command in terminal:

                        able@ableNotebook:~$ sudo dpkg -i
//home/able/VirtualBoxDownloaded/virtualbox-5.0_5.0.2-102096~Ubuntu~trusty_amd64.deb
[sudo] password for able: 
(Reading database ... 178396 files and
directories currently installed.)
Preparing to unpack
.../virtualbox-5.0_5.0.2-102096~Ubuntu~trusty_amd64.deb ...
Unpacking virtualbox-5.0
(5.0.2-102096~Ubuntu~trusty) over (5.0.2-102096~Ubuntu~trusty) ...
dpkg: dependency pablelems prevent configuration
of virtualbox-5.0:
 virtualbox-5.0 depends on libqt4-opengl (>=
4:4.7.2); however:
  Package libqt4-opengl:amd64 is not installed.
 dpkg: error processing package virtualbox-5.0
(--install):
 dependency pablelems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-16)
...
Processing triggers for hicolor-icon-theme
(0.13-1) ...
Processing triggers for shared-mime-info
(1.2-0ubuntu3) ...
Processing triggers for desktop-file-utils
(0.22-1ubuntu1) ...
Processing triggers for mime-support
(3.54ubuntu1.1) ...
Errors were encountered while processing:
 virtualbox-5.0
able@ableNotebook:~$ 
 
It looked like I could install it with package installer before, but if I try to install it now I get a message in a rectangular dialogue box with an exclamation point that says: ! Broken dependencies Your system has broken dependencies. This application cannot continue until this is fixed. To fix it run 'gksudo synaptic' or 'sudo apt-get install-f' in a terminal window.

I am not sure how to fix this with Synaptic Package Manager. Package Manager says I have 1 broken dependency and seems to identify virtualbox as the broken pacakage.

It looks like I have to install "libqt4-opengl:amd64"

Thanks,

Able

---

### Post by AbleTassie on 2015-08-30
I installed libqt4-opengl:amd64 and was then able to install Virtualbox, and I was able to run Windows inside the Virtual machine. 

How do I add the Oracle PPA to my system as suggested by SeijiSense? (Then my version of VirtualBox will be automatically updated when new releases come out.)

Thank you,

Able

---

### Post by CharlesA on 2015-08-30
Have a read here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

You will need to purge the existing virtualbox packages before you install.

---

### Post by SeijiSensei on 2015-08-31
> **CharlesA said:**
> Have a read here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

In particular the section concerning "Debian-based Linux distributions" on that page.

---

### Post by slickymaster on 2015-08-31
> **AbleTassie said:**
> I installed libqt4-opengl:amd64 and was then able to install Virtualbox, and I was able to run Windows inside the Virtual machine. 

How do I add the Oracle PPA to my system as suggested by SeijiSense? (Then my version of VirtualBox will be automatically updated when new releases come out.)

Thank you,

Able

Great you've got it working. Like CharlesA and SeijiSensei said, all you have to do is to purge your existent VB install and follow the instruction on the Virtual Box downloads page.

Please don't forget to mark this thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution for this problem.

---

### Post by AbleTassie on 2015-08-31
OK, thanks to everybody, [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"), ChalesA and Slickymaster. I was looking at the information on automatic updates and I do not really understand how to add lines to /etc/apt/sources.list, but I guess that is the title for another thread if I can't figure it out.

I will mark this thread as solved. 

Thanks again,

Able

---

