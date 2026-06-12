---
title: "HOWTO: Latest NVIDIA drivers"
date: 2005-08-16
forum: Tutorials
---

### Post by tseliot on 2005-08-16
If you want to install Nvidia driver with the nvidia installer (I've tried v.7667) and you use a kernel from Ubuntu Hoary or you compiled it from Hoary sources (or kernel.org sources), then just try this HOWTO.
If you have a kernel from Ubuntu Breezy then try this HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924) [COLOR=Blue]OR just look at point 2 of the problems section of THIS guide.[/COLOR]

Make sure you graphic card is not among the ones which are NOT SUPPORTED by looking at the list you will find in the NOTES SECTION * 
[COLOR=Red]
You need 7676 version only if you have Geforce 7800, otherwise is useless (and it has some bugs). If you haven't got this graphic card PLEASE try 7667, it's more stable.[/COLOR]

Download the installer from this page according to your architecture (32bit or 64bit)
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) 

Before you start you have to make sure the following things are installed (see points "a","b","c"). If not, you can install them following these steps:

Open either Terminal or Konsole and type:

uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

a) press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

b) press the "Search" button and put "linux-source" in the search field

you will see a list of files, find "linux-source-the name you got from uname -r"

click on the file and select "Mark for installation"

c) press the "Search" button and put "build-essential" in the search field

click on the file and select "Mark for installation"


d) Press the "Apply" button.

You can close Synaptic (or Kynaptic) after it has finished installing the headers.


Ok, now let's begin:

1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc (just in case)

ctl-alt-f1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd &#8220;directory where you have the nvidia installer&#8221;

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run

If you have Ubuntu 64bit you can't install OpenGL32bit compatibility libraries, so when the installer asks whether to install it just answer no OR you may want to try a workaround which Draugen found but which I haven't tried myself (look at the PROBLEMS SECTION at the end of the guide: point 5).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with &#8220;Modules&#8221; and comment out (by putting a "#" before the line) the 2 lines I put in blue and add Load "glx". It should look like the example below:


Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#[COLOR=Blue]Load "dri"[/COLOR]
#[COLOR=Blue]Load &#8220;GLcore&#8221;[/COLOR]
Load "extmod"
Load "freetype"
[COLOR=Green]Load "glx"[/COLOR]
Load "int10"
Load "record"
Load "type1"
Load "vbe"

Then find the section Device and make sure the word I put in red is &#8220;nvidia&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR=Red]nvidia[/COLOR]"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

sudo /etc/init.d/gdm start (or "kdm start" if you use KDE)

Now you have installed the new nvidia driver.

[COLOR=Magenta]If you want a "control panel" which shows the settings of your card you might want to install "Nvidia-settings" (this part of the guide has been taken from the Unofficial Ubuntu Starter Guide) although they driver works fine also without it (the choice it's up to you).
[/COLOR]
Open Terminal or Konsole and type

sudo apt-get install nvidia-settings

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop (you can use "kate" instead of "gedit" in KDE)

Insert the following lines into the new file:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


Save the file and exit.

Restart your computer

You will be able to see "Nvidia settings" in the menu (the one from which you launch all the applications)

Enjoy!
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------[COLOR=Magenta]
NOTES SECTION[/COLOR]

* Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.

NVIDIA chip name Device PCI ID
------------------------------- -------------------------------
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153
----------------------------------------------------------------


** the name of the installer may vary:
e.g. it could be NVIDIA-Linux-x86_64-1.0-7667-pkg1.run.

So just put the name of the installer you've downloaded from Nvidia website.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[COLOR=Magenta]PROBLEMS SECTION[/COLOR]

1) If the installer reports that the &#8220;Framebuffer&#8221; kernel module conflicts with the drivers you will have to recompile your kernel and disable this function
Here's  a HOWTO for kernel compilation for newbies
[http://www.ubuntuforums.org/showthread.php?t=56835&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=56835&page=1&pp=10)

2) If the installer complains in this way (this is an example of part of the error):
...
nvidia: version magic '2.6.10-5-386 preempt 386 gcc-[COLOR=Blue]3.4'[/COLOR] should be
'2.6.10-5-386 preempt 386 gcc-[COLOR=Red]3.3[/COLOR]'
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details.
...

This means the installer tries to use gcc-3.4 instead of gcc-3.3(the right one).Type this before launching NVIDIA installer:

CC=gcc-[COLOR=Red]3.3[/COLOR] 
export CC

The number of the version of gcc has to be the same as the 2nd one reported in the error by nvidia installer (i.e. the word I put in red instead of the one I put in blue)

then run nvidia installer again.

3) If the installer complains in this way:
...
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.

The user Reid has suggested this solution:

To find out where 'gcc' is located I did:
Code:

which gcc


which returned:
Code:

/usr/bin/gcc


then I made a symbolic link to gcc called cc so programs trying to use 'cc' would get gcc, with this code:
Code:

sudo ln -s /usr/bin/gcc /usr/bin/cc

Then try the installer again.

4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:
sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection


This will either disable 3d acceleration or make it slower (sorry but I haven't got an AGP card so I haven't tried them myself)

If this doesn't work for you try asking at this Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

5) If you have Ubuntu 64bit you will have some problems when trying to install OpenGL32bit compatibility libraries, so yuomay want to try a workaround suggested by Draugen but which I haven't tried myself

type:

sudo mkdir /emul
sudo mkdir /emul/ia32-linux
sudo mkdir /emul/ia32-linux/usr

sudo ln -s /usr/lib32 /emul/ia32-linux/usr/lib


if /usr/lib32 does not exist, you need to do this

Type:

sudo apt-get install ia32-libs lib32gcc1 lib32stdc++6

without which the opengl compat libs probably won't be much use anyway 

there are more 32bit libs as well. check synaptic.


Alberto

---

### Post by cutOff on 2005-08-16
> Option "RenderAccel" "On" 
It's not sure. At least for me.

Anyway thanks for the howto.

---

### Post by tseliot on 2005-08-16
You're right, thanks it was a mistake. Fixed.

---

### Post by Kyral on 2005-08-16
What if I'm in Breezy but I'm using the Hoary kernel?

---

### Post by earobinson on 2005-08-17
dident work for me got a kernel error :(

---

### Post by tseliot on 2005-08-17
[QUOTE=Kyral]What if I'm in Breezy but I'm using the Hoary kernel?[/QUOTE]

Before running NVIDIA installer, type:

[COLOR=Red]CC=gcc-3.4[/COLOR] (here you have to put the number of the gcc you used to compile your kernel, which is 3.4 in my case*)

[COLOR=Red]export CC[/COLOR]


When I wanted to compile the modules for a Breezy kernel in Hoary I had to use gcc 3.4. If you want to compile them for a Hoary kernel in Breezy you should use the gcc with which Hoary kernel are usually compiled.

I'm not sure if it is gcc 3.3 (try with this one first).

If this gcc doesn't work you should try different versions of gcc until you find the right one (and the module will compile).

Have a look at this:
[QUOTE=haddog]This works great. Getting the corect version of gcc is the key. When you run the Nvidia installer, if it fails because of your version of gcc, it will tell you what version of gcc you need based on what your kernel is compiled with. Make sure to get gcc-X.X and not just gcc-X.X- base.[/QUOTE]

This was in my other thread about installing NVIDIA drivers with a Breezy kernel. That's how things work.

---

### Post by tseliot on 2005-08-17
[QUOTE=earobinson]dident work for me got a kernel error :([/QUOTE]

1) Have you installed the kernel headers of your current kernel?

2) Are you using Ubuntu Hoary or Breezy?

3) What's the output of the error (what does the installer say?)?

---

### Post by izmaelis on 2005-08-17
What are big improvements in this new nVidia driver if there are any? If there are no, why should any user bother installing/upgrading them?

---

### Post by tseliot on 2005-08-17
[QUOTE=izmaelis]What are big improvements in this new nVidia driver if there are any? If there are no, why should any user bother installing/upgrading them?[/QUOTE]

Well, the main reason is COMPATIBILITY. Without driver 7664-7667 I could never have 3d acceleration or a screen without any corruption with my Geforce 6200 PCI-E. Latest Nvidia graphic cards might not work with Ubuntu's nvidia drivers. I don't play games under Linux (I have an Xbox for that) but: in my case "nv" drivers= screen corruption, nvidia drivers (the ones you can install following Ubuntu Starter Guide) =black screen, no Xorg. If you want to know about the changes in the latest release (7676 I think) you shoul go to nvidia forum, Linux section.

---

### Post by izmaelis on 2005-08-17
I think that I won't bother installing new nVidia drivers cause my video card is quite old (FX5600XT), I'm not a gamer person and it works just fine now.
Anyway, I'll remember this thread for possible future needs. Thanks.

---

### Post by earobinson on 2005-08-17
[QUOTE=tseliot]1) Have you installed the kernel headers of your current kernel?

2) Are you using Ubuntu Hoary or Breezy?

3) What's the output of the error (what does the installer say?)?[/QUOTE]
 1) Have you installed the kernel headers of your current kernel?

no how do i do this?

---

### Post by tseliot on 2005-08-17
Well, I didn't explain how to install the headers, I'll fix this in the HOWTO. All you've got to do is:

Open either Terminal or Konsole and type:

uname -r (this will tell you the name and version of the kernel you are using)


Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-[COLOR=Red]the name you got from uname -r[/COLOR]"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

Press the "Apply" button.

After it has installed the headers try to follow my HOWTO again.

---

### Post by earobinson on 2005-08-17
> **tseliot]Well, I didn't explain how to install the headers, I'll fix this in the HOWTO. All you've got to do is:

Open either Terminal or Konsole and type:

uname -r (this will tell you the name and version of the kernel you are using)


Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-[COLOR=Red]the name you got from uname -r[/COLOR]"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

Press the "Apply" button.

After it has installed the headers try to follow my HOWTO again.[/QUOTE]
 Still no luck

here is the nvidia-install.log

[QUOTE]
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Aug 17 17:29:41 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
       kernel.  This may be because it is in use (for example, by the X
       server), but may also happen if your kernel was configured without
       support for module unloading.  Please be sure you have exited X before
       attempting to upgrade your driver.  If you have exited X, know that your
       kernel supports module unloading, and still receive this message, then
       an error may have occured that has corrupted the NVIDIA kernel module's
       usage count said:**
> www.nvidia.com[/url].


---

### Post by tseliot on 2005-08-17
Sorry pal, I've got to go to bed now (it's midnight in Italy and I' very tired). Tomorrow I'll find a solution.

good night

---

### Post by kangpeh on 2005-08-17
Just a wild guess, as I will in fact not do any additional research above and beyong merely scanning the error message posted in your forum posting above, but basically, it means that the module is in fact still loaded (as the statement claims).

To begin, try looking in your processes list for any and all applications/software that may in fact be using the said drivers (i.e., "X", "gdm", etc. may be good grep keywords) [ps aux |grep <keyword>].  Also, if in fact you do not find any said applications in your processes list, then go ahead and type "lsmod |grep nv".  What the previous command will do is 'list' the 'modules' loaded in your kernel and 'grep' the results for 'nv' and only return said lines which contain such keyword 'nv'.  If in fact there is any module still loaded into the kernel, once you find out the name (it will probably be like 'nvidia' or something) type 'sudo rmmod nvidia' or whatever applicable command.

Good luck in your endeavours.

pz and blessings.

---

### Post by tseliot on 2005-08-18
I agree with kangpeh. Try his/her method and install the drivers again.

However if this doesn't solve the problem try installing kernel image and headers 2.6.11. Here's how to do it:

Open Synaptic (or Kynaptic) and put "linux" in the search engine. 
You will find something like linux-image-2.6.11 and linux-headers-2.6.11, install them. 
Restart your computer.

Follow my HOWTO again.
Make sure you follow EVERY step in my guide, don't skip any.

Let me know if it works.

---

### Post by earobinson on 2005-08-18
[QUOTE=tseliot]I agree with kangpeh. Try his/her method and install the drivers again.

However if this doesn't solve the problem try installing kernel image and headers 2.6.11. Here's how to do it:

Open Synaptic (or Kynaptic) and put "linux" in the search engine. 
You will find something like linux-image-2.6.11 and linux-headers-2.6.11, install them. 
Restart your computer.

Follow my HOWTO again.
Make sure you follow EVERY step in my guide, don't skip any.

Let me know if it works.[/QUOTE]
 Will do as soon as i get home thanks for all the help guys, ill let you know if it works.

---

### Post by blackant on 2005-08-18
Newbie here... can we have a update through apt-get?

---

### Post by tseliot on 2005-08-18
[QUOTE=blackant]Newbie here... can we have a update through apt-get?[/QUOTE]
Unfortunately the only driver available for Ubuntu (using apt-get) is 7174 version. 

It's not hard. Follow the instructions, they are described step by step. If you think something is not clear or you have any doubt do not hesitate to ask me. I'm here to help newbies like you.

You just have to follow the steps, and you will also learn something.

---

### Post by strawberry on 2005-08-18
[QUOTE=tseliot]Unfortunately the only driver available for Ubuntu (using apt-get) is 7174 version. 
...
[/QUOTE]
i think the 7174 is not so bad for a newbie and very easy to install...
then you can play the latest driver version...

---

### Post by tseliot on 2005-08-18
[QUOTE=strawberry]i think the 7174 is not so bad for a newbie and very easy to install...
then you can play the latest driver version...[/QUOTE]
You're right but if he/she has the same graphic card as mine s/he will only have a black screen. The biggest problem is compatibility.

---

### Post by Marshalus on 2005-08-18
Just used your guide, and it worked great. No problems at all.

---

### Post by tseliot on 2005-08-18
[QUOTE=Marshalus]Just used your guide, and it worked great. No problems at all.[/QUOTE]
I'm happy it helped you.

---

### Post by tseliot on 2005-08-18
[QUOTE=strawberry]i think the 7174 is not so bad for a newbie and very easy to install...
then you can play the latest driver version...[/QUOTE]
Oh, and by the way s/he wanted to update her/his driver.

---

### Post by DancingSun on 2005-08-18
[QUOTE=tseliot](...)
If this doesn't work for you try asking at the official Nvidia Forum (there's a Linux section) (it's very useful)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)


Alberto[/QUOTE]

Alberto, nvnews.net is a fan/nVidia news site, not an "official" representation of nVidia.  Just thought I'd point that out.  Although it is said that there are 2 nVidia employees on the Unix team that frequently hangs out in that forum.

---

### Post by tseliot on 2005-08-18
[QUOTE=DancingSun]Alberto, nvnews.net is a fan/nVidia news site, not an "official" representation of nVidia.  Just thought I'd point that out.  Although it is said that there are 2 nVidia employees on the Unix team that frequently hangs out in that forum.[/QUOTE]

Thanks for the information. I talked to a developer of the drivers in there so I think it's quite a useful place to ask questions and to find solutions.

---

### Post by tseliot on 2005-08-18
Dancingsun, I've corrected the thread.

---

### Post by earobinson on 2005-08-18
[QUOTE=tseliot]Dancingsun, I've corrected the thread.[/QUOTE]
 thanks all i got it working instead of ctrl - alt - f1 i did a reboot.

---

### Post by jodef on 2005-08-18
Tried the HOWTo but ran into problems early on with installer not finding gcc, I tried the suggestion early on : 
```
CC=gcc-3.3
export CC
``` 
But this doesn't have any effect I post the error log here I would appreciate any suggestions that might help:```

option status:
license pre-accepted    : false
update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
```

---

### Post by reid on 2005-08-19
[QUOTE=jodef]Tried the HOWTo but ran into problems early on with installer not finding gcc, I tried the suggestion early on : 
```
CC=gcc-3.3
export CC
``` 
But this doesn't have any effect I post the error log here I would appreciate any suggestions that might help:```


<snipped>

ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
```[/QUOTE]
 I did something a little different.  To find out where 'gcc' is located I did:
```

$ which gcc

```
which returned:
```

/usr/bin/gcc

```
then I made a symbolic link to gcc called cc so programs trying to use 'cc' would get gcc, with this code:
```

$ sudo ln -s /usr/bin/gcc /usr/bin/cc

```

HTH,

Reid

---

### Post by tseliot on 2005-08-19
I think the problem is easy to solve

Please jodef, open Synaptic or Kynaptic and make sure you have gcc-3.3 installed (not only the base package)*, if not install it. Then try the command (the one which failed before) again.


*If you don't know how to install them, follow this steps:
Press the Search button and put "gcc" in the search field. I this way you will see a list of all gcc(s) available. There will be 2 items named "gcc-3.3" (the 2nd one is "gcc-3.3-base" or something like this). select them with your mouse, then select "Mark for installaton" and press the "Apply" button. The packages will be installed.

---

### Post by reid on 2005-08-19
[QUOTE=tseliot]I think the problem is easy to solve

Please jodef, open Synaptic or Kynaptic and make sure you have gcc-3.3 installed (not only the base package)*, if not install it. Then try the command (the one which failed before) again.


*If you don't know how to install them, follow this steps:
Press the Search button and put "gcc" in the search field. I this way you will see a list of all gcc(s) available. There will be 2 items named "gcc-3.3" (the 2nd one is "gcc-3.3-base" or something like this). select them with your mouse, then select "Mark for installaton" and press the "Apply" button. The packages will be installed.[/QUOTE]
 tseliot - when I encountered the 'no cc' problem, that is the first thing I did - and gcc 3.3 and gcc 3,3-base were both already installed.  I then told synaptic to reisntall them in hopes that would fix the problem.  Nope.  That is when I tapped into my limited linux knowledge and pulled a 'ln -s' out of my hat.  Are there other gcc 3.3 packages that need to be installed as well?

It worked for me, and hopefully it helps someone else also.

Thanks for the great HOWTO - I just needed to add a little to it to get it to work locally.


reid

---

### Post by tseliot on 2005-08-19
[QUOTE=reid]tseliot - when I encountered the 'no cc' problem, that is the first thing I did - and gcc 3.3 and gcc 3,3-base were both already installed.  I then told synaptic to reisntall them in hopes that would fix the problem.  Nope.  That is when I tapped into my limited linux knowledge and pulled a 'ln -s' out of my hat.  Are there other gcc 3.3 packages that need to be installed as well?

It worked for me, and hopefully it helps someone else also.

Thanks for the great HOWTO - I just needed to add a little to it to get it to work locally.


reid[/QUOTE]
Thanks for your contribution reid. I didn't mean to say your suggestion is wrong. I remember that when I had the same problem I hadn't installed the right version of gcc yet.

In a nutshell, I wanted to say that jodef should make sure the right gcc is installed (otherwise it won't work), then if it doesn't solve the problem, he can try your method. 

reid I really appreciate your help.

---

### Post by tseliot on 2005-08-19
Reid, I've added your method to the guide (giving you the credits for this)

---

### Post by jodef on 2005-08-19
Thanks reid and tseliot haven't tried it yet but will later. tseliot the necessary gcc packages are installed and it is the correct version. I hope the symlink works.

---

### Post by strawberry on 2005-08-19
[QUOTE=tseliot]You're right but if he/she has the same graphic card as mine s/he will only have a black screen. The biggest problem is compatibility.[/QUOTE]
I see. 
It was not mentioned so far but we also should consider that the new drivers - from version 1.0-7664 - do not support the following /old/ cards:

> 
Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                   Device PCI ID
    -------------------------------    -------------------------------
    RIVA TNT                           0x0020
    RIVA TNT2/TNT2 Pro                 0x0028
    RIVA TNT2 Ultra                    0x0029
    Vanta/Vanta LT                     0x002C
    RIVA TNT2 Model 64/Model 64 Pro    0x002D
    Aladdin TNT2                       0x00A0
    GeForce 256                        0x0100
    GeForce DDR                        0x0101
    Quadro                             0x0103
    GeForce2 GTS/GeForce2 Pro          0x0150
    GeForce2 Ti                        0x0151
    GeForce2 Ultra                     0x0152
    Quadro2 Pro                        0x0153


---

### Post by tseliot on 2005-08-19
[QUOTE=strawberry]I see. 
It was not mentioned so far but we also should consider that the new drivers - from version 1.0-7664 - do not support the following /old/ cards:[/QUOTE]
I see, that's a good point. I'll add the information to the HOWTO. Thanks, strawberry.

---

### Post by Cyberkef on 2005-08-19
Yet again a great HOWTO :)

I just had one problem, but because i came here from your great "Kernel Rebuild for Newbies" I found the solution myself :) 

I'll post it in this thread so anyone with the same problem would be helped :)

The Warning:
```
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
```
I have build my own custom kernel, so i selected **No** (dunno if it would have worked if I did Yes)

I have a GeForce MX 400 (which is not in the 'Old' list), and I got this error:

```
-> Kernel source path: '/lib/modules/2.6.10-cyberia/source'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
ERROR: Your kernel was configured to include rivafb support!
       
       The rivafb driver conflicts with the NVIDIA driver, please
       reconfigure your kernel and *disable* rivafb support, then
       try installing the NVIDIA kernel module again.
```
I had to rebuild my Kernel with the following option DISABLED (not enabled, not as module) :

Device Drivers > Graphics Support > nVidia Riva Support (disable it by pressing N)

Then rebuild your kernel :)

Worked like a charm to me ^_^

---

### Post by blastus on 2005-08-19
In setting up the drivers for my nVidia card I used the instructions posted at 
[http://ubuntuguide.org/](http://ubuntuguide.org/) and they worked fine. However, everytime I boot up I need to open the NVIDIA Settings program or enter in "nvidia-settings --load-config-only" to get the settings to load.

My question is how do I get the "nvidia-settings --load-config-only" command to run everytime I boot up? How do I get something like this to run everytime I boot up with X.Org in Ubuntu or with XFree86 in Mepis??? :?

---

### Post by linuxa on 2005-08-20
I followed the instructions as best as I could in the parent post. Except for the following change:

After I type CTRL-ALT-F1 and tried to shut kde down with "kdm stop", trying to install the NVIDIA drivers still come up with "it detected X server running"...

So I ended up deleting /etc/rc2.d/S21kdm (safe to do, since was a symbolic link to /etc/init.d/kdm). After rebooting, it forced Ubuntu into a terminal window, from which I was able to successfully install the drivers.

Unfortunately, after installation, my screen size has been reduced to 800x600 (that being the biggest size in control centre). I had a peak into /etc/X11/xorg.conf and it seems that all modes were still at 1021x768, just as I had left them.

Does any one know how I could get back my larger screen size please?

p.s. FYI, with S21kdm gone, Ubuntu will always boot to terminal, to undo what you did and restore booting to KDE type "ln -s /etc/init.d/kdm /etc/rc2.d/S21kdm" in a terminal

Content of xorg.conf:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2005-08-20
[QUOTE=blastus]In setting up the drivers for my nVidia card I used the instructions posted at 
[http://ubuntuguide.org/](http://ubuntuguide.org/) and they worked fine. However, everytime I boot up I need to open the NVIDIA Settings program or enter in "nvidia-settings --load-config-only" to get the settings to load.

My question is how do I get the "nvidia-settings --load-config-only" command to run everytime I boot up? How do I get something like this to run everytime I boot up with X.Org in Ubuntu or with XFree86 in Mepis??? :?[/QUOTE]
Sorry pal, I've no idea of how to do it. Try asking the nvidia forums (the link is at the bottom of the page of the guide)

---

### Post by tseliot on 2005-08-20
[QUOTE=linuxa]I followed the instructions as best as I could in the parent post. Except for the following change:

After I type CTRL-ALT-F1 and tried to shut kde down with "kdm stop", trying to install the NVIDIA drivers still come up with "it detected X server running"...

So I ended up deleting /etc/rc2.d/S21kdm (safe to do, since was a symbolic link to /etc/init.d/kdm). After rebooting, it forced Ubuntu into a terminal window, from which I was able to successfully install the drivers.

Unfortunately, after installation, my screen size has been reduced to 800x600 (that being the biggest size in control centre). I had a peak into /etc/X11/xorg.conf and it seems that all modes were still at 1021x768, just as I had left them.

Does any one know how I could get back my larger screen size please?

p.s. FYI, with S21kdm gone, Ubuntu will always boot to terminal, to undo what you did and restore booting to KDE type "ln -s /etc/init.d/kdm /etc/rc2.d/S21kdm" in a terminal

Content of xorg.conf:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection[/QUOTE]

Ok try this command (let's make another symlink):

sudo ln -s /etc/init.d/kdm /etc/rc2.d/S21kdm

Then restart your computer.

Tell me if it works

---

### Post by linuxa on 2005-08-20
OK, I finally got this solved.  :grin: 

Effectively for my Toshiba Laptop with the Gefore4 420GO, the nv drivers that came with Ubuntu worked fine except for 3d acceleration (and it was somewhat laggy). But neither the nvidia-glx nor the nvidia drivers from nvidia.com wanted to display the 1024x768 resolution native to my laptop. Both opting to go with 800x600 each and every time.

After examining the the xorg log /var/log/Xorg.0.log line by line, I found that the EDID reported by the laptop was identifying the screen width as 969 (it was auto-correcting the horizontal & vertical refresh rates I entered as well), basically telling the driver that width of 1024 wouldn't fit.

It all worked out after I put the line:

**Option "IgnoreEDID" "true" **

in the Device section in xorg.conf. Basically telling X to trust the figures in xorg.conf instead what EDID comes back with.

**Beware that the above option could be dangerous if you haven't set your xorg.conf correctly, it could potentially mess up your X when you start (read: black or warped display). So please careful if you intend to use this option.**

Also  the above option will only work for the nvidia driver. nvidia-glx doesn't have this option as far as I'm aware (someone correct me if I'm wrong).

And for anyone wanting to upgrade their drivers. It soooo pays to back up your xorg.conf before you start.

I've had many situations where I've uninstalled either of the nvidia drivers and X refused to boot to X using the default nv driver (even know the driver file was still where it's suppose to be). In those situations I've had to restore the xorg.conf to its original state and reboot to revert back to my pre-change status.

All in all, a very lengthy exercise. But well worth the fact that I can now play tuxracer  with no lag ;-) 

A big thank you goes out to the thread originator - **tseliot**)

p.s. for those wishing to install nvidia-glx instructions could be found at [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by kwid21 on 2005-08-20
I don't understand.....
I did all the steps in the how-to, but the installation still fails.  It gives an error message about my source files are not the ones used to compile my original kernel.  I have used Synaptic to install the right ones for my kernel, but they don't work. Why does this have to be so hard?

---

### Post by cutOff on 2005-08-20
[QUOTE=kwid21]I don't understand.....
I did all the steps in the how-to, but the installation still fails.  It gives an error message about my source files are not the ones used to compile my original kernel.  I have used Synaptic to install the right ones for my kernel, but they don't work. Why does this have to be so hard?[/QUOTE]
First, make sure you don't have installed nvidia-glx from repos and remove /etc/init.d/nvidia-glx.

Second, you have to install kernel-headers according to your kernel. Type 

sudo aptitude install linux-headers-$(uname -r)

---

### Post by kwid21 on 2005-08-20
Same error.  The error is cannot locate kernel module 'nvidia.ko'

Here's the terminal dialouge for getting the headers:

root@ubuntu:~ # sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
root@ubuntu:~ #

---

### Post by tseliot on 2005-08-20
[QUOTE=kwid21]Same error.  The error is cannot locate kernel module 'nvidia.ko'

Here's the terminal dialouge for getting the headers:

root@ubuntu:~ # sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
root@ubuntu:~ #[/QUOTE]

could you give me a more complete output of the error ( "The error is cannot locate kernel module 'nvidia.ko'" is not enough for me) you can find it in "/var/log/" it should be a file called "Nvidia log" or something (I don't recall its name). Please post it.

---

### Post by kwid21 on 2005-08-20
Had to format and reinstall because I could not get back to the desktop.  I guess I start from scratch [COLOR=Red]AGAIN [/COLOR](this is like my 6th install of Ubuntu in 2 days trying to just update my video drivers) and I have been trying to update my video drivers for 2 weeks trying 6 different distros in the process.

---

### Post by kwid21 on 2005-08-20
I [COLOR=Green]think[/COLOR] I got it now.  It said that the driver install was successful, then I edited my xorg.conf and restarted X.  The Nvidia logo splash screen went up, and brought me to the desktop.  Is there a way to test if it is installed correctly?

---

### Post by cutOff on 2005-08-20
[QUOTE=kwid21]I [COLOR=Green]think[/COLOR] I got it now.  It said that the driver install was successful, then I edited my xorg.conf and restarted X.  The Nvidia logo splash screen went up, and brought me to the desktop.  Is there a way to test if it is installed correctly?[/QUOTE]
Type ' glxinfo | grep rendering'. If yes, all ok.

btw what do you say 'glxgears'?

---

### Post by tseliot on 2005-08-20
[QUOTE=kwid21]I [COLOR=Green]think[/COLOR] I got it now.  It said that the driver install was successful, then I edited my xorg.conf and restarted X.  The Nvidia logo splash screen went up, and brought me to the desktop.  Is there a way to test if it is installed correctly?[/QUOTE]
I completely understand you. I've tried many distros. And, well after the 20th reinstallation I've lost the count...  :-P

---

### Post by kwid21 on 2005-08-20
robby@ubuntu:~$ glxgears
44947 frames in 5.0 seconds = 8989.400 FPS
50780 frames in 5.0 seconds = 10156.000 FPS
50633 frames in 5.0 seconds = 10126.600 FPS
50533 frames in 5.0 seconds = 10106.600 FPS
65570 frames in 5.0 seconds = 13114.000 FPS
70335 frames in 5.0 seconds = 14067.000 FPS
69883 frames in 5.0 seconds = 13976.600 FPS
59932 frames in 5.0 seconds = 11986.400 FPS
59815 frames in 5.0 seconds = 11963.000 FPS
65689 frames in 5.0 seconds = 13137.800 FPS
69870 frames in 5.0 seconds = 13974.000 FPS
69982 frames in 5.0 seconds = 13996.400 FPS
70386 frames in 5.0 seconds = 14077.200 FPS
62468 frames in 5.0 seconds = 12493.600 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
robby@ubuntu:~$


BTW  Thanks for helping guys!  I been wrestling with this for 2 weeks, and thanks to you guys I FINALLY got it working!    \\:D/

---

### Post by tseliot on 2005-08-20
I'm very happy for you!  :)

---

### Post by linuxa on 2005-08-20
[QUOTE=kwid21]Had to format and reinstall because I could not get back to the desktop.  I guess I start from scratch [COLOR=Red]AGAIN [/COLOR](this is like my 6th install of Ubuntu in 2 days trying to just update my video drivers) and I have been trying to update my video drivers for 2 weeks trying 6 different distros in the process.[/QUOTE]


When the driver install failed, did it boot to Terminal (i.e. text mode)? ?

Because that would've given you a chance to recover the original xorg.conf which in theory should take you back to the way it was before you attempted the driver install. 

Assuming that you backed up xorg.conf to begin with and that the default ubuntu installation did get you to X...

*Edit: Glad it all worked out for you in the end **Kwid21***

---

### Post by arnieboy on 2005-08-20
[QUOTE=tseliot]sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with “Modules” and either remove the first 2 lines in red and add Load "glx" or just make it look like this:


Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#Load "dri"
#Load “GLcore”
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"[/QUOTE]
Its very important that u comment out the "Load "dri"" lineby placing  a "#" before it. if u dont do that, xserver will crash when u try to restart it. 
Thanks for the HOWTO though.

---

### Post by tseliot on 2005-08-21
[QUOTE=arnieboy]Its very important that u comment out the "Load "dri"" lineby placing  a "#" before it. if u dont do that, xserver will crash when u try to restart it. 
Thanks for the HOWTO though.[/QUOTE]
Thanks for the correction, I'll fix it.

---

### Post by tseliot on 2005-08-21
I had made a mess with the colours (which I forgot to use in that case) but now it's fixed. Sorry for the mess, guys.

---

### Post by tseliot on 2005-08-21
Hi guys, I've just noticed my HOWTO has only 1 vote and it's a bad rating. 

This guide has worked for a few people so could I know the reason for such a LOW rate?

I would like an answer, some constructive criticism will be accepted. And in conclusion if you are having a problems using my guide, please tell me. We can make it better together!

And if you like it as it is, PLEASE VOTE.

---

### Post by izmaelis on 2005-08-22
I upgraded my kernel to 2.6.10-5-686 and can't install these nvidia drivers.
```

sudo sh NVIDIA-Linux-x86-1.0-7676-pkg1.run

```
says that there are no kernel sources although i aot-geted linux-headers-2.6.10-5-686 and linux-headers-2.6.10-5.
Thanks for your help.

---

### Post by tseliot on 2005-08-22
[QUOTE=izmaelis]I upgraded my kernel to 2.6.10-5-686 and can't install these nvidia drivers.
```

sudo sh NVIDIA-Linux-x86-1.0-7676-pkg1.run

```
says that there are no kernel sources although i aot-geted linux-headers-2.6.10-5-686 and linux-headers-2.6.10-5.
Thanks for your help.[/QUOTE]

Does it also complain about GCC and kernel modules?

EDIT: can you post the output of the error (look at /ver/log you will find a nvidia log file)

---

### Post by izmaelis on 2005-08-22
Here is my /var/log/nvidia-installer.log
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug 22 21:34:25 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.10-5-686/build'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.10-5-686/bu
   ild SYSOUT=/lib/modules/2.6.10-5-686/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.10-5-686/build SUBDIRS=/tmp
   /selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_vers
   ions
   make -f scripts/Makefile.build obj=/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz9511/NVI
   DIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nv.o
   .d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fomit-frame
   -pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i686 -Iincl
   ude/asm-i386/mach-default  -I/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD 
    -Wsign-compare -Wno-c
   ast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_G
   NU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 
   -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SI
   GNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT 
   -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9
   511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz9511/NVID
   IA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nv-v
   m.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fomit-fr
   ame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i686 -Ii
   nclude/asm-i386/mach-default  -I/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -
   O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL
   _NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D_
   _KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVE
   L=7676  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RAN
   GE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv_v
   m -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pk
   g1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/us
   r/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-a
   gp.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fomit-f
   rame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i686 -I
   include/asm-i386/mach-default  -I/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-p
   kg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
   ripts
    -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD  
   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ 
   -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  
   -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_D
   EBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHAN
   GE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRES
   ENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_agp -DKBUILD_MODNAME=
   nvidia -c -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_
   os-agp.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-i
   nterface.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -f
   omit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i
   686 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-
   7676-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-
   compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODUL
   E  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MA
   JOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -D
   NDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE
   _ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DN
   V_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_interface -DKBUILD_MODNAME=n
   vidia -c -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_o
   s-interface.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/os-i
   nterface.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-r
   egistry.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fo
   mit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march
   =i686 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz9511/NVIDIA-Linux-x86-1.
   0-7676-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wch
   ar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno
   -common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES
   -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL
   __ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676 
   -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESE
   NT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GE
   T_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_registry 
   -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1
   /usr/src/nv/.tmp_os-registry.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg
   1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     ld -m elf_i386  -r -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/s
   rc/nv/nvidia.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv-
   kernel.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.o /tmp
   /selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz951
   1/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/os-agp.o /tmp/selfgz9511/NVIDIA-
   Linux-x86-1.0-7676-pkg1/usr/src/nv/os-interface.o /tmp/selfgz9511/NVIDIA-Lin
   ux-x86-1.0-7676-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.10-5-686/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.10-5-686/Module.sy
   mvers /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nvid
   ia.mod.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fom
   it-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i68
   6 -
   Iinclude/asm-i386/mach-default     -DKBUILD_BASENAME=nvidia -DKBUILD_MODNAME
   =nvidia -DMODULE -c -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/sr
   c/nv/nvidia.mod.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/
   nvidia.mod.c
     ld -m elf_i386 -r -o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/sr
   c/nv/nvidia.ko /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvi
   dia.o /tmp/selfgz9511/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 File exists
-> Kernel messages:
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   NET: Registered protocol family 10
   Disabled Privacy Extensions on device c0313ce0(lo)
   IPv6 over IPv4 tunneling driver
   eth0: no IPv6 routers present
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```
Hope it helps.

---

### Post by tseliot on 2005-08-22
I'll try to solve your problem tomorrow. By the way have you tried driver 7667? Does it work?

Version 7676 just adds the following feature to 7667 and it seems (I'm not sure yet though) to have several bugs (have a look at the forum):

Improved GeForce 7800 GTX performance

So unless you have this card you should use 7667. I'll try to solve your problem although I can't try the drivers myself as I haven't got my computer any more.

---

### Post by izmaelis on 2005-08-22
Ok. I had to do
```

#sudo rmmod nvidia

```
and than new driver was compiled perfectly. Now I have another problem. Here is a part from my /var/log/Xorg.0.org:
```

(II) Loading extension NV-CONTROL
(EE) NVIDIA(0): Failed to load GLX
(==) RandR enabled

```
So, another question is why glx fails to load?

---

### Post by tseliot on 2005-08-22
Your log file says the nvidia module can't be loaded because it (or another module) exists.

1) Did you uninstall your previous drivers (do it ONLY if you had installed the drivers recommended by the Unofficial Starter guide)

If you did or you just didn't use them then try this:

sudo rm ./usr/src/nv/nvidia.ko

Then try the installer again.

Let me know if it works.

---

### Post by tseliot on 2005-08-22
[QUOTE=izmaelis]Ok. I had to do
```

#sudo rmmod nvidia

```
and than new driver was compiled perfectly. Now I have another problem. Here is a part from my /var/log/Xorg.0.org:
```

(II) Loading extension NV-CONTROL
(EE) NVIDIA(0): Failed to load GLX
(==) RandR enabled

```
So, another question is why glx fails to load?[/QUOTE]

Try asking here, this questions are out of range for me (since when my motherboard decided to die):
[http://www.nvnews.net/vbulletin/showthread.php?t=54863](http://www.nvnews.net/vbulletin/showthread.php?t=54863)

---

### Post by senectus on 2005-08-23
How come every time I reboot that PC I have to re-install the new drivers or 3D will not work (segfault) ?

---

### Post by arnieboy on 2005-08-23
[QUOTE=senectus]How come every time I reboot that PC I have to re-install the new drivers or 3D will not work (segfault) ?[/QUOTE]
try commenting "load dri" under "Module" by adding a "#" before that in /ect/X11/xorg.conf.

---

### Post by senectus on 2005-08-23
[QUOTE=arnieboy]try commenting "load dri" under "Module" by adding a "#" before that in /ect/X11/xorg.conf.[/QUOTE]

load "dri"  isn't in my xorg.conf at all, so it's not that :-P

---

### Post by arnieboy on 2005-08-23
[QUOTE=senectus]load "dri"  isn't in my xorg.conf at all, so it's not that :-P[/QUOTE]
dude.. READ ur xorg.conf. LOOK FOR THE SECTION CALLED   "MODULE"
u will find "load dri"

---

### Post by senectus on 2005-08-23
[QUOTE=arnieboy]dude.. READ ur xorg.conf. LOOK FOR THE SECTION CALLED   "MODULE"
u will find "load dri"[/QUOTE]

Would you like me to post my xorg.conf.. ?
LOAD      "dri" _is not_ in my xorg.conf.

It's not under the Module section or anywhere else in that document either (I did a search just to make sure I wasn't going blind).

---

### Post by arnieboy on 2005-08-23
[QUOTE=senectus]Would you like me to post my xorg.conf.. ?
LOAD      "dri" _is not_ in my xorg.conf.

It's not under the Module section or anywhere else in that document either (I did a search just to make sure I wasn't going blind).[/QUOTE]
shucks am sorry..  been attending to a few zillion posts on DRI and 3d acceleration all evening and its really late here. my apologies.

