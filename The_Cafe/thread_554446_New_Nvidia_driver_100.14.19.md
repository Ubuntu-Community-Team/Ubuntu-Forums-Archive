---
title: "New Nvidia driver 100.14.19"
date: 2007-09-19
forum: The Cafe
---

### Post by FuturePilot on 2007-09-19
Nvidia just released a new driver. Seems to have a lot of improvements. Noticeably an improved GLX_EXT_texture_from_pixmap. Hopefully that reduces black windows caused by the black window bug.
[LIST]
[*]  Added support for new GPUs:
[/LIST]
          [LIST]
     [*]           Quadro FX 290
     [*]          Quadro FX 370
     [*]          Quadro FX 570
     [*]          Quadro FX 1700
[/LIST]
   [LIST]
[*] **Improved GLX_EXT_texture_from_pixmap out-of-memory handling.**
[*]     Fixed a performance regression on GeForce 8 GPUs.
[*]     Added support for a 'NoScanout' mode to the X driver, useful for high performance computing environments and remote graphics; please see the UseDisplayDevice option description for details.
[*]     Improved power management support with GeForce 8 and older GPUs.
[*]     Improved compatibility with recent X.Org X servers.
[*]     Improved G-Sync support with Quadro FX 4600 and Quadro FX 5600.
[*]     Added XV brightness and contrast controls to the GeForce 8 video texture adapter implementation.
[*]     Further improved interaction with ATi RS480/482 based mainboards.
[*]     Fixed stability problems with some GeForce 8 GPUs.
[*]     Fixed XvMC support on GeForce 7050 PV / NVIDIA nForce 630a GPUs with PureVideo support.
[*]     Added support for bridgeless SLI with GeForce 8 GPUs.
[*]     Fixed rotation support on some GeForce 8 GPUs.
[*]     Fixed a problem causing X to render incorrectly after VT switches with composited desktops.
[*]     Fixed a RENDER acceleration bug that was causing 2D rendering corruption in Eclipse with GeForce 8 GPUs.
[*]     Improved VGA console restoration with DFPs and TVs.
[*]     Fixed a bug that resulted in the generation of incorrect EDIDs on some notebooks.
[*]     Fixed flickering corruption with SLIAA on GeForce 8 GPUs.
[*]     Improved compatibility with recent Linux 2.6 kernels.
[*]     Fixed a compatibility problem with some Linux 2.4 kernels.
[*]     Improved hotkey switching support.
[*]     Fixed an nvidia-installer bug that was causing the installer to treat some of its temporary files as conflicting.
[*]     Fixed several problems causing crashes if /dev is mounted with the noexec option.
[*]     Reduced kernel virtual memory usage with some GeForce 8 GPUs.
[/LIST]

---

### Post by xat_ on 2007-09-19
What would be the standard procedure of installing this if I already have the drivers that came by default with the restricted drivers manager?

---

### Post by Bachstelze on 2007-09-19
```
sudo apt-get remove --purge nvidia-glx*
sudo apt-get remove --purge linux-restricted*
sudo apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev
```

Then reboot and install using the installer provided by nvidia. You can answer no to the last question (about configuring X).

---

### Post by 23meg on 2007-09-19
[QUOTE=FuturePilot]Hopefully that reduces black windows caused by the black window bug.[/QUOTE]

It seems fixed. I'm no longer getting black windows with direct rendering on a Go6200.

---

### Post by FuturePilot on 2007-09-19
Yes, this one seems a lot better. One thing I'm noticing is that I'm no longer getting freezes from Compiz. With the previous driver enabling Compiz, logging out, logging back in was a guaranteed freeze every time. It seems to be working fine now. And hopefully the black window bug has been reduced if not completely fixed.\\:D/

---

### Post by AlexenderReez on 2007-09-19
i hope it will be in repo soon....

released news =

