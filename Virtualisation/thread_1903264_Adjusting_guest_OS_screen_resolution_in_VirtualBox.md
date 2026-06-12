---
title: "Adjusting guest OS screen resolution in VirtualBox 4.1.8"
date: 2012-01-02
forum: Virtualisation
---

### Post by ADeadCat on 2012-01-02
So, I'm running VirtualBox 4.1.8 on an Ubuntu 11.10 host, and when I run a guest OS (32-bit BackTrack 5 R1 with a KDE desktop, in this specific case if it matters), the resolution is stuck at 800x600.
This (or some variation of it) seemed to work for others:
```
vboxmanage setextradata global GUI/MaxGuestResolution any
```
But when I run it, nothing seems to happen. Suggestions/other solutions?

---

### Post by lukeiamyourfather on 2012-01-02
Install the guest additions if possible. This will give the guest full control of the virtual hardware offered by VirtualBox including the virtual graphics card. With the guest additions installed the guest should resize the resolution of the monitor to whatever the interface window size is or even fullscreen if you want.

---

### Post by ADeadCat on 2012-01-02
Ok, thanks, I got it to work. Just surprisingly hard to find the guest additions .iso (found it here: [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/) for any future readers)

---

### Post by lukeiamyourfather on 2012-01-02
There's a menu item to mount a disc image of the guest additions if you're using the GUI version of VirtualBox. Manually downloading it is another option like you found.

---

### Post by darvishjo on 2012-01-03
I'm running VirtualBox 3.1.6 but when I download and try to install 4.1_4.1.0 the package installer says "error: conflicts with the installed package 'virtualbox-ose' and I'm not sure what to do.

My biggest problem is guest screen resolution:

I have Windows XP running as guest on Ubuntu 10.04 LTS and am unable to resize the windows screen, which is stuck at 800x600.  I tried running 

vboxmanage setextradata global GUI/MaxGuestResolution any

but this did not change anything.  I have the Guest additions installed.  Under the settings details in Virtual Box OSE it shows I have 16 MB of video memory and that 3d Acceleration and 2D video Acceleration are disabled, but I cannot find a way to enable them.  

I have an NVidia video card.  

Any suggestions how I can fix this?

---

### Post by Perryg on 2012-01-03
@darvishjo,
As the error message indicates major upgrades require you to remove the previous one.  Your guest/guests should not be lost as they are not stored in the same location.

As for the guest resolution, if you are certain that the guest additions are installed in the guest, check to see if auto-resize is activated.  (host+G) or the pull down

Oh and you might want to consider not tagging to a topic that is marked solved.

---

### Post by jerrrys on 2012-01-03
> **darvishjo said:**
> I'm running VirtualBox 3.1.6 but when I download and try to install 4.1_4.1.0 the package installer says "error: conflicts with the installed package 'virtualbox-ose' and I'm not sure what to do.

My biggest problem is guest screen resolution:

I have Windows XP running as guest on Ubuntu 10.04 LTS and am unable to resize the windows screen, which is stuck at 800x600.  I tried running 

vboxmanage setextradata global GUI/MaxGuestResolution any

but this did not change anything.  I have the Guest additions installed.  Under the settings details in Virtual Box OSE it shows I have 16 MB of video memory and that 3d Acceleration and 2D video Acceleration are disabled, but I cannot find a way to enable them.  

I have an NVidia video card.  

Any suggestions how I can fix this?


You must load the proper guess addition.  Not 4.1, but 3.1

---

### Post by terrykiow on 2012-01-04
> **ADeadCat said:**
> So, I'm running VirtualBox 4.1.8 on an Ubuntu 11.10 host, and when I run a guest OS (32-bit BackTrack 5 R1 with a KDE desktop, in this specific case if it matters), the resolution is stuck at 800x600.
This (or some variation of it) seemed to work for others:
```
vboxmanage setextradata global GUI/MaxGuestResolution any
```
But when I run it, nothing seems to happen. Suggestions/other solutions?
Thanks for this.  Having struggled some hours to change the resolution, I found that this worked fine for me to install Windows 7 64-bit on an AMD Athlon CPU (Acer Aspire 5552)

---

### Post by Suncat2000 on 2012-02-04
**Additional information**

Note also that if you have *Guest Additions* installed and you don't use the [FONT="Courier New"]VBoxManage[/FONT] command to reset the maximum resolution, VirtualBox assigns different size choices in windowed mode than in full-screen mode.

On my *Ubuntu 11.10* system running *VirtualBox 4.1.8* with *Guest Additions* and a *Windows 7* guest, VB uses a default resolution of 1024x768 with a maximum of 1152x864 in windowed mode. In full-screen mode, I get the full resolution of my monitor as max resolution, 1280x1024.

---

### Post by adrian_nye on 2012-02-24
On 10.04 (windows 7 host)
this is what worked for me:

1. have same version guest additions and virtualbox
2. install the guest additions
3. use right Ctrl-F to get both screens in the mode you want
4. Select the "Auto-resize Guest Display" option on the View menu of VirtualBox.
5. From Ubuntu System menu, Preferences, Monitors, make sure the checkbox that makes both screens the same is off

The order of these might be a little off.

---

### Post by japzone on 2012-02-25
Or for OSs that aren't yet supported by Guest Additions(like Windows 8 ) follow the steps here:
[http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/]("http://www.windows7hacker.com/index.php/2011/09/running-windows-8-on-virtualbox-with-additional-wide-screen-resolution/")

Allows you to add a Screen Resolution that you can then set while inside the Guest OS.

---

### Post by mideal on 2013-02-02
I installed a WinXP guest in my Linux Mint 14 (Nadia) with VirtualBox.
My notebook has got a native resolution of 1680*1050.
The WinXP has a maximum of 1600*1200 (without any  additional guest drivers).
As I need Xp to use a special VPN software setup needed to work at home
(with FortiClient) without always restart from Linux to Windows I looked for a solution
to better setup the screen resolution - the computer which I logon via remote desktop connection has a resolution of 1680*1050 again, so there are always some differences.

What I found out in the meantime is the possibility of setting up a bigger virtual screen reosultion on the host system, which may help many users with smaller displays.

Use 
> xrandxto find out what the name of your display is, in my case "LCDS", and what is the maximum of resolution your graphics adapter supports, in my case 8192*8192.
Afterwards, you can easily setup higher resolutions e.g. with
> xrandr  --output LVDS --panning 3360x2100which gives me a four times bigger desktop.

Hope somebody finds this useful.

---

### Post by wildmanne39 on 2013-02-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

