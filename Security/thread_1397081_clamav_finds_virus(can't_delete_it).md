---
title: "clamav finds virus(can't delete it)"
date: 2010-02-02
forum: Security
---

### Post by delukard on 2010-02-02
hi i installed ubuntu 9.10 64 (jaunty) and downloaded packages from the ubuntu software center.
i only downloaded 1 thing in the terminal and it was a frontend for the clamav antivirus
by using sudo apt-get install clamtk.
i downloaded some themes for ubuntu but i downloaded them from the link provided by the 
appearance preferences window.
I connected my sister's psp and analized it, and found 7 virus. i right cliked on them and selected quarantine.
I was curious and analyzed home and it found 7 virus.
Was ubuntu infected by these viruses? i chose to delete them 1 by 1 and, i analyzed it again and it found only 1 this time.
from what i see it is related to firefox but tbh. i haven't visited any risky sites (i'm using wot also on firefox)

heres my log (i'm sorry if this isn't the way to do this, thanks for clearing my doubts)
```
ClamTk, v4.15
Tue Feb  2 17:57:12 2010
ClamAV Signatures: 706625
Directories Scanned:
/home/delukard
/home/delukard/.cache
/home/delukard/.cache/compizconfig
/home/delukard/.cache/gedit
/home/delukard/.clamtk
/home/delukard/.clamtk/db
/home/delukard/.compiz/session
/home/delukard/.config
/home/delukard/.config/Empathy
/home/delukard/.config/compiz/compizconfig
/home/delukard/.config/gtk-2.0
/home/delukard/.config/smplayer
/home/delukard/.config/smplayer/file_settings/e
/home/delukard/.config/totem
/home/delukard/.dbus/session-bus
/home/delukard/.evolution/addressbook/local/system
/home/delukard/.fontconfig
/home/delukard/.gamix
/home/delukard/.gconf/apps/bluetooth-manager
/home/delukard/.gconf/apps/brasero/config
/home/delukard/.gconf/apps/brasero/config/priority
/home/delukard/.gconf/apps/compiz/general/allscreens/options
/home/delukard/.gconf/apps/compiz/general/screen0/options
/home/delukard/.gconf/apps/empathy/accounts
/home/delukard/.gconf/apps/empathy/ui
/home/delukard/.gconf/apps/eog/ui
/home/delukard/.gconf/apps/evolution/addressbook/self
/home/delukard/.gconf/apps/evolution/calendar
/home/delukard/.gconf/apps/evolution/calendar/notify
/home/delukard/.gconf/apps/file-roller/general
/home/delukard/.gconf/apps/file-roller/listing
/home/delukard/.gconf/apps/file-roller/ui
/home/delukard/.gconf/apps/gcalctool
/home/delukard/.gconf/apps/gedit-2/plugins/filebrowser/on_load
/home/delukard/.gconf/apps/gedit-2/preferences/ui/statusbar
/home/delukard/.gconf/apps/gnome-power-manager/actions
/home/delukard/.gconf/apps/gnome-power-manager/backlight
/home/delukard/.gconf/apps/gnome-power-manager/buttons
/home/delukard/.gconf/apps/gnome-power-manager/disks
/home/delukard/.gconf/apps/gnome-power-manager/timeout
/home/delukard/.gconf/apps/gnome-power-manager/ui
/home/delukard/.gconf/apps/gnome-terminal/profiles/Default
/home/delukard/.gconf/apps/gnome_settings_daemon/xrandr
/home/delukard/.gconf/apps/metacity/general
/home/delukard/.gconf/apps/miro
/home/delukard/.gconf/apps/miro/window
/home/delukard/.gconf/apps/nautilus/desktop-metadata/8@46@0@32@GB@32@Filesystem@46@volume
/home/delukard/.gconf/apps/nautilus/desktop-metadata/PRO-DUO@46@volume
/home/delukard/.gconf/apps/nautilus/desktop-metadata/directory
/home/delukard/.gconf/apps/nautilus/desktop-metadata/utileria@46@volume
/home/delukard/.gconf/apps/nautilus/preferences
/home/delukard/.gconf/apps/nm-applet
/home/delukard/.gconf/apps/panel/applets/clock_screen0
/home/delukard/.gconf/apps/panel/applets/clock_screen0/prefs
/home/delukard/.gconf/apps/panel/applets/fast_user_switch_screen0
/home/delukard/.gconf/apps/panel/applets/indicator_applet_screen0
/home/delukard/.gconf/apps/panel/applets/notification_area_screen0
/home/delukard/.gconf/apps/panel/applets/show_desktop_button_screen0
/home/delukard/.gconf/apps/panel/applets/trashapplet_screen0
/home/delukard/.gconf/apps/panel/applets/window_list_screen0
/home/delukard/.gconf/apps/panel/applets/window_list_screen0/prefs
/home/delukard/.gconf/apps/panel/applets/workspace_switcher_screen0
/home/delukard/.gconf/apps/panel/applets/workspace_switcher_screen0/prefs
/home/delukard/.gconf/apps/panel/general
/home/delukard/.gconf/apps/panel/objects/browser_launcher_screen0
/home/delukard/.gconf/apps/panel/objects/menu_bar_screen0
/home/delukard/.gconf/apps/panel/objects/yelp_launcher_screen0
/home/delukard/.gconf/apps/panel/toplevels/bottom_panel_screen0
/home/delukard/.gconf/apps/panel/toplevels/bottom_panel_screen0/background
/home/delukard/.gconf/apps/panel/toplevels/top_panel_screen0
/home/delukard/.gconf/apps/panel/toplevels/top_panel_screen0/background
/home/delukard/.gconf/apps/procman
/home/delukard/.gconf/apps/procman/disktreenew
/home/delukard/.gconf/apps/procman/proctree
/home/delukard/.gconf/apps/rhythmbox
/home/delukard/.gconf/apps/rhythmbox/plugins/artdisplay
/home/delukard/.gconf/apps/rhythmbox/plugins/audiocd
/home/delukard/.gconf/apps/rhythmbox/plugins/audioscrobbler
/home/delukard/.gconf/apps/rhythmbox/plugins/cd-recorder
/home/delukard/.gconf/apps/rhythmbox/plugins/daap
/home/delukard/.gconf/apps/rhythmbox/plugins/generic-player
/home/delukard/.gconf/apps/rhythmbox/plugins/ipod
/home/delukard/.gconf/apps/rhythmbox/plugins/iradio
/home/delukard/.gconf/apps/rhythmbox/plugins/jamendo
/home/delukard/.gconf/apps/rhythmbox/plugins/magnatune
/home/delukard/.gconf/apps/rhythmbox/plugins/mmkeys
/home/delukard/.gconf/apps/rhythmbox/plugins/status-icon
/home/delukard/.gconf/apps/rhythmbox/plugins/visualizer
/home/delukard/.gconf/apps/rhythmbox/state
/home/delukard/.gconf/apps/rhythmbox/state/iradio
/home/delukard/.gconf/apps/rhythmbox/state/library
/home/delukard/.gconf/apps/rhythmbox/state/podcast
/home/delukard/.gconf/apps/sysinfo
/home/delukard/.gconf/apps/totem
/home/delukard/.gconf/apps/totem/plugins/bbc
/home/delukard/.gconf/apps/totem/plugins/media_player_keys
/home/delukard/.gconf/apps/totem/plugins/movie-properties
/home/delukard/.gconf/apps/totem/plugins/screensaver
/home/delukard/.gconf/apps/totem/plugins/screenshot
/home/delukard/.gconf/apps/totem/plugins/skipto
/home/delukard/.gconf/apps/totem/plugins/youtube
/home/delukard/.gconf/apps/update-manager
/home/delukard/.gconf/desktop/gnome/accessibility/keyboard
/home/delukard/.gconf/desktop/gnome/applications/window_manager
/home/delukard/.gconf/desktop/gnome/background
/home/delukard/.gconf/desktop/gnome/interface
/home/delukard/.gconf/desktop/gnome/peripherals/keyboard/host-delukard-laptop/0
/home/delukard/.gconf/desktop/gnome/peripherals/keyboard/kbd
/home/delukard/.gconf/desktop/gnome/peripherals/mouse
/home/delukard/.gconf/desktop/gnome/peripherals/touchpad
/home/delukard/.gconf/desktop/gnome/sound
/home/delukard/.gconf/system/networking/connections/1/802-11-wireless
/home/delukard/.gconf/system/networking/connections/1/802-11-wireless-security
/home/delukard/.gconf/system/networking/connections/1/connection
/home/delukard/.gconfd
/home/delukard/.gnome2
/home/delukard/.gnome2/accels
/home/delukard/.gnome2/gedit
/home/delukard/.gnome2/keyrings
/home/delukard/.gnupg
/home/delukard/.gstreamer-0.10
/home/delukard/.icons/GNOME_alternatives
/home/delukard/.icons/GNOME_alternatives/16x16/actions
/home/delukard/.icons/GNOME_alternatives/16x16/places
/home/delukard/.icons/GNOME_alternatives/16x16/status
/home/delukard/.icons/GNOME_alternatives/22x22/actions
/home/delukard/.icons/GNOME_alternatives/22x22/places
/home/delukard/.icons/GNOME_alternatives/22x22/status
/home/delukard/.icons/GNOME_alternatives/24x24/actions
/home/delukard/.icons/GNOME_alternatives/24x24/places
/home/delukard/.icons/GNOME_alternatives/24x24/status
/home/delukard/.icons/GNOME_alternatives/32x32/actions
/home/delukard/.icons/GNOME_alternatives/32x32/places
/home/delukard/.icons/GNOME_alternatives/32x32/status
/home/delukard/.icons/GNOME_alternatives/scalable/actions
/home/delukard/.icons/GNOME_alternatives/scalable/places
/home/delukard/.icons/GNOME_alternatives/scalable/status
/home/delukard/.icons/Gorilla
/home/delukard/.icons/Gorilla/scalable/actions
/home/delukard/.icons/Gorilla/scalable/apps
/home/delukard/.icons/Gorilla/scalable/categories
/home/delukard/.icons/Gorilla/scalable/devices
/home/delukard/.icons/Gorilla/scalable/emblems
/home/delukard/.icons/Gorilla/scalable/emotes
/home/delukard/.icons/Gorilla/scalable/mimetypes
/home/delukard/.icons/Gorilla/scalable/places
/home/delukard/.icons/Gorilla/scalable/status
/home/delukard/.icons/Kreski-Lines
/home/delukard/.icons/Kreski-Lines/32x32/filesystems
/home/delukard/.icons/Kreski-Lines/64x64/apps
/home/delukard/.icons/Kreski-Lines/64x64/devices
/home/delukard/.icons/Kreski-Lines/64x64/emblems
/home/delukard/.icons/Kreski-Lines/64x64/filesystems
/home/delukard/.icons/Kreski-Lines/64x64/mimetypes
/home/delukard/.icons/OpenWorld
/home/delukard/.icons/OpenWorld/48x48/apps
/home/delukard/.icons/OpenWorld/48x48/categories
/home/delukard/.icons/OpenWorld/48x48/devices
/home/delukard/.icons/OpenWorld/48x48/emblems
/home/delukard/.icons/OpenWorld/48x48/filesystems
/home/delukard/.icons/OpenWorld/48x48/mimetypes
/home/delukard/.icons/OpenWorld/48x48/places
/home/delukard/.icons/OpenWorld/48x48/status
/home/delukard/.icons/OpenWorld/48x48/stock
/home/delukard/.icons/SmoothGNOME
/home/delukard/.icons/SmoothGNOME/16x16/gtk
/home/delukard/.icons/SmoothGNOME/24x24/gtk
/home/delukard/.icons/SmoothGNOME/36x36/apps
/home/delukard/.icons/SmoothGNOME/48x48/apps
/home/delukard/.icons/SmoothGNOME/48x48/emblems
/home/delukard/.icons/SmoothGNOME/48x48/filesystems
/home/delukard/.icons/SmoothGNOME/48x48/mimetypes
/home/delukard/.icons/SmoothGNOME/cursors
/home/delukard/.icons/YattaBlues
/home/delukard/.icons/YattaBlues/32x32/emblems
/home/delukard/.icons/YattaBlues/32x32/emblems/oth
/home/delukard/.icons/YattaBlues/scalable/devices
/home/delukard/.icons/YattaBlues/scalable/devices (copy)
/home/delukard/.icons/YattaBlues/scalable/emblems
/home/delukard/.icons/YattaBlues/scalable/filesystems
/home/delukard/.icons/YattaBlues/scalable/mimetypes
/home/delukard/.kde/share/apps/kconf_update/log
/home/delukard/.kde/share/config
/home/delukard/.local/share/Trash/files
/home/delukard/.local/share/Trash/info
/home/delukard/.local/share/applications
/home/delukard/.local/share/gvfs-metadata
/home/delukard/.local/share/rhythmbox
/home/delukard/.miro
/home/delukard/.miro/icon-cache
/home/delukard/.miro/mozilla
/home/delukard/.miro/mozilla/Cache
/home/delukard/.mission-control/accounts
/home/delukard/.mozilla/firefox
/home/delukard/.mozilla/firefox/aoub5n9q.default
/home/delukard/.mozilla/firefox/aoub5n9q.default/Cache
/home/delukard/.mozilla/firefox/aoub5n9q.default/adblockplus
/home/delukard/.mozilla/firefox/aoub5n9q.default/bookmarkbackups
/home/delukard/.mozilla/firefox/aoub5n9q.default/chrome
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/tabscope@xuldev.org
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/tabscope@xuldev.org/chrome
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/tabscope@xuldev.org/defaults/preferences
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{66E978CD-981F-47DF-AC42-E3CF417C1467}
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{66E978CD-981F-47DF-AC42-E3CF417C1467}/chrome/content
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{66E978CD-981F-47DF-AC42-E3CF417C1467}/defaults/preferences
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content/colorPicker
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/locale/en-US
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/skin/classic
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/components
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/defaults/preferences
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ar
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/bg-BG
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ca-AD
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/cs-CZ
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/da-DK
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/de-DE
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/el-GR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/en-GB
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/es-AR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/es-ES
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/et-EE
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/fi-FI
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/fr
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/fr-FR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ga-IE
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/gl-ES
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/he-IL
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/hu-HU
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/it-IT
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ja-JP
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/kk-KZ
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ko-KR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/lt-LT
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/mn-MN
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/nl-NL
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pl-PL
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pt-BR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pt-PT
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ro-RO
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ru-RU
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/si-LK
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/sk-SK
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/sr-RS
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/sv-SE
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/tr-TR
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/uk-UA
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/vi-VN
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/zh-CN
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/zh-TW
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}/META-INF
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{a0d7ccb3-214d-498b-b4aa-0e8fda9a7bf7}/chrome
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/META-INF
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/chrome
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/components
/home/delukard/.mozilla/firefox/aoub5n9q.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults/preferences
/home/delukard/.mplayer
/home/delukard/.pulse
/home/delukard/.themes/Clearlooks2-Squared-Berries/metacity-1
/home/delukard/.themes/GreenHeart
/home/delukard/.themes/GreenHeart/gtk-2.0
/home/delukard/.themes/Quiet-Environment-v2
/home/delukard/.themes/Quiet-Environment-v2/metacity-1
/home/delukard/.themes/Quiet-Graphite
/home/delukard/.themes/Quiet-Graphite/metacity-1
/home/delukard/.themes/Quiet-Purple-2K6
/home/delukard/.themes/Quiet-Purple-2K6/metacity-1
/home/delukard/.themes/ShinyBlack
/home/delukard/.themes/ShinyBlack/gtk-2.0
/home/delukard/.themes/Tetelestai-Modern/metacity-1
/home/delukard/.themes/ThinMC/metacity-1
/home/delukard/.themes/W2k/metacity-1
/home/delukard/.themes/c2
/home/delukard/.themes/c2/gtk-2.0
/home/delukard/.themes/c2/metacity-1
/home/delukard/.thumbnails/fail/gnome-thumbnail-factory
/home/delukard/.thumbnails/normal
/home/delukard/.update-manager-core
/home/delukard/.update-notifier
/home/delukard/.xine
/home/delukard/Desktop
/home/delukard/Desktop/linux themes/borders
/home/delukard/Desktop/linux themes/controls
/home/delukard/Desktop/linux themes/icons
/home/delukard/Desktop/musica
/home/delukard/Pictures
```

