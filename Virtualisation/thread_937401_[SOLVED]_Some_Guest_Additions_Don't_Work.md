---
title: "[SOLVED] Some Guest Additions Don't Work"
date: 2008-10-03
forum: Virtualisation
---

### Post by ace214 on 2008-10-03
I have UbuntuStudio Intrepid installed in VirtualBox on a UbuntuStudio Hardy system.

I installed the Guest Additions seemingly without a hitch, but only the mouse pointer integration seems to work. The seamless option is still grayed out and the resolution won't get any bigger than 800x600. I made sure I upped the video memory to 128 MB for the guest OS.

Help? :-)

---

### Post by MystaMax on 2008-10-04
in your intrepid guest, open your xorg.conf file by running one of the following lines from a terminal window:

```
sudo nano /etc/X11/xorg.conf
```or 

```
sudo gedit /etc/X11/xorg.conf
```you want to add the following line to the xorg.conf file

```
Driver      "vboxvideo"
```Look for the Device section w/ the "Configured Video Device" Identifier. It should look like the following section:

```
Section "Device"
          Identifier      "Configured Video Device"
          Driver          "vboxvideo"
EndSection
```

---

### Post by ace214 on 2008-10-08
Thanks, that solved it.

---

