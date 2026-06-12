---
title: "Gnome-shell v. 3.23.91 does not work"
date: 2017-03-02
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-03-02
Has anyome already tested new gnome-shell (3.23.91-0ubuntu1) yet?
This version is still in proposed, though.
However, mutter (3.23.91) is already in release repo.

I did try these together, but the desktop environment did not launch.
I am using gdm (3.23.91) DE Manager.
I had to chroot the drive and downgrade back to g-s and m to v. 3.23.90.
That version works well.
I haven't tried installing only new mutter 3.23.91 without new g-s.

So, what did happen between these two?
Does g-s 3.23.91 need to be rebuild against newest mozjs38 first, I do not know.

I hope Jeremy Bicha helps with this issue here.

---

### Post by dino99 on 2017-03-02
ZZ is unusable here too: login loop, X does not start via tty neither.
I've checked .Xauthority and /tmp as usual in such a case, but does not resolve that issue.
Reconfiguring lightdm or switching to gdm/gdm3 also does not work.
Waiting some new updates till next week.

---

### Post by harry332 on 2017-03-02
Here is the bug report (#1669374):

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1669374](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1669374)

---

### Post by jbicha on 2017-03-02
GNOME Shell works fine here on zesty, but Budgie [doesn't work]("https://launchpad.net/bugs/1669495") with mutter 3.23.91.

---

### Post by harry332 on 2017-03-02
Most of the bugs are related to nvidia proprietary drivers and g-s.
However, I have Intel GPU (integral with Haswell processor).
Secondly, my setup works fine with g-s and mutter 3.23.90, but not with the 3.23.91 version.
What has changed between those version?

---

### Post by fthx on 2017-03-02
I don't know if it's related, but I do not get anymore a Wayland choice in GDM.

---

### Post by jbicha on 2017-03-03
The Budgie issue has been worked around with [mutter 3.23.91-0ubuntu1.1]("https://launchpad.net/ubuntu/+source/mutter/3.23.91-0ubuntu1.1")

---

### Post by harry332 on 2017-03-03
Jeremy,

Do you think that gnome-shell 3.23.91 needs to have xserver-xorg-video-intel installed, when using Intel GPU hardware?

1. Even though the package description says:
[COLOR=#ff0000]"The use of this driver is discouraged if your hw is new enough (ca.
2007 and newer). You can try uninstalling this driver and let the
server use it's builtin modesetting driver instead."
[/COLOR]
2. Even though the gnome-shell 3.23.90 works perfectly well without the xserver-xorg-video-intel.

3. My hardware is Intel Haswell (2013).

---

### Post by jbicha on 2017-03-03
harry, why don't you install it and find out :) It is installed by default.

---

### Post by harry332 on 2017-03-03
Well, tried the latest g-s and mutter with xserver-xorg-video-intel => blackscreen.
I found the console in the tty6.
Downgraded to 3.23.90 and all is well again.

---

### Post by ventrical on 2017-03-03
Daily .ISO just locks up.

Go figure.
Will try another machine.

---

### Post by ventrical on 2017-03-03
Ok.. it is working really good here. The installer and post installer greeter/welcome  are just super from an Instructional Development standpoint. I took a screencast using vokoscreen (which is better suited for unity) so there is a chipmunk (or xerus)  in there so just mute it.

Running on an old 8 year old  machine with 40GB Sata hdd.

[URL="https://www.youtube.com/watch?v=lpjtHN6yTtM&feature=youtu.be"]https://www.youtube.com/watch?v=lpjtHN6yTtM&feature=youtu.be

[/URL]

Regards..

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.10.0-9-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.23.90 (Gtk 3.22.7-1ubuntu2)
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: desktop Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 driver: N/A
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 13.0.4 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-3 Logitech Webcam C210 driver: USB Audio usb-ID: 001-002
           Sound: Advanced Linux Sound Architecture v: k4.10.0-9-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 40.0GB (14.5% used)
           ID-1: /dev/sda model: WDC_WD400BD size: 40.0GB
Partition: ID-1: / size: 34G used: 5.5G (18%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.5C mobo: 34.0C gpu: 35.0
           Fan Speeds (in rpm): cpu: 4192 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 213 Uptime: 39 min Memory: 1867.1/3005.7MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.51) inxi: 2.3.8 
ventrical@ventrical-System-Product-Name:~$ 

```

---

### Post by ventrical on 2017-03-03
bwwahahahah... You are all testing 91 and I have 90.. doh ! :)

Regards..

---

### Post by harry332 on 2017-03-04
Ventrical, gnome-shell 3.23.91 is still in proposed (and I think I know why).
However, mutter 3.23.91 is in release repo.

---

### Post by harry332 on 2017-03-04
I have now tested Zesty with all updates (but without proposed enabled) and it is working just fine.
This means that mutter 3.23.91-0ubuntu1.1 is OK.

This thread is now only about gnome-shell 3.23.91.

---

### Post by dino99 on 2017-03-04
@harry
can you check which gir1.2-mutter-* is installed with your latest config. On my system, checking the 'obsolete' package via synaptic, i see that mutter 3.23.91 has been proposed _without_ upgrading to gir1.2-mutter-0 . This seems unexpected, as the gir1.2-mutter-0 is at 3.23.91 version.

---

### Post by harry332 on 2017-03-04
Dino99,

Checked, installation is complete.
See here:

 "apt-cache show gir1.2-mutter-0"
Package: gir1.2-mutter-0
Priority: optional
Section: universe/introspection
Installed-Size: 657
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: mutter
Version: 3.23.91-0ubuntu1.1
Depends: gir1.2-atk-1.0, gir1.2-freedesktop, gir1.2-gdesktopenums-3.0, gir1.2-glib-2.0, gir1.2-gtk-3.0, gir1.2-json-1.0, gir1.2-pango-1.0, libmutter-0-0 (= 3.23.91-0ubuntu1.1)
Breaks: gnome-shell (<< 3.13.92~)
Filename: pool/universe/m/mutter/gir1.2-mutter-0_3.23.91-0ubuntu1.1_amd64.deb
Size: 132996
MD5sum: 498a5111c0466685d83cdf29f6f576bb
SHA1: 9786dd72cdc173a9aa670ae126d308e9ca0310fc
SHA256: d6178c7481941bda0e904e209f9b67150e5206cbec86c1e672150fe98bae3305

---

### Post by harry332 on 2017-03-04
Dino99,
Also note that gnome-shell_3.23.91 depends on gir12-mutter-0_>=3.23.91.
So having gnome-shell_3.23.91 and gir1.2-mutter-0_3.23.90 installed at the same time should be an impossible situation (or broken package installation).

---

### Post by dino99 on 2017-03-04
Thanks ,
i've checked on a ZZ partition which has not been upgraded yet to 3.23.91, due to an other ZZ partition fully upgraded, and having the known issue.

---

### Post by harry332 on 2017-03-04
This is from the bug report #1663974:

I get the following error with blackscreen and taken from (tty6) vt6.
 [SIZE=2]
"journalctl"

org.gnome.Shell.desktop[744]: (EE)[/SIZE]

 [SIZE=2]org.gnome.Shell.desktop[744]: Fatal server error[/SIZE]

 [SIZE=2]org.gnome.Shell.desktop[744]: (EE)[/SIZE]

 [SIZE=2]gnome-session-binary[726]: Unrecoverable failure in requested component org.gnome.Shell.desktop[/SIZE]

 [SIZE=2]gnome-session-binary[726]: Warning: app ’org.gnome.Shell.desktop’ exited with code 1[/SIZE]

 [SIZE=2]gnome-session[726]: gnome-session-binary: Warning: app ’org.gnome.Shell.desktop’ exited with code 1[/SIZE]

 [SIZE=2]gdm-launch-environment[704]: Pam_unix (gdm-launch-environment: session) session closed for user gdm


[/SIZE]

---

### Post by harry332 on 2017-03-04
I also tested if the older gdm3 (3.23.4-0ubuntu1) works better, but no avail.

---

### Post by fthx on 2017-03-06
Some news :

Yesterday I installed lightdm and I could see that brutal logouts happens with it too. Next I changed one setting in Synaptic, unchecking "consider recommends as depends" (I don't know the exact words in English). And it marked as removable some packages, that I removed. Next I switched back to gdm and this morning I've got a console login, no graphical session (Nvidia or Nouveau driver).

The faulty package is **libgnome-2-0** that is apparently needed by **gdm3** but not treated as a depends.

I recovered instantly a graphical gdm & session.

---

### Post by harry332 on 2017-03-06
fthx,

Now that would be very strange indeed.
Package libgnome-2-0 is gtk2 package which pulls in gconf-service, libbonobo2-0, libgnomevfs2-0 ...

How did you come to the conclusion that gdm3 needs it?
Do you have gdm3_3.23.91 installed along with mutter 3.23.91?
Do you have gnome-shell_3.23.91 installed? It is still in proposed now.

---

### Post by fthx on 2017-03-06
I've got all the latest *.91 Gnome packages.
Well, without libgnome I got no gdm since it's the only package change which could affect gdm, I don't think gimp is related :-) .
And this morning when I installed back libgnome, it caused an immediate successful login with gdm.

I'll check that again now.

edit : so I tried the exact procedure again and gdm works without libgnome.

All that is strange. The only thing I did yesterday was installing/removing lightdm and removing libgnome & al.

---

### Post by jbicha on 2017-03-06
> **fthx said:**
> 
All that is strange. The only thing I did yesterday was installing/removing lightdm and removing libgnome & al.

Remember that during the development cycle, updates are installed [automatically]("https://ubuntuforums.org/showthread.php?t=2346439"). So check your unattended-upgrades logs too.

libgnome-2-0 being removed is expected since openjdk-8 was updated this weekend to not recommend it. Did you have default-jre (or similar) installed?

---

### Post by fthx on 2017-03-06
If it's in /var/log/unattended-upgrades, the log is void.
Yes i've got default-jre package installed. I installed the latest *-4 openjdk version saturday, so it should be the right explanation.

I still don't know what happened to get a console login this morning (twice in a row). It works now, and that's the point.

---

### Post by fthx on 2017-03-09
I noticed that my (X) session will brutally logout when I get no "GNOME on Wayland" option in GDM menu.

edit : no... but still strange that Wayland option sometimes appears, sometimes not.

---

### Post by harry332 on 2017-03-10
This original thread is about gnome-shell crashing at the moment it should start (gnome-shell does not work).
The bug report is here:

[https://bugs.launchpad.net/ubuntu/+s...l/+bug/1669374]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1669374")

The forced logout issue is not the same bug.
It is about session dying because gdm couldn't start correctly.
That is why you do not see the wayland session option when logging in.
Another remarkable difference is that if you still log in (gnome session) you cannot shut down the session anymore nor log in as another user.
There is no window with the shut down - restart - log in options.
And soon the session ends (forced) with another log in loop.

---

### Post by dino99 on 2017-03-10
gnome-shell has been updated to add the missing gir1.2-geoclue-2.0
its fine now here.

---

### Post by harry332 on 2017-03-10
Right, installing this missing dependence has fixed this bug.
Marking this "solved" now.

---

### Post by jbicha on 2017-03-10
Harry and dino99, thanks for the follow up.

For you to have experienced this bug meant that you didn't have ubuntu-gnome-desktop, gnome-maps or gnome-weather installed. (And that's why I couldn't duplicate the bug earlier.)

gnome-shell 3.23.91 added a new Weather forecast below the calendar in the clock drop-down in the top bar. I'm curious whether it works for you without gnome-weather installed.

---