---

### Post by tseliot on 2005-08-23
[QUOTE=senectus]Would you like me to post my xorg.conf.. ?
LOAD      "dri" _is not_ in my xorg.conf.

It's not under the Module section or anywhere else in that document either (I did a search just to make sure I wasn't going blind).[/QUOTE]
make sure you have the lines I put in blue in the example


Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
[COLOR=Blue]#Load "dri"
#Load “GLcore”[/COLOR]
Load "extmod"
Load "freetype"
[COLOR=Blue]Load "glx"[/COLOR]
Load "int10"
Load "record"
Load "type1"
Load "vbe"

---

### Post by Fyrzen on 2005-08-23
I installed the drivers using your guide(great guide btw).

And I've run into my first problem, maybe you can help? When i check screensavers, none of the OpenGL ones work. I just get a black screen, the small preview says "No Preview Available". Something tells me i'm not going to be able to run neverwinter nights once i install it... The screensavers worked before.

Maybe not worth mentioning is, that in my xorg.conf file there was no *Load "GLcore"* line and *Load "glx"* was already present.

---

### Post by tseliot on 2005-08-23
[QUOTE=Fyrzen]I installed the drivers using your guide(great guide btw).

And I've run into my first problem, maybe you can help? When i check screensavers, none of the OpenGL ones work. I just get a black screen, the small preview says "No Preview Available". Something tells me i'm not going to be able to run neverwinter nights once i install it... The screensavers worked before.

Maybe not worth mentioning is, that in my xorg.conf file there was no *Load "GLcore"* line and *Load "glx"* was already present.[/QUOTE]
It's weird, I've never had such a problem. I don't use games in Ubuntu but OpenGL screensavers woked well on my computer.

I can try to run the installer again and to say yes when it asks you about OpenGL32bit compatibility libraries (expecially if you have Ubuntu 32)

Tell me if it works

---

### Post by izmaelis on 2005-08-23
After messing arround with new nvidia drivers for about three hours I finaly got them working... but I'm not so happy, cause performance isn't as it should be. I get:
```

izmaelis@boxzilla:~$ glxgears
6761 frames in 5.0 seconds = 1352.200 FPS
7931 frames in 5.0 seconds = 1586.200 FPS
7942 frames in 5.0 seconds = 1588.400 FPS
7866 frames in 5.0 seconds = 1573.200 FPS
7801 frames in 5.0 seconds = 1560.200 FPS
7688 frames in 5.0 seconds = 1537.600 FPS
7827 frames in 5.0 seconds = 1565.400 FPS
7716 frames in 5.0 seconds = 1543.200 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```
And I had to disable **Composite** extention in xorg.conf.
Now, how can I rollback to standart nvidia driver from ubuntu repos? I remember them working better than 7676 driver that I have now.

EDIT: I have GeForce FX5600XT 128Mb

---

### Post by tseliot on 2005-08-23
[QUOTE=izmaelis]After messing arround with new nvidia drivers for about three hours I finaly got them working... but I'm not so happy, cause performance isn't as it should be. I get:
```

izmaelis@boxzilla:~$ glxgears
6761 frames in 5.0 seconds = 1352.200 FPS
7931 frames in 5.0 seconds = 1586.200 FPS
7942 frames in 5.0 seconds = 1588.400 FPS
7866 frames in 5.0 seconds = 1573.200 FPS
7801 frames in 5.0 seconds = 1560.200 FPS
7688 frames in 5.0 seconds = 1537.600 FPS
7827 frames in 5.0 seconds = 1565.400 FPS
7716 frames in 5.0 seconds = 1543.200 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```
And I had to disable **Composite** extention in xorg.conf.
Now, how can I rollback to standart nvidia driver from ubuntu repos? I remember them working better than 7676 driver that I have now.

EDIT: I have GeForce FX5600XT 128Mb[/QUOTE]
Set xorg.conf to either "vesa" or "nv"
then follow the method in the guide to launch the installer but this time you will have to launch it in this way:

sudo sh NVIDIA-Linux-x86_64-1.0-7676-pkg2.run [COLOR=Red]--uninstall[/COLOR]

[COLOR=Blue]Of course use the name of the file you downloaded[/COLOR] (this is an example of my installer)

Then you can follow Ubuntu guide and install the driver you like most.

---

### Post by Fyrzen on 2005-08-23
I haven't tried reinstalling the driver yet, yes i am running ubuntu 32 but i didn't get a prompt for libraries. I thought it wasn't worth mentioning that i did **not** add the line Device "Nvidia", since i saw it was "nv" I figured *"what's the difference right?"*

Meanwhile i ran NWN from the terminal and it didn't start, it repeated the error "GLX missing on display 0:0" "Failed to initialize graphics". So i reinstalled the GLX packages from Synaptic. To no avail... If there's a difference between nv and Nvidia i might as well remove glx again and reinstall the drivers and be done with it, so is this the root of my problem?

---

### Post by arnieboy on 2005-08-23
[QUOTE=Fyrzen]I haven't tried reinstalling the driver yet, yes i am running ubuntu 32 but i didn't get a prompt for libraries. I thought it wasn't worth mentioning that i did **not** add the line Device "Nvidia", since i saw it was "nv" I figured *"what's the difference right?"*

Meanwhile i ran NWN from the terminal and it didn't start, it repeated the error "GLX missing on display 0:0" "Failed to initialize graphics". So i reinstalled the GLX packages from Synaptic. To no avail... If there's a difference between nv and Nvidia i might as well remove glx again and reinstall the drivers and be done with it, so is this the root of my problem?[/QUOTE]
nv is the nvidia driver that Ubuntu has packaged. Its old and ineffective. the whole point of this HowTo is to replace that. u need to change the driver name to "nvidia" if u want to use the most current Nvidia drivers that u have installed.

---

### Post by tseliot on 2005-08-23
[QUOTE=Fyrzen]I haven't tried reinstalling the driver yet, yes i am running ubuntu 32 but i didn't get a prompt for libraries. I thought it wasn't worth mentioning that i did **not** add the line Device "Nvidia", since i saw it was "nv" I figured *"what's the difference right?"*

Meanwhile i ran NWN from the terminal and it didn't start, it repeated the error "GLX missing on display 0:0" "Failed to initialize graphics". So i reinstalled the GLX packages from Synaptic. To no avail... If there's a difference between nv and Nvidia i might as well remove glx again and reinstall the drivers and be done with it, so is this the root of my problem?[/QUOTE]
It's important to follow EVERY step in my guide. Remove nvidia-glx in Synaptic and follow my guide again.

I hope it works now

---

### Post by Fyrzen on 2005-08-23
Fix't.

Thanks for your help, t'was my mistake.
Screensavers actualy work with a decent fps now, thanks again for this guide! :smile:

---

### Post by tseliot on 2005-08-23
[QUOTE=Fyrzen]Fix't.

Thanks for your help, t'was my mistake.
Screensavers actualy work with a decent fps now, thanks again for this guide! :smile:[/QUOTE]
I'm happy for you  :)

---

### Post by onlyOknows on 2005-08-23
my experience after appling this howto; (I think I need some help too) 

I tried this upgrade expecting to be able to make my philips 107B monitor run with 100Hz refresh rate. But I'm still can't reach this refresh rate. It's still working with 85 Hz at 1024x768. But I know this monitor and my FX5200 card support 100hz. (Actually it runs at 100Hz under windows.) How can I succed in that issue?

I could easily completed installing new nvidia drivers by following simply this howto.
Thanks to tseliot.

But I'm not sure if I really succedded upgrading my drivers. How can I check it. When I restarted the gdm after installation it seems nothing changed!!! But at least I could be able to return my X again :-)

And an other thing, I have previously installed Celestia. It was working well before the installation. After this upgrade it started to not to work!. 

The error I got when I tried to start celestia is below;

onlyOknows@ubuntu:~$ celestia
kbuildsycoca running...
Unable to resolve Xmu symbols - please check your Xmu library installation.
DCOP aborting call from 'anonymous-10336' to 'celestia'
celestia: ERROR: Communication problem with celestia, it probably crashed.
onlyOknows@ubuntu:~$

Thanks in advance. 

P.S.
These how to really makes sense for newbies like me. I'm learning many more things besides the main aim of the howto by just appling these howto's, even I can't succed. Thanks again.

---

### Post by tseliot on 2005-08-23
[QUOTE=onlyOknows]my experience after appling this howto; (I think I need some help too) 

I tried this upgrade expecting to be able to make my philips 107B monitor run with 100Hz refresh rate. But I'm still can't reach this refresh rate. It's still working with 85 Hz at 1024x768. But I know this monitor and my FX5200 card support 100hz. (Actually it runs at 100Hz under windows.) How can I succed in that issue?

I could easily completed installing new nvidia drivers by following simply this howto.
Thanks to tseliot.

But I'm not sure if I really succedded upgrading my drivers. How can I check it. When I restarted the gdm after installation it seems nothing changed!!! But at least I could be able to return my X again :-)

And an other thing, I have previously installed Celestia. It was working well before the installation. After this upgrade it started to not to work!. 

The error I got when I tried to start celestia is below;

onlyOknows@ubuntu:~$ celestia
kbuildsycoca running...
Unable to resolve Xmu symbols - please check your Xmu library installation.
DCOP aborting call from 'anonymous-10336' to 'celestia'
celestia: ERROR: Communication problem with celestia, it probably crashed.
onlyOknows@ubuntu:~$

Thanks in advance. 

P.S.
These how to really makes sense for newbies like me. I'm learning many more things besides the main aim of the howto by just appling these howto's, even I can't succed. Thanks again.[/QUOTE]

1) can you post your /etc/xorg.conf, please?

2) I don't know Celestia but I think you should try to reinstall it

3) If you want to know which driver version you are using try this (it's from Ubuntu Starter guide):
Open Terminal or Konsole and type

sudo apt-get install nvidia-settings

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop (you can use "kate" instead of "gedit" in KDE) 

Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Save the file and exit.

Restart your computer

You will be able to see "Nvidia settings" in the menu (I don't remember the exact name of the menu in GNOME which is the one with all the applications, and which is called kmenu in KDE)

Use it and you will be able to check and set a few things.

I'm going to add this in the guide

Let me know if it works.

---

### Post by mega on 2005-08-23
Is there a howto to ensure everything is working?

glxgears peaks my cpu at 100 %, and seems pretty slow, trying to play warcraft is not fun

card is a fx5200

mega@mainpc:/etc/X11$ glxgears
5103 frames in 5.0 seconds = 1020.600 FPS
6049 frames in 5.0 seconds = 1209.800 FPS


mega@mainpc:/etc/X11$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

I can run xpdyinfo but ONLY if it's the first thing I do, if I run it after glxgears I crash out to the shell, and gdm restarts

mega@mainpc:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3

---

### Post by tseliot on 2005-08-23
[QUOTE=mega]Is there a howto to ensure everything is working?

glxgears peaks my cpu at 100 %, and seems pretty slow, trying to play warcraft is not fun

card is a fx5200

mega@mainpc:/etc/X11$ glxgears
5103 frames in 5.0 seconds = 1020.600 FPS
6049 frames in 5.0 seconds = 1209.800 FPS


mega@mainpc:/etc/X11$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

I can run xpdyinfo but ONLY if it's the first thing I do, if I run it after glxgears I crash out to the shell, and gdm restarts

mega@mainpc:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3[/QUOTE]

Which driver version do you use?

---

### Post by mega on 2005-08-23
mega@mainpc:~$ glxgears -info
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = GeForce FX 5200/AGP/SSE2/3DNOW!
GL_VERSION    = 2.0.0 NVIDIA 76.76
GL_VENDOR     = NVIDIA Corporation


76.76 I think, installed it last night

I coulda swore I was getting 3000fps last night, today after a few reboots everything is slow again, been trying to get my microphone working properly (it is now)

---

### Post by tseliot on 2005-08-23
[QUOTE=mega]mega@mainpc:~$ glxgears -info
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = GeForce FX 5200/AGP/SSE2/3DNOW!
GL_VERSION    = 2.0.0 NVIDIA 76.76
GL_VENDOR     = NVIDIA Corporation


76.76 I think, installed it last night

I coulda swore I was getting 3000fps last night, today after a few reboots everything is slow again, been trying to get my microphone working properly (it is now)[/QUOTE]
Please use[COLOR=Red] 7667[/COLOR], they are more stable. Try to install them and see if they solve the problem. You need 7676 only if you have Geforce 7800, otherwise is useless.

---

### Post by mega on 2005-08-23
installign it now

I did learn something interesting

glxinfo only crashes if I run it right after glxgears

but if I do glxinfo > test.txt it wont crash

it must be writing something from the registers onto the screen that crashes the driver?!?

---

### Post by onlyOknows on 2005-08-23
[QUOTE=tseliot]1) can you post your /etc/xorg.conf, please?

2) I don't know Celestia but I think you should try to reinstall it

3) If you want to know which driver version you are using try this (it's from Ubuntu Starter guide):
Open Terminal or Konsole and type

sudo apt-get install nvidia-settings

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop (you can use "kate" instead of "gedit" in KDE) 

Insert the following lines into the new file

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Save the file and exit.

Restart your computer

You will be able to see "Nvidia settings" in the menu (I don't remember the exact name of the menu in GNOME which is the one with all the applications, and which is called kmenu in KDE)

Use it and you will be able to check and set a few things.

I'm going to add this in the guide

Let me know if it works.[/QUOTE]

Celestia is a real-time visual simulation of space program. 

I installed nvidia-settings as you said. But after installation I couldn't find the file NVIDIA-Settings.desktop in the location you said. (even I did "locate")

my xorg.conf file; (just the working lines)
------------------------------------------------------------------------------------------------------
Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "tr"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "PHILIPS 107B"
        Option          "DPMS"
        HorizSync       30-86
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "PHILIPS 107B"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

-----------------------end of my xorg.conf--------------------------------------------------------------

Thanks.

---

### Post by mega on 2005-08-23
No improvement with 7667

mega@mainpc:~$ glxgears -info
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = GeForce FX 5200/AGP/SSE2/3DNOW!
GL_VERSION    = 2.0.0 NVIDIA 76.67
GL_VENDOR     = NVIDIA Corporation

4957 frames in 5.0 seconds = 991.400 FPS
5257 frames in 5.0 seconds = 1051.400 FPS
5223 frames in 5.0 seconds = 1044.600 FPS


cpu is peaked at 100 %, should glxgears hit the cpu like that?

---

### Post by tseliot on 2005-08-23
[QUOTE=onlyOknows]... But after installation I couldn't find the file NVIDIA-Settings.desktop in the location you said. (even I did "locate")[/QUOTE]

Please, follow my instructions. Of course the file doesn't exists but you have to create it by using the commands I told you to use.

[QUOTE=onlyOknows]Section "Monitor"
        Identifier      "PHILIPS 107B"
        Option          "DPMS"
        HorizSync       30-86
        VertRefresh     50-160
EndSection
[/QUOTE]

Find the specs of your monitor (you can use Google) and find the Horizontal and the Vertical refresh of your monitor then put them instead of the default values

 HorizSync       [COLOR=Red]30-86[/COLOR]
 VertRefresh     [COLOR=Red]50-160[/COLOR]


Then save the file.

If you do this using the graphic interface log out and then login (it should restart Xorg)

---

### Post by onlyOknows on 2005-08-23
ohh. sorry sorry sorry! I have missed the words "the new file". I'm a newbie but not as new as that :-)
now I'm restarting the machine.

---

### Post by tseliot on 2005-08-23
[QUOTE=mega]No improvement with 7667

mega@mainpc:~$ glxgears -info
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = GeForce FX 5200/AGP/SSE2/3DNOW!
GL_VERSION    = 2.0.0 NVIDIA 76.67
GL_VENDOR     = NVIDIA Corporation

4957 frames in 5.0 seconds = 991.400 FPS
5257 frames in 5.0 seconds = 1051.400 FPS
5223 frames in 5.0 seconds = 1044.600 FPS


cpu is peaked at 100 %, should glxgears hit the cpu like that?[/QUOTE]
Try to add the lines I've put in blue to your xorg.conf:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Blue]Option "RenderAccel" "OFF"[/COLOR]
[COLOR=Blue]Option "AllowGLXWithComposite" "OFF"[/COLOR]

 Restart X by (logout and then login) and try glxgears again. If this does the trick but you have low FPS THEN (and ONLY THEN) erase "Option "RenderAccel" "OFF"" and try glxgears again.

 Tell me what happens in both cases.

---

### Post by DancingSun on 2005-08-23
[QUOTE=tseliot](...)
Find the specs of your monitor (you can use Google) and find the Horizontal and the Vertical refresh of your monitor then put them instead of the default values

 HorizSync       [COLOR=Red]30-86[/COLOR]
 VertRefresh     [COLOR=Red]50-160[/COLOR]


Then save the file.

If you do this using the graphic interface log out and then login (it should restart Xorg)[/QUOTE]
Or you could try commenting out those two lines by putting a "#" in front of the lines.  I did this and all my refresh rate@resolution combinations are detected automatically.  If this doesn't work for you, just uncomment the lines and you should be back on track.

---

### Post by onlyOknows on 2005-08-23
[QUOTE=tseliot]Please, follow my instructions. Of course the file doesn't exists but you have to create it by using the commands I told you to use.



Find the specs of your monitor (you can use Google) and find the Horizontal and the Vertical refresh of your monitor then put them instead of the default values

 HorizSync       [COLOR=Red]30-86[/COLOR]
 VertRefresh     [COLOR=Red]50-160[/COLOR]


Then save the file.

If you do this using the graphic interface log out and then login (it should restart Xorg)[/QUOTE]

Following your guide to nvidia-settings installation is worked. Thanks. 

I entered the values as what is given in the Philisps data sheet. In the data sheet these values are also given as ranges, but not as a single value!
The results is, I'm still couldn't reach the 100 Hz refresh rate. I also tried the way explained in the following howto;
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

It also didn't worked :-(

In the linux kernel or in the driver who decides to use which refresh rate? In the "Screen Resolution preference tool" of ubuntu the maximum listed rate is 85Hz. How these lists are generated? And when I changed the value in this list which file is being affected exactly? So maybe I can change this file by myself.

---

### Post by tseliot on 2005-08-23
> **onlyOknows]Following your guide to nvidia-settings installation is worked. Thanks. 

I entered the values as what is given in the Philisps data sheet. In the data sheet these values are also given as ranges, but not as a single value!
The results is, I'm still couldn't reach the 100 Hz refresh rate. I also tried the way explained in the following howto said:**
> http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21[/url]

It also didn't worked :-(

In the linux kernel or in the driver who decides to use which refresh rate? In the "Screen Resolution preference tool" of ubuntu the maximum listed rate is 85Hz. How these lists are generated? And when I changed the value in this list which file is being affected exactly? So maybe I can change this file by myself.
The file you are looking for is xorg.conf.

Have you tried this (in the command line)? :

[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]

And follow the instructions (it will also ask you the refresh rate (Vertical and Horizontal) of your monitor

---

### Post by REBELinBLUE on 2005-08-24
If you haven't got this solved now (and even if you had so other people will know) I have to make a symlink from linux-headers-2.6.10-5 (think thats the name, you'll see the folder in /usr/src) to linux, i.e.

```
sudo ln -s /usr/src/linux-headers-2.6.10-5/ /usr/src/linux/
```

then it worked

---

### Post by tseliot on 2005-08-24
[QUOTE=REBELinBLUE]If you haven't got this solved now (and even if you had so other people will know) I have to make a symlink from linux-headers-2.6.10-5 (think thats the name, you'll see the folder in /usr/src) to linux, i.e.

```
sudo ln -s /usr/src/linux-headers-2.6.10-5/ /usr/src/linux/
```

then it worked[/QUOTE]
I'm happy it works in this way. I might add this method to my guide later. Thanks

---

### Post by mega on 2005-08-24
[QUOTE=tseliot]
[COLOR=Blue]Option "RenderAccel" "OFF"[/COLOR]
[COLOR=Blue]Option "AllowGLXWithComposite" "OFF"[/COLOR]
[/QUOTE]

if I put this in, I can no longer start xorg, it tries 3-4 times, then locks up the computer

I had to boot in recovery mode to fix it, both have to be set to true, or xorg crashes

glxgears fps seems bad, but I was playing warcraft last night and I was getting 15-30fps, not too bad for a old card like this

---

### Post by tseliot on 2005-08-24
[QUOTE=mega]if I put this in, I can no longer start xorg, it tries 3-4 times, then locks up the computer

I had to boot in recovery mode to fix it, both have to be set to true, or xorg crashes[/QUOTE]
Try the other suggestions (in red) at the end of the guide. 

Then if  they don't work you will have to ask in Nvidia Forum (at the Linux section) as your problem can be related to some bug of the driver. You can ask the developers and some users in there.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by mega on 2005-08-24
I'm just going to leave it as is, glxgears fps sucks, but warcraft was ok, drop shadows works fine, overall desktop performance seems fine too

everything says direct rendering is working properly, not sure why glxgears performance is half what others get with this card

