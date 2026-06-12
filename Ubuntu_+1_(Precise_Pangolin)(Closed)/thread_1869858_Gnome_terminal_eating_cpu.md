---
title: "Gnome terminal eating cpu"
date: 2011-10-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lan3y on 2011-10-26
Hi,

i'm currently running the latest packages from precise repos so i though i should post here.

When ever i close terminal the window disappears but the process takes up all cpu power (100% on system monitor > processes ).

has anyone else had this problem?

lan3y

---

### Post by collisionystm on 2011-10-26
> **lan3y said:**
> Hi,

i'm currently running the latest packages from precise repos so i though i should post here.

When ever i close terminal the window disappears but the process takes up all cpu power (100% on system monitor > processes ).

has anyone else had this problem?

lan3y
[COLOR=Red]

latest packages from precise repos [/COLOR]

[COLOR=Black]Why even bother asking when you know you are using beta software?[/COLOR] Did this problem occur on 11.10?

---

### Post by lan3y on 2011-10-26
> **collisionystm said:**
> [COLOR=Red]

latest packages from precise repos [/COLOR]

[COLOR=Black]Why even bother asking when you know you are using beta software?[/COLOR] Did this problem occur on 11.10?

No it did not occur in 11.10, which is why I'm posting it in the 12.04 forum.

and i wanted to see if any others had a similar problem.

lan3y

---

### Post by effenberg0x0 on 2011-10-26
> **lan3y said:**
> Hi,

i'm currently running the latest packages from precise repos so i though i should post here.

When ever i close terminal the window disappears but the process takes up all cpu power (100% on system monitor > processes ).

has anyone else had this problem?

lan3y

One other user reported what I think it's a very similar problem so far. [http://ubuntuforums.org/showthread.php?t=1868734](http://ubuntuforums.org/showthread.php?t=1868734) If you can't find a reason for this (ie. a process you created in the terminal, etc) and the problem persists after full update / upgrade to standard sources and a couple restarts, you should consider reporting it to launchpad bugs. 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-26
> **lan3y said:**
> No it did not occur in 11.10, which is why I'm posting it in the 12.04 forum.

and i wanted to see if any others had a similar problem.

lan3y

You are right. The only reason for testing is finding bugs and unusual behaviors, checking if others see the same thing, and creating detailed reports that can possibly help developers.

---

### Post by cariboo on 2011-10-26
Even though the packages we are using come from Debian Testing, we could consider them pre-alpha. 

That being said I tried to duplicate the op's problem, both using another terminal with top running and system monitor. I get a spike up to about 8% when closing a terminal according to system monitor, but how much of that is system monitor itself. I'm not sure.

Top shows a jump up to 5% when closing a terminal, so I don't have the problem here

---

### Post by lan3y on 2011-10-26
Looking deeper in to the issue it seems to be a more wider issue to gnome, i have tried taking a print screen to show what happens but the gnome-screenshot program produces a black image with just the mouse cursor showing. after 2 attempts at using gnome-screenshot 2 gnome-screenshot processes have also appeared in the system monitor, eating the cpu as well.

