---
title: "Problem with Linux and ASRock motherboard."
date: 2016-01-03
forum: Ubuntu/Debian BASED
---

### Post by jesus-freak on 2016-01-03
I have a very basic computer with an ASRock Q1900B-ITX motherboard in it. I have no additional hardware, no sound car or video card ad on's. I have 4GB of memory. It has an Intel Celeron CPU J1900  1.99GHz × 4.  I have tried this computer with an SSD and with a standard HD and the problem exists for both. The problem is this, on any linux distro that uses a kernel newer than 3.13-0-27 (which is most now) I get a complete freeze up of my system regularly. This is not a crash that you can wait out and then it un-freezes. It totally locks up and is completely unresponsive. I actually have to force a shut down and restart. Until now my only solution has been to download the old 3.13 kernel and then set grub to automatically boot to that kernel. This completely fixes the issue. However, I would really like to figure out why this is happening and find out if there is any kind of real fix for this so I don't have to jump through hoops to use a linux system and then be using an older kernel. If anyone has any thoughts or ideas I would appreciate it.

---

### Post by kurt18947 on 2016-01-03
Have you checked for a BIOS update? Is it practical for you to install Windows 10 temporarily to see if it does the same thing? See if a distro using a 4.x kernel like a 16.04 daily locks up as well, or only recent 3.13.x?

---

### Post by jesus-freak on 2016-01-03
Thanks for your post! No, I haven't updated the BIOS. I'm not sure even how to do that. I'll research it. As for your question about Windows 10, no, I do not even have a copy of any version of Windows. I have tried many different distros and many different kernels. I can tell you this for sure, Kernel 3.16.x up until the latest kernel 4.x all have these freezes. The only kernel that I have found that works well for me is 3.13-0-27. The kernel 3.13-0-27 works really well for me with no problems. However, at some point things will progress beyond that kernel and so I really want to figure out how to actually fix this.

---

### Post by kurt18947 on 2016-01-03
Asrock's web site should have info on how to do a BIOS update for your board. BIOS upgrades are regarded as somewhat risky because a bad flash can permanently disable your motherboard. One cause is power interruption during the flash process. Flashing only takes a couple minutes but if the timing is really bad.......  it is possible to download a Windows 10 .iso directly from Microsoft. My thought on installing Windows 10 would be to see if your problem exists with a 'modern' O.S. besides linux. Microsoft download link -

[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)

When asked for the 25 digit key there should be a 'insert later' button. I would not recommend using this Windows install long term without having a a key/license but I'd hope Microsoft wouldn't get too upset about running it for an short time for troubleshooting purposes then wipe.

---

### Post by jesus-freak on 2016-01-03
I just updated my BIOS from version 1.06 to version 1.80. I'm running kernel 4+. I'll run it for a while and see if there is any change. I'll let you know what happens.

---

### Post by kurt18947 on 2016-01-03
Yes please. We have a machine with an AMD A88 chipset and it's been excellent, no hiccups at all.

---

### Post by jesus-freak on 2016-01-03
Well, so far so good!!! I've been running it with the latest kernel for over 7 hours now without any freezing at all. Thanks so much for the suggestion of updating the BIOS!!! I need to give it some more time before I can say that it is 100% fixed but it's looking really good so far!! Thanks again!

---

### Post by grahammechanical on 2016-01-03
I am not clear if the machine has a video card or not. If it has a video adapter then what model is it? And are you using the open source video driver or a proprietary video driver.

I have an Nivida GT220 which is old enough for Nvidia to drop support for it from the latest drivers. During testing of Ubuntu 15.10 & the 3.19 kernel I was getting GPU lockup when running the open source video driver (Nouveau). It would happen when I attempted to select large amounts of text in a Libreoffice document. This problem does not exist with the older Nvidia driver that supports my video card.

Everything would freeze, just like you say. Switch to tty1 (Ctrl+Alt_F1) and Linux would be reporting GPU lockup.

Just a thought about what the problem could be.

Regards.

---

### Post by jesus-freak on 2016-01-03
grahammechanical, As I stated in my first post >  I have no additional hardware, no sound card or video card ad on's...I use the on-board sound and video at the moment. Unlike your problem, mine never happened during a specific task, it was completely random.My problem seems to have been completely resolved by updating the BIOS as kurt18947 suggested.

Just as I was declaring victory, I got a freeze up of my system :( Still, it is much better than before. It could have just been a fluke so I will just keep playing with it and see if it happens again.

So it's official, the BIOS update did not fix my problem. I've had two freeze ups. So once again I will entertain any suggestions.

---

### Post by mastablasta on 2016-01-04
you need to find out why it is freezing. install psensor and check the temp.

I couldn't get it to work at all. couldn't figure out why suddenly it is no longer working and freezing. in any case, it was from overheating, but I couldn't figure it out what would be causing it suddenly. I even re-pasted the thermal paste on CPU. well it turns out there were two settings in BIOS that were wrong. one was CPU quiet which kept the fan speed low but it was too low. the other one was (so it seems) the voltage for GPU. it looked like it didn't have enough voltage so sometimes the fan would just be still even though the board was hot.

so check the temps (you can also reset on freeze and immediately go to BIOS to check the temp). if they are high (clean all fans and such) then check BIOS for any setting that could affect fan speed or temp.

---

### Post by oldfred on 2016-01-04
Possible issue, or he shows many of the tests he ran to resolve issue.
  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)

---

### Post by jesus-freak on 2016-01-04
mastablasta, this motherboard is a fan-less board that doesn't require any fans other than the fan built into the power supply. Right now it is running at 39c.... Oldfred, that article seems to be for a different system. That guy mentions the fix having to do with the ""CPU OC Fixed Mode" in the BIOS but my BIOS has no such setting.

Just an update. My system is still freezing up. One thing I have noticed is that when I use Ubuntu or any system running Gnome that when I run the driver manager, it doesn't turn up anything. But when I run a system with KDE or in this case Deepin15, the driver manager shows this "Unknown This device is not working. intel-microcode (open-source) Version 3.20151106.1. Processor microcode firmware for intel CPU's" The option that is selected by default is "Do not use the device". I have selected to enable it and to use the driver shown but it doesn't seem to make any improvement. I just wanted to post this in case this might be a clue for someone.

---

### Post by mastablasta on 2016-01-05
does any of the system logs show why the failure occurred or at what point? - boot into recovery mode to check the old logs.

---

### Post by jesus-freak on 2016-01-05
To be honest I really don't even know how to boot into recovery mode and check old logs. I am good at following instructions and getting things done in Linux but I don't have much first hand knowledge. I know that once I just kept the system monitor open hoping the computer would freeze while it was open. I expected to see some jump in CPU or the RAM doing something crazy but when it did freeze, everything just looked totally normal. No spikes or dips in the graphs. It's just weird.

---

