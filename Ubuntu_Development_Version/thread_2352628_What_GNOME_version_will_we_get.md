---
title: "What GNOME version will we get ?"
date: 2017-02-14
forum: Ubuntu Development Version
---

### Post by fthx on 2017-02-14
Hi,

These days, we have installed some pre-3.24 Gnome apps. Will all the apps go for 3.24 or GTK+ will remain 3.22 ? Nautilus and terminal will go for 3.22 ? 3.24 ? remain 3.20 ?
Thanks !

@ jeremy : I noticed that the GDM battery icon is Ubuntu's, not Adwaita's. That's not a big deal !! :-)

---

### Post by dino99 on 2017-02-14
Jeremy is doing the move stuff build tests, to get 3.24 asap; usually nautilus is a step older (i already use 3.22 since a while)

---

### Post by jbicha on 2017-02-16
Ubuntu 17.04 will include GNOME 3.24.

The biggest reason we are able to package the latest GNOME so early is that GTK3 has stabilized. GTK 3.22 is the last series of gtk3. There will be new bugfix releases with 3.22 numbers for several years (like what happened with GTK 2.24). GTK4 development has started (GTK 3.90 is expected to be released in the coming weeks.)

The other reason is that I happened to have time to work on these updates. There's no guarantee that this will happen for future releases. For LTS releases, we will likely target the previous stable release like we've done for years. So although it's early, I am guessing that 18.04 LTS will use GNOME 3.26.

GNOME will keep its current numbering system until they do another major UI overhaul or get tired of the 3.* numbers. There's no requirement that GTK and GNOME version numbers match. GNOME 3.28 will probably look very similar to GNOME 3.22 even if 3.28 uses GTK4.

I think some of your other questions are briefly answered in the [Release Notes]("https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes/UbuntuGNOME#Highlights").

> **fthx said:**
> I noticed that the GDM battery icon is Ubuntu's, not Adwaita's.

We've had that bug for years!

---

### Post by fthx on 2017-02-16
Ok thanks ! and re-thanks for the wiki update ;-)

---

### Post by fthx on 2017-02-16
Do I need to fill a bug report for this ? (v. 3.23.90)
The start of the week is monday in France and by the way it's thursday March 9, not 10. There is no error in the month view.
[[IMG]http://img11.hostingpics.net/pics/678368Capturedcrande20170216135358.png[/IMG]](http://www.hostingpics.net/viewer.php?id=678368Capturedcrande20170216135358.png)

---

### Post by jbicha on 2017-02-16
Could you file that gnome-calendar bug [upstream]("https://wiki.ubuntu.com/Bugs/Upstream/GNOME") against GNOME?

---

### Post by fthx on 2017-02-16
1) This bug seems already filled :
[https://bugzilla.gnome.org/show_bug.cgi?id=777762](https://bugzilla.gnome.org/show_bug.cgi?id=777762)
By the way, it seems that calendar (and especially week view) needs to become more stable.

2) The new localization icon seems to mean "activated" when I choose loc. to be OFF. Is that intended or is this a (small) bug ?

3) Thunderbird (as in 16.10, at least) does not display new email notifications in Gnome Shell. I know that the Gnotifier extension can do this job but is there any plan to make that native in Ubuntu ?

---

### Post by jbicha on 2017-02-16
1. Thanks!
2. Could you report that?
3. I don't know anything about that. I assume that Evolution has better GNOME integration than Thunderbird.

---

### Post by fthx on 2017-02-20
Ok, sorry for the lag, I was busy and waiting for your upload of some 3.24 packages.

