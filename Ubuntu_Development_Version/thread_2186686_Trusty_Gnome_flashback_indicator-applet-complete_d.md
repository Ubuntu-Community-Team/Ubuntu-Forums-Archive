---
title: "Trusty Gnome flashback indicator-applet-complete disappeared"
date: 2013-11-08
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-11-08
A day or two ago I think I seen where indicator-applet-complete got an error.
I haven't seen it since. There is no date/time, network indicator, login, etc at the right of the top panel.

I installed some other files indicator-applet-session, indicator-applet-appmenu and indicator-applet (I believe) although I should not have had to.
indicator-applet-complete is supposed to be everything combined.

Anyway I rebooted and it's still gone.

Any one else have this issue?

---

### Post by kansasnoob on 2013-11-08
Same thing here, but apport fails to send the bug report:

[ATTACH=CONFIG]247677[/ATTACH]

[ATTACH=CONFIG]247678[/ATTACH]

---

### Post by mc4man on 2013-11-08
> **kansasnoob said:**
> Same thing here, but apport fails to send the bug report:

If you clicked send or continue, ect. it did send the report, just not to launchpad bugs

---

### Post by kansasnoob on 2013-11-09
> **mc4man said:**
> If you clicked send or continue, ect. it did send the report, just not to launchpad bugs

Where did it go?

---

### Post by mc4man on 2013-11-09
> **kansasnoob said:**
> Where did it go?
look up woopsie