---

### Post by tseliot on 2005-08-24
[QUOTE=mega]I'm just going to leave it as is, glxgears fps sucks, but warcraft was ok, drop shadows works fine, overall desktop performance seems fine too

everything says direct rendering is working properly, not sure why glxgears performance is half what others get with this card[/QUOTE]
By the way I've read somewhere that glxgears fps aren't very important (I don't remember the exact reason though).

---

### Post by arnoct on 2005-08-24
Is there *any* way to enable hardware rendering without potentially randomly killing the x session? This was one of the reasons I went back to windows last time, because what use is emulating games like Warcraft 3 if they're unplayable?

---

### Post by tseliot on 2005-08-24
[QUOTE=arnoct]Is there *any* way to enable hardware rendering without potentially randomly killing the x session? This was one of the reasons I went back to windows last time, because what use is emulating games like Warcraft 3 if they're unplayable?[/QUOTE]
As mega said he/she had no problems with Warcraft. I don't use Linux for games. 

1) Have you tried this guide? (following EVERY step)
2) If you tried it, which is your problem (when does it occur,etc.)?

---

### Post by onlyOknows on 2005-08-24
[QUOTE=tseliot]The file you are looking for is xorg.conf.

Have you tried this (in the command line)? :

[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]

And follow the instructions (it will also ask you the refresh rate (Vertical and Horizontal) of your monitor[/QUOTE]

As soon as I returned from the job started to apply your suggestions.

Yess! That worked. But the only difference in my xorg.conf file is that the 1600x1200 is added. my monitor  supports that mode but since I don't want to use it I didn't thought to add it. But while reconfiguration when it asked me for the supported modes I also chose 1600x1200. After reconfiguration completed I started "Screen Resolution preference tool" and seen that for 1024x768 now 100hz is available  \\:D/ 
Just chose it and it worked.  :grin: 

here is the diff of my previous and after reconfiguration xorg.conf files.
onlyOknows@ubuntu:~$ diff -u /etc/X11/xorg.conf.200508241920 /etc/X11/xorg.conf --- /etc/X11/xorg.conf.200508241920     2005-08-24 19:20:19.528869888 +0300
+++ /etc/X11/xorg.conf  2005-08-24 19:20:19.664849216 +0300
@@ -37,7 +37,7 @@
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
-#      Load    "dri"
+       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
@@ -77,10 +77,6 @@
        Option          "DPMS"
        HorizSync       30-92
        VertRefresh     50-160

#it was just a trial. I had also tried without the following 3 lines. 
-
-        # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
-  Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
-
 EndSection

#see difference in modes. Only 1600x1200 is added!
 Section "Screen"
@@ -90,27 +86,27 @@
        DefaultDepth    24
        SubSection "Display"
                Depth           1
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
-               Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
+               Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
 EndSection

onlyOknows@ubuntu:~$


Thanks for your help. Now I have a really flicker free monitor.  :smile: 
And by solving the problems I'm really getting far away to use MS Windows from day to day.

---

### Post by tseliot on 2005-08-24
[QUOTE=onlyOknows]Thanks for your help. Now I have a really flicker free monitor.  :smile: 
And by solving the problems I'm really getting far away to use MS Windows from day to day.[/QUOTE]
I hope one day you can completely switch to Ubuntu as I did.
I'm happy the monitor works for you now :)

---

### Post by onlyOknows on 2005-08-24
[QUOTE=onlyOknows]As soon as I returned from the job started to apply your suggestions.

Yess! That worked. But the only difference in my xorg.conf file is that the 1600x1200 is added. my monitor  supports that mode but since I don't want to use it I didn't thought to add it. But while reconfiguration when it asked me for the supported modes I also chose 1600x1200. After reconfiguration completed I started "Screen Resolution preference tool" and seen that for 1024x768 now 100hz is available  \\:D/ 
Just chose it and it worked.  :grin: 

[/QUOTE]


Ohh No!!!  When I reboot the machine lost 100hz again  :-x 
And beside that my login window is started to open at 1600x1200@65Hz (it was 1024x768@75Hz). And the main window is again 1024x768@85Hz as before. 

What am I missing???

One more thing tseliot, you modified the "how to", and at the beggining you are saying that; "You need 7676 version only if you have Geforce 7800, otherwise is useless (and it has some bugs). If you haven't got this graphic card PLEASE try 7667, it's more stable." 
So, since my graphic card is an Fx5200 T128 I think I need to downgrade the nvdia driver. How can I do that?

---

### Post by tseliot on 2005-08-24
[QUOTE=onlyOknows]Ohh No!!!  When I reboot the machine lost 100hz again  :-x 
And beside that my login window is started to open at 1600x1200@65Hz (it was 1024x768@75Hz). And the main window is again 1024x768@85Hz as before. 

What am I missing???

One more thing tseliot, you modified the "how to", and at the beggining you are saying that; "You need 7676 version only if you have Geforce 7800, otherwise is useless (and it has some bugs). If you haven't got this graphic card PLEASE try 7667, it's more stable." 
So, since my graphic card is an Fx5200 T128 I think I need to downgrade the nvdia driver. How can I do that?[/QUOTE]
1) You can do this again:

sudo dpkg-reconfigure xserver-xorg
[COLOR=Red]You can try to select the resolution you use as the only supported mode (1024x768 )[/COLOR]

2) If you want to install 7667 follow the guide again and use nvidia installer 7667. It will ask you if you want to overwrite the previous installation, answer yes and there you go.

---

### Post by arnoct on 2005-08-24
[QUOTE=tseliot]As mega said he/she had no problems with Warcraft. I don't use Linux for games. 

1) Have you tried this guide? (following EVERY step)
2) If you tried it, which is your problem (when does it occur,etc.)?[/QUOTE]

I'm having the "random freezeups when RenderAccel is turned on" bug. yes I followed the guide, but since it was really bad I rolled back my drivers to an old version (I only have a 32mb GeForce2) and the problem still persisted, albeit slightly less.

---

### Post by onlyOknows on 2005-08-25
[QUOTE=tseliot]1) You can do this again:

sudo dpkg-reconfigure xserver-xorg
[COLOR=Red]You can try to select the resolution you use as the only supported mode (1024x768 )[/COLOR]

2) If you want to install 7667 follow the guide again and use nvidia installer 7667. It will ask you if you want to overwrite the previous installation, answer yes and there you go.[/QUOTE]


1- it didn!t worked :-(

2- I successfully downgraded to 7667. here is the link where to download the installer for 7667 driver; [http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html)

---

### Post by tseliot on 2005-08-25
[QUOTE=arnoct]I'm having the "random freezeups when RenderAccel is turned on" bug. yes I followed the guide, but since it was really bad I rolled back my drivers to an old version (I only have a 32mb GeForce2) and the problem still persisted, albeit slightly less.[/QUOTE]
Old graphic cards are not supported any more by this driver
Here's a list
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153

---

### Post by tseliot on 2005-08-25
> **onlyOknows]1- it didn!t worked :-(
2- I successfully downgraded to 7667. here is the link where to download the installer for 7667 driver said:**
> http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html[/url]
I didn't understand if 7667 work for you.
I really don't know how to help you with the refresh rate. 

1) Can you see the refresh in nvidia-settings?
2) Otherwise you can start another thread and ask for help. I'm sure there are more experienced user who can help you.

---

### Post by onlyOknows on 2005-08-25
[QUOTE=tseliot]I didn't understand if 7667 work for you.
I really don't know how to help you with the refresh rate. 

1) Can you see the refresh in nvidia-settings?
2) Otherwise you can start another thread and ask for help. I'm sure there are more experienced user who can help you.[/QUOTE]

you suggested; "sudo dpkg-reconfigure xserver-xorg
You can try to select the resolution you use as the only supported mode (1024x768 )"

I mean that suggestion didn't worked. 

But installing 7667 is OK.

Thanks anyway. Although I'm still working with 85Hz refresh rate, I learned many things. :-)

---

### Post by liquidfire on 2005-08-25
> **tseliot]I didn't understand if 7667 work for you.
I really don't know how to help you with the refresh rate. 

1) Can you see the refresh in nvidia-settings?
2) Otherwise you can start another thread and ask for help. I'm sure there are more experienced user who can help you.[/QUOTE]

Great guide :)
But i'm having some compile errors.
It stops with the error 
No kernelsources found blabla nvidia.ro.
I downloaded the right source (I hope) but i get that error above
Here's my log

[quote]
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug 25 20:47:28 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel said:**
> ftp://download.nvidia.com)?[/url] (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.12-6-amd64-generic/build'
-> Performing CC test with CC="gcc-3.3".
-> Performing rivafb check.
-> Performing change_page_attr() check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.12-6-amd64-
   generic/build SYSOUT=/lib/modules/2.6.12-6-amd64-generic/build'...
   
   NVIDIA: calling KBUILD...
   make CC=gcc-3.3  KBUILD_VERBOSE=1 -C /lib/modules/2.6.12-6-amd64-generic/bui
   ld SUBDIRS=/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv modu
   les
   mkdir -p /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/.tmp_v
   ersions
   make -f scripts/Makefile.build obj=/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7
   676-pkg2/usr/src/nv
   echo \#define NV_COMPILER \"`gcc-3.3 -v 2>&1 | tail -n 1`\" > /tmp/selfgz538
   6/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/nv_compiler.h
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.nv.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3.3.6/inclu
   de -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer  -mno-r
   ed-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare -fno-as
   ynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow   -I/tmp/se
   lfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointe
   r-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -minline-all-s
   tringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAME
   S -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNE
   L_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DN
   V_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MU
   LTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_
   ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV
   _VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o
   /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/.tmp_nv.o /tmp/
   selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/nv.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:215: let op: signed and unsigned type in conditional
   expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:221: let op: signed and unsigned type in conditional
   expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/nodemask.h: In function `__first_node':
   include/linux/nodemask.h:226: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__next_node':
   include/linux/nodemask.h:232: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__first_unset_node':
   include/linux/nodemask.h:250: let op: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: let op: pointer van type `void *' gebruikt in r
   ekensom
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:308: let op: argument van verkeerd type voor incrementeren
   In file included from include/asm/pci.h:94,
                    from include/linux/pci.h:904,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv.c:14:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: let op: pointer van type `void *' g
   ebruikt in rekensom
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3.3.6/in
   clude -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer  -mn
   o-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare -fno
   -asynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow   -I/tmp
   /selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat 
   -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O 
   -fno-common -mno-red-zone -minline-all-stringops -MD   -Wsign-compare -Wno-c
   ast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=ke
   rnel -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_
   MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG 
   -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_R
   EMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE
   _PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_B
   ASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5386/NVIDIA-Linux-x86
   _64-1.0-7676-pkg2/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz5386/NVIDIA-Linux-x86_6
   4-1.0-7676-pkg2/usr/src/nv/nv-vm.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:215: let op: signed and unsigned type in conditional
   expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:221: let op: signed and unsigned type in conditional
   expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/nodemask.h: In function `__first_node':
   include/linux/nodemask.h:226: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__next_node':
   include/linux/nodemask.h:232: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__first_unset_node':
   include/linux/nodemask.h:250: let op: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: let op: pointer van type `void *' gebruikt in r
   ekensom
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:308: let op: argument van verkeerd type voor incrementeren
   In file included from include/asm/pci.h:94,
                    from include/linux/pci.h:904,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: let op: pointer van type `void *' g
   ebruikt in rekensom
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3.3.6/i
   nclude -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno
   -strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer  -m
   no-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare -fn
   o-asynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow   -I/tm
   p/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv -Wall -Wimplicit -
   Wreturn-type -Wswitch -Wformat -Wchar-subs
   cripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common
   -mno-red-zone -minline-all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wn
   o-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM 
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSIO
   N=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DN
   V_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_RAN
   GE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_a
   gp -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-767
   6-pkg2/usr/src/nv/.tmp_os-agp.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676
   -pkg2/usr/src/nv/os-agp.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:215: let op: signed and unsigned type in conditional
   expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:221: let op: signed and unsigned type in conditional
   expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/nodemask.h: In function `__first_node':
   include/linux/nodemask.h:226: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__next_node':
   include/linux/nodemask.h:232: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__first_unset_node':
   include/linux/nodemask.h:250: let op: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: let op: pointer van type `void *' gebruikt in r
   ekensom
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:308: let op: argument van verkeerd type voor incrementeren
   In file included from include/asm/pci.h:94,
                    from include/linux/pci.h:904,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-agp.c:24:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: let op: pointer van type `void *' g
   ebruikt in rekensom
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3
   .3.6/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraph
   s -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-point
   er  -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compa
   re -fno-asynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow  
   -I/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-s
   ubscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-com
   mon -mno-red-zone -minline-all-stringops -MD   -Wsign-compare -Wno-cast-qual
   -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNT
   RM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VER
   SION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG 
   -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_
   RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT 
   -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=o
   s_interface -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5386/NVIDIA-Linux-x86_6
   4-1.0-7676-pkg2/usr/src/nv/.tmp_os-interface.o /tmp/selfgz5386/NVIDIA-Linux-
   x86_64-1.0-7676-pkg2/usr/src/nv/os-interface.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:215: let op: signed and unsigned type in conditional
   expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:221: let op: signed and unsigned type in conditional
   expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/nodemask.h: In function `__first_node':
   include/linux/nodemask.h:226: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__next_node':
   include/linux/nodemask.h:232: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__first_unset_node':
   include/linux/nodemask.h:250: let op: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: let op: pointer van type `void *' gebruikt in r
   ekensom
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-interface.c:26:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:308: let op: argument van verkeerd type voor incrementeren
   In file included from include/asm/pci.h:94,
                    from include/linux/pci.h:904,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-interface.c:26:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: let op: pointer van type `void *' g
   ebruikt in rekensom
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.os-registry.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3.
   3.6/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs
   -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer
    -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare 
   -fno-asynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow   -I
   /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -minline
   -all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNE
   L_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -D_GNU_SOURCE -D_LOOSE
   _KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION
   =0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -
   DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE
   _PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESEN
   T -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_registry -DKBUILD_MODNA
   ME=nvidia -c -o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv
   /.tmp_os-registry.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/sr
   c/nv/os-registry.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:215: let op: signed and unsigned type in conditional
   expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:221: let op: signed and unsigned type in conditional
   expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/nodemask.h: In function `__first_node':
   include/linux/nodemask.h:226: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__next_node':
   include/linux/nodemask.h:232: let op: signed and unsigned type in conditiona
   l expression
   include/linux/nodemask.h: In function `__first_unset_node':
   include/linux/nodemask.h:250: let op: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:46,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: let op: pointer van type `void *' gebruikt in r
   ekensom
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-registry.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:308: let op: argument van verkeerd type voor incrementeren
   In file included from include/asm/pci.h:94,
                    from include/linux/pci.h:904,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/nv-linux.h:69,
                    from /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/
   src/nv/os-registry.c:14:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: let op: pointer van type `void *' g
   ebruikt in rekensom
     ld -m elf_x86_64  -r -o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/
   usr/src/nv/nvidia.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/sr
   c/nv/nv-kernel.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/n
   v/nv.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/nv-vm.o 
   /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/os-agp.o /tmp/s
   elfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/os-interface.o /tmp/s
   elfgz5386/NVIDIA-Linux-x86_6
   4-1.0-7676-pkg2/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.12-6-amd64-generic/scripts/Makefile.m
   odpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.12-6-amd64-generic
   /Module.symvers /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv
   /nvidia.o
   Warning: could not find /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/us
   r/src/nv/.nv-kernel.o.cmd for /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-p
   kg2/usr/src/nv/nv-kernel.o
     gcc-3.3 -Wp,-MD,/tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/
   nv/.nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc-lib/x86_64-linux-gnu/3.3
   .6/include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs 
   -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer
    -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare 
   -fno-asynchronous-unwind-tables  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow     
   -DKBUILD_BASENAME=nvidia -DKBUILD_MODNAME=nvidia -DMODULE -c -o /tmp/sel
   fgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/nvidia.mod.o /tmp/selfg
   z5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/nvidia.mod.c
     ld -m elf_x86_64 -r -o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/u
   sr/src/nv/nvidia.ko /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/sr
   c/nv/nvidia.o /tmp/selfgz5386/NVIDIA-Linux-x86_64-1.0-7676-pkg2/usr/src/nv/n
   vidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   [  360.828049] cpu_init done, current fid 0xe, vid 0x6
   [  397.796974] Bluetooth: Core ver 2.7
   [  397.796979] NET: Registered protocol family 31
   [  397.796981] Bluetooth: HCI device and connection manager initialized
   [  397.796989] Bluetooth: HCI socket layer initialized
   [  397.810820] Bluetooth: L2CAP ver 2.7
   [  397.810823] Bluetooth: L2CAP socket layer initialized
   [  397.817729] Bluetooth: RFCOMM ver 1.5
   [  397.817735] Bluetooth: RFCOMM socket layer initialized
   [  397.817744] Bluetooth: RFCOMM TTY layer initialized
   [  831.262068] ibm_acpi: ec object not found
   [ 1308.306748] ISO 9660 Extensions: Microsoft Joliet Level 3
   [ 1309.386012] ISO 9660 Extensions: RRIP_1991A
   [ 1371.851331] nvidia: version magic '2.6.12-6-amd64-generic gcc-3.3' should
   be '2.6.12-6-amd64-generic gcc-3.4'
   [ 1724.604132] nvidia: version magic '2.6.12-6-amd64-generic gcc-3.3' should
   be '2.6.12-6-amd64-generic gcc-3.4'
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


---

### Post by bagatonovic on 2005-08-25
> **onlyOknows]1- it didn!t worked :-(

2- I successfully downgraded to 7667. here is the link where to download the installer for 7667 driver said:**
> http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html[/url]


I got a higher refresh rate using any Nvidia driver by commenting out the following lines in my xorg.conf

HorizSync
VertRefresh

So just add "#" in front of those 2 lines.  This will force X to probe the monitor and will automatically pick best refresh

---

### Post by tseliot on 2005-08-25
[QUOTE=liquidfire]Great guide :)
But i'm having some compile errors.
It stops with the error 
No kernelsources found blabla nvidia.ro.
I downloaded the right source (I hope) but i get that error above
Here's my log[/QUOTE]
It's easy to solve. I've dealt with it in [COLOR=Red]point 2 of the "Problem Section"[/COLOR] of my guide. Have a look at it.

By the way this is the solution for you:

It means the installer tries to use gcc-3.3 instead of gcc-3.4(the right one).Type this before launching NVIDIA installer:

CC=gcc-3.4 
export CC

then run nvidia installer again.

P.S. Let me guess: you are using a Breezy kernel, aren't you?

---

### Post by liquidfire on 2005-08-25
[QUOTE=tseliot]It's easy to solve. I've dealt with it in [COLOR=Red]point 2 of the "Problem Section"[/COLOR] of my guide. Have a look at it.

By the way this is the solution for you:

It means the installer tries to use gcc-3.3 instead of gcc-3.4(the right one).Type this before launching NVIDIA installer:

CC=gcc-3.4 
export CC

then run nvidia installer again.

P.S. Let me guess: you are using a Breezy kernel, aren't you?[/QUOTE]
Sorry, how stupid of me ;) I did exactly what I read, setting CC=gcc3.3 but i type 3 instead of four :)

---

### Post by tseliot on 2005-08-25
[QUOTE=liquidfire]Sorry, how stupid of me ;) I did exactly what I read, setting CC=gcc3.3 but i type 3 instead of four :)[/QUOTE]
No problem, have fun with your new driver :)

---

### Post by liquidfire on 2005-08-25
[QUOTE=tseliot]No problem, have fun with your new driver :)[/QUOTE]
Hmm, its conflicting with the 7667 driver which is installed by default 
Any idea how to avoid it? I removed everything except the common thingy.
Should I remove it, if so it will remove some image files too and I don't know if that would be harmfull.

---

### Post by onlyOknows on 2005-08-25
[QUOTE=bagatonovic]I got a higher refresh rate using any Nvidia driver by commenting out the following lines in my xorg.conf

HorizSync
VertRefresh

So just add "#" in front of those 2 lines.  This will force X to probe the monitor and will automatically pick best refresh[/QUOTE]

I have already tried it, but it didn't change anything.  I thing xorg.conf is a useless file.  I have tried billions of configurations that are all suggested by some people on the forums. But no one worked!!!   :-x  :-x  :-x   ](*,)  ](*,)  ](*,)

---

### Post by tseliot on 2005-08-25
[QUOTE=liquidfire]Hmm, its conflicting with the 7667 driver which is installed by default 
Any idea how to avoid it? I removed everything except the common thingy.
Should I remove it, if so it will remove some image files too and I don't know if that would be harmfull.[/QUOTE]
I don't understand (perhaps because it's 10.35PM and I'm still studying and I'm tired) . 

1) Which driver are you trying to install?

2) Which driver was previously installed? And what do you mean when saying "installed by default"

3) What do you want to remove?

Thanks

---

### Post by liquidfire on 2005-08-26
[QUOTE=tseliot]I don't understand (perhaps because it's 10.35PM and I'm still studying and I'm tired) . 

1) Which driver are you trying to install?

2) Which driver was previously installed? And what do you mean when saying "installed by default"

3) What do you want to remove?

Thanks[/QUOTE]

1) I try to install the 7676 drivers because I have a 7800GTX
2)I had none driver installed, but by default the 7667 is installed.
3) I want to remove nvidia-kernel-common because it says the 7667 is in it, but i'm unsure if I can boot if I remove that.

---

### Post by bagatonovic on 2005-08-26
[QUOTE=liquidfire]1) I try to install the 7676 drivers because I have a 7800GTX
2)I had none driver installed, but by default the 7667 is installed.
3) I want to remove nvidia-kernel-common because it says the 7667 is in it, but i'm unsure if I can boot if I remove that.[/QUOTE]

I am sorry the refresh rate fix didn't work for you.  It worked for me.  I feel bad for ya because I know what this is like.  I remember trying to get my GeForce2 to work on Mandrake 6.x a long time ago, and it was hell.

Tseliot's guide is totally awesome, and it worked for me.  Could you humor me and just try the following.  
DONT remove any packages with synaptic or Apt-get.
DO the following command:  sudo rm /etc/init.d/nvidia-glx
DO install the latest driver downloaded form Nvidia.
Make sure your xorg.conf is setup just like tseliot's guide tells you to with the exception of the refresh rate fix I posted earlier. 

I would be interested to see if this works for you.  

BTW - I think it's funny when you say xorg.conf is useless because it controls the X settings.  Could you please verify the exact location and name of the file you are editing?  I am not poking fun, and would sincerely like to help.  :)

---

### Post by DancingSun on 2005-08-26
[QUOTE=liquidfire]1) I try to install the 7676 drivers because I have a 7800GTX
2)I had none driver installed, but by default the 7667 is installed.
3) I want to remove nvidia-kernel-common because it says the 7667 is in it, but i'm unsure if I can boot if I remove that.[/QUOTE]
Hmm ... I didn't know 7667 was installed by default.  I had to use Synaptic to install my nVidia drivers and those were only 7174.  By default, I believe X was using theb built-in nv drivers.

---

### Post by tseliot on 2005-08-26
[QUOTE=liquidfire]1) I try to install the 7676 drivers because I have a 7800GTX
2)I had none driver installed, but by default the 7667 is installed.
3) I want to remove nvidia-kernel-common because it says the 7667 is in it, but i'm unsure if I can boot if I remove that.[/QUOTE]
Neither 7667 nor 7174 is the default driver in Ubuntu Hoary although you can get 7174 in Synaptic. ("nv" is the default open source driver in Ubuntu)

Are you using Breezy?

---

### Post by liquidfire on 2005-08-26
[QUOTE=tseliot]Neither 7667 nor 7174 is the default driver in Ubuntu Hoary although you can get 7174 in Synaptic. ("nv" is the default open source driver in Ubuntu)

Are you using Breezy?[/QUOTE]
Yes, i am using breezy.
nvidia-kernell-common states that its driver version 7667 :neutral:

---

### Post by tseliot on 2005-08-26
[QUOTE=liquidfire]Yes, i am using breezy.
nvidia-kernell-common states that its driver version 7667 :neutral:[/QUOTE]
Ok, set "vesa" instead of nvidia in your xorg.conf.
Log out and log in
Open Synaptic/Kynaptic and remove anything that has to do with nvidia (you can keep "nvidia-settings" if you installed it before).

Then follow this guide which is for Breezy (and which also works in Hoary with Breezy kernels) (as I recommended to do in this HOWTO)

[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)

and use gcc 3.4 (as it's explained in the guide)

---

### Post by liquidfire on 2005-08-26
> **tseliot]Ok, set "vesa" instead of nvidia in your xorg.conf.
Log out and log in
Open Synaptic/Kynaptic and remove anything that has to do with nvidia (you can keep "nvidia-settings" if you installed it before).

Then follow this guide which is for Breezy (and which also works in Hoary with Breezy kernels) (as I recommended to do in this HOWTO)

[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)

