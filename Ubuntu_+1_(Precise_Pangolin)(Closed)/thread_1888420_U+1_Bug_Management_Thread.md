---
title: "U+1 Bug Management Thread"
date: 2011-11-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2011-11-28
Moderated Thread.
> **INTRODUCTION**

This sticky thread was created and is maintained by the group of testers of the Ubuntu Development Version area (Ubuntu+1) of this forum.

Our goal is to find, study, report and keep track of bugs that affect the current development version of Ubuntu and it's flavors (such as Lubuntu).

**TARGETS**

The target-audiences for this content are:

[LIST]
[*]Developers: Will hopefully find usable and summarized info here to ease and speed up their work.
[*]Bug Triagers: Can use this content to help in triaging / validating / merging open Launchpad bugs.
[*]Helpers: Will learn of current bugs and workarounds, thus being to provide better help for users in other forum sections.
[/LIST]

**BUG REPORTS**

The following fields of information will be used. A bug reporter can choose to not fill all fields, according to bug characteristics, his own perception, limitations on current information.

[LIST=1]
[*]Bug Short Description:
[*]How to Reproduce the bug:
[*]Current behavior:
[*]Attachments: (image, code, files that can contribute to understanding the bug, if any);
[*]Platform tested: (Ubuntu flavor, related software / package versions, hardware involved, if relevant);
[*]Workaround: (only if known by the poster. Full workaround in CODE (for code) or QUOTE (for other procedures) tags. Not a long tutorial targeted at users. A working/usable fix. No external link to workarounds unless really needed (download of package, etc), so one can rapidly learn how to solve the problem when reading this sticky;
[*]Link to Discussion Thread: (if it exists. Full U+1 link, so we can easily click it to open);
[*]Link to Bug Report: (full launchpad link, so we can easily click to open it);
[*]Bug Report Status: (will fix, will not fix, if the status is known and there is a Launchpad report);
[*]Bug status: (Fixed, Not Fixed, if the status is known and there is a Launchpad report).
[/LIST]
**Attention Bug Reporter: Not all fields are required! Do the best you can. We as a group will try to work on each report to make it as precise as possible.**

**RULES**

[LIST=1]
[*]Only one bug should be report per post.
[*]Even if kept blank, all fields must be respected and kept in order. Just cut & paste the above model when reporting;
[*]Partial, confusing reports, will be checked by us, and re-reported in proper way if valid;
[*]Descriptions must be as succinct, technical and direct as possible. Remember we are trying to make life easier for developers, triagers, etc;
[*]No unrelated post of any kind. One can start a normal thread in this forum section to discuss other issues or comment on the reported bugs. Help us keep this thread as clean as possible;
[*]If a bug report is posted by someone (tester or not) and no one can reproduce the bug (e.g. the report is wrong) the bug report will be deleted;
[*]Use common-sense.
[/LIST]

**If you are not sure about how to use this thread and need more information in order to post a bug, please start a normal thread here with a descriptive title, such as [BUG] Testing needed.**

---

### Post by ronacc on 2011-11-29
1 notification when mounting internal hard drive with nautilus .
2 mount a hard drive that is not in fstab .
3 displays notification asking what to do even though it is already open in nautilus .
4 see attached image .
5 Ubuntu 12.04 with Gnome-shell ( does not happen in unity )
6 disable prompting in system settings>removeable media
7 [http://ubuntuforums.org/showthread.php?t=1884141](http://ubuntuforums.org/showthread.php?t=1884141)
8 [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/893730](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/893730)
9 none yet
10 confirmed

if I screwed this up let me know and I'll edit it .

---

### Post by effenberg0x0 on 2011-11-29
**1.Bug Short Description:** Inability to use VDPAU acceleration on some nvidia driver installs
**2.How to Reproduce the bug:** Run /usr/bin/vdpauinfo after clean install of PP and NVidia proprietary / open driver 290.10.
**3. Current behavior:** "Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file."
**4. Attachments:**
**5. Platform tested:** Ubuntu PP, NVIDIA-Linux-x86_64-290.10.run
**6. Workaround:** sudo ln -s /usr/lib/vdpau/libvdpau_nvidia.so.290.10 /usr/lib/libvdpau_nvidia.so
**7. Link to Discussion Thread:**
**8. Link to Bug Report:** [https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/510390](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/510390)
**9. Bug Report Status:** Fix Released
**10. Bug status:** Not Fixed

---

### Post by effenberg0x0 on 2011-11-29
**1.Bug Short Description:** Absence of a GUI way to customize mouse pointer size
**2.How to Reproduce the bug:** Check the absence of this option in gnome-control-center 
**3. Current behavior:** No customization of mouse cursor size impacts OS use by the visually impaired
**4. Attachments:**
**5. Platform tested:** Ubuntu PP
**6 Workaround: **No definitive / user-friendly one found.
**7. Link to Discussion Thread:**
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/786325](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/786325)
**9. Bug Report Status:** Triaged
**10. Bug status:** Not Fixed

---

### Post by ventrical on 2011-11-29
**1.Bug Short Description**:Gedit  is not working properly. When clicked upon on the Unity 2D desktop it will then show up on the Unity launcher, wobble and then disappear - hence as which led to this bug report from apport. Also system monitor, when open, will take 3 to 4 second delay before closing on both Unity 2D, and 3D, with  both ATi and nVidia drivers.3.2.0-1-generic #1-Ubuntu SMP Fri Nov 18 20:52:58 UTC 2011 i686 i686 i386 GNU/Linux
**2.How to Reproduce the bug:** Log into Unity 2D, left click Gedit Icon real quick on desktop.
**3.Current Behavior:** Causes intermittent crashes.
**4.Attatchments: **[http://www.youtube.com/watch?v=FvNt6Mpd_0Q](http://www.youtube.com/watch?v=FvNt6Mpd_0Q)
**5.Platform Tested: **Ubuntu PP
**6.Workaround:** Click icon second time and Gedit will open.
**8.Link to Bug Report: **[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/897900](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/897900)
**9.Bug Report Status:**Duplicate

---

### Post by scradock on 2011-11-30
1.Bug Short Description:Update-manager does not run correctly. Unusable.
2.How to Reproduce the bug: Open Update manager; click on "Check" button
3.Current Behavior: endless circulating "wait" cursor; no progress.
4.Attachments: 
5.Platform Tested: Ubuntu PP fully updated, including U-M 1:0.154.5
6.Workaround: need to log-out to end program, and use Synaptic instead.
8.Link to Bug Report: none as yet
9.Bug Report Status:

---

### Post by effenberg0x0 on 2011-12-01
**1.Bug Short Description:** Gedit unexpectedly exits
**2.How to Reproduce the bug:** Seems to happen more often when File/Open/Browsing through folders / network shares
**3. Current behavior:** Launching Gedit via console one can see this when the crash happens: [I](gedit:2680): GLib-CRITICAL **: g_main_loop_quit: assertion `g_atomic_int_get (&loop->ref_count) > 0' failed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.[/I]
**4. Attachments: **
**5. Platform tested:** Ubuntu PP Alpha
**6 Workaround: **Unknown
**7. Link to Discussion Thread:** 
**8. Link to Bug Report:** 
**9. Bug Report Status:** 
**10. Bug status:**

---

### Post by pbhedlund on 2011-12-01
[LIST=1]
[*]Bug Short Description: Distorted display on MacBook Air 3,2
[*]How to Reproduce the bug: Boot computer
[*]Current behavior: The internal display shows the desktop but it is distorted by vertical colored bands separated by black and white noise. This is a regression since Oneiric.
[*]Attachments: None
[*]Platform tested: Precise Alpha 1 64 bit live session, Macbook Air 3,2 Nvidia 320M
[*]Workaround: None known
[*]Link to Discussion Thread: N/A
[*]Link to Bug Report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784)
[*]Bug Report Status: New
[*]Bug status: Undecided
[/LIST]

---

### Post by cariboo on 2011-12-01
[LIST=1]
[*]**Bug Short Description**: gnome-activity-journal crashed with DBusException
[*]**How to Reproduce the bug**: Start gnome-activty-journal from the dash
[*]**Current behavior**: Doesn't start
[*]**Attachments**: Terminal output
[*]**Workaround**: none yet
[*]**Link to Discussion Thread**: Haven't started one yet :)
[*]**Link to Bug Report**: Bug #[lpbug]898903[/lpbug]
[*]**Bug Report Status**: Confirmed
[*]**Bug status**: waiting for update from launchpad
[/LIST]

---

### Post by kaldor on 2011-12-02
**Bug Short Description:** Volume slider misleading and broken on Alpha 1. Was working fine on daily build from ~5 days prior. Sound quality has deteriorated along with it (probably same issue), as it becomes too muffled when the sound is at a comfortable level.

**How to Reproduce the bug:** Boot an Alpha 1 live USB and try to play audio.

**Current behavior:** Sound is inaudible until it is at least halfway on the slider. Slider needs to be at least 80% to the right to listen at an okay (but still low) level. Any farther than that and it goes into a muffled mess of a sonic boom (WAY too loud!). On the previous daily build I tried (under a week ago), everything worked 100% perfectly. The current issue makes listening to *anything* a pain.

**Attachments:** N/A

**Platform tested:** Ubuntu 12.04 Alpha 1 x86_64 on a 4 GB live USB session.

**Workaround:** Unknown.

**Link to Discussion Thread:** N/A

**Link to Bug Report:** [_Click_]("https://bugs.launchpad.net/ubuntu/+bug/898961").

**Bug Report Status:** New

**Bug status:** Just discovered it.

---

### Post by WarriorIng64 on 2011-12-02
**1. Bug Short Description:** Install Updates button in Update Manager does not install updates
**2. How to Reproduce the bug:** Open the Update Manager when there are updates available to apply (may have to use the Check button or ```
sudo apt-get update
``` beforehand), and click Install Updates.
**3. Current behavior:** The Update Manager window will gray out and become unresponsive for a few minutes, with the mouse cursor turning into a "busy" icon when held over it. Afterwards, the window will become colored and responsive again, but will still show all updates as waiting to be applied.
**4. Attachments:** n/a
**5. Platform tested:** Ubuntu 12.04 amd64, pre-alpha and Alpha 1; update-manager 1:0.154.6
**6. Workaround:** Open a terminal and run ```
sudo apt-get upgrade
``` to apply any updates (after checking for them using one of the above methods in **2**).
**7. Link to Discussion Thread:** [http://ubuntuforums.org/showpost.php?p=11505741&postcount=22](http://ubuntuforums.org/showpost.php?p=11505741&postcount=22)
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898807](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898807)
**9. Bug Report Status:** [COLOR=SeaGreen]Fix Released[/COLOR], marked as duplicate (see [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/894671](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/894671))
**10. Bug status:** [COLOR=SeaGreen]Fixed[/COLOR]

---

### Post by WarriorIng64 on 2011-12-02
**1. Bug Short Description:** Cannot install/remove software via the Ubuntu Software Center
**2. How to Reproduce the bug:** Open the Ubuntu Software Center, and do one of the following:[INDENT]1. Find a piece of software that is not already installed, and click the Install button.
2. Find a piece of software that is already installed, and click the Remove button.
[/INDENT]**3. Current behavior:** The button clicked will gray out and become inactive for a few minutes; nothing else occurs. Afterwards, it will become active again and still show what it showed previously, and the software will not be installed/removed.
**4. Attachments:** n/a
**5. Platform tested:** Ubuntu 12.04 amd64, pre-alpha and Alpha 1; software-center 5.1.2.1 through 5.1.3
**6. Workaround:** Open a terminal and run ```
sudo apt-get install <package name>
``` to manually install software, or ```
sudo apt-get remove <package name>
``` to manually remove software.
**7. Link to Discussion Thread:** [http://ubuntuforums.org/showpost.php...1&postcount=22]("http://ubuntuforums.org/showpost.php?p=11505741&postcount=22")
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/897984](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/897984)
**9. Bug Report Status:** [COLOR=SeaGreen]Fix Released[/COLOR] (marked as duplicate, see [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745))
**10. Bug status:** [COLOR=SeaGreen]Fixed[/COLOR]

---

### Post by ronacc on 2011-12-02
1.Bug Short Description: dkms (jockey) trys to install the wrong driver for some nvidia cards
2.How to Reproduce the bug: install from a daily or wait for a kernel update .
3. Current behavior: message saying "nvidia 173.xxx driver failed to install"
4. Attachments:
5. Platform tested: ubuntu 12.04 AMD 64 / nvidia 7600gs
6. Workaround: install nvidia-current if it is working or hand install 290.10 from nvidia 
7. Link to Discussion Thread:
8. Link to Bug Report: [ https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/897681 ]( https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/897681 )
9. Bug Report Status: confirmed
10. Bug status: not fixed

---

### Post by WarriorIng64 on 2011-12-03
**1. Bug Short Description:** Alt+Tab app switcher shows black rectangles for window previews while workspace switcher is active
**2. How to Reproduce the bug:**[INDENT]1. Enter the workspace switcher (Super + S or click the launcher shortcut) with some windows open.
2. Enter Alt+Tab while in it.
3. Press the down arrow key or wait for the window preview(s) to appear.
[/INDENT]**3. Current behavior:** The window previews will be replaced by solid black rectangles instead of showing the windows.
**4. Attachments:** n/a
**5. Platform tested:** Ubuntu 12.04 amd64, pre-alpha and Alpha 1 and Ubuntu 11.10 on my custom-built desktop with integrated NVIDIA graphics and the Nouveau driver; Ubuntu 11.10 on a Toshiba Satellite A505-S6960 laptop
**6. Workaround:** Only use Alt+Tab when the workspace switcher is not open.
**7. Link to Discussion Thread:** n/a
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/899762](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/899762)
**9. Bug Report Status:** Triaged
**10. Bug status:** Not Fixed

---

### Post by kaldor on 2011-12-04
**Bug Short Description:** Poor performance with open source Radeon driver. 

**How to Reproduce the bug:** Boot an Alpha 1 live USB. Move windows, try scrolling (wheel or bar work the same), select appmenu items and hover over the different options, drag desktop icons, etc. Desktop is delayed and jerky when I do any of these things.

**Current behavior:** The DE is too jerky on my Radeon HD 6450 card. Delays in movement of items (unity launcher, desktop icons), choppy scrolling, windows stutter when dragged. Even when I highlight text I find that the highlight effect races to catch up to my cursor. Videos and 3d works as expected on this driver, but the desktop is not smooth at all. Aside from a low-end graphics card, I have modern specs (6 core processor and 8 GB of RAM), so system requirements are fine. 

**Attachments:** N/A

**Platform tested:** Ubuntu 12.04 Alpha 1 x86_64 on a 4 GB live USB session.

**Workaround:** Possible workaround [_here_]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707/comments/14").

**Link to Discussion Thread:** [http://ubuntuforums.org/showthread.php?t=1885172](http://ubuntuforums.org/showthread.php?t=1885172)

**Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/898963](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/898963)

**Bug Report Status:** New

**Bug status:** Still an issue.

---

### Post by WarriorIng64 on 2011-12-04
**1. Bug Short Description:** Dragging icons from the dash to the launcher is slow and laggy
**2. How to Reproduce the bug:**[INDENT]1. Open the dash and in the Applications Lens find a program that is not already pinned to the launcher.
2. Drag the application's icon to the launcher to pin it there.
[/INDENT]**3. Current behavior:** Lag will occur, with the icon trailing behind the mouse cursor in a jerky fashion. Re-ordering icons within the launcher is similarly affected, to a lesser extent.
**4. Attachments:** [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/900034/+attachment/2619625/+files/out.ogv](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/900034/+attachment/2619625/+files/out.ogv)
**5. Platform tested:** Ubuntu 12.04 amd64 Alpha 1 on my custom-built desktop with integrated NVIDIA graphics  and the Nouveau driver
**6. Workaround:** Open the application first then pin it using the right-click menu, when you would otherwise drag a new icon from the dash. There is no workaround for re-ordering icons that are already in the launcher.
**7. Link to Discussion Thread:** [http://ubuntuforums.org/showpost.php?p=11511384&postcount=45](http://ubuntuforums.org/showpost.php?p=11511384&postcount=45)
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/900034](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/900034)
**9. Bug Report Status:** Duplicate (see [https://bugs.launchpad.net/unity/+bug/851172](https://bugs.launchpad.net/unity/+bug/851172)); [COLOR=Green]Fix Released[/COLOR]
**10. Bug status:** [COLOR=Green](Mostly) Fixed[COLOR=Black] with Unity 5.0[/COLOR]
[/COLOR]

---

### Post by cariboo on 2011-12-21
1. **Bug Short Description:** Intel Atom + 945 video chipset kernel panics
2. **How to Reproduce the bug:** Boot into the Unity desktop, wait less than a minute for kernel to panic
3.** Current behavior:** Kernel panics after less than a minute running Unity
4. **Attachments:** apport.linux-image-3.2.0-5-generic.ui00Jv.apport.tar.gz 
5. **Platform tested:** Precise running Unity desktop on an Atom 270 + Intel 945 graphics chipset
6. **Workaround: ** None
7. **Link to Discussion Thread:** [http://ubuntuforums.org/showthread.php?t=1896087&highlight=Atom](http://ubuntuforums.org/showthread.php?t=1896087&highlight=Atom)
8. **Link to Bug Report: ** Bug #[lpbug]905606[/lpbug]
9. **Bug Report Status:** Confirmed
10. **Bug status:** Not Fixed

---

### Post by uid313 on 2012-01-12
**Bug Short Description:** Screenshot does not work.

**How to Reproduce the bug:** Run 'gnome-screenshot' or open Screenshot from the menu.

**Current behavior:** It takes screenshot of the login screen instead of desktop.

**Attachments:** N/A

**Platform tested:** Ubuntu 12.04 Alpha 1 x86_64 on VirtualBox.

**Workaround:** Unknown.

**Link to Discussion Thread:** N/A

**Link to Bug Report:** N/A ?

**Bug Report Status:** Oops, this is bug in egtk theme.

**Bug status:** Just discovered it.

---

### Post by uid313 on 2012-01-12
**Bug Short Description:** Menus in gnome-panel have this annoying scroll at top and bottom of the menu.

**How to Reproduce the bug:** Install 'gnome-session-fallback' and select GNOME Classic at the login screen. Click on any of the Applications, Places or user-menu.

**Current behavior:** Menu have scroll thing at top and bottom of menu.

**Attachments:** N/A

**Platform tested:** Ubuntu 12.04 Alpha 1 x86_64 on VirtualBox.

**Workaround:** Unknown.

**Link to Discussion Thread:** N/A

**Link to Bug Report:** N/A ?

**Bug Report Status:** ?

**Bug status:** Wasn't initially like this in 12.04, it became like this after an update.

---

### Post by dankegel on 2012-01-16
Bug Short Description: networking flaky
How to Reproduce the bug: install, then do full update, and try to use firefox or install nvidia drivers
Current behavior: network not usable enough to file bug reports
Attachments:
Platform tested: 12.04 alpha 1 64 bit after update
Workaround: 
Link to Discussion Thread: 
Link to Bug Report: [https://bugs.launchpad.net/ubuntu/+bug/917399](https://bugs.launchpad.net/ubuntu/+bug/917399)
Bug Report Status: Undecided
Bug status: New

---

### Post by dankegel on 2012-01-16
Bug Short Description: Atheros AR9285 wireless doesn't work in Ubuntu 12.04 alpha 1
How to Reproduce the bug: install, optionally do full update, then try to connect via wireless
Current behavior: no networks visible
Attachments:
Platform tested: 12.04 alpha 1 64 bit after update, with AR9285 wifi chip
Workaround: 
Link to Discussion Thread: 
Link to Bug Report: [https://bugs.launchpad.net/ubuntu/+bug/917402](https://bugs.launchpad.net/ubuntu/+bug/917402)
Bug Report Status: Undecided
Bug status: New

Note: the installer had no problem with wireless; only after installation was it broken.

---

### Post by quequotion on 2012-02-14
**Bug Short Description:** root on RAID:0 fails to boot (again)
How to Reproduce the bug: Upgrade from Oneiric to Precise, observe that pc fails to boot.
**Current behavior:** Boot drops to busybox when attempting to boot from (fake)RAID:0
**Attachments:**
**Platform tested:** 12.04 upgraded from 11.10 by editing **/etc/apt/sources.list** and "**sudo apt-get dist-upgrade**"
**Workaround:** In busybox, "**dmraid -ay**" to activate the raid then "**exit**" to continue booting.
**Link to Discussion Thread:**
**Link to Bug Report:**[bug/931929]("https://bugs.launchpad.net/initramfs-tools/+bug/931929")
**Bug Report Status:** Undecided & Unassigned
**Bug status:** New

---

### Post by ranch hand on 2012-02-16
**Bug Short Description:cups and other cups packages throw a dpkg code 1 error when upgraded in a chroot environment**[B]
[/B][B]Platform tested:clean install of Xubuntu 12.04-testing
[/B]**Workaround:run "dpkg --configure -a when booted to Xubuntu**
**Link to Bug Report:**[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/933973](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/933973)
**Bug status:Brand spanking new.**

---

### Post by williejones on 2012-02-18
**1.Bug Short Description:** Emachine E725 boots to a black screen.
[B]2.How to Reproduce the bug: 
[/B]**3. Current behavior: **When booting up the screen is black. I can shine a flashlight on the screen and barely see the login prompt. Log in works as I can hear the startup sound. Again a flashlight shows a dim logged in screen.  The function + brightness does nothing
[B]4. Attachments:
[/B]**5. Platform tested:** Ubuntu PP 64 bit
**6. Workaround: **Edit Grub with acpi_osi=Linux.  The function + bright, dim keys work in reverse (dim key brightens screen, brighter key dims screen)
**7. Link to Discussion Thread:**
**8. Link to Bug Report: **[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/934707](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/934707)
**9. Bug Report Status: **Confirmed
**10. Bug status:** High

---

### Post by dankegel on 2012-02-21
**Bug Short Description:** regression: hard to resize windows
**How to Reproduce the bug:** try resizing terminal window by dragging lower right hand corner
**Current behavior:** sweet spot is nice and wide but is only one or two pixels high.
**Expected behavior:** sweet spot should be several (five) pixels high
**Workaround:** none
**Link to Discussion Thread:**
**Link to Bug Report:**[bug/933198]("https://bugs.launchpad.net/bugs/933198")
**Bug Report Status:** Undecided & Unassigned
**Bug status:** New

---

### Post by bryanl on 2012-03-13
Setting laptop external monitor to 1920x1200 freezes system

An Acer i3 M 370 CPU with a Samsung 1980x1200 monitor connected via HDMI

VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Display settings, move to maximum on the Samsung, Apply, screen blanks except mouse point, which is frozen. System unresponsive and have to power down to get system back.

It was working on one of the earlier alpha's but, since a few weeks ago, it's a no-go. It does function at lower resolutions currently in 12.04.

System does OK with maverick (which also does fax on the all-in-one HP which later versions don't seem to do- but that's another problem)

---

### Post by grahammechanical on 2012-03-14
[LIST=1]
[*]**Bug Short Description:** Xchat-gnome uses 100% CPU when the Network>Channels combi-box is opened when on irc channel #ubuntu-uk. Xchat-gnome becomes unusable and a forced quit is required. This does not happen if the Network>Channels combi-box is opened when on irc channel freenode.
[*]**How to Reproduce the bug:** Run Xchat-gnome. allow it to establish connection to #ubuntu-uk channel and try to join another channel such as #U+1 or #ubuntuforums. Then force close and try again but this time after a connection is made to #ubuntu-uk channel, switch to #freenode channel and go to Network>Channels and the combi-box will open and you can join another channel.
[*]**Current behavior:** This behavior does not happen on my 12.04 install that has been upgraded from  an 11.10 install in November and has been updated daily. It is happening on a default install from the 12.04 Beat 1 ISO image.
[*]**Attachments:** I need to research what reports are useful and how to create them.
[*]**Platform tested:** Ubuntu 12.04 Beta 1 Precise Pangolin installed from the recently released Beta 1 ISO image. This install is a default,  unmodified install for the purpose of testing this Beta 1 image.
[*]**Workaround:** (only if known by the poster. Full workaround in CODE  (for code) or QUOTE (for other procedures) tags. Not a long tutorial  targeted at users. A working/usable fix. No external link to workarounds  unless really needed (download of package, etc), so one can rapidly  learn how to solve the problem when reading this sticky;
[*]**Link to Discussion Thread:** (if it exists. Full U+1 link, so we can easily click it to open);
[*]**Link to Bug Report:** Yet to find if has been reported. Will update.
[*]**Bug Report Status:** (will fix, will not fix, if the status is known and there is a Launchpad report);
[*]**Bug status:** (Fixed, Not Fixed, if the status is known and there is a Launchpad report).
[/LIST]

---

### Post by meanpt on 2012-03-15
[LIST=1]
[*]Firefox closes by itself and unity (both 2d and 3d) freezes; system menu only shows user accounts; the desktop starts freezing and no action occurs when clicking the icons
[*]browsing the net for some time
[*]Current behavior: as described in 1
[*]Attachments: none
[*]Platform tested: 12.04 beta1, both 32b and 64 bits, installed in an external 500 GB external hard drive
[*]Workaround: none
[*]Link to Discussion Thread: none
[*]Link to Bug Report: no crash report is produced and hence no bug report is made
[*]Bug Report Status: not applicable
[*]Bug status: not applicable.
[/LIST]

---

### Post by WarriorIng64 on 2012-03-19
[LIST=1]
[*]**Bug Short Description:** Cannot install MP3 playback support from the Ubuntu One Music Store
[*]**How to Reproduce the bug:** 1) Open Rhythmbox (12.04) or Banshee (11.10) and select the Ubuntu One Music Store.
2) The top of the window will say "MP3 playback support is not  available. It must be installed to play Previews and Purchased Music on  this computer." A button marked "Install" is provided after that  message; click it.
3) Accept the "MPEG Layer-3 audio decoding technology notice" dialog that comes up.
4) A dialog asking for authentication to change software repository settings will come up. Provide your password.
5) A progress bar will appear in Rhythmbox/Banshee. Another dialog asking for  authentication to install or remove software will come up. Provide your  password.
6) The progress bar and notice will now disappear.
[*]**Current behavior:** Installation silently fails; no error messages are given, even when  running from a terminal. Previews will not play and you can't play any  MP3 files you have. If Rhythmbox/Banshee is closed and reopened, the notice and  install button from step 2 above will reappear.
[*]**Attachments:** *n/a*
[*]**Platforms tested:** Rhythmbox on Ubuntu 12.04 Beta 1 64-bit (two partitions on separate machines), Banshee in Ubuntu 11.10 up-to-date final release.
[*]**Workaround:** Manually install the [FONT=Courier New]gstreamer0.10-fluendo-mp3[/FONT] package from the Ubuntu Software Center or apt-get.
[*]**Link to Discussion Thread:** *n/a*
[*]**Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-fluendo-plugins-partner/+bug/932103](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-fluendo-plugins-partner/+bug/932103)
[*]**Bug Report Status:** [COLOR=SeaGreen]Fix Released[/COLOR]
[*]**Bug status:** [COLOR=Red]Fixed on 11.10, but not on Precise[/COLOR]; I can easily reproduce this bug on my 12.04 test machines after this was marked Fix Released, but the issue seems resolved on 11.10 now.
[/LIST]

---

### Post by PaulW2U on 2012-04-01
[LIST=1][*]**Bug Short Description**:  Cannot log-in due to lightdm continually restarting.
[*]**How to Reproduce the bug**: Always happens here. This bug probably affects you or it doesn't.
[*]**Current behavior**: Before a log-in can be attempted, lightdm restarts. Switching to a tty isn't possible.
[*]**Attachments**: None.
[*]**Platform tested**: Ubuntu 12.04, fully updated from Beta 2.
[*]**Workaround**: Install/configure the use of gdm instead of lightdm.
[*]**Link to Discussion Thread**: [http://ubuntuforums.org/showthread.php?t=1949697](http://ubuntuforums.org/showthread.php?t=1949697)
[*]**Link to Bug Report**: [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/969589](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/969589)
[*]**Bug Report Status**: [COLOR="Green"]**Confirmed**[/COLOR], showing 8 users currently affected.
[*]**Bug status**: [COLOR="Green"]**Fix Released**[/COLOR].

This bug was probably a duplicate of [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/946674](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/946674) which is also showing as fixed.
[/LIST]

---

### Post by Doug S on 2012-04-03
[LIST=1]
[*]**Bug Short Description**: Reported load averages can be massively too low.
[*]**How to Reproduce the bug**: [Example program, exaggerates issue]("https://launchpadlibrarian.net/93810228/waiter.txt").
[*]**Current behavior**: uptime, top, report 0 load average when actually really high, under certain conditions.
[*]**Attachments**: Many on Launchpad bug report.
[*]**Platform tested**: Ubuntu 12.04. (and many more)(not 3.2.0-22.35, yet)
[*]**Workaround**: Compile kernel with CONFIG_NOHZ=no
[*]**Link to Discussion Thread**: [here]("http://ubuntuforums.org/showthread.php?t=1909253")
[*]**Link to Bug Report**: [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811")
[*]**Bug Report Status**: **[COLOR=#008000]Medium[/COLOR]**
[*]**Bug status**: Fixed (just) released - will be in kernel [FONT=Calibri]3.2.0-22.35[/FONT]
[*][FONT=Calibri]Also fixed in Kernel 3.4RC1, was backported to above.[/FONT]
[/LIST]

---

### Post by ray field on 2012-04-05
> **dankegel said:**
> Bug Short Description: Atheros AR9285 wireless doesn't work in Ubuntu 12.04 alpha 1
How to Reproduce the bug: install, optionally do full update, then try to connect via wireless
Current behavior: no networks visible
Attachments:
Platform tested: 12.04 alpha 1 64 bit after update, with AR9285 wifi chip
Workaround: 
Link to Discussion Thread: 
Link to Bug Report: [https://bugs.launchpad.net/ubuntu/+bug/917402](https://bugs.launchpad.net/ubuntu/+bug/917402)
Bug Report Status: Undecided
Bug status: New

Note: the installer had no problem with wireless; only after installation was it broken.

I have this card in the Lenovo S100 where it actually works under Lucid, much to my surprise. I don't even know how, because I had moved a prior installation from an Asus eee 1001P via Remastersys, and much to my amazement, the wifi simply worked.

---

### Post by Nick Payne on 2012-04-08
**Bug Short Description:** With Chrome pinned to launcher, using Unity launcher shortcut (Super+number) starts Chrome on wrong monitor with dual monitors.
**How to Reproduce the bug:** Pin Chrome to the launcher, position the mouse pointer on the right-hand monitor, use Super+number to launch Chrome. Chrome starts on the left-hand monitor, whereas if you use the mouse to start Chrome from the launcher on the RH monitor, it starts on the RH monitor
**Current behavior:** As above
**Attachments:**
**Platform tested:** 12.04 beta 2 amd64, Chrome 18.0.1025.151
**Workaround:** Don't use Unity launcher shortuct to start Chrome
**Link to Discussion Thread:**
**Link to Bug Report:**
**Bug Report Status:**
**Bug status:**

---

### Post by cornelis spronk on 2012-04-16
**Bug Short Description:**  HP LaserJet 6MP installs properly.  Printing a test page produces a blank page.
**How to Reproduce the bug:**   Doing a printer delete and reinstall does not solve problem
**Current behavior:** Normal printing does not even produce a blank page.  Only the printer install produces a blank page.
**Attachments:Terminal output:**


cs@cs-Dimension-3000:~$ system-config-printer
**** Incorrect IEEE 1284 Device ID: [u'drv:///hpijs.drv/hp-laserjet_6mp-hpijs-pcl3.ppd', u'drv:///hpcups.drv/hp-laserjet_6mp-pcl3.ppd']
**** Actual ID is MFG:Hewlett-Packard;MDL:HP LaserJet 6MP;
**** Please report a bug against the HPLIP component
**** Incorrect IEEE 1284 Device ID: [u'drv:///hpijs.drv/hp-laserjet_6mp-hpijs-pcl3.ppd', u'drv:///hpcups.drv/hp-laserjet_6mp-pcl3.ppd']
**** Actual ID is MFG:Hewlett-Packard;MDL:HP LaserJet 6MP;
**** Please report a bug against the HPLIP component


**Workaround:** Do not know how.
**Link to Discussion Thread:**
**Link to Bug Report:** None
**Bug Report Status: **
**Bug status:**

---

### Post by TerryNewton on 2012-04-20
1. Bug Short Description: Unclean shutdown
2. How to Reproduce the bug: do dmesg|grep EXT and note it has to recover the file system, or disable the boot splash to see the messages directly and note the message / is busy when shutting down or restarting.
3. Current behavior: Doesn't unmount root cleanly
4. Attachments:
5. Platform tested: Ubuntu PP
6. Workaround: funky: add /sbin/killall5 -15;sleep 2 to /etc/init.d/umountroot before the part where it remounts the root FS read-only - or directly kill the dhclient task which is causing this bug
7. Link to Discussion Thread:
8. Link to Bug Report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/963106](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/963106)
9. Bug Report Status: confirmed
10. Bug status: in progress [Apr 24 2012]

This in my opinion is a critical bug and can potentially cause data loss.

---

### Post by Johan Ryberg on 2012-04-20
**1.Bug Short Description:** Can't install Ubuntu 12.04 beta 2 Alternative 
**2.How to Reproduce the bug:** Install alternative
**3. Current behavior:** Installing the base systems seems OK but not the softwares. I got a big red screen with error message "An installation step failed..."
**4. Attachments:**
**5. Platform tested:** amd64
**6. Workaround:** install server and then ubuntu-desktop meta package I want to use LVM and disk encryption so I cant use the standard installation.
**7. Link to Discussion Thread:**
**8. Link to Bug Report:** [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/976509](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/976509)
**9. Bug Report Status:** Confirmed
**10. Bug status:** Not Fixed

---

### Post by tecs on 2012-04-21
**Bug Short Description:** After some usage from boot (10+ hrs) UI falls apart
**How to Reproduce the bug:** After using the PC for some time (10+ hrs, sometimes earliear) glitches start to appear
**Current behavior:** Pages opened in chrome are black until scrolled up and down, buttons become invisible in UI throughout the whole system, some filenames dissapear from icons, edited text in gedit becomes invisible (working on HTML pages only '<' and '>' remain visible).
**Attachments:** Two image attachments. Also when the bug appears:

```
Xorg.0.log is flooded with

[ 84428.555] (WW) intel(0): intel_uxa_prepare_access: bo map failed: No space left on device
[ 84428.555] (WW) intel(0): intel_uxa_prepare_access: bo map failed: No space left on device
```
```
kern.log and syslog are flooded with
[82929.434974] [drm:drm_gem_create_mmap_offset] *ERROR* failed to allocate offset for bo 0
[82929.536345] [drm:drm_gem_create_mmap_offset] *ERROR* failed to allocate offset for bo 0
```
There are no preceding errors in the logs.

**Platform tested:** 12.04 beta 2 i686, 3.2.0-23-generic, Chromium 18.0.1025.151
**Workaround:** Reboot the PC - temporary fix
**Link to Discussion Thread:** none
**Link to Bug Report:** none
**Bug Report Status:** none
**Bug status:** none

---

### Post by Doug S on 2012-04-23
[LIST=1]
[*]**Bug Short Description**: disk I/O race condition after update.
[*]**How to Reproduce the bug**: Needs pathetic computer and high disk I/O.
[*]**Current behavior**: Computer freezes for about 30 seconds, then appears to recover, after operation timeout.
[*]**Attachments**: See Launchpad bug report.
[*]**Platform tested**: Server edition minimum requirements test computer 12.04 server editiion. (with ATA drive. computer is actually < minimum requirements)
[*]**Workaround 1**: Use a modern computer
[*]**Workaround 2**: Install from ISO of 2012.03.27 and then do not update.
[*]**Link to Discussion Thread**: [here]("http://ubuntuforums.org/showthread.php?t=1958838")
[*]**Link to Bug Report**: [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986654")
[*]**Bug Report Status**: **[COLOR=#008000]Medium[/COLOR]**
[*]**Bug status**: Confirmed
[/LIST]

---