So, tell me if I need to report against Gnome these bugs :
- sometimes no Nautilus icons on desktop followed by some random brutal logouts (maybe solved by latest uploads ? I don't experience this bug today) ;
- the localization icon remains even if deactivated ;
- the padding of this localization icon is not consistent with others in system bar ;
- no icon for night light in system menu (I believe to have read that it should appear in 3.24) ;
- the night light "disable until tomorrow" is not adapted to my use (simply activate/deactivate with one menu action), it could be simply "disable/resume" ;
- no icon for night light in system bar ;
- no access (Chrome, Firefox) to the list of all extensions on [https://extensions.gnome.org/](https://extensions.gnome.org/) (disabling "compatible with current version" works) ;
- Epiphany does not detect Gnome's version on this website [https://extensions.gnome.org/](https://extensions.gnome.org/) ;
- chrome-gnome-shell crashes on Chrome exit.

If it's unclear, I'll check that in Gnome's bugzilla.

---

### Post by jbicha on 2017-02-20
fthx, yes, please do file bugs for those. Here's a few already known:

[LIST]
[*]The  missing Night Light icon in GNOME's system menu is because there hasn't  been a release of adwaita-icon-theme with those icons yet but those icons are in the git repo. 
[*]extensions.gnome.org not ignoring the extension version like gnome-shell 3.22+ does by default is [bug 776460]("https://bugzilla.gnome.org/776460") 
[/LIST]

Which version of Nautilus are you using?

---

### Post by fthx on 2017-02-20
Ok I'll report that.

I use the Ubuntu's 3.20.3 Nautilus version. But I do not get missing icons or savage logout today. So...

---

### Post by fthx on 2017-02-21
Ok, the logout bug still happens :
> Unrecoverable failure in required component org.gnome.SettingsDaemon.Sharing.desktop
followed by the well known :
> CRITICAL: We failed, but the fail whale is dead. Sorry....

It's easy to know if this logout will happen : when my desktop has icons, it's ok, when it get no icons at startup, it will disconnect.

---

### Post by harry332 on 2017-02-21
I am also experiencing the logout bug.
It has been around for nearly two weeks now.
I do not have any desktop icons on my desktop.
The brutal logout happens like every third or fourth logging (Gnome-Shell).
I have also found that the logout is connected to the logging where there is no shut down or logout menu in Gnome-Shell.
So, if that menu is missing (in the upper right corner of the Gnome-Shell), the logout will soon happen.

---

### Post by dino99 on 2017-02-22
The pcre2/3 for a place into "main" struggle will probably lock nautilus/terminal again. The "main" rules are so strict that transitioning is a nightmare, as the team is also not allowing dependencies  not in "main" (recursive self biting loop ](*,) )
Anyway nautilus & terminal with pcre3 are working as expected (gnome3-staging ppa)

---

### Post by fthx on 2017-02-23
I do not see anymore the Wayland session in GDM menu ?

---

### Post by fthx on 2017-03-03
The start of the week in Gnome Calendar's week view has been solved in 3.23.91.

---

### Post by fthx on 2017-03-08
> **jbicha said:**
> 
[LIST]
[*]extensions.gnome.org not ignoring the extension version like gnome-shell 3.22+ does by default is [bug 776460]("https://bugzilla.gnome.org/776460") 
[/LIST]


How can I do to install/update extensions at the moment ?
The above bug is still open and I cannot see any way to install extensions via Gnome Software.

I'm sure I missed something as you updated recently the chrome-gnome-shell connector.

---

### Post by dino99 on 2017-03-08
goto extensions.gnome.org page, and choose what you wish :p
(nothing listed by default, you have to switch to 'all versions' instead of 'current' )

---

### Post by fthx on 2017-03-08
Tss tss tss :biggrin: you can *display* extensions, that I know, but I cannot install one of them.

---

### Post by jbicha on 2017-03-10
> **fthx said:**
> I cannot see any way to install extensions via Gnome Software.

That's bug [1671612]("https://launchpad.net//bugs/1671612")

---

### Post by fthx on 2017-03-16
Some remaining tiny bugs :
- when I install lightdm and remove lightdm, GDM does not appear on next login (reinstalling it does the trick) ;
- logout window does not have focus and consequently  I have to click twice to do something here ;
- Synaptic does not work when running a Wayland session ;
- suspend does not work (laptop lid closed or gnome menu), it goes for a session lock from which I can return only pressing power button (lightdm or gdm, no matter) :
> [  725.411062] ACPI : button: The lid device is not compliant to SW_LID.
[  728.336994] PM: Syncing filesystems ... done.
[  728.343195] PM: Preparing system for sleep (freeze)
[  728.344662] Freezing user space processes ... (elapsed 0.003 seconds) done.
[  728.347850] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  728.349292] PM: Suspending system (freeze)
[  728.349294] Suspending console(s) (use no_console_suspend to debug)
[  728.349842] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[  728.353881] sd 3:0:0:0: [sda] Stopping disk
[  728.394235] e1000e: EEE TX LPI TIMER: 00000011
[  728.394396] ACPI : EC: event blocked
[  728.610243] PM: suspend of devices complete after 260.634 msecs
[  728.629802] PM: late suspend of devices complete after 19.554 msecs
[  728.634710] ACPI : EC: interrupt blocked
[  728.636030] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  728.785851] PM: noirq suspend of devices complete after 151.947 msecs
[  728.785856] PM: suspend-to-idle
[  732.513096] Suspended for 3.061 seconds
[  737.782848] Suspended for 4.999 seconds
[  745.608474] Suspended for 7.999 seconds
[  747.162696] Suspended for 1.999 seconds
[  748.505905] Suspended for 0.999 seconds
[  748.505954] PM: resume from suspend-to-idle
[  748.506314] ACPI : EC: interrupt unblocked
[  748.525194] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  748.869373] PM: noirq resume of devices complete after 363.321 msecs
[  748.874165] PM: early resume of devices complete after 1.056 msecs
[  748.874576] ACPI : EC: event unblocked
[  748.878890] rtc_cmos 00:02: System wakeup disabled by ACPI
[  748.881824] [drm] GuC firmware load skipped
[  748.884783] sd 3:0:0:0: [sda] Starting disk
[  749.124500] PM: resume of devices complete after 250.314 msecs
[  749.125060] PM: Finishing wakeup.
[  749.125061] Restarting tasks ... 
[  749.128893] [drm] RC6 on