and use gcc 3.4 (as it's explained in the guide)[/QUOTE]
I'm getting new errors now.

[quote]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Aug 26 21:06:02 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel said:**
> ftp://download.nvidia.com)?[/url] (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.12-6-amd64-generic/build'
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


---

### Post by tseliot on 2005-08-26
[QUOTE=liquidfire]I'm getting new errors now.[/QUOTE]
Did you install the kernel headers for your kernel version?

If you didn't, you can install it in Synaptic and then try the installer again

---

### Post by liquidfire on 2005-08-26
[QUOTE=tseliot]Did you install the kernel headers for your kernel version?

If you didn't, you can install it in Synaptic and then try the installer again[/QUOTE]
I did but nevermind i'll wait till we get a more stable version for breezy :)

---

### Post by arnoct on 2005-08-26
[QUOTE=tseliot]Old graphic cards are not supported any more by this driver
Here's a list
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153[/QUOTE]

My card is not in that list. It's a GeForce2 MX 100/200, which is supported. However, it *doesn't matter*, since *every version I've used in the last six months has had this bug.* I can't enable hardware rendering (RenderAccel) because if I do, Xorg freezes. I just want to know if there's a fix/workaround for it yet, or if nvidia is just sitting on their hands with the problem.

---

### Post by DancingSun on 2005-08-26
[QUOTE=arnoct]My card is not in that list. It's a GeForce2 MX 100/200, which is supported. However, it *doesn't matter*, since *every version I've used in the last six months has had this bug.* I can't enable hardware rendering (RenderAccel) because if I do, Xorg freezes. I just want to know if there's a fix/workaround for it yet, or if nvidia is just sitting on their hands with the problem.[/QUOTE]
Please consult the last paragraph of this [page](http://www.nvidia.com/object/linux_display_ia64_1.0-5336).

---

### Post by liquidfire on 2005-08-27
Oke breezy just attracted me again.
I'm having new errors :/
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Aug 27 20:05:51 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `make` in your path; please make
       sure that you have the package 'make' installed.  If make is installed
       on your system, then please check that `make` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


---

### Post by liquidfire on 2005-08-27
[QUOTE=liquidfire]Oke breezy just attracted me again.
I'm having new errors :/[/QUOTE]

Something is wrong with the forums

---

### Post by PsychoTrauma on 2005-08-31
How would you go about updating the drivers for a new kernel? Would it be as simple as using the nvidia installer with the --uninstall command, then logging in with the new kernel and following the above steps?

---

### Post by tseliot on 2005-08-31
[QUOTE=PsychoTrauma]How would you go about updating the drivers for a new kernel? Would it be as simple as using the nvidia installer with the --uninstall command, then logging in with the new kernel and following the above steps?[/QUOTE]
Just follow the instructions from the beginning. As I wrote you have to set the driver to vesa or nv (if it worked for you) in xorg. 

Then you boot in the new kernel and repeat the installation process with the nvidia installer (which will ask you to overwrite the previous installation).

---

### Post by tseliot on 2005-08-31
[QUOTE=liquidfire]Oke breezy just attracted me again.
I'm having new errors :/[/QUOTE]
Open synaptic or kynaptic and make sure you have installed "make" and "makedev" packages.

Then try again.

---

### Post by PsychoTrauma on 2005-08-31
Thank you, I took your advice as well as trying the way I described above and they both worked. I left the settings as "nvidia" though and just did the removal and reinstall after X couldn't start.

---

### Post by AntiKris on 2005-09-02
Howdy.  First off, I'm a complete linux noob, so apologies for asking what would appear to be dumb, basic questions.  I've reviewed this and similar posts, and have tried some of the various offered solutions, but nothing seems to work yet.  I apologize if the answer I need has already been posted, but so far, I'm still out in the NVIDIA cold, so to speak.

Here's what I'm running: thanks to Tseliot's very helpful HOWTO, I compiled a brand spanking new emt64 smp kernel from 2.6.13 (it was the new release that inspired me to get around to checking out linux).  I've got a pentium 830d on a p5wd2 (which is a problematic board, so far, if anyone's thinking of getting one), with a crappy-ass Asus en6200 TC.  I compiled my kernel from the 'vanilla' 2.6.13.

So far, trying to install NVIDIA's latest two drivers (7667 and 7676, doesn't matter, same effect), in a word, fails.  I'm postulating that this might be because of smp, or the 2.6.13 (instead of .11 or .12), but my rather uneducated guesswork is worth the paper this is printed on.  (nobody print this reply out)

I can successfully compile the module, using either NVIDIA's run package, or doing it manually in terminal, but the results are the same: X-server fails to load the graphical environment.  

Before anyone asks, I've done all the cancelling out of "Load DRI" and added "nvidia" and the other steps in NVIDIA's readme.  That is apparently successful in telling the system to load a driver which, alas, isn't.  I'm not expecting wonderful things from my crapply little video card (that's what November is for), but I'd like to load the NVIDIA driver just to prevent the inevitable screen corruption yielded by the default nv driver.  Having said that, who wouldn't want Opengl working?  I've managed to get my girlfriend hooked on Baldur's Gate (I think that deserves a standing ovation, actually), so when BG2 time comes around, I'd like to have her play that in Ubuntu, rather than Winblows.  

Any and all help appreciated.  You can even be nasty and derogatory while helping me, as long as you're funny, too. ](*,)

---

### Post by brainspank on 2005-09-02
was reading the topic and saw the references to gcc 3.3 -> 3.4 and thought I'd add a tip:

when updating symlinks, a simpler command is to use "ln -sf" instead of just "ln -s".

eg.

"ln -sf gcc-3.4 gcc"

instead of

"rm gcc"
"ln -s gcc-3.4 gcc"

it just avoids an "rm" and "f"orces the new symlink, and you don't have to worry if it already exists.

---

### Post by tseliot on 2005-09-03
[QUOTE=AntiKris]Howdy.  First off, I'm a complete linux noob, so apologies for asking what would appear to be dumb, basic questions.  I've reviewed this and similar posts, and have tried some of the various offered solutions, but nothing seems to work yet.  I apologize if the answer I need has already been posted, but so far, I'm still out in the NVIDIA cold, so to speak.

Here's what I'm running: thanks to Tseliot's very helpful HOWTO, I compiled a brand spanking new emt64 smp kernel from 2.6.13 (it was the new release that inspired me to get around to checking out linux).  I've got a pentium 830d on a p5wd2 (which is a problematic board, so far, if anyone's thinking of getting one), with a crappy-ass Asus en6200 TC.  I compiled my kernel from the 'vanilla' 2.6.13.

So far, trying to install NVIDIA's latest two drivers (7667 and 7676, doesn't matter, same effect), in a word, fails.  I'm postulating that this might be because of smp, or the 2.6.13 (instead of .11 or .12), but my rather uneducated guesswork is worth the paper this is printed on.  (nobody print this reply out)

I can successfully compile the module, using either NVIDIA's run package, or doing it manually in terminal, but the results are the same: X-server fails to load the graphical environment.  

Before anyone asks, I've done all the cancelling out of "Load DRI" and added "nvidia" and the other steps in NVIDIA's readme.  That is apparently successful in telling the system to load a driver which, alas, isn't.  I'm not expecting wonderful things from my crapply little video card (that's what November is for), but I'd like to load the NVIDIA driver just to prevent the inevitable screen corruption yielded by the default nv driver.  Having said that, who wouldn't want Opengl working?  I've managed to get my girlfriend hooked on Baldur's Gate (I think that deserves a standing ovation, actually), so when BG2 time comes around, I'd like to have her play that in Ubuntu, rather than Winblows.  

Any and all help appreciated.  You can even be nasty and derogatory while helping me, as long as you're funny, too. ](*,)[/QUOTE]
Open either Terminal or Konsole and type:
sudo gedit /etc/X11/xorg.conf (if you use GNOME)

or

sudo kate /etc/X11/xorg.conf (if you use KDE)

and post the file, please.

I have my last exam in 2 days (5 september) and I'm studying really hard. I'll have much more time to help you after the exam (if I pass it).

---

### Post by TakisX on 2005-09-03
My problem is i have a Sony tft monitor with dvi conection.I can not select resolution bigger of 1024 768 my conf file is 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

the 1280x1024 was put by me ( aforum in Greece says so )

---

### Post by TakisX on 2005-09-03
My problem is i have a Sony tft monitor with dvi conection.I can not select resolution bigger of 1024 768 my conf file is
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
# sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
# sudo dpkg-reconfigure xserver-xorg

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV20 [GeForce3]"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-49
VertRefresh 43-72
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV20 [GeForce3]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

the 1280x1024 was put by me ( aforum in Greece says so )

---

### Post by tseliot on 2005-09-03
[QUOTE=TakisX]Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
[COLOR=Red]#Load "dri"[/COLOR]
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection
[/QUOTE]
First of all look at the red line and set it as in the example

And about the resolution issue:

Find the supported refresh rates (Horizontal and Vertical refresh) in the manual of your monitor. Or find it in google.

and put the rates in these lines in red

[QUOTE=TakisX]
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[COLOR=Red]HorizSync 28-49[/COLOR]
[COLOR=Red]VertRefresh 43-72[/COLOR]
EndSection[/QUOTE]


Then log out and log in.

Try to select the resolution you want

---

### Post by DancingSun on 2005-09-03
It's also possible to have X automatically detect your monitor's supported refresh rates, although this doesn't always work.  Just comment out the two refresh rate lines above (put a "#" in front of the lines), and restart the computer (just to be sure).  If this doesn't work, you can try entering the refresh rate values manually.

Also, according to the xorg.conf you posted, it seems like you have to have 24-bit color enabled to be able to get 1280x1024.  And that resolution is the highest it can go.

---

### Post by TakisX on 2005-09-04
Thanks it worked the trick with # in xorg.conf but the disaster came.
I tried ti install the new drivers and 
1 unistalled nvidia-glx
2 clt-alt -f1
3 stoped gdm
4 gave sudo sh nvidia-linux-x86-1.0-7667-pkg1.run and gave an error message about some module in kernel
5 gave /etc/init.d/gdm start    and Failed Gnome does not start
reboot xserver does not load
gave sudo xorgconfig followed the steps the same failed
Disaster 
Please help
gave sudo apt-get install nvidia-glx to install the old drivers but i cant get Gnome

---

### Post by tseliot on 2005-09-04
[QUOTE=TakisX]Thanks it worked the trick with # in xorg.conf but the disaster came.
I tried ti install the new drivers and 
1 unistalled nvidia-glx
2 clt-alt -f1
3 stoped gdm
4 gave sudo sh nvidia-linux-x86-1.0-7667-pkg1.run and gave an error message about some module in kernel
5 gave /etc/init.d/gdm start    and Failed Gnome does not start
reboot xserver does not load
gave sudo xorgconfig followed the steps the same failed
Disaster 
Please help
gave sudo apt-get install nvidia-glx to install the old drivers but i cant get Gnome[/QUOTE]
It will boot in the command line.

sudo nano /etc/X11/xorg.conf

and set "nvidia" back to either "nv" or "vesa"

save and exit. Reboot.

If this works (it should) please post the nvidia log file (you can find it under /var/log)

---

### Post by TakisX on 2005-09-04
Nothing worked . I installed Ubuntu again .
What can i do with that error message for kernel ? Recompile the kernel ?

---

### Post by tseliot on 2005-09-04
[QUOTE=TakisX]Nothing worked . I installed Ubuntu again .
What can i do with that error message for kernel ? Recompile the kernel ?[/QUOTE]
1) which kernel are you using?
if you don't know: open Terminal or Konsole and type "uname -r"

2) try to run the nvidia installer WITHOUT following ANY OTHER thing in my guide:
i.e. Just follow (ONLY) the instructions below


QUOTE:
---------------------------------------------------------------------------------------------------------------------------------
uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

click on the files and select "Mark for installation"

Press the "Apply" button.

You can close Synaptic (or Kynaptic) after it has finished installing the headers.


1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc (just in case)

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd “directory where you have the nvidia installer”

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run


sudo /etc/init.d/gdm start
--------------------------------------------------------------------------------------------------------------------------------

3) get to /var/log/ and look for "nvidia-installer.log" and post the content of the file.

In this way I will see the complete error output.

---

### Post by DariusTriplet on 2005-09-05
Hey,

I'm running Hoary, and tried to install the newest drivers.  I was able to install without a problem, but upon startup, X crashes.  I checked the X log, and it stated that it couldn't load the Nvidia kernel modules.  The strange part is, according to dmesg, the modules -did- load.

I cannot post dmesg, X log, or the install log at the moment, as I'm posting this via Links.  If it's possible to copy/paste the text into here, though, I'll see what I can do about posting those.

Thanks in advance!

---

### Post by tseliot on 2005-09-05
[QUOTE=DariusTriplet]Hey,

I'm running Hoary, and tried to install the newest drivers.  I was able to install without a problem, but upon startup, X crashes.  I checked the X log, and it stated that it couldn't load the Nvidia kernel modules.  The strange part is, according to dmesg, the modules -did- load.

I cannot post dmesg, X log, or the install log at the moment, as I'm posting this via Links.  If it's possible to copy/paste the text into here, though, I'll see what I can do about posting those.

Thanks in advance![/QUOTE]
1) What's the model of your graphic card?
2) Can you post your /etc/X11/xorg.conf?

---

### Post by DariusTriplet on 2005-09-05
[QUOTE=tseliot]1) What's the model of your graphic card?
2) Can you post your /etc/X11/xorg.conf?[/QUOTE]

1) Fx5600

2) (All irrelevant information, such as InputDevice, have been removed for this post)

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
#        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection

---

### Post by muzzie on 2005-09-06
OK... I've got a problem.

I followed your guide (which is excellent, btw), tseliot,and got my nvidia drivers installed and running fine (or so I thought).
I have been using them for the last week or so with no trouble, but I hadn't done any 3d stuff yet.

Today I installed the game Enemy Territory, and it would load, but was very slow.  I went ingame and it would play at 15-30fps and all the textures/graphics were very low quality.  My machine is a 3000+ Athlon 64 paired with a GeForce 6800 GT, so obviously something was wrong with my software.

I then noticed that my OpenGL screensavers were just black in preview, and would not start when I tried to test them.  Finnaly, I ran glxgears and the results are pitiful, 14fps.  Yes, 14fps glxgears, on a brand spankin' new system that plays Half Life 2 at 100+ FPS under Winblows.

So, I am thinking something is wrong with my OpenGL drivers.  I am very new to Linux, only a week or so, but I'm enjoying it despite all the little problems I've come across.   
Normally I'd spend hours crawling around on Google to figure this out, but I see you are a helpful guy who knows this stuff pretty well, so I thought I'd ask...
What the heck is going on? :D

---

### Post by tseliot on 2005-09-06
[QUOTE=DariusTriplet]1) Fx5600

2) (All irrelevant information, such as InputDevice, have been removed for this post)

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
#        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection[/QUOTE]
Try point 4 in the problem section of my guide

---

### Post by tseliot on 2005-09-06
[QUOTE=muzzie]OK... I've got a problem.

I followed your guide (which is excellent, btw), tseliot,and got my nvidia drivers installed and running fine (or so I thought).
I have been using them for the last week or so with no trouble, but I hadn't done any 3d stuff yet.

Today I installed the game Enemy Territory, and it would load, but was very slow.  I went ingame and it would play at 15-30fps and all the textures/graphics were very low quality.  My machine is a 3000+ Athlon 64 paired with a GeForce 6800 GT, so obviously something was wrong with my software.

I then noticed that my OpenGL screensavers were just black in preview, and would not start when I tried to test them.  Finnaly, I ran glxgears and the results are pitiful, 14fps.  Yes, 14fps glxgears, on a brand spankin' new system that plays Half Life 2 at 100+ FPS under Winblows.

So, I am thinking something is wrong with my OpenGL drivers.  I am very new to Linux, only a week or so, but I'm enjoying it despite all the little problems I've come across.   
Normally I'd spend hours crawling around on Google to figure this out, but I see you are a helpful guy who knows this stuff pretty well, so I thought I'd ask...
What the heck is going on? :D[/QUOTE]

Can you post your /etc/X11/xorg.conf?

---

### Post by muzzie on 2005-09-06
Sure, here ya go, attached to this post.

---

### Post by tseliot on 2005-09-06
[QUOTE=muzzie]Sure, here ya go, attached to this post.[/QUOTE]
Which driver version did you install? (7667, 7676,etc.)

---

### Post by muzzie on 2005-09-06
I installed 7676.  I know now that you recommend that folks use 7667 unless they have a 7800, but somehow I didn't remember that when getting the drivers.

Still though, could the 7676 drivers really be causing all the trouble I'm having? If you think that's the case, I could do a driver reinstall I suppose.

---

### Post by tseliot on 2005-09-06
[QUOTE=muzzie]I installed 7676.  I know now that you recommend that folks use 7667 unless they have a 7800, but somehow I didn't remember that when getting the drivers.

Still though, could the 7676 drivers really be causing all the trouble I'm having? If you think that's the case, I could do a driver reinstall I suppose.[/QUOTE]
I think it's worth a try (use 7667).

---

### Post by TakisX on 2005-09-06
Disaster help.
I installed the kernel 2.6.11 with synaptic ,everything ok . Reboot and when goew to Desktop freezes.Reboot the same.Reboot with the old kernel everything ok.

I follow your how to to install nvidia drivers.When i give sudo sh Nvidia ..... it says somethind about a mising modules and compiles it .Everything ok it says.I give sudo /etc/init.d/gdm start  and canot load xserver .Black screen.
Reboot in command line. I type sudo gedit /etc/X11/xorg.conf to see what it says
and get

GK-warning ** : cannot open display
every log file i try open the same
Disaster (not install ubuntu again) i cnt get grafical gui .
p.s. how it is posible to install kernrl form synaptic and not working ?

---

### Post by tseliot on 2005-09-06
[QUOTE=TakisX]Disaster help.
I installed the kernel 2.6.11 with synaptic ,everything ok . Reboot and when goew to Desktop freezes.Reboot the same.Reboot with the old kernel everything ok.

I follow your how to to install nvidia drivers.When i give sudo sh Nvidia ..... it says somethind about a mising modules and compiles it .Everything ok it says.I give sudo /etc/init.d/gdm start  and canot load xserver .Black screen.
Reboot in command line. I type sudo gedit /etc/X11/xorg.conf to see what it says
and get

GK-warning ** : cannot open display
every log file i try open the same
Disaster (not install ubuntu again) i cnt get grafical gui .
p.s. how it is posible to install kernrl form synaptic and not working ?[/QUOTE]
It's not a disaster: of course gedit doesn't work when the gui is not running.

Type this instead:

sudo nano /etc/X11/xorg.conf

and set "nvidia" back to "nv" or "vesa"

CTRL+O to overwrite the file
CTRL+X to exit

Then:

sudo /etc/init.d/gdm start

---

### Post by TakisX on 2005-09-06
I did that and xserver started.
I installed with synaptic the nvidia driver and made vesa nvidia to xorg.conf
reboot
and the xserver does not begin
it says module already started


It makes crazy something so simple in win driver instalation to be so dificult
In the nvidia - linux forum so many with the same problem

Why the kernel instalation with synaptic does not work is crazy ?

---

### Post by TakisX on 2005-09-06
I install ubuntu one more time.If ican not setup this OS to work properly good bye Linux .I like the linux idea but is years behind windows in usability ,so sory about it.

Nvidia so big company and no drivers for Linux ,Shame

---

### Post by tseliot on 2005-09-07
[QUOTE=TakisX]I install ubuntu one more time.If ican not setup this OS to work properly good bye Linux .I like the linux idea but is years behind windows in usability ,so sory about it.

Nvidia so big company and no drivers for Linux ,Shame[/QUOTE]
Calm down. Repeat the step from the command line and set "nvidia" back to "nv".

The driver you can install in synaptic didn't work for me. I use the installer.

Which is you graphic card model?

---

### Post by TakisX on 2005-09-07
But if i change nvidia to nv the resolution is only 1024 768 and refresh rate is 0 ???
My card is Geforce3 (agp)  my display Sony tft with dvi

Finally when you install a nvidia driver what is right at xorg.conf  ? nvidia vesa nv ?

---

### Post by tseliot on 2005-09-07
[QUOTE=TakisX]But if i change nvidia to nv the resolution is only 1024 768 and refresh rate is 0 ???
My card is Geforce3 (agp)  my display Sony tft with dvi

Finally when you install a nvidia driver what is right at xorg.conf  ? nvidia vesa nv ?[/QUOTE]
CTRL+ALT+F1

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

it will ask you several things(if you don't know the answer just press Enter):

Tell it to autodetect the card and then select "nv".

It will ask you (I don't remember when) you desired resolutions:

select the one you need and press the spacebar to enable it (press Enter when you've finished)

When it comes to the refresh rate question select "advanced" and put the values of your monitor (horizontal and vertical refresh)

sudo /etc/init.d/gdm start

I hope it works now

---

### Post by Owdy on 2005-09-07
Trying to update. There arent installer in latest package, just makefile. Make install gives Makefile:17: *** missing separator.  Stop.


Other thing, my corg.conf says
Section "Device"
	Identifier	"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"

I have GF 5200 now. That is my old card. Does it matter?

---

### Post by tseliot on 2005-09-08
[QUOTE=Owdy]Trying to update. There arent installer in latest package, just makefile. Make install gives Makefile:17: *** missing separator.  Stop.


Other thing, my corg.conf says
Section "Device"
	Identifier	"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"

I have GF 5200 now. That is my old card. Does it matter?[/QUOTE]
Trying to update from what? From the installer or from synaptic?

---

### Post by Owdy on 2005-09-08
I try to update my driver. I downloaded package from there [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) , but those packages dont have installers in it.

And, my corg.conf is outdated. I have differend card now. I have no idea what to put in that.


Section "Device"
Identifier "NVIDIA Corporation NV15DDR [GeForce2 Ti]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo"

---

### Post by tseliot on 2005-09-08
[QUOTE=Owdy]I try to update my driver. I downloaded package from there [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) , but those packages dont have installers in it.

And, my corg.conf is outdated. I have differend card now. I have no idea what to put in that.


Section "Device"
Identifier "NVIDIA Corporation NV15DDR [GeForce2 Ti]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo"[/QUOTE]
for example "NVIDIA-Linux-x86-1.0-7676-pkg1.run" IS an installer.

If you want to update the name of your card:
CTRL+ALT+F1

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

it will ask you several things(if you don't know the answer just press Enter):

Tell it to autodetect the card and then select "nvidia".

And so on.

sudo /etc/init.d/gdm start

---

### Post by Owdy on 2005-09-08
There arent any .pkg1.run file in that package: [http://download.nvidia.com/freebsd/1.0-7676/NVIDIA-FreeBSD-x86-1.0-7676.tar.gz](http://download.nvidia.com/freebsd/1.0-7676/NVIDIA-FreeBSD-x86-1.0-7676.tar.gz)

---

### Post by tseliot on 2005-09-08
[QUOTE=Owdy]There arent any .pkg1.run file in that package: [http://download.nvidia.com/freebsd/1.0-7676/NVIDIA-FreeBSD-x86-1.0-7676.tar.gz](http://download.nvidia.com/freebsd/1.0-7676/NVIDIA-FreeBSD-x86-1.0-7676.tar.gz)[/QUOTE]
Why are you trying to install the drivers for BSD???
Remember that this is an Ubuntu forum

BSD is not Linux

---

### Post by tseliot on 2005-09-08
select "Linux IA32" in this page [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Owdy on 2005-09-08
LOL. I shoyuld learn how to read. Sorry. Ill try with that :D

---

### Post by tseliot on 2005-09-08
[QUOTE=Owdy]LOL. I shoyuld learn how to read. Sorry. Ill try with that :D[/QUOTE]
No problem  :)

---

### Post by Owdy on 2005-09-08
Yes, worked.

Now i have this:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"NoLogo"

That driver part was 'nv' after reinstall, changed that to 'nvidia'. What is that UseFBDev part, it wasnt there before?

---

### Post by tseliot on 2005-09-08
[QUOTE=Owdy]Yes, worked.

Now i have this:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"NoLogo"

That driver part was 'nv' after reinstall, changed that to 'nvidia'. What is that UseFBDev part, it wasnt there before?[/QUOTE]
I have no idea, I had never noticed it (and I can't check it on my computer because I don't have it now).

However if it works properly don't you worry...  :)

---

### Post by vayu on 2005-09-08
After a bit of struggling I finally got the driver to compile and install succesfully. Yay!  

But now whenever I try to run anything OpenGL I get a segmentation error.  Even glxinfo gives me the error.   I have an eVGA GeForce 6200 (AGP).  I have my xorg.conf set the way you describe.  I used the 7667 driver.  I unistalled nvidia-glx first.  I don't know where to go from here.

---

### Post by tseliot on 2005-09-08
[QUOTE=vayu]After a bit of struggling I finally got the driver to compile and install succesfully. Yay!  

But now whenever I try to run anything OpenGL I get a segmentation error.  Even glxinfo gives me the error.   I have an eVGA GeForce 6200 (AGP).  I have my xorg.conf set the way you describe.  I used the 7667 driver.  I unistalled nvidia-glx first.  I don't know where to go from here.[/QUOTE]
Look at point 4 in the Problems section of my guide

---

### Post by Cinjun on 2005-09-08
Super HOWTO tseliot, no problems whatsoever, Worked like a charm. Thanks again. :)

---

### Post by wmaddler on 2005-09-08
Very useful.
It worked (breezy C4 on AMD64). Everything went fine, but I had to (discover  ](*,) and) remove /usr/X11R6/lib/modules/extensions/libglx.a which prevented glx extension to properly work. 

The file is provided by xerver-core, so it will have to be removed every time you update dat package.

Best regards...

---

### Post by vayu on 2005-09-08
Where can I look up the "Option" values in xorg.conf (under device)?

---

### Post by tseliot on 2005-09-09
[QUOTE=vayu]Where can I look up the "Option" values in xorg.conf (under device)?[/QUOTE]
If you want to add them follow the example:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

Usually there are no options set by default

---

### Post by tseliot on 2005-09-09
[QUOTE=wmaddler]Very useful.
It worked (breezy C4 on AMD64). Everything went fine, but I had to (discover  ](*,) and) remove /usr/X11R6/lib/modules/extensions/libglx.a which prevented glx extension to properly work. 

The file is provided by xerver-core, so it will have to be removed every time you update dat package.

Best regards...[/QUOTE]
thanks for the tip

---

### Post by TakisX on 2005-09-09
I compiled the new driver. HERE is a part of my log file .A lot of warnings. Do you see something wrong ?

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Sep  9 22:20:09 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> There appears to already be a driver installed on your system (version: 1.0-
   7667).  As part of installing this driver (version: 1.0-7667), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.13-maria/source'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.13-maria/so
   urce SYSOUT=/lib/modules/2.6.13-maria/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc KBUILD_OUTPUT=/lib/modules/2.6.13-maria/build KBUILD_VERBOSE=1 -C
   /lib/modules/2.6.13-maria/source SUBDIRS=/tmp/selfgz7853/NVIDIA-Linux-x86-1.
   0-7667-pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.13-maria/build		\
 
   
   -> done.
-> Kernel module compilation complete.
-> Installing both new and classic TLS OpenGL libraries.
-> Parsing log file:
-> done.
-> Validating previous installation:
-> Unable to access previously installed file
   '/usr/X11R6/lib/modules/drivers/nvidia_drv.o' (No such file or directory).
-> Unable to access previously installed file '/usr/X11R6/lib/libXvMCNVIDIA.a'
   (No such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-settings' (No
   such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-bug-report.sh'
   (No such file or directory).
-> Unable to access previously installed file
   '/lib/modules/2.6.10-5-386/kernel/drivers/video/nvidia.ko' (No such file or
   directory).
-> Unable to access previously installed file '/usr/lib/libGL.la' (No such file
   or directory).
-> Unable to access previously installed symlink
   '/usr/X11R6/lib/modules/extensions/libglx.so' (No such file or directory).
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than the nvidia-installer
         (such as rpm or with the NVIDIA tarballs).  The nvidia-installer will
         attempt to uninstall as best it can.  Please see the file
         '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-7667):
-> Unable to restore symbolic link /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa ->
   libGL.so.1.2 (No such file or directory).
ERROR: Unable to create '/usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa' for
       copying (No such file or directory)
WARNING: Unable to restore file '/usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa'.
ERROR: Unable to create '/usr/X11R6/lib/nvidia/libGLcore.a.xlibmesa' for
       copying (No such file or directory)
WARNING: Unable to restore file '/usr/X11R6/lib/nvidia/libGLcore.a.xlibmesa'.
ERROR: Unable to create '/usr/X11R6/lib/nvidia/libglx.a.xlibmesa' for copying
       (No such file or directory)
WARNING: Unable to restore file '/usr/X11R6/lib/nvidia/libglx.a.xlibmesa'.
-> Unable to restore symbolic link /usr/lib/nvidia/libGL.so.1.xlibmesa ->
   libGL.so.1.2 (No such file or directory).
-> Unable to restore symbolic link /usr/lib/nvidia/libGL.so.1.2.xlibmesa ->
   ../X11R6/lib/libGL.so.1.2 (No such file or directory).
ERROR: Unable to create '/usr/lib/nvidia/libnvidia-tls.so.1.0.7174' for copying
       (No such file or directory)
WARNING: Unable to restore file '/usr/lib/nvidia/libnvidia-tls.so.1.0.7174'.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (1.0-7667) is complete.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-7667):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-7667) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.

---

### Post by tseliot on 2005-09-09
Does the driver work?

By the way try to type this in the command line:

sudo ln -s  /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa libGL.so.1.2

---

### Post by vayu on 2005-09-10
> **tseliot]If you want to add them follow the example:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" &#8220 said:**
> 

Usually there are no options set by default
 I mean where do you find out about those options? Which ones are available, what they do, etc....

---

### Post by Resin on 2005-09-10
Thanks buddy, this thread is wicked.  Its the first one I've found that actually worked!  :grin:

---

### Post by tseliot on 2005-09-10
[QUOTE=vayu]I mean where do you find out about those options? Which ones are available, what they do, etc....[/QUOTE]
As I said before there are no options set by default.

The options are useful if you have any problems with the driver.

Some of them disable 3d acceleration.

However if you want to know something more about them you can ask at this forum (maybe the developers themselves will answer you)

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) 

P.S. if you don't have any problems, please don't mess with them

---

### Post by tseliot on 2005-09-10
[QUOTE=Resin]Thanks buddy, this thread is wicked.  Its the first one I've found that actually worked!  :grin:[/QUOTE]
Thanks, I'm happy for you  :)

---

### Post by TakisX on 2005-09-10
This driver is mystery to me.
I downloaded installed with your how to.If i put nvidia and not nv in xorg.conf the system dont reboot .If iput nv ok .I recompiled the original kernel , the new kernel 2.6.13 , i tried everything. 

I read this forum the nvidia forum nothing works .
Why ?

---

### Post by tseliot on 2005-09-10
[QUOTE=TakisX]This driver is mystery to me.
I downloaded installed with your how to.If i put nvidia and not nv in xorg.conf the system dont reboot .If iput nv ok .I recompiled the original kernel , the new kernel 2.6.13 , i tried everything. 

I read this forum the nvidia forum nothing works .
Why ?[/QUOTE]
Try to add the red lines to your xorg.conf:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

Log oout and login

---

### Post by busboy.ca on 2005-09-10
Thanks Alberto. Molto bene bello.  :)

---

### Post by tseliot on 2005-09-10
[QUOTE=busboy.ca]Thanks Alberto. Molto bene bello.  :)[/QUOTE]
Grazie a te  :)

---

### Post by TakisX on 2005-09-10
If i put the lines you say freezes even i put nv in xorg.conf
At the other forum a lot of people ungry with nvidia because the drivers dont work
The last driver they say is 6629 that worked ok

Why a big firm like  nvidia does not fix it ?

---

### Post by tseliot on 2005-09-10
[QUOTE=TakisX]If i put the lines you say freezes even i put nv in xorg.conf
At the other forum a lot of people ungry with nvidia because the drivers dont work
The last driver they say is 6629 that worked ok

Why a big firm like  nvidia does not fix it ?[/QUOTE]
Because they focus more on Windows drivers than on Linux ones. And Games are developed for Windows.

By the way you could give Breezy (stable) a shot (13th october) as it has 7667 nvidia driver modules available in the repositories. Please try to be patient until then (I understand your frustration though).

---

### Post by TheTK421 on 2005-09-10
Well add me to the list of failures when trying to install these drivers. Right after I installed them I rebooted X, got the Nvidia screen, then it dumped me out to command line. I was able to uninstall the "glx" package, then restore from a copy of xorg.conf I kept for situations like this. It will only boot into GDM if I am root, and even then it I have about a 1-in-a-hundred chance of it working, or it will just boot to the gray screen with the "x" for the mouse pointer until I restart the computer. Recently I have been getting a blue screen with an error box asking me if I wish to look at the Xorg.0.log file to see if I can fix the problem, but it looks fine. I haven't had the courage to reboot my system for a few days now and I don't plan on ever rebooting it.  
Is there anyway to fix this? I finally went through the horrible process of getting KDE installed, just so I could never use it. I can post a copy of my xorg.conf and the backup I have used if it would help. 

I have searched the nVidia forums to no avail. I would love to keep using Ubuntu, but I never had these problems with SuSE or any other distro I have used.

---

### Post by tseliot on 2005-09-11
[QUOTE=TheTK421]I can post a copy of my xorg.conf and the backup I have used if it would help.[/QUOTE]
Please post them.

And did the driver compile?

---

### Post by muzzie on 2005-09-11
Hey Tseilot,

You might remember a couple pages back I was having trouble with OpenGL.  glxgears was getting 14fps and my games weren't rendering properly at all.
You suggested I downgrade from 7676 to 7667 and I have just now finnaly got around to doing that, and, voila! It works great now.  Glxgears is giving 12,000+ and I am getting a solid 90fps (locked there) in Enemy Territory with all details at max @ 1024x768.

I thought the process was going to be a pain, but I simply just downloaded the 7667 drivers, stopped X and did a sh "NVIDA-blablablaDrivers" and the whole process was automated. Uninstalled 7676 and put 7667 in.  I don't know if that's the safest way to go about it, but no problems so far!

Thanks!

---

### Post by tseliot on 2005-09-11
[QUOTE=muzzie]Hey Tseilot,

You might remember a couple pages back I was having trouble with OpenGL.  glxgears was getting 14fps and my games weren't rendering properly at all.
You suggested I downgrade from 7676 to 7667 and I have just now finnaly got around to doing that, and, voila! It works great now.  Glxgears is giving 12,000+ and I am getting a solid 90fps (locked there) in Enemy Territory with all details at max @ 1024x768.

I thought the process was going to be a pain, but I simply just downloaded the 7667 drivers, stopped X and did a sh "NVIDA-blablablaDrivers" and the whole process was automated. Uninstalled 7676 and put 7667 in.  I don't know if that's the safest way to go about it, but no problems so far!

Thanks![/QUOTE]
Of course I remember of you  ;-)  . Well, let's say there's a reason if I discourage users from installing 7676. The way you installed the new driver is right (so don't you worry). 

I'm very happy for you!  :)

---

### Post by Zillion on 2005-09-11
[QUOTE=tseliot].. in my case "nv" drivers= screen corruption, nvidia drivers (the ones you can install following Ubuntu Starter Guide) =black screen, no Xorg...[/QUOTE]

could you plz explain me (=noob) how to get the display driver working after installing Ubuntu (Hoary). At the moment Xserver should start I get black screen, though I can get in the shell with ctrl alt f1.
I have MSI Neo4 Nforce4 Platinum board with Nvidia 6800gt vga

tx

edit -> forget it, I changed in xorg.conf driver from NV to Vesa, and now I have visuals :)

