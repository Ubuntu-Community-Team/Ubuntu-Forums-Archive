---
title: "New nvidia-graphics-driver launched (304.37)"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-14
Nvidia has launched a new graphics driver for Linux systems, 304.37.
This is no more a beta version, it is certified.

This driver can be downloaded from the xorg-edgers PPA.
It has been built against ABI-11, ABI-12 and ABI-13, so it can be installed on both xserver1.12 and xserver1.13 environments.

If you upgrade from xserver 1.12 to xserver 1.13 (in QQ proposed repos), you need to upgrade all video and input drivers at the same time.
Otherwise learn to use the console without a desktop. :D

Here are the release highlights:

[LIST]
[*]Added       support for the following GPUs:
[/LIST]
 
[LIST]
[*]GeForce GTX 680M
  Quadro K1000M
  Quadro K2000M
  Tesla K10
[/LIST]
 
[LIST]
[*]Removed       the ability to enable SLI on GPUs with ECC enabled.
[*]Fixed       several bugs that prevented some RandR transform geometries from being applied.
[*]Fixed       a bug that caused frequent hangs or crashes on some systems.
[*]Fixed       a bug that would cause corruption and performance  issues in certain OpenGL applications  such as Amnesia: The Dark Descent  on GeForce 6 and 7 GPUs.
[*]Fixed       a bug that caused applications that use DirectColor  visuals, such as Enemy Territory:  Quake Wars and Braid, to appear in  shades of blue instead of the correct  colors.
[*]Modified       handling of RRSetScreenSize requests to ignore  requests that do not actually  resize the screen.This reduces screen   flicker in certain cases when using  GNOME.
[*]Added       a new option, "--disable-nouveau" to nvidia-installer.  This option changes the  action that is chosen by default when  Nouveauis detected by  nvidia-installer. If the "--disable-nouveau"  optionis set, then the  default will be to attempt to disable Nouveau  when it is detected;  otherwise, no attempt will be made unless  requested.
[*]Added       support for xserver ABI 13 (xorg-server 1.13).
[*]Added       support for RandR per-CRTC gamma manipulation through  the RandR 1.2  RRGetCrtcGammaSize, RRGetCrtcGamma, and RRSetCrtcGamma  requests.
[*]Fixed       a bug that caused RRSetOutputPrimary requests to  incorrectly generate BadValue  errors when setting the primary output to  None.This caused  gnome-settings-daemon to crash after changing the  screen configuration in  response to a display hotplug or the display  change hot-key being pressed.
[*]Fixed       a problem where RENDER Glyphs operations would exhibit  severe performance issues in  certain cases, such as when used with  gradients by Cairo and  Chromium.
[*]Fixed       a bug that caused X to hang when resuming certain  DisplayPort display devices (such  as Apple brand mini-DisplayPort to  dual-link DVI adapters) from  power-saving mode.
[*]Fixed       a bug that caused an X screen to be extended to Quadro  SDI Output devices by  default.  An X screen will still use an  SDI  Output device if it is the only  display device available.  To use a SDI   Output device on an X screen with  other display devices available,  include the SDI Output device with either  the "UseDisplayDevice" or  "MetaMode" X configuration options.
[*]Updated       X11 modeline validation such that modes not defined  in a display device's EDID  are discarded if the EDID 1.3 "GTF  Supported" flag is unset or if  the EDID 1.4 "Continuous Frequency" flag  is unset. The new "AllowNonEdidModes" token  for the ModeValidationX  configuration  option can be used to disable this new check.
[*]Fixed       a bug, introduced in the 295.xx release series, with  EDID detection on some  laptop internal panels.  This bug caused  the  laptop internal panel  to show six small copies of the desktop.
[*]Added       support for FXAA, Fast Approximate Anti-Aliasing.  Using regular anti-aliasing modes  or Unified Back Buffers with FXAA is  not currently supported.
[*]Enhanced       the functionality of the IncludeImplicitMetaModes X  configuration option: Implicit MetaModes will be added for the  primary  display device,  even if multiple display devices are in use  when X is initialized.
[/LIST]
 
[LIST]
[*]Implicit MetaModes will be added for common  resolutions, even
  if there isn't a mode with that resolution in  the mode pool of
the display device.
Extended the syntax of the IncludeImplicitMetaModes  X
  configuration option, e.g., to control which  display device is
  used for creation of implicit MetaModes.
See the description  of the IncludeImplicitMetaModes X configuration
  option in the README  for details.
[/LIST]
    
