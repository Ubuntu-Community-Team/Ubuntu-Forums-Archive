---
title: "video card : XGI Volari Z9s issue"
date: 2017-10-16
forum: Server Platforms
---

### Post by philoneo on 2017-10-16
Hello,  I have an HP proliant ML150 G6, bi quad cores, I installed Ubuntu  server 16.04.3 and installed Gnome Desktop, it works but the server is  in low definition on screen display, I encounter problems with my video card which is a:

      XGI Volari Z9s Grafikkarte PCI 32MB 1x DVI 1x VGA 96VG -32M-P-D2-XGI.

I found the video card drivers compatible with ubuntu, but I can not install the driver!
I have several options:
1 / I run the install_ubuntu.sh script, I have the following error:
```
# ./install_ubuntu.sh

XGI Linux driver installation for package 2.81.8

ubuntu
Cannot open X11 installation path /usr/X11R6/lib/modules/drivers. Exit.
./install_ubuntu.sh: 254: exit: Illegal number: -1
root@hpc-actaris:/home/phipo/drivers-xgi/drivers-xgi/2.81.08/EM64T/xgipkg_Xorg8_x86_64
```
2 / I execute the executable file: xgi_xg27_x86_64_xorg8_2_81_08.run I have the following error:
```
/phipo/drivers-xgi/drivers-xgi/2.81.08/EM64T# ./xgi_xg27_x86_64_xorg8_2_81_08.run
Verifying archive integrity... All good.
Uncompressing xg27 volari linux package....................................

XGI Linux driver installation for package 2.81.8
ubuntu
XGI Linux driver installation for package 2.81.8
ubuntu
Cannot open X11 installation path /usr/X11R6/lib/modules/drivers. Exit.
install_ubuntu.sh: 254: exit: Illegal number: -1
root@hpc-actaris:/home/phipo/drivers-xgi/drivers-xgi/2.81.08/EM64T# 

```
      do not see how to do this because I have two directories:
      EM64T and IA32 containing the drivers.

> Cards_21.xgi            pcitable.xgi
        readme.txt
Cards_27.xgi            removemodes.sh
       uninstall.sh
                               Vendor.xgi
Cards.xgi                           version
identity_21.xgi           
Identity_27.xgi            
identity.xgi                xgicfg.plx
install_nor.sh             xgiz_drv.so.73
                                xgiz_drv.so.74
                                xgiz_drv.so.75
install_ubuntu.sh        
install.sh            xgiz_drv.so.76
modpci.plx            
pcitable_21.xgi          
pcitable_27.xgi            xorg.conf.fc10x64
        xorg.conf.fc10x86

i have this files with the driver's distribution :



Regards
Philippe

---

### Post by slickymaster on 2017-10-17
Thread moved to **Server Platforms** for a better fit

---

### Post by mörgæs on 2017-10-17
It's a weak card and I would not expect it to run Ubuntu Gnome. If it has to run a GUI at all you should aim for LXDE or something similar light. 

> **philoneo said:**
> 
```

Cannot open X11 installation path /usr/X11R6/lib/modules/drivers. Exit.

```


I don't have that path on my Xubuntu. Do you?
What kind of script are you running?

This might be of interest:
[https://sites.google.com/site/easylinuxtipsproject/xgiz7z9](https://sites.google.com/site/easylinuxtipsproject/xgiz7z9)

---

### Post by philoneo on 2017-10-18
after several tests with the video card "XGI Volari Z9s" I abandoned  this last for a graphics card "3DFX Voodoo3", it is more recent.
I pity that it will work, because on the web there is interesting information.

dmesg of OpenBSD 6.1:
     Code:
     vga1 at pci7 dev 4 function 0 "3DFX Voodoo3" rev 0x01
wsdisplay0 at vga1 mux 1: console (80x25, vt100 emulation)
wsdisplay0: screen 1-5 added (80x25, vt100 emulation) 
i found the drivers libglide3_2002.04.10ds1-11_i386.deb, instalation with dpkg command work fine.
but now can i put the parametres of the file /etc/x11/Xorg

---