---

### Post by 23meg on 2005-09-13
i've just got a new computer with a nvidia geforce go6200 chip. i've done everything exactly as specified in this thread, yet i'm still getting the dreaded blackout. and with ubuntu's "nv" driver x does start, but gnome hangs on startup (it plays the startup sound after login, the mouse pointer works, but no splash, no desktop, nothing, just a brown screen). 

in short i just can't run ubuntu any more! the device and module sections of my xorg.conf are exactly the same as those on tseliot's first post. i'm trying with the 7667 driver + stock hoary kernel, and there were no errors in the driver installation.

any help appreciated.

 ](*,)   ](*,)   ](*,)

---

### Post by tseliot on 2005-09-13
[QUOTE=23meg]i've just got a new computer with a nvidia geforce go6200 chip. i've done everything exactly as specified in this thread, yet i'm still getting the dreaded blackout. and with ubuntu's "nv" driver x does start, but gnome hangs on startup (it plays the startup sound after login, the mouse pointer works, but no splash, no desktop, nothing, just a brown screen). 

in short i just can't run ubuntu any more! the device and module sections of my xorg.conf are exactly the same as those on tseliot's first post. i'm trying with the 7667 driver + stock hoary kernel, and there were no errors in the driver installation.

any help appreciated.

 ](*,)   ](*,)   ](*,)[/QUOTE]
I'm afraid I can't help you with that card. However I can recommend you to make a search in the nvidia forum (you can follow the link at the end of the 1st page of my guide) or start a new thread in there and ask for help. The (nvidia) developers of the drivers can help you in there.

---

### Post by TheTK421 on 2005-09-13
Sorry it took me so long to get back to you with the file (working on my C++)

Here is the backup and current xorg.conf file I am using.

If there is anything else you need please ask, I would love to have 3d support.

---

### Post by linkunderscore on 2005-09-14
I used this guide to help me install my nvidia drivers about 3 weeks ago. Worked great.

After this last Ubuntu Update, my system wouldn't start X. I would get the nvidia splash then it would crash into commandline. After some digging I found that the update required me to manually change "Keyboard" to "kbd" and "nvidia" to "nv" in order to startX. 

I was wondering...If i re-install these drivers again(following the same instructions), would it b0rk on start up again? 

I'd leave it "nv" except I can't play UT2004 or any game for that matter.

---

### Post by tseliot on 2005-09-14
[QUOTE=linkunderscore]I used this guide to help me install my nvidia drivers about 3 weeks ago. Worked great.

After this last Ubuntu Update, my system wouldn't start X. I would get the nvidia splash then it would crash into commandline. After some digging I found that the update required me to manually change "Keyboard" to "kbd" and "nvidia" to "nv" in order to startX. 

I was wondering...If i re-install these drivers again(following the same instructions), would it b0rk on start up again? 

I'd leave it "nv" except I can't play UT2004 or any game for that matter.[/QUOTE]
Follow my guide again and reinstall the drivers, it will work (probably the update upgraded your kernel)

---

### Post by tseliot on 2005-09-14
[QUOTE=TheTK421]Sorry it took me so long to get back to you with the file (working on my C++)

Here is the backup and current xorg.conf file I am using.

If there is anything else you need please ask, I would love to have 3d support.[/QUOTE]
Follow my guide again and add the lines in red to your xorg.conf (see the example below)

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"[/COLOR]

If this doesn't work you can try to add the other lines as shown in point 4 of the problems section of my guide.

Tell me if it works

---

### Post by draugen on 2005-09-14
just a quick note on the 32bit compatibility libraries for x86_64: you can install them with this hack:

```

sudo mkdir /emul/ia32-linux/usr/
sudo ln -s /usr/lib32 /emul/ia32-linux/usr/lib

``` 

if /usr/lib32 does not exist, you need to do this

```
sudo apt-get install ia32-libs lib32gcc1 lib32stdc++6
```

without which the opengl compat libs probably won't be much use anyway :)

there are more 32bit libs as well. check synaptic :)


--martin

edited for clarity :)

---

### Post by tseliot on 2005-09-14
[QUOTE=draugen]just a quick note on the 32bit compatibility libraries for x86_64: you can install them with this hack:

```

sudo mkdir /emul/ia32-linux/usr/
sudo ln -s /usr/lib32 /emul/ia32-linux/usr/lib

``` 

if /usr/lib32 does not exist, you need to do this

```
sudo apt-get install ia32-libs lib32gcc1 lib32stdc++6
```

without which the opengl compat libs probably won't be much use anyway :)

there are more 32bit libs as well. check synaptic :)


--martin

edited for clarity :)[/QUOTE]

I can't try it (I'm running Ubuntu 32bit in this period) but I can add it to my guide later (I'm studying for an exam).

Thanks for the tip!

---

### Post by draugen on 2005-09-14
[QUOTE=tseliot]I can't try it (I'm running Ubuntu 32bit in this period) but I can add it to my guide later (I'm studying for an exam).

Thanks for the tip![/QUOTE]
happy to help!

 oh... one thing. you probably need to break up the mkdir command:
```

sudo mkdir /emul
sudo mkdir /emul/ia32-linux
sudo mkdir /emul/ia32-linux/usr

```

---

### Post by 23meg on 2005-09-14
i've tried again, this time with the 2.6.11 kernel, and i can now get the driver running only with the "Accel" "Off" option, but window moving and resizing are horribly, unusably slow. 

after months of low 2d performance from an ATI card, i specially looked for a laptop with a NVIDIA chip and bought one, and now look what i got in my hands...

anyone having these issues with the 2.6.12 kernel? i can't properly set it up now since ubuntu doesn't recognize my new ethernet adapter either and i can't connect to the net with my laptop... 

 ](*,)   ](*,)   ](*,)

---

### Post by tseliot on 2005-09-14
[QUOTE=23meg]i've tried again, this time with the 2.6.11 kernel, and i can now get the driver running only with the "Accel" "Off" option, but window moving and resizing are horribly, unusably slow. 

after months of low 2d performance from an ATI card, i specially looked for a laptop with a NVIDIA chip and bought one, and now look what i got in my hands...

anyone having these issues with the 2.6.12 kernel? i can't properly set it up now since ubuntu doesn't recognize my new ethernet adapter either and i can't connect to the net with my laptop... 

 ](*,)   ](*,)   ](*,)[/QUOTE]
Use kernel 2.6.11 and try this:

1) Delete the "Accel" "Off" option

2) add the lines in red to your xorg.conf

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR=Red]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

In this way the acceleration should work.

Tell me if it works

---

### Post by tseliot on 2005-09-14
Of course everytime you change your kernel you have to reinstall the nvidia drivers

---

### Post by 23meg on 2005-09-14
i've tried that, it doesn't work. the only way to get past the splash screen is to use "Accel" "Off" or use the vesa driver. in both cases i get 16bit color depth, and low 2d performance, plus my laptop's native resolution of 1400x1050 is unavailable in vesa. in short, all is bad.

i also tried the latest 7676 driver, and it just totally crashes x.

i'm now downloading the breezy preview at an internet cafe to see if the 2.6.12 kernel plays well with my go6200 chip... i'm that desperate.



 ](*,)   ](*,)    ](*,)

---

### Post by tseliot on 2005-09-14
[QUOTE=23meg]i've tried that, it doesn't work. the only way to get past the splash screen is to use "Accel" "Off" or use the vesa driver. in both cases i get 16bit color depth, and low 2d performance, plus my laptop's native resolution of 1400x1050 is unavailable in vesa. in short, all is bad.

i also tried the latest 7676 driver, and it just totally crashes x.

i'm now downloading the breezy preview at an internet cafe to see if the 2.6.12 kernel plays well with my go6200 chip... i'm that desperate.



 ](*,)   ](*,)    ](*,)[/QUOTE]
I don't think Breezy can solve your problem. It's a matter of hardware compatibility. Please ask for help (register there and start a new thread) at the nvidia forum (at the Linux section). Only the developers can help you and you might also find other users who have the same problem (they might have solved the problem).

I can't help you as there are some problems with Geforce Go in Linux (and I don't have such a graphic card)

---

### Post by 23meg on 2005-09-14
my only reason for trying breezy is the 2.6.12 kernel, since i have no way of installing it on top of hoary right now. the driver is very "kernel sensitive" so it may "play better" with the newer kernel. plus almost half of all hardware on my Tecra M4 isn't detected by hoary, so i'm hoping the newer kernel will provide better hardware support as well.

if all fails i may have to abandon ubuntu altogether (i can't believe i'm saying this!  :-#  )... or replace my laptop (i don't want to do that either)...

btw, i've posted on the nvnews forum as well. i hope the folks there come up with something.

 ](*,)

---

### Post by tseliot on 2005-09-14
[QUOTE=23meg]my only reason for trying breezy is the 2.6.12 kernel, since i have no way of installing it on top of hoary right now. the driver is very "kernel sensitive" so it may "play better" with the newer kernel. plus almost half of all hardware on my Tecra M4 isn't detected by hoary, so i'm hoping the newer kernel will provide better hardware support as well.

if all fails i may have to abandon ubuntu altogether (i can't believe i'm saying this!  :-#  )... or replace my laptop (i don't want to do that either)...

btw, i've posted on the nvnews forum as well. i hope the folks there come up with something.

 ](*,)[/QUOTE]
If you add Breezy repositories you can install kernel image header and source (2.6.12-8) in Synaptic.

Then restart your computer and try again. (remember to delete the new repos after the process)

---

### Post by 23meg on 2005-09-14
[QUOTE=tseliot]If you add Breezy repositories you can install kernel image header and source (2.6.12-8) in Synaptic.

Then restart your computer and try again. (remember to delete the new repos after the process)[/QUOTE]

i know, but i can't do that, since Hoary doesn't recognize my new laptop's Marvell/Yukon ethernet adapter and i can't connect to the net using Ubuntu, and grabbing the 2.6.12 kernel + headers from packages.ubuntu.com with all their dependencies one by one is a royal pain.

i'm now installing Breezy on the laptop. i'll post back and report how things went.

---

### Post by TakisX on 2005-09-14
The nvidia driver is just a broken thing .
Another try ( 1000000 times )
here what i get
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Sep 15 00:20:50 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : false
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> There appears to already be a driver installed on your system (version: 1.0-
   7667).  As part of installing this driver (version: 1.0-6629), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.13.1-dyo/source'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Performing rivafb module check.