Will GTK+ be upgraded from 3.22.7 or is it freezed ?

---

### Post by jbicha on 2017-03-16
I think you're aware that gtk3 is stable now and future gtk3 releases will be in the 3.22 series. We will upload gtk3 3.22.10 to zesty once ubuntu-app-launch no longer depends on upstart. (That's being worked on.)

---

### Post by jbicha on 2017-03-16
synaptic needs [more work]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=818366") to be used on Wayland.

---

### Post by fthx on 2017-03-16
> **jbicha said:**
> We will upload gtk3 3.22.10 to zesty once ubuntu-app-launch no longer depends on upstart. (That's being worked on.)

synaptic needs [more work]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=818366") to be used on Wayland.

ok thanks !

---

### Post by fthx on 2017-03-17
never mind for sleep issue, S3 state was blocked in bios...
It works now (X, Wayland).

Almost everything is perfect now (in my case !). No more session disconnections.
When Xorg 1.19 will land, we will get the choice of GPU to use (switch. graph.)  with right-click on an app icon ?

In another thread you remind me the Gnome staging ppa to get Nautilus 3.24 ; I installed it and it seems to work very well and I get icons on Wayland Gnome's desktop. GOOD.

---

### Post by jbicha on 2017-03-17
> **fthx said:**
> 
When Xorg 1.19 will land, we will get the choice of GPU to use (switch. graph.)  with right-click on an app icon ?


Install switcheroo-control for this GNOME Shell 3.24 [feature]("http://www.hadess.net/2016/10/dual-gpu-integration-in-gnome.html"). Ubuntu GNOME will install it by default (hopefully for 17.04), but it's not been accepted into Ubuntu yet. It is in the GNOME3 Staging PPA though.

I wish I had known months ago that piece was needed so it could have been accepted sooner!

The funny name is because it's a control for the Linux kernel interface which is named switcheroo.

---

### Post by fthx on 2017-03-18
I still run Xorg 1.18.
I switched from proprietary Nvidia to nouveau and I get this feature in right-click-on-app menu.

I tried to run it in Wayland but... There's something I do not understand : why Wayland session is not available with nouveau ? it is available with Nvidia proprietary.

---

### Post by jbicha on 2017-03-18
@fthx, what's the output of 
```
glxinfo | grep renderer
```

---

### Post by fthx on 2017-03-19
> [SIZE=3][FONT=courier new]GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics P530 (Skylake GT2) 
[/FONT][/SIZE]

Additionnally, is the dGPU usage from app right-click supposed to work with Xorg 1.18 too ?

---

### Post by jbicha on 2017-03-19
@fthx, please report a GNOME bug (against gnome-session I think) since I don't know what's going on there.

Yes, zesty's X should be new enough.

What does GNOME Settings>Details say is your graphics when you are using nouveau?

---

### Post by fthx on 2017-03-21
(I've not the time to investigate more Waymand stuff at the moment.)

GS Extensions website works if the extension is installed from the website itself. Don't know what was wrong with the extension that I installed before.
Still no extensions in Gnome Software, though.

---

### Post by pebcak2 on 2017-03-21
> **fthx said:**
> I do not see anymore the Wayland session in GDM menu ?

Me too. It was there prior to updating to 17.04.

---

### Post by jbicha on 2017-03-21
> **pebcak2 said:**
> Me too. It was there prior to updating to 17.04.

Please report that bug against gnome-session.

---