[LIST]
[*]Modified       the handling of the RandR 1.0/1.1 requests  RRGetScreenInfo and RRSetScreenConfig  (e.g., `xrandr -q --q1` and  `xrandr --size ...` and `xrandr  --orientation ...`) such that they  operate on MetaModes. This was the behavior  in NVIDIA X driver versions  295.xx and earlier, but 302.xx  releases altered the handling of these  RandR 1.0/1.1 requests to  operate on a single RandR output's modes.
[*]With       the above changes to IncludeImplicitMetaModes and RandR  1.0/1.1 handling, fullscreen  applications (e.g., SDL-based  applications, Wine), should have  more resolutions available to them,  and should interact better with  multiple monitor configurations.
[*]Fixed       a bug that could cause G8x, G9x, and GT2xx GPUs to  display a black screen or corruption  after waking up from suspend.
[*]Fixed       several bugs that could cause some OpenGL programs to hang when calling fork(3).
[*]Fixed       an nvidia-settings bug that caused the results of  ProbeDisplays queries made with the  --display-device-string option to  be formatted incorrectly.
[*]Improved       the responsiveness of updates to the nvidia-settings control panel when  displays are hotplugged.
[*]Fixed       a bug that caused display corruption when setting some transforms,  especially when panning a transformed display.
[*]Fixed       a bug that caused extra RandR events to be generated the first time a display is  hotplugged.
[*]Fixed       a bug that caused X11 modelines with '@' in their names to be rejected.
[*]Added       support for DisplayPort 1.2 branch devices, which  allow multiple displays to be  connected to a single DisplayPort  connector on a graphics board.
[*]Fixed       a bug that caused most OpenGL texture uploads to be  slow when the context was bound  rendering to an RGB overlay drawable.
[*]Fixed       a bug that caused audio over HDMI to not work after restarting the X server on some  MCP7x (IGP) GPUs.
[*]Updated       the X configuration option "UseDisplayDevice" to honor the value  "none" on any GPU.
[*]Added       support for DKMS in nvidia-installer. Installing the  kernel module through DKMS  allows the module to be rebuilt  automatically when changing to a  different Linux kernel. See the README  and the nvidia-installer help  text for the "--dkms" option.
[*]Added       RandR output properties _ConnectorLocation,  ConnectorNumber, ConnectorType, EDID,  _GUID, and SignalFormat.  See the  README  for details on these properties.
[*]Extended       support for Base Mosaic to all G80+ SLI configurations with up to three displays.
[*]Fixed       a bug that caused some monitors to fail to wake from  DPMS suspend mode when multiple  DisplayPort monitors were attached to  one GPU.
[*]Removed       controls for XVideo attributes from the "X Server  XVideo Settings" page  of the nvidia-settings control panel. XVideo  attributes can be configured in  XVideo player applications, or through  utilities such as xvattr.
[*]Fixed       a bug that caused all ports on an XVideo adaptor to share color correction  settings.
[*]Removed       support for the following X configuration options:
[/LIST]
 
[LIST]
[*]SecondMonitorHorizSync
  SecondMonitorVertRefresh
[/LIST]
 
[LIST]
[*]Similar control is  available through the NVIDIA HorizSync and
  VertRefresh X  configuration options.  Please see the  NVIDIA driver
  README for details.
[/LIST]
 
[LIST]
[*]Fixed       a bug that prevented NVIDIA 3D Vision Pro from working properly when  switching between X servers on different VTs.
[*]Added       support for desktop panning when rotation, reflection,  or transformation is  applied to a display device (either through RandR  or through the  MetaMode syntax); panning would previously be ignored  in that case.
[*]Implemented       hotfix for a privilege escalation vulnerability reported on August 1, 2012.  For more details, see:
[/LIST]

---

### Post by MikeCyber on 2012-08-14
This should fix also the Flashplugin color problem? Just updated with:

sudo service lightdm stop

sudo ./NV* --update

sudo reboot

---

### Post by Harry33 on 2012-08-14
Well, gnome-shell does not run with this xserver1.13 and nvidia-current_304.37 combination. Only xserver1.12 works.

---

### Post by effenberg0x0 on 2012-08-14
> **Harry33 said:**
> Well, gnome-shell does not run with this xserver1.13 and nvidia-current_304.37 combination. Only xserver1.12 works.