WARNING: Your kernel was configured to include rivafb support as
         a loadable kernel module.
         
         The rivafb driver conflicts with the NVIDIA driver; the
         NVIDIA kernel module will still be built and installed,
         but be aware that the NVIDIA driver will not be able to
         function properly if the rivafb module is loaded!
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.13.1-dyo/so
   urce SYSOUT=/lib/modules/2.6.13.1-dyo/build'...
   Your kernel was configured to include rivafb support as
   a loadable kernel module.
   
   The rivafb driver conflicts with the NVIDIA driver; the
   NVIDIA kernel module will still be built and installed,
   but be aware that the NVIDIA driver will not be able to
   function properly if the rivafb module is loaded!
   
   *** Failed rivafb module sanity check, but continuing! ***
   
   
   NVIDIA: calling KBUILD...
   make CC=cc KBUILD_OUTPUT=/lib/modules/2.6.13.1-dyo/build KBUILD_VERBOSE=1 -C
   /lib/modules/2.6.13.1-dyo/source SUBDIRS=/tmp/selfgz12491/NVIDIA-Linux-x86-1
   .0-6629-pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.13.1-dyo/build		\
   KBUILD_SRC=/usr/src/linux-2.6.13.1	     KBUILD_VERBOSE=1	\
   KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1
   /usr/src/nv"	\
           -f /usr/src/linux-2.6.13.1/Makefile modules
   mkdir -p /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_ver
   sions
   make -f /usr/src/linux-2.6.13.1/scripts/Makefile.build obj=/tmp/selfgz12491/
   NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz12491/NV
   IDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc-lib/i486-linux/3.3.5/include -D__KERNEL
   __ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.13.1/include  -I/tmp/selfgz1249
   1/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wstrict-prototypes -Wno-t
   rigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame-po
   inter -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i686 -I/usr/src
   /linux-2.6.13.1/include/asm-i386/mach-default -Iinclude/asm-i386/mach-defaul
   t  -I/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -O -fno-common -MD -Wno-cast-qual -Wno-error
   -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KE
   RNEL_NAMES -D__KERNEL__ -DMODULE -DNV_MAJOR_VERSION=1 -DNV_MI
   NOR_VERSION=0 -DNV_PATCHLEVEL=6629 -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCP
   U_X86 -UDEBUG -U_DEBUG -DNDEBUG -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAG
   E_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -D
   MODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz12491/N
   VIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz12491/NVIDIA-L
   inux-x86-1.0-6629-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:52,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:870,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:75,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function
   `nvidia_init_module':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:930: warning
   : `pm_register' is deprecated (declared at include/linux/pm.h:107)
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function
   `nvidia_exit_module':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:1051: warnin
   g: `pm_unregister' is deprecated (declared at include/linux/pm.h:112)
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function
   `_get_phys_address':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2509: warnin
   g: passing arg 1 of `pmd_offset' from incompatible pointer type
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function
   `nv_agp_init':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2991: warnin
   g: implicit declaration of function `inter_module_get'
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2992: warnin
   g: `inter_module_put' is deprecated (declared at include/linux/module.h:573)
     cc -Wp,-MD,/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc-lib/i486-linux/3.3.5/include -D__KER
   NEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.13.1/include  -I/tmp/selfgz1
   2491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wstrict-prototypes -Wn
   o-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-frame
   -pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i686 -I/usr/
   src/linux-2.6.13.1/include/asm-i386/mach-default -Iinclude/asm-i386/mach-def
   ault  -I/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/
   src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -O -fno-common -MD -Wno-c
   ast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GN
   U_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_MAJOR_VERSION=1 -D
   NV_MINOR_VERSION=0 -DNV_PATCHLEVEL=6629 -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -
   DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANG
   E_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESE
   NT -DMODULE -DKBUILD_BASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfg
   z12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz124
   91/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:52,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:870,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:75,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c: At top l
   evel:
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c:59: warni
   ng: `cache_flush' defined but not used
     cc -Wp,-MD,/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc-lib/i486-linux/3.3.5/include -D__KE
   RNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.13.1/include  -I/tmp/selfgz
   12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wstrict-prototypes -W
   no-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os -fomit-fram
   e-pointer -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i686 -I/usr
   /src/linux-2.6.13.1/include/asm-i386/mach-default -Iinclude/asm-i386/mach-de
   fault  -I/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -W
   implicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wp
   ointer-arith -Wno-multichar -Werror -O -fno-common -MD -Wno-cast-qual -Wno-e
   rror -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOO
   SE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSIO
   N=0 -DNV_PATCHLEVEL=6629 -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDE
   BUG -U_DEBUG -DNDEBUG -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRE
   SENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DMODULE -DK
   BUILD_BASENAME=os_agp -DKBUILD_M
   ODNAME=nvidia -c -o /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/
   nv/.tmp_os-agp.o /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/
   os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:52,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:870,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/nv-linux.h:75,
                    from /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: At top 
   level:
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: erro
   r: syntax error before '*' token
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: warn
   ing: type defaults to `int' in declaration of `drm_agp_p'
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: warn
   ing: data definition has no type or storage class
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In func
   tion `KernInitAGP':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:76: warn
   ing: assignment discards qualifiers from pointer target type
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:85: erro
   r: request for member `acquire' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:88: warn
   ing: `inter_module_put' is deprecated (declared at include/linux/module.h:57
   3)
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:113: err
   or: request for member `copy_info' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:173: err
   or: request for member `enable' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:185: err
   or: request for member `release' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:186: war
   ning: `inter_module_put' is deprecated (declared at include/linux/module.h:5
   73)
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In func
   tion `KernTeardownAGP':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:216: err
   or: request for member `release' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:218: war
   ning: `inter_module_put' is deprecated (declared at include/linux/module.h:5
   73)
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In func
   tion `KernAllocAGPPages':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:265: err
   or: request for member `allocate_memory' in something not a structure or uni
   on
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:273: err
   or: request for member `bind_memory' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:290: err
   or: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:305: err
   or: request for member `free_memory' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In func
   tion `KernMapAGPPages':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:345: err
   or: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In func
   tion `KernFreeAGPPages':
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:444: err
   or: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:445: err
   or: request for member `free_memory' in something not a structure or union
   make[4]: *** [/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-
   agp.o] Error 1
   make[3]: *** [_module_/tmp/selfgz12491/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/sr
   c/nv] Error 2
   make[2]: *** [modules] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by 23meg on 2005-09-14
hell, i tried with a fresh install of Breezy, and it W O R K S !

everyone having trouble with 2.6.1x kernels: if all fails, try Breezy, or get the 2.6.12-8 kernel and follow tseliot's other guide for setting the drivers for use with the Breezy kernel.

2d performance is remarkably better than the vesa driver, and when it comes to 3d all i can say is that glxgears shows 4000-something fps. can you suggest a more reliable way to make sure 3d acceleration is working?

---

### Post by tseliot on 2005-09-14
[QUOTE=23meg]hell, i tried with a fresh install of Breezy, and it W O R K S !

everyone having trouble with 2.6.1x kernels: if all fails, try Breezy, or get the 2.6.12-8 kernel and follow tseliot's other guide for setting the drivers for use with the Breezy kernel.

2d performance is remarkably better than the vesa driver, and when it comes to 3d all i can say is that glxgears shows 4000-something fps. can you suggest a more reliable way to make sure 3d acceleration is working?[/QUOTE]
I'm happy for you and I really don't know why it works. I'm happy to be wrong though  ;-)

---

### Post by tseliot on 2005-09-14
for TakisX:

It's not a problem related to the driver this time. What kernel is yours? Did you compile it?

The kernel has  the nvidia Framebuffer module enabled and this won't make the driver work. You have to compile a new one (with that module disabled) OR You can try a Breezy kernel if you need kernel 2.6.12. It should work (install kernel image, source and headers) and Look at the problems section as the installer will complain about GCC.

---

### Post by linkunderscore on 2005-09-14
[QUOTE=tseliot]Follow my guide again and reinstall the drivers, it will work (probably the update upgraded your kernel)[/QUOTE]

It did. I love you :heart:

---

### Post by TakisX on 2005-09-15
It drives me crazy. I installed Ubuntu 5.10 .In synartic i see i have installed 7667 driver but it does not work .Why ?its so crazy. If i put nvidia or nv in xorg file it crushes.

What to do ? I want to have 1280x1024 and i have only 1024x768

If i put glxgears 

takisx@nisaki:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
takisx@nisaki:~$
what is the problem ? the kernel is the original 

Please help

---

### Post by TakisX on 2005-09-15
Here is my xorg.conf  file

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"2048x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"2048x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2005-09-15
[QUOTE=TakisX]It drives me crazy. I installed Ubuntu 5.10 .In synartic i see i have installed 7667 driver but it does not work .Why ?its so crazy. If i put nvidia or nv in xorg file it crushes.

What to do ? I want to have 1280x1024 and i have only 1024x768

If i put glxgears 

takisx@nisaki:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
takisx@nisaki:~$
what is the problem ? the kernel is the original 

Please help[/QUOTE]
I understand your frustration. Uninstall nvidia drivers from synaptic and follow my guide again (every step). 
Then if the installer complains about gcc, please see the problem section of my guide. If the installer doesn't work, please post the nvidia log file under /var/log/

---

### Post by TakisX on 2005-09-15
I updated drivers with synaptic and reboot and crashes .I cant get xserver start even if i put vesa or nv or nvidia in xorg file.
Format and new of instalation of 5.04
So bad expirience with linux .i cant even my desktop look ok , and i have so typical ,comon hardware .

---

### Post by tseliot on 2005-09-15
[QUOTE=TakisX]I updated drivers with synaptic and reboot and crashes .I cant get xserver start even if i put vesa or nv or nvidia in xorg file.
Format and new of instalation of 5.04
So bad expirience with linux .i cant even my desktop look ok , and i have so typical ,comon hardware .[/QUOTE]
Maybe I asked you before but I don't remember (I'm studying too hard and my brain is not ok) what is your graphic card model.

---

### Post by merlyn on 2005-09-16
Could someone explain what the following line from the device section, actually does.

Option NvAGP "1"

I always have mine set at 1, as this value was suggested in another howto.

Having read through this forum, some posts made reccomendations to set this at 0 to resolve particular problems.

Recently in another forum I noticed that this was set to 3 in another persons conf file.

Does, this affect the AGP rate, my card is an 8? 

Also is there any value in setting this to a higher value.

Cheers.

---

### Post by tseliot on 2005-09-16
[QUOTE=merlyn]Could someone explain what the following line from the device section, actually does.

Option NvAGP "1"

I always have mine set at 1, as this value was suggested in another howto.

Having read through this forum, some posts made reccomendations to set this at 0 to resolve particular problems.

Recently in another forum I noticed that this was set to 3 in another persons conf file.

Does, this affect the AGP rate, my card is an 8? 

Also is there any value in setting this to a higher value.

Cheers.[/QUOTE]
No, don't you worry it doesn't have anything to do with the AGP rate. It only tells xorg which module it has to load (nvAGP). You have to change it only if nvidia drivers don't work for you.

I think AGP rate can be changed in the bios.

---

### Post by TakisX on 2005-09-16
Tseliot thanks for trying to help this Greek 

I have Geforce3 and Sony tft with dvi

I instaled Ubuntu 5.04 and in synaptic i see that nvidia drivers not installed.
I just upgraded the packets with synartic.
I changed nv to vesa and put # dri in xorg.conf
What to do ? Install drivers with synartic or do your how to ?
The kernel is the original .( in the previous instalation i had compiled kernels easily ,only the drivers is my problem

Thanks

---

### Post by tseliot on 2005-09-16
[QUOTE=TakisX]Tseliot thanks for trying to help this Greek 

I have Geforce3 and Sony tft with dvi

I instaled Ubuntu 5.04 and in synaptic i see that nvidia drivers not installed.
I just upgraded the packets with synartic.
I changed nv to vesa and put # dri in xorg.conf
What to do ? Install drivers with synartic or do your how to ?
The kernel is the original .( in the previous instalation i had compiled kernels easily ,only the drivers is my problem

Thanks[/QUOTE]
Perhaps Geforce 3 is not supported very well in driver 7667.
You should use the Ubuntu Starter's guide and follow its instructions about installing the nvidia drivers (the ones in synaptic).

If it doesn't work you have to switch back to "vesa".

---

### Post by TheTK421 on 2005-09-16
Thanks for all your help! Is there anyway to install the nVidia drivers and enable 3d support during the inital install? 

Thanks in advance!
TheTK421

---

### Post by Owdy on 2005-09-16
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver)

I tryed optimise my card with that tutorila, still my settings are
Fast Writes:     Disabled
 SBA:             Disabled

Motherboard support those. Ideas to fix that?

---

### Post by tseliot on 2005-09-17
[QUOTE=TheTK421]Thanks for all your help! Is there anyway to install the nVidia drivers and enable 3d support during the inital install? 

Thanks in advance!
TheTK421[/QUOTE]
There's no way to do it in Ubuntu during the installation. But if you use the Ubuntu starter's guide it's just a matter of copy and paste.

[http://ubuntuguide.org/](http://ubuntuguide.org/) 

or

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

---

### Post by tseliot on 2005-09-17
[QUOTE=Owdy][http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_Nvidia_3D_driver)

I tryed optimise my card with that tutorila, still my settings are
Fast Writes:     Disabled
 SBA:             Disabled

Motherboard support those. Ideas to fix that?[/QUOTE]
I've never tried such things because I've had a PCI-E card. I bought a new computer last week and it has an agp card but I haven't tried the trick. I don't use the card for games.

I'm sorry, I can't help you with that.

---

### Post by zBoost on 2005-09-18
Thanks for this How-to, it's great.
So I've done everything, and installed the 7667 driver without problems and it is working on my GF 6600GT AGP. On glxgears I get about 7800 fps but I noticed that the GL screensavers doesn't show up. I remember before on my x86_64 Kubuntu when I installed the GL driver from Kynaptic, they worked.
Do u have any idea why, it seems it isn't something serious while glxgears is runing fine and it says Direct Rendering yes, and shows OpenGL versions etc.

---

### Post by tseliot on 2005-09-18
[QUOTE=zBoost]Thanks for this How-to, it's great.
So I've done everything, and installed the 7667 driver without problems and it is working on my GF 6600GT AGP. On glxgears I get about 7800 fps but I noticed that the GL screensavers doesn't show up. I remember before on my x86_64 Kubuntu when I installed the GL driver from Kynaptic, they worked.
Do u have any idea why, it seems it isn't something serious while glxgears is runing fine and it says Direct Rendering yes, and shows OpenGL versions etc.[/QUOTE]
I don't know. It worked for me in 64bit too. I haven't tried in 32bit though

---

### Post by zBoost on 2005-09-18
Hmm I just tested the Doom 3 demo and on high, 1024x768 with 4x AA is over 60 fps, I think it's perfect :D

---

### Post by tseliot on 2005-09-19
zBoost, I think you won't miss opengl screensavers as Doom is better  ;-)

---

### Post by rjwood on 2005-09-21
I went to nvidia's site and the 7667 drivers are not listed only the 7676 drivers are there. I have amd athalon 2800+ and I just installed a "e-GeForce FX 5500" card. The box says DDR-128MB and AGP 8X/4X.
I installed this card after I did a new install of Breezy and had problems with rebooting (couldn't) so I did a clean reinstall of horay and seems to be ok. I just installed the k7 kernel and now want to make sure I have the proper drivers. This is what my device manager says:

/home/rob/Screenshot.png
Can you advise me what to do.

I am not a gamer I just want faster more clean graphics all around and was compelled to upgrade card because I tried the "composit and transset thing. Shadowing and fading was nice but locked up my system.

 Thanks

---

### Post by tseliot on 2005-09-21
[QUOTE=rjwood]I went to nvidia's site and the 7667 drivers are not listed only the 7676 drivers are there. I have amd athalon 2800+ and I just installed a "e-GeForce FX 5500" card. The box says DDR-128MB and AGP 8X/4X.
I installed this card after I did a new install of Breezy and had problems with rebooting (couldn't) so I did a clean reinstall of horay and seems to be ok. I just installed the k7 kernel and now want to make sure I have the proper drivers. This is what my device manager says:

/home/rob/Screenshot.png
Can you advise me what to do.

I am not a gamer I just want faster more clean graphics all around and was compelled to upgrade card because I tried the "composit and transset thing. Shadowing and fading was nice but locked up my system.

 Thanks[/QUOTE]
1) I can't see the image but you can use the link below:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) 

2) click on the word "Archive" below your desired architecture:

This is an example

Graphics Drivers 

Linux IA32
Latest Version: 1.0-7676
Archive 

Linux IA64
Latest Version: 1.0-5336
Archive 

Linux AMD64/EM64T
Latest Version: 1.0-7676
Archive 

3) Then you will see a list of all the versions of nvidia drivers and you can click 7667.

P.S. your architecture is IA32 (as AMD64 is for 64bit systems ONLY)

---

### Post by persis on 2005-09-21
Hi there -

Been running Hoary for quite awhile now with no problems. Just upgraded displays from a Dell CRT to an Apple Cinema 20" lcd display. I installed a FX 5200 card so that I would have the DVI interface - and now I'm trying to get the drivers , lcd, etc.. working properly. I don't know if there have been many people to setup a 20" cinema on a PC running Hoary, but I thought I'd give it a shot.

I ran through your manual, but still am not able to loadup the gui. Attached is a view of my xorg.conf.

Hope all is well - and thanks in advance for any support. Would love to get this baby working and maybe it would serve as a good doc for anyone else doing the same.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
# sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
# sudo dpkg-reconfigure xserver-xorg

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
# Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 5200]"  (I put this in manually)
Driver "nvidia"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "DELL P992"
Option "DPMS"
HorizSync 30-107
VertRefresh 85
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "DELL P992"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by tseliot on 2005-09-21
[QUOTE=persis]Hi there -

Been running Hoary for quite awhile now with no problems. Just upgraded displays from a Dell CRT to an Apple Cinema 20" lcd display. I installed a FX 5200 card so that I would have the DVI interface - and now I'm trying to get the drivers , lcd, etc.. working properly. I don't know if there have been many people to setup a 20" cinema on a PC running Hoary, but I thought I'd give it a shot.

I ran through your manual, but still am not able to loadup the gui. Attached is a view of my xorg.conf.

Hope all is well - and thanks in advance for any support. Would love to get this baby working and maybe it would serve as a good doc for anyone else doing the same.
[/QUOTE]
Have a look at this link, I hope it helps you.

[http://www.ubuntuforums.org/showthread.php?t=60030&highlight=DVI](http://www.ubuntuforums.org/showthread.php?t=60030&highlight=DVI)

---

### Post by tseliot on 2005-09-21
If you can see something (at least the command line) when booting using the new monitor you can use this command:

sudo dpkg-reconfigure xserver-xorg

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor

---

### Post by persis on 2005-09-21
[QUOTE=tseliot]Have a look at this link, I hope it helps you.

[http://www.ubuntuforums.org/showthread.php?t=60030&highlight=DVI](http://www.ubuntuforums.org/showthread.php?t=60030&highlight=DVI)[/QUOTE]



Yup - got the cinema going now.  Thing is, I don't have an option under "Screen Resolution" for it's native resolution of 1680 X 1050.

Any thoughts on how to go about getting the resolution there?

Thanks

---

### Post by tseliot on 2005-09-21
[QUOTE=persis]Yup - got the cinema going now.  Thing is, I don't have an option under "Screen Resolution" for it's native resolution of 1680 X 1050.

Any thoughts on how to go about getting the resolution there?

Thanks[/QUOTE]
Open Terminal or Konsole and type:

sudo dpkg-reconfigure xserver-xorg

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor.

It will ask you your desired resolutions, select the ones you need.

After it ends you can go to "Screen Resolution" and select your resolution.

Tell me if it works

---

### Post by rjwood on 2005-09-21
thanks for the how to tseliot. your a great help. I am thinking about trying breezy upgrade. Nothing to lose really--I can just re-install. Do you think breezy will try to change my kernel or settings for my driver?? thanks again

---

### Post by tseliot on 2005-09-21
[QUOTE=rjwood]thanks for the how to tseliot. your a great help. I am thinking about trying breezy upgrade. Nothing to lose really--I can just re-install. Do you think breezy will try to change my kernel or settings for my driver?? thanks again[/QUOTE]
It could upgrade your kernel to 2.6.12-8 version and you would have to modify your xorg.conf (and set "nvidia" to "nv" or "vesa") (because it's likely that the graphical interface doesn't start) and to reinstall the nvidia drivers. There might be dependency problems and other bugs, but if you have nothing to lose...

---

### Post by persis on 2005-09-21
Still nothing -

attempted to follow various examples from :
[http://micke.hallendal.net/archives/2004/09/apple_cinema_di_1.html](http://micke.hallendal.net/archives/2004/09/apple_cinema_di_1.html)

but still nothing.

---

### Post by persis on 2005-09-21
Current Xorg.conf:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"GEFORCE FX5200"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
EndSection

Section "Monitor"
	Identifier	"Apple Cinema Display"
	#Option		"DPMS"
	HorizSync	28-90
	VertRefresh	43-72
	UseModes "Modes0"
EndSection

Section "Modes"
	Identifier "Modes0"
	ModeLine "1680x1050" 177.05 1680 1752 2112 2256 1050 1052 1064 1090 #72Hz
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GEFORCE FX5200"
	Monitor		"Apple Cinema Display"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1680x1050" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2005-09-22
Persis: Your problem is the resolution, isn't it? Can't you chose it from screen resolution right?

1) put the lines in blue in your xorg.conf

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
[COLOR=Blue]#Load "dri"
#Load “GLcore”[/COLOR]

2) sudo dpkg-reconfigure xserver-xorg

I suppose you've put the refresh rates manually, right? (do it again)

When it asks you which resolutions you want to use select ONLY the one you need ([COLOR=Red]by pressing the spacebar on it[/COLOR])

Then log out and press CTRL+ALT+Backspace

Tell me if it works

---

### Post by oneybm on 2005-09-22
I just printed out this how to and used it on a pretty fresh install with driver version 7676 and have had no problems on my FX 5200.  Thank you for another exceptional how-to on this forum.

---

### Post by tseliot on 2005-09-22
[QUOTE=oneybm]I just printed out this how to and used it on a pretty fresh install with driver version 7676 and have had no problems on my FX 5200.  Thank you for another exceptional how-to on this forum.[/QUOTE]
You're welcome. I'm happy it worked for you.

---

### Post by rjwood on 2005-09-23
Hi tseliot,  can you tell me the difference between pci cards and agp? I dont game and I just want to give my computer good performance graphics and response. I purchased a e-geforce fx 5500 agp and installed the nvidia drivers as you instructed. Just want to be sure that I  purchased the correct card for my needs. I have 12 days to return it and get a different one if I need to. Thanks

---

### Post by tseliot on 2005-09-23
[QUOTE=rjwood]Hi tseliot,  can you tell me the difference between pci cards and agp? I dont game and I just want to give my computer good performance graphics and response. I purchased a e-geforce fx 5500 agp and installed the nvidia drivers as you instructed. Just want to be sure that I  purchased the correct card for my needs. I have 12 days to return it and get a different one if I need to. Thanks[/QUOTE]
I had posted the answer (a long one) to your question but it has disappeared (or it's fault of my connection problems). BTW I have the same card (128mb RAM) and it's quite a good card (if you don't need to play the latest games), it's compatible with Linux (both open source and proprietary drivers) (my geforce 6200 PCI-E was not compatible with the open source drivers). If you need it to watch films the qualty is good as well.

I think it's the card for you.

---

### Post by rjwood on 2005-09-23
[QUOTE=tseliot]I had posted the answer (a long one) to your question but it has disappeared (or it's fault of my connection problems). BTW I have the same card (128mb RAM) and it's quite a good card (if you don't need to play the latest games), it's compatible with Linux (both open source and proprietary drivers) (my geforce 6200 PCI-E was not compatible with the open source drivers). If you need it to watch films the qualty is good as well.

I think it's the card for you.[/QUOTE]

Thanks for the time and help  :)

---

### Post by brentoboy on 2005-09-23
[QUOTE=tseliot]
ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

[/QUOTE]

you know, there is no need to "switch" out to console and kill X, instead, you can reboot, and choose the Recovery mode in grub, it will boot you to a root terminal and never even start your x display manager.

---

### Post by reet on 2005-09-23
But....this way doesn't require a reboot.

---

### Post by tseliot on 2005-09-24
[QUOTE=reet]But....this way doesn't require a reboot.[/QUOTE]
Exactly!

---

### Post by persis on 2005-09-26
Tseliot - 

Was able to get the 1680x1050 resoultion work on the Cinema 20", but the problem is - the visuals are way too small for my design needs / and taste.

The clarity is good, but size too small.  How do I go about adjusting the DPI?

Thanks,
persis

---

### Post by tseliot on 2005-09-26
[QUOTE=persis]Tseliot - 

Was able to get the 1680x1050 resoultion work on the Cinema 20", but the problem is - the visuals are way too small for my design needs / and taste.

The clarity is good, but size too small.  How do I go about adjusting the DPI?

Thanks,
persis[/QUOTE]
I hope this can help you (maybe I didn't get what your problem is).

[http://ubuntuforums.org/showthread.php?t=20976]("http://ubuntuforums.org/showthread.php?t=20976")

You can find a way to change the DPI in GNOME (in the first part of the guide)

---

### Post by bob_c_b on 2005-09-26
First time I tried this it failed, said it couldn't find a screen. I suspect this is because I instaled the 686 kernel the other day and was wonking around quite a bit with the nvidia and restricted packages in Synpatic. Killed GDM again, did an apt-get remove for anything nvidia related and stepped through the procedure again. Worked perfectly, thanks for the effort, I just ordered an AGP 6200 (a Gigabyte NV43 with the HSI bridge chip so unlocked pipes might be in the future) since I got this working.

---

### Post by tseliot on 2005-09-27
[QUOTE=bob_c_b]First time I tried this it failed, said it couldn't find a screen. I suspect this is because I instaled the 686 kernel the other day and was wonking around quite a bit with the nvidia and restricted packages in Synpatic. Killed GDM again, did an apt-get remove for anything nvidia related and stepped through the procedure again. Worked perfectly, thanks for the effort, I just ordered an AGP 6200 (a Gigabyte NV43 with the HSI bridge chip so unlocked pipes might be in the future) since I got this working.[/QUOTE]
I'm happy it worked for you ;)

---

### Post by persis on 2005-09-27
Tseliot -

bad news.  Just got back in town from a wedding, and I realize that I didn't save the configuration (xorg.conf) which had enabled me to get that Cinema 20" native resolution of 1680 x 1050 which I'm shooting for.  I must've been in a rush to head out the door - and rather than saving that config - I just replaced it with the current one I'm using which only gives me this pain in the but 1280x800 resolution:

the followin is the current xorg.conf I'm using.  I have searched all over the internet for a way to get this Apple Cinema 20" display at it's native resolution within Hoary - I'm using a GEFORCE FX 5200 video card.

It would be great if I, us, WE could get to the bottom of this so others could benefit from a working xorg.conf that displays in native res.

Let me know what you think?  

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"GEFORCE FX5200"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
	Option "ConnectedMonitor" "DFP"
	Option "DDCMode" "on"
EndSection

Section "Monitor"
	Identifier	"Apple Cinema Display"
	#Option		"DPMS"
	HorizSync	28-90
	VertRefresh	43-60
	UseModes "Modes0"
EndSection

Section "Modes"
	Identifier "Modes0"
	ModeLine "1680x1050" 149.01 1680 1752 2112 2256 1050 1052 1064 1090 #60Hz
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GEFORCE FX5200"
	Monitor		"Apple Cinema Display"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes "1680x1050" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2005-09-27
[QUOTE=persis]Tseliot -

bad news.  Just got back in town from a wedding, and I realize that I didn't save the configuration (xorg.conf) which had enabled me to get that Cinema 20" native resolution of 1680 x 1050 which I'm shooting for.  I must've been in a rush to head out the door - and rather than saving that config - I just replaced it with the current one I'm using which only gives me this pain in the but 1280x800 resolution:

the followin is the current xorg.conf I'm using.  I have searched all over the internet for a way to get this Apple Cinema 20" display at it's native resolution within Hoary - I'm using a GEFORCE FX 5200 video card.

It would be great if I, us, WE could get to the bottom of this so others could benefit from a working xorg.conf that displays in native res.

Let me know what you think?  

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"GEFORCE FX5200"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
	Option "ConnectedMonitor" "DFP"
	Option "DDCMode" "on"
EndSection

Section "Monitor"
	Identifier	"Apple Cinema Display"
	#Option		"DPMS"
	HorizSync	28-90
	VertRefresh	43-60
	UseModes "Modes0"
EndSection

Section "Modes"
	Identifier "Modes0"
	ModeLine "1680x1050" 149.01 1680 1752 2112 2256 1050 1052 1064 1090 #60Hz
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GEFORCE FX5200"
	Monitor		"Apple Cinema Display"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes "1680x1050" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection[/QUOTE]
I don't know how you managed to make it work before but you can try this method again:

Open Terminal or Konsole and type:

sudo dpkg-reconfigure xserver-xorg

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor.

It will ask you your desired resolutions, select the ones you need.

After it ends you can go to "Screen Resolution" and select your resolution.

---

### Post by persis on 2005-09-27
Hey, just got it working by adding the following modeline to my xorg.conf

Got this from the NVIDIA Linux Forums -

[B]# 1680x1050 @ 59.9 Hz hsync: 64.7 kHz; PixelClock: 119.00 MHz
Modeline "1680x1050" 119.00 1680 1728 1760 1840 1050 1053 1059 1080[/B]

as well as added **Option "ExactModeTimingsDVI" "true"**
to the device section!

Thanks Tseliot for the support -!

---

### Post by tseliot on 2005-09-27
> **persis]Hey, just got it working by adding the following modeline to my xorg.conf

Got this from the NVIDIA Linux Forums -

[B]# 1680x1050 @ 59.9 Hz hsync: 64.7 kHz said:**
> 

as well as added **Option "ExactModeTimingsDVI" "true"**
to the device section!

Thanks Tseliot for the support -!
Now if you lose your xorg you can find the settings (you've posted) you need here ;)

---

### Post by persis on 2005-09-27
tseliot

My new problem:

Now that I have the res set to native 1680 x 1050 - I don't like how everything, web pages, etc.. are too small.  So I tried to decrease the DPI.  Problem is, even when I verify that I have decreased the dpi to 75 x 75 dpi by doing:

**xdpyinfo | grep dimensions**
dimensions:    1680x1050 pixels (561x356 millimeters)

**xdpyinfo | grep resolution**
resolution:    76x75 dots per inch

I still don't get any change to the actual display.  However, if I go to preferences / resolution and select another resolution, for example:

1024 x 768 I instantly notice the difference (the fact that I changed the dpi to something smaller and then everything looks a little bit bloated in the 1024 x 768 resolution.

I'm wondering why the change to a lesser DPI is not being recognized undere the 1680 x 1050 native resolution that I'm currently under.

_**The following is my current xorg.conf:**_


Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath        "/usr/lib/X11/fonts/75dpi"
	FontPath	"/usr/lib/X11/fonts/100dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection


Section "Device"
	Identifier	"GEFORCE FX5200"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
	Option "AllowGLXWithComposite" "1"
	Option "RenderAccel" "true"
EndSection


Section "Monitor"
	Identifier	"Apple Cinema Display"
	UseModes "16:10"
	HorizSync 31.5 - 90.0
	VertRefresh 60.0 - 60.0
	#Option "dpms"
	DisplaySize	560.3	353.6	#1680x1050 120dpi
EndSection



Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection



Section "Device"
        Identifier      "GEFORCE FX5200"
        Driver          "nvidia"
        BusID           "PCI:1:4:0"
        Option "AllowGLXWithComposite" "1"
        Option "RenderAccel" "true"
	Option "ExactModeTimingsDVI" "true"
EndSection



Section "Screen"
Identifier "Default Screen"
Device "GEFORCE FX5200"
Monitor "Apple Cinema Display"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1680x1050" "1400x1050" "1280x1024" "1280x960" "1024x800" "1024x768" "800x600" "640x480"
EndSubSection 
EndSection

Section "Modes"
Identifier "16:10"
# 1680x1050 @ 59.9 Hz hsync: 64.7 kHz; PixelClock: 119.00 MHz
Modeline "1680x1050" 119.00 1680 1728 1760 1840 1050 1053 1059 1080
EndSection 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



**Any thoughts?**

---

### Post by DancingSun on 2005-09-27
Are you saying the font is too small?  Or the graphics/icons stuff is too small in general?  If it's just the text, instead of increasing the dpi (that should just make the font smoother), increase the font size.

If in general everything is too small and you want to make them bigger....well, you'll need to lower the resolution.

Note that you can increase the font size displayed on the web page by configuring your browser.  I have my monitor set at 1280 x 1024 and I find some webpage text too small as well, so I just ctrl+scrollwheel-up to increase the font size.  I have my system font set at size 10 as well, which looked like size 8 on 1024 x 768.

---

### Post by persis on 2005-09-27
Hey Dancing -

Well, I'm talking about the graphics, icons, etc... being too small - and so I guess I need to change resolution.  Does 1280 x 1024 stretch your page out too much.  I'm running on a 20" widescreen.  Maybe that's the problem.

---

### Post by persis on 2005-09-27
I should be able to change the dpi though so the graphics under a 1680x1050 resolution enlarge rather than being so damn small.

---

### Post by DancingSun on 2005-09-27
[QUOTE=persis]Hey Dancing -

Well, I'm talking about the graphics, icons, etc... being too small - and so I guess I need to change resolution.  Does 1280 x 1024 stretch your page out too much.  I'm running on a 20" widescreen.  Maybe that's the problem.[/QUOTE]
Are you talking about graphics being stretched out?  If that's the case, then I haven't notice any stretching, the icons still look very normal and proportional.

---

### Post by DancingSun on 2005-09-27
[QUOTE=persis]I should be able to change the dpi though so the graphics under a 1680x1050 resolution enlarge rather than being so damn small.[/QUOTE]
I just used FreeNX to take a look at my dpi settings with xdypinfo, and I have 75 x 75 dpi on a 1018 x 713 X display via FreeNX...so I guess you should lower that even more and see if it makes a difference.

Using VNC, which retains the exact display settings that I have at home gives me 90 x 96 dpi, and 1280 x 1024 pixels.

---

### Post by brentoboy on 2005-09-27
[QUOTE=linuxa]
Does any one know how I could get back my larger screen size please?
[/QUOTE]

boot using recovery mode from grub

once you are at a root prompt, 
nano /etc/X11/xorg.conf
change the:  Driver "nvidia" 
line back to 
Driver "vesa"

save and close
reboot

X should start up in full screen mode, but you dont get hardware exceleration until you sort out nvidia, but I'm guessing you would rather have higher resolution while you are fixing your situation.

---

### Post by rjwood on 2005-09-27
[QUOTE=tseliot]It could upgrade your kernel to 2.6.12-8 version and you would have to modify your xorg.conf (and set "nvidia" to "nv" or "vesa") (because it's likely that the graphical interface doesn't start) and to reinstall the nvidia drivers. There might be dependency problems and other bugs, but if you have nothing to lose...[/QUOTE]
you were correct and I cannot get into gdm. I edited as you instructed to both "nv" and "vesa" but niether work. message say's:

/etc/init.d/gdm:line 49: /dev/null: Permission denied
/lib/lsb/init.d-functions: line 182: dev/null:Permission denied...fail
also got;
perl:warning:Setting locale failed
Perl warning:Please check that your locale settings:
LANGUAGE="en"
LC_All=(unset)
LANG="en_US.UTF-8" are supported and installed on your system.

Is this something you can help me with?:rolleyes:

btw sudo dpkg-reconfigure xserver-xorg doesn't help

---

### Post by tseliot on 2005-09-27
[QUOTE=rjwood]you were correct and I cannot get into gdm. I edited as you instructed to both "nv" and "vesa" but niether work. message say's:

/etc/init.d/gdm:line 49: /dev/null: Permission denied
/lib/lsb/init.d-functions: line 182: dev/null:Permission denied...fail
also got;
perl:warning:Setting locale failed
Perl warning:Please check that your locale settings:
LANGUAGE="en"
LC_All=(unset)
LANG="en_US.UTF-8" are supported and installed on your system.

Is this something you can help me with?:rolleyes:

btw sudo dpkg-reconfigure xserver-xorg doesn't help[/QUOTE]
I'm afraid I can't help you. I've never dealt with such a problem (I use stable versions). You should try to post in the Breezy development section.

---

### Post by tseliot on 2005-09-27
[QUOTE=persis]I should be able to change the dpi though so the graphics under a 1680x1050 resolution enlarge rather than being so damn small.[/QUOTE]
I really don't know how to help you, I hope other users can.

---

### Post by tht00 on 2005-09-27
Alright; I've got an issue getting the driver to work.  I as far as I know, I followed the guide, I downloaded the 7667 version, and I've done the edits to the xorg.conf file.

I had previously installed the 7676 version, and it is doing the exact same now that I have uninstalled and reinstalled the 'correct' driver.

Here is what it is doing:
When I do everything, including changing the xorg file, it boots up and displays a blank black page; as far as I can tell, gnome never loads,   When I replaced the edited xorg config file with the backup, everything works again (as far as booting up, the 3d screen savers have since stopped working altogther).  The problem only occurs when the 'Driver' section is changed to "nvidia"... not sure if this is significant, as it sounds like something just hasn't installed correctly.

As far as I know, I uninstalled the oddball 7676 driver, but I'm a Linux newb, so I may have missed something... seeing that I saw no difference between 7676 and 7667, I'm guessing the problem lies somewhere in there.  I've tried the installation with the 7667 driver twice with the same results.

System specs:
32-bit Ubuntu 5.04
AMD 64bit 3300+
512 mem
20gig parition (ext3)
Nvidia GeForce FX 5200

I also have XP on another partition; no driver conflicts there.

Thanks,
Tom

oh, and this is my first post on these forums. :)

---

### Post by tseliot on 2005-09-27
[QUOTE=tht00]Alright; I've got an issue getting the driver to work.  I as far as I know, I followed the guide, I downloaded the 7667 version, and I've done the edits to the xorg.conf file.

I had previously installed the 7676 version, and it is doing the exact same now that I have uninstalled and reinstalled the 'correct' driver.

Here is what it is doing:
When I do everything, including changing the xorg file, it boots up and displays a blank black page; as far as I can tell, gnome never loads,   When I replaced the edited xorg config file with the backup, everything works again (as far as booting up, the 3d screen savers have since stopped working altogther).  The problem only occurs when the 'Driver' section is changed to "nvidia"... not sure if this is significant, as it sounds like something just hasn't installed correctly.

As far as I know, I uninstalled the oddball 7676 driver, but I'm a Linux newb, so I may have missed something... seeing that I saw no difference between 7676 and 7667, I'm guessing the problem lies somewhere in there.  I've tried the installation with the 7667 driver twice with the same results.

System specs:
32-bit Ubuntu 5.04
AMD 64bit 3300+
512 mem
20gig parition (ext3)
Nvidia GeForce FX 5200

I also have XP on another partition; no driver conflicts there.

Thanks,
Tom

oh, and this is my first post on these forums. :)[/QUOTE]
can you post your xorg.conf (copy and paste it here)?

---

### Post by tht00 on 2005-09-27
yeah:

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	#Driver		"nvidia"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HP v75"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HP v75"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


I commented out the line that caused the glitch and put in the original that at least boots.

---

### Post by phlawed on 2005-09-27
Everything worked great until this

NVIDIA Corporation NV40? [Unknown nVidia Card]

it wouldnt let me restart gdm with this as the the identifier

I am using a PNY GeForce 6200 Verto 128mb, why is ubuntu not recognizing my card?

---

### Post by tseliot on 2005-09-28
[QUOTE=phlawed]Everything worked great until this

NVIDIA Corporation NV40? [Unknown nVidia Card]

it wouldnt let me restart gdm with this as the the identifier

I am using a PNY GeForce 6200 Verto 128mb, why is ubuntu not recognizing my card?[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

and select autodetect when it asks you about your graphic card (if it doesn't work select it manually)

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor. OR you can make it autodetect.

It will ask you your desired resolutions, select the ones you need.

---

### Post by tseliot on 2005-09-28
[QUOTE=tht00]I had previously installed the 7676 version, and it is doing the exact same now that I have uninstalled and reinstalled the 'correct' driver.[/QUOTE]
Did the driver installed without any error? 

Reinstall the driver (make sure you follow EVERY step of my guide) then go to /var/log and post your nvidia log file (open it and paste it here)

[QUOTE=tht00]Here is what it is doing:
When I do everything, including changing the xorg file, it boots up and displays a blank black page; as far as I can tell, gnome never loads,   When I replaced the edited xorg config file with the backup, everything works again (as far as booting up, the 3d screen savers have since stopped working altogther).  The problem only occurs when the 'Driver' section is changed to "nvidia"... not sure if this is significant, as it sounds like something just hasn't installed correctly.[/QUOTE]
Do you mean it displays the command line or it just boots to a blank page? Does xorg complain about anything?

---

### Post by tht00 on 2005-09-28
> **tseliot]Did the driver installed without any error? 

Reinstall the driver (make sure you follow EVERY step of my guide) then go to /var/log and post your nvidia log file (open it and paste it here)[/quote]

I did the uninstall/reinstall again last night... same thing...  I'll try again and post the log file.

And as far as I know, there were no errors anywhere.


[QUOTE=tseliot]Do you mean it displays the command line or it just boots to a blank page? Does xorg complain about anything?[/QUOTE]

It boots up normal until it starts Gnome, then it goes blank.


Edit:

Here's the log said:**
> 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep 28 09:22:49 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.10-5-386/build'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.10-5-386/bu
   ild SYSOUT=/lib/modules/2.6.10-5-386/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.10-5-386/build SUBDIRS=/tmp
   /selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_vers
   ions
   make -f scripts/Makefile.build obj=/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz8122/NVI
   DIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nv.o
   .d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame
   -pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iincl
   ude/asm-i386/mach-default  -I/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD 
    -Wsign-compare -Wno-c
   ast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_G
   NU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 
   -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SI
   GNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT 
   -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8
   122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz8122/NVID
   IA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nv-v
   m.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-fr
   ame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Ii
   nclude/asm-i386/mach-default  -I/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -
   O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL
   _NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D_
   _KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVE
   L=7667  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RAN
   GE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv_v
   m -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pk
   g1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/us
   r/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-a
   gp.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-f
   rame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -I
   include/asm-i386/mach-default  -I/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-p
   kg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
   ripts
    -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD  
   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ 
   -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  
   -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_D
   EBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHAN
   GE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRES
   ENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_agp -DKBUILD_MODNAME=
   nvidia -c -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_
   os-agp.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-i
   nterface.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -f
   omit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i
   386 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-
   7667-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-
   compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODUL
   E  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MA
   JOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_DEBUG -D
   NDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE
   _ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DN
   V_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_interface -DKBUILD_MODNAME=n
   vidia -c -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_o
   s-interface.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-i
   nterface.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-r
   egistry.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fo
   mit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march
   =i386 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz8122/NVIDIA-Linux-x86-1.
   0-7667-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wch
   ar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno
   -common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES
   -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL
   __ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667 
   -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESE
   NT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GE
   T_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_registry 
   -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1
   /usr/src/nv/.tmp_os-registry.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg
   1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     ld -m elf_i386  -r -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/s
   rc/nv/nvidia.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv-
   kernel.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv.o /tmp
   /selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz812
   2/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-agp.o /tmp/selfgz8122/NVIDIA-
   Linux-x86-1.0-7667-pkg1/usr/src/nv/os-interface.o /tmp/selfgz8122/NVIDIA-Lin
   ux-x86-1.0-7667-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.10-5-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.10-5-386/Module.sy
   mvers /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nvid
   ia.mod.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fom
   it-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i38
   6 -
   Iinclude/asm-i386/mach-default     -DKBUILD_BASENAME=nvidia -DKBUILD_MODNAME
   =nvidia -DMODULE -c -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/sr
   c/nv/nvidia.mod.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/
   nvidia.mod.c
     ld -m elf_i386 -r -o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/sr
   c/nv/nvidia.ko /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvi
   dia.o /tmp/selfgz8122/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Installing both new and classic TLS OpenGL libraries.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-7667):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-7667) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.


---

### Post by tseliot on 2005-09-28
[QUOTE=tht00]I did the uninstall/reinstall again last night... same thing...  I'll try again and post the log file.

And as far as I know, there were no errors anywhere.




It boots up normal until it starts Gnome, then it goes blank.[/QUOTE]
Nothing useful comes to my mind. Perhaps it's because I passed my last exam last monday and my head is literally burning. I think you should try asking at nvidia forum as suggested in my guide. Sorry :(

---

### Post by DancingSun on 2005-09-28
Yes, it's better if nVidia knows about these problems, so that they can get their Linux drivers to the quality of their windows counterparts.

---

### Post by tht00 on 2005-09-28
[QUOTE=tseliot]Nothing useful comes to my mind. Perhaps it's because I passed my last exam last monday and my head is literally burning. I think you should try asking at nvidia forum as suggested in my guide. Sorry :([/QUOTE]

Alright; will do.  Thanks for the help! :) 

I'll let you know what I find out.

---

### Post by strawberry on 2005-09-28
Hi Everybody,
I would like to know what is the difference between the built in 'nv' driver and the compiled/installed 'nvidia' driver?
Sorry if it seems little off but I thought the experts here could give the proper answer.
Thanks.

---

### Post by tseliot on 2005-09-29
[QUOTE=strawberry]Hi Everybody,
I would like to know what is the difference between the built in 'nv' driver and the compiled/installed 'nvidia' driver?
Sorry if it seems little off but I thought the experts here could give the proper answer.
Thanks.[/QUOTE]
"nv" driver is the open source one and it doesn't enable 3d acceleration. "nvidia" driver is the proprietary one which enables 3d acceleration and (I think, because it does on my computer) should slightly improve the video decoding (=playing) (but I'm not 100% sure about the latter thing)

---

### Post by linuxwannaB on 2005-09-30
Hi there, good guide.  I have installed 7676 drivers on hoary with out problem, I am now on breeze and I get the following error. I type this first /etc/init.d/gdm stop and it says it stoped.


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Sep 30 14:45:35 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists... an X server appears to be running
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by rjwood on 2005-09-30
luxixwannaB,

unfortunatly now you will have to remove the 7676 driver and install nvidia glx

sudo apt-get install nvidia-glx.

if you dont remove the 7676driver---it wont work

---

### Post by linuxwannaB on 2005-09-30
thx will give it a try figured out how to get around that hit ctrl+alt+backspace then it whent inot the installer but said no kernel match tried to download new header with synaptic but says unresolved dependencies will not install.

---

### Post by tseliot on 2005-09-30
[QUOTE=linuxwannaB]thx will give it a try figured out how to get around that hit ctrl+alt+backspace then it whent inot the installer but said no kernel match tried to download new header with synaptic but says unresolved dependencies will not install.[/QUOTE]
Try to install kernel sources and headers according to your kernel version.

P.S. What's your kernel version? Did you compile it yourself or are you using Breezy?

---

### Post by linuxwannaB on 2005-09-30
Using breezy 2.6.11 generic x86_64 wont let me install newer one says unresolved dependencies. I did however got 7667 driver to install just fine.

---

### Post by tseliot on 2005-10-01
[QUOTE=linuxwannaB]Using breezy 2.6.11 generic x86_64 wont let me install newer one says unresolved dependencies. I did however got 7667 driver to install just fine.[/QUOTE]
If you did manage to install 7667 stick with it (7676 can give you some problems)

---

### Post by coz on 2005-10-04
Hello,
 I have been reading about the nvidia drivers install and honestly it is all goop to me!. I am a noob with linux . I have an Nvidia fx 5200 PCI, not agp, card.
 I cannot get it to run. Of course if I activate the defualt nvidia agp drivers in Ubuntu Breezy I can't get into the system. i need someone who is willing to give me a blow by blow of installing drivers, and running the PCI (pci) nvidia fx 5200 card!
 thanks
 Coz

---

### Post by tseliot on 2005-10-04
[QUOTE=coz]Hello,
 I have been reading about the nvidia drivers install and honestly it is all goop to me!. I am a noob with linux . I have an Nvidia fx 5200 PCI, not agp, card.
 I cannot get it to run. Of course if I activate the defualt nvidia agp drivers in Ubuntu Breezy I can't get into the system. i need someone who is willing to give me a blow by blow of installing drivers, and running the PCI (pci) nvidia fx 5200 card!
 thanks
 Coz[/QUOTE]
The driver is the same for both PCI and AGP cards. If you need any explanation just ask me. You can quote every single passage which is not clear for you and I will explain it better.

---

### Post by coz on 2005-10-04
Hello,
 Thanks for reply.
 Well , let me tell you what I have done first.
 I downloaded the latest Nvidia Linux drivers from their site. I put it both on the desktop and in the root of c.
I went to the terminal typed "init 1" 
from there I did # cd /home
from there I typed the sh NVIDIA-Linux-x86-1.0-767-pkg1.run which was  the name of the driver I downloaded. However, it always reports that there is no such file or directory.
 Now I did what you said to find out what device it sees. Right now it sees intel graphics onboard video. No mention of the Nvidia fx 5200 PCI card at all.
 Where do I go from here?

---

### Post by tseliot on 2005-10-04
[QUOTE=coz]Hello,
 Thanks for reply.
 Well , let me tell you what I have done first.
 I downloaded the latest Nvidia Linux drivers from their site. I put it both on the desktop and in the root of c.
I went to the terminal typed "init 1" 
from there I did # cd /home
from there I typed the sh NVIDIA-Linux-x86-1.0-767-pkg1.run which was  the name of the driver I downloaded. However, it always reports that there is no such file or directory.
 Now I did what you said to find out what device it sees. Right now it sees intel graphics onboard video. No mention of the Nvidia fx 5200 PCI card at all.
 Where do I go from here?[/QUOTE]
you should do:

cd /home/[COLOR="#ff0000"]your_username
[/COLOR]
and the right command is sudo sh NVIDIA-Linux-x86-1.0-76[COLOR="Red"]6[/COLOR]7-pkg1.run

(if you want to see its name type "ls" in the directory in which you put the file)

P.S. why did you do init1?

---

### Post by coz on 2005-10-04
Hello,
 first, "init 1" shuts down all services . You are then at a command prompt only.
 To my understanding this is the only way to install something properly in linux.
I will try the sudo first, however, I did the user name also and found nothing. I did the ls and also the dir and still it found no file by that name. So maybe if I try the sudo first..... i will let you know what happens then

---

### Post by coz on 2005-10-04
Well I tried everything and again " no file or directory exists."
  i am at a loss here!!!
I realize this must be simple for you but I find it pretty frustrating. Although I felt that way when I started windows also.
 So in time, right?

---

### Post by DancingSun on 2005-10-04
[QUOTE=coz]Well I tried everything and again " no file or directory exists."
i am at a loss here!!!
I realize this must be simple for you but I find it pretty frustrating. Although I felt that way when I started windows also.
So in time, right?[/QUOTE]
Where did you download the file to?  If you don't remember, do a search for it using the search feature under the "Places" menu on the gnome bar.

---

### Post by tseliot on 2005-10-04
[QUOTE=coz]Well I tried everything and again " no file or directory exists."
i am at a loss here!!!
I realize this must be simple for you but I find it pretty frustrating. Although I felt that way when I started windows also.
So in time, right?[/QUOTE]
1) make sure to put the file under /home/your_username (do it while using the graphical interface and then open terminal and type "ls" just to be sure)

2) follow EVERY STEP of my guide i.e. please do things my way (no "init 1") otherwise I can't support you at my best. Believe me if my way works for many users here then maybe it's worth trying ;)

---

### Post by coz on 2005-10-04
OK I got as far as this;

[COLOR="Blue"]Ok, now let's begin:

1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc (just in case)

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd &#8220;directory where you have the nvidia installer&#8221;

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x8[/COLOR]6-1.0-7667-pkg2.run
 Excep my package is NVIDIA-Linux-x86-1.0-7676-pkg1.run

[COLOR="Black"][/COLOR]After accepting the agreement, etc, it then said I did not have libc. That I had to download libc development package  before it could install 
 Where do I get that?

---

### Post by DancingSun on 2005-10-04
[QUOTE=coz]...
After accepting the agreement, etc, it then said I did not have libc. That I had to download libc development package  before it could install 
 Where do I get that?[/QUOTE]
Try searching for it in Synaptic.  The package should have a "-dev" postfix attached to it.

---

### Post by tseliot on 2005-10-04
> **coz]OK I got as far as this said:**
> Ok, now let's begin:

1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc (just in case)

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd &#8220;directory where you have the nvidia installer&#8221;

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x8[/COLOR]6-1.0-7667-pkg2.run
 Excep my package is NVIDIA-Linux-x86-1.0-7676-pkg1.run

[COLOR="Black"][/COLOR]After accepting the agreement, etc, it then said I did not have libc. That I had to download libc development package  before it could install 
 Where do I get that?
Yes, follow DancingSun's suggestion.

[COLOR="Red"]I only want to warn you: driver 7676 doesn't work for everyone so if it doesn't work for you you should stick with 7667 (which works fine)[/COLOR]

---

### Post by coz on 2005-10-04
Well another problem
 When I used your  "sudo apr-get install gcc" it apparently installed gcc 4.0.
 Mine is gcc 3.4 and the nvidia installer would not work until gcc 3.4 was installed, however, there is NO gcc 3.4 .
 Now what?
 thanks
 Coz

---

### Post by tseliot on 2005-10-04
[QUOTE=coz]Well another problem
When I used your  "sudo apr-get install gcc" it apparently installed gcc 4.0.
Mine is gcc 3.4 and the nvidia installer would not work until gcc 3.4 was installed, however, there is NO gcc 3.4 .
Now what?
thanks
Coz[/QUOTE]
Open synaptic/kynaptic and put "gcc" in the search field. You will see a list: install gcc-3.4 (not only the base package)

---

### Post by coz on 2005-10-04
unfortunately the reinstallation og gcc 3.4 did not work.
 I am going to reinstall and start from the beginning without any of the updates. I will see if it works this way. I won't do the get gcc command , however.
 I will pass that and try it.
 I will let you know what happens.
 i am reinstalling right now so....
 Thanks
 Coz

---

### Post by tseliot on 2005-10-04
Remember to try version 7667 too

---

### Post by coz on 2005-10-04
Hello,
 You mean instead of NVIDIA-Linux-x86-1.0-7667-pkg1.run ?
I don't know guy!
 I wanted to try this flavor of linux to see if it had alot of merit. The GUI is great, but frankly, I run BeOs 5 professional and it is more compatibls with all of my hardware than Ubuntu Breezy is!!
You have to do similar things to update software etc, but essencially it's more up to date than Ubuntu! I can play dvds right out of the box, not so with my Ubuntu!
My nvidia fx5200 PCi card is recognized right out of the box, not so Ubuntu!My wacom table works about the same on both Be and Ubuntu, crappy.
 As I said BeOs 5, dead since 1999, is slightly more advanced than ubuntu Breezy!, And BeOs 5 is not very compatible with alot of hardware!
I will try one more time with this damn video card, if it doesn't work, I am going back to BeOS.
 Thanks
 I will let you know
 Coz

---

### Post by DancingSun on 2005-10-04
[QUOTE=coz]Hello,
You mean instead of NVIDIA-Linux-x86-1.0-7667-pkg1.run ?
I don't know guy!
I wanted to try this flavor of linux to see if it had alot of merit. The GUI is great, but frankly, I run BeOs 5 professional and it is more compatibls with all of my hardware than Ubuntu Breezy is!!
You have to do similar things to update software etc, but essencially it's more up to date than Ubuntu! I can play dvds right out of the box, not so with my Ubuntu!
My nvidia fx5200 PCi card is recognized right out of the box, not so Ubuntu!My wacom table works about the same on both Be and Ubuntu, crappy.
As I said BeOs 5, dead since 1999, is slightly more advanced than ubuntu Breezy!, And BeOs 5 is not very compatible with alot of hardware!
I will try one more time with this damn video card, if it doesn't work, I am going back to BeOS.
Thanks
I will let you know
Coz[/QUOTE]
Does BeOS lets you use the latest nVidia drivers?  If you just want your 3D acceleration to work, you should just use Synaptic and install the nVidia drivers from there.  That's the easy way, you should've just said so!

Follow the following guide if you want to install via Synaptic:
[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

That's the way I installed my nVidia drivers, they're not the lastest version but they work and it's easy to install.

---

### Post by tseliot on 2005-10-05
> **coz]OK I got as far as this said:**
> Ok, now let's begin:

1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc (just in case)

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd &#8220;directory where you have the nvidia installer&#8221;

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x8[/COLOR]6-1.0-7667-pkg2.run
 Excep my package is NVIDIA-Linux-x86-1.0-7676-pkg1.run

[COLOR="Black"][/COLOR]After accepting the agreement, etc, it then said I did not have libc. That I had to download libc development package  before it could install 
 Where do I get that?
Here you said your driver was 7676

---

### Post by cosimo on 2005-10-06
Hello
 Ok I have tried everything including downloading the nvidia drivers from synaptic. NOTHING works. I am goiing to give up on this one I think.
I have to use theonboard intel video , which is crap and uses too many system resources for this machine. The video card would be great but apparently I can't do it. I alwys get the message, regarless of the driver verison I use, that there is either NO gcc or the wrong version.
That's as far as I can get.
 The drivers from synaptic always screw up the system I get a weird screen, all blue with white backdrop for the font, saying that the video is set up incorrectly and xserver cannot start.
 So ....
 Coz

---

### Post by cosimo on 2005-10-06
The drivers from synaptic are the nvidia-glx. I have a PCI nvidia card NOT an AGP card.

---

### Post by DancingSun on 2005-10-06
Have you made sure that you're not getting conflicts between the onboard and the addon video card?  Do you need to disable the onboard graphics?

---

### Post by cosimo on 2005-10-06
Hello,
 yes the onboard graphics have to be disabled in the bios.
 Doesn't matter. They don't work!
 The error is about xconfig and xserver
 After diableing the onboard graphics I get this error

---

### Post by DancingSun on 2005-10-06
[QUOTE=cosimo]Hello,
 yes the onboard graphics have to be disabled in the bios.
 Doesn't matter. They don't work!
 The error is about xconfig and xserver
 After diableing the onboard graphics I get this error[/QUOTE]
Can you post the errors again?  It's not showing.

---

### Post by PiIsExactly3 on 2005-10-06
I thought I had followed your guide to the letter, however I cannot install the NVIDIA drivers.  My error log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Oct  6 21:37:12 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `make` in your path; please make
       sure that you have the package 'make' installed.  If make is installed
       on your system, then please check that `make` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by tseliot on 2005-10-06
[QUOTE=PiIsExactly3]I thought I had followed your guide to the letter, however I cannot install the NVIDIA drivers.  My error log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Oct  6 21:37:12 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the development tool `make` in your path; please make
       sure that you have the package 'make' installed.  If make is installed
       on your system, then please check that `make` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```[/QUOTE]
