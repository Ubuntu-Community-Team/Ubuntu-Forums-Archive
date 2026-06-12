---
title: "Deluge 1.0.0 is final!"
date: 2008-09-22
forum: The Cafe
---

### Post by zachtib on 2008-09-22
Here's the Announcement: [http://forum.deluge-torrent.org/viewtopic.php?f=8&t=9875](http://forum.deluge-torrent.org/viewtopic.php?f=8&t=9875)

Please Digg it: [http://digg.com/linux_unix/Deluge_Torrent_Client_1_0_Released](http://digg.com/linux_unix/Deluge_Torrent_Client_1_0_Released)

As always, my Ubuntu repository is here:[http://launchpad.net/~deluge-team/+archive](http://launchpad.net/~deluge-team/+archive) (Now supporting Gutsy, Hardy, & Intrepid)

---

### Post by picpak on 2008-09-22
Just upgraded. I think the placement of things is a little cumbersome, but overall, a nice release.

---

### Post by binbash on 2008-09-22
I just installed it, it's cool, nice release

---

### Post by FuturePilot on 2008-09-22
Awesome! I love Deluge. :)

---

### Post by adityakavoor on 2008-09-22
loving it :D

---

### Post by earthpigg on 2008-09-22
is this a p2p program? please clarify :)

---

### Post by binbash on 2008-09-22
> **earthpigg said:**
> is this a p2p program? please clarify :)

Yup, only for torrents

---

### Post by kostkon on 2008-09-22
> **zachtib said:**
> Here's the Announcement: [http://forum.deluge-torrent.org/viewtopic.php?f=8&t=9875](http://forum.deluge-torrent.org/viewtopic.php?f=8&t=9875)

Please Digg it: [http://digg.com/linux_unix/Deluge_Torrent_Client_1_0_Released](http://digg.com/linux_unix/Deluge_Torrent_Client_1_0_Released)

As always, my Ubuntu repository is here:[http://launchpad.net/~deluge-team/+archive](http://launchpad.net/~deluge-team/+archive) (Now supporting Gutsy, Hardy, & Intrepid)
Great app!

And thanks for maintaining the PPA :)

---

### Post by SuperSonic4 on 2008-09-22
I'll try it tonight for my arch download (I'm feeling brave xD)

---

### Post by zachtib on 2008-09-23
Thanks guys, and keep digging that story, I'm trying to get the word out.

---

### Post by RiceMonster on 2008-09-23
Sweet, can't wait to test it out.

---

### Post by Greyed on 2008-09-23
Rats.  My torrent machine is on Debian.  :/

---

### Post by FuturePilot on 2008-09-23
> **Greyed said:**
> Rats.  My torrent machine is on Debian.  :/

There's Debian packages [here]("http://deluge-torrent.org/downloads.php") :)

---

### Post by zachtib on 2008-09-23
> **Greyed said:**
> Rats.  My torrent machine is on Debian.  :/

also, you might be able to grab my source and build debs (assuming you can't make use of the prebuilt packages on deluge-torrent.org)

---

### Post by luispa on 2008-10-11
Hi,

I recently upgraded to Deluge 1.0.0-1 and I'm unable to use it. This is the message I get when launching it from a console:
...
[DEBUG   ] 01:27:52 ipcinterface:83 Processing args from other process: []
[DEBUG   ] 01:27:52 ipcinterface:86 Not connected to host.. Adding to queue.
[INFO    ] 01:27:52 dbusinterface:82 Registering with DBUS..
[DEBUG   ] 01:27:52 component:102 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 01:27:52 configmanager:88 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:58: GtkWarning: Invalid input string
  "glade/main_window.glade"))
Fallo de segmentación

Any idea on how to solve it?

Thank you very much in advance,

Luis Pablo

---

### Post by zachtib on 2008-10-11
> **luispa said:**
> Hi,