screenshot output: [http://imgur.com/i0rrD](http://imgur.com/i0rrD)

Package infos:

```
->dpkg -s gnome-terminal
Package: gnome-terminal
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 756
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 3.0.1-0ubuntu3
Replaces: gnome-terminal-data (<< 2.28.1-1ubuntu1)
Provides: x-terminal-emulator
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk-3-0 (>= 3.0.0), libice6 (>= 1:1.0.0), liblaunchpad-integration-3.0-1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0), libsm6, libvte-2.90-9 (>= 1:0.28.1-1ubuntu1), libx11-6, gsettings-desktop-schemas (>= 0.1.0), gnome-terminal-data (>= 3.0), gnome-terminal-data (<< 3.1)
Recommends: yelp, gvfs
Description: GNOME terminal emulator application
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 GNOME Terminal features the ability to use multiple terminals in a single
 window (tabs) and profiles support.
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>

``````
->dpkg -s gnome-system-monitor
Package: gnome-system-monitor
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1216
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 3.2.1-0ubuntu1
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libglibmm-2.4-1c2a (>= 2.28.0), libgtk-3-0 (>= 3.0.0), libgtkmm-3.0-1 (>= 3.0.1), libgtop2-7 (>= 2.23.2), liblaunchpad-integration-3.0-1 (>= 0.1.17), librsvg2-2 (>= 2.14.4), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.6), libwnck-3-0 (>= 2.91.6), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend
Recommends: gvfs
Description: Process viewer and system resource monitor for GNOME
 This package allows you to graphically view and manipulate the running
 processes on your system.  It also provides an overview of available
 resources such as CPU and memory.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>

``````
->dpkg -s gnome-screenshot
Package: gnome-screenshot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 316
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gnome-utils
Version: 3.2.1-0ubuntu1
Replaces: gnome-utils (<< 2.30.0-2)
Depends: libc6 (>= 2.7), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.29.14), libgtk-3-0 (>= 3.0.3), libx11-6, libxext6, dconf-gsettings-backend | gsettings-backend, gnome-utils-common (>= 3.2), gnome-utils-common (<< 3.3)
Recommends: nautilus
Conflicts: gnome-utils (<< 2.30.0-2)
Description: screenshot application for GNOME
 This tool takes a picture of the desktop or of a window and saves it
 into a file.
Homepage: http://live.gnome.org/GnomeUtils
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

```

---

### Post by effenberg0x0 on 2011-10-26
I left a terminal running **while true; do ps ax; done** for about 3 minutes and was looking at system-monitor. The CPU usage was stuck at 2 to 3% at most, when all 6 cores were underclocked to 800MHz, which I believe would be normal CPU usage. I could not see a spike in cpu usage when closing the terminal. There's some different condition in the setup of users that see this behavior.

@lan3y
A test one could do is launch **strace gnome-terminal** and look for some clue and distinct error (fread/fstat errors, timeouts, etc).

---

### Post by effenberg0x0 on 2011-10-26
@lan3y

There's a similar report on Google, with a solution. Can you try it and report back?
[http://forums.gentoo.org/viewtopic-t-888252-start-0.html](http://forums.gentoo.org/viewtopic-t-888252-start-0.html)

---

### Post by lan3y on 2011-10-26
will try the google result now

here is the strace on terminal: [http://pastebin.com/BMDYbSmX](http://pastebin.com/BMDYbSmX)

lan3y
[COLOR=Red]
Fixed after going back down to nvidia driver 173,

Cheers for the help everybody[/COLOR]

---

### Post by effenberg0x0 on 2011-10-26
Cool, but maybe going back to 173 is a little too drastic. You could try going back one or two versions and see how it goes from there.

Regards,
Effenberg

---

### Post by ventrical on 2011-10-26
> **lan3y said:**
> Looking deeper in to the issue it seems to be a more wider issue to gnome, i have tried taking a print screen to show what happens but the gnome-screenshot program produces a black image with just the mouse cursor showing. after 2 attempts at using gnome-screenshot 2 gnome-screenshot processes have also appeared in the system monitor, eating the cpu as well.

screenshot output: [http://imgur.com/i0rrD](http://imgur.com/i0rrD)

Package infos:

```
->dpkg -s gnome-terminal
Package: gnome-terminal
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 756
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 3.0.1-0ubuntu3
Replaces: gnome-terminal-data (<< 2.28.1-1ubuntu1)
Provides: x-terminal-emulator
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk-3-0 (>= 3.0.0), libice6 (>= 1:1.0.0), liblaunchpad-integration-3.0-1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0), libsm6, libvte-2.90-9 (>= 1:0.28.1-1ubuntu1), libx11-6, gsettings-desktop-schemas (>= 0.1.0), gnome-terminal-data (>= 3.0), gnome-terminal-data (<< 3.1)
Recommends: yelp, gvfs
Description: GNOME terminal emulator application
 GNOME Terminal is a terminal emulation application that you can use to
 perform the following actions:
  - Access a UNIX shell in the GNOME environment.
  - Run any application that is designed to run on VT102, VT220, and xterm
 terminals.
 .
 GNOME Terminal features the ability to use multiple terminals in a single
 window (tabs) and profiles support.
Original-Maintainer: Guilherme de S. Pastore <gpastore@debian.org>

``````
->dpkg -s gnome-system-monitor
Package: gnome-system-monitor
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1216
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Version: 3.2.1-0ubuntu1
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libglibmm-2.4-1c2a (>= 2.28.0), libgtk-3-0 (>= 3.0.0), libgtkmm-3.0-1 (>= 3.0.1), libgtop2-7 (>= 2.23.2), liblaunchpad-integration-3.0-1 (>= 0.1.17), librsvg2-2 (>= 2.14.4), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.6), libwnck-3-0 (>= 2.91.6), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend
Recommends: gvfs
Description: Process viewer and system resource monitor for GNOME
 This package allows you to graphically view and manipulate the running
 processes on your system.  It also provides an overview of available
 resources such as CPU and memory.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>

``````
->dpkg -s gnome-screenshot
Package: gnome-screenshot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 316
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386
Source: gnome-utils
Version: 3.2.1-0ubuntu1
Replaces: gnome-utils (<< 2.30.0-2)
Depends: libc6 (>= 2.7), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.29.14), libgtk-3-0 (>= 3.0.3), libx11-6, libxext6, dconf-gsettings-backend | gsettings-backend, gnome-utils-common (>= 3.2), gnome-utils-common (<< 3.3)
Recommends: nautilus
Conflicts: gnome-utils (<< 2.30.0-2)
Description: screenshot application for GNOME
 This tool takes a picture of the desktop or of a window and saves it
 into a file.
Homepage: http://live.gnome.org/GnomeUtils
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

```


Yup .. same problem here ... I removed the Unity package, downloaded shutter and all is well again in (Gnome-Shell)

---

