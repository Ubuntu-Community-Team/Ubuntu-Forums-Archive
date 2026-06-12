---
title: "AMD Catalyst 9.10 Linux Driver Released"
date: 2009-10-23
forum: The Cafe
---

### Post by Pasdar on 2009-10-23
Download/install/test, post comments... :D

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by edin9 on 2009-10-23
What's the 'major advancement' I read about on Phoronix?

---

### Post by Pasdar on 2009-10-23
> **edin9 said:**
> What's the 'major advancement' I read about on Phoronix?

We'll never know unless someone installs it and tests it... I don't have my laptop with me so I can't test.

---

### Post by edin9 on 2009-10-23
> **Pasdar said:**
> We'll never know unless someone installs it and tests it... I don't have my laptop with me so I can't test.

lol

---

### Post by tom66 on 2009-10-23
Does this driver fix Ubuntu's black screen of death when using fglrx?

---

### Post by Pasdar on 2009-10-23
Seems like this is going to be the zillionth, 'let's ask questions, but not try it ourself' topic at UB.

---

### Post by JJ_Kame_R on 2009-10-23
Tried to install in different ways:
dpkg -i, shell, ati installer.

Reconfigured xorg 100 times.
No way to have the xserver starting with fglrx enabled.
I am really disappointed. After almost 6 months no good release for jaunty.
Rolled back to buggy and crappy 9.9.

I wonder when I will start watching movies again with my laptop... maybe when I will buy a new one with an nVidia card... :popcorn:

---

### Post by edin9 on 2009-10-23
> **JJ_Kame_R said:**
> Tried to install in different ways:
dpkg -i, shell, ati installer.

Reconfigured xorg 100 times.
No way to have the xserver starting with fglrx enabled.
I am really disappointed. After almost 6 months no good release for jaunty.
Rolled back to buggy and crappy 9.9.

I wonder when I will start watching movies again with my laptop... maybe when I will buy a new one with an nVidia card... :popcorn:

lolol. Some things never change XD

---

### Post by Foster Grant on 2009-10-23
> **Pasdar said:**
> Download/install/test, post comments... :D

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

No good for me. ATi doesn't actively support its older hardware¹ and an xorg update a few months ago broke the old-but-working version of the Catalyst driver. Fortunately the open-source driver is working fine on my laptop.

[size=1]¹ATi calls it the "legacy support structure" but also says, "The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above." Windows users apparently get an officially-supported driver that doesn't incorporate newer software features. Meh.[/size]

---

### Post by Pasdar on 2009-10-23
> **JJ_Kame_R said:**
> Tried to install in different ways:
dpkg -i, shell, ati installer.

Reconfigured xorg 100 times.
No way to have the xserver starting with fglrx enabled.
I am really disappointed. After almost 6 months no good release for jaunty.
Rolled back to buggy and crappy 9.9.

I wonder when I will start watching movies again with my laptop... maybe when I will buy a new one with an nVidia card... :popcorn:
Whats your videocard

---

### Post by JJ_Kame_R on 2009-10-24
HD3650 laptop version.

---

### Post by Pasdar on 2009-10-24
**ATI Catalyst Linux Display Driver 9.10**

**New Features **
[LIST]
[*]Ubuntu 9.10 early look support
[/LIST]

**Resolved Issues **
[LIST]
[*]"aticonfig -xinerama=on" no longer results in different dimensions and DPI settings between Ubuntu 8.10 and 9.04 
[*]CAL SDK samples will no longer throw an error message while executing on the second ASIC 
[*]Playback with UVD acceleration no longer causes Mplayer to terminate abruptly or display blank video 
[*]Display corruption no longer observed after changing TV format from NTSC to PAL and restarting X server 
[*]System now responds properly when multi-display mode is being configured 
[*]Pressing the "Detect Displays" button in Catalyst Control Center will now detect newly hotplugged displays properly 
[*]System no longer becomes unresponsive when playing VC-1 or H.264 content in dual stream with SD MPEG content 
[*]Changes to gamma values are no longer applied to the wrong display when X is restarted 
[*]With CrossFire enabled, pressing the "Detect Displays" button no longer causes the "3D" settings drop down menu to expand in the Catalyst Control Center Display Manager 
[*]Desktop rotation changes will no longer cause segmentation fault in clone mode 
[*]Systems with both CRT and LVDS displays connected will now respond properly when starting the X server
[/LIST]