Open Synaptic/Kynaptic and install "Make". Then try again.

---

### Post by tseliot on 2005-10-07
[QUOTE=cosimo]Hello,
 yes the onboard graphics have to be disabled in the bios.
 Doesn't matter. They don't work!
 The error is about xconfig and xserver
 After diableing the onboard graphics I get this error[/QUOTE]
Open /var/log/nvidia-installer.log copy its content and paste it here, please.

---

### Post by PiIsExactly3 on 2005-10-07
Thanks for your help.  It replaced one error for another, but I figured the rest out on my own.  I needed to get libc6-dev as well.

---

### Post by tseliot on 2005-10-07
[QUOTE=PiIsExactly3]Thanks for your help.  It replaced one error for another, but I figured the rest out on my own.  I needed to get libc6-dev as well.[/QUOTE]
I want thank you because you made me realise that I had to add something more to the guide.;)

---

### Post by gmatt on 2005-10-09
[QUOTE=tseliot]

If you have Ubuntu 64bit you can't install OpenGL32bit compatibility libraries, so when the installer asks whether to install it just answer no.
[/QUOTE]

This is troublesome because now that I have Nvidia installed and cedega installed and when I play games in -opengl mode I get alot of crashes. Is there a way that I can install the OpenGL32bit libraries? I remember reading on the cedega wiki page a howto that let you use 32bit libraries by chrooting your system.

---

### Post by tseliot on 2005-10-10
[QUOTE=gmatt]This is troublesome because now that I have Nvidia installed and cedega installed and when I play games in -opengl mode I get alot of crashes. Is there a way that I can install the OpenGL32bit libraries? I remember reading on the cedega wiki page a howto that let you use 32bit libraries by chrooting your system.[/QUOTE]
Look at point 5) of the Problems section at the end of the guide. I've just added it.

---

### Post by cosimo on 2005-10-10
Hello,
 Maybe you can help me with this. I have a machine with an intel video chip onboard. Through windows it is easy to disable this, however, Ubuntu Breezy , picks it up during install and installs the drivers for it. I believe this is one of the problems with initiating the nvidia PCi video card. I know that through windows , if I don't diasble the onboard video, the pci card will not work. I have to, as I said , diable this in harware profiles on windows.
 So how do I uninstall the intel drivers from ubuntu, and initiate the pci card at the same time before I reboot?
 Thanks
 Coz

---

### Post by tseliot on 2005-10-10
[QUOTE=cosimo]Hello,
 Maybe you can help me with this. I have a machine with an intel video chip onboard. Through windows it is easy to disable this, however, Ubuntu Breezy , picks it up during install and installs the drivers for it. I believe this is one of the problems with initiating the nvidia PCi video card. I know that through windows , if I don't diasble the onboard video, the pci card will not work. I have to, as I said , diable this in harware profiles on windows.
 So how do I uninstall the intel drivers from ubuntu, and initiate the pci card at the same time before I reboot?
 Thanks
 Coz[/QUOTE]
1) Try to select the graphic board from your bios; If this function isn't available, go straight to point 2) 

2) Then follow this steps > open Terminal or Konsole and type:

sudo dpkg-reconfigure xserver-xorg

When it asks you about your graphic card select it manually (don't do autodetect). [COLOR="Red"]DO NOT SELECT the "NVIDIA" DRIVER, SELECT "NV" instead[/COLOR]

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor (try in google or if you have a manual of the monitor) OR you can make it autodetect.

It will ask you your desired resolutions, select the ones you need by pressing the SPACEBAR.

If you don't know how to answer the other questions you can use the suggested answers (which will work) by pressing ENTER (without typing anything).

3) After you finish, log out and press CTRL+ALT+BACKSPACE

4) log in and see if everything is displayed correctly. If it works you can reinstall the nvidia drivers as described in my guide.

Tell me if it works

---

### Post by cosimo on 2005-10-10
Hello,
 NO GO!
There is no bios switch for the onboard video , so I followed your directions.  To make the story short, when I rebooted I got a blue screen with a white window saying "The X Server is now diabled. Resrt GDM when it is configured correctly"
 Now what? All I have is command line interface!
 Thanks
 Coz

---

### Post by tseliot on 2005-10-10
Type:
sudo dpkg-reconfigure xserver-xorg

When it asks you about your graphic card autodetect it.

---

### Post by cosimo on 2005-10-10
Hello,
 NO GO!
There is no bios switch for the onboard video , so I followed your directions.  To make the story short, when I rebooted I got a blue screen with a white window saying "The X Server is now diabled. Resrt GDM when it is configured correctly"
 Now what? All I have is command line interface!
 Thanks
 Coz

---

### Post by tseliot on 2005-10-10
[QUOTE=cosimo]Hello,
 NO GO!
There is no bios switch for the onboard video , so I followed your directions.  To make the story short, when I rebooted I got a blue screen with a white window saying "The X Server is now diabled. Resrt GDM when it is configured correctly"
 Now what? All I have is command line interface!
 Thanks
 Coz[/QUOTE]
From the command line:

sudo dpkg-reconfigure xserver-xorg

When it asks you about your graphic card select it manually (don't do autodetect) SELECT YOUR PREVIOUS CARD (not the nvidia one).

---

### Post by BLTicklemonster on 2005-10-11
[QUOTE=tseliot]
ctl-alt-f1 (so as to get to the command line)

Alberto[/QUOTE]

Um, you really really really ought to put a warning right next to that telling people who don't know any better that ctl-alt-f1 is going to put them out of this screen, and into the command line, not in a windowed terminal, but IN THE COMMAND LINE, AS IN A BLACK SCREEN, NO GUI, no way back if they didn't already know what to do following that line up there. I did that and couldn't get back to xserver. restart did no good, nothing did.

So if you put anything like that, please warn people about what is going to happen to them, thank you. (you know us noobs are swarming the Earth, as a matter of fact there's one coming to a theater near you!)

---

### Post by tseliot on 2005-10-11
[QUOTE=BLTicklemonster]Um, you really really really ought to put a warning right next to that telling people who don't know any better that ctl-alt-f1 is going to put them out of this screen, and into the command line, not in a windowed terminal, but IN THE COMMAND LINE, AS IN A BLACK SCREEN, NO GUI, no way back if they didn't already know what to do following that line up there. I did that and couldn't get back to xserver. restart did no good, nothing did.

So if you put anything like that, please warn people about what is going to happen to them, thank you. (you know us noobs are swarming the Earth, as a matter of fact there's one coming to a theater near you!)[/QUOTE]
Ok, I'll be more precise in my descriptions. Thanks for the advice.

BTW you can get back to the GUI (some time ago I switched 4 times subsequently from the GUI to the command line and vice versa)

---

### Post by dahli.llama on 2005-10-11
Ok, I want to install the latest nVidia drivers, but I have a few quick questions.

1.  This one my be stupid, but how do I uninstall the nvidia-glx?  Just use apt-get uninstall I assume?

2.  Does this require a kernel recompile?  I want to know so I can be prepared to reconfigure my wireless ethernet drivers if I screw with the kernel.

Thanks!!

---

### Post by dahli.llama on 2005-10-11
Ok, I successfully installed the 7676 drivers with this.  By far the easiest linux drivers to install so far :D

Thank you very much.

---

### Post by BLTicklemonster on 2005-10-11
!!! I'm such a noob. I posted that, but forgot to print out the instructions at work today and bring them home. (printers? yeah, I got printers out the wazoo, I just ain't got no stinkin' ink, lol)

---

### Post by funkenstein on 2005-10-12
the last config line, for those that are paranoid n00bs (as myself) and panic when it says failed and start thinking they've broken something.... it's ```
**sudo** /etc/init.d/gdm start
``` :o Thanks for the Howto! I got nearly 2000fps from glxgears on my laptop (using 7667 as got a GeForce Go 6200 turbocrack and bleeding bleeding edge crap is starting to get annoying when I want to do more than tinker with my puter.

---

### Post by tseliot on 2005-10-12
[QUOTE=funkenstein]the last config line, for those that are paranoid n00bs (as myself) and panic when it says failed and start thinking they've broken something.... it's ```
**sudo** /etc/init.d/gdm start
``` :o Thanks for the Howto! I got nearly 2000fps from glxgears on my laptop (using 7667 as got a GeForce Go 6200 turbocrack and bleeding bleeding edge crap is starting to get annoying when I want to do more than tinker with my puter.[/QUOTE]
I've fixed it, thanks :)

---

### Post by BLTicklemonster on 2005-10-12
So, ah, how does this relate to Breezy? Same, different, blow stuff up if attempted?

---

### Post by tseliot on 2005-10-12
[QUOTE=BLTicklemonster]So, ah, how does this relate to Breezy? Same, different, blow stuff up if attempted?[/QUOTE]
That's a good question. Some users have reported to have successfully installed the nvidia drivers with my guide. However I haven't tested it myself on Breezy and I'm planning to do it as soon as I manage to get my hands on Breezy stable (tomorrow?). Then I will adapt my guide(s) to Breezy (in the new Breezy's section of the forum).

---

### Post by Karasu Tengu on 2005-10-12
I've followed your guide, and everything went fine

the only problem I got, is that the resolution isnt good?

I should be getting 1400x1050
but I only get options up to 1280x1024

---

### Post by tseliot on 2005-10-12
[QUOTE=Karasu Tengu]I've followed your guide, and everything went fine

the only problem I got, is that the resolution isnt good?

I should be getting 1400x1050
but I only get options up to 1280x1024[/QUOTE]
Open Terminal or Konsole and type:

sudo dpkg-reconfigure xserver-xorg

When it asks you about your graphic card select it manually (don't do autodetect).

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor (try in google or if you have a manual of the monitor) [COLOR="Red"]this is very important[/COLOR].

It will ask you your desired resolutions, select the ones you need by pressing the SPACEBAR.

If you don't know how to answer the other questions you can use the suggested answers (which will work) by pressing ENTER (without typing anything).

3) After you finish, log out and press CTRL+ALT+BACKSPACE

4) log in and see if everything is displayed correctly and if you can select the resolution you need.

Tell me if it works

---

### Post by SillyHalfMexican on 2005-10-12
Great tutorial, thanks!

One question though.  When I did this the first time, it worked perfectly.
However, at the time I was using the 64 bit version, so I assumed I download the 64 bit drivers from nvidia for my 6800GT.

So I did, worked fine.

Then, because some things wasnt as compatible for the 64 bit version, I reinstalled Ubuntu, but with the 32 bit version.

Downloaded the 32 bit drivers for my nvidia, followed the directions the same as I did for the 64 bit version.

Everything was normal.  So I reboot after installing them, and nothing comes up, its just blank.

So I go and edit the xorg.conf file and change the Driver from nvidia back to nv.  Works just fine then, but now I'm assuming that I'm not getting the full acceleration for it now.

So my question is now, why is it not working properly?

Should I download the 64 bit version for some reason and install it on the 32 bit version of Ubuntu?

Not sure if it's like Windows and you have to have the 32 bit drivers for Windows XP 32 bit version.

I have an AMD64 3500+ and an Nvidia 6800GT AGP.

Thanks!

---

### Post by tseliot on 2005-10-13
[QUOTE=SillyHalfMexican]So my question is now, why is it not working properly?[/QUOTE]
Please post your /etc/X11/xorg.conf

[QUOTE=SillyHalfMexican]Should I download the 64 bit version for some reason and install it on the 32 bit version of Ubuntu?[/QUOTE]

No, you shouldn't: 32 bit drivers are meant for 32 bit systems (like Ubuntu 32)[/QUOTE]

---

### Post by malacoda on 2005-10-16
:D Thanks tseliot!

I needed the nVidia display driver installed - obviously - or my desktop would become corrupted and display colored snow in the various panels I had open...

Trouble was if I installed the drivers available via Adept my system would hang at boot up (after checking battery status completion).  A bit of research led me to believe the drivers in the repositories have a bug that prevents X11 from starting properly - at least in my case for whatever reason.  

Decided to install from source - which I'm sure would've been a hair-pulling experience since I'm still quite a linux noob.  Thankfully I found your How-To posted in the forums, followed it and WooHOO!... worked like a charm.  

After several reboots just to be sure, my 'boot hang' issue seems to be resolved.

Great how-to!  Saved me from baldness I'm sure.

regards,
Malac

---

### Post by tseliot on 2005-10-17
[QUOTE=malacoda]:D Thanks tseliot!

I needed the nVidia display driver installed - obviously - or my desktop would become corrupted and display colored snow in the various panels I had open...

Trouble was if I installed the drivers available via Adept my system would hang at boot up (after checking battery status completion).  A bit of research led me to believe the drivers in the repositories have a bug that prevents X11 from starting properly - at least in my case for whatever reason.  

Decided to install from source - which I'm sure would've been a hair-pulling experience since I'm still quite a linux noob.  Thankfully I found your How-To posted in the forums, followed it and WooHOO!... worked like a charm.  

After several reboots just to be sure, my 'boot hang' issue seems to be resolved.

Great how-to!  Saved me from baldness I'm sure.

regards,
Malac[/QUOTE]
Glad to save you some hair :p

---

### Post by comradevik on 2005-10-21
:( 
it worked.. then u ran olanetpenguinracer to test it and after 2 minutes it froze.. i rebooted the computer and when i tried glxinfo it said "segmentation error" and everything i try to run gives me segmentation error...
how do i uninstall the 7667 kernel thing that the Nvidia-linux-x86.. built ??

---

### Post by comradevik on 2005-10-21
*segmenattion fault.. not error.. sorry

---

### Post by Cud on 2005-10-29
I am getting a black screen and then my monitor "clicks" like when its powering down when I try to use the nvidia drivers. When "nv" is in my xorg.conf file everything works except glxgears where I get an error: 
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual
I have followed the instructions exactly, but I was messing around with nvidia-glx beforehand (which also didn't work), so maybe I screwed something else up. Here is a copy of xorg.conf (with the driver still set to "nv"):

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'

#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


And here is a copy of the log when I use the "nvidia" driver ( I removed a lot of stuff that didn't seem to have anything to do with NVIDIA):


X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux finally 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686
Build Date: 31 August 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 29 23:16:34 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "de"
(**) XKB: layout: "de"
(**) Option "XkbOptions" "nodeadkeys"
(**) XKB: options: "nodeadkeys"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)






(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource

(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX


(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7676
	Module class: XFree86 Video Driver

(II) NVIDIA X Driver  1.0-7676  Fri Jul 29 13:01:02 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[13] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[14] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[15] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[16] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[17] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5700VE
(--) NVIDIA(0): VideoBIOS: 04.36.20.41.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 400 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): Generic Monitor: Using default hsync range of 30.00-95.00 kHz
(II) NVIDIA(0): Generic Monitor: Using default vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(WW) (640x350,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x175,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x400,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x200,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (720x400,Generic Monitor) mode clock 35.5MHz exceeds DDC maximum 0MHz
(WW) (360x200,Generic Monitor) mode clock 17.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 25.2MHz exceeds DDC maximum 0MHz
(WW) (320x240,Generic Monitor) mode clock 12.6MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (320x240,Generic Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (400x300,Generic Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 40MHz exceeds DDC maximum 0MHz
(WW) (400x300,Generic Monitor) mode clock 20MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 50MHz exceeds DDC maximum 0MHz
(WW) (400x300,Generic Monitor) mode clock 25MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 49.5MHz exceeds DDC maximum 0MHz
(WW) (400x300,Generic Monitor) mode clock 24.75MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 56.3MHz exceeds DDC maximum 0MHz
(WW) (400x300,Generic Monitor) mode clock 28.15MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Generic Monitor) mode clock 44.9MHz exceeds DDC maximum 0MHz
(WW) (512x384,Generic Monitor) mode clock 22.45MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Generic Monitor) mode clock 65MHz exceeds DDC maximum 0MHz
(WW) (512x384,Generic Monitor) mode clock 32.5MHz exceeds DDC maximum 0MHz

(WW) (1024x768,Generic Monitor) mode clock 75MHz exceeds DDC maximum 0MHz
(WW) (512x384,Generic Monitor) mode clock 37.5MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Generic Monitor) mode clock 78.8MHz exceeds DDC maximum 0MHz
(WW) (512x384,Generic Monitor) mode clock 39.4MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Generic Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(WW) (512x384,Generic Monitor) mode clock 47.25MHz exceeds DDC maximum 0MHz
(WW) (1152x864,Generic Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (576x432,Generic Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x960,Generic Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 0MHz
(WW) (640x480,Generic Monitor) mode clock 74.25MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Generic Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (640x512,Generic Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Generic Monitor) mode clock 135MHz exceeds DDC maximum 0MHz
(WW) (640x512,Generic Monitor) mode clock 67.5MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 0MHz
(WW) (640x512,Generic Monitor) mode clock 78.75MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 81MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 87.75MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 0MHz
(WW) (800x600,Generic Monitor) mode clock 101.25MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 0MHz
(WW) (896x672,Generic Monitor) mode clock 102.4MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 0MHz
(WW) (928x696,Generic Monitor) mode clock 109.15MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 0MHz
(WW) (960x720,Generic Monitor) mode clock 117MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (832x624,Generic Monitor) mode clock 57.284MHz exceeds DDC maximum 0MHz
(WW) (416x312,Generic Monitor) mode clock 28.642MHz exceeds DDC maximum 0MHz
(WW) (1280x768,Generic Monitor) mode clock 80.14MHz exceeds DDC maximum 0MHz
(WW) (640x384,Generic Monitor) mode clock 40.07MHz exceeds DDC maximum 0MHz
(WW) (1280x800,Generic Monitor) mode clock 83.46MHz exceeds DDC maximum 0MHz
(WW) (640x400,Generic Monitor) mode clock 41.73MHz exceeds DDC maximum 0MHz
(WW) (1152x768,Generic Monitor) mode clock 64.995MHz exceeds DDC maximum 0MHz
(WW) (576x384,Generic Monitor) mode clock 32.497MHz exceeds DDC maximum 0MHz
(WW) (1152x864,Generic Monitor) mode clock 121.5MHz exceeds DDC maximum 0MHz
(WW) (576x432,Generic Monitor) mode clock 60.75MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Generic Monitor) mode clock 122MHz exceeds DDC maximum 0MHz
(WW) (700x525,Generic Monitor) mode clock 61MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 0MHz
(WW) (700x525,Generic Monitor) mode clock 75.5MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 0MHz
(WW) (700x525,Generic Monitor) mode clock 77.9MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 0MHz
(WW) (700x525,Generic Monitor) mode clock 92MHz exceeds DDC maximum 0MHz
(WW) (1440x900,Generic Monitor) mode clock 108.84MHz exceeds DDC maximum 0MHz
(WW) (720x450,Generic Monitor) mode clock 54.42MHz exceeds DDC maximum 0MHz
(WW) (1600x1024,Generic Monitor) mode clock 106.91MHz exceeds DDC maximum 0MHz
(WW) (800x512,Generic Monitor) mode clock 53.455MHz exceeds DDC maximum 0MHz
(WW) (1680x1050,Generic Monitor) mode clock 147.14MHz exceeds DDC maximum 0MHz
(WW) (840x525,Generic Monitor) mode clock 73.57MHz exceeds DDC maximum 0MHz
(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 0MHz
(WW) (960x600,Generic Monitor) mode clock 96.58MHz exceeds DDC maximum 0MHz
(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 0MHz
(WW) (960x600,Generic Monitor) mode clock 115MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Generic Monitor) mode clock 133.475MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "1024x768" (height 1536 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "960x720" (height 1440 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "928x696" (height 1392 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "896x672" (height 1344 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(**) NVIDIA(0):      Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): Display dimensions: (360, 270) mm
(--) NVIDIA(0): DPI set to (90, 96)


(II) NVIDIA(0): Setting mode "1280x1024"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000006f8, 1)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000006f8, 1)
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000da8, 1)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000da8, 1)

Any helpful hints??
Thanks in advance.:razz:

---

### Post by tseliot on 2005-10-30
[QUOTE=Cud]I am getting a black screen and then my monitor "clicks" like when its powering down when I try to use the nvidia drivers. When "nv" is in my xorg.conf file everything works except glxgears where I get an error: 
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual
I have followed the instructions exactly, but I was messing around with nvidia-glx beforehand (which also didn't work), so maybe I screwed something else up. Here is a copy of xorg.conf (with the driver still set to "nv"):[/QUOTE]

1) make this part of your xorg.conf look like this
Section "Module"
Load "GLcore"
Load "bitmap"
Load "dbe"
Load "ddc"
[COLOR="Blue"]#[/COLOR]Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

2) can you post your "/etc/modules"?

---

### Post by Cud on 2005-10-30
I dont know I missed commenting out dri, I was pretty darn sure I did it. Here's 
etc/modules.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

---

### Post by Cud on 2005-10-30
Tried again with dri commented out. Still the same story.

---

### Post by tseliot on 2005-10-30
[QUOTE=Cud]Tried again with dri commented out. Still the same story.[/QUOTE]
try this methods in the following order (if one doesn't solve the problem then try the following one) (don't try them all at once)

1) sudo rmmod nvidia
sudo modprobe nvidia

2) Open synaptic and remove the restricted modules for your kernel

3) sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"[/COLOR]
[COLOR="Blue"]Option "Accel" "Off"[/COLOR]
[COLOR="#ff0000"]Option "AllowGLXWithComposite" &#8220;Off&#8221;[/COLOR]

EndSection

If it doesn't solve the problem then you can try to put also the line in blue

---

### Post by Peksi on 2005-11-19
I tryed to install 7667, but it didn't work. I've got 2.6.12-9-386. So here is my nvidia-install.log:
option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

I've tryed gcc 3.3 and 3.4 but it won't work. I installed kernel headers and everything else, but still not working. help me please.

---

### Post by tseliot on 2005-11-19
> **Peksi]I tryed to install 7667, but it didn't work. I've got 2.6.12-9-386. So here is my nvidia-install.log:
option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel said:**
> ftp://download.nvidia.com)?[/url] (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

I've tryed gcc 3.3 and 3.4 but it won't work. I installed kernel headers and everything else, but still not working. help me please.

First off if you use Breezy try this guide [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

BTW try this command:

```
sudo apt-get install linux-tree
```

and try the installer again

---

### Post by scotishhaggis on 2006-03-14
i am having the same problem but its lookh for complier 4.0 any ideas its driving me nuts lol\\:D/

---

### Post by tseliot on 2006-04-12
[QUOTE=scotishhaggis]i am having the same problem but its lookh for complier 4.0 any ideas its driving me nuts lol\\:D/[/QUOTE]
Can you post your nvidia-install.log?

---

### Post by scotishhaggis on 2006-04-15
how do i get them

---

### Post by tseliot on 2006-04-20
[QUOTE=scotishhaggis]how do i get them[/QUOTE]
in /var/log/

---

### Post by flusteredpie on 2006-05-31
Hi there,

  I have a fun problem that I hope someone can help me with. Card is a GeForce4 440MX. Tried your methods and they all resulted in the same problem. When Ubuntu starts up, I get a white screen like you'd expect, however there's no nvidia logo. The system simply displays the white screen, and then seems to hang. Of course, i change xorg.conf back to nv again and everything works fine.  

Any ideas?

Cheers!
Neil

---

### Post by tseliot on 2006-05-31
[QUOTE=flusteredpie]Hi there,

  I have a fun problem that I hope someone can help me with. Card is a GeForce4 440MX. Tried your methods and they all resulted in the same problem. When Ubuntu starts up, I get a white screen like you'd expect, however there's no nvidia logo. The system simply displays the white screen, and then seems to hang. Of course, i change xorg.conf back to nv again and everything works fine.  

Any ideas?

Cheers!
Neil[/QUOTE]
Which version of Ubuntu do you use (Hoary, Breezy or Dapper)?

---

### Post by flusteredpie on 2006-05-31
Oops, came here from google and didn't notice the forum name. It's actually Breezy I'm using, so this should probably be in the Breezy Nvidia thread :S Sorry!

Help still required though..

---

### Post by tseliot on 2006-06-01
[QUOTE=flusteredpie]Oops, came here from google and didn't notice the forum name. It's actually Breezy I'm using, so this should probably be in the Breezy Nvidia thread :S Sorry!

Help still required though..[/QUOTE]
please see note 7 of my guide for Breezy

---

### Post by Duhkha on 2006-11-25
Hello!
i'm trying to install nvidia drivers for riva tnt2 m64 in a xubuntu system in my old AMD K6, my kernel version is 2.6.17-10... i've tried with the nvidia-glx-legacy and it doesn't work; X freezes... i've also tried with legacy drivers from nvidia (6629 and the lastest one, 7184, i think) and i can't install the driver: Unable to build kernel module.
I attach here the nvidia-installer.log
any idea how to solve all this????
Thx!!!!

---

### Post by Duhkha on 2006-11-28
Hello again!
i've finally installed the nvidia-legacy driver coming with xubuntu... the problem with the X server freezing was agp related: when i try to use agpgart it freezes, it only works without using agp : option "NVidiaAgp" "0"
Trying to use nvagp, it doesn't load 'couse it detects agpgart loaded... if i try disabling agpgart, the nvidia kernel module doesn't load and i can't use X...
How to solve all this?
How can i use agp?
Thank you very much!

---

### Post by thidranki on 2006-12-18
Great how-to. Worked perfectly for me. Now all of my 3D screen savers have a drastically noticeable improvement in speed.

---

### Post by thidranki on 2006-12-18
Actually, I take that back :( 

When I restarted my computer, I get a message that says "Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

So how do I fix this/revert to what i had before?

---

### Post by der on 2007-02-15
I recently purchased a new motherboard/CPU combo ( AMD Athlon 64) the mother board has on board video (NVIDIA GeForce 6100) 

After going through your guide, i started the GUI and it ran perfectly, video and all... but when i restarted my computer, i got an error starting X Server.

If i go through the driver install again and launch right into the GUI it will run fine, but every time i restart my computer X Server wont start correctly.

Is this a Driver related problem?

---

### Post by wolf08 on 2007-02-15
> **der said:**
> I recently purchased a new motherboard/CPU combo ( AMD Athlon 64) the mother board has on board video (NVIDIA GeForce 6100) 

After going through your guide, i started the GUI and it ran perfectly, video and all... but when i restarted my computer, i got an error starting X Server.

If i go through the driver install again and launch right into the GUI it will run fine, but every time i restart my computer X Server wont start correctly.

Is this a Driver related problem?


I had this problem too. I think what's happening is that at boot, ubuntu is replacing the kernel module (the driver you installed) with the non-3d one. There should be a way to disable this service, but I'm not sure how.

---

### Post by Arup on 2007-02-16
I still can't figure out when using Synamptic, Ubuntu 6.10 would insist on removing the generic SMP kernel and install 386 kernel with nvidia-legacy drivers makign my dual CPU machine totally useless. This is a bug that needs to be addressed soon, thanks to Envy its not a worry with my system.

---

### Post by Michelpt on 2007-02-21
tseliot wrote:

```
If you want to install Nvidia driver with the nvidia installer (I've tried v.7667) and you use a kernel from Ubuntu Hoary or you compiled it from Hoary sources (or kernel.org sources), then just try this HOWTO.
If you have a kernel from Ubuntu Breezy then try this HOWTO:
http://www.ubuntuforums.org/showthread.php?t=52924 OR just look at point 2 of the problems section of THIS guide.

Make sure you graphic card is not among the ones which are NOT SUPPORTED by looking at the list you will find in the NOTES SECTION *

You need 7676 version only if you have Geforce 7800, otherwise is useless (and it has some bugs). If you haven't got this graphic card PLEASE try 7667, it's more stable.

Download the installer from this page according to your architecture (32bit or 64bit)
http://www.nvidia.com/object/unix.html

Before you start you have to make sure the following things are installed (see points "a","b","c"). If not, you can install them following these steps:

Open either Terminal or Konsole and type:

uname -r (this will tell you the name and version of the kernel you are using)

Open either Synaptic or Kynaptic

a) press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

```

Just to share my experience. First of all many thanks to **tseliot** for detailed HOWTO with nvidia! I have learned many things with it. And now, my experience: I used envy script and installed proprietary drivers instead nvidia-glx, but that drivers does not support 1280x800 resolution on GeForce 7300 256Mb. I tried everything nvidia-config options, forced ModeLine parameters, but without result. However, login screen worked fine, but after login my screen was automatically redirected to 1024x768. Now, seems to me I can write xorg.conf on some sheet of paper without looking at the screen :) After 4 days of ](*,)   , I uninstalled the proprietary drives, installed the restricted modules again and nvidia-glx, and now 1280x800 is working with the same "Screen" and "Monitor" options of the xorg.conf file. Thanks again to tseliot for howto! ;)

---

### Post by graylion on 2007-02-25
If you have a 8800 card you will have to use the latest driver from nvidia, as the ones for edgy do not support that card yet.

it's at [http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run)

also you first have to get rid of the nvidia kernel module if you (like myself) had a different nvidia card in there before because otherwise you'll run into an incompatibility between the installed kernel module and the one required (and provided) by the driver.

---

### Post by masteryurez on 2007-03-08
That was a superb guide. All drivers and OpenGL works perfekt with my Ubuntu-installation :) Continue do good guides!

THANK YOU!!

---

### Post by finite9 on 2007-03-08
> **tseliot said:**
> Well, the main reason is COMPATIBILITY. Without driver 7664-7667 I could never have 3d acceleration or a screen without any corruption with my Geforce 6200 PCI-E. Latest Nvidia graphic cards might not work with Ubuntu's nvidia drivers. I don't play games under Linux (I have an Xbox for that) but: in my case "nv" drivers= screen corruption, nvidia drivers (the ones you can install following Ubuntu Starter Guide) =black screen, no Xorg. If you want to know about the changes in the latest release (7676 I think) you shoul go to nvidia forum, Linux section.

Not neccessarily...I have a brand new GeForce Go 7600 512Mb (in an HP Pavilion dv9297ea) and the nvidia-glx driver in the repos works fine for me in Feisty Herd 5 right from the word go.

---

### Post by sablettes on 2007-06-04
**Could not open the file /home/sablettes/Desktop/NVI…6_64-1.0-9755-pkg2(2).run.**
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I don't know what the problem might be, I downloaded the driver from the nVidia.com website, when I am in the command line (CTRL-ALT-F1), It tells me it can't open the file, any suggestions? 

I have the x64 7.04 Ubuntu (feisty), and i followed every step. Can someone give me a pointer of some kind? 

Thank you in advance, Sablettes :)

