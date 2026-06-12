---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-01-09
forum: Ubuntu Studio
---

### Post by sam28 on 2016-01-09
[IMG]http://joxi.ru/v29QZd6SYDN42G.jpg[/IMG]
How to fix this?

sudo apt-get install -f
and
sudo apt-get install -f
dosent help.

---

### Post by Bashing-om on 2016-01-09
sam28; Hello;

Let's poke at it. As you have the advisory:
" libunity-control-center1 is half-installed"
what results when we attempt to install it ?
```

sudo apt-get install --reinstall libunity-control-center1

```
Please use the "code tag" tool to post these results - much easier to work with.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see then where we go
[INDENT][INDENT][INDENT]from here[/INDENT][/INDENT][/INDENT]

---

### Post by sam28 on 2016-01-12
> **Bashing-om said:**
> sam28; Hello;

Let's poke at it. As you have the advisory:
" libunity-control-center1 is half-installed"
what results when we attempt to install it ?
```

sudo apt-get install --reinstall libunity-control-center1

```
Please use the "code tag" tool to post these results - much easier to work with.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see then where we go[INDENT][INDENT][INDENT]from here[/INDENT]
[/INDENT]
[/INDENT]

Tried. Here is result:
```
unclesam@unclesam-Aspire-4520G:~$ sudo apt-get install --reinstall libunity-control-center1[sudo] password for unclesam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/571 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package libunity-control-center1.
(Reading database ... 1178715 files and directories currently installed.)
Preparing to unpack .../libunity-control-center1_14.04.3+14.04.20150916-0ubuntu1_amd64.deb ...
Unpacking libunity-control-center1 (14.04.3+14.04.20150916-0ubuntu1) over (14.04.3+14.04.20150916-0ubuntu1) ...
Setting up libunity-control-center1 (14.04.3+14.04.20150916-0ubuntu1) ...
dpkg: error processing package unity-settings-daemon (--configure):
 package unity-settings-daemon is not ready for configuration
 cannot configure (current status `half-installed')
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
/sbin/ldconfig.real: /usr/lib/joxi/libbz2.so.1.0 is not a symbolic link


Errors were encountered while processing:
 unity-settings-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
unclesam@unclesam-Aspire-4520G:~$ 



```

Then i run 
```

sudo apt-get install --reinstall unity-settings-daemon

```

And now looks fine. :)

But do i need these packages in my Ubuntu Studio with XFCE 4.10?
If no nned - how to delete properly? 
Or better live it?

Thanx.

---

### Post by Bashing-om on 2016-01-12
sam28; Tough call :

> 
But do i need these packages in my Ubuntu Studio with XFCE 4.10?
If no need - how to delete properly? 
Or better live it?


I too run xfce4 - on a minimalistic install - and I do not have unity-settings-daemon installed on my system.
```

sysop@1404mini:~$ dpkg -l unity-settings-daemon
dpkg-query: no packages found matching unity-settings-daemon
sysop@1404mini:~$ apt-cache show unity-settings-daemon

```

I happen to know that ubuntu_studio has lightdm as the display manager - and as such I bet in your use case you do need it .

What returns:
```

apt-cache depends unity-settings-daemon
apt-cache rdepends unity-settings-daemon

```

[INDENT][INDENT]if it ain't broke
[INDENT][INDENT][INDENT]don't fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sam28 on 2016-01-13
> **Bashing-om said:**
> sam28; Tough call :



I too run xfce4 - on a minimalistic install - and I do not have unity-settings-daemon installed on my system.
```

sysop@1404mini:~$ dpkg -l unity-settings-daemon
dpkg-query: no packages found matching unity-settings-daemon
sysop@1404mini:~$ apt-cache show unity-settings-daemon

```

I happen to know that ubuntu_studio has lightdm as the display manager - and as such I bet in your use case you do need it .

What returns:
```

apt-cache depends unity-settings-daemon
apt-cache rdepends unity-settings-daemon