Confirmed, I just updated/upgraded QQ using only default sources and installed Nvidia 304.37 from Nvidia binary installer. I haven't tested it extensively yet, but it seems to be OK with X.Org X Server 1.12.1.902 (1.12.2 RC 2) and failed with 1.13.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-14
Same here - you have to figure this is a known issue
(can't file a good apport on Xorg crash due to no current db symbols for module-init-tools

---

### Post by Harry33 on 2012-08-15
I bet this is a well known issue.
That is why nvidia drivers xserver 1.13 support is only a preliminary one.

---

### Post by Ravi5kumar on 2012-08-17
Will it will be available for ubuntu 12.04 LTS?

---

### Post by Harry33 on 2012-08-17
> **Ravi5kumar said:**
> Will it will be available for ubuntu 12.04 LTS?

It is already available from xorg-edgers.
You can manually download nvidia-current from there and install it with dpkg.
The same driver supports xserver1.11 and xserver1.12 and xserver1.13.

---

### Post by Ravi5kumar on 2012-08-17
> **Harry33 said:**
> It is already available from xorg-edgers.
You can manually download nvidia-current from there and install it with dpkg.
The same driver supports xserver1.11 and xserver1.12 and xserver1.13.

Thanks, but can I get it via official update?:confused:

---

### Post by Harry33 on 2012-08-18
> **Ravi5kumar said:**
> Thanks, but can I get it via official update?:confused:

I am afraid you cannot.

---

### Post by dino99 on 2012-08-18
nouveau works with the actual packages if you follow this post:

[http://ubuntuforums.org/showpost.php?p=12178106&postcount=7](http://ubuntuforums.org/showpost.php?p=12178106&postcount=7)

---

### Post by Harry33 on 2012-08-19
It is true that nouveau works with xserver 1.13 (both from QQ repos).
But, xserver 1.12 and nvidia-current works so much better.
No need to use xserver 1.13 for the time being.
New nvidia driver will anyway be ready soon.

---

### Post by xeizo on 2012-08-19
> **Harry33 said:**
> It is true that nouveau works with xserver 1.13 (both from QQ repos).
But, xserver 1.12 and nvidia-current works so much better.
No need to use xserver 1.13 for the time being.
New nvidia driver will anyway be ready soon.

xserver 1.13 works just fine with Nvidia 304.32 if one uses xubuntu-desktop, chromium-browser or opera instead of unity and firefox. Skyrim under Wine is noticeable more smooth with xfce under the hood than with unity, so mabe this breakage was a good thing because it changed my usage beaviour("real" gaming under Linux is the next big thing, ask Valve, in that case a 3D resource-hungy desktop like Unity is of no benefit).

Even Microsoft scrapped Aero in Windows 8, Ubuntu is moving in the different direction. Xubuntu ftw, as it seems  :)

---

### Post by VinDSL on 2012-08-19
> **xeizo said:**
> [...] maybe this breakage was a good thing because it changed my usage behavioral [...]
Heh!  My thoughts, exactly.

I'm already back on LXDE...  :D

---

### Post by teHIngo on 2012-08-19
Any clue when this one will land in Quantal officially? I don't understand how it fits their new stable alpha policy that they uploaded Xorg 13 but did not wait for the NVIDIA driver. This broke the systems of many testers.

---

### Post by effenberg0x0 on 2012-08-19
> **teHIngo said:**
> Any clue when this one will land in Quantal officially? I don't understand how it fits their new stable alpha policy that they uploaded Xorg 13 but did not wait for the NVIDIA driver. This broke the systems of many testers.

+1... People already answered why it was done, I just can't understand how it is reasonable or helps Ubuntu be a better product. 

IMO the problem is that there's no policy in the sense of repos for testers. Right now we're 100% development when it comes to these things, testing seems to be secondary. I have tried to bring attention to this some times in the last two cycles or so, but I have failed to make people understand how vital this is. A testers repo, associated with a working hw database is the only viable way for real testing and reporting. Maybe it's the language barrier but my suggestions for a testers-only repo using a new concept (named "working sets") and a "T-1" (24-hours delayed) repo were even considered funny somehow :)

Last time we messed up with nvidia stuff PP LTS was released with a broken and exploitable nvidia-current, we got tons of LP reports, a lot of work for LP triaging (still happening) and support (UF, AskUbuntu, International Boards, etc). 

Regards,
Effenberg

---

### Post by Harry33 on 2012-08-20
> **teHIngo said:**
> Any clue when this one will land in Quantal officially? I don't understand how it fits their new stable alpha policy that they uploaded Xorg 13 but did not wait for the NVIDIA driver. This broke the systems of many testers.

Well regarding nvidia-current-304.37, it actually does not help the situation with xserver_1.13 any better. It simply does not work with that one.

But, I do think that xserver-1.13 should have stayed in the proposed repo for a bit longer, as it really is only matter of a short time until we have a working nvidia blob.

Anyway, it seems to me Canonical does not care about closed drivers of nvidia that much.
It is apparently enough to know that the open source nouveau is working with xserver_1.13. The same applies to open source ati driver vs fglrx.

---

### Post by lucazade on 2012-08-20
unfortunately nouveau hard freeze after some mins on my Nvidia GTS 250.. reported bug but never been solved!

---

### Post by teHIngo on 2012-08-20
> **Harry33 said:**
> Well regarding nvidia-current-304.37, it actually does not help the situation with xserver_1.13 any better. It simply does not work with that one.

But, I do think that xserver-1.13 should have stayed in the proposed repo for a bit longer, as it really is only matter of a short time until we have a working nvidia blob.

Anyway, it seems to me Canonical does not care about closed drivers of nvidia that much.
It is apparently enough to know that the open source nouveau is working with xserver_1.13. The same applies to open source ati driver vs fglrx.

Thanks for the answer. Indeed they seem to care little... Which is not the smartest thing to do, however, since on my company workstation I can not use a multi-monitor set-up with the Nouveau driver. If I want to keep testing without major annoyances it would be nice to at least have a working multi-monitor setup, but I of course I also realize that during alphas one can not always expect everything to work.

Is it possible to revert back to the old XORG until this has been fixed? Otherwise, how long would the wait be until the new driver is in? I don't even know who to ask about this...

---

### Post by xeizo on 2012-08-20
So, Gnome-shell, Unity and Mozilla doesn't work with 1.13/Nvidia-blob(304.32 in my case, 304.37 seems to be a lemon).

But it's amazing how all other stuff works just fine, Kubuntu and Xubuntu - no problem - heavy contemporary Windows games under Wine - no problem - Windows 8 RTM under Virtualbox with both 2D- and 3D-accelleration enabled through guest additions - works fine!(I've tried it all)

Somehow the blob itself doesn't seem that bad, neither do Xorg 1.13 - I am running Windows 8 in fullscreen right now posting this - works perfect, could it be something else ...

---

### Post by Harry33 on 2012-08-20
> **xeizo said:**
> So, Gnome-shell, Unity and Mozilla doesn't work with 1.13/Nvidia-blob(304.32 in my case, 304.37 seems to be a lemon).

But it's amazing how all other stuff works just fine, Kubuntu and Xubuntu - no problem - heavy contemporary Windows games under Wine - no problem - Windows 8 RTM under Virtualbox with both 2D- and 3D-accelleration enabled through guest additions - works fine!(I've tried it all)

Somehow the blob itself doesn't seem that bad, neither do Xorg 1.13 - I am running Windows 8 in fullscreen right now posting this - works perfect, could it be something else ...

The issue with nvidia-current not working properly with xserver_1.13 is about Nvidia Open GL driver calling invalid function pointers due to changes (compared to xserver_1.12) in the layout of xserver_1.13. data structure. So this is a known bug now.
It will be resolved in the next update of Nvidia blob.

---

### Post by xeizo on 2012-08-20
> **Harry33 said:**
> The issue with nvidia-current not working properly with xserver_1.13 is about Nvidia Open GL driver calling invalid function pointers due to changes (compared to xserver_1.12) in the layout of xserver_1.13. data structure. So this is a known bug now.
It will be resolved in the next update of Nvidia blob.

That's great news if the problem have been isolated, seems most programs didn't use those pointers, even if we now know where they where vital.

---

### Post by teHIngo on 2012-08-27
Is it possible to run the NVIDIA drivers in Quantal again? Can I install nvidia-current without breaking my system?

---

### Post by paul_in_london on 2012-08-27
> **teHIngo said:**
> Is it possible to run the NVIDIA drivers in Quantal again? Can I install nvidia-current without breaking my system?

The new version (304.43) hasn't hit the repos yet.

I'd suggest waiting until it does. :smile:

EDIT: But if you can't wait see here:

[http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

---

### Post by Sir_Sid on 2012-08-27
It is possible, as was said earlier in the thread. Just make sure you don't run xorg version 1.13 with them as unity won't play nice in that combination

---

### Post by paul_in_london on 2012-08-27
The new nvidia-settings has arrived:

```
paul@quantal-64:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 304.43-0ubuntu1~xedgers~quantal1
  Candidate: 304.43-0ubuntu1~xedgers~quantal1
  Version table:
 *** 304.43-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
paul@quantal-64:~$
```

so it shouldn't be too long before the nvidia-current update turns up.

---

### Post by paul_in_london on 2012-08-27
Well it's here, but doesn't build for 3.6-rc3:

```
Current status: 1 update [+1].
paul@quantal-64:~$ sudo aptitude full-upgrade                                   
The following packages will be upgraded: 
  nvidia-current 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.7 MB of archives. After unpacking 27.6 kB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main nvidia-curr
ent amd64 304.43-0ubuntu1~xedgers~quantal1 [67.7 MB]
Fetched 67.7 MB in 45s (1,473 kB/s)                                             
(Reading database ... 208918 files and directories currently installed.)
Preparing to replace nvidia-current 304.37-0ubuntu1~xedgers~quantal1 (using .../
nvidia-current_304.43-0ubuntu1~xedgers~quantal1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-current (304.43-0ubuntu1~xedgers~quantal1) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Hewlett-Packard with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Hewlett-Packard with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.43 DKMS files...
Building only for 3.6.0-030600rc3-generic
Building for architecture x86_64
Building initial module for 3.6.0-030600rc3-generic
Error! Application of patch buildfix_kernel_3.6.patch failed.
Check /var/lib/dkms/nvidia-current/304.43/build/ for more information.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.6.0-030600rc3-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 0 updates [-1].
paul@quantal-64:~$
```

What am I supposed to be looking at in here though?!

```
paul@quantal-64:~$ ls -la /var/lib/dkms/nvidia-current/304.43/build/                                                                                                                                                                          
total 15384
drwxr-xr-x 3 root root     4096 Aug 27 20:46 .
drwxr-xr-x 3 root root     4096 Aug 27 20:46 ..
-rwxr-xr-x 1 root root    66944 Aug 27 20:46 conftest.sh
-rw-r--r-- 1 root root     9324 Aug 27 20:46 cpuopsys.h
-rw-r--r-- 1 root root      478 Aug 27 20:46 dkms.conf
-rw-r--r-- 1 root root     9077 Aug 27 20:46 gcc-version-check.c
-rw-r--r-- 1 root root     5720 Aug 27 20:46 g_nvreadme.h
-rw-r--r-- 1 root root     2079 Aug 27 20:46 makefile
-rw-r--r-- 1 root root     8227 Aug 27 20:46 Makefile
-rw-r--r-- 1 root root     8227 Aug 27 20:46 Makefile.kbuild
-rw-r--r-- 1 root root     3853 Aug 27 20:46 Makefile.nvidia
-rw-r--r-- 1 root root    39855 Aug 27 20:46 nv-acpi.c
-rw-r--r-- 1 root root    39855 Aug 27 20:46 nv-acpi.c.orig
-rw-r--r-- 1 root root      438 Aug 27 20:46 nv-acpi.c.rej
-rw-r--r-- 1 root root   107334 Aug 27 20:46 nv.c
-rw-r--r-- 1 root root      825 Aug 27 20:46 nv-chrdev.c
-rw-r--r-- 1 root root     7042 Aug 27 20:46 nv-cray.c
-rw-r--r-- 1 root root      453 Aug 27 20:46 nverror.h
-rw-r--r-- 1 root root     3260 Aug 27 20:46 nv-gvi.c
-rw-r--r-- 1 root root    25776 Aug 27 20:46 nv.h
-rw-r--r-- 1 root root     9816 Aug 27 20:46 nv-i2c.c
-rw-r--r-- 1 root root 14998056 Aug 27 20:46 nv-kernel.o
-rw-r--r-- 1 root root    67157 Aug 27 20:46 nv-linux.h
-rw-r--r-- 1 root root     2974 Aug 27 20:46 nv-memdbg.h
-rw-r--r-- 1 root root      470 Aug 27 20:46 nv-mempool.c
-rw-r--r-- 1 root root      715 Aug 27 20:46 nv-misc.h
-rw-r--r-- 1 root root     3281 Aug 27 20:46 nv-mlock.c
-rw-r--r-- 1 root root    14546 Aug 27 20:46 nv-mmap.c
-rw-r--r-- 1 root root     6514 Aug 27 20:46 nv-p2p.c
-rw-r--r-- 1 root root     5817 Aug 27 20:46 nv-p2p.h
-rw-r--r-- 1 root root     7092 Aug 27 20:46 nv-pat.c
-rw-r--r-- 1 root root    22614 Aug 27 20:46 nv-procfs.c
-rw-r--r-- 1 root root     2946 Aug 27 20:46 nv-proto.h
-rw-r--r-- 1 root root    21048 Aug 27 20:46 nv-reg.h
-rw-r--r-- 1 root root    24759 Aug 27 20:46 nvtypes.h
-rw-r--r-- 1 root root     1003 Aug 27 20:46 nv-usermap.c
-rw-r--r-- 1 root root    24364 Aug 27 20:46 nv-vm.c
-rw-r--r-- 1 root root     2447 Aug 27 20:46 nv-vtophys.c
-rw-r--r-- 1 root root     9362 Aug 27 20:46 os-agp.c
-rw-r--r-- 1 root root      807 Aug 27 20:46 os-agp.h
-rw-r--r-- 1 root root    36574 Aug 27 20:46 os-interface.c
-rw-r--r-- 1 root root    10918 Aug 27 20:46 os-interface.h
-rw-r--r-- 1 root root     1094 Aug 27 20:46 os-mtrr.c
-rw-r--r-- 1 root root     2551 Aug 27 20:46 os-registry.c
-rw-r--r-- 1 root root     1552 Aug 27 20:46 os-smp.c
-rw-r--r-- 1 root root      712 Aug 27 20:46 os-usermap.c
drwxr-xr-x 2 root root     4096 Aug 27 20:46 patches
-rw-r--r-- 1 root root     1426 Aug 27 20:46 rmil.h
-rw-r--r-- 1 root root     5224 Aug 27 20:46 rmretval.h
-rw-r--r-- 1 root root     5195 Aug 27 20:46 xapi-sdk.h
paul@quantal-64:~$
```

Haven't tried reinstalling with the 3.5 kernel.

---

### Post by Colo993 on 2012-08-27
I installed 304.37 on my Ubuntu 12.04 Dell laptop with an Nvidia NVS 3100M chipset and quickly discovered that I can't go in to suspend mode when the lid is closed.  I re-installed the 295.59 driver and it fixed the suspend issues.

Colo993

---

### Post by mc4man on 2012-08-27
> **paul_in_london said:**
> Well it's here, but doesn't build for 3.6-rc3:


What am I supposed to be looking at in here though?!

In that folder is a patch dir. with the 3.6 patch which is trying to patch nv-acpi.c
It fails likely because the code in the patch differs from the .c file
specifically - 
patch 
```
if (pNvAcpiObject->notify_handler_installed)
     {
         [COLOR="Red"]// no status returned for this function[/COLOR]
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,0)
+        acpi_os_wait_events_complete();
+#else
         acpi_os_wait_events_complete(NULL);
+#endif
 
         // remove event notifier
         status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```

.c
```
 if (pNvAcpiObject->notify_handler_installed)
    {
       [COLOR="Red"] NV_ACPI_OS_WAIT_EVENTS_COMPLETE();[/COLOR]

        // remove event notifier
        status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```


"Haven't tried reinstalling with the 3.5 kernel."
works fine

---

### Post by paul_in_london on 2012-08-27
> **mc4man said:**
> In that folder is a patch dir. with the 3.6 patch which is trying to patch nv-acpi.c
It fails likely because the code in the patch differs from the .c file
specifically - 
patch 
```
if (pNvAcpiObject->notify_handler_installed)
     {
         [COLOR="Red"]// no status returned for this function[/COLOR]
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,0)
+        acpi_os_wait_events_complete();
+#else
         acpi_os_wait_events_complete(NULL);
+#endif
 
         // remove event notifier
         status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```

.c
```
 if (pNvAcpiObject->notify_handler_installed)
    {
       [COLOR="Red"] NV_ACPI_OS_WAIT_EVENTS_COMPLETE();[/COLOR]

        // remove event notifier
        status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```


"Haven't tried reinstalling with the 3.5 kernel."
works fine

Ah, ok. Thanks mc4man.

---

### Post by mc4man on 2012-08-27
> **paul_in_london said:**
> Ah, ok. Thanks mc4man.
If you were inclined to _fool about_ I'd edit the patch to match the code, as in take the red line from the code & use it to replace the red line in the patch
(noting that _I've no past history_ with this code.. & if feels like there should be an empty line after NV_ACPI_OS_WAIT_EVENTS_COMPLETE(); though may not matter
```
--- a/nv-acpi.c
+++ b/nv-acpi.c
@@ -300,7 +300,11 @@ static int nv_acpi_remove(struct acpi_de
     if (pNvAcpiObject->notify_handler_installed)
     {
         NV_ACPI_OS_WAIT_EVENTS_COMPLETE();
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3,6,0)
+        acpi_os_wait_events_complete();
+#else
         acpi_os_wait_events_complete(NULL);
+#endif
 
         // remove event notifier
         status = acpi_remove_notify_handler(device->handle, ACPI_DEVICE_NOTIFY, nv_acpi_event);
```

Edit: though it may be that the build folder is overwritten when trying a re-install, in that case you'd need to unpack the .deb, edit, repack
(if so probably should be done as root to maintain any permissions though again may not matter, I did something similar so I could use the 290.10 package in 12.04 with the 3.5 kernel

---

### Post by paul_in_london on 2012-08-27
Another update and it now builds ok with 3.6-rc3:

```
The following packages will be upgraded: 
  nvidia-current 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.7 MB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main nvidia-curr
ent amd64 304.43-0ubuntu1~xedgers~quantal2 [67.7 MB]
Fetched 67.7 MB in 45s (1,480 kB/s)                                             
(Reading database ... 208918 files and directories currently installed.)
Preparing to replace nvidia-current 304.43-0ubuntu1~xedgers~quantal1 (using .../
nvidia-current_304.43-0ubuntu1~xedgers~quantal2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-current (304.43-0ubuntu1~xedgers~quantal2) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Hewlett-Packard with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Hewlett-Packard with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.43 DKMS files...
Building only for 3.6.0-030600rc3-generic
Building for architecture x86_64
Building initial module for 3.6.0-030600rc3-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.6.0-030600rc3-generic/updates/dkms/

depmod......

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.6.0-030600rc3-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 0 updates [-1].
paul@quantal-64:~$
```

---

### Post by mc4man on 2012-08-27
Interesting -  the change was to dkms.conf & dkms.conf.ini

-PATCH[0]="buildfix_kernel_3.6.patch"
-PATCH_MATCH[0]="^3.6"
+#PATCH[0]="buildfix_kernel_3.6.patch"
+#PATCH_MATCH[0]="^3.6

---

### Post by VinDSL on 2012-08-27
Heh!

That 304.43-0ubuntu1~xedgers~quantal**[COLOR="Red"][SIZE="+1"] 1[/SIZE][/COLOR]** was quite a hoot, eh what?  :D

I'm booted into Unity under Linux 3.6/xserver 1.13/nVidia 304.43 now.

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.43-0ubuntu1~xedgers~quantal2
  Candidate: 304.43-0ubuntu1~xedgers~quantal2
  Version table:
 *** 304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
     304.32-0ubuntu4 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages

vindsl@Zuul:~$ apt-cache policy  xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.12.99.905-0ubuntu3
  Candidate: 2:1.12.99.905-0ubuntu3
  Version table:
 *** 2:1.12.99.905-0ubuntu3 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
     2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages

vindsl@Zuul:~$ uname -a
Linux Zuul 3.6.0-030600rc3-generic #201208221735 SMP Wed Aug 22 21:45:31 UTC 2012 i686 i686 i686 GNU/Linux

```

All's well, that ends well.  Good job edgers!

---

### Post by paul_in_london on 2012-08-27
Everything works ok now with the latest nvidia-current (304.43-0ubuntu1~xedgers~quantal**[COLOR="Red"]2[/COLOR]**), 3.6-rc3 and xserver 1.13.

G-S and FF load ok. No need to disable glx in xorg.conf any more.

---

### Post by VinDSL on 2012-08-27
> **paul_in_london said:**
> G-S and FF load ok.[...]
LXDE/Openbox loads ok too.

BTW, did use lose your shutdown app-indicator in Unity?

I removed PulseAudio a few days ago, and immediately lost my volume indicator.  That was to be expected. But, now, my shutdown button is gone too.

This doesn't have anything to do with nvidia-current.  Just curious...

---

### Post by paul_in_london on 2012-08-27
> **VinDSL said:**
> LXDE/Openbox loads ok too.

BTW, did use lose your shutdown app-indicator in Unity?

I removed PulseAudio a few days ago, and immediately lost my volume indicator.  That was to be expected. But, now, my shutdown button is gone too.

This doesn't have anything to do with nvidia-current.  Just curious...

Hi Vin,

Well I haven't got Unity installed, but I don't see a corresponding shutdown option in G-S. Haven't logged into G-S for a long time though (just wanted to check it out after the latest updates) so I'm not sure if there was a shutown option there before! :lolflag:

Cheers,

Paul

---

### Post by VinDSL on 2012-08-27
> **paul_in_london said:**
> Hi Vin,

Well I haven't got Unity installed, but I don't see a corresponding shutdown option in G-S.[...]
Okay, thanks, Paul!

I'm running 3 DEs right now -- Unity, G-S & LXDE.

Shutdown buttons are available in G-S & LXDE, but not Unity.

I'll go see if I can get it working again, now that my system isn't all hacked up.  ;)

---

### Post by Cheltspy on 2012-08-27
Everything seems to working fine with 304.43:D

Over scan problems on HDTVs can be solved by ViewPortIn/Out in the screen section of xorg.conf 

Example;

Option "metamodes" "DFP-0: 1280x720 { ViewPortIn=1280x720, ViewPortOut=1250x690+15+15 }"

The above creates a 15 point border around the screen edges and scales the desktop within.

---

### Post by paul_in_london on 2012-08-27
> **VinDSL said:**
> Okay, thanks, Paul!

I'm running 3 DEs right now -- Unity, G-S & LXDE.

Shutdown buttons are available in G-S & LXDE, but not Unity.

I'll go see if I can get it working again, now that my system isn't all hacked up.  ;)

Yeah I've got a mininal LXDE quantal install on another partition, but I mainly use this gnome install.

And most of the time I shutdown from the shell anyway!

---

### Post by jerrylamos on 2012-08-27
> **VinDSL said:**
> BTW, did use lose your shutdown app-indicator?27 August Daily Build updated Unity is a bit wierder than usual - it's on a 1366x768 TV via VGA.  The wallpaper shows as 1366x768 - but there's an overlay on the top left 800x600 pixels there's a whole other copy of the wallpaper.  Not only that, but the usual set of applets on the top right panel are repeated - once where they should be at the 1366 end of the line, and again at the 800 corner.  

The applets at the normally expected 1366 don't work, not even logoff.

The applets at the unexpected 800 corner do work.  They're about 2/3 of the way across the screen.

Curious.  I'll let the Unity buffs handle the Unity problems.  Flaky install icons, drop down windows that display nothing until moused over, etc.  If I get a crash I'll let apport report that of course.

I did a sudo apt-get install lxde everything I've tried works.  Lxde is a Debian desktop and Ubuntu is still close enough to Debian that lxde works.

The terminal sudo halt and sudo reboot did work under Unity desktop.

Jerry

---

### Post by VinDSL on 2012-08-27
> **jerrylamos said:**
> 27 August Daily Build updated Unity is a bit wierder than usual [...]

Not only that, but the usual set of applets on the top right panel are repeated - once where they should be at the 1366 end of the line, and again at the 800 corner.  

The applets at the normally expected 1366 don't work, not even logoff.

The applets at the unexpected 800 corner do work.  They're about 2/3 of the way across the screen.

Curious.
Thanks, Jerry!

I've been checking into the situation, and...

The session-indicator is actually there, but it's sitting so far to the right, that it's located off the visible area of my display.

I accidentally discovered this by switching my theme to Ambiance.  With the Ambiance theme, everything aligns itself correctly.  But, if I choose a theme other than Ambiance, the session box drifts out of view again.

cecilpierce started a thread about this:  [http://ubuntuforums.org/showthread.php?t=2049044](http://ubuntuforums.org/showthread.php?t=2049044)

---

### Post by Harry33 on 2012-08-28
Regarding the gnome-shell - xserver(1.13) - nvidia-current issue, that I referred to
in post #3, I can now mark this issue solved.
We have a working nvidia-current(304.43) now.
However, it is available from xorg-edgers PPA for the time being, not yet from the QQ official repos.

---

### Post by Harry33 on 2012-08-28
Here are the nvidia graphics drivers (304.43) release highlights:

 
[LIST]
[*]Added support for the following GPUs:
[LIST]GeForce  GTX 660 Ti
  Quadro  K5000
  Quadro  K5000M
  Quadro  K4000M
  Quadro  K3000M
  NVS 510
[/LIST]
[*]Fixed a bug that caused pre-release versions of X.Org xserver 1.13  to crash when certain  GLX operations were performed, such as when  starting  Firefox.
[*]Fixed a bug that caused VDPAU to hang when expanding the YouTube Flash Player.
[*]Fixed a bug that caused gnome-settings-daemon to revert display configuration changes  made by nvidia-settings.
[*]Updated nvidia-settings to use RandR per-CRTC gamma control, when  available.  When controlling an X server with support for  RandR 1.2,   nvidia-settings will  display the color correction widget as a tab   within each display  device page, instead of a per-X screen color  correction page.
[*]Fixed a bug that prevented the display palette from being updated immediately after an  application called XStoreColors.
[*]Added the ability to select and move X screens in the "X Server  Display Configuration" page of nvidia-settings via Ctrl-(Left)Click +  Drag.
[/LIST]

---

### Post by effenberg0x0 on 2012-08-28
As usual, it's available from Nvidia (proprietary binary installer):

**32-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86-304.43.run)

**64-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run)

Now who's gonna install it, remove the pin on xserver, upgrade xserver* to current and report back? I'm too lazy :)

Regards,
Effenberg

---

### Post by Harry33 on 2012-08-28
> **effenberg0x0 said:**
> As usual, it's available from Nvidia (proprietary binary installer):

**32-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86_64-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86_64-304.43.run)

**64-bit**
wget [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run)

Now who's gonna install it, remove the pin on xserver, upgrade xserver* to current and report back? I'm too lazy :)

Regards,
Effenberg


I have installed the deb package from xorg-edgers PPA,
nvidia-current (304.43-0ubuntu1~xedgers~quantal2).
That is working here.

---

### Post by effenberg0x0 on 2012-08-28
> **Harry33 said:**
> I have installed the deb package from xorg-edgers PPA,
nvidia-current (304.43-0ubuntu1~xedgers~quantal2).
That is working here.

Hi Harry33,

I just finished testing with the binary installer, it is working fine. I have removed all pins, fully upgraded QQ and got into Unity normally. Thunderbird, Firefox are stable so far.

The only two things I have noticed that are worth mentioning:

- Using the desktop (opening the dash, moving windows, etc) while running any glx application had a horrible performance after install/reboot. One can test that by running glxgears and trying to use the desktop. As it has happened in the past, unchecking "Sync to Vblank" in ccsm -> OpenGL fixes it. **EDIT:** Checking Vsync in nvidia-settings causes the same sluggishness, unchecking fixes it. 

- The transition from lightdm to Unity is not as smooth as it has been in the recent past. I get a blackscreen for about 2 seconds or so now.

Regards,
Effenberg

---

### Post by teHIngo on 2012-08-28
Awesomeness. 304.43 *finally* landed by default in Quantal, and everything is working fine here again. Couldn't be any smooter.

Great job and thanks to all involved!

---

### Post by xeizo on 2012-08-28
I upgraded _everything_, removed my locks, and 304.43 do work with 1.13 BUT an earlier problem with xfce reappeared: all apps except Chromium browser lacks a titlebar. It's not only non-visible, there is nothing there. I have to use alt+mouse to move any Windows. Anyone know what this bug is?

---

### Post by effenberg0x0 on 2012-08-28
> **xeizo said:**
> I upgraded _everything_, removed my locks, and 304.43 do work with 1.13 BUT an earlier problem with xfce reappeared: all apps except Chromium browser lacks a titlebar. It's not only non-visible, there is nothing there. I have to use alt+mouse to move any Windows. Anyone know what this bug is?

Hi Xeizo, looks like you have no Window Manager or decorations. If you're using xfce+Compiz, and compiz is not running (as you can check with ps ax | grep -i compiz), run compiz --replace &. If compiz is running is running, maybe you have no decorations enabled. You can fix that in ccsm (Compiz Config Settings Manager): check that you have "Decorations" enabled. If you're not using compiz but metacity or something, restart it via gnome-terminal and check console  output for errors (ex. at gnome-terminal: metacity --replace&).

Maybe the cause could also be no proper nvidia module loaded (check with lsmod | grep -i nv and modinfo <results from previous command>) or nouveau is not blacklisted and loaded (lsmod | grep -i nouveau), and even if neither is loaded and you're running via llvmsomething. If you expect glx in your setup (i.e. you're running compiz in xfce), you can also run /usr/lib/unity-support-test -p from nux-tools package or glxgears -info from mesa-utils package to check for GLX support).

Another possibility I stumble every now and then is /etc/modprobe.d/*. Not only blacklists should be correct but wrong aliases to nvidia-current, nvidia-current-updates, etc can cause weird stuff.

Regards,
Effenberg

---

### Post by xeizo on 2012-08-28
> **effenberg0x0 said:**
> Hi Xeizo, looks like you have no Window Manager or decorations. If you're using xfce+Compiz, and compiz is not running (as you can check with ps ax | grep -i compiz), run compiz --replace &. If compiz is running is running, maybe you have no decorations enabled. You can fix that in ccsm (Compiz Config Settings Manager): check that you have "Decorations" enabled. If you're not using compiz but metacity or something, restart it via gnome-terminal and check console  output for errors (ex. at gnome-terminal: metacity --replace&).

Maybe the cause could also be no proper nvidia module loaded (check with lsmod | grep -i nv and modinfo <results from previous command>) or nouveau is not blacklisted and loaded (lsmod | grep -i nouveau), and even if neither is loaded and you're running via llvmsomething. If you expect glx in your setup (i.e. you're running compiz in xfce), you can also run /usr/lib/unity-support-test -p from nux-tools package or glxgears -info from mesa-utils package to check for GLX support).

Another possibility I stumble every now and then is /etc/modprobe.d/*. Not only blacklists should be correct but wrong aliases to nvidia-current, nvidia-current-updates, etc can cause weird stuff.

Regards,
Effenberg

metacity --replace& brought back Windows decorations, but they're not the Xfce ones but rather Unity-style  ;) So, xfce must be using some other Window-manager ...
GLX works just fine.

edit. oh, and compositing stopped working when I enabled metacity, so bugginess is very present  :D

edit2. on the flip side of things so does Unity 3D work flawless now when Xfce is bugged ....

edit3. but ouch how slow nautilus is compared to Thunar, it's magnitudes slower, but then Thunar is practically motionless compared to gnome-commander ...

---

### Post by pnarciso on 2012-08-28
> **xeizo said:**
> I upgraded _everything_, removed my locks, and 304.43 do work with 1.13 BUT an earlier problem with xfce reappeared: all apps except Chromium browser lacks a titlebar. It's not only non-visible, there is nothing there. I have to use alt+mouse to move any Windows. Anyone know what this bug is?

It's an issue with the Greybird and some other included themes. Change to another working theme and title bars are back.
It's a major issue, considering that Greybird is the major theme, I'm surprised why this wasn't fixed already.

In the meantime I'm testing Ubuntu 12.10 with my Nvidia GTX680 and so far I still get horrible window movement stutter. Major regression compared to 12.04.

---

### Post by xeizo on 2012-08-28
> **pnarciso said:**
> It's an issue with the Greybird and some other included themes. Change to another working theme and title bars are back.
It's a major issue, considering that Greybird is the major theme, I'm surprised why this wasn't fixed already.

In the meantime I'm testing Ubuntu 12.10 with my Nvidia GTX680 and so far I still get horrible window movement stutter. Major regression compared to 12.04.

Thank's, I suspected something like that. Well, just have to run Unity again for a while ;)

My Windows are smooth as butter in Unity 3D, no tearing whatsoever even if I shake the Windows furiously from side to side. And HD-video is perfect. I run a GT430 bios-modded to GT440(GTX680 in the Windows-box).

---

### Post by effenberg0x0 on 2012-08-28
> **pnarciso said:**
> It's an issue with the Greybird and some other included themes. Change to another working theme and title bars are back.
It's a major issue, considering that Greybird is the major theme, I'm surprised why this wasn't fixed already.

In the meantime I'm testing Ubuntu 12.10 with my Nvidia GTX680 and so far I still get horrible window movement stutter. Major regression compared to 12.04.

Pnarciso, try disabling "Sync to Vblank" in compiz-config-settings-manager / OpenGL and nvidia-settings / OpenGL Settings. I see a huge improvement here. You might need to restart the session.

Regards,
Effenberg

---

### Post by pnarciso on 2012-08-28
> **effenberg0x0 said:**
> Pnarciso, try disabling "Sync to Vblank" in compiz-config-settings-manager / OpenGL and nvidia-settings / OpenGL Settings. I see a huge improvement here. You might need to restart the session.

Regards,
Effenberg

The point of using opengl composite is to have proper vsync, if I disable it, there's not much point in using it.

This issue with window movement  is only present in compiz 0.9.8 so it's a performance regression bug that should be fixed.

---

### Post by effenberg0x0 on 2012-08-28
> **pnarciso said:**
> The point of using opengl composite is to have proper vsync, if I disable it, there's not much point in using it.

This issue with window movement  is only present in compiz 0.9.8 so it's a performance regression bug that should be fixed.

I completely agree, I'd fix it immediately if I knew how :)
But, meanwhile, in order to be able to move windows without throwing my mouse/monitors on the wall, I accept to disable Vsync and deal with a little tearing.

Regards,
Effenberg

---

### Post by pnarciso on 2012-08-28
> **effenberg0x0 said:**
> I completely agree, I'd fix it immediately if I knew how :)
But, meanwhile, in order to be able to move windows without throwing my mouse/monitors on the wall, I accept to disable Vsync and deal with a little tearing.

Regards,
Effenberg

In the meanwhile I'm testing Xubuntu along with Ubuntu, and it has been a  solid DE without much bugs (apart the major theme one), and now that they ditched unico engine for gtk3, I can disable composite and not having firefox window content distortion while moving it.

---

### Post by VinDSL on 2012-08-30
Whoa!  nvidia-current 304.43 (official Ubu repo) killed my xserver.

Going back to the edgers version fixed it.  ;)

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.43-0ubuntu1~xedgers~quantal2
  Candidate: 304.43-0ubuntu1
  Version table:
     304.43-0ubuntu1 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
 *** 304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

Caveat emptor...

---

### Post by Harry33 on 2012-08-30
> **VinDSL said:**
> Whoa!  nvidia-current 304.43 (official Ubu repo) killed my xserver.

Going back to the edgers version fixed it.  ;)

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.43-0ubuntu1~xedgers~quantal2
  Candidate: 304.43-0ubuntu1
  Version table:
     304.43-0ubuntu1 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
 *** 304.43-0ubuntu1~xedgers~quantal2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```Caveat emptor...


QQ repos version works well here.
I have installed the QQ repo version of xserver_1.13 rc5 too.
I am also using the QQ repo kernel v. 3.5.3.

---

### Post by VinDSL on 2012-08-30
> **Harry33 said:**
> QQ repos version works well here.
I have installed the QQ repo version of xserver_1.13 rc5 too.
I am also using the QQ repo kernel v. 3.5.3.
Upgraded nvidia-current before the first pot of "black magic".

I'll try it again later, after I've saturated myself with caffeine.

Heh!  Coffee is a lovely drug, isn't it?  :D

---

### Post by Harry33 on 2012-08-31
> **VinDSL said:**
> Upgraded nvidia-current before the first pot of "black magic".

I'll try it again later, after I've saturated myself with caffeine.

Heh!  Coffee is a lovely drug, isn't it?  :D

Indeed it is, fully dark brewed with real cream. ):P

---