Crashers opening a launchpad report is turned off in apport slightly before release & not re-enabled in the next dev for a while, a month or so, never exactly checked.
> (apport (2.12.5-0ubuntu2) saucy; urgency=low

  * etc/apport/crashdb.conf: Disable Launchpad crash/kernel reports for the
    final release. Only report to [http://errors.ubuntu.com](http://errors.ubuntu.com) from now on.

(- as far as woopsie - in a lts it's disabled at release or thereabouts , otherwise in interim releases it's active
[https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001658.html](https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001658.html)

---

### Post by kansasnoob on 2013-11-09
> **mc4man said:**
> look up woopsie

Crashers opening a launchpad report is turned off in apport slightly before release & not re-enabled in the next dev for a while, a month or so, never exactly checked.

(- as far as woopsie - in a lts it's disabled at release or thereabouts , otherwise in interim releases it's active
[https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001658.html](https://lists.ubuntu.com/archives/ubuntu-release/2012-August/001658.html)

There was an update earlier today that might be related:

> update-notifier (0.148) trusty; urgency=low

  [ Iain Lane ]
  * data/update-motd-updates-available: Update the stamp file atomically.
    Thanks to Marius Gedminas! (LP: #1146170)

  [ Brian Murray ]
  * In the upstart crash notification job fix the path for watershed.
  * [B]debian/update-notifier-crash.conf: check that we have read permission on
    the crash file before launching apport-gtk, additionally just launch
    apport-gtk or system-crash-notification as they will check for new crashes
    and start bug filing for each one (LP: #1193509)[/B]
  * data/update-motd-fsck-at-reboot: Update the stamp file atomically.
    Thanks to Marius Gedminas! (LP: #1240549)

 -- Brian Murray <brian@ubuntu.com>  Fri, 08 Nov 2013 15:32:25 -0800

I'm just not sure how various crash reports play with other apps????

---

### Post by Cavsfan on 2013-11-09
My apport is on:
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/default/apport
# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=1

```

Is there something we should do to woopsie? It seems to be on too.
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/default/whoopsie

[General]
report_crashes=true
```

---

### Post by Cavsfan on 2013-11-09
Here is the bug: [https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/1249663](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/1249663)

---

### Post by kansasnoob on 2013-11-09
> **Cavsfan said:**
> Here is the bug: [https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/1249663](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/1249663)

Cool I me-too'ed :)

---

### Post by Cavsfan on 2013-11-10
> **kansasnoob said:**
> Cool I me-too'ed :)

Kewl! Hopefully more than just the [COLOR=#0000ff]*too*[/COLOR] of us get on that. :)

---

### Post by mc4man on 2013-11-10
Both flashback sessions work ok here, all the indicators show up & work.

Maybe go to ~/.cache & delete the upstart folder.
Then log out/in & see what shows up in ~/.cache/upstart/  gnome-session.log & dbus.log

fresh dbus.log here right after login
> Activating service name='org.ayatana.bamf'

** (bamfdaemon:10750): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ijjneDIfoy: Connection refused
Activating service name='org.gtk.vfs.Daemon'
Successfully activated service 'org.gtk.vfs.Daemon'
Successfully activated service 'org.ayatana.bamf'
Activating service name='ca.desrt.dconf'
Successfully activated service 'ca.desrt.dconf'
Activating service name='org.freedesktop.IBus'
Successfully activated service 'org.freedesktop.IBus'
Activating service name='org.gnome.GConf'
Successfully activated service 'org.gnome.GConf'
Activating service name='org.gtk.Private.UDisks2VolumeMonitor'
Successfully activated service 'org.gtk.Private.UDisks2VolumeMonitor'
Activating service name='org.gtk.Private.AfcVolumeMonitor'
Successfully activated service 'org.gtk.Private.AfcVolumeMonitor'
Activating service name='org.gtk.Private.MTPVolumeMonitor'
Successfully activated service 'org.gtk.Private.MTPVolumeMonitor'
Activating service name='org.gtk.Private.GPhoto2VolumeMonitor'
Successfully activated service 'org.gtk.Private.GPhoto2VolumeMonitor'
Activating service name='org.gnome.panel.applet.IndicatorAppletCompleteFactory'
Successfully activated service 'org.gnome.panel.applet.IndicatorAppletCompleteFactory'

(indicator-applet-complete:10918): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion 'accelerator != NULL' failed

** (indicator-applet-complete:10918): WARNING **: Unable to parse mouse modifier '(null)'

Activating service name='com.canonical.indicator.printers'
Activating service name='com.canonical.indicator.sync'
Activating service name='com.canonical.indicator.application'
Activating service name='com.canonical.indicator.datetime'
Activating service name='com.canonical.indicator.power'
Activating service name='com.canonical.indicator.sound'
Activating service name='com.canonical.indicator.keyboard'
Activating service name='com.canonical.indicator.session'
Activating service name='com.canonical.indicator.messages'
Activating service name='com.canonical.indicator.bluetooth'
Successfully activated service 'com.canonical.indicator.sync'
Activating service name='org.gnome.ScreenSaver'
Successfully activated service 'com.canonical.indicator.messages'
Successfully activated service 'com.canonical.indicator.session'
Activating service name='org.gnome.evolution.dataserver.Sources1'
Successfully activated service 'com.canonical.indicator.datetime'
Successfully activated service 'com.canonical.indicator.application'

(indicator-applet-complete:10918): Indicator-Applet-Complete-CRITICAL **: entry_removed: assertion 'menuitem != NULL' failed
Successfully activated service 'com.canonical.indicator.sound'
Successfully activated service 'com.canonical.indicator.bluetooth'
Successfully activated service 'com.canonical.indicator.power'
module-cache-reaper-Message: Scanning data directories
module-cache-reaper-Message: Scanning cache directories
Successfully activated service 'org.gnome.evolution.dataserver.Sources1'
Successfully activated service 'com.canonical.indicator.printers'
Activating service name='org.gnome.evolution.dataserver.Calendar4'

(indicator-applet-complete:10918): GLib-GObject-WARNING **: g_object_disconnect: invalid signal spec "signal::show"
Successfully activated service 'org.gnome.ScreenSaver'
Successfully activated service 'com.canonical.indicator.keyboard'
Successfully activated service 'org.gnome.evolution.dataserver.Calendar4'
Activating service name='org.gtk.vfs.Metadata'
Successfully activated service 'org.gtk.vfs.Metadata'
Activating service name='org.gnome.zeitgeist.Engine'
Activating service name='org.gnome.zeitgeist.SimpleIndexer'
Successfully activated service 'org.gnome.zeitgeist.Engine'
Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
...irrelevant


---

### Post by Cavsfan on 2013-11-10
Still nada.

gnome-session.log:
```
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-PtCj8f
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-PtCj8f
GPG_AGENT_INFO=/run/user/1000/keyring-PtCj8f/gpg:0:1
SSH_AUTH_SOCK=/run/user/1000/keyring-PtCj8f/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-PtCj8f
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-PtCj8f
GPG_AGENT_INFO=/run/user/1000/keyring-PtCj8f/gpg:0:1
GPG_AGENT_INFO=/run/user/1000/keyring-PtCj8f/gpg:0:1


(gnome-panel:7695): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion 'accelerator != NULL' failed


** (gnome-panel:7695): WARNING **: Unable to parse mouse modifier '(null)'


I/O warning : failed to load external entity "/home/cavsfan/.compiz/session/1068727d0c5b6eb08a138411825952955400000075200003"


Tracker-Message: Importing config file to GSettings
Tracker-Message: Importing config file to GSettings
Tracker-Message: Importing config file to GSettings


(gnome-panel:7695): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion 'accelerator != NULL' failed


** (gnome-panel:7695): WARNING **: Unable to parse mouse modifier '(null)'


** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon


(nautilus:7753): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


(nautilus:7753): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


Launcher-API-Daemon: registered as Unity: <dbus.service.BusName com.canonical.Unity on <dbus._dbus.SessionBus (session) at 0x1357410> at 0x133e710>
connect...
-> connected to cairo-dock
('new owner:', dbus.UTF8String(':1.59'))
Launcher-API-Daemon: Update application://nautilus.desktop with dbus.Dictionary({dbus.String(u'count'): dbus.Int64(0L, variant_level=1), dbus.String(u'progress-visible'): dbus.Boolean(False, variant_level=1), dbus.String(u'count-visible'): dbus.Boolean(False, variant_level=1), dbus.String(u'quicklist'): dbus.ObjectPath('/com/canonical/unity/launcherentry/706927342', variant_level=1), dbus.String(u'urgent'): dbus.Boolean(False, variant_level=1), dbus.String(u'progress'): dbus.Double(0.0, variant_level=1)}, signature=dbus.Signature('sv'))
Launcher-API-Daemon: set_count (0)
Launcher-API-Daemon: set_progress (0.00)
Launcher-API-Daemon: set_urgent (0)
Launcher-API-Daemon: set_menu (/com/canonical/unity/launcherentry/706927342)
Launcher-API-Daemon: set_count_visible (0)
Launcher-API-Daemon: set_progress_visible (0)
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
Launcher-API-Daemon: Update application://nautilus-home.desktop with dbus.Dictionary({dbus.String(u'count'): dbus.Int64(0L, variant_level=1), dbus.String(u'progress-visible'): dbus.Boolean(False, variant_level=1), dbus.String(u'count-visible'): dbus.Boolean(False, variant_level=1), dbus.String(u'quicklist'): dbus.ObjectPath('/com/canonical/unity/launcherentry/1543400804', variant_level=1), dbus.String(u'urgent'): dbus.Boolean(False, variant_level=1), dbus.String(u'progress'): dbus.Double(0.0, variant_level=1)}, signature=dbus.Signature('sv'))
Launcher-API-Daemon: set_count (0)
Launcher-API-Daemon: set_progress (0.00)
Launcher-API-Daemon: set_urgent (0)
Launcher-API-Daemon: set_menu (/com/canonical/unity/launcherentry/1543400804)
Launcher-API-Daemon: set_count_visible (0)
Launcher-API-Daemon: set_progress_visible (0)
Launcher-API-Daemon: launcher bus name changed: :1.50
Launcher-API-Daemon: launcher bus name changed: :1.50
Conky: unknown variable 
Conky: forked to background, pid is 7890


Conky: desktop window (1e00006) is subwindow of root window (26e)
Conky: window type - normal
Conky: drawing to created window (0x2200002)
Conky: drawing to double buffer


Downloading main data file...


Weather update download completed.
Conkywx program execution completed in: 0m5.387s


(zeitgeist-datahub:8051): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(zeitgeist-datahub:8051): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


(nautilus:7753): Gtk-CRITICAL **: gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed


(nautilus:7753): Gtk-CRITICAL **: gtk_spinner_start: assertion 'GTK_IS_SPINNER (spinner)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed


(gtk-window-decorator:7730): Wnck-CRITICAL **: wnck_window_get_xid: assertion 'WNCK_IS_WINDOW (window)' failed

```

dbus.log:
```
Activating service name='org.ayatana.bamf'
Activating service name='org.a11y.Bus'
Successfully activated service 'org.a11y.Bus'
Activating service name='org.a11y.atspi.Registry'
Activating service name='org.gtk.vfs.Daemon'
Successfully activated service 'org.a11y.atspi.Registry'
Successfully activated service 'org.gtk.vfs.Daemon'


** (at-spi2-registryd:7541): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (at-spi2-registryd:7541): WARNING **: Unable to register client with session manager
Successfully activated service 'org.ayatana.bamf'
Activating service name='ca.desrt.dconf'
Successfully activated service 'ca.desrt.dconf'
Activating service name='org.freedesktop.IBus'
Successfully activated service 'org.freedesktop.IBus'
Activating service name='org.gnome.GConf'
Successfully activated service 'org.gnome.GConf'
Activating service name='org.gtk.Private.UDisks2VolumeMonitor'
Successfully activated service 'org.gtk.Private.UDisks2VolumeMonitor'
Activating service name='org.gtk.Private.GPhoto2VolumeMonitor'
Successfully activated service 'org.gtk.Private.GPhoto2VolumeMonitor'
Activating service name='org.gtk.Private.AfcVolumeMonitor'
Successfully activated service 'org.gtk.Private.AfcVolumeMonitor'
Activating service name='org.gtk.Private.MTPVolumeMonitor'
Successfully activated service 'org.gtk.Private.MTPVolumeMonitor'
Activating service name='org.gnome.zeitgeist.Engine'
Activating service name='org.gnome.zeitgeist.SimpleIndexer'
Successfully activated service 'org.gnome.zeitgeist.Engine'
Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'


** (zeitgeist-datahub:8070): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Activating service name='org.gnome.evolution.dataserver.Sources1'
module-cache-reaper-Message: Scanning data directories
module-cache-reaper-Message: Scanning cache directories
Successfully activated service 'org.gnome.evolution.dataserver.Sources1'
Activating service name='org.gnome.OnlineAccounts'
Activating service name='org.gnome.evolution.dataserver.Calendar4'
Successfully activated service 'org.gnome.OnlineAccounts'
Successfully activated service 'org.gnome.evolution.dataserver.Calendar4'


** (zeitgeist-fts:8064): WARNING **: Unable to get info on application://nautilus-autostart.desktop


** (zeitgeist-fts:8064): WARNING **: Unable to get info on application://nautilus-autostart.desktop

```

I took out most of the normal compiz lines in gnome-session.log.

---

### Post by mc4man on 2013-11-10
Well your dbus.log is showing no indication of even trying to load the indicators/services

You only need indicator-appmenu-complete installed though indicator-application is a recommend so may as well be installed.

Things to ck. - 
Do you have the various indicators installed? (indicator-session, indicator-datetime, indicator-power, indicator-messages, indicator-sound, ect.

If the various indicators are installed, what happens in a guest session? (at least here you must log out of user session to go to a guest session

---

### Post by stoneguy on 2013-11-11
I chimed in on the Launchpad report, and added some info on how we may be seeing different things.

---

### Post by Cavsfan on 2013-11-11
> **mc4man said:**
> Well your dbus.log is showing no indication of even trying to load the indicators/services

You only need indicator-appmenu-complete installed though indicator-application is a recommend so may as well be installed.

Things to ck. - 
Do you have the various indicators installed? (indicator-session, indicator-datetime, indicator-power, indicator-messages, indicator-sound, ect.

If the various indicators are installed, what happens in a guest session? (at least here you must log out of user session to go to a guest session

I have all of the above installed. I had disabled the guest login like always so I had to re-enable that and reboot.
Upon trying to use the guest login I selected Gnome Flashback but it still logged into Unity. I tried several times and it did the same thing everytime. I even tried Gnome Classic and it still loaded Unity.

> **stoneguy said:**
> I chimed in on the Launchpad report, and added  some info on how we may be seeing different things. 

So, you are saying that in CSSM when you make it 1 panel the indicators display properly but, not with 4 panels?

---

### Post by muktupavels on 2013-11-11
Did you try to re-add indicator applet complete to panel?

---

### Post by Cavsfan on 2013-11-11
> **albertsmuktupavels said:**
> Did you try to re-add indicator applet complete to panel?

I purged indicator-applet-complete, re-installed it and rebooted still nothing.

Here is what I have: 

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2013-11-11122733.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2013-11-11122733.php")

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy indicator-applet-complete
indicator-applet-complete:
  Installed: 12.10.2+13.10.20130924.2-0ubuntu1
  Candidate: 12.10.2+13.10.20130924.2-0ubuntu1
  Version table:
 *** 12.10.2+13.10.20130924.2-0ubuntu1 0
        500 http://ubuntu.wikimedia.org/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```

indicator-application-gtk2 is not installed. Should it be?

---

### Post by kansasnoob on 2013-11-11
I did a fresh install of Ubuntu i386 20131111 today and all seems well :)

I think once things have been tweaked a gazillion times that it's best to start over, and the installer needs to be tested continuously ;)

---

### Post by muktupavels on 2013-11-12
> **Cavsfan said:**
> I purged indicator-applet-complete, re-installed it and rebooted still nothing.

Reinstalling won't add it to panel. If it is removed than you need manualy add back to panel.

---

### Post by ventrical on 2013-11-12
I upgraded Edubuntu  today and gnome-flashback (no effects) will not even come up. Just the background screen. I'm using lunity now. :) lol

---

### Post by Cavsfan on 2013-11-12
> **ventrical said:**
> I upgraded Edubuntu  today and gnome-flashback (no effects) will not even come up. Just the background screen. I'm using lunity now. :) lol

Oh Noz! I am in the middle of doing a clean install of Trusty. :) I figured it was time. I got that iso before there were daily ISOs. We shall soon see what I get. About to do first reboot after installing nvidia drivers. :lol:

---

### Post by Cavsfan on 2013-11-12
Completed the re-install and the indicators are back. None of it works: logout, shutdown, no restart option. But Saucy is in the same state. Haven't tried suspend but, it used to work.
It was time I guess for a re-install. Still trying to figure out how to get date to display along with time which does display.

I have Cairo Dock for all of the functions that do not work.

---

### Post by ventrical on 2013-11-12
Nope .. no indicators here either.

---

### Post by Cavsfan on 2013-11-12
> **ventrical said:**
> Nope .. no indicators here either.

You mean the whole top right panel is blank as in my previous picture or the indicators do not work?

Here is what I have now:

[[IMG]http://en.zimagez.com/miniature/flashbackisback11-12-13.png[/IMG]]("http://en.zimagez.com/zimage/flashbackisback11-12-13.php")

I did a clean install from today's ISO. Got everything copied back into places then installed **gnome-session-flashback** via CLI and it suggested but didn't install **desktop-base** so I installed that. I think a bunch of stuff came with that.
Then it suggested but did not install **gnome** so I installed that and a flood of stuff was installed then.

I have never tried flashback with no effects always just chose flashback. LoL I just now seen where you said you were in Lunity :lol:
I disabled the Unity bar in CCSM one time but it's still not Gnome. That is a total waste of space IMO.

---

### Post by ventrical on 2013-11-12
I am speaking specifically of the edubuntu version. I kept getting errors - unity-system-compositor- but aport will not send , crashes .. or wahtever it does .. (it did not send a report because no network activity after authentication).

But I did update and got this (plus added screenshot).

```

The following NEW packages will be installed:
  speech-dispatcher-audio-plugins
The following packages will be upgraded:
  gir1.2-gmenu-3.0 gnome-menus gnome-settings-daemon grub-common grub-pc
  grub-pc-bin grub2-common libgnome-menu-3-0 libmission-control-plugins0
  libqt5sensors5 libspeechd2 python3-speechd speech-dispatcher
  telepathy-mission-control-5
14 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,774 kB of archives.
After this operation, 379 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Installing new version of config file /etc/speech-dispatcher/speechd.conf ...
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Setting up libgnome-menu-3-0 (3.8.0-1ubuntu6) ...
Setting up gir1.2-gmenu-3.0 (3.8.0-1ubuntu6) ...
Setting up gnome-menus (3.8.0-1ubuntu6) ...
Setting up grub-common (2.00-19ubuntu4) ...
Setting up grub2-common (2.00-19ubuntu4) ...
Setting up grub-pc-bin (2.00-19ubuntu4) ...
Setting up grub-pc (2.00-19ubuntu4) ...
Installation finished. No error reported.

```


otherwise Unity works great and so does gnome-flashback (both) on Ubuntu only (but not Edubuntu).

---

### Post by Cavsfan on 2013-11-13
> **ventrical said:**
> I am speaking specifically of the edubuntu version. I kept getting errors - unity-system-compositor- but aport will not send , crashes .. or wahtever it does .. (it did not send a report because no network activity after authentication).

But I did update and got this (plus added screenshot).

```

The following NEW packages will be installed:
  speech-dispatcher-audio-plugins
The following packages will be upgraded:
  gir1.2-gmenu-3.0 gnome-menus gnome-settings-daemon grub-common grub-pc
  grub-pc-bin grub2-common libgnome-menu-3-0 libmission-control-plugins0
  libqt5sensors5 libspeechd2 python3-speechd speech-dispatcher
  telepathy-mission-control-5
14 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,774 kB of archives.
After this operation, 379 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Installing new version of config file /etc/speech-dispatcher/speechd.conf ...
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Setting up libgnome-menu-3-0 (3.8.0-1ubuntu6) ...
Setting up gir1.2-gmenu-3.0 (3.8.0-1ubuntu6) ...
Setting up gnome-menus (3.8.0-1ubuntu6) ...
Setting up grub-common (2.00-19ubuntu4) ...
Setting up grub2-common (2.00-19ubuntu4) ...
Setting up grub-pc-bin (2.00-19ubuntu4) ...
Setting up grub-pc (2.00-19ubuntu4) ...
Installation finished. No error reported.

```


otherwise Unity works great and so does gnome-flashback (both) on Ubuntu only (but not Edubuntu).

I just got those same updates and yeah my system errors sometimes and nothing goes any where. It will ask for my password a few times but nothing happens.

I see it is just Edubuntu you mean. Thanks for the clarification. 
On this install I just commented out the extra repositories; the first time I changed "trusty" to "saucy" as some had suggested but, I think I'll just leave this commented out until there is one for Trusty.

---

### Post by Cavsfan on 2013-11-15
Too bad the Ubuntu developers couldn't just pull some code from the Cairo Dock Logout button functionality and add it to the logout button at the top right of the top panel.

---

### Post by kansasnoob on 2013-11-15
> **Cavsfan said:**
> Too bad the Ubuntu developers couldn't just pull some code from the Cairo Dock Logout button functionality and add it to the logout button at the top right of the top panel.

IMHO that would only mean adding additional unneeded packages :)

I think we should keep it light and simple.

---

### Post by Cavsfan on 2013-11-15
> **kansasnoob said:**
> IMHO that would only mean adding additional unneeded packages :smile:

I think we should keep it light and simple.

Apparently you didn't understand what I meant. The code in the dock logout button (Shutdown, Restart, Suspend, Logout, Switch User, Lock Screen, etc.) works well. Copy that code and use it in the top panel. :)

I was not talking about "adding additional unneeded packages".

---

### Post by muktupavels on 2013-11-15
> **Cavsfan said:**
> Too bad the Ubuntu developers couldn't just pull some code from the Cairo Dock Logout button functionality and add it to the logout button at the top right of the top panel.

What exactly does not work for you? Are you using default configuration? Menu Bar on left and indicator applet complete on right? I can logout, restart, shutdown and suspend without problems.

---

### Post by muktupavels on 2013-11-15
> **Cavsfan said:**
> The code in the dock logout button (Shutdown, Restart, Suspend, Logout, Switch User, Lock Screen, etc.) works well. Copy that code and use it in the top panel. :).

If you are using indicator applet complete than what happens when you click logout/restart/shutdown? Maybe you can attach log file - .cache/indicator-applet-complete.log

---

### Post by Cavsfan on 2013-11-15
> **albertsmuktupavels said:**
> What exactly does not work for you? Are you using default configuration? Menu Bar on left and indicator applet complete on right? I can logout, restart, shutdown and suspend without problems.

Yes it is all default. The only thing that does work is suspend. Although I haven't tried it lately. I just use Cairo Dock. It's is the exact same way in Saucy. I am suprised that yours does work. I think it affects a lot of other people.

---

### Post by Cavsfan on 2013-11-15
> **albertsmuktupavels said:**
> If you are using indicator applet complete than what happens when you click logout/restart/shutdown? Maybe you can attach log file - .cache/indicator-applet-complete.log

Exactly nothing happens. I'm not worried about it enough to try anything to fix it. I'll wait for a fix as I cannot be the only one.

---

### Post by muktupavels on 2013-11-15
> **Cavsfan said:**
> Exactly nothing happens. I'm not worried about it enough to try anything to fix it. I'll wait for a fix as I cannot be the only one.

Please attach log file I asked, maybe there will be some info about why it does not work for you. Just click on logout/shutdown/restart, than add log file here. You can try attach dbus.log and gnome-session.log files from .cache/upstart directory too.

Is there open bug report about this?

---

### Post by Cavsfan on 2013-11-15
> **albertsmuktupavels said:**
> Please attach log file I asked, maybe there will be some info about why it does not work for you. Just click on logout/shutdown/restart, than add log file here. You can try attach dbus.log and gnome-session.log files from .cache/upstart directory too.

Is there open bug report about this?

Suspend does work but that is all. There is no "restart" option; sometimes it's there and sometimes it's not. I clicked on logout and shutdown.

~/.cache/indicator-applet-complete.log:
```
DEBUG: Indicator-Applet-Complete - Icons directory: /usr/share/libindicator/icons/
WARNING: Indicator-Applet-Complete - Binding '<Super>S' failed!

DEBUG: Indicator-Applet-Complete - Looking at Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Loading Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Loading Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Loading Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libappmenu.la
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.power
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.datetime
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.keyboard
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.sound
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.session
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.bluetooth
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.messages
DEBUG: Indicator-Application - Connected to Application Indicator Service.
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.sound
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.sound (indicator-sound): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.session
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.session (indicator-session): -1
DEBUG: Indicator-Application - Request current apps
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.datetime
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.datetime (indicator-datetime): -1
DEBUG: Indicator-Application - Building new application entry: :1.27  with icon: nm-device-wired at position 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libapplication.so
DEBUG: Indicator-Applet-Complete - Placing libapplication.so (nm-applet): 9
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
DEBUG: Sync-Indicator - indicator-sync.c:249 setting accessible_desc to 'Sync'
DEBUG: Sync-Indicator - indicator-sync.c:217 setting visibility flag to 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
CRITICAL: Indicator-Applet-Complete - entry_removed: assertion 'menuitem != NULL' failed
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.messages
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.messages (indicator-messages): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Placing libprintersmenu.so (indicator-printers): -1
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.keyboard
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.keyboard (indicator-keyboard): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
WARNING: GLib-GObject - g_object_disconnect: invalid signal spec "signal::show"
WARNING: IDO - unable to fetch album art: Operation not supported
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 151
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 152
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 153
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 154
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 155
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 158
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 159
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 160
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 161
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 162
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 163
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 164
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 165
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 156
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 157
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
```

The bug is on post #8 page 1 of this thread.

---

### Post by muktupavels on 2013-11-16
> **Cavsfan said:**
> Suspend does work but that is all. There is no "restart" option; sometimes it's there and sometimes it's not. I clicked on logout and shutdown.

~/.cache/indicator-applet-complete.log:
```
DEBUG: Indicator-Applet-Complete - Icons directory: /usr/share/libindicator/icons/
WARNING: Indicator-Applet-Complete - Binding '<Super>S' failed!

DEBUG: Indicator-Applet-Complete - Looking at Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Loading Module: libsyncindicator.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Loading Module: libapplication.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Loading Module: libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Looking at Module: libappmenu.la
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.power
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.datetime
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.keyboard
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.sound
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.session
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.bluetooth
DEBUG: Indicator-Applet-Complete - loading indicator: com.canonical.indicator.messages
DEBUG: Indicator-Application - Connected to Application Indicator Service.
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.sound
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.sound (indicator-sound): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.session
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.session (indicator-session): -1
DEBUG: Indicator-Application - Request current apps
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.datetime
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.datetime (indicator-datetime): -1
DEBUG: Indicator-Application - Building new application entry: :1.27  with icon: nm-device-wired at position 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libapplication.so
DEBUG: Indicator-Applet-Complete - Placing libapplication.so (nm-applet): 9
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
DEBUG: Sync-Indicator - indicator-sync.c:249 setting accessible_desc to 'Sync'
DEBUG: Sync-Indicator - indicator-sync.c:217 setting visibility flag to 0
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
CRITICAL: Indicator-Applet-Complete - entry_removed: assertion 'menuitem != NULL' failed
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.messages
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.messages (indicator-messages): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from libprintersmenu.so
DEBUG: Indicator-Applet-Complete - Placing libprintersmenu.so (indicator-printers): -1
CRITICAL: Gtk - gtk_distribute_natural_allocation: assertion 'extra_space >= 0' failed
DEBUG: Indicator-Applet-Complete - Signal: Entry Added from com.canonical.indicator.keyboard
DEBUG: Indicator-Applet-Complete - Placing com.canonical.indicator.keyboard (indicator-keyboard): -1
DEBUG: Indicator-Applet-Complete - Signal: Entry Removed
WARNING: GLib-GObject - g_object_disconnect: invalid signal spec "signal::show"
WARNING: IDO - unable to fetch album art: Operation not supported
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 151
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 152
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 153
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 154
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 155
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 158
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 159
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 160
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 161
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 162
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 163
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 164
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 165
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 156
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
DEBUG: LIBDBUSMENU-GLIB - Generating properties error for: 157
DEBUG: LIBDBUSMENU-GLIB - Error getting properties on a new menuitem: Error getting properties for ID
```

The bug is on post #8 page 1 of this thread.

I was asking about bug report for not working logout/restart/shutdown not about disappeared applet.

When indicator applet complete disappeared you only needed re-add it to panel. When applet crashes there should be displayed dialog asking what you want to do. You should click on Reload button to add it back to panel. If you click on Don't Reload or simply close dialog applet wont be added back. You had two choices. First - manualy add applet to panel. Second - reset gnome-panel config forcing recreate panel with default configuration "dconf reset -f /org/gnome/gnome-panel/".

About not working logout/restart/shutdown buttons. For me it works on my pc (x64). Tried to install trusty in virtualbox, both 32 bit and 64 bit versions. Installed gnome-session-flashback and than tried both flashback sessions (with compiz and with metacity). I was able to logout every time I tried. I was able to shutdown and restart too. So problem could be with your install. Do you have added extra ppa's or installed other packages which is not installed by default? Show output of this command: ```
apt-cache policy libdbusmenu*
```

---

### Post by Cavsfan on 2013-11-16
> **albertsmuktupavels said:**
> I was asking about bug report for not working logout/restart/shutdown not about disappeared applet.

When indicator applet complete disappeared you only needed re-add it to panel. When applet crashes there should be displayed dialog asking what you want to do. You should click on Reload button to add it back to panel. If you click on Don't Reload or simply close dialog applet wont be added back. You had two choices. First - manualy add applet to panel. Second - reset gnome-panel config forcing recreate panel with default configuration "dconf reset -f /org/gnome/gnome-panel/".

About not working logout/restart/shutdown buttons. For me it works on my pc (x64). Tried to install trusty in virtualbox, both 32 bit and 64 bit versions. Installed gnome-session-flashback and than tried both flashback sessions (with compiz and with metacity). I was able to logout every time I tried. I was able to shutdown and restart too. So problem could be with your install. Do you have added extra ppa's or installed other packages which is not installed by default? Show output of this command: ```
apt-cache policy libdbusmenu*
```

The title of this thread is **Trusty Gnome flashback indicator-applet-complete disappeared**. That problem was resolved with a fresh install of a daily iso. My original install was pretty much a Saucy iso as the daily ISO was not yet available.
I could not simply re-add indicator-applet-complete to the panel because I tried that more than once. This issue is resolved and that bug should be too IMO.

Trusty's Gnome flashback indicator-applet-complete works exactly like the one in Saucy. Neither will restart or shutdown.

---