```
[INDENT][INDENT]if it ain't broke[INDENT][INDENT][INDENT]don't fix it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

```
unclesam@unclesam-Aspire-4520G:~$ apt-cache depends unity-settings-daemonunity-settings-daemon
  Depends: libaccountsservice0
  Depends: libasound2
  Depends: libc6
  Depends: libcairo2
  Depends: libcanberra-gtk3-0
  Depends: libcanberra0
  Depends: libcolord1
  Depends: libcups2
  Depends: libfontconfig1
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgnome-desktop-3-7
  Depends: libgtk-3-0
  Depends: libgudev-1.0-0
  Depends: libibus-1.0-5
  Depends: liblcms2-2
  Depends: libnotify4
  Depends: libpango-1.0-0
  Depends: libpulse-mainloop-glib0
  Depends: libpulse0
  Depends: librsvg2-2
  Depends: libupower-glib1
  Depends: libwacom2
  Depends: libx11-6
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxi6
  Depends: libxkbfile1
  Depends: libxtst6
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: accountsservice
  Depends: gsettings-desktop-schemas
  Depends: nautilus-data
  Depends: gnome-settings-daemon-schemas
  Depends: gnome-settings-daemon-schemas
  Depends: gsettings-ubuntu-schemas
  Suggests: x11-xserver-utils
  Suggests: gnome-screensaver
 |Suggests: metacity
  Suggests: <x-window-manager>
    fvwm1
    mutter
    notion
    ratpoison
    subtle
    9wm
    aewm
    aewm++
    afterstep
    amiwm
    awesome
    blackbox
    clfswm
    compiz
    ctwm
    dwm
    e17
    evilwm
    fluxbox
    flwm
    fvwm
    fvwm-crystal
    herbstluftwm
    i3-wm
    icewm
    icewm-experimental
    icewm-lite
    jwm
    kde-window-manager
    kde-window-manager-active
    larswm
    lwm
    matchbox-window-manager
    metacity
    miwm
    muffin
    mwm:i386
    mwm
    olvwm
    olwm
    openbox
    oroborus
    pekwm
    sapphire
    sawfish
    spectrwm
    stumpwm
    tinywm
    twm
    vtwm
    w9wm
    windowlab
    wm2
    wmaker
    wmii
    xfwm4
  Recommends: ibus
    ibus:i386
  Recommends: pulseaudio
  Recommends: systemd-services
    systemd-services:i386
  Breaks: banshee
  Breaks: banshee:i386
  Breaks: gnome-color-manager
  Breaks: gnome-color-manager:i386
  Breaks: gnome-control-center
  Breaks: gnome-control-center:i386
  Breaks: gnome-screensaver
  Breaks: gnome-screensaver:i386
  Breaks: gnome-session
  Breaks: <gnome-session:i386>
  Breaks: indicator-datetime
  Breaks: indicator-datetime:i386
  Breaks: rhythmbox
  Breaks: rhythmbox:i386
  Breaks: totem
  Breaks: totem:i386
  Breaks: unity
  Breaks: unity:i386
  Breaks: unity-greeter
  Breaks: unity-greeter:i386
  Conflicts: unity-settings-daemon:i386
unclesam@unclesam-Aspire-4520G:~$ apt-cache rdepends unity-settings-daemon
unity-settings-daemon
Reverse Depends:
  unity-settings-daemon:i386
  unity-settings-daemon:i386
  gnome-session-flashback
  unity-greeter
  unity-control-center
  ubuntu-session
  unity-settings-daemon:i386
  gnome-session-flashback
  unity-greeter
  unity-control-center
  ubuntu-session
  ubuntu-desktop
unclesam@unclesam-Aspire-4520G:~$ 
```

---

### Post by Bashing-om on 2016-01-13
sam28; Hummm ...

Presently I just do not see the need for you to have " libunity-control-center1 " installed UNLESS you have also installed the gnome desktop and/or some gnome applications .

We know:
> 
sysop@1404mini:~$ apt-cache show libunity-control-center1
-bk-
Description-en: utilities to configure the GNOME desktop
 This package contains the library used by Control Center panels

Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

xfce4 has no play here.

in the requested outputs I also do not see that xfce/lightdm are a factor .
Best however to double check:
What returns:
```

dpkg -l unity-settings-daemon:i386  gnome-session-flashback  unity-greeter  unity-control-center  ubuntu-session  unity-settings-daemon:i386  gnome-session-flashback  unity-greeter  unity-control-center  ubuntu-session  ubuntu-desktop

```

If all returns " dpkg-query: no packages found matching ....." Then I would think it safe to remove "libunity-control-center1" from the system.

If we break it ... we get to keep the pieces .. and
[INDENT][INDENT][INDENT]put it back together
[/INDENT][/INDENT][/INDENT]

---

