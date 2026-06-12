---
title: "ATI Catalyst™ 9.2 Proprietary Linux x86_64 Display Driver is out"
date: 2009-02-21
forum: The Cafe
---

### Post by newbie2 on 2009-02-21
>     Resolved Issues

        * Resolved visible corruption when starting MythTV frontend in full screen
        * Catalyst Control Center, disabling primary display and re-launching CCC caused a Floating Point Exception
        * Google Earth failed to start
        * With some ATI adapters the display port monitor was not detected after being hotplugged
        * Able to reboot or shutdown when ATI Catalyst Control Center is opened
        * Catalyst Control Center, displayed the wrong version using the Information/Driver Version
        * No audio output was available through HDMI
        * Connecting both a CRT and DFP display device no longer results in the CRT failing to display an image if the DFP is disconnected and then reconnected to the system
        * Corruption is no longer seen on secondary display after enabling secondary display Big Desktop
        * Sections of the task bar no longer turn black when using the application 'Blender'
        * Enemy Territory Quake Wars v1.4, system no longer becomes intermittently unresponsive when game is run.
        * Some Open GL application no longer cause segmentation fault with Crossfire and dual head enabled
        * Maya crash fixed when using the following settings subinvisions Axis and subinvisions Height are set to 2000
        * Tearing no longer occurs during picture-in-picture playback of H.264,VC-1,MPEG2 files on SUSE
        * Playing AVI files with Mplayer in full screen no longer causes Mplayer to stop responding
        * Resolved, Video does not resize or may appear filled with pink/black when changing from a low to high resolution

    Known Issues

        * White screens may occur on the extended displays of a with a quad display configuration with 'Xinerama=on'
        * Quake4 cannot start after using the load default option
        * With both a DFP and CRT connected using the swap monitor option may cause the following error “KDE Panel - The KDE Crash Handler”
        * X may fail to start when the driver has been configured with the following command: aticonfig --force-monitor=nocrt1
        * RedHat 4.7 hot plugging a display may cause X to shutdown
        * Some display corruption may be observed while returning from XServer with two display connected
        * Catalyst Control Center, primary display manager may be missing on systems with dual head enabled
        * Some systems may fail to restore after returning from hibernation
        * Catalyst Control Center, the primary display is not identified when using the Identify Displays button
        * X-Server may become unresponsive when hot plugging the display after changing the resolution
        * Dual head mode, the mouse cursor cannot move to the secondary displays
        * The mouse cursor may fail to render when hot plugging a display in clone mode
        * Catalyst Control Center, on some systems X may fails to start when the resolution is set to less than 1680x1050 through displays manager
        * With some system configurations Catalyst Control Center may take up to 30 seconds to start
        * SUSE 11, No CrossFire confirmation is displayed when running Open GL applications
        * Running Specviewperf 9.0.3 in CrossFire mode may causes a segmentation fault and failures in log file.
        * When X is killed, the desktop background for the display:0.1 remains
        * Screensaver corruption may be observed with 'xinerama on' in multi-head configuration.
        * On some CrossFire systems resizing Glxgreas may cause some screen corruption
        * Corruption may occur in Maya with a multview configuration using three displays
        * Flickering may occur with some screensaver and Flash movies when using either Normal or Extra Visual Effects.
        * X-Server may stop responding or shutdown when loading some Open GL applications on a secondary display
        * On some systems with RedHat 4.7 and Radeon X1800 the system may fail to start after installing the display driver
        * SUSE 10.3 32bit: The operating system may fail to respond when pressing “Ctrl+alt+F7/F8” to switch session when “fgl_glxgears” is running
        * Image rendering is not visible and only able to see the blank application window when moving the application a secondary display
        * Red Hat 5.2 32bit, KDM X windows may restart when user selects to “Start New Session” during user switch

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

---

### Post by Polygon on 2009-02-21
this made me laugh:

> 
SUSE 10.3 32bit: The operating system may fail to respond when pressing “Ctrl+alt+F7/F8” to switch session when “fgl_glxgears” is running


i wonder who reported that bug.

---

### Post by Mazza558 on 2009-02-21
I'll stick to the FOSS drivers, unless these ones bring some decent performance boosts. The FOSS drivers are exceptional, especially in Jaunty.

---

### Post by jimi_hendrix on 2009-02-21
i pray this will fix my bug and let me upgrade to intrepid...

in interpid for waht ever reason i cannot activate my driver...i hit activate and enter my password but nothing happens...

any way i can try this without a reinstall?

---

### Post by Vince4Amy on 2009-02-21
I've found the close sourced drivers to outperform the Open Source ones significantly so far.

---

### Post by jimi_hendrix on 2009-02-22
> **Vince4Amy said:**
> I've found the close sourced drivers to outperform the Open Source ones significantly so far.

same

---

### Post by oldHat on 2009-02-22
> **Vince4Amy said:**
> I've found the close sourced drivers to outperform the Open Source ones significantly so far.


glxgears does 5500 fps under 9.2 with my brand-new 4650.  Would I be better off with FOSS?

---

### Post by Vince4Amy on 2009-02-22
> **oldHat said:**
> glxgears does 5500 fps under 9.2 with my brand-new 4650.  Would I be better off with FOSS?

Well what do you get on glxgears on the open source driver?

---

### Post by oldHat on 2009-02-22
> **Vince4Amy said:**
> Well what do you get on glxgears on the open source driver?

Point taken.  I only used the open source drivers briefly, and didn't have much luck with them.  I'm better off with what I've got.

---