> [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

> [http://www.nvnews.net/vbulletin/showthread.php?t=98635](http://www.nvnews.net/vbulletin/showthread.php?t=98635)

---

### Post by Laervian on 2007-09-19
Good, I was able to install the new drivers, and had to uninstall them quite quickly :( Is there no way for us laptop users to have these drivers installed WITHOUT having to remove the restricted-modules packages? I need wireless more than I need the new driver :(

---

### Post by nowshining on 2007-09-19
Awesome thanks for the update info. :) i'll download that soon after I take care of some business.

---

### Post by hanzomon4 on 2007-09-19
Does this fix the bug that causes the system to freeze when switching to tty terminals or fast user switching?

---

### Post by emisca on 2007-09-19
Try to use envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) to install the new driver.

This evening I'm going to try the new driver...... I hope that some issues are gone....

---

### Post by Andrewie on 2007-09-19
> **FuturePilot said:**
> 
 Fixed a bug that resulted in the generation of incorrect EDIDs on some notebooks.


finally, whenever I booted my laptop I needed to ctrl+alt+backspace a few times to get my screen to turn on.

---

### Post by veratyr on 2007-09-19
Has resume after suspend when using compiz been fixed in this?

---

### Post by starcraft.man on 2007-09-19
Sounds good, will have to try the driver later. Though, this isn't as encouraging as if they had open sourced... disappointing.

---

### Post by nowshining on 2007-09-19
updated I hope it fixed kppp restarting x-server since it does fix compatibility issues i won't know until after the second or third dial -

1st dial in - works like a charm
2nd dial in- maybe will restart x-server or maybe will work but no notification icon
3rs. RARE to work good - restarts x-server.

---

### Post by Billy_McBong on 2007-09-19
[COLOR="Blue"]cool. hope it gets into the repos soon[/COLOR]

---

### Post by mgazb on 2007-09-20
I have just installed this driver on my Feisty system with FX5200 graphics card. I get approx 1000 fps on glxgears, but when I draw textures in my application the rendering is very slow. I see first one half and then the other being drawn line by line. 

Has anyone else seen this? Does any know what I am doing wrong?

The application was OK using the distributed drivers but I want to improve the performance. I certainly couldn't see the image being rendered on the screen before the images were pasted in one go.
I have enabled SBA and Fastwrite on the graphics card.

thanks

dan

---

### Post by nowshining on 2007-09-20
there might be a bug in the nvidia installer and what your using is the older version -

open up a terminal and type the following then hit Enter and then input ur password Don't worry The PASSword WIL NOT SHOW up as u type - just type it as usual - hit enter and copy and paste the output..

```

 cat /proc/driver/nvidia/version


```

if yours says something such as

```

NVRM version: NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007

```

in it then we have a problem of the previous drivers not being removed and updated along with a new Nvidia Kernel.

---

### Post by mgazb on 2007-09-20
the file /proc/driver/nvidia/version lists the driver as 

NVRM cersion: NVIDIA UNIX x86 Kernel Module  100.14.19 Wed Sep 12 14:12:24 PDT 2007
GCC version:  gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

---

### Post by mgazb on 2007-09-20
I managed to solve the problem by going back to an older (9639) driver.

---

### Post by rustybronco on 2007-09-20
Tried to install NVIDIA-Linux-100.14.19-pkg1.run  last night and hosed x, I can get it up and running by re-configuring xorg but I can't get nvidia-settings to work. That's why I have 2 hard drives installed, so I can hose one and learn. To bad the 30 gig drive i'm using now is going out to lunch.
I will try again tonight to image the 30 gig then try the 10.14.19 install on the 120 gig again.
***edit*** it wanted me to run `telinit 3` as root but that brought me to a graphical log in and you can't install it with x running, vicious circle.

---

### Post by garythornton1956 on 2007-09-20
Envy would be a good idea but Gutsy is not supported by it yet

Booting to a different runlevel and using the nvidia installer seems to be the answer but ubuntu don't make it easy:(

---

### Post by FuturePilot on 2007-09-20
You don't need to boot to a different run level. Just log out and press Ctrl+Alt+F2 and sign in through a tty then just issue this command to shutdown X
```
sudo /etc/init.d/gdm stop
```
run the installer then start X again
```
sudo /etc/init.d/gdm start
```

And this is my output of cat /proc/driver/nvidia/version
> NVRM version: NVIDIA UNIX x86 Kernel Module 100.14.19 Wed Sep 12 14:12:24 PDT 2007
GCC version: gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

---

### Post by nowshining on 2007-09-20
mgazb - odd ur look fine

for FuturePilot good all good

for me and other why then

"NVIDIA UNIX x86 Kernel Module  100.14.11 " = is what I still have the .11 version.

---

### Post by garythornton1956 on 2007-09-20
Thanks, but I tried that and the machine locked up after stopping gdm without giving me a prompt.

It may be because Gutsy isn't finished yet?

---

### Post by nowshining on 2007-09-20
gary it was fine for me and yes i'm also using Gutsy in Dev.

---

### Post by garythornton1956 on 2007-09-20
OK I think I will try re-installing Gutsy.  I am using a Thinkpad T61p and I read in another thread that some of the hardware may be 'too new' for ubuntu at the moment, namely the video and the sound but I don't know if this is the case.  Certainly neither of them work properly for me yet.

---

### Post by bimmerd00d on 2007-09-20
I have my own way of upgrading via Envy, which involves the following.

1) opening envy homepage and installing new .deb
2) opening envy app, uninstalling Nvidia driver
3) installing new nvidia driver
4) no modification to my xorg
5) restart system.