**Known Issues **
[LIST]
[*]With CrossFire enabled, system may become unresponsive when switching to DC (battery) mode with full-screen applications running 
[*]Desktop resolution changes through Catalyst Control Center might not be applied after restarting X 
[*]System may become unresponsive when toggling between virtual terminals in multihead configuration with applications running 
[*]System may become unreponsive after executing specific combinations of XRandR reflections and rotations 
[*]X server may fail to start GUI Desktop Manager after enabling secondary adapter using Catalyst Control Center 
[*][Ubuntu 9.04] Animated busy mouse cursor may disappear or flicker in clone mode 
[*]Corruption may be visible after hotplugging a display and doing a Virtual Terminal switch 
[*][RHEL 5.3] The secondary display may become disabled after resuming from sleep/hibernation in big desktop mode 
[*]Screen rotation may result in corrupt video playback 
[*][SUSE 11.1] Unplugging the secondary display and terminating the X server (Ctrl + Alt + Backspace) may cause the primary display to become blank and display corruption 
[*]fgl_glxgears application may fail to function and cause the system to stop responding while performing OpenGL GLX Remote Rendering 
[*]In dual-head mode, performing a XRandR command (rotation or screen resolution change) on screen 1 may cause both screens to display corruption 
[*]Segmentation fault may occur or system may display error during boot up if X is stopped in Dual-Head mode
[/LIST]

---

### Post by blimbo on 2009-10-24
I just upgraded to 9.10 and now find any OpenGL applications are horribly slow, and in one case (Hugin) completely hangs the system.

I have a Radeon 9000 and am currently using the open source drivers (as I believe I was on 9.04).

Current xorg.conf

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

(has fglrx but resitred drivers says no proprietry drivers are installed?)

Old backup 9.04 xorg.conf

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Will the Catalyst drivers do anything to solve my problem?

Cheers,
Tim

---

### Post by Pasdar on 2009-10-24
> **JJ_Kame_R said:**
> HD3650 laptop version.

I have the same videocard, but I haven't tested it yet.. (can't yet)

On phoronix they mention improvements... even with this same card...
[http://www.phoronix.com/forums/showthread.php?t=19753](http://www.phoronix.com/forums/showthread.php?t=19753)

---

### Post by Pasdar on 2009-10-24
> **blimbo said:**
> I just upgraded to 9.10 and now find any OpenGL applications are horribly slow, and in one case (Hugin) completely hangs the system.

I have a Radeon 9000 and am currently using the open source drivers (as I believe I was on 9.04).

Current xorg.conf

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

(has fglrx but resitred drivers says no proprietry drivers are installed?)

Old backup 9.04 xorg.conf

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Will the Catalyst drivers do anything to solve my problem?

Cheers,
Tim
Doesn't hurt to try does it... just remember that the drivers in Ubuntu repositories are beta drivers... you need to download from the website.

---

### Post by JJ_Kame_R on 2009-10-24
> **Pasdar said:**
> I have the same videocard, but I haven't tested it yet.. (can't yet)

On phoronix they mention improvements... even with this same card...
[http://www.phoronix.com/forums/showthread.php?t=19753](http://www.phoronix.com/forums/showthread.php?t=19753)

I wonder how they managed to have an xserver running...
I tried for over 2 ours yesterday.
I will try after the update to karmic...

---

### Post by Tonelero on 2009-10-30
> **JJ_Kame_R said:**
> I wonder how they managed to have an xserver running...
I tried for over 2 ours yesterday.
I will try after the update to karmic...

I`m having the same Black Screen of Death issue. It just doesn't work. FGLRX is a total fail for me since Jaunty. I've tried Catalyst 9.8, 9.9 and now the 9.10, as well as the Restricted Drivers that comes with Ubuntu. Nothing. I have an ATI 4890.

It seems to me that the only way to fix this is buying a Nvidia card. ;)

---

### Post by @ntonius on 2009-10-30
My HD 2400 Pro  (AGP) works fine in 9.10 Karmic with the 9.10 catalyst

---

### Post by days_of_ruin on 2009-10-30
It has been all positive for me, I can play video with compiz enabled just fine. I have yet to experience a freeze when using Virtual Terminal switching. Ati 4770 btw.

---

### Post by handy on 2009-10-30
> **Tonelero said:**
> I`m having the same Black Screen of Death issue. It just doesn't work. FGLRX is a total fail for me since Jaunty. I've tried Catalyst 9.8, 9.9 and now the 9.10, as well as the Restricted Drivers that comes with Ubuntu. Nothing. I have an ATI 4890.

It seems to me that the only way to fix this is buying a Nvidia card. ;)

I've seen that some are having trouble with the 4000 series over on the Arch forum too.

Don't throw your card away, apart from Catalyst eventually getting your bug(s) sorted, the open-source support is moving fast, (though you'll get your good 3D from Catalyst before the free software).

Mark my words it won't be too long & AMD GPUs will be the GNU/FOSS flavour of choice, 2D is already the best & 3D will be. :)

---

### Post by M20554443 on 2009-11-02
Radeon 4670 does not seem to work? When installing the properitary driver (via System - Hardware) there is only a black screen after reboot, and Ubuntu won't come up again. As I have a onboard graphics card, I guess its this issue:

"X server may fail to start GUI Desktop Manager after enabling secondary adapter
using Catalyst Control Center" (from Catalyst 9.10 release notes)

---