I recently upgraded to Deluge 1.0.0-1 and I'm unable to use it. This is the message I get when launching it from a console:
...
[DEBUG   ] 01:27:52 ipcinterface:83 Processing args from other process: []
[DEBUG   ] 01:27:52 ipcinterface:86 Not connected to host.. Adding to queue.
[INFO    ] 01:27:52 dbusinterface:82 Registering with DBUS..
[DEBUG   ] 01:27:52 component:102 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 01:27:52 configmanager:88 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:58: GtkWarning: Invalid input string
  "glade/main_window.glade"))
Fallo de segmentación

Any idea on how to solve it?

Thank you very much in advance,

Luis Pablo

how'd you install it?

also, try moving your ~/.config/deluge folder and run again

---

### Post by toocer on 2008-12-07
I cant install the latest version?

This is what i get in the terminal when i try to start it.

```
[INFO    ] 00:14:04 main:85 Deluge ui 1.0.6
[DEBUG   ] 00:14:04 main:86 options: {'config': None, 'logfile': None, 'ui': None}
[DEBUG   ] 00:14:04 main:87 args: []
[DEBUG   ] 00:14:04 configmanager:36 ConfigManager started..
[INFO    ] 00:14:04 main:90 Starting ui..
[DEBUG   ] 00:14:04 ui:36 UI init..
[DEBUG   ] 00:14:04 configmanager:80 Getting config 'ui.conf'
[DEBUG   ] 00:14:04 config:39 Config created with filename: ui.conf
[DEBUG   ] 00:14:04 config:40 Config defaults: {'default_ui': 'gtk'}
[INFO    ] 00:14:04 ui:52 Starting GtkUI..
[DEBUG   ] 00:14:04 client:46 CoreProxy init..
[DEBUG   ] 00:14:04 configmanager:61 get_config_dir: /home/ulha/.config/deluge
[DEBUG   ] 00:14:04 configmanager:80 Getting config 'gtkui.conf'
[DEBUG   ] 00:14:04 config:39 Config created with filename: gtkui.conf
[DEBUG   ] 00:14:04 config:40 Config defaults: {'autoadd_queued': False, 'close_to_tray': True, 'window_width': 640, 'default_load_path': None, 'window_y_pos': 0, 'classic_mode': True, 'window_pane_position': -1, 'enabled_plugins': [], 'show_connection_manager_on_start': True, 'show_statusbar': True, 'autoadd_enable': False, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'show_sidebar': True, 'window_x_pos': 0, 'window_height': 480, 'lock_tray': False, 'connection_limit_list': [50, 100, 200, 300, 500], 'tray_password': '', 'focus_add_dialog': True, 'show_new_releases': True, 'start_in_tray': False, 'autoconnect': False, 'choose_directory_dialog_path': '/home/ulha', 'check_new_releases': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/ulha/.config/deluge', 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'interactive_add': True, 'signal_port': 40000}
1.0.6
[DEBUG   ] 00:14:04 gtkui:149 retcode: 0
[DEBUG   ] 00:14:04 component:94 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 00:14:04 configmanager:80 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/queuedtorrents.py:47: GtkWarning: Failed to set text from markup due to error parsing markup: Fel pÃ¥ rad 1 tecken 18: Ogiltigt UTF-8-kodad text - inte giltig "<big><b>Lï¿½gg till kï¿½ade Torrentar</b></big>"
  "glade/queuedtorrents.glade"))
[DEBUG   ] 00:14:04 component:94 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 00:14:04 component:94 Registered DbusInterface with ComponentRegistry..
[DEBUG   ] 00:14:04 ipcinterface:75 Processing args from other process: []
[DEBUG   ] 00:14:04 ipcinterface:78 Not connected to host.. Adding to queue.
[INFO    ] 00:14:04 dbusinterface:74 Registering with DBUS..
[DEBUG   ] 00:14:04 component:94 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 00:14:04 configmanager:80 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/mainwindow.py:50: GtkWarning: Invalid input string
  "glade/main_window.glade"))
Segmenteringsfel

```

I have tried to purge all files, and reinstalled with the PPA files, still no luck, if i remove the apt source and install the one included then there is no problem.

Please help

---

### Post by Polygon on 2008-12-07
try posting it on the forums in deluge-torrent.org 
thats where the developers lurk and will be able to help you =P

---

