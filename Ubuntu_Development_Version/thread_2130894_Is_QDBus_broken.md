---
title: "Is QDBus broken?"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-03-30
Anyone else having problems with QDBus, in Raring :confused:

I keep getting this error:

```
qdbus: could not find a Qt installation of ''

```

UbuntuUpdates says:

> Package "qdbus"

Name:	qdbus

Description:	
Qt 4 D-Bus tool

Latest version:	4:4.8.4+dfsg-0ubuntu9
Release:	raring (13.04)
Level:	base
Repository:	main
Head package:	qt4-x11
Homepage:	[http://qt-project.org/](http://qt-project.org/)


Installed version:

```
vindsl@Zuul:~$ apt-cache policy qdbus
qdbus:
  Installed: 4:4.8.4+dfsg-0ubuntu9
  Candidate: 4:4.8.4+dfsg-0ubuntu9

```

---

### Post by mc4man on 2013-03-31
Where might one be seeing such message?

Whatever it is qdbus might be doing here unseen it appears to be fine.
If I take a service I know of, (org.mpris.MediaPlayer2.<whatever>) & a path, (/org/mpris/MediaPlayer2) with  an appropriate arg. it works fine. (in this case meaning player open with something in playlist
Ex.'s
```
qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause
```
 ```
qdbus org.mpris.MediaPlayer2.audacious /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause
```
ect.

---

### Post by VinDSL on 2013-03-31
> **mc4man said:**
> Where might one be seeing such message?
I'm using it to extract Guayadeque titles for Conky.  I have other ways of extracting titles, but QDBus has been working flawlessly for  me, for at least a year.  It just quit working, a couple of days ago.

I was interested in seeing if anyone else was having problems with QDBus, or more precisely, if anyone else was even using it... LoL!

Evidently, it's working for you, which is encouraging.

In order to provide some context, using your first example, let's crank up Icecast via VLC.

Here's what I'm seeing on my rig...

```

vindsl@Zuul:~$ vlc
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x9940908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xafd98698] access_http access: Raw-audio server found, m4a demuxer selected
[0xafd9bd80] packetizer_mpeg4audio demux packetizer: AAC channels: 1 samplerate: 22050

```

So far, so good.  Now let's try pausing the playback...

```
vindsl@Zuul:~$ qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause
qdbus: could not find a Qt installation of ''
vindsl@Zuul:~$ 
```

Nuttin' honey!  :D

---

### Post by VinDSL on 2013-03-31
w00t!  Think I figured it out.

I just installed the Qt5 'ubuntu-sdk' and the QDBus error went away.

Link:  [https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper](https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-proper)

Maybe Qt5 is being used now.  Here's the output...

```
vindsl@Zuul:~$ qdbus
:1.1
 org.a11y.Bus
:1.10
 org.freedesktop.ScreenSaver
 org.gnome.SettingsDaemon
 org.gnome.SettingsDaemon.Power
 org.gnome.SettingsDaemon.XRANDR
:1.11
 org.PulseAudio1
 org.freedesktop.ReserveDevice1.Audio0
 org.pulseaudio.Server
:1.114
:1.115
:1.116
:1.12
 org.freedesktop.secrets
 org.gnome.keyring
:1.122
:1.123
:1.125
 com.ubuntu.OneConf
:1.126
:1.13
 org.freedesktop.Notifications
 org.gnome.Caribou.Keyboard
 org.gnome.Magnifier
 org.gnome.Panel
 org.gnome.ScreenSaver
 org.gnome.Shell
 org.gnome.Shell.Screenshot
 org.gnome.keyring.SystemPrompter
 org.gtk.MountOperationHandler
:1.137
 org.gnome.Terminal
:1.138
:1.14
:1.15
 ca.desrt.dconf
:1.16
 org.freedesktop.Telepathy.Client.GnomeShell._3a1_2e16.n0
:1.17
 org.gnome.Shell.CalendarServer
:1.18
 org.gnome.evolution.dataserver.Sources1
:1.19
:1.2
:1.20
 org.freedesktop.Telepathy.AccountManager
 org.freedesktop.Telepathy.ChannelDispatcher
 org.freedesktop.Telepathy.MissionControl5
:1.21
:1.22
 org.gnome.Identity
 org.gnome.OnlineAccounts
:1.24
 org.gtk.Private.UDisks2VolumeMonitor
:1.25
 org.gtk.Private.AfcVolumeMonitor
:1.26
 org.gtk.Private.MTPVolumeMonitor
:1.27
 org.gtk.Private.GPhoto2VolumeMonitor
:1.29
 org.gnome.GConf
:1.31
 org.gnome.Bluetooth.applet
:1.32
 org.gnome.zeitgeist.datahub
:1.33
 org.gnome.zeitgeist.Engine
:1.35
 org.freedesktop.Tracker1.Miner.Applications
 org.freedesktop.Tracker1.Miner.Files
 org.freedesktop.Tracker1.Miner.Files.Index
:1.36
:1.37
 org.freedesktop.Tracker1
:1.39
 org.freedesktop.FileManager1
 org.gnome.Nautilus
 org.gnome.Nautilus.SearchProvider
:1.4
 org.gtk.vfs.Daemon
:1.41
:1.42
 com.canonical.Unity
 net.launchpad.plank.dock1
:1.43
 org.gnome.DejaDup.Monitor
:1.44
 org.gnome.network_manager_applet
:1.47
 org.gnome.EvolutionAlarmNotify
:1.48
:1.5
:1.50
 org.gnome.zeitgeist.SimpleIndexer
:1.51
 org.ayatana.bamf
:1.52
 org.freedesktop.Telepathy.Client.Zeitgeist
:1.57
:1.58
 org.gnome.evolution.dataserver.AddressBook5
:1.6
:1.61
:1.62
 org.gnome.evolution.dataserver.Calendar4
:1.65
:1.67
:1.7
 org.gnome.SessionManager
:1.71
:1.72
:1.73
 com.ubuntuone.SyncDaemon
:1.74
:1.78
:1.80
:1.81
:1.88
:1.89
:1.9
:1.98
 org.freedesktop.Telepathy.Client.Logger
 org.freedesktop.Telepathy.Logger
:1.99
org.freedesktop.DBus
vindsl@Zuul:~$ 

```

Was just getting the error dialog before.

---

### Post by VinDSL on 2013-03-31
Bingo!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-30-mar-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-mar-2013-2.png")[/INDENT]


Thanks!

Takes a village...  ;)

---

### Post by VinDSL on 2013-03-31
Oh, BTW...

Here's a sample of the CLI output (listening to Puls' Radio right now)

