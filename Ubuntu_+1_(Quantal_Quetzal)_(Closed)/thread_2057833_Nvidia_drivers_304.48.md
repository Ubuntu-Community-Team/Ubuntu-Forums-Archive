---
title: "Nvidia drivers 304.48"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-09-14
There is a new nvidia graphics driver in Xorg-edgers PPA: 304.48.

---

### Post by whatthefunk on 2012-09-14
I tried that one...broke everything.  Couldnt get x to start.  Im using 304.37 now and it seems stable enough.  Had the blue youtube faces bug at first, but thats easy enough to correct.

---

### Post by xebian on 2012-09-14
> **whatthefunk said:**
> I tried that one...broke everything.  Couldnt get x to start.  Im using 304.37 now and it seems stable enough.  Had the blue youtube faces bug at first, but thats easy enough to correct.

There is a 304.43 stable release.

---

### Post by effenberg0x0 on 2012-09-14
I have just installed 304.48 (using Nvidia installer). It is available at ftp.download.nvidia, as usual, and here are the direct links:

**For 32-bit:**
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/304.48/NVIDIA-Linux-x86-304.48.run
```
**For 64-bit:**
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/304.48/NVIDIA-Linux-x86_64-304.48.run
```

It works normally for me using up-to-date QQ, with no alternate repos/PPAs.
[ATTACH]224131[/ATTACH]

OBS: There are 3 new options in ccsm / OpenGL (I hadn't noticed this change yet). "Framebuffer Object", "Vertex Buffer Object" and " Always use Buffer Swapping".

[B]EDIT:
[/B]
- I noticed my glxgears went from &#8771; 14000.000 to 4000.000. Enabling or disabling the new ccsm options I listed above had no effect in performance here. Disabling FXAA and "Texture Sharpening" on nvidia-settings brought me back to &#8771; 14000.000 on glxgears with no tearing and similar quality. 

- Enabling or disabling "Sync to VBlank" on ccsm is not working for me anymore (only works on nvidia-settings).

Regards,
Effenberg

---

### Post by whatthefunk on 2012-09-14
> **xebian said:**
> There is a 304.43 stable release.

Thats the one I tried.  I tried getting it from the ppa first, and then downloaded it direct from nvidia.  Broke x both times.  Dont know what went wrong there....

---

### Post by effenberg0x0 on 2012-09-14
I did a cold boot, just to be sure, and everything is fine so far. Here are the versions of the related packages in my install:
 
```
[12:20:07] ahsl@AL-DESK01:[~]: uname -a
Linux AL-DESK01 3.5.0-14-generic #16-Ubuntu SMP Mon Sep 10 21:57:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[12:20:17] ahsl@AL-DESK01:[~]: X -version

X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-23-generic x86_64 Ubuntu
Current Operating System: Linux AL-DESK01 3.5.0-14-generic #16-Ubuntu SMP Mon Sep 10 21:57:14 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-14-generic root=UUID=39279a24-1546-4695-b67c-46c823d8a063 ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
Build Date: 06 September 2012  10:13:05PM
xorg-server 2:1.13.0-0ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[12:20:22] ahsl@AL-DESK01:[~]: compiz --version
Compiz 0.9.8.0
[12:20:31] ahsl@AL-DESK01:[~]: unity --version
unity 6.4.0
```

I have re-checked apt sources, apt prefs and dpkg status. I have no pins and packages on hold using default sources, but I'm holding some packages. I think they're mostly unrelated (no Kernel, xorg*, compiz, unity) but heres the list anyway:
```
The following packages have been kept back:
  braindump calibre calibre-bin calligra calligra-libs calligraflow calligraplan calligrasheets calligrastage
  calligrawords cups-filters gnome-commander gwibber-service inkscape karbon kde-runtime kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools kexi krita libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkprintutils4 libkpty4
  libkrosscore4 libkrossui4 libktexteditor4 libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3
  libpoppler-glib8 libpoppler-qt4-4 libsolid4 libthreadweaver4 plasma-scriptengine-javascript poppler-utils
  python-ubuntuone-control-panel ubuntu-desktop ubuntuone-control-panel ubuntuone-control-panel-qt
```

Regards,
Effenberg

---

### Post by BrianBlaze on 2012-09-14
I have yet been able to install nvidia drivers without any problems... I shall try again!

---

### Post by Dr.Paneas on 2012-09-14
I use GTX 465 and I successfully installed 304.48 using [this guide]("http://ubuntuxtreme.com/howto/nvidia-304-48-drivers-released-install-guide/").

It's based on my 1-click install script. If the new drivers cause problem, you can always go back to the stable (non-beta) or remove proprietary and use open source noveau ;)
:popcorn:

---

### Post by Harry33 on 2012-09-14
This is a guide on what to do if something goes wrong.
First of all, if you do not know what you are doing, do not use nvidia*.run package,
only use official or trusted PPA debian (.deb) packages (nvidia-current_*.deb).

It is a good practise to learn the manual installation from the terminal.
So, first download the version you want, for example from a trusted PPA (like Xorg.edgers). It is a very good quality PPA.

After this download the same nvidia-current_*.deb you are successfully using before the installation. Remember where it was downloaded to, but do not keep it in the same folder as the new nvidia-current_*.deb or any other .deb package.

Then in terminal go to the folder where you downloaded your new nvidia-current_*.deb package. See that no other .deb package is in the same folder, otherwise they will get installed too.

Run this command:
sudo apt-get -i *.deb

Then reboot.
If you cannot get to the login screen or desktop, just press cntrl+alt+F1, which takes you to VT1.
Login.
Go to the directory, where the older, working version of the nvidia-current_*.deb is and run the same command again.

sudo apt-get -i *.deb
Reboot and your system is OK again.

---

### Post by Harry33 on 2012-09-17
Now Canonical has a new invention here.
This beta Nvidia driver (304.48 - nvidia-current) has been renamed to nvidia-experimental.
This is a very bad practise and makes it more difficult to install the driver manually.

However, no need to use this QQ flavour as the same driver can be found from Xorg edgers PPA.

---

### Post by dino99 on 2012-09-18
> **Harry33 said:**
> Now Canonical has a new invention here.
This beta Nvidia driver (304.48 - nvidia-current) has been renamed to nvidia-experimental.
This is a very bad practise and makes it more difficult to install the driver manually.

However, no need to use this QQ flavour as the same driver can be found from Xorg edgers PPA.

I was told that Canonical was having a design service ;) , seems not every devs team knows it :mad:

---

### Post by Harry33 on 2012-09-18
And now it says this:

> **Publishing history**

                            **       [304.48-0ubuntu1]("https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-experimental/304.48-0ubuntu1")     **                                           **DELETED**:            [Quantal]("https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-experimental")            pocket **Release**            in component **universe**            and section **misc**                                  
             
[LIST]
[*]       Removed from disk       1 hour ago.
[*]       Removal requested       5 hours ago.
[*]       Deleted       5 hours ago       by [Adam Conrad]("https://launchpad.net/%7Eadconrad")       Being renamed

[*]
[*]       Published       16 hours ago
[/LIST]
     
  
       
   


So now what?

---

### Post by robtygart on 2012-09-19
I just seen an Nvidia Beta driver come up in my additional drivers menu. 304.48. Just installed it, so far its working. Is there anything I should be doing, or looking for, since it is a beta version?

---

### Post by robtygart on 2012-09-19
Supported
> GeForce 600 series:
GTX 690, GTX 680, GTX 670, GT 645, GT 640, GT 630, GT 620, GT 610, 605

GeForce 500 series:
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 560 SE, GTX 560, GTX 555, GTX 550 Ti, GT 545, GT 530, GT 520, 510

GeForce 400 series:
GTX 480, GTX 470, GTX 465, GTX 460 v2, GTX 460 SE v2, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, 405

GeForce 300 series:
GT 340, GT 330, GT 320, 315, 310

GeForce 200 series:
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 210, 205

GeForce 100 series:
GT 140, GT 130, GT 120, G 100

GeForce 9 series:
9800 GX2, 9800 GTX/GTX+, 9800 GT, 9600 GT, 9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 GS, 9300 GE, 9300, 9200, 9100

GeForce 8 series:
8800 Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS, 8600 GT, 8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200 / nForce 730a, 8200, 8100 / nForce 720a

GeForce 7 series:
7950 GX2, 7950 GT, 7900 GTX, 7900 GT/GTO, 7900 GS, 7800 SLI, 7800 GTX, 7800 GT, 7800 GS, 7650 GS, 7600 LE, 7600 GT, 7600 GS, 7550 LE, 7500 LE, 7350 LE, 7300 SE / 7200 GS, 7300 LE, 7300 GT, 7300 GS, 7150 / NVIDIA nForce 630i, 7100 GS, 7100 / NVIDIA nForce 630i, 7100 / NVIDIA nForce 620i, 7050 PV / NVIDIA nForce 630a, 7050 / NVIDIA nForce 630i, 7050 / NVIDIA nForce 610i, 7025 / NVIDIA nForce 630a

GeForce 6 series:
6800 XT, 6800 XE, 6800 Ultra, 6800 Series GPU, 6800 LE, 6800 GT, 6800 GS/XT, 6800 GS, 6800, 6700 XL, 6610 XL, 6600 VE, 6600 LE, 6600 GT, 6600, 6500, 6250, 6200 TurboCache, 6200SE TurboCache, 6200 LE, 6200 A-LE, 6200, 6150SE nForce 430, 6150LE / Quadro NVS 210S, 6150 LE, 6150, 6100 nForce 420, 6100 nForce 405, 6100 nForce 400, 6100

ION series:
ION LE, ION


---

### Post by robtygart on 2012-09-19
N/A 
Old info....

---

### Post by robtygart on 2012-09-19
.........

---

### Post by cariboo on 2012-09-19
Merged two threads on the same subject.

---