### Post by Pasdar on 2009-11-02
> **M20554443 said:**
> Radeon 4670 does not seem to work? When installing the properitary driver (via System - Hardware) there is only a black screen after reboot, and Ubuntu won't come up again. As I have a onboard graphics card, I guess its this issue:

"X server may fail to start GUI Desktop Manager after enabling secondary adapter
using Catalyst Control Center" (from Catalyst 9.10 release notes)
See what happens if you install the drivers from ati website instead. You can disable your onboard videocard in BIOS.

---

### Post by M20554443 on 2009-11-02
Hi, thank you. I have disabled the onboard videocard in BIOS. After activating the drivers (and before the reboot) fglrxinfo shows:

```
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.6)
```

Hm, that doesn't look right, what do you think? I will deactivate them again, and try the 9.10 driver from ATI website later ...

---

### Post by Pasdar on 2009-11-03
> **M20554443 said:**
> Hi, thank you. I have disabled the onboard videocard in BIOS. After activating the drivers (and before the reboot) fglrxinfo shows:

```
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.6)
```

Hm, that doesn't look right, what do you think? I will deactivate them again, and try the 9.10 driver from ATI website later ...

Your system is not even using the drivers. Personally, I never install the drivers from the repositories and always from the site. I checked the internet and more people have gone through the same issue. What does it say in your /etc/xorg.conf?

also check [http://ubuntuforums.org/showthread.php?t=285614](http://ubuntuforums.org/showthread.php?t=285614)

the file from the site should be either a .run or a .bin file, you do sudo chmod +x and then sudo ./nameoffile.whatever.... installation is easy.

---

### Post by togo59 on 2009-11-03
The Catalyst 9.10 install guide talks of uninstalling previously installed graphics drivers. However, I'm not clear whether this is really necessary and, if so, which drivers listed in Synaptic to remove?

E.g. My laptop has a Radeon 3400 do I remove [FONT="Courier New"]xserver-xorg-video-radeon[/FONT] ? What about other [FONT="Courier New"]xserver-xorg-video-xxxx[/FONT] drivers?

The Hardware Drivers utility doesn't make it at all clear what version of FGLRX it is offering to install. All I know is that it will cause the black screen problem (because I tried it). It would be useful if I knew what, exactly, it was trying to install (version etc). Can anyone advise?

To anyone that has successfully installed AMD/ATI Catalyst 9.10 could you post what preliminary steps you took? Also did you do the "Automatic" install, the "Custom Driver" or the "Package Generation" option? (With what results?)

Many thanks!

---

### Post by Pasdar on 2009-11-03
> **togo59 said:**
> The Catalyst 9.10 install guide talks of uninstalling previously installed graphics drivers. However, I'm not clear whether this is really necessary and, if so, which drivers listed in Synaptic to remove?

E.g. My laptop has a Radeon 3400 do I remove [FONT="Courier New"]xserver-xorg-video-radeon[/FONT] ? What about other [FONT="Courier New"]xserver-xorg-video-xxxx[/FONT] drivers?

The Hardware Drivers utility doesn't make it at all clear what version of FGLRX it is offering to install. All I know is that it will cause the black screen problem (because I tried it). It would be useful if I knew what, exactly, it was trying to install (version etc). Can anyone advise?

To anyone that has successfully installed AMD/ATI Catalyst 9.10 could you post what preliminary steps you took? Also did you do the "Automatic" install, the "Custom Driver" or the "Package Generation" option? (With what results?)

Many thanks!
ATI website mentions the following:

> Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

......

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"
You have now successfully uninstalled the ATI Linux Proprietary Driver.

---

### Post by M20554443 on 2009-11-03
I have removed the drivers comming with Ubuntu (8.660) and installed the drivers from ATI site (8.661). The result is almost the same (black screen), except that even recovery mode ins't working anymore (black screen)! Argh, it's no fun ... now I am starting the Live CD, mounting my drives and trying to repair.

---

### Post by M20554443 on 2009-11-03
This is the current xorg.conf (after running ATI installer):

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier "Configured Screen Device"
    Device     "Configured Video Device"
    SubSection "Display"
        Virtual   2560 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

This was my previous xorg.conf:

```
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2560 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
```

(I have two monitors at the moment, I guess right after the Ubuntu installation there wasn't any xorg.conf at all)

---

### Post by togo59 on 2009-11-03
> **Pasdar said:**
> ATI website mentions the following:

Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

......

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati
folder
2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh"
You have now successfully uninstalled the ATI Linux Proprietary Driver. 

Many thanks for the reply. That works if you have installed an ATI driver that didn't come bundled with the OS. The instructions also ask you to uninstall any that did come with the OS. That's the bit that I'd like advice on.

Since some folk have installed Catalyst 9.10 and claim that 2D/3D is working on Radeon graphics using Karmic (running XOrg 1.7.x, 2.6.31, KMS and wotnot), I was just wondering what they did prior to installing it.

---