```
vindsl@Zuul:~$ qdbus org.mpris.guayadeque /\Player org.freedesktop.MediaPlayer.GetMetadata | grep title | cut -f2- -d" "
Triotonic (Extended Mix)
vindsl@Zuul:~$
```

Conky code looks like this (provides scrolling for long names)

```
##################################
##   GUAYADEQUE (Experimental)  ##
##################################
${if_running guayadeque}
${voffset -33}${font DroidSans:bold:size=8}${color4}GUAYADEQUE${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.guayadeque /\Player org.freedesktop.MediaPlayer.GetMetadata | grep title | cut -f2- -d" "`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.guayadeque /\Player org.freedesktop.MediaPlayer.GetMetadata | grep title | cut -f2- -d" "}}${font}${else}${alignc}${execi 2 qdbus org.mpris.guayadeque /\Player org.freedesktop.MediaPlayer.GetMetadata | grep title | cut -f2- -d" "}${font}${endif}${endif}

```

---

### Post by VinDSL on 2013-03-31
> **mc4man said:**
> If I take a service I know of, (org.mpris.MediaPlayer2.<whatever>) & a path, (/org/mpris/MediaPlayer2) with  an appropriate arg. it works fine.[...]
Finally got VLC working with QDBus/MPRIS.

Had to upgrade to the 2.1.0-git version.  Is that what you're running?!?!?

Just curious...

Heh!  VLC 2.1.0 is nice!  Didn't know what I was missing.  :)


Openbox/LXDE

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-31-mar-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-31-mar-2013-1.png")[/INDENT]

---

### Post by mc4man on 2013-03-31
> **VinDSL said:**
> Finally got VLC working with QDBus/MPRIS.

Had to upgrade to the 2.1.0-git version.  Is that what you're running?!?!?

While I normally would use the git dev version, as of late have just been installing what's in the repo (lazy I guess

As far as vlc with mpris - that's been working for quite some, as in soundmenu (& the qdbus commands ), in the soundmenu since 11.04 or so. (lost track, though it's needed a small trick or 2 at times to get going

Maybe you mean in some VinDSL special use???

---

### Post by VinDSL on 2013-03-31
> **mc4man said:**
> Maybe you mean in some VinDSL special use???
That's undoubtedly part of it.  This poor box has turned into Frankenstein's Monster. LoL!

Qt5 took care of the Guayadeque QDBus error, but...

I tried your MPRIS example tonight.  It still wasn't working / left me scratching my head.

I was getting a "org.mpris.MediaPlayer2 doesn't exist" (or similar) QDBus error.

Doing some Google forensics, I ran across a Q&A blog that suggested installing the VLC "[master-daily]("https://launchpad.net/~videolan/+archive/master-daily")" dev branch.

And, sure enough, it worked a treat (on this machine) ;)

---