---

### Post by namelessone on 2007-06-13
> **sablettes said:**
> **Could not open the file /home/sablettes/Desktop/NVI&#8230;6_64-1.0-9755-pkg2(2).run.**
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I don't know what the problem might be, I downloaded the driver from the nVidia.com website, when I am in the command line (CTRL-ALT-F1), It tells me it can't open the file, any suggestions? 

I have the x64 7.04 Ubuntu (feisty), and i followed every step. Can someone give me a pointer of some kind? 

You cannot open the file with gedit because it is an executable. use *chmod +x <file>* to make it executable, then run it with *./<file>* (replace <file> with the whole filename)

---

### Post by loxety on 2007-06-28
The information in the OP is old.  The author has built a script called ENVY that automagically installs the driver.. check out his web site.  I've used it for a few years now and it works great every time!

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by G00dY on 2007-09-15
I cant get it to work...

After I write "sudo /etc/init.d/gdm stop" I just get this screen, where I can't do anything...
[[IMG]http://img396.imageshack.us/img396/2379/linuxst7.th.jpg[/IMG]](http://img396.imageshack.us/my.php?image=linuxst7.jpg)

Please help, I really want to give linux a change, i'm a super-noob :-/

---

### Post by namelessone on 2007-09-15
> I cant get it to work...

After I write "sudo /etc/init.d/gdm stop" I just get this screen, where I can't do anything...


Please help, I really want to give linux a change, i'm a super-noob :-/

You can't type this command from a terminal in the graphical environment. You need to press Alt+f2 and type the command there.

---

### Post by G00dY on 2007-09-15
Ahh yes, okay, I see that now. thanks...

---

### Post by bluebyt on 2007-09-20
To make the drivers work, I need to disabled this modules:

gksudo gedit /etc/default/linux-restricted-modules-common

and find the line:
DISABLED_MODULES=""

replace it with:
DISABLED_MODULES="nv nvidia_new"

I don't know why this instruction are not in the howto?

Thanks thought for you hard work tseliot !

---

### Post by Proximo1 on 2007-09-20
I just destroyed my Installation

I am running Fiesty Fawn 7.04 and the following How To: caused my Nvidia Driver not to match what the Kernel states.

I am now stuck with no gdm

HELP.  I am a Linux Newbie.

---

### Post by arashcuzi on 2007-09-24
okay, I followed along with all these instructions, I even went and looked for that so called pkg2.run file, couldn't find it, all I found was pkg1, it didn't run, some error halfway through when compiling kernel...

I did the last part about changing the conf file and restarted my gdm and an nvidia logo came up and the whole system freaked for a sec, then the login screen came up, I logged in, and there was a warning about ubuntu using a restricted driver, then I installed the nvidia-settings apt and everything, did the desktop file as you said and restarted...

I got an error, x server couldn't be started and the text was all garbled...I've tried this with about 5 different drivers (x86_64_1.0_7667_pkg2, x86_1.0_7667_pkg1, x86_1.0_9755_pkg1) and nothing is working...

can an nVidia GeForce Go 7800 GTX handle beryl or desktop effects, etc?  Cause it doesn't seem to want to work, I've already asked but it seems to work for everyone else and not me...it's a clean install, no fancy new recompiled kernel or anything, just a fresh install, please someone help me out with this...I can't get this to work with anything...

---

### Post by donyfrosman on 2007-10-09
When I wanted to compile the modules for a Breezy kernel in Hoary I had to use gcc 3.4. If you want to compile them for a Hoary kernel in Breezy you should use the gcc with which Hoary kernel are usually compiled.

How do we know which version that kernel are usually compiled

---

### Post by sweatshopking on 2007-10-26
Hey guys, im kinda new to linux. Not totally new but pretty new, and im having difficulty installing these drivers. Everytime i try to install them, it tells me it cant install them and asks are they binary. Im running x64 bit breezy,and i dled the Linux AMD64/EM64T drivers, and im wondering if i shoudl try a different one? any help is appreciated.

---

### Post by monomaniacpat on 2007-10-28
Hello.

I have already set up the nvidia driver on my own and unfortunately I am affected by the infamous missing title bar. I followed google to a site which give a solution: [http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/)

That works, but I can't seem to set my monitor to the resolution I prefer (1280x1024@85Hz) without it exhibiting the bug again.

Here's a thread I started with more details: [http://ubuntuforums.org/showthread.php?p=3651725](http://ubuntuforums.org/showthread.php?p=3651725)

You'll find my xorg.conf there, which I used in Dapper but which seems to no longer work.

Thanks for looking.

---

### Post by symbo978 on 2007-11-17
Hi. I have just built a 64biy Gutsy PC. I changed some of the desktop preferences and the system recommended I install the latest drivers for the NVidia card (5200). I said yes, it downloaded and installed then said must reboot. I rebooted, now, nothing. Black screen. Not even the bios splash from the card, let alone the mobo. Can't even enter mobo setup. Any suggestions?

Thanks but no need. I have worked out that the monitor I was using failed at exactly the moment of the reboot: The PC started again but nothing on the screen because the screen was dead where it had been working 30 seconds before. Should I feel unlucky?

---

### Post by junner18 on 2007-11-26
> **monomaniacpat said:**
> 
I have already set up the nvidia driver on my own and unfortunately I am affected by the infamous missing title bar. I followed google to a site which give a solution: [http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/)


I had the same problem, which the solution at the above site fixed for a while..   But then after a restart days later, my screen resolution had changed dramatically.  After changing it back, the menu bars had disappeared again.  Now when i save /etc/X11/xorg.conf I get the Following error:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Any clue on how to solve this?

---

### Post by junner18 on 2007-11-28
> **junner18 said:**
> I had the same problem, which the solution at the above site fixed for a while..   But then after a restart days later, my screen resolution had changed dramatically.  After changing it back, the menu bars had disappeared again.  Now when i save /etc/X11/xorg.conf I get the Following error:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Any clue on how to solve this?

Problem seems to have solved itself.  Thanks.

---

### Post by KiwiDalang on 2007-12-07
HEEEELP

I tried this, and it has successfully fried my nvidia graphics, so now it's not only not fixed the problem but I have now lost openGL rendering, which was working.

I have:

AMD64, Gutsy, and an FX5200. I have been trying to get Cedega going, but the Cedega tests came up saying 3D acceleration wasn't working, but everything else was. My screen does not display the Nvidia splash.

I followed the instructions here.

Now nothing is working. I have to boot through something that comes up low resolution mode, and wants to set my screen to Plug and Play, by graphics card to VESA. I change it to nvidia and IBM screen, and it brings up the login.

I tried going back to the nvidia-glx-new, but it's there. Tried enabling it on the restricted drivers, but can't seem to get the system back to where it was either.

Tried reinstalling kernel
Tried reinstalling nvidia-glx-new
No change, I have the same problem

---

### Post by KiwiDalang on 2007-12-07
Tried some new things today, and it's back to where I started at least:

Did the Draugen 32 bit libraries thing first.

Ran the latest nvidia driver install, When it asked whether I wanted to try to download a kernel interface I said no this time. Then said yes to the 32bit libraries. Now have OpenGL back, and glxgears runs again.

---

### Post by KiwiDalang on 2007-12-08
I spoke far too soon. The system won't boot into the splash login.

At the moment my workaround is boot it. It comes up black screen with a box saying my hardware can't be detected and has to be set up manually.
I do so, but use the nv driver as it is the only one offered.
That gets me into the login and gdm then I have to
Ctrl-Alt-F1
sudo /etc/init.d/gdm stop
cd /etc/X11
sudo cp xorg.conf.backup xorg.conf
sudo /etc/init.d/gdm start

from which it seems to work fine until I have to reboot, at which it all happens all over again.

---

### Post by anonymousnobody on 2008-03-25
I have a similar problem. After installing the nvidia driver via the console with the "sudo sh NVIDIA-..." command. I would make the necessary adjustments to the xorg.conf file. Then when I reboot, It would not load normally. I would get this black screen with a dialogue box saying that the hardware or the driver wasn't detected. And I would have to revert to the old "nv" driver (not the restricted one) that's default on ubuntu.

Can anyone help?

---

### Post by jamesnewell on 2008-03-26
Hi,

Has anyone got drivers working for the NVIDIA 9600GT? I have followed the described procedure with the 171.06 driver, just as I have with previous cards but I keep getting a "low resolution" dialog after "successful" installation. 

I also upgraded to Ubuntu 8.04 as someone on a NVIDIA forum suggested. Ubuntu 8.04 still does not detect my card. I have vesa drivers working on a single monitor at 1680x1050 but it is ***very*** annoying that I can't use my dual monitors.

Please let there be a solution!

Thanks,
James.

P.S. Using 64bit

---

### Post by Neo0351 on 2008-03-26
> **jamesnewell said:**
> Hi,

Has anyone got drivers working for the NVIDIA 9600GT? I have followed the described procedure with the 171.06 driver, just as I have with previous cards but I keep getting a "low resolution" dialog after "successful" installation. 

I also upgraded to Ubuntu 8.04 as someone on a NVIDIA forum suggested. Ubuntu 8.04 still does not detect my card. I have vesa drivers working on a single monitor at 1680x1050 but it is ***very*** annoying that I can't use my dual monitors.

Please let there be a solution!

Thanks,
James.

P.S. Using 64bit

I'm running a 9600GT on the 171.06 drivers.  It can be a pain to get to work but once you figure it out its not too bad.  This thread has how I got mine working [http://ubuntuforums.org/showthread.php?t=705795&highlight=9600gt](http://ubuntuforums.org/showthread.php?t=705795&highlight=9600gt)
post 37
also make sure you have the 64 bit driver [ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06/](ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06/)

---

### Post by p1r8bunn3 on 2008-05-16
I just installed the 9600gt and I have serious problems.

dual boot xp/kubuntu 8.04 64 bit
NVIDIA-Linux-x86_64-171.06-pkg2.run

First I installed the drivers in adept.  That did nothing.  I stopped kdm to install the above driver and then it wouldn't start again.  I rebooted and it won't start.  All I get is a black screen that flashes to a somewhat lighter screen with the cursor and then to black again.  It just stays that way.  Flipping back and forth.  It doesn't even get to the login screen. :(

While I can manage to do these things I don't know enough to know why I get the results I get.  Sigh.  Very frustrating.

-pb

---

### Post by p1r8bunn3 on 2008-05-16
Ok.  I found another thread that said that the 171.05 driver worked for the 9600gt so I tried installing that one after a recover boot.  No luck.  Same problem.

Other things I can add that might help.

In the installation process it asks if it should install the 32 bit OpenGL libraries.  I hit yes.  I have no idea if that was a bad plan.

At the end it says something like: "Error: Unable to perform the runtime configuration check library 'libGL.so.1'.  Assuming successful"

Apparently not.  I had to run recovery mode yet again.

And my next question: why the hell is the card fan on all the time?  In Winsucks it stops and starts like normal.  I assume it the driver that would regulate that?

-pb (awfully near tantrum)

---

### Post by Neo0351 on 2008-05-17
ok, can u first walk me through how u tried installing the 171.06 drivers.  sounds like because u are used some other driver first, there might be a conflict.  oh, and i install the 32 bit libraries so that shouldnt be a problem.

---

### Post by pingpongboss on 2008-05-19
You guys should try the beta 173.08 Nvidia drivers. They work well for my 9600GT

Running hardy 64-bit. These instructions are similar to what I did: [http://ubuntuforums.org/showthread.php?t=796898](http://ubuntuforums.org/showthread.php?t=796898)

---

### Post by Neo0351 on 2008-05-19
i've used the 171.05, 171.06, and the 173.08 drivers and havent really noticed much difference between any of them.  but the 173.08 makes my screen flicker sometimes.

---

### Post by LinuxDanP on 2009-05-19
Help! I am trying to get Kubuntu 9.04 running with hardware acceleration, and it just isn't working. I have two EVGA e-GeForce 8600 GTS graphics boards, and I am trying to set up a multiseat computer. I know that the nVidia drivers are the ones I need, I had Gentoo linux on the same computer and I used the nVidia drivers without any problems.

Here's what I've tried so far:
logging in, and using KDE's hardware drivers application to install both of the drivers it came up with.

installing nvidia-glx-180.

banging my head on the desk(that didn't work either)

I also tried downloading the driver from nVidia, and that one didn't work either.

All that happens with any of these, when I try to boot, I don't get to a graphical login, and if I don't switch tty's I don't get to a terminal login either. I posted a detailed explanation of my problem [here]("http://ubuntuforums.org/showthread.php?t=1162689"). I have absolutely no idea where to go from here.

---

### Post by noblerabbit on 2009-05-19
i am trying to get nvidia drivers (180) to work. 

i set up a thread about it here:
[http://ubuntuforums.org/showthread.php?t=1164310](http://ubuntuforums.org/showthread.php?t=1164310)

basically my problem is this:

 i get the pkg from nvidia site, then stop X with
 ```

     sudo /etc/init.d/gdm stop 

```
then chmod +x to the pkg, and run it with
 ```

     sudo sh NVIDIA...etc etc 

```

Installation goes fine, i say no to the 32bit OPENGL stuff because i have x64 obviously.

Upon restarting gdm everything seems fine (the first good sign is the annoying GPU fan finally stops) then i get the NVIDIA screen, and a correct resolution login screen.

Everything would appear it is as it should be, but as soon as i try to restart it cant load X (Ubuntu is running in low graphics mode... cannot determine screen video card etc, dont rememebr exactly what it says).

So I am having to do the above steps again, overwriting the previous driver and the xorg.conf file. I had a look at the file but I cant make much of it.

Does anyone know why this could be happening? I mean i load X fine the first time, so why should it be any different when i reboot?..

---

### Post by RaveJunkie on 2009-06-05
I installed today the NEWEST nvidia driver with this video tut and its the 64bit vers


this might help you

[http://linuxcrypt.net/?p=255&cpage=1#comment-1809](http://linuxcrypt.net/?p=255&cpage=1#comment-1809)

---

### Post by Arup on 2009-06-06
Make sure to remove linux-restricted-modules from Synaptic. Also install x32 open GL support, some apps which are x32 and ported to x64 will need them. A good way to install is described here at [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) and Kosimo's excellent tutorial at [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by moogies on 2009-06-12
> **noblerabbit said:**
> Everything would appear it is as it should be, but as soon as i try to restart it cant load X (Ubuntu is running in low graphics mode... cannot determine screen video card etc, dont rememebr exactly what it says).

I am having this problem. It says my graphics card has been unplugged and must check my connectors or something. It's obviously not the case as I run in windows XP fine. I'm using 32bit ubuntu 9.04 and have tried both 180 nvidia drivers and the newest 185 drivers. I use a 7950 GT

edit: also I tried reformatting my PC (erased using dban) and installing ubuntu again fresh. it worked, but as soon as I installed the nvidia drivers it gave me the error. I've tried installing through console with the nvidia binaries. I've tried using envyng. I've tried using the hardware driver manager in ubuntu.

---

### Post by sahboune on 2009-10-28
hi 
i got compaq presario cq60 amd sempron cpu and nvidia geforce 8200 mg graphic.I try nvidia driver 190.42
first i download the driver from nvidia site
after ctrl+alt+f1
sudo telinit 1
sudo telinit 3
sudo sh NVIDIA-linux-x86-190.42-pkg1.run
follow the instruction 
sudo /etc/init.d/gdm star

driver working great i use ubuntu 9.10

---

### Post by zalmoxes on 2010-01-11
> **tseliot said:**
> 1) Have you installed the kernel headers of your current kernel?

2) Are you using Ubuntu Hoary or Breezy?

3) What's the output of the error (what does the installer say?)?

i'm using karmic koala, i've installed the headers and source and gcc.
nvidia-installer says its unable to build kernel.

---

### Post by Jhon Butcher on 2010-01-12
This is by design after uninstalling the old driver, otherwise you'd be
looking at a blank moniter, and be unable to install your new driver.
Vista's default driver will upgrade/go away when you perform the new
installation

---

### Post by alex_o on 2010-04-16
> ctl-alt-f1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)

i cant access any tty's so this is no help :(

---

### Post by Linuxforall on 2010-04-16
Have you installed build-essential? ctrl+alt+F1 or F2 should get you out of GUI and into terminal unless there is something wrong seriously. Make sure you remove any previous traces of nvidia driver installed via repository.

---

### Post by kevin_hill54 on 2010-05-06
Too much information.

My problem is that I have just upgraded from 9.10 and now will only run in low resolution mode.

I have a GT216 with a 1920x1080 monitor which wqas working perfectly on 9.10.

I have deleted all nvidia drivers using several different instructions and retried several different installs.

I have tried a number of different driver versions from both Nvidia and the repository.

I think now I have so many different changes I should throw it all out and start again.

Is there a recognised standard fix for this video card?

I have now spent 5 days trying to fix this and am about to give up!!

I have booted with a live Fedora12 and all works perfectly.

Any suggestions would be welcomed.

Thanks

Kevin

---

### Post by KherKhere on 2010-05-07
Hello to all , 

i have Problem to Install NVIDIA Driver ,

i saw Error 
> ERROR: Unable to load the kernel module ‘nvidia.ko’.  This happens most  frequently when this kernel module was built against the wrong or  improperly configured kernel sources, with a version of gcc that differs  from the one used to build the target kernel, or if a driver such as  rivafb/nvidiafb is present and prevents the NVIDIA kernel module from  obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU  installed in this system is not supported by this NVIDIA Linux graphics  driver release.

my uname-r is : 2.6.32-21-generic

Please Help me .

---

### Post by K1mp3 on 2010-05-16
I've updated from 9.04 to 9.10 and now to 10.04.
uname -r is:
2.6.31-17-generic
problem following these instructions is, I cant find source code for this kernel version from synaptics and thus the nVidia installer just exist saying that the kernel source code does not exist... should I build my own kernel or is there any other way out of this mess? everything was working fine with 9.x and also after the upgrade to 10.04 it worked fine for the first 1-2 weeks until last nights system update. Now I can only run low res mode with generic driver as nVidia kernel module does not load.

---

### Post by Linuxforall on 2010-05-16
[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

Please follow instructions here on how to properly install nvidia on Lucid, as an alternate the Xswat PPA has latest nvidia drivers so it can be installed easily and with DKMS support as well.

---

### Post by K1mp3 on 2010-05-22
Proglem solved, 

I realised that the upgrade to 10.04  had failed to update my grub menu so I was loading the old Kernel  version. Changed from kernel 2.6.31-17-generic to kernel  2.6.32-21-generic in (/boot/grub/menu.lst) and now nVidia driver loads  just fine.

---

### Post by ingeon on 2010-10-21
Noob question:

Looked at installing the latest Linux Display Driver v.260.19.12

I noticed they say "Stopped installing OpenGL, VDPAU, CUDA, and OpenCL header files with the driver"

How will this affect us, aka what does it actually mean?
Will i have to seek out all those things manually?

---

### Post by py8elo on 2011-01-08
Hi all!!!
I already had many problems to install my 8400 GS NVIDIA GEFORCE on UBUNTU and I find many solutions to do it all the times...
For now, I has discovered on a Brazilian forum a little shell script to do it easyly... The shell script was developed by a Brazilian guy...
Download the shell script from [http://www.meroprojects.com/download...er2.1.1.tar.gz](http://www.meroprojects.com/download...er2.1.1.tar.gz) and cd to the folder where You has saved it. I sugest You to save it on your home folder.
Then, type the commands bellow:

CODE:
$ sudo service gdm stop

or

$ sudo service kdm stop

$ tar -xf vmanager2.1.1.tar.gz

$ cd vmanager2.1.1

$ chmod +x -R *

Now You can execute the shell script typing the command below:

CODE:
$ ./vmanager2.1.1.sh

It will check for and download the latest Nvidia driver and after download has finished it will automatically install the driver...

I hope it will solve your issue!!!

Best Regards,

Silva.




> **ingeon said:**
> Noob question:

Looked at installing the latest Linux Display Driver v.260.19.12

I noticed they say "Stopped installing OpenGL, VDPAU, CUDA, and OpenCL header files with the driver"

How will this affect us, aka what does it actually mean?
Will i have to seek out all those things manually?

---

### Post by Epokhe on 2011-12-17
Sorry i haven't read all pages, only first one but i am new in ubuntu, and want to know why ubuntu doesn't see my gtx 560m card. Actually, i installed nvidia driver(the recommended one) and i have a program "nvidia x server settings". This program sees my card, but in system information(i'm translating it it may be different) reads unknown driver. Why does program see it but ubuntu doesn't?

---

### Post by gillza on 2012-01-05
Remove whatever you have installed. Make sure all the traces of the open source driver are removed as well: 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Removing_Nouveau_.28advanced.2BAC8-expert_users.29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Removing_Nouveau_.28advanced.2BAC8-expert_users.29)

After your system is clean and driver-less run the following:

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

Restart

...and check the following thread.
[http://ubuntuforums.org/showthread.php?t=1771806](http://ubuntuforums.org/showthread.php?t=1771806)

---