It's not that intensive, but is there a "proper" way of doing it?  The new driver improved overall performance in compiz-fusion on my Quadro NVS 120M (recognized as a Geforce Go 7400).

---

### Post by garythornton1956 on 2007-09-20
Nowshining, are you using Gutsy Tribe 5?  I was installing Tribe 4 which didn't work so am no downloading Tribe 5.

---

### Post by starcraft.man on 2007-09-20
> **garythornton1956 said:**
> Nowshining, are you using Gutsy Tribe 5?  I was installing Tribe 4 which didn't work so am no downloading Tribe 5.

Tribe 5 is old, you will have to update a lot (we passed 6 milestone without a release). I recommend if you want the latest Gutsy download the latest live or alt snapshot or wait a week for the beta to come out (I believe it releases on the 27).

---

### Post by nowshining on 2007-09-20
i just update when new updates come out gary so i don't know - however I did uininstall the Nvidia drivers and still no problems - so my guess is that the ones with Gutsy are being used, in the restricted drivers manager - it has one unchecked and one checked - both the same.. i'll try myself disabling and then running the installer again. :)

---

### Post by garythornton1956 on 2007-09-20
Thanks guys, I downloaded Tribe 5 and installed from there.  

It now recognised the Quadro 570 video card and I could install the latest nvidia driver with Restricted Driver Manager.  This went ahead with no problems and the screen resolution is now set to 1920x1200 and there are some enhanced effects enabled.  Having said that, the fonts are not right and appear too big, but I expect that this will be solved by a fairly simple config change.  

Wireless LAN is working fine on the new Intel chip (4965?) and seems to be stable but the indicator light does not come on.  Bluetooth seems to be working now and I can associate with my phone but haven't tested it fully yet.

Still no audio, but that's for another day.

I'm now downloading the updates (517 of them) so will see which problems are still there and which are cured.

It will be worth the effort to get the T61p working, after all it must be better than the Vista that came pre-installed (now gone)

---

### Post by nowshining on 2007-09-20
lolz welcome and glad you got urs fixed :)

---

### Post by pt123 on 2007-09-21
the new drivers are great they work so much better with Compiz. No black windows. (6600GT card)

I got this from here, and I have been installing the nvidia drivers using this successfully. 

Open a terminal window Ctrl+Alt+F[1-6]

```

Code:

sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv"

ctrl+x and y to save.

Then
Code:

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start


```

---

### Post by nowshining on 2007-09-21
pt123 u could of subsituted nano for gedit for an external editor. :)

---

### Post by nowshining on 2007-09-21
xorg.conf sucks - it's really odd tho in that if I remove it and have NO xorg.conf then well gdm starts up - with it it doesn't work - well sometims..errr..

---