### Post by mastablasta on 2016-01-05
when booting hold shift then select to recovery mode then mount the disk: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
you can use nano to see the logs. which are in /var/log it could be there is a good command line log viewer available as well. maybe tail? : [http://www.faqforge.com/linux/distributions/debian/linux-how-to-view-log-files-on-the-shell/](http://www.faqforge.com/linux/distributions/debian/linux-how-to-view-log-files-on-the-shell/)

alternatively you could boot into OS the drop to console using crtl+alt+F1 (F7 to get back to desktop). while in console, desktop shouldn't crash.

then run top or better install and run htop. these should provide various system load information.

you said the CPU temp is good as well as GPU temp. so I guess you do not need lm-sensors then.

---

### Post by jesus-freak on 2016-01-05
as for the recovery mode I don't understand 80% of the instructions on that.... as for top command, I have run this before but it seems to me to be showing what is happening at the moment as it's always moving and changing. I don't really see how I could use that to check what happened yesterday at 10:00pm, the last time it froze. Anyway, I don't even know how to save the information when I run top so that I can post it here.... I opened /ver/log in nautilus and there are a bunch of text files with all kinds of information in them. Are these the logs? If so, which ones should I be looking at? There are a bunch of them. If you can tell me the specific name (or names) of the logs that I need to check, then I can copy the contents here for you to check out.

The last time it froze was on the 5th at 10:00pm. Here is the syslog for the five minutes proceeding that freeze.... My apologies, I know we are supposed to enter code in a specific way, but I no longer see the controls on here like for adding pics or code or quotes.

```
 Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: g_vfs_backend_smb_browse_init: default workgroup = 'NULL'
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: Using netbios name JUSTDREA-PC.
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: Using workgroup WORKGROUP.
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: do_mount - URI = smb://WORKGROUP/
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: do_mount - try #0
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: parsed path: fname='smb://WORKGROUP/' server='WORKGROUP' share='' path='' options=''
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: SMBC_check_options(): server='WORKGROUP' share='' path='' options=''
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: looking up cached server 'WORKGROUP'\'IPC$', user 'WORKGROUP';'justdrea'
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE:   returning (nil)
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: auth_callback - anonymous pass
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: auth_callback - out: last_user = 'justdrea', last_domain = 'WORKGROUP'
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: looking up cached server 'WORKGROUP'\'IPC$', user 'WORKGROUP';'justdrea'
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE:   returning (nil)
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
Jan  5 22:25:02 justdrea-pc org.gtk.vfs.Daemon[574]: name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_wins: WINS server resolution selected and no WINS servers listed.
Jan  5 22:25:03 justdrea-pc org.gtk.vfs.Daemon[574]: name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: Unable to create directory /var/cache/samba for file gencache.tdb. Error was Permission denied
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x20>
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x20>
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_wins: WINS server resolution selected and no WINS servers listed.
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_hosts: Attempting host lookup for name WORKGROUP<0x20>
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: resolve_hosts: getaddrinfo failed for name WORKGROUP [Name or service not known]
Jan  5 22:25:04 justdrea-pc org.gtk.vfs.Daemon[574]: name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x20>
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: do_mount - [smb://WORKGROUP/; 0] dir = (nil), cancelled = 0, errno = [111] 'Connection refused'
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: do_mount - (errno != EPERM && errno != EACCES), cancelled = 0, breaking
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: Performing aggressive shutdown.
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: ### SMB-BROWSE: purging server cache
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: Context 0x7f6abc00f470 successfully freed
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: ** (gvfsd:637): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan  5 22:25:05 justdrea-pc org.gtk.vfs.Daemon[574]: ** (process:1520): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan  5 22:27:33 justdrea-pc org.gnome.Nautilus[574]: (eog:1562): Gtk-WARNING **: Theme parsing error: gtk-contained.css:3928:61: Expected a valid selector
Jan  5 22:27:33 justdrea-pc org.gnome.Nautilus[574]: (eog:1562): EOG-WARNING **: Failed to open file '/home/justdrea/.cache/thumbnails/normal/b093a8a560895bf0562c057b6f4fb54d.png': No such file or directory
Jan  5 22:27:33 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for eog
Jan  5 22:27:33 justdrea-pc daemon/dock[610]: runtime_apps.go:298: eog Item is docked: false
Jan  5 22:27:33 justdrea-pc daemon/dock[610]: runtime_apps.go:314: eog change to dock
Jan  5 22:27:33 justdrea-pc daemon/dock[610]: manager.go:125: register entry success: dde.dock.entry.de95c7b13468496963d6716a40620dff9
Jan  5 22:27:37 justdrea-pc daemon/dock[610]: entry_manager.go:95: destroyEntry: eog
Jan  5 22:27:37 justdrea-pc daemon/dock[610]: manager.go:167: unregister entry success: dde.dock.entry.de95c7b13468496963d6716a40620dff9
Jan  5 22:27:40 justdrea-pc org.gnome.Nautilus[574]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jan  5 22:27:43 justdrea-pc org.gnome.Nautilus[574]: (eog:1575): Gtk-WARNING **: Theme parsing error: gtk-contained.css:3928:61: Expected a valid selector
Jan  5 22:27:44 justdrea-pc org.gnome.Nautilus[574]: (eog:1575): EOG-WARNING **: Failed to open file '/home/justdrea/.cache/thumbnails/normal/8895080de3388cc49d3ad608cfd50b06.png': No such file or directory
Jan  5 22:27:44 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for eog
Jan  5 22:27:44 justdrea-pc daemon/dock[610]: runtime_apps.go:298: eog Item is docked: false
Jan  5 22:27:44 justdrea-pc daemon/dock[610]: runtime_apps.go:314: eog change to dock
Jan  5 22:27:44 justdrea-pc daemon/dock[610]: manager.go:125: register entry success: dde.dock.entry.de95c7b13468496963d6716a40620dff9
Jan  5 22:27:46 justdrea-pc daemon/dock[610]: entry_manager.go:95: destroyEntry: eog
Jan  5 22:27:46 justdrea-pc daemon/dock[610]: manager.go:167: unregister entry success: dde.dock.entry.de95c7b13468496963d6716a40620dff9
Jan  5 22:27:55 justdrea-pc org.gnome.Nautilus[574]: sys:1: Warning: Source ID 2953 was not found when attempting to remove it
Jan  5 22:27:55 justdrea-pc org.gnome.Nautilus[574]: sys:1: Warning: Source ID 766 was not found when attempting to remove it
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for opera-browser
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: runtime_apps.go:583: create desktop app info for opera-browser.desktop(window id: 0x4c00001) failed:
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: runtime_apps.go:586: opera-browser using icon from X
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: runtime_apps.go:298: opera-browser Item is docked: false
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: runtime_apps.go:314: opera-browser change to dock
Jan  5 22:27:59 justdrea-pc daemon/dock[610]: manager.go:125: register entry success: dde.dock.entry.d503d0a30b94b8086a412f538cd3c4a7b
Jan  5 22:28:51 justdrea-pc org.gnome.Nautilus[574]: (nautilus:1796): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Jan  5 22:28:51 justdrea-pc org.gnome.Nautilus[574]: (nautilus:1796): Gtk-WARNING **: Theme parsing error: gtk-contained.css:3928:61: Expected a valid selector
Jan  5 22:28:51 justdrea-pc org.gnome.Nautilus[574]: Initializing nautilus-open-terminal extension
Jan  5 22:28:51 justdrea-pc org.gnome.Nautilus[574]: Initializing nautilus-dropbox 2015.10.28
Jan  5 22:28:51 justdrea-pc org.gnome.Nautilus[574]: sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded.
Jan  5 22:28:52 justdrea-pc org.gnome.Nautilus[574]: /usr/share/nautilus-python/extensions/nautilus-admin.py:18: PyGIWarning: GConf was imported without specifying a version first. Use gi.require_version('GConf', '2.0') before import to ensure that the right version gets loaded.
Jan  5 22:28:52 justdrea-pc org.gnome.Nautilus[574]: from gi.repository import Nautilus, GObject, GConf, Gtk, GLib
Jan  5 22:28:52 justdrea-pc dbus[379]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jan  5 22:28:52 justdrea-pc systemd[1]: Starting Hostname Service...
Jan  5 22:28:52 justdrea-pc dbus[379]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan  5 22:28:52 justdrea-pc systemd[1]: Started Hostname Service.
Jan  5 22:28:52 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for org.gnome.nautilus
Jan  5 22:28:52 justdrea-pc daemon/dock[610]: runtime_apps.go:298: org.gnome.nautilus Item is docked: true
Jan  5 22:28:52 justdrea-pc daemon/dock[610]: runtime_apps.go:302: org.gnome.nautilus change to undock
Jan  5 22:30:02 justdrea-pc desktop-toggle[1829]: main.go:43: Get showing desktop state failed: GetProperty: No such property '_NET_SHOWING_DESKTOP' on window d3.
Jan  5 22:30:48 justdrea-pc org.gnome.Nautilus[574]: ** (nautilus:1796): WARNING **: Could not establish a connection to Tracker: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Tracker1 was not provided by any .service files
Jan  5 22:31:38 justdrea-pc org.gnome.Nautilus[574]: (nautilus:1796): GnomeDesktop-WARNING **: Error creating thumbnail for file:///usr/share/cmake-3.4/Modules/CPack.background.png.in: Fatal error reading PNG image file: PNG file corrupted by ASCII conversion
Jan  5 22:31:38 justdrea-pc org.gnome.Nautilus[574]: (nautilus:1796): GnomeDesktop-WARNING **: Error creating thumbnail for file:///usr/share/cmake-3.4/Modules/CPack.OSXScriptLauncher.rsrc.in: Compressed icons are not supported
Jan  5 22:32:07 justdrea-pc org.gnome.Nautilus[574]: ** (nautilus:1796): WARNING **: Could not establish a connection to Tracker: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Tracker1 was not provided by any .service files
Jan  5 22:32:15 justdrea-pc org.gnome.Nautilus[574]: sys:1: Warning: Source ID 10779 was not found when attempting to remove it
Jan  5 22:32:15 justdrea-pc org.gnome.Nautilus[574]: sys:1: Warning: Source ID 19167 was not found when attempting to remove it
Jan  5 22:33:46 justdrea-pc daemon/dock[610]: traymanager.go:99: Added try icon: ""(92274709)
Jan  5 22:33:47 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for spotify
Jan  5 22:33:47 justdrea-pc daemon/dock[610]: runtime_apps.go:298: spotify Item is docked: true
Jan  5 22:33:47 justdrea-pc daemon/dock[610]: runtime_apps.go:302: spotify change to undock
Jan  5 22:34:14 justdrea-pc org.freedesktop.Notifications[574]: Notify "Spotify" "" "Two Of Us - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  5 22:34:14 justdrea-pc org.freedesktop.Notifications[574]: (deepin-notifications:2046): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  5 22:34:14 justdrea-pc org.freedesktop.Notifications[574]: (deepin-notifications:2046): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  5 22:34:16 justdrea-pc org.freedesktop.Notifications[574]: bubbleDismissed
Jan  5 22:34:37 justdrea-pc pulseaudio[597]: [alsa-sink-USB Audio] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write.
Jan  5 22:34:37 justdrea-pc pulseaudio[597]: [alsa-sink-USB Audio] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
Jan  5 22:34:37 justdrea-pc pulseaudio[597]: [alsa-sink-USB Audio] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jan  5 22:34:38 justdrea-pc pulseaudio[597]: [alsa-source-USB Audio] alsa-source.c: ALSA woke us up to read new data from the device, but there was actually nothing to read.
Jan  5 22:34:38 justdrea-pc pulseaudio[597]: [alsa-source-USB Audio] alsa-source.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
Jan  5 22:34:38 justdrea-pc pulseaudio[597]: [alsa-source-USB Audio] alsa-source.c: We were woken up with POLLIN set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jan  5 22:35:09 justdrea-pc daemon/dock[610]: traymanager.go:99: Added try icon: ""(92274709)
Jan  5 22:35:10 justdrea-pc daemon/dock[610]: runtime_apps.go:104: NewRuntimeApp for spotify
Jan  5 22:35:10 justdrea-pc daemon/dock[610]: runtime_apps.go:298: spotify Item is docked: true
Jan  5 22:35:10 justdrea-pc daemon/dock[610]: runtime_apps.go:302: spotify change to undock
Jan  5 22:35:13 justdrea-pc org.freedesktop.Notifications[574]: Notify "Spotify" "" "Two Of Us - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  5 22:35:13 justdrea-pc org.freedesktop.Notifications[574]: (deepin-notifications:2220): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  5 22:35:13 justdrea-pc org.freedesktop.Notifications[574]: (deepin-notifications:2220): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  5 22:35:17 justdrea-pc org.freedesktop.Notifications[574]: bubbleDismissed
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Jan  5 23:39:42 justdrea-pc rsyslogd
```

---

### Post by mastablasta on 2016-01-06
nothing unusual in this log. looks like 4 mins before crash all was working well.

what about dmesg? though that one shows boot messages....

daemon.log and maybe kern.log

you can just attach the .log file I think.

more on logs:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

you should also be able to see old logs (form previous session). marked with ending .log.old or something like that. you can then compare them see if there is any common lines between them upon crash. look at the final couple of lines, let's say say 10 or so.

you can check and view logs in log viewer: [http://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/](http://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/)

basically you are looking for any major error at the end or a pattern between new and older logs. let's say same application was running or was having warning when the crash occurred. 

there might also be some other logs out there worth looking at such as  the one from GPU chip and similar.

top / htop would show if any application is causing unusual load on the CPU, memory leakage (taking up more and more RAM) etc.

---

### Post by jesus-freak on 2016-01-06
Okay, it just happened again and here is the section from the same log...

```
Jan  6 16:24:16 justdrea-pc org.freedesktop.Notifications[557]: bubbleDismissed
Jan  6 16:26:32 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d431d6ddcb91c240df94fdeaf12ece59c
Jan  6 16:26:32 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: evince
Jan  6 16:26:35 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d53723716c0ccb7ff964c7dbadf1fd25e
Jan  6 16:26:35 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: wps-office-wps
Jan  6 16:26:52 justdrea-pc dbus[367]: [system] Activating service name='com.deepin.store.Api' (using servicehelper)
Jan  6 16:26:52 justdrea-pc dbus[367]: [system] Successfully activated service 'com.deepin.store.Api'
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:104: NewRuntimeApp for maxthon
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:298: maxthon Item is docked: false
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:314: maxthon change to dock
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: manager.go:125: register entry success: dde.dock.entry.d0fbd5a99c82d301232e3e4b7dfa02a8b
Jan  6 16:28:04 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d0fbd5a99c82d301232e3e4b7dfa02a8b
Jan  6 16:28:04 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: maxthon
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: Notify "Spotify" "" "Maggie Mae - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("image-data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: (deepin-notifications:4643): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: (deepin-notifications:4643): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  6 16:28:19 justdrea-pc org.freedesktop.Notifications[557]: Notify "Spotify" "" "I've Got A Feeling - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("image-data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  6 16:28:21 justdrea-pc org.freedesktop.Notifications[557]: bubbleExpired
Jan  6 16:28:22 justdrea-pc org.freedesktop.Notifications[557]: bubbleDismissed
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Jan  6 16:33:05 justdrea-pc rsyslogd: [origin software="rsyslogd" swVersion="8.15.0" x-pid="384" x-info="http://www.rsyslog.com"] start
```


#####################dmesg seems to be empty.  deamon log says############################

```
Jan  6 16:20:37 justdrea-pc dbus[367]: [system] Activating service name='com.deepin.store.Api' (using servicehelper)
Jan  6 16:20:37 justdrea-pc dbus[367]: [system] Successfully activated service 'com.deepin.store.Api'
Jan  6 16:20:38 justdrea-pc daemon/dock[594]: runtime_apps.go:104: NewRuntimeApp for google-chrome
Jan  6 16:20:38 justdrea-pc daemon/dock[594]: runtime_apps.go:298: google-chrome Item is docked: false
Jan  6 16:20:38 justdrea-pc daemon/dock[594]: runtime_apps.go:314: google-chrome change to dock
Jan  6 16:20:38 justdrea-pc daemon/dock[594]: manager.go:125: register entry success: dde.dock.entry.d6ec18dd0745fcbd73eee7d24753c13b5
Jan  6 16:21:29 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: google-chrome
Jan  6 16:21:29 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d6ec18dd0745fcbd73eee7d24753c13b5
Jan  6 16:23:46 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d0fbd5a99c82d301232e3e4b7dfa02a8b
Jan  6 16:23:46 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: maxthon
Jan  6 16:26:32 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d431d6ddcb91c240df94fdeaf12ece59c
Jan  6 16:26:32 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: evince
Jan  6 16:26:35 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d53723716c0ccb7ff964c7dbadf1fd25e
Jan  6 16:26:35 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: wps-office-wps
Jan  6 16:26:52 justdrea-pc dbus[367]: [system] Activating service name='com.deepin.store.Api' (using servicehelper)
Jan  6 16:26:52 justdrea-pc dbus[367]: [system] Successfully activated service 'com.deepin.store.Api'
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:104: NewRuntimeApp for maxthon
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:298: maxthon Item is docked: false
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: runtime_apps.go:314: maxthon change to dock
Jan  6 16:26:53 justdrea-pc daemon/dock[594]: manager.go:125: register entry success: dde.dock.entry.d0fbd5a99c82d301232e3e4b7dfa02a8b
Jan  6 16:28:04 justdrea-pc daemon/dock[594]: manager.go:167: unregister entry success: dde.dock.entry.d0fbd5a99c82d301232e3e4b7dfa02a8b
Jan  6 16:28:04 justdrea-pc daemon/dock[594]: entry_manager.go:95: destroyEntry: maxthon
Jan  6 16:33:05 justdrea-pc systemd-modules-load[195]: Inserted module 'lp'
Jan  6 16:33:05 justdrea-pc systemd-modules-load[195]: Inserted module 'ppdev'
Jan  6 16:33:05 justdrea-pc systemd[1]: Started Set Up Additional Binary Formats.
Jan  6 16:33:05 justdrea-pc systemd-modules-load[195]: Inserted module 'parport_pc'
```

##################### kern.log says....#############################

```
Jan  6 14:56:35 justdrea-pc kernel: [   11.432766] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
Jan  6 14:56:35 justdrea-pc kernel: [   11.468958] r8169 0000:02:00.0: firmware: direct-loading firmware rtl_nic/rtl8168g-2.fw
Jan  6 14:56:35 justdrea-pc kernel: [   11.508645] r8169 0000:02:00.0 enp2s0: link down
Jan  6 14:56:35 justdrea-pc kernel: [   11.508682] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
Jan  6 14:56:35 justdrea-pc kernel: [   11.508733] r8169 0000:02:00.0 enp2s0: link down
Jan  6 14:56:38 justdrea-pc kernel: [   13.962738] r8169 0000:02:00.0 enp2s0: link up
Jan  6 14:56:38 justdrea-pc kernel: [   13.962755] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
Jan  6 14:57:46 justdrea-pc kernel: [   82.578594] fuse init (API version 7.23)
Jan  6 15:57:00 justdrea-pc kernel: [ 3643.540053] perf interrupt took too long (2538 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Linux version 4.2.0-1-amd64 (debian-kernel@lists.debian.org) (gcc version 4.9.3 (Debian 4.9.3-8) ) #1 SMP Debian 4.2.6-3 (2015-12-06)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-1-amd64 root=UUID=b07b1af1-4799-425d-bb67-1d2e51cc6e53 ro splash quiet
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009efff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000020100000-0x00000000ad580fff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ad581000-0x00000000ad5b0fff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ad5b1000-0x00000000ad604fff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ad605000-0x00000000ad715fff] ACPI NVS
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ad716000-0x00000000ada21fff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ada22000-0x00000000ada7cfff] type 20
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ada7d000-0x00000000ada7dfff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ada7e000-0x00000000adabffff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000adac0000-0x00000000adc2dfff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000adc2e000-0x00000000adff9fff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000adffa000-0x00000000adffffff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] efi: EFI v2.31 by American Megatrends
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] efi:  ACPI=0xad68b000  ACPI 2.0=0xad68b000  SMBIOS=0xf04d0  MPS=0xfd4b0 
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] SMBIOS 2.8 present.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./Q1900B-ITX, BIOS P1.80 12/10/2015
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] MTRR default type: uncachable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   00000-9FFFF write-back
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   C0000-E7FFF write-through
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   E8000-FFFFF write-protect
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] MTRR variable ranges enabled:
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   1 base 080000000 mask FE0000000 write-back
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   2 base 0A0000000 mask FF0000000 write-back
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   3 base 0AE800000 mask FFF800000 uncachable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   4 base 0AF000000 mask FFF000000 uncachable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   5 base 100000000 mask FC0000000 write-back
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   6 disabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   7 disabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: update [mem 0xae800000-0xffffffff] usable ==> reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: last_pfn = 0xae000 max_arch_pfn = 0x400000000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] found SMP MP-table at [mem 0x000fd6b0-0x000fd6bf] mapped at [ffff8800000fd6b0]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f2d000, 0x01f2dfff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f2e000, 0x01f2efff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f2f000, 0x01f2ffff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f30000, 0x01f30fff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x120000000-0x13fdfffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x120000000-0x13fdfffff] page 2M
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x20100000-0xad580fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x20100000-0x201fffff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x20200000-0xad3fffff] page 2M
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0xad400000-0xad580fff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f31000, 0x01f31fff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] BRK [0x01f32000, 0x01f32fff] PGTABLE
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0xad5b1000-0xad604fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0xad5b1000-0xad604fff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0xada7d000-0xada7dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0xada7d000-0xada7dfff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0xadac0000-0xadc2dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0xadac0000-0xadc2dfff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0xadffa000-0xadffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0xadffa000-0xadffffff] page 4k
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] RAMDISK: [mem 0x33d4c000-0x35e9dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: RSDP 0x00000000AD68B000 000024 (v02 ALASKA)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: XSDT 0x00000000AD68B080 000084 (v01 ALASKA A M I    01072009 AMI  00010013)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: FACP 0x00000000AD6963D0 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/32 (20150619/tbfadt-623)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: DSDT 0x00000000AD68B1A0 00B229 (v02 ALASKA A M I    01072009 INTL 20120913)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: FACS 0x00000000AD715F80 000040
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: APIC 0x00000000AD6964E0 000084 (v03 ALASKA A M I    01072009 AMI  00010013)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: FPDT 0x00000000AD696568 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: MCFG 0x00000000AD6965B0 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: LPIT 0x00000000AD6965F0 000104 (v01 ALASKA A M I    00000003 VLV2 0100000D)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: AAFT 0x00000000AD6966F8 0000D7 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: HPET 0x00000000AD6967D0 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: SSDT 0x00000000AD696808 000763 (v01 PmRef  CpuPm    00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: SSDT 0x00000000AD696F70 000290 (v01 PmRef  Cpu0Tst  00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: SSDT 0x00000000AD697200 00017A (v01 PmRef  ApTst    00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: UEFI 0x00000000AD697380 000042 (v01 ALASKA A M I    00000000      00000000)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: BGRT 0x00000000AD6973C8 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] No NUMA configuration found
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x13fff6000-0x13fff9fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013ba00000-ffff88013f5fffff] on node 0
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Zone ranges:
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000013fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Movable zone start for each node
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Early memory node ranges
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x000000000009f000-0x000000000009ffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x0000000020100000-0x00000000ad580fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x00000000ad5b1000-0x00000000ad604fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x00000000ada7d000-0x00000000ada7dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x00000000adac0000-0x00000000adc2dfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x00000000adffa000-0x00000000adffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000013fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000013fffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] On node 0 totalpages: 972264
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA zone: 25 pages reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA32 zone: 11034 pages used for memmap
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   DMA32 zone: 706122 pages, LIFO batch:31
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   Normal zone: 4096 pages used for memmap
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000]   Normal zone: 262144 pages, LIFO batch:31
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] x86/hpet: Will disable the HPET for this platform because it's not reliable
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xaf000000-0xbeffffff
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high dfl lint[0x7d])
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] res edge lint[0xbe])
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x77])
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] low level lint[0x15])
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: NMI not connected to LINT 1!
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-86
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xad581000-0xad5b0fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xad605000-0xad715fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xad716000-0xada21fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xada22000-0xada7cfff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xada7e000-0xadabffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xadc2e000-0xadff9fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xae000000-0xaeffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xaf000000-0xbeffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbf000000-0xe00f7fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xffafffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] e820: [mem 0xbf000000-0xe00f7fff] available for PCI devices
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:4 nr_node_ids:1
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PERCPU: Embedded 32 pages/cpu @ffff88013fc00000 s92696 r8192 d30184 u524288
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] pcpu-alloc: s92696 r8192 d30184 u524288 alloc=1*2097152
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 957045
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Policy zone: Normal
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-1-amd64 root=UUID=b07b1af1-4799-425d-bb67-1d2e51cc6e53 ro splash quiet
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Memory: 3480456K/3889056K available (5479K kernel code, 1095K rwdata, 2748K rodata, 1292K init, 832K bss, 408600K reserved, 0K cma-reserved)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Hierarchical RCU implementation.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] 	Build-time adjustment of leaf fanout to 64.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=512 to nr_cpu_ids=4.
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] NR_IRQS:33024 nr_irqs:1024 16
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Console: colour dummy device 80x25
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] console [tty0] enabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Maximum core-clock to bus-clock ratio: 0x18
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] Resolved frequency ID: 0, frequency: 83200 KHz
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] TSC runs at 1996800 KHz
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] lapic_timer_frequency = 332800
Jan  6 16:33:05 justdrea-pc kernel: [    0.000000] tsc: Detected 1996.800 MHz processor
Jan  6 16:33:05 justdrea-pc kernel: [    0.000036] Calibrating delay loop (skipped), value calculated using timer frequency.. 3993.60 BogoMIPS (lpj=7987200)
Jan  6 16:33:05 justdrea-pc kernel: [    0.000041] pid_max: default: 32768 minimum: 301
Jan  6 16:33:05 justdrea-pc kernel: [    0.000057] ACPI: Core revision 20150619
Jan  6 16:33:05 justdrea-pc kernel: [    0.022620] ACPI: All ACPI Tables successfully acquired
Jan  6 16:33:05 justdrea-pc kernel: [    0.024752] Security Framework initialized
Jan  6 16:33:05 justdrea-pc kernel: [    0.024759] AppArmor: AppArmor disabled by boot time parameter
Jan  6 16:33:05 justdrea-pc kernel: [    0.024762] Yama: disabled by default; enable with sysctl kernel.yama.*
Jan  6 16:33:05 justdrea-pc kernel: [    0.025274] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.027179] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.028060] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.028079] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.028488] Initializing cgroup subsys blkio
Jan  6 16:33:05 justdrea-pc kernel: [    0.028497] Initializing cgroup subsys memory
Jan  6 16:33:05 justdrea-pc kernel: [    0.028511] Initializing cgroup subsys devices
Jan  6 16:33:05 justdrea-pc kernel: [    0.028518] Initializing cgroup subsys freezer
Jan  6 16:33:05 justdrea-pc kernel: [    0.028524] Initializing cgroup subsys net_cls
Jan  6 16:33:05 justdrea-pc kernel: [    0.028531] Initializing cgroup subsys perf_event
Jan  6 16:33:05 justdrea-pc kernel: [    0.028538] Initializing cgroup subsys net_prio
Jan  6 16:33:05 justdrea-pc kernel: [    0.028574] CPU: Physical Processor ID: 0
Jan  6 16:33:05 justdrea-pc kernel: [    0.028578] CPU: Processor Core ID: 0
Jan  6 16:33:05 justdrea-pc kernel: [    0.028583] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Jan  6 16:33:05 justdrea-pc kernel: [    0.028586] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Jan  6 16:33:05 justdrea-pc kernel: [    0.033361] mce: CPU supports 6 MCE banks
Jan  6 16:33:05 justdrea-pc kernel: [    0.033372] CPU0: Thermal monitoring enabled (TM1)
Jan  6 16:33:05 justdrea-pc kernel: [    0.033377] process: using mwait in idle threads
Jan  6 16:33:05 justdrea-pc kernel: [    0.033383] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
Jan  6 16:33:05 justdrea-pc kernel: [    0.033386] Last level dTLB entries: 4KB 128, 2MB 16, 4MB 16, 1GB 0
Jan  6 16:33:05 justdrea-pc kernel: [    0.033695] Freeing SMP alternatives memory: 20K (ffffffff81c56000 - ffffffff81c5b000)
Jan  6 16:33:05 justdrea-pc kernel: [    0.054895] ftrace: allocating 23178 entries in 91 pages
Jan  6 16:33:05 justdrea-pc kernel: [    0.067177] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Jan  6 16:33:05 justdrea-pc kernel: [    0.106899] TSC deadline timer enabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.106905] smpboot: CPU0: Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz (fam: 06, model: 37, stepping: 08)
Jan  6 16:33:05 justdrea-pc kernel: [    0.106944] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
Jan  6 16:33:05 justdrea-pc kernel: [    0.106959] ... version:                3
Jan  6 16:33:05 justdrea-pc kernel: [    0.106962] ... bit width:              40
Jan  6 16:33:05 justdrea-pc kernel: [    0.106963] ... generic registers:      2
Jan  6 16:33:05 justdrea-pc kernel: [    0.106966] ... value mask:             000000ffffffffff
Jan  6 16:33:05 justdrea-pc kernel: [    0.106968] ... max period:             000000ffffffffff
Jan  6 16:33:05 justdrea-pc kernel: [    0.106969] ... fixed-purpose events:   3
Jan  6 16:33:05 justdrea-pc kernel: [    0.106971] ... event mask:             0000000700000003
Jan  6 16:33:05 justdrea-pc kernel: [    0.108078] x86: Booting SMP configuration:
Jan  6 16:33:05 justdrea-pc kernel: [    0.108083] .... node  #0, CPUs:      #1
Jan  6 16:33:05 justdrea-pc kernel: [    0.116155] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan  6 16:33:05 justdrea-pc kernel: [    0.116388]  #2 #3
Jan  6 16:33:05 justdrea-pc kernel: [    0.132396] x86: Booted up 1 node, 4 CPUs
Jan  6 16:33:05 justdrea-pc kernel: [    0.132401] smpboot: Total of 4 processors activated (15974.40 BogoMIPS)
Jan  6 16:33:05 justdrea-pc kernel: [    0.133395] devtmpfs: initialized
Jan  6 16:33:05 justdrea-pc kernel: [    0.140826] PM: Registering ACPI NVS region [mem 0xad605000-0xad715fff] (1118208 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.141076] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Jan  6 16:33:05 justdrea-pc kernel: [    0.141312] pinctrl core: initialized pinctrl subsystem
Jan  6 16:33:05 justdrea-pc kernel: [    0.141655] NET: Registered protocol family 16
Jan  6 16:33:05 justdrea-pc kernel: [    0.152418] cpuidle: using governor ladder
Jan  6 16:33:05 justdrea-pc kernel: [    0.164437] cpuidle: using governor menu
Jan  6 16:33:05 justdrea-pc kernel: [    0.164624] ACPI: bus type PCI registered
Jan  6 16:33:05 justdrea-pc kernel: [    0.164629] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jan  6 16:33:05 justdrea-pc kernel: [    0.164788] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  6 16:33:05 justdrea-pc kernel: [    0.164792] PCI: not using MMCONFIG
Jan  6 16:33:05 justdrea-pc kernel: [    0.164795] PCI: Using configuration type 1 for base access
Jan  6 16:33:05 justdrea-pc kernel: [    0.177387] ACPI: Added _OSI(Module Device)
Jan  6 16:33:05 justdrea-pc kernel: [    0.177393] ACPI: Added _OSI(Processor Device)
Jan  6 16:33:05 justdrea-pc kernel: [    0.177397] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan  6 16:33:05 justdrea-pc kernel: [    0.177401] ACPI: Added _OSI(Processor Aggregator Device)
Jan  6 16:33:05 justdrea-pc kernel: [    0.192414] ACPI: Dynamic OEM Table Load:
Jan  6 16:33:05 justdrea-pc kernel: [    0.192426] ACPI: SSDT 0xFFFF88013AA6D000 0003D7 (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.193554] ACPI: Dynamic OEM Table Load:
Jan  6 16:33:05 justdrea-pc kernel: [    0.193563] ACPI: SSDT 0xFFFF88013AA68C00 0003DE (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.195146] ACPI: Dynamic OEM Table Load:
Jan  6 16:33:05 justdrea-pc kernel: [    0.195155] ACPI: SSDT 0xFFFF88013AA9FE00 00015F (v01 PmRef  ApIst    00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.196224] ACPI: Dynamic OEM Table Load:
Jan  6 16:33:05 justdrea-pc kernel: [    0.196232] ACPI: SSDT 0xFFFF88013AA74400 00008D (v01 PmRef  ApCst    00003000 INTL 20061109)
Jan  6 16:33:05 justdrea-pc kernel: [    0.198896] ACPI: Interpreter enabled
Jan  6 16:33:05 justdrea-pc kernel: [    0.198912] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
Jan  6 16:33:05 justdrea-pc kernel: [    0.198922] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
Jan  6 16:33:05 justdrea-pc kernel: [    0.198952] ACPI: (supports S0 S3 S4 S5)
Jan  6 16:33:05 justdrea-pc kernel: [    0.198955] ACPI: Using IOAPIC for interrupt routing
Jan  6 16:33:05 justdrea-pc kernel: [    0.199088] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan  6 16:33:05 justdrea-pc kernel: [    0.200450] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jan  6 16:33:05 justdrea-pc kernel: [    0.200519] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan  6 16:33:05 justdrea-pc kernel: [    0.212483] ACPI: Power Resource [USBC] (on)
Jan  6 16:33:05 justdrea-pc kernel: [    0.214561] ACPI: Power Resource [PLPE] (on)
Jan  6 16:33:05 justdrea-pc kernel: [    0.214975] ACPI: Power Resource [PLPE] (on)
Jan  6 16:33:05 justdrea-pc kernel: [    0.224945] ACPI: Power Resource [CLK0] (on)
Jan  6 16:33:05 justdrea-pc kernel: [    0.225042] ACPI: Power Resource [CLK1] (on)
Jan  6 16:33:05 justdrea-pc kernel: [    0.299837] ACPI: Power Resource [FN00] (off)
Jan  6 16:33:05 justdrea-pc kernel: [    0.301039] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  6 16:33:05 justdrea-pc kernel: [    0.301050] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jan  6 16:33:05 justdrea-pc kernel: [    0.301363] \_SB_.PCI0:_OSC invalid UUID
Jan  6 16:33:05 justdrea-pc kernel: [    0.301366] _OSC request data:1 1f 0 
Jan  6 16:33:05 justdrea-pc kernel: [    0.301374] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Jan  6 16:33:05 justdrea-pc kernel: [    0.302134] PCI host bridge to bus 0000:00
Jan  6 16:33:05 justdrea-pc kernel: [    0.302141] pci_bus 0000:00: root bus resource [bus 00-ff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302146] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302150] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302154] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302158] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302162] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302166] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302170] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302174] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xd0716ffe window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302187] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
Jan  6 16:33:05 justdrea-pc kernel: [    0.302402] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
Jan  6 16:33:05 justdrea-pc kernel: [    0.302423] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302436] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302448] pci 0000:00:02.0: reg 0x20: [io  0xf080-0xf087]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302661] pci 0000:00:13.0: [8086:0f23] type 00 class 0x010601
Jan  6 16:33:05 justdrea-pc kernel: [    0.302690] pci 0000:00:13.0: reg 0x10: [io  0xf070-0xf077]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302701] pci 0000:00:13.0: reg 0x14: [io  0xf060-0xf063]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302712] pci 0000:00:13.0: reg 0x18: [io  0xf050-0xf057]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302723] pci 0000:00:13.0: reg 0x1c: [io  0xf040-0xf043]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302733] pci 0000:00:13.0: reg 0x20: [io  0xf020-0xf03f]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302744] pci 0000:00:13.0: reg 0x24: [mem 0xd0716000-0xd07167ff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.302780] pci 0000:00:13.0: PME# supported from D3hot
Jan  6 16:33:05 justdrea-pc kernel: [    0.302968] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
Jan  6 16:33:05 justdrea-pc kernel: [    0.302997] pci 0000:00:14.0: reg 0x10: [mem 0xd0700000-0xd070ffff 64bit]
Jan  6 16:33:05 justdrea-pc kernel: [    0.303050] pci 0000:00:14.0: PME# supported from D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.303185] pci 0000:00:14.0: System wakeup disabled by ACPI
Jan  6 16:33:05 justdrea-pc kernel: [    0.303287] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
Jan  6 16:33:05 justdrea-pc kernel: [    0.303328] pci 0000:00:1a.0: reg 0x10: [mem 0xd0500000-0xd05fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.303343] pci 0000:00:1a.0: reg 0x14: [mem 0xd0400000-0xd04fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.303429] pci 0000:00:1a.0: PME# supported from D0 D3hot
Jan  6 16:33:05 justdrea-pc kernel: [    0.303619] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
Jan  6 16:33:05 justdrea-pc kernel: [    0.303653] pci 0000:00:1b.0: reg 0x10: [mem 0xd0710000-0xd0713fff 64bit]
Jan  6 16:33:05 justdrea-pc kernel: [    0.303715] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.303901] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
Jan  6 16:33:05 justdrea-pc kernel: [    0.303962] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.304150] pci 0000:00:1c.1: [8086:0f4a] type 01 class 0x060400
Jan  6 16:33:05 justdrea-pc kernel: [    0.304211] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.304398] pci 0000:00:1c.2: [8086:0f4c] type 01 class 0x060400
Jan  6 16:33:05 justdrea-pc kernel: [    0.304459] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.304645] pci 0000:00:1c.3: [8086:0f4e] type 01 class 0x060400
Jan  6 16:33:05 justdrea-pc kernel: [    0.304715] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.304908] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
Jan  6 16:33:05 justdrea-pc kernel: [    0.305155] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
Jan  6 16:33:05 justdrea-pc kernel: [    0.305205] pci 0000:00:1f.3: reg 0x10: [mem 0xd0714000-0xd071401f]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305278] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305609] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305732] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Jan  6 16:33:05 justdrea-pc kernel: [    0.305775] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305805] pci 0000:02:00.0: reg 0x18: [mem 0xd0604000-0xd0604fff 64bit]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305824] pci 0000:02:00.0: reg 0x20: [mem 0xd0600000-0xd0603fff 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.305891] pci 0000:02:00.0: supports D1 D2
Jan  6 16:33:05 justdrea-pc kernel: [    0.305895] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  6 16:33:05 justdrea-pc kernel: [    0.305950] pci 0000:02:00.0: System wakeup disabled by ACPI
Jan  6 16:33:05 justdrea-pc kernel: [    0.312709] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jan  6 16:33:05 justdrea-pc kernel: [    0.312719] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.312726] pci 0000:00:1c.1:   bridge window [mem 0xd0600000-0xd06fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.312850] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jan  6 16:33:05 justdrea-pc kernel: [    0.312955] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jan  6 16:33:05 justdrea-pc kernel: [    0.314243] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.314382] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 *11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.314520] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.314656] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.314794] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.314931] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Jan  6 16:33:05 justdrea-pc kernel: [    0.315069] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.315210] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
Jan  6 16:33:05 justdrea-pc kernel: [    0.317854] ACPI: Enabled 6 GPEs in block 00 to 3F
Jan  6 16:33:05 justdrea-pc kernel: [    0.318102] vgaarb: setting as boot device: PCI:0000:00:02.0
Jan  6 16:33:05 justdrea-pc kernel: [    0.318107] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan  6 16:33:05 justdrea-pc kernel: [    0.318113] vgaarb: loaded
Jan  6 16:33:05 justdrea-pc kernel: [    0.318116] vgaarb: bridge control possible 0000:00:02.0
Jan  6 16:33:05 justdrea-pc kernel: [    0.318535] PCI: Using ACPI for IRQ routing
Jan  6 16:33:05 justdrea-pc kernel: [    0.324490] PCI: pci_cache_line_size set to 64 bytes
Jan  6 16:33:05 justdrea-pc kernel: [    0.324537] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324541] e820: reserve RAM buffer [mem 0xad581000-0xafffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324545] e820: reserve RAM buffer [mem 0xad605000-0xafffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324548] e820: reserve RAM buffer [mem 0xada7e000-0xafffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324551] e820: reserve RAM buffer [mem 0xadc2e000-0xafffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324554] e820: reserve RAM buffer [mem 0xae000000-0xafffffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.324888] clocksource: Switched to clocksource refined-jiffies
Jan  6 16:33:05 justdrea-pc kernel: [    0.337293] pnp: PnP ACPI init
Jan  6 16:33:05 justdrea-pc kernel: [    0.337413] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.337671] system 00:01: [io  0x0680-0x069f] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.337677] system 00:01: [io  0x0400-0x047f] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.337681] system 00:01: [io  0x0500-0x05fe] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.337688] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.337896] system 00:02: [io  0x0290-0x029f] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.337904] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.338540] pnp 00:03: [dma 3]
Jan  6 16:33:05 justdrea-pc kernel: [    0.338777] pnp 00:03: Plug and Play ACPI device, IDs PNP0400 PNP0401 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.339146] pnp 00:04: [dma 0 disabled]
Jan  6 16:33:05 justdrea-pc kernel: [    0.339256] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.339668] pnp 00:05: [dma 0 disabled]
Jan  6 16:33:05 justdrea-pc kernel: [    0.339777] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.340253] system 00:06: [mem 0xe0000000-0xefffffff] could not be reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340259] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340264] system 00:06: [mem 0xfed03000-0xfed03fff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340268] system 00:06: [mem 0xfed04000-0xfed04fff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340275] system 00:06: [mem 0xfed0c000-0xfed0ffff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340280] system 00:06: [mem 0xfed08000-0xfed08fff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340285] system 00:06: [mem 0xfed1c000-0xfed1cfff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340289] system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340294] system 00:06: [mem 0xfef00000-0xfeffffff] has been reserved
Jan  6 16:33:05 justdrea-pc kernel: [    0.340300] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan  6 16:33:05 justdrea-pc kernel: [    0.342628] pnp: PnP ACPI: found 7 devices
Jan  6 16:33:05 justdrea-pc kernel: [    0.352589] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Jan  6 16:33:05 justdrea-pc kernel: [    0.352619] clocksource: Switched to clocksource acpi_pm
Jan  6 16:33:05 justdrea-pc kernel: [    0.352643] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352650] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352655] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352667] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352683] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352688] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352693] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352703] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352708] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352713] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000 add_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352732] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352737] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352742] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352746] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352751] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352755] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352760] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352764] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352769] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352775] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352780] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352810] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352815] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352819] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352824] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352828] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352832] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352837] pci 0000:00:1c.2: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352841] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352845] pci 0000:00:1c.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jan  6 16:33:05 justdrea-pc kernel: [    0.352856] pci 0000:00:1c.0: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352860] pci 0000:00:1c.0: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352873] pci 0000:00:1c.0: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352877] pci 0000:00:1c.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352887] pci 0000:00:1c.1: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352891] pci 0000:00:1c.1: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352898] pci 0000:00:1c.2: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352902] pci 0000:00:1c.2: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352911] pci 0000:00:1c.2: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352915] pci 0000:00:1c.2: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352921] pci 0000:00:1c.3: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352925] pci 0000:00:1c.3: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352934] pci 0000:00:1c.3: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352938] pci 0000:00:1c.3: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352945] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352951] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352956] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352965] pci 0000:00:1c.3: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352969] pci 0000:00:1c.3: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352979] pci 0000:00:1c.3: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352983] pci 0000:00:1c.3: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352989] pci 0000:00:1c.2: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.352993] pci 0000:00:1c.2: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353002] pci 0000:00:1c.2: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353006] pci 0000:00:1c.2: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353015] pci 0000:00:1c.1: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353019] pci 0000:00:1c.1: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353025] pci 0000:00:1c.0: BAR 14: no space for [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353029] pci 0000:00:1c.0: BAR 14: failed to assign [mem size 0x00200000]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353038] pci 0000:00:1c.0: BAR 15: no space for [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353042] pci 0000:00:1c.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353047] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353052] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353063] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353068] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353074] pci 0000:00:1c.1:   bridge window [mem 0xd0600000-0xd06fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353082] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353086] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353097] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353101] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353112] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353117] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353120] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353124] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353128] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353132] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353136] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353140] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xd0716ffe window]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353144] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353148] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353152] pci_bus 0000:02: resource 1 [mem 0xd0600000-0xd06fffff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353156] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353160] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Jan  6 16:33:05 justdrea-pc kernel: [    0.353310] NET: Registered protocol family 2
Jan  6 16:33:05 justdrea-pc kernel: [    0.353641] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.353789] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.353946] TCP: Hash tables configured (established 32768 bind 32768)
Jan  6 16:33:05 justdrea-pc kernel: [    0.354015] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.354057] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    0.354239] NET: Registered protocol family 1
Jan  6 16:33:05 justdrea-pc kernel: [    0.354278] pci 0000:00:02.0: Video device with shadowed ROM
Jan  6 16:33:05 justdrea-pc kernel: [    0.354631] PCI: CLS 64 bytes, default 64
Jan  6 16:33:05 justdrea-pc kernel: [    0.354742] Unpacking initramfs...
Jan  6 16:33:05 justdrea-pc kernel: [    1.241949] Freeing initrd memory: 34120K (ffff880033d4c000 - ffff880035e9e000)
Jan  6 16:33:05 justdrea-pc kernel: [    1.241993] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan  6 16:33:05 justdrea-pc kernel: [    1.241998] software IO TLB [mem 0x9b0e6000-0x9f0e6000] (64MB) mapped at [ffff88009b0e6000-ffff88009f0e5fff]
Jan  6 16:33:05 justdrea-pc kernel: [    1.242234] microcode: CPU0 sig=0x30678, pf=0x4, revision=0x831
Jan  6 16:33:05 justdrea-pc kernel: [    1.242251] microcode: CPU1 sig=0x30678, pf=0x4, revision=0x831
Jan  6 16:33:05 justdrea-pc kernel: [    1.242270] microcode: CPU2 sig=0x30678, pf=0x4, revision=0x831
Jan  6 16:33:05 justdrea-pc kernel: [    1.242288] microcode: CPU3 sig=0x30678, pf=0x4, revision=0x831
Jan  6 16:33:05 justdrea-pc kernel: [    1.242459] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan  6 16:33:05 justdrea-pc kernel: [    1.242815] simple-framebuffer simple-framebuffer.0: framebuffer at 0xc0000000, 0x300000 bytes, mapped to 0xffffc90000800000
Jan  6 16:33:05 justdrea-pc kernel: [    1.242821] simple-framebuffer simple-framebuffer.0: format=a8r8g8b8, mode=1024x768x32, linelength=4096
Jan  6 16:33:05 justdrea-pc kernel: [    1.247868] Console: switching to colour frame buffer device 128x48
Jan  6 16:33:05 justdrea-pc kernel: [    1.252695] simple-framebuffer simple-framebuffer.0: fb0: simplefb registered!
Jan  6 16:33:05 justdrea-pc kernel: [    1.253328] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    1.253398] audit: initializing netlink subsys (disabled)
Jan  6 16:33:05 justdrea-pc kernel: [    1.253432] audit: type=2000 audit(1452069171.243:1): initialized
Jan  6 16:33:05 justdrea-pc kernel: [    1.254039] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  6 16:33:05 justdrea-pc kernel: [    1.254100] zpool: loaded
Jan  6 16:33:05 justdrea-pc kernel: [    1.254108] zbud: loaded
Jan  6 16:33:05 justdrea-pc kernel: [    1.254441] VFS: Disk quotas dquot_6.6.0
Jan  6 16:33:05 justdrea-pc kernel: [    1.254483] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan  6 16:33:05 justdrea-pc kernel: [    1.255502] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 250)
Jan  6 16:33:05 justdrea-pc kernel: [    1.255605] io scheduler noop registered
Jan  6 16:33:05 justdrea-pc kernel: [    1.255611] io scheduler deadline registered
Jan  6 16:33:05 justdrea-pc kernel: [    1.255645] io scheduler cfq registered (default)
Jan  6 16:33:05 justdrea-pc kernel: [    1.256520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  6 16:33:05 justdrea-pc kernel: [    1.256540] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  6 16:33:05 justdrea-pc kernel: [    1.256590] intel_idle: MWAIT substates: 0x33000020
Jan  6 16:33:05 justdrea-pc kernel: [    1.256593] intel_idle: v0.4 model 0x37
Jan  6 16:33:05 justdrea-pc kernel: [    1.256596] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan  6 16:33:05 justdrea-pc kernel: [    1.257052] GHES: HEST is not enabled!
Jan  6 16:33:05 justdrea-pc kernel: [    1.257209] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan  6 16:33:05 justdrea-pc kernel: [    1.277816] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Jan  6 16:33:05 justdrea-pc kernel: [    1.298573] 00:05: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
Jan  6 16:33:05 justdrea-pc kernel: [    1.299526] hpet: number irqs doesn't agree with number of timers
Jan  6 16:33:05 justdrea-pc kernel: [    1.299569] Linux agpgart interface v0.103
Jan  6 16:33:05 justdrea-pc kernel: [    1.299675] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
Jan  6 16:33:05 justdrea-pc kernel: [    1.299678] AMD IOMMUv2 functionality not available on this system
Jan  6 16:33:05 justdrea-pc kernel: [    1.300437] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jan  6 16:33:05 justdrea-pc kernel: [    1.303189] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  6 16:33:05 justdrea-pc kernel: [    1.303201] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan  6 16:33:05 justdrea-pc kernel: [    1.304118] mousedev: PS/2 mouse device common for all mice
Jan  6 16:33:05 justdrea-pc kernel: [    1.304236] rtc_cmos 00:00: RTC can wake from S4
Jan  6 16:33:05 justdrea-pc kernel: [    1.304903] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Jan  6 16:33:05 justdrea-pc kernel: [    1.304933] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram
Jan  6 16:33:05 justdrea-pc kernel: [    1.304959] Intel P-state driver initializing.
Jan  6 16:33:05 justdrea-pc kernel: [    1.305393] ledtrig-cpu: registered to indicate activity on CPUs
Jan  6 16:33:05 justdrea-pc kernel: [    1.306336] NET: Registered protocol family 10
Jan  6 16:33:05 justdrea-pc kernel: [    1.307409] mip6: Mobile IPv6
Jan  6 16:33:05 justdrea-pc kernel: [    1.307420] NET: Registered protocol family 17
Jan  6 16:33:05 justdrea-pc kernel: [    1.307435] mpls_gso: MPLS GSO support
Jan  6 16:33:05 justdrea-pc kernel: [    1.310663] registered taskstats version 1
Jan  6 16:33:05 justdrea-pc kernel: [    1.310703] zswap: loading zswap
Jan  6 16:33:05 justdrea-pc kernel: [    1.310711] zswap: using zbud pool
Jan  6 16:33:05 justdrea-pc kernel: [    1.310720] zswap: using lzo compressor
Jan  6 16:33:05 justdrea-pc kernel: [    1.313275] rtc_cmos 00:00: setting system clock to 2016-01-06 08:32:52 UTC (1452069172)
Jan  6 16:33:05 justdrea-pc kernel: [    1.313548] PM: Hibernation image not present or could not be loaded.
Jan  6 16:33:05 justdrea-pc kernel: [    1.314935] Freeing unused kernel memory: 1292K (ffffffff81b13000 - ffffffff81c56000)
Jan  6 16:33:05 justdrea-pc kernel: [    1.314941] Write protecting the kernel read-only data: 10240k
Jan  6 16:33:05 justdrea-pc kernel: [    1.317383] Freeing unused kernel memory: 652K (ffff88000175d000 - ffff880001800000)
Jan  6 16:33:05 justdrea-pc kernel: [    1.318799] Freeing unused kernel memory: 1348K (ffff880001aaf000 - ffff880001c00000)
Jan  6 16:33:05 justdrea-pc kernel: [    1.353584] random: systemd-udevd urandom read with 2 bits of entropy available
Jan  6 16:33:05 justdrea-pc kernel: [    1.400319] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
Jan  6 16:33:05 justdrea-pc kernel: [    1.400328] ACPI: Power Button [PWRB]
Jan  6 16:33:05 justdrea-pc kernel: [    1.400435] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input3
Jan  6 16:33:05 justdrea-pc kernel: [    1.400440] ACPI: Sleep Button [SLPB]
Jan  6 16:33:05 justdrea-pc kernel: [    1.400540] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
Jan  6 16:33:05 justdrea-pc kernel: [    1.400545] ACPI: Power Button [PWRF]
Jan  6 16:33:05 justdrea-pc kernel: [    1.402620] sdhci: Secure Digital Host Controller Interface driver
Jan  6 16:33:05 justdrea-pc kernel: [    1.402626] sdhci: Copyright(c) Pierre Ossman
Jan  6 16:33:05 justdrea-pc kernel: [    1.407469] hidraw: raw HID events driver (C) Jiri Kosina
Jan  6 16:33:05 justdrea-pc kernel: [    1.429861] thermal LNXTHERM:00: registered as thermal_zone0
Jan  6 16:33:05 justdrea-pc kernel: [    1.429867] ACPI: Thermal Zone [TZ01] (27 C)
Jan  6 16:33:05 justdrea-pc kernel: [    1.432501] SCSI subsystem initialized
Jan  6 16:33:05 justdrea-pc kernel: [    1.433795] ACPI: bus type USB registered
Jan  6 16:33:05 justdrea-pc kernel: [    1.433847] usbcore: registered new interface driver usbfs
Jan  6 16:33:05 justdrea-pc kernel: [    1.433868] usbcore: registered new interface driver hub
Jan  6 16:33:05 justdrea-pc kernel: [    1.433923] usbcore: registered new device driver usb
Jan  6 16:33:05 justdrea-pc kernel: [    1.434486] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan  6 16:33:05 justdrea-pc kernel: [    1.434508] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jan  6 16:33:05 justdrea-pc kernel: [    1.436025] libata version 3.00 loaded.
Jan  6 16:33:05 justdrea-pc kernel: [    1.436587] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan  6 16:33:05 justdrea-pc kernel: [    1.436606] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Jan  6 16:33:05 justdrea-pc kernel: [    1.437040] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
Jan  6 16:33:05 justdrea-pc kernel: [    1.437050] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Jan  6 16:33:05 justdrea-pc kernel: [    1.437220] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan  6 16:33:05 justdrea-pc kernel: [    1.437224] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 16:33:05 justdrea-pc kernel: [    1.437227] usb usb1: Product: xHCI Host Controller
Jan  6 16:33:05 justdrea-pc kernel: [    1.437230] usb usb1: Manufacturer: Linux 4.2.0-1-amd64 xhci-hcd
Jan  6 16:33:05 justdrea-pc kernel: [    1.437233] usb usb1: SerialNumber: 0000:00:14.0
Jan  6 16:33:05 justdrea-pc kernel: [    1.437675] hub 1-0:1.0: USB hub found
Jan  6 16:33:05 justdrea-pc kernel: [    1.437693] hub 1-0:1.0: 6 ports detected
Jan  6 16:33:05 justdrea-pc kernel: [    1.438439] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan  6 16:33:05 justdrea-pc kernel: [    1.438447] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Jan  6 16:33:05 justdrea-pc kernel: [    1.438512] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Jan  6 16:33:05 justdrea-pc kernel: [    1.438516] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  6 16:33:05 justdrea-pc kernel: [    1.438519] usb usb2: Product: xHCI Host Controller
Jan  6 16:33:05 justdrea-pc kernel: [    1.438521] usb usb2: Manufacturer: Linux 4.2.0-1-amd64 xhci-hcd
Jan  6 16:33:05 justdrea-pc kernel: [    1.438524] usb usb2: SerialNumber: 0000:00:14.0
Jan  6 16:33:05 justdrea-pc kernel: [    1.438844] hub 2-0:1.0: USB hub found
Jan  6 16:33:05 justdrea-pc kernel: [    1.438858] hub 2-0:1.0: 1 port detected
Jan  6 16:33:05 justdrea-pc kernel: [    1.439085] ahci 0000:00:13.0: version 3.0
Jan  6 16:33:05 justdrea-pc kernel: [    1.439233] ahci 0000:00:13.0: controller can't do DEVSLP, turning off
Jan  6 16:33:05 justdrea-pc kernel: [    1.440288] [drm] Initialized drm 1.1.0 20060810
Jan  6 16:33:05 justdrea-pc kernel: [    1.443873] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc9000064a000, d0:50:99:38:de:f7, XID 0c000800 IRQ 89
Jan  6 16:33:05 justdrea-pc kernel: [    1.443880] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jan  6 16:33:05 justdrea-pc kernel: [    1.454834] ahci 0000:00:13.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x1 impl SATA mode
Jan  6 16:33:05 justdrea-pc kernel: [    1.454841] ahci 0000:00:13.0: flags: 64bit ncq led clo pio slum part deso 
Jan  6 16:33:05 justdrea-pc kernel: [    1.455911] scsi host0: ahci
Jan  6 16:33:05 justdrea-pc kernel: [    1.456584] scsi host1: ahci
Jan  6 16:33:05 justdrea-pc kernel: [    1.456686] ata1: SATA max UDMA/133 abar m2048@0xd0716000 port 0xd0716100 irq 88
Jan  6 16:33:05 justdrea-pc kernel: [    1.456690] ata2: DUMMY
Jan  6 16:33:05 justdrea-pc kernel: [    1.458288] [drm] Memory usable by graphics device = 2048M
Jan  6 16:33:05 justdrea-pc kernel: [    1.458295] checking generic (c0000000 300000) vs hw (c0000000 10000000)
Jan  6 16:33:05 justdrea-pc kernel: [    1.458297] fb: switching to inteldrmfb from simple
Jan  6 16:33:05 justdrea-pc kernel: [    1.458332] Console: switching to colour dummy device 80x25
Jan  6 16:33:05 justdrea-pc kernel: [    1.458630] [drm] Replacing VGA console driver
Jan  6 16:33:05 justdrea-pc kernel: [    1.459584] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan  6 16:33:05 justdrea-pc kernel: [    1.459588] [drm] Driver supports precise vblank timestamp query.
Jan  6 16:33:05 justdrea-pc kernel: [    1.483051] r8169 0000:02:00.0 enp2s0: renamed from eth0
Jan  6 16:33:05 justdrea-pc kernel: [    1.498017] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan  6 16:33:05 justdrea-pc kernel: [    1.529070] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan  6 16:33:05 justdrea-pc kernel: [    1.529907] acpi device:09: registered as cooling_device1
Jan  6 16:33:05 justdrea-pc kernel: [    1.530020] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Jan  6 16:33:05 justdrea-pc kernel: [    1.530076] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
Jan  6 16:33:05 justdrea-pc kernel: [    1.555560] fbcon: inteldrmfb (fb0) is primary device
Jan  6 16:33:05 justdrea-pc kernel: [    1.747620] usb 1-1: new full-speed USB device number 2 using xhci_hcd
Jan  6 16:33:05 justdrea-pc kernel: [    1.775749] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  6 16:33:05 justdrea-pc kernel: [    1.777698] ata1.00: ATA-8: Hitachi HUA722050CLA330, JP2OA3MA, max UDMA/133
Jan  6 16:33:05 justdrea-pc kernel: [    1.777703] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan  6 16:33:05 justdrea-pc kernel: [    1.779346] ata1.00: configured for UDMA/133
Jan  6 16:33:05 justdrea-pc kernel: [    1.780273] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HUA72205 A3MA PQ: 0 ANSI: 5
Jan  6 16:33:05 justdrea-pc kernel: [    1.857815] Console: switching to colour frame buffer device 170x48
Jan  6 16:33:05 justdrea-pc kernel: [    1.870098] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jan  6 16:33:05 justdrea-pc kernel: [    1.870104] i915 0000:00:02.0: registered panic notifier
Jan  6 16:33:05 justdrea-pc kernel: [    1.878521] usb 1-1: New USB device found, idVendor=0d8c, idProduct=013c
Jan  6 16:33:05 justdrea-pc kernel: [    1.878530] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  6 16:33:05 justdrea-pc kernel: [    1.878536] usb 1-1: Product: USB PnP Sound Device
Jan  6 16:33:05 justdrea-pc kernel: [    1.885696] usbcore: registered new interface driver usbhid
Jan  6 16:33:05 justdrea-pc kernel: [    1.885701] usbhid: USB HID core driver
Jan  6 16:33:05 justdrea-pc kernel: [    1.885981] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jan  6 16:33:05 justdrea-pc kernel: [    1.886065] sd 0:0:0:0: [sda] Write Protect is off
Jan  6 16:33:05 justdrea-pc kernel: [    1.886070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  6 16:33:05 justdrea-pc kernel: [    1.886107] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  6 16:33:05 justdrea-pc kernel: [    1.888126] input: USB PnP Sound Device as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.3/0003:0D8C:013C.0001/input/input6
Jan  6 16:33:05 justdrea-pc kernel: [    1.919005]  sda: sda1 sda2 sda3 sda4
Jan  6 16:33:05 justdrea-pc kernel: [    1.920443] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  6 16:33:05 justdrea-pc kernel: [    1.944789] hid-generic 0003:0D8C:013C.0001: input,hidraw0: USB HID v1.00 Device [USB PnP Sound Device] on usb-0000:00:14.0-1/input3
Jan  6 16:33:05 justdrea-pc kernel: [    1.996160] usb 1-2: new high-speed USB device number 3 using xhci_hcd
Jan  6 16:33:05 justdrea-pc kernel: [    2.126040] usb 1-2: New USB device found, idVendor=05e3, idProduct=0608
Jan  6 16:33:05 justdrea-pc kernel: [    2.126049] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan  6 16:33:05 justdrea-pc kernel: [    2.126054] usb 1-2: Product: USB2.0 Hub
Jan  6 16:33:05 justdrea-pc kernel: [    2.127701] hub 1-2:1.0: USB hub found
Jan  6 16:33:05 justdrea-pc kernel: [    2.128122] hub 1-2:1.0: 3 ports detected
Jan  6 16:33:05 justdrea-pc kernel: [    2.240357] tsc: Refined TSC clocksource calibration: 1999.999 MHz
Jan  6 16:33:05 justdrea-pc kernel: [    2.240365] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x39a85afc727, max_idle_ns: 881590685098 ns
Jan  6 16:33:05 justdrea-pc kernel: [    2.296846] usb 1-4: new low-speed USB device number 4 using xhci_hcd
Jan  6 16:33:05 justdrea-pc kernel: [    2.485030] usb 1-4: New USB device found, idVendor=093a, idProduct=2510
Jan  6 16:33:05 justdrea-pc kernel: [    2.485037] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  6 16:33:05 justdrea-pc kernel: [    2.485040] usb 1-4: Product: USB Optical Mouse
Jan  6 16:33:05 justdrea-pc kernel: [    2.485043] usb 1-4: Manufacturer: PixArt
Jan  6 16:33:05 justdrea-pc kernel: [    2.485513] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan  6 16:33:05 justdrea-pc kernel: [    2.487830] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:093A:2510.0002/input/input7
Jan  6 16:33:05 justdrea-pc kernel: [    2.488469] hid-generic 0003:093A:2510.0002: input,hidraw1: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:14.0-4/input0
Jan  6 16:33:05 justdrea-pc kernel: [    2.553195] usb 1-2.3: new low-speed USB device number 5 using xhci_hcd
Jan  6 16:33:05 justdrea-pc kernel: [    2.647547] usb 1-2.3: New USB device found, idVendor=1c4f, idProduct=0026
Jan  6 16:33:05 justdrea-pc kernel: [    2.647555] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  6 16:33:05 justdrea-pc kernel: [    2.647558] usb 1-2.3: Product: USB Keyboard
Jan  6 16:33:05 justdrea-pc kernel: [    2.647561] usb 1-2.3: Manufacturer: SIGMACHIP
Jan  6 16:33:05 justdrea-pc kernel: [    2.648251] usb 1-2.3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan  6 16:33:05 justdrea-pc kernel: [    2.648262] usb 1-2.3: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan  6 16:33:05 justdrea-pc kernel: [    2.651617] input: SIGMACHIP USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.0/0003:1C4F:0026.0003/input/input8
Jan  6 16:33:05 justdrea-pc kernel: [    2.705968] hid-generic 0003:1C4F:0026.0003: input,hidraw2: USB HID v1.10 Keyboard [SIGMACHIP USB Keyboard] on usb-0000:00:14.0-2.3/input0
Jan  6 16:33:05 justdrea-pc kernel: [    2.709478] input: SIGMACHIP USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.1/0003:1C4F:0026.0004/input/input9
Jan  6 16:33:05 justdrea-pc kernel: [    2.766074] hid-generic 0003:1C4F:0026.0004: input,hidraw3: USB HID v1.10 Device [SIGMACHIP USB Keyboard] on usb-0000:00:14.0-2.3/input1
Jan  6 16:33:05 justdrea-pc kernel: [    3.242912] clocksource: Switched to clocksource tsc
Jan  6 16:33:05 justdrea-pc kernel: [    3.617779] PM: Starting manual resume from disk
Jan  6 16:33:05 justdrea-pc kernel: [    3.617788] PM: Hibernation image partition 8:1 present
Jan  6 16:33:05 justdrea-pc kernel: [    3.617790] PM: Looking for hibernation image.
Jan  6 16:33:05 justdrea-pc kernel: [    3.618479] PM: Image not found (code -22)
Jan  6 16:33:05 justdrea-pc kernel: [    3.618482] PM: Hibernation image not present or could not be loaded.
Jan  6 16:33:05 justdrea-pc kernel: [    5.485687] random: nonblocking pool is initialized
Jan  6 16:33:05 justdrea-pc kernel: [    8.373093] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Jan  6 16:33:05 justdrea-pc kernel: [   10.380336] lp: driver loaded but no devices found
Jan  6 16:33:05 justdrea-pc kernel: [   10.385827] ppdev: user-space parallel port driver
Jan  6 16:33:05 justdrea-pc kernel: [   10.409848] parport_pc 00:03: reported by Plug and Play ACPI
Jan  6 16:33:05 justdrea-pc kernel: [   10.409945] parport0: PC-style at 0x378 (0x778), irq 5 [PCSPP,TRISTATE,EPP]
Jan  6 16:33:05 justdrea-pc kernel: [   10.505066] lp0: using parport0 (interrupt-driven).
Jan  6 16:33:05 justdrea-pc kernel: [   10.869551] EXT4-fs (sda4): re-mounted. Opts: data=ordered
Jan  6 16:33:05 justdrea-pc kernel: [   11.372461] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  6 16:33:05 justdrea-pc kernel: [   11.391722] EFI Variables Facility v0.08 2004-May-17
Jan  6 16:33:05 justdrea-pc kernel: [   11.395054] ACPI Warning: SystemIO range 0x000000000000F000-0x000000000000F01F conflicts with OpRegion 0x000000000000F000-0x000000000000F00F (\_SB_.PCI0.SBUS.SMBI) (20150619/utaddress-254)
Jan  6 16:33:05 justdrea-pc kernel: [   11.395065] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan  6 16:33:05 justdrea-pc kernel: [   11.410144] pstore: Registered efi as persistent store backend
Jan  6 16:33:05 justdrea-pc kernel: [   11.467080] input: PC Speaker as /devices/platform/pcspkr/input/input10
Jan  6 16:33:05 justdrea-pc kernel: [   11.482049] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  6 16:33:05 justdrea-pc kernel: [   11.577528] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
Jan  6 16:33:05 justdrea-pc kernel: [   11.724048] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC662 rev1: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Jan  6 16:33:05 justdrea-pc kernel: [   11.724055] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=1 (0x15/0x0/0x0/0x0/0x0)
Jan  6 16:33:05 justdrea-pc kernel: [   11.724059] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Jan  6 16:33:05 justdrea-pc kernel: [   11.724062] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Jan  6 16:33:05 justdrea-pc kernel: [   11.724064] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Jan  6 16:33:05 justdrea-pc kernel: [   11.724068] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
Jan  6 16:33:05 justdrea-pc kernel: [   11.724072] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
Jan  6 16:33:05 justdrea-pc kernel: [   11.724075] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Jan  6 16:33:05 justdrea-pc kernel: [   11.869075] iTCO_vendor_support: vendor-support=0
Jan  6 16:33:05 justdrea-pc kernel: [   11.869737] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.11
Jan  6 16:33:05 justdrea-pc kernel: [   11.869808] iTCO_wdt: Found a Bay Trail SoC TCO device (Version=3, TCOBASE=0x0460)
Jan  6 16:33:05 justdrea-pc kernel: [   11.870077] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan  6 16:33:05 justdrea-pc kernel: [   11.881582] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Jan  6 16:33:05 justdrea-pc kernel: [   11.881702] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Jan  6 16:33:05 justdrea-pc kernel: [   11.881818] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Jan  6 16:33:05 justdrea-pc kernel: [   11.881929] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Jan  6 16:33:05 justdrea-pc kernel: [   11.915656] intel_rapl: Found RAPL domain package
Jan  6 16:33:05 justdrea-pc kernel: [   11.915663] intel_rapl: Found RAPL domain core
Jan  6 16:33:05 justdrea-pc kernel: [   11.998358] usbcore: registered new interface driver snd-usb-audio
Jan  6 16:33:05 justdrea-pc kernel: [   12.410463] Adding 4553724k swap on /dev/sda1.  Priority:-1 extents:1 across:4553724k FS
Jan  6 16:33:05 justdrea-pc kernel: [   12.635099] FAT-fs (sda3): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Jan  6 16:33:06 justdrea-pc kernel: [   15.037437] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
Jan  6 16:33:06 justdrea-pc kernel: [   15.158757] r8169 0000:02:00.0: firmware: direct-loading firmware rtl_nic/rtl8168g-2.fw
Jan  6 16:33:06 justdrea-pc kernel: [   15.200631] r8169 0000:02:00.0 enp2s0: link down
Jan  6 16:33:06 justdrea-pc kernel: [   15.200656] r8169 0000:02:00.0 enp2s0: link down
Jan  6 16:33:06 justdrea-pc kernel: [   15.200690] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
Jan  6 16:33:08 justdrea-pc kernel: [   17.713851] r8169 0000:02:00.0 enp2s0: link up
Jan  6 16:33:08 justdrea-pc kernel: [   17.713866] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
Jan  6 16:33:19 justdrea-pc kernel: [   28.005339] fuse init (API version 7.23)
```

I'm really sorry but I was not able to upload the files, it said that it was not an accepted format.

---

### Post by mastablasta on 2016-01-06
hmmm crashed while running same application..

```
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: Notify "Spotify" "" "Maggie Mae - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("image-data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: (deepin-notifications:4643): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  6 16:28:15 justdrea-pc org.freedesktop.Notifications[557]: (deepin-notifications:4643): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
Jan  6 16:28:19 justdrea-pc org.freedesktop.Notifications[557]: Notify "Spotify" "" "I've Got A Feeling - Remastered 2009" "Let It Be (Remastered)" () QMap(("icon_data", QVariant(QDBusArgument, ))("image-data", QVariant(QDBusArgument, ))("urgency", QVariant(uchar, 0))) -1
Jan  6 16:28:21 justdrea-pc org.freedesktop.Notifications[557]: bubbleExpired
Jan  6 16:28:22 justdrea-pc org.freedesktop.Notifications[557]: bubbleDismissed
```

other than that presented logs don't show any major error messages. maybe someone else can spot something strange.

furthermore: 
> If X.org crashes look at /var/log/Xorg.0.log (or /var/log/Xorg.0.log.old when a new X session is started after the crash).
so let's see if the GPU is crashing or what...

are you using Deepin? it is based on Debian unstable. hmmm...

---

### Post by jesus-freak on 2016-01-06
Yes, I am running Deepin at the moment. But remember, this happens with ALL OS's I've tried. From Ubuntu and all of it's flavors to Arch to Fadora to Opensuse. Anything and everything I have tried that runs a fairly new kernel (post 3.13)  this always happens.

I'll get that xorg log for you as soon as I can. Right now I'm running my system on a second hard drive with a version of Ubuntu running 3.13.0-27 kernel so that I can work without crashes. As soon as my work finishes I'll switch back to the Deepin drive and get that log and post it.

---

### Post by howefield on 2016-01-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mastablasta on 2016-01-06
ok so a kernel setting or a (misconfigured?!) driver is likely to be causing this.

if oyu know which kernel changes it it might be good to also check the change long for that kernel and see if it refers to any hardware you might be using.

---

### Post by jesus-freak on 2016-01-06
Xorg.0.log
```
 
[    11.731] 
X.Org X Server 1.17.3
Release Date: 2015-10-26
[    11.731] X Protocol Version 11, Revision 0
[    11.731] Build Operating System: Linux 3.16.0-4-amd64 x86_64 Debian
[    11.731] Current Operating System: Linux justdrea-pc 4.2.0-1-amd64 #1 SMP Debian 4.2.6-3 (2015-12-06) x86_64
[    11.731] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-1-amd64 root=UUID=b07b1af1-4799-425d-bb67-1d2e51cc6e53 ro splash quiet
[    11.731] Build Date: 27 October 2015  11:41:02PM
[    11.731] xorg-server 2:1.17.3-2 (http://www.debian.org/support) 
[    11.732] Current version of pixman: 0.33.4
[    11.732] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.732] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.732] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  6 23:02:23 2016
[    11.791] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    11.791] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.818] (==) No Layout section.  Using the first Screen section.
[    11.818] (==) No screen section available. Using defaults.
[    11.818] (**) |-->Screen "Default Screen Section" (0)
[    11.818] (**) |   |-->Monitor "<default monitor>"
[    11.819] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    11.819] (==) Automatically adding devices
[    11.819] (==) Automatically enabling devices
[    11.819] (==) Automatically adding GPU devices
[    11.858] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.858] 	Entry deleted from font path.
[    11.862] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    11.862] (==) ModulePath set to "/usr/lib/xorg/modules"
[    11.862] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.863] (II) Loader magic: 0x55e90f898de0
[    11.863] (II) Module ABI versions:
[    11.863] 	X.Org ANSI C Emulation: 0.4
[    11.863] 	X.Org Video Driver: 19.0
[    11.863] 	X.Org XInput driver : 21.0
[    11.863] 	X.Org Server Extension : 9.0
[    11.866] (EE) systemd-logind: failed to get session: PID 465 does not belong to any known session
[    11.867] (II) xfree86: Adding drm device (/dev/dri/card0)
[    11.873] (--) PCI:*(0:0:2:0) 8086:0f31:1849:0f31 rev 14, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[    11.987] (II) LoadModule: "glx"
[    12.018] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.091] (II) Module glx: vendor="X.Org Foundation"
[    12.091] 	compiled for 1.17.3, module version = 1.0.0
[    12.091] 	ABI class: X.Org Server Extension, version 9.0
[    12.091] (==) AIGLX enabled
[    12.091] (==) Matched intel as autoconfigured driver 0
[    12.091] (==) Matched intel as autoconfigured driver 1
[    12.091] (==) Matched modesetting as autoconfigured driver 2
[    12.091] (==) Matched fbdev as autoconfigured driver 3
[    12.091] (==) Matched vesa as autoconfigured driver 4
[    12.091] (==) Assigned the driver to the xf86ConfigLayout
[    12.091] (II) LoadModule: "intel"
[    12.092] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.119] (II) Module intel: vendor="X.Org Foundation"
[    12.119] 	compiled for 1.17.2, module version = 2.99.917
[    12.119] 	Module class: X.Org Video Driver
[    12.119] 	ABI class: X.Org Video Driver, version 19.0
[    12.119] (II) LoadModule: "modesetting"
[    12.119] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.121] (II) Module modesetting: vendor="X.Org Foundation"
[    12.121] 	compiled for 1.17.3, module version = 1.17.3
[    12.121] 	Module class: X.Org Video Driver
[    12.121] 	ABI class: X.Org Video Driver, version 19.0
[    12.121] (II) LoadModule: "fbdev"
[    12.121] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.127] (II) Module fbdev: vendor="X.Org Foundation"
[    12.127] 	compiled for 1.17.1, module version = 0.4.4
[    12.127] 	Module class: X.Org Video Driver
[    12.127] 	ABI class: X.Org Video Driver, version 19.0
[    12.127] (II) LoadModule: "vesa"
[    12.127] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.132] (II) Module vesa: vendor="X.Org Foundation"
[    12.132] 	compiled for 1.17.3, module version = 2.3.4
[    12.132] 	Module class: X.Org Video Driver
[    12.132] 	ABI class: X.Org Video Driver, version 19.0
[    12.132] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    12.133] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    12.133] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    12.133] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    12.133] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.133] (II) FBDEV: driver for framebuffer: fbdev
[    12.133] (II) VESA: driver for VESA chipsets: vesa
[    12.133] (++) using VT number 7

[    12.142] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150522
[    12.142] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-2 (Vincent Cheng <vcheng@debian.org>)
[    12.142] (II) intel(0): SNA compiled for use with valgrind
[    12.144] (WW) Falling back to old probe method for modesetting
[    12.144] (WW) Falling back to old probe method for fbdev
[    12.144] (II) Loading sub module "fbdevhw"
[    12.144] (II) LoadModule: "fbdevhw"
[    12.144] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.147] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.147] 	compiled for 1.17.3, module version = 0.0.2
[    12.147] 	ABI class: X.Org Video Driver, version 19.0
[    12.147] (WW) Falling back to old probe method for vesa
[    12.156] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics
[    12.156] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    12.156] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    12.156] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    12.156] (==) intel(0): RGB weight 888
[    12.156] (==) intel(0): Default visual is TrueColor
[    12.157] (II) intel(0): Output VGA1 has no monitor section
[    12.157] (II) intel(0): Enabled output VGA1
[    12.157] (II) intel(0): Output HDMI1 has no monitor section
[    12.157] (II) intel(0): Enabled output HDMI1
[    12.157] (II) intel(0): Output DP1 has no monitor section
[    12.157] (II) intel(0): Enabled output DP1
[    12.157] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    12.157] (II) intel(0): Output VIRTUAL1 has no monitor section
[    12.157] (II) intel(0): Enabled output VIRTUAL1
[    12.157] (--) intel(0): Output VGA1 using initial mode 1366x768 on pipe 0
[    12.157] (==) intel(0): TearFree disabled
[    12.157] (==) intel(0): DPI set to (96, 96)
[    12.157] (II) Loading sub module "dri2"
[    12.157] (II) LoadModule: "dri2"
[    12.157] (II) Module "dri2" already built-in
[    12.157] (II) Loading sub module "present"
[    12.157] (II) LoadModule: "present"
[    12.157] (II) Module "present" already built-in
[    12.157] (II) UnloadModule: "modesetting"
[    12.158] (II) Unloading modesetting
[    12.158] (II) UnloadModule: "fbdev"
[    12.158] (II) Unloading fbdev
[    12.158] (II) UnloadSubModule: "fbdevhw"
[    12.158] (II) Unloading fbdevhw
[    12.158] (II) UnloadModule: "vesa"
[    12.158] (II) Unloading vesa
[    12.158] (==) Depth 24 pixmap format is 32 bpp
[    12.183] (II) intel(0): SNA initialized with Baytrail (gen7) backend
[    12.183] (==) intel(0): Backing store enabled
[    12.183] (==) intel(0): Silken mouse enabled
[    12.183] (II) intel(0): HW Cursor enabled
[    12.183] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.184] (==) intel(0): DPMS enabled
[    12.184] (==) intel(0): display hotplug detection enabled
[    12.185] (II) intel(0): [DRI2] Setup complete
[    12.185] (II) intel(0): [DRI2]   DRI driver: i965
[    12.185] (II) intel(0): [DRI2]   VDPAU driver: i965
[    12.185] (II) intel(0): direct rendering: DRI2 enabled
[    12.185] (II) intel(0): hardware support for Present enabled
[    12.185] (--) RandR disabled
[    12.193] (II) SELinux: Disabled on system
[    12.301] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.301] (II) AIGLX: enabled GLX_ARB_create_context
[    12.301] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    12.301] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    12.301] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.301] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.301] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    12.301] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    12.301] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.301] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    12.301] (II) AIGLX: Loaded and initialized i965
[    12.301] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.323] (II) intel(0): switch to mode 1366x768@59.8 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    12.328] (II) intel(0): Setting screen physical size to 361 x 203
[    12.595] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    12.595] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.595] (II) LoadModule: "evdev"
[    12.602] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.620] (II) Module evdev: vendor="X.Org Foundation"
[    12.620] 	compiled for 1.16.4, module version = 2.9.2
[    12.620] 	Module class: X.Org XInput Driver
[    12.620] 	ABI class: X.Org XInput driver, version 21.0
[    12.620] (II) Using input driver 'evdev' for 'Power Button'
[    12.620] (**) Power Button: always reports core events
[    12.620] (**) evdev: Power Button: Device: "/dev/input/event2"
[    12.621] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.621] (--) evdev: Power Button: Found keys
[    12.621] (II) evdev: Power Button: Configuring as keyboard
[    12.621] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event2"
[    12.621] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    12.621] (**) Option "xkb_rules" "evdev"
[    12.621] (**) Option "xkb_model" "pc105"
[    12.621] (**) Option "xkb_layout" "us"
[    12.622] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    12.622] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    12.622] (II) Using input driver 'evdev' for 'Video Bus'
[    12.622] (**) Video Bus: always reports core events
[    12.622] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    12.622] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    12.622] (--) evdev: Video Bus: Found keys
[    12.622] (II) evdev: Video Bus: Configuring as keyboard
[    12.622] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event3"
[    12.622] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    12.622] (**) Option "xkb_rules" "evdev"
[    12.622] (**) Option "xkb_model" "pc105"
[    12.622] (**) Option "xkb_layout" "us"
[    12.623] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.623] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.623] (II) Using input driver 'evdev' for 'Power Button'
[    12.623] (**) Power Button: always reports core events
[    12.623] (**) evdev: Power Button: Device: "/dev/input/event0"
[    12.623] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.623] (--) evdev: Power Button: Found keys
[    12.623] (II) evdev: Power Button: Configuring as keyboard
[    12.623] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event0"
[    12.624] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    12.624] (**) Option "xkb_rules" "evdev"
[    12.624] (**) Option "xkb_model" "pc105"
[    12.624] (**) Option "xkb_layout" "us"
[    12.625] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    12.625] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    12.625] (II) Using input driver 'evdev' for 'Sleep Button'
[    12.625] (**) Sleep Button: always reports core events
[    12.625] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    12.625] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    12.625] (--) evdev: Sleep Button: Found keys
[    12.625] (II) evdev: Sleep Button: Configuring as keyboard
[    12.625] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input3/event1"
[    12.625] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    12.625] (**) Option "xkb_rules" "evdev"
[    12.625] (**) Option "xkb_model" "pc105"
[    12.625] (**) Option "xkb_layout" "us"
[    12.627] (II) config/udev: Adding input device USB PnP Sound Device (/dev/input/event4)
[    12.627] (**) USB PnP Sound Device: Applying InputClass "evdev keyboard catchall"
[    12.627] (II) Using input driver 'evdev' for 'USB PnP Sound Device'
[    12.627] (**) USB PnP Sound Device: always reports core events
[    12.627] (**) evdev: USB PnP Sound Device: Device: "/dev/input/event4"
[    12.627] (--) evdev: USB PnP Sound Device: Vendor 0xd8c Product 0x13c
[    12.627] (--) evdev: USB PnP Sound Device: Found keys
[    12.627] (II) evdev: USB PnP Sound Device: Configuring as keyboard
[    12.627] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.3/0003:0D8C:013C.0001/input/input6/event4"
[    12.627] (II) XINPUT: Adding extended input device "USB PnP Sound Device" (type: KEYBOARD, id 10)
[    12.627] (**) Option "xkb_rules" "evdev"
[    12.627] (**) Option "xkb_model" "pc105"
[    12.627] (**) Option "xkb_layout" "us"
[    12.628] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event6)
[    12.628] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    12.629] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    12.629] (**) SIGMACHIP USB Keyboard: always reports core events
[    12.629] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event6"
[    12.629] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x26
[    12.629] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    12.629] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    12.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.0/0003:1C4F:0026.0003/input/input8/event6"
[    12.629] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 11)
[    12.629] (**) Option "xkb_rules" "evdev"
[    12.629] (**) Option "xkb_model" "pc105"
[    12.629] (**) Option "xkb_layout" "us"
[    12.630] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event7)
[    12.630] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    12.630] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    12.630] (**) SIGMACHIP USB Keyboard: always reports core events
[    12.630] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event7"
[    12.630] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x26
[    12.630] (--) evdev: SIGMACHIP USB Keyboard: Found 1 mouse buttons
[    12.630] (--) evdev: SIGMACHIP USB Keyboard: Found scroll wheel(s)
[    12.630] (--) evdev: SIGMACHIP USB Keyboard: Found relative axes
[    12.630] (II) evdev: SIGMACHIP USB Keyboard: Forcing relative x/y axes to exist.
[    12.631] (--) evdev: SIGMACHIP USB Keyboard: Found absolute axes
[    12.631] (II) evdev: SIGMACHIP USB Keyboard: Forcing absolute x/y axes to exist.
[    12.631] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    12.631] (II) evdev: SIGMACHIP USB Keyboard: Configuring as mouse
[    12.631] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    12.631] (II) evdev: SIGMACHIP USB Keyboard: Adding scrollwheel support
[    12.631] (**) evdev: SIGMACHIP USB Keyboard: YAxisMapping: buttons 4 and 5
[    12.631] (**) evdev: SIGMACHIP USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.631] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.1/0003:1C4F:0026.0004/input/input9/event7"
[    12.631] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 12)
[    12.631] (**) Option "xkb_rules" "evdev"
[    12.631] (**) Option "xkb_model" "pc105"
[    12.631] (**) Option "xkb_layout" "us"
[    12.631] (II) evdev: SIGMACHIP USB Keyboard: initialized for relative axes.
[    12.631] (WW) evdev: SIGMACHIP USB Keyboard: ignoring absolute axes.
[    12.631] (**) SIGMACHIP USB Keyboard: (accel) keeping acceleration scheme 1
[    12.632] (**) SIGMACHIP USB Keyboard: (accel) acceleration profile 0
[    12.632] (**) SIGMACHIP USB Keyboard: (accel) acceleration factor: 2.000
[    12.632] (**) SIGMACHIP USB Keyboard: (accel) acceleration threshold: 4
[    12.633] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event5)
[    12.633] (**) PixArt USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    12.633] (II) Using input driver 'evdev' for 'PixArt USB Optical Mouse'
[    12.633] (**) PixArt USB Optical Mouse: always reports core events
[    12.633] (**) evdev: PixArt USB Optical Mouse: Device: "/dev/input/event5"
[    12.688] (--) evdev: PixArt USB Optical Mouse: Vendor 0x93a Product 0x2510
[    12.688] (--) evdev: PixArt USB Optical Mouse: Found 3 mouse buttons
[    12.688] (--) evdev: PixArt USB Optical Mouse: Found scroll wheel(s)
[    12.688] (--) evdev: PixArt USB Optical Mouse: Found relative axes
[    12.688] (--) evdev: PixArt USB Optical Mouse: Found x and y relative axes
[    12.688] (II) evdev: PixArt USB Optical Mouse: Configuring as mouse
[    12.688] (II) evdev: PixArt USB Optical Mouse: Adding scrollwheel support
[    12.688] (**) evdev: PixArt USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    12.688] (**) evdev: PixArt USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.688] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:093A:2510.0002/input/input7/event5"
[    12.688] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 13)
[    12.688] (II) evdev: PixArt USB Optical Mouse: initialized for relative axes.
[    12.689] (**) PixArt USB Optical Mouse: (accel) keeping acceleration scheme 1
[    12.689] (**) PixArt USB Optical Mouse: (accel) acceleration profile 0
[    12.689] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    12.689] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    12.690] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse0)
[    12.690] (II) No input driver specified, ignoring this device.
[    12.690] (II) This device may have been added with another device file.
[    12.691] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[    12.691] (II) No input driver specified, ignoring this device.
[    12.691] (II) This device may have been added with another device file.
[    12.692] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event10)
[    12.692] (II) No input driver specified, ignoring this device.
[    12.692] (II) This device may have been added with another device file.
[    12.693] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    12.693] (II) No input driver specified, ignoring this device.
[    12.693] (II) This device may have been added with another device file.
[    12.693] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    12.693] (II) No input driver specified, ignoring this device.
[    12.693] (II) This device may have been added with another device file.
[    12.694] (II) config/udev: Adding input device PC Speaker (/dev/input/event8)
[    12.694] (II) No input driver specified, ignoring this device.
[    12.694] (II) This device may have been added with another device file.

```

Xorg.0.log.old
```

[    16.097] 
X.Org X Server 1.17.3
Release Date: 2015-10-26
[    16.097] X Protocol Version 11, Revision 0
[    16.097] Build Operating System: Linux 3.16.0-4-amd64 x86_64 Debian
[    16.097] Current Operating System: Linux justdrea-pc 4.2.0-1-amd64 #1 SMP Debian 4.2.6-3 (2015-12-06) x86_64
[    16.097] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-1-amd64 root=UUID=b07b1af1-4799-425d-bb67-1d2e51cc6e53 ro splash quiet
[    16.097] Build Date: 27 October 2015  11:41:02PM
[    16.097] xorg-server 2:1.17.3-2 (http://www.debian.org/support) 
[    16.097] Current version of pixman: 0.33.4
[    16.097] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.097] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.097] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  6 16:33:07 2016
[    16.134] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    16.134] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.152] (==) No Layout section.  Using the first Screen section.
[    16.152] (==) No screen section available. Using defaults.
[    16.152] (**) |-->Screen "Default Screen Section" (0)
[    16.152] (**) |   |-->Monitor "<default monitor>"
[    16.153] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.153] (==) Automatically adding devices
[    16.153] (==) Automatically enabling devices
[    16.153] (==) Automatically adding GPU devices
[    16.177] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.177] 	Entry deleted from font path.
[    16.184] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    16.184] (==) ModulePath set to "/usr/lib/xorg/modules"
[    16.184] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.184] (II) Loader magic: 0x55cdeb5d9de0
[    16.184] (II) Module ABI versions:
[    16.184] 	X.Org ANSI C Emulation: 0.4
[    16.184] 	X.Org Video Driver: 19.0
[    16.184] 	X.Org XInput driver : 21.0
[    16.184] 	X.Org Server Extension : 9.0
[    16.187] (EE) systemd-logind: failed to get session: PID 464 does not belong to any known session
[    16.188] (II) xfree86: Adding drm device (/dev/dri/card0)
[    16.194] (--) PCI:*(0:0:2:0) 8086:0f31:1849:0f31 rev 14, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f080/8
[    16.195] (II) LoadModule: "glx"
[    16.213] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.294] (II) Module glx: vendor="X.Org Foundation"
[    16.294] 	compiled for 1.17.3, module version = 1.0.0
[    16.294] 	ABI class: X.Org Server Extension, version 9.0
[    16.294] (==) AIGLX enabled
[    16.294] (==) Matched intel as autoconfigured driver 0
[    16.294] (==) Matched intel as autoconfigured driver 1
[    16.294] (==) Matched modesetting as autoconfigured driver 2
[    16.294] (==) Matched fbdev as autoconfigured driver 3
[    16.294] (==) Matched vesa as autoconfigured driver 4
[    16.294] (==) Assigned the driver to the xf86ConfigLayout
[    16.294] (II) LoadModule: "intel"
[    16.294] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.329] (II) Module intel: vendor="X.Org Foundation"
[    16.329] 	compiled for 1.17.2, module version = 2.99.917
[    16.329] 	Module class: X.Org Video Driver
[    16.329] 	ABI class: X.Org Video Driver, version 19.0
[    16.329] (II) LoadModule: "modesetting"
[    16.329] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.330] (II) Module modesetting: vendor="X.Org Foundation"
[    16.330] 	compiled for 1.17.3, module version = 1.17.3
[    16.330] 	Module class: X.Org Video Driver
[    16.330] 	ABI class: X.Org Video Driver, version 19.0
[    16.330] (II) LoadModule: "fbdev"
[    16.330] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.331] (II) Module fbdev: vendor="X.Org Foundation"
[    16.331] 	compiled for 1.17.1, module version = 0.4.4
[    16.331] 	Module class: X.Org Video Driver
[    16.331] 	ABI class: X.Org Video Driver, version 19.0
[    16.331] (II) LoadModule: "vesa"
[    16.332] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.342] (II) Module vesa: vendor="X.Org Foundation"
[    16.342] 	compiled for 1.17.3, module version = 2.3.4
[    16.342] 	Module class: X.Org Video Driver
[    16.342] 	ABI class: X.Org Video Driver, version 19.0
[    16.342] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    16.342] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    16.342] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    16.342] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    16.342] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.342] (II) FBDEV: driver for framebuffer: fbdev
[    16.342] (II) VESA: driver for VESA chipsets: vesa
[    16.343] (++) using VT number 7

[    16.353] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20150522
[    16.353] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-2 (Vincent Cheng <vcheng@debian.org>)
[    16.353] (II) intel(0): SNA compiled for use with valgrind
[    16.354] (WW) Falling back to old probe method for modesetting
[    16.354] (WW) Falling back to old probe method for fbdev
[    16.354] (II) Loading sub module "fbdevhw"
[    16.354] (II) LoadModule: "fbdevhw"
[    16.355] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.357] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.357] 	compiled for 1.17.3, module version = 0.0.2
[    16.357] 	ABI class: X.Org Video Driver, version 19.0
[    16.357] (WW) Falling back to old probe method for vesa
[    16.366] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics
[    16.366] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    16.366] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.366] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.366] (==) intel(0): RGB weight 888
[    16.366] (==) intel(0): Default visual is TrueColor
[    16.366] (II) intel(0): Output VGA1 has no monitor section
[    16.366] (II) intel(0): Enabled output VGA1
[    16.366] (II) intel(0): Output HDMI1 has no monitor section
[    16.366] (II) intel(0): Enabled output HDMI1
[    16.366] (II) intel(0): Output DP1 has no monitor section
[    16.366] (II) intel(0): Enabled output DP1
[    16.366] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    16.367] (II) intel(0): Output VIRTUAL1 has no monitor section
[    16.367] (II) intel(0): Enabled output VIRTUAL1
[    16.367] (--) intel(0): Output VGA1 using initial mode 1366x768 on pipe 0
[    16.367] (==) intel(0): TearFree disabled
[    16.367] (==) intel(0): DPI set to (96, 96)
[    16.367] (II) Loading sub module "dri2"
[    16.367] (II) LoadModule: "dri2"
[    16.367] (II) Module "dri2" already built-in
[    16.367] (II) Loading sub module "present"
[    16.367] (II) LoadModule: "present"
[    16.367] (II) Module "present" already built-in
[    16.367] (II) UnloadModule: "modesetting"
[    16.367] (II) Unloading modesetting
[    16.367] (II) UnloadModule: "fbdev"
[    16.367] (II) Unloading fbdev
[    16.367] (II) UnloadSubModule: "fbdevhw"
[    16.367] (II) Unloading fbdevhw
[    16.367] (II) UnloadModule: "vesa"
[    16.367] (II) Unloading vesa
[    16.368] (==) Depth 24 pixmap format is 32 bpp
[    16.393] (II) intel(0): SNA initialized with Baytrail (gen7) backend
[    16.393] (==) intel(0): Backing store enabled
[    16.393] (==) intel(0): Silken mouse enabled
[    16.394] (II) intel(0): HW Cursor enabled
[    16.394] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.395] (==) intel(0): DPMS enabled
[    16.396] (==) intel(0): display hotplug detection enabled
[    16.396] (II) intel(0): [DRI2] Setup complete
[    16.396] (II) intel(0): [DRI2]   DRI driver: i965
[    16.396] (II) intel(0): [DRI2]   VDPAU driver: i965
[    16.396] (II) intel(0): direct rendering: DRI2 enabled
[    16.396] (II) intel(0): hardware support for Present enabled
[    16.396] (--) RandR disabled
[    16.405] (II) SELinux: Disabled on system
[    16.519] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.519] (II) AIGLX: enabled GLX_ARB_create_context
[    16.519] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.519] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.519] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.519] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.519] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    16.519] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    16.519] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.519] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    16.519] (II) AIGLX: Loaded and initialized i965
[    16.519] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.540] (II) intel(0): switch to mode 1366x768@59.8 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    16.544] (II) intel(0): Setting screen physical size to 361 x 203
[    16.813] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.813] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.813] (II) LoadModule: "evdev"
[    16.820] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.838] (II) Module evdev: vendor="X.Org Foundation"
[    16.838] 	compiled for 1.16.4, module version = 2.9.2
[    16.838] 	Module class: X.Org XInput Driver
[    16.838] 	ABI class: X.Org XInput driver, version 21.0
[    16.838] (II) Using input driver 'evdev' for 'Power Button'
[    16.839] (**) Power Button: always reports core events
[    16.839] (**) evdev: Power Button: Device: "/dev/input/event2"
[    16.839] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.839] (--) evdev: Power Button: Found keys
[    16.839] (II) evdev: Power Button: Configuring as keyboard
[    16.839] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event2"
[    16.839] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.839] (**) Option "xkb_rules" "evdev"
[    16.839] (**) Option "xkb_model" "pc105"
[    16.839] (**) Option "xkb_layout" "us"
[    16.840] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    16.840] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.840] (II) Using input driver 'evdev' for 'Video Bus'
[    16.840] (**) Video Bus: always reports core events
[    16.840] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    16.840] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.840] (--) evdev: Video Bus: Found keys
[    16.840] (II) evdev: Video Bus: Configuring as keyboard
[    16.840] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event3"
[    16.840] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.840] (**) Option "xkb_rules" "evdev"
[    16.840] (**) Option "xkb_model" "pc105"
[    16.840] (**) Option "xkb_layout" "us"
[    16.841] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.841] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.841] (II) Using input driver 'evdev' for 'Power Button'
[    16.842] (**) Power Button: always reports core events
[    16.842] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.842] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.842] (--) evdev: Power Button: Found keys
[    16.842] (II) evdev: Power Button: Configuring as keyboard
[    16.842] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event0"
[    16.842] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.842] (**) Option "xkb_rules" "evdev"
[    16.842] (**) Option "xkb_model" "pc105"
[    16.842] (**) Option "xkb_layout" "us"
[    16.843] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.843] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.843] (II) Using input driver 'evdev' for 'Sleep Button'
[    16.843] (**) Sleep Button: always reports core events
[    16.843] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    16.843] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    16.843] (--) evdev: Sleep Button: Found keys
[    16.843] (II) evdev: Sleep Button: Configuring as keyboard
[    16.843] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input3/event1"
[    16.843] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    16.843] (**) Option "xkb_rules" "evdev"
[    16.843] (**) Option "xkb_model" "pc105"
[    16.843] (**) Option "xkb_layout" "us"
[    16.845] (II) config/udev: Adding input device USB PnP Sound Device (/dev/input/event4)
[    16.845] (**) USB PnP Sound Device: Applying InputClass "evdev keyboard catchall"
[    16.845] (II) Using input driver 'evdev' for 'USB PnP Sound Device'
[    16.845] (**) USB PnP Sound Device: always reports core events
[    16.845] (**) evdev: USB PnP Sound Device: Device: "/dev/input/event4"
[    16.845] (--) evdev: USB PnP Sound Device: Vendor 0xd8c Product 0x13c
[    16.845] (--) evdev: USB PnP Sound Device: Found keys
[    16.845] (II) evdev: USB PnP Sound Device: Configuring as keyboard
[    16.845] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.3/0003:0D8C:013C.0001/input/input6/event4"
[    16.845] (II) XINPUT: Adding extended input device "USB PnP Sound Device" (type: KEYBOARD, id 10)
[    16.845] (**) Option "xkb_rules" "evdev"
[    16.845] (**) Option "xkb_model" "pc105"
[    16.845] (**) Option "xkb_layout" "us"
[    16.847] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event6)
[    16.847] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.847] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    16.847] (**) SIGMACHIP USB Keyboard: always reports core events
[    16.847] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event6"
[    16.847] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x26
[    16.847] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    16.847] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    16.847] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.0/0003:1C4F:0026.0003/input/input8/event6"
[    16.847] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 11)
[    16.847] (**) Option "xkb_rules" "evdev"
[    16.847] (**) Option "xkb_model" "pc105"
[    16.847] (**) Option "xkb_layout" "us"
[    16.848] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event7)
[    16.848] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    16.848] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    16.848] (**) SIGMACHIP USB Keyboard: always reports core events
[    16.849] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event7"
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x26
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Found 1 mouse buttons
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Found scroll wheel(s)
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Found relative axes
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: Forcing relative x/y axes to exist.
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Found absolute axes
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: Forcing absolute x/y axes to exist.
[    16.849] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: Configuring as mouse
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: Adding scrollwheel support
[    16.849] (**) evdev: SIGMACHIP USB Keyboard: YAxisMapping: buttons 4 and 5
[    16.849] (**) evdev: SIGMACHIP USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.849] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.3/1-2.3:1.1/0003:1C4F:0026.0004/input/input9/event7"
[    16.849] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 12)
[    16.849] (**) Option "xkb_rules" "evdev"
[    16.849] (**) Option "xkb_model" "pc105"
[    16.849] (**) Option "xkb_layout" "us"
[    16.849] (II) evdev: SIGMACHIP USB Keyboard: initialized for relative axes.
[    16.849] (WW) evdev: SIGMACHIP USB Keyboard: ignoring absolute axes.
[    16.850] (**) SIGMACHIP USB Keyboard: (accel) keeping acceleration scheme 1
[    16.850] (**) SIGMACHIP USB Keyboard: (accel) acceleration profile 0
[    16.850] (**) SIGMACHIP USB Keyboard: (accel) acceleration factor: 2.000
[    16.850] (**) SIGMACHIP USB Keyboard: (accel) acceleration threshold: 4
[    16.851] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event5)
[    16.851] (**) PixArt USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    16.851] (II) Using input driver 'evdev' for 'PixArt USB Optical Mouse'
[    16.851] (**) PixArt USB Optical Mouse: always reports core events
[    16.851] (**) evdev: PixArt USB Optical Mouse: Device: "/dev/input/event5"
[    16.904] (--) evdev: PixArt USB Optical Mouse: Vendor 0x93a Product 0x2510
[    16.904] (--) evdev: PixArt USB Optical Mouse: Found 3 mouse buttons
[    16.904] (--) evdev: PixArt USB Optical Mouse: Found scroll wheel(s)
[    16.904] (--) evdev: PixArt USB Optical Mouse: Found relative axes
[    16.904] (--) evdev: PixArt USB Optical Mouse: Found x and y relative axes
[    16.904] (II) evdev: PixArt USB Optical Mouse: Configuring as mouse
[    16.904] (II) evdev: PixArt USB Optical Mouse: Adding scrollwheel support
[    16.904] (**) evdev: PixArt USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    16.904] (**) evdev: PixArt USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.904] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:093A:2510.0002/input/input7/event5"
[    16.904] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 13)
[    16.904] (II) evdev: PixArt USB Optical Mouse: initialized for relative axes.
[    16.905] (**) PixArt USB Optical Mouse: (accel) keeping acceleration scheme 1
[    16.905] (**) PixArt USB Optical Mouse: (accel) acceleration profile 0
[    16.905] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    16.905] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    16.906] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse0)
[    16.906] (II) No input driver specified, ignoring this device.
[    16.906] (II) This device may have been added with another device file.
[    16.907] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[    16.907] (II) No input driver specified, ignoring this device.
[    16.907] (II) This device may have been added with another device file.
[    16.908] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event10)
[    16.908] (II) No input driver specified, ignoring this device.
[    16.908] (II) This device may have been added with another device file.
[    16.908] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    16.909] (II) No input driver specified, ignoring this device.
[    16.909] (II) This device may have been added with another device file.
[    16.909] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    16.909] (II) No input driver specified, ignoring this device.
[    16.909] (II) This device may have been added with another device file.
[    16.910] (II) config/udev: Adding input device PC Speaker (/dev/input/event8)
[    16.910] (II) No input driver specified, ignoring this device.
[    16.910] (II) This device may have been added with another device file.
[   877.676] (II) evdev: PixArt USB Optical Mouse: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: SIGMACHIP USB Keyboard: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: SIGMACHIP USB Keyboard: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: USB PnP Sound Device: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: Sleep Button: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: Power Button: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.677] (II) evdev: Video Bus: Close
[   877.677] (II) UnloadModule: "evdev"
[   877.677] (II) evdev: Power Button: Close
[   877.677] (II) UnloadModule: "evdev"
[   877.705] (II) Server terminated successfully (0). Closing log file.
```

You said " also check the change log" How do I do that?  The Kernel that works well for me is 3.13.0-27. Anything newer like the 3.16+ 3.19+ and 4+ all have this same issue.

---

### Post by mastablasta on 2016-01-06
what's this? normal shutdown?:
```
[   877.676] (II) evdev: PixArt USB Optical Mouse: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: SIGMACHIP USB Keyboard: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: SIGMACHIP USB Keyboard: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: USB PnP Sound Device: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: Sleep Button: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.676] (II) evdev: Power Button: Close
[   877.676] (II) UnloadModule: "evdev"
[   877.677] (II) evdev: Video Bus: Close
[   877.677] (II) UnloadModule: "evdev"
[   877.677] (II) evdev: Power Button: Close
[   877.677] (II) UnloadModule: "evdev"
[   877.705] (II) Server terminated successfully (0). Closing log file.
```

by the way saw this and remembered your case (for checking logs in CLI a more efficient way: [http://lintut.com/install-and-use-log-file-navigator-lnav-in-ubuntu-and-centos-linux/](http://lintut.com/install-and-use-log-file-navigator-lnav-in-ubuntu-and-centos-linux/)

here are the changelogs but there is a lot of them and plenty of changes: [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/)

i thought we could narrow it down to component causing the issue so you could find the change log for that. but i don't see any major errors in any of your log files. and you also do not know the exact kernel where the system doesn't work anymore. it would be hard to find what the issue is liek that then.

just to be sure and to recap -  you have stock install deeping/ubuntu, no proprietary drivers and no boot options, right? and it always crashes no matter if you just turn it on and leave it on for a bit. as long as newer kernel is installed. and the crash is actually a freeze of the desktop. and you tried lightweight desktops to see if GPU 3D acceleration is doing the crash.

what if you tried to install (and i hope you don't have much data on yet) a non debian based distro like OpenSUSE or maybe Manjaro with new kernels? or maybe try them in live session first.

also did you ever run the mem test ? although i think ram would crash it differently. but you never know...

---

### Post by jesus-freak on 2016-01-06
> and you also do not know the exact kernel where the system doesn't work anymore. Well I do know that all of the 3.16, 3.19 kernels cause the freezing. And as far as what I am running now in Deepin, that is kernel 4.2 and it is freezing.

>  you have stock install deeping/ubuntu, no proprietary drivers and no boot options, right?  Correct.

>  and it always crashes no matter if you just turn it on and leave it on for a bit. as long as newer kernel is installed. and the crash is actually a freeze of the desktop.  Yes, however it does seem to last longer without freezing in left alone. Sometimes I will try to make it freeze, I will push it and open up a bunch of applications and it will do fine. Other times it will freeze when running the same applications.Sometimes it will freeze up with nothing open or just a browser open. I can't seem to recreate it, it just happens randomly it seems.

> and you tried lightweight desktops to see if GPU 3D acceleration is doing the crash. I have tried just about everything out there. Light, heavy, everything. If it has the 3.16 kernel or later, it freezes. 

>  what if you tried to install (and i hope you don't have much data on yet) a non debian based distro like OpenSUSE or maybe Manjaro with new kernels? or maybe try them in live session first. I have tried Manjaro, I have tried OpenSuse, I have tried Fadora. I get the same problem on all.

> also did you ever run the mem test ? although i think ram would crash it differently. but you never know... Yes, I did a memtest and it didn't show any problems. To be honest I'm almost to the end of trying here. As you can see I am not an expert at these things and I don't even understand half of the things people are telling me to do. I really appreciate all the help but I don't know if I am even capable of doing what you guys tell me to do.

---

### Post by mastablasta on 2016-01-07
i am also not an admin or some expert. I just had my fair share of freezes when helping others as well as at home, so I picked up some troubleshooting. yes it does seem we are at an end here. the most bothering to me is I can't figure out what component would actually cause the freeze. well aside from kernel, but kernel must be setting some parameter wrong. or some setting in BIOS confuses it and it set's a parameter wrong. you could try Ubuntu Launchpad. or better yet try Linux bug tracking system to report this. it looks like a bug to me but what kind of bug and what setting it affects it I have no idea.

it's what bothers me with Linux. you upgrade kernel and then things that used to work perfectly suddenly no longer work. no one knows why and often no one cares. sometimes you can find a workaround. sometimes you are stuck with it. in windows, manufacturer would resolve this if not MS.

I FOUND IT!!!! It's the CPU. here is the bug report and possible workaround: [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
this kernel parameter might help:

intel_idle.max_cstate=1

there are more workarounds lower down for different boards and assemblies.

oh and it will be good if you read this on how to add temporary kernel boot parameter and a permanent one- [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by jesus-freak on 2016-01-07
Okay, I'm really excited to try this out but I went to the link and read through the comments. It seems that this has worked for a lot of people but I never saw any instructions on how to actually do it. Where  is the file that I edit? How do I edit it?

---

### Post by mastablasta on 2016-01-07
see my second link for how to temporarily (and if it works later permanently) add this fix to your grub. to get to grub you need to hold (press?!) shift on boot.

---

### Post by jesus-freak on 2016-01-07
Oh, sorry about that. I got too excited and didn't see the second link lol. So in the grub file the line should look like this, correct?

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet intel_idle.max_cstate=1"
```

---

### Post by mastablasta on 2016-01-08
yes. if temporary adding the parameter fixed the issue you can move to permanent fix.

> Note: The parameter(s) you've added to the GRUB_CMDLINE_LINUX_DEFAULT line are persistent, and will be in effect for every subsequent boot session (unless you remove them by repeating the procedure above).

---

### Post by jesus-freak on 2016-01-08
Okay, Since Deepin using the 4.2 Kernel is installed on a second hard rive at the moment, I just went ahead and added that line to the grub file for permanent change. So far so good!! I'm going to wait a little bit longer before saying that it is fixed because last time I got a little burnt with doing that. However, I've been running it all day today and pushing it as hard as I can without any issues at all! The ultimate test will be doing my work on it. For some reason it always freezes up more when I am working. So if this lasts through my work, I think I can safely say that it is fixed. I'll let you know what happens.

UPDATE!!!! I used the Deepin drive all day and even did my work with it all evening with no problems at all! Thanks so much for all the help! That was epic of you to find that fix for me!

---

### Post by mastablasta on 2016-01-12
i've been "battling demons" of my own in the past few days. good to hear you have this solved.

now it's time for you to make one small, easy & final step and potentially help others in the process: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

:P

---

### Post by ivanpop on 2016-04-01
Disabling CPU features isn't a way to solve problems.
I have a machine with Asrock q1900b-itx, with Ubuntu 15.10 x64 and I'm experiencing the same freezes. I bought this machine for a low power server and disabling power saving features is the last thing I would want to do.
I have found threads about this problem that are more than a year older, so this problem is going for some quite long time. If a fix can't be made I suggest that BayTrail CPU's have to be labeled as "Not supported".

---