Found 1 possible virus (3395 files scanned).

/home/delukard/.mozilla/firefox/aoub5n9q.default/Cache/662F157Cd01
BTW can i use ubuntu to clean infected usb drives? is clamav good at removing them without risking the ubuntu install?

---

### Post by yogesh.girikumar on 2010-02-03
Hi,


       Installing software using the software center and installing them using the terminal are both pretty safe.

       The Virus that was detected could have been installed when you installed the themes. Sometimes, some themes carry malicious code. These themes are usually removed quickly. But some might have slipped through inspection.


       There are hardly any viruses that target Linux operating systems, thanks to the community that constantly keeps plugging security holes and vulnerabilities and fixing issues.. Any virus that it detects could most likely have been Windows viruses. When somebody runs a Linux server with a lot of Windows clients, it is important to protect the clients from viruses. That's where ClamAV fits in.


       P.S. Clam AV is only a virus scanner and it won't be able to remove the virus or clean the infected file.


But you can use this to remove the infected file.

   ```
$ sudo clamscan --remove /home
```      But be careful, this is not entirely safe. Make sure you don't delete any important file. See links below.
       Here are some links that you might find interesting.
       
[LIST=1]
[*][https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
[*]Here is why you need antivirus in linux: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[/LIST]
       **To Clean USB Drive**

       **Option 1: Using Clamtk**

       Clamtk is a GUI based front end for the command line based clamav.

       1. Open clamtk by going to Applications -> System tools -> Virus Scanner
2. Click system wide if prompted
3. Click on directory
4. Select the USB as the directory, select necessary options by checking the checkboxes and click ok.
5. Results are displayed below.
       
[IMG]http://www.imagepundit.com/images/clamtk.png[/IMG]

       **Option 2: command line**
       1. Go to Applications -> Accesories -> Terminal
2. Type the following code.

   ```
$ sudo clamscan -r /media/USB_DISK
```   Where USB_DISK is the name of your USB drive.

HTH
Yogesh

---

### Post by delukard on 2010-02-03
ty vm.
Before i saw this answer i closed firefox and rescan home, and clamav found the virus but this time i could remove it.

This was on my laptop dual booting windows7x64 and ubuntu 64 9.10 (both freshly installed)

i'm typing this on my desktop wich has a dual boot(xp64 and ubuntu  64 9.10)
and doing full scan on windows partitions.
thank's for the help!

---

### Post by mikewhatever on 2010-02-03
I'd advise stop being paranoid. The file in question was in Firefox cache and was labeled as **possible** virus. Note, possible != it is. You can try scanning your Windows partitions with Clam, but there are more products for Windows to do just that, including Clam. Anyway, good luck with that.

---

### Post by ebozzz on 2010-02-04
> **mikewhatever said:**
> The file in question was in Firefox cache and was labeled as **possible** virus.

Yep, clearing then cache should have removed the possible threat.

---

### Post by earhear on 2010-09-02
I've just started using Linux and I'm loving it.  I've one partition set aside that contains all my previous windows applications.  Recently, after scanning through my PC with ClamAV, I've detected that some of these .exe files have been infected.  
I would prefer to have them cleaned, not deleted.  How, do I do this?

---

### Post by OpSecShellshock on 2010-09-02
> **earhear said:**
> I've just started using Linux and I'm loving it.  I've one partition set aside that contains all my previous windows applications.  Recently, after scanning through my PC with ClamAV, I've detected that some of these .exe files have been infected.  
I would prefer to have them cleaned, not deleted.  How, do I do this?

Depends on what they are. If they're trojans, then the entire file was malicious to begin with, so there's no way to clean it. If they're PUPs (potentially unwanted programs) then it just means that they warrant looking into a little more to see if you really want them, not that they're definitely malicious. What exactly is the scanner saying about the files you're concerned about? Has it identified them as a specific type?

---

### Post by earhear on 2010-09-02
There are 5 types - Heuristics.Broken.Executable, Heuristics.Encrypted.Zip, Trojan.Agent-165292, Trojan.Keygen-17 and Trojan.W32.HotKeysHook.A

---

### Post by bodhi.zazen on 2010-09-02
> **earhear said:**
> I would prefer to have them cleaned, not deleted.  How, do I do this?

I know of no linux tools that will clean the files, you delete them.

Because of the ever evolving nature of viruses it would be difficult to clean files and you would almost certainly need to do it manually.

---

### Post by OpSecShellshock on 2010-09-02
> **earhear said:**
> There are 5 types - Heuristics.Broken.Executable, Heuristics.Encrypted.Zip, Trojan.Agent-165292, Trojan.Keygen-17 and Trojan.W32.HotKeysHook.A
 
Well as I mentioned, the trojans simply have to go, as to "clean" them would leave nothing behind anyway. The Encrypted.Zip means just that: it's an encrypted zip file and so there's no way for the scanner to know what's in it. You'd need to extract it and then scan the extracted files. I'm not entirely sure about the broken executable, but I've seen it mentioned before. If I'm guessing, I'd suggest that perhaps the executable has remained, but that other files associated with the software and referenced in the executable's routines are no longer present--so it wouldn't run. Then again, perhaps it was specifically designed to crash so that arbitrary code could be run, which would make it a trojan (in which case, see above).

Either way, they're all Windows-only.

---

### Post by earhear on 2010-09-04
Noted and thank you.

---