### Post by Yeeha on 2007-09-22
Strange, with either 100.14.11 and 100.14.19 i cant enable fastwrites, has anyone had same problem?

---

### Post by pt123 on 2007-09-22
> **nowshining said:**
> pt123 u could of subsituted nano for gedit for an external editor. :)

No, I am logged into just terminal, that way I can stop & start GDM.

---

### Post by n3tfury on 2007-09-22
> **pt123 said:**
> the new drivers are great they work so much better with Compiz. No black windows. (6600GT card)

I got this from here, and I have been installing the nvidia drivers using this successfully. 

Open a terminal window Ctrl+Alt+F[1-6]

```

Code:

sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv"

ctrl+x and y to save.

Then
Code:

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
**sudo /etc/init.d/gdm stop**
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start


```

oh boy, i got as far as the highlighted line above, then my screen went blank and i had to reboot.  i'm currently unable to get back into gnome and the xorg.conf error log mentions "failed to load module "nvidia" module does not exist, 0) duh.  No drivers available.

help?

---

### Post by n3tfury on 2007-09-22
k, learned some things tonight.  like how to mount a usb drive from a prompt and copying over the .run file to the desktop and all's well, exept i don't 3d acceleration yet (googling it now)

---

### Post by nowshining on 2007-09-22
> **pt123 said:**
> No, I am logged into just terminal, that way I can stop & start GDM.

oh well anyway ur nano command helped me because simply VI sucks - :) nano has the commands at the bottom unlike VI where I didn't know what to do. So again now I use nano instead and it helped save me behind recently. :)

---

### Post by pt123 on 2007-09-26
> **n3tfury said:**
> oh boy, i got as far as the highlighted line above, then my screen went blank and i had to reboot.  i'm currently unable to get back into gnome and the xorg.conf error log mentions "failed to load module "nvidia" module does not exist, 0) duh.  No drivers available.

help?

No you are meant to do this outside X, by opening a new terminal window (not sure of the correct phase).

Press Ctrl + Alt + F1 , a black terminal with a login prompt should appear.

Press Ctrl + Alt + F7 to get back to X ( i.e. Gnome)

---

### Post by dreadlocks1221 on 2007-09-27
I've tried many ways to install the new driver in tribe 5 and all it says is cant open file and envy can't install it either (maybe envy isn't compatible). 

Also Is it better to do it manually or with envy?

---

### Post by nowshining on 2007-09-28
> **dreadlocks1221 said:**
> I\'ve tried many ways to install the new driver in tribe 5 and all it says is cant open file and envy can\'t install it either (maybe envy isn\'t compatible). 

Also Is it better to do it manually or with envy?


press ctrl + alt + f1

type out ur username 

then password (it won \'t show up as u type which is normal)...


cd

to the directory where it was downloaded.

example.

cd /home

cd nowshining

cd Drivers

is mine

from there

type

sudo /etc/init.d/gdm stop

hit enter

enter ur password and again nothing will show up as u type - don\'t worry

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

if you\'d rather do a uninstall first then input ur old package with the --uninstall command at the end if not and you\'d rather let it auto uninstall then to the above

input ur password

at the end i\'d suggest NOT letting it modify your xorg.conf file.


back at the command prompt type

sudo /etc/init.d/gdm start


enter your password


if the screen goes off the on again press ctrl + alt + backspace several times and if it goes back to cutting off the screen and shutting it off, keep press the above - if you get a x server error -press okay. Next at the command prompt type ur username and then password

then

issue the command

sudo /etc/init.d/gdm stop

enter password - may need to wait a minute if it is slow

then issue the following if you want to try to delet the xorg.conf to see if you then can enter graphical mode - i myself had to at times..

issues the following

sudo rm /etc/X11/xorg.conf

enter your password

then issue the following command

sudo /etc/init.d/gdm start

if still not try a reboot by pressing ctrl + alt + del

if still not try uninstalling and the re-installing.

---

### Post by dreadlocks1221 on 2007-10-01
I get the installer to run but it  says I have no p recompiled kernel source and I need "kernel-source" or "kernel-devel" rpm installed

---

