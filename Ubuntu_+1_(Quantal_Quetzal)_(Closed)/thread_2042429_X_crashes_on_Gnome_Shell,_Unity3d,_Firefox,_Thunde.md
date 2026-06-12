---
title: "X crashes on: Gnome Shell, Unity3d, Firefox, Thunderbird"
date: 2012-08-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Wise Ferret on 2012-08-14
I just upgraded to Quantal and I have the following issues:

1. Logging into Gnome Shell or Unity 3d crashes X immediately and returns me to lightDM.
2. Starting Firefox and Thunderbird has a similar effect.

I use nvidia proprietary driver, and 3d apps seem to work fine.

I corrected all the problematic fontconfig files (see here: [http://ubuntuforums.org/showpost.php?p=12159762&postcount=13](http://ubuntuforums.org/showpost.php?p=12159762&postcount=13)), so they are not the problem.

Here is my xsession-error file:
```
org.gtk.vfs.MountTracker.listMountableInfo call failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker (g-dbus-error-quark, 19)
gnome-session[7446]: WARNING: Could not parse desktop file /home/yotam/.config/autostart/gnome-volume-control-applet.desktop: Key file does not have key 'Name'
gnome-session[7446]: WARNING: could not read /home/yotam/.config/autostart/gnome-volume-control-applet.desktop
gnome-session[7446]: WARNING: Could not parse desktop file /home/yotam/.config/autostart/orca-autostart.desktop: Key file does not have key 'Name'
gnome-session[7446]: WARNING: could not read /home/yotam/.config/autostart/orca-autostart.desktop
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: GConf key '/apps/metacity/general/visual_bell_type' is set to an invalid value
Window manager warning: GConf key '/apps/metacity/general/action_double_click_titlebar' is set to an invalid value
Window manager warning: GConf key '/apps/metacity/general/action_middle_click_titlebar' is set to an invalid value

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed

(metacity:7527): GConf-CRITICAL **: gconf_value_get_string: assertion `value->type == GCONF_VALUE_STRING' failed
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel/libpanelplugin-appname.so" 
Gtk-Message: Failed to load module "canberra-gtk-module"
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panelGtk-Message: Failed to load module "canberra-gtk-module"
: [DEBUG] Loading panel plugin: "/usr/lib/x86_64-linux-gnu/unity-2d/plugins/panel/libpanelplugin-separator.so" 
Tracker-Message: Setting up monitor for changes to config file:'/home/yotam/.config/tracker/tracker-miner-fs.cfg'
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
Tracker-Message: Setting up monitor for changes to config file:'/home/yotam/.config/tracker/tracker-store.cfg'
Tracker-Message: Setting up monitor for changes to config file:'/home/yotam/.config/tracker/tracker-store.cfg'

(tracker-store:7553): Tracker-CRITICAL **: D-Bus service name:'org.freedesktop.Tracker1' is already taken, perhaps the daemon is already running?
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: applet now removed from the notification area
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-shellunity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
: [WARNING] libindicator: Desktop file '/home/yotam/.local/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Unable to find group 'NewWindow Shortcut Group'
unity-2d-shell: [WARNING] libindicator: Desktop file '/home/yotam/.local/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xc00014
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
** Message: moving back from GtkStatusIcon to indicator
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1600002 (unity-2d-s)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060647193:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060647611:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060648752:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060649339:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060650119:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060651407:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1060652242:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1061167047:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1061167746:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /usr/lib/chromium-browser/chromium-browser: undefined symbol: menu_proxy_module_load
[7867:7867:1061168948:ERROR:browser_main_loop.cc(154)] Gtk: Failed to load type module: (null)

unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://ubuntuone-installer.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://ubuntuone-installer.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
Nautilus-Share-Message: Called "net usershare info" but it failed: &#8207;'net usershare' &#1495;&#1494;&#1512; &#1506;&#1501; &#1513;&#1490;&#1497;&#1488;&#1492; 255:&#8207; net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```
Any ideas?

---

### Post by mc4man on 2012-08-14
Same as other thread (& a well known issue), though no 'if's' needed here
You've upgraded xserver packages to the 1.13 version by having the proposed repo enabled

So either remove nvidia drivers & use nouveau or downgrade back to the 1.12 xserver packages
(downgrading can be made much easier if you first remove all the uneeded xserver packages 
Or stick it out, use a 2d session without FF & TB

---

### Post by Wise Ferret on 2012-08-14
> **mc4man said:**
> So either remove nvidia drivers & use nouveau or downgrade back to the 1.12 xserver packages
(downgrading can be made much easier if you first remove all the uneeded xserver packages 
Or stick it out, use a 2d session without FF & TB

Thanks, mc4man!

---

### Post by xeizo on 2012-08-15
> **mc4man said:**
> Same as other thread (& a well known issue), though no 'if's' needed here
You've upgraded xserver packages to the 1.13 version by having the proposed repo enabled

So either remove nvidia drivers & use nouveau or downgrade back to the 1.12 xserver packages
(downgrading can be made much easier if you first remove all the uneeded xserver packages 
Or stick it out, use a 2d session without FF & TB

Except Unity 2D is now removed, so in my case I had to go to the xubuntu-desktop. Strange that a bug this serious is so presistent over several days ...
I run Windows Firefox under Wine instead, to get Firefox-functionality missing in Chromium(plugins are superior), works ok.

---

### Post by Harry33 on 2012-08-16
> **xeizo said:**
> Except Unity 2D is now removed, so in my case I had to go to the xubuntu-desktop. Strange that a bug this serious is so presistent over several days ...
I run Windows Firefox under Wine instead, to get Firefox-functionality missing in Chromium(plugins are superior), works ok.

The fact is, however, that xserver 1.13 is in the proposed repo, not in the main repo.
So QQ works just fine with proposed repo unenabled and with old xserver 1.12.
The function of the proposed repo is to have the packages better tested before uploading to the main section.
Anyways, the issue is very much outside of Canonical, there is nothing they can do about this.
It seems that xserver 1.13 itself is also more or less fine, and works with open source drivers. This suggests, that the problem here is in the nvidia graphical drivers (blob). Only nvidia developers can fix this "only preliminary support".

---

### Post by xeizo on 2012-08-16
> **Harry33 said:**
> The fact is, however, that xserver 1.13 is in the proposed repo, not in the main repo.
So QQ works just fine with proposed repo unenabled and with old xserver 1.12.
The function of the proposed repo is to have the packages better tested before uploading to the main section.
Anyways, the issue is very much outside of Canonical, there is nothing they can do about this.
It seems that xserver 1.13 itself is also more or less fine, and works with open source drivers. This suggests, that the problem here is in the nvidia graphical drivers (blob). Only nvidia developers can fix this "only preliminary support".
 
That is true, nevertheless it is strange that only Mozilla and Unity 3D are affected, other programs including hardware demanding Windows games under Wine works just fine ...

---

### Post by Harry33 on 2012-08-16
> **xeizo said:**
> That is true, nevertheless it is strange that only Mozilla and Unity 3D are affected, other programs including hardware demanding Windows games under Wine works just fine ...

Gnome-shell doesn't work either.

---

### Post by mc4man on 2012-08-17
Well xorg* is now  out of proposed & SSDD here for 3d with nvidia

---

### Post by Sworddragon on 2012-08-17
The XServer 1.12.99 packages are now in the main repository and doing the troubles as explained here. I have now tried some things a few hours to find a solution and the best that I could find was to downgrade the xserver-xorg-*, nvidia-*, linux-image-* and linux-headers-* packages to the Precise version.

---

### Post by Wise Ferret on 2012-08-17
> **Sworddragon said:**
> The XServer 1.12.99 packages are now in the main repository and doing the troubles as explained here. I have now tried some things a few hours to find a solution and the best that I could find was to downgrade the xserver-xorg-*, nvidia-*, linux-image-* and linux-headers-* packages to the Precise version.

Yes, that's quite impressive. Every update is making the situation worse. First nvidia was broken, then we could not use unity2D any more, then the yet-incompatible xorg went into main, and now there is an update to nvidia-current-updates which should resolve this somehow but I cannot install it, because it requires xorg-video-abi-11 or xorg-video-abi-12 which are not installable (if they are even packages).

---

### Post by cariboo on 2012-08-17
> **Wise Ferret said:**
> Yes, that's quite impressive. Every update is making the situation worse. First nvidia was broken, then we could not use unity2D any more, then the yet-incompatible xorg went into main, and now there is an update to nvidia-current-updates which should resolve this somehow but I cannot install it, because it requires xorg-video-abi-11 or xorg-video-abi-12 which are not installable (if they are even packages).

The closed source Nvidia drivers from the repositories are now marked as uninstallable, so your only choices are the nouvea driver, or those from xorg-edgers. Isn't running a development version fun? :-)

---

### Post by Harry33 on 2012-08-18
> **Sworddragon said:**
> The XServer 1.12.99 packages are now in the main repository and doing the troubles as explained here. I have now tried some things a few hours to find a solution and the best that I could find was to downgrade the xserver-xorg-*, nvidia-*, linux-image-* and linux-headers-* packages to the Precise version.

I only had to downgrade the xserver to the 1.12 branch.
The latest nvidia-current_304.37 (xorg-edgers)
and the latest kernel (3.5.0-11.11) works just fine.

It is true that the latest nvidia-current in official repos of QQ (v. 304.32 beta) is now uninstallable on a xserver_1.13 setup.
The version in xorg-edgers (304.37) is not a beta, it is a certified version. But without a true xserver_1.13 support.

---

### Post by voyager6868 on 2012-08-18
For those who haven't updated the X server yet, an easy workaround to prevent it is to run, as root:

echo "xserver-xorg-core hold" | dpkg --set-selections

This allows you to keep getting updates, use the proprietary nvidia driver, etc., but will leave your X server at the current version (1.12).

---

### Post by effenberg0x0 on 2012-08-18
> **voyager6868 said:**
> For those who haven't updated the X server yet, an easy workaround to prevent it is to run, as root:

echo "xserver-xorg-core hold" | dpkg --set-selections

This allows you to keep getting updates, use the proprietary nvidia driver, etc., but will leave your X server at the current version (1.12).

Hey,

```
$ echo "xserver-xorg-core hold" | sudo dpkg --set-selections
$ dpkg --get-selections  | grep -i hold
xserver-xorg-core				hold

```

Also:```

grep -iHnr 'Status: hold' /var/lib/dpkg/status -A 10 -B 1
```

Good tip.

Regards,
Effenberg

**EDIT:** apt update&&upgrade still tried to update a couple more xserver/xorg things, which I added to hold just for safety:```

[18:58:35] ahsl@AL-DESK01:[~]: grep -iHnr 'Status: hold' /var/lib/dpkg/status -B 1
/var/lib/dpkg/status-11472-Package: xorg
/var/lib/dpkg/status:11473:Status: hold ok installed
--
/var/lib/dpkg/status-13659-Package: xserver-xorg-core
/var/lib/dpkg/status:13660:Status: hold ok installed
--
/var/lib/dpkg/status-20008-Package: xserver-xorg
/var/lib/dpkg/status:20009:Status: hold ok installed
--
/var/lib/dpkg/status-20873-Package: xserver-xorg-video-all
/var/lib/dpkg/status:20874:Status: hold ok installed
--
/var/lib/dpkg/status-50046-Package: xserver-xorg-input-all
/var/lib/dpkg/status:50047:Status: hold ok installed
[18:58:43] ahsl@AL-DESK01:[~]: 

```

---

### Post by VinDSL on 2012-08-18
> **Harry33 said:**
> I only had to downgrade the xserver to the 1.12 branch.
The latest nvidia-current_304.37 (xorg-edgers)
and the latest kernel (3.5.0-11.11) works just fine.[...]
Oh!  Now, that's funny, Harry.  Good one!  ;)

I did just as you said -- except, I accidentally downgraded to the 1.11 branch:

```
vindsl@Zuul:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.11.4-0ubuntu10.6
  Candidate: 2:1.12.99.904-0ubuntu1
  Version table:
     2:1.12.99.904-0ubuntu1 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
     2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages
 *** 2:1.11.4-0ubuntu10.6 0
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 
```

And, guess what?!?!?  It works!  LoL!  :D

I cannot tell you the last time I was able to log into Unity -- several weeks, for sure.  Seems like an eternity!

Actually, it's been so long that I couldn't remember how to use it -- you know, that sinking feeling -- sitting idle at the Unity desktop, and wondering how to bring up the non-existent menu. Bwahahahaha!

Anyway, all I changed was the xorg server...

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~
Current Date/Time: Sat Aug 18 16:04:21 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.6.0-030600rc2-generic
Unity Release: unity 6.2.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.37

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch
  Installed: 2:1.11.4-0ubuntu10.6

vindsl@Zuul:~$
```

Everything else is on the fringe edge...

Guess I'll go play with Unity for a while, then try GS.

Thanks!

---

### Post by Sworddragon on 2012-08-18
> **Harry33 said:**
> I only had to downgrade the xserver to the 1.12 branch.
The latest nvidia-current_304.37 (xorg-edgers)
and the latest kernel (3.5.0-11.11) works just fine.

I'm not using the xorg-edgers ppa which made it a little more complicated. nvidia-current 304.32-0* makes trouble with XServer 1.11 (it removes it if I remember correctly) and nvidia-current 295.40-0ubuntu1 wouldn't compile with the 3.5 kernel on my system.

---

### Post by Harry33 on 2012-08-19
> **Sworddragon said:**
> I'm not using the xorg-edgers ppa which made it a little more complicated. nvidia-current 304.32-0* makes trouble with XServer 1.11 (it removes it if I remember correctly) and nvidia-current 295.40-0ubuntu1 wouldn't compile with the 3.5 kernel on my system.

Well I think it is a good practise to use the latest stable nvidia-current. The one in QQ repos is not the latest, it is a beta.
The only thing to remember (when using xorg-edgers PPA and nvidia-current_304.37 from there) is not to update xserver to 1.13 branch (=> 1.12.9*).

ATM nvidia-current is the only package I use from xorg-edgers.
Also, xserver 1.12 branch works fine, no need to downgrade that to 1.11 branch.

You can find the QQ repo version (1.12.2) here:
[https://launchpad.net/ubuntu/+source/xorg-server/2:1.12.99.902-0ubuntu1](https://launchpad.net/ubuntu/+source/xorg-server/2:1.12.99.902-0ubuntu1)

It is not the latest, which is 1.12.3.
If you like, you can find that one here (xorg-edgers pool):
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xorg-server/)

---

### Post by VinDSL on 2012-08-19
I used the 1.11 branch (accidentally) last night.  It gave me a chance to check out Unity.

Fx worked fine, but TB would crash (out to the desktop) every time it started downloading message headers from a different mail account.  

BTW, I use IMAP exclusively, not POP3.  Maybe this is why some ppl are experiencing TB crashes, and others aren't.  Might depend on the protocol, yes?

Thanks, for the link to the edger's pool.  I didn't even know that pool existed.  LoL!

I think I'll try the 1.12.3 git next... after I get some "Black Magic" (coffee) in me.  :)

---

### Post by VinDSL on 2012-08-19
> **Sworddragon said:**
> I'm not using the xorg-edgers ppa which made it a little more complicated. nvidia-current 304.32-0* makes trouble with XServer 1.11 **[COLOR="DarkRed"](it removes it if I remember correctly)[/COLOR]** and nvidia-current 295.40-0ubuntu1 wouldn't compile with the 3.5 kernel on my system.
You probably know this already, but for others...

You *must* be extremely careful when mixing n' matching items from the edger's PPA.


SOURCE: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
> == Important notice ==

**[COLOR="DarkRed"]This PPA is currently meant to be used as a whole. Please do _not_ individually install packages from it, add it to your sources and let your package manager pull in every update.[/COLOR]** The packages here build against each other and compile different features based on whats available at build time. **[COLOR="DarkRed"]Do not assume that because it lets you install a DDX with just the driver and libdrm update that it will work.[/COLOR]** These packages are made with scripts that use the the current packages as the base, so **[COLOR="DarkRed"]some dependencies can be wrong and your package manager will not resolve that for you. (i.e. Synaptic ~VinDSL)[/COLOR]** If you want to individually install something from here, grab the source and rebuild it in your current environment instead.

** **[COLOR="DarkRed"]Please do not publish instructions for how to install from this archive without linking to this page![/COLOR]** Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **


We're all guilty of ignoring these "Important Notices".

For instance, I don't know anyone that adds the edger's PPA to their sources and lets the package manager pull in every update.

Anyway, caveat emptor, when using the "xorg crack pushers" PPA.  ;)

---

### Post by Harry33 on 2012-08-19
> **VinDSL said:**
> I used the 1.11 branch (accidentally) last night.  It gave me a chance to check out Unity.

Fx worked fine, but TB would crash (out to the desktop) every time it started downloading message headers from a different mail account.  

BTW, I use IMAP exclusively, not POP3.  Maybe this is why some ppl are experiencing TB crashes, and others aren't.  Might depend on the protocol, yes?

Thanks, for the link to the edger's pool.  I didn't even know that pool existed.  LoL!

I think I'll try the 1.12.3 git next... after I get some "Black Magic" (coffee) in me.  :)

About TB, I have always only used IMAP. I need to access my posts via mobile phone and webmail too. Never had any crashes with TB, though.

---

### Post by VinDSL on 2012-08-19
> **Harry33 said:**
> Never had any crashes with TB, though.
I read that comment a lot... in various threads.  It seems that TB works for you, or it doesn't.  Dittos for Fx.  I would judge it's a 50/50 proposition, at present.

I couldn't even get TB to run without disabling the extensions.

I ran:
```
thunderbird -safe-mode
```
[LIST]
[*]
[*]Disabled all extensions

[*]Started it up normally

[*]TB would download the message headers in this-or-that account, but...

[*]When TB started reading the next account, it spit me out to the desktop

[*]Every time I restarted TB, it would download more headers, crash, and return to the desktop.

[*]Yada, yada, yada, ad infinitum...
[/LIST]
I *suppose* if I had done it enough times, TB would have eventually downloaded all the message headers, but I grew tired of testing the theory.  It obviously wasn't working for me.

I started TB from CLI, ran a search for the error message on DuckDuckGo, and came up with pages n' pages of results, including results in these forums.  Unfortunately, I cannot pull it up in my browser history because I'm logged into LXDE right now, not Unity.

I think I'll try a wash, rinse & restyle of TB later today, and see if that works...

---

### Post by VinDSL on 2012-08-19
> **cariboo907 said:**
> Isn't running a development version fun? :-)
LoL!  This is GREAT!

I was soooo bored with 12.04, I was ready to give up testing.  Seriously.

But, that's the nature of LTS releases, isn't it? Devs don't wanna rock the boat (too much).

12.10 is making up for it, in spades!  :D

---

### Post by effenberg0x0 on 2012-08-19
> **VinDSL said:**
> I read that comment a lot... in various threads.  It seems that TB works for you, or it doesn't.  Dittos for Fx.  I would judge it's a 50/50 proposition, at present.

I couldn't even get TB to run without disabling the extensions.

I ran:
```
thunderbird -safe-mode
```
[LIST]
[*]
[*]Disabled all extensions

[*]Started it up normally

[*]TB would download the message headers in this-or-that account, but...

[*]When TB started reading the next account, it spit me out to the desktop

[*]Every time I restarted TB, it would download more headers, crash, and return to the desktop.

[*]Yada, yada, yada, ad infinitum...
[/LIST]
I *suppose* if I had done it enough times, TB would have eventually downloaded all the message headers, but I grew tired of testing the theory.  It obviously wasn't working for me.

I started TB from CLI, ran a search for the error message on DuckDuckGo, and came up with pages n' pages of results, including results in these forums.  Unfortunately, I cannot pull it up in my browser history because I'm logged into LXDE right now, not Unity.

I think I'll try a wash, rinse & restyle of TB later today, and see if that works...

Hey Vin,
I use TB heavily on the DR. I also have my corp mail (IMAP) in a PP laptop and smartphone, but it's important for me to have it working on the Dev. Release (work related stuff). This version is solid for me so far:
```
[10:58:23] ahsl@AL-DESK01:[~]: cat /etc/apt/preferences
Package: thunderbird*
Pin: version 12.0.1+build1-0ubuntu0.12.04.1
Pin-Priority: 1001

```
I have the standard addons plus lightning and tonequilla.

TIP: All the times I had problems with TB in the development releases I found out the best way to fix it was to move/backup the $HOME TB profile folder and let TB re-create it again from scratch.

You mentioned a restyle. One of my main gripes with TB is that it's too white for me, it contributes to my constant headache (too many hours in the PC everyday) :| I try to use darkthemes in everything here (like using Stylish for chromium, Dark Juno for eclipse), etc. I'd love to run a dark theme on TB (like TT DeepDark 2.2.1 addon) but these theme addons are never compatible with the testing version. 

Now, considering your amazing and well-known desktop design/artistic skills, I got excited about the possibility of you theming it. Please let me know of your TB customization (and Share them!) :) 

Regards,
Effenberg

---

### Post by VinDSL on 2012-08-19
> **effenberg0x0 said:**
> You mentioned a restyle. One of my main gripes with TB is that it's too white for me, it contributes to my constant headache (too many hours in the PC everyday) :| I try to use darkthemes in everything here (like using Stylish for chromium, Dark Juno for eclipse), etc. I'd love to run a dark theme on TB (like TT DeepDark 2.2.1 addon) but these theme addons are never compatible with the testing version.[...]
w00t!  Xserver 1.12.3 git allowed me to start TB successfully.  :)

I hear ya on the "too white" TB interface, so I played around with it a little.

Are you looking for something like this -- or is it too dark?!?!?


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-2.png")[/INDENT]


Personally, I like dark themes with light windows -- an odd combination -- but, that's what I use.

It's a little hard for me to judge what would be acceptable in a TB theme.


**EDIT**

GS is working now, too!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-3.png")[/INDENT]


Bring on the breakage!  :D

---

### Post by effenberg0x0 on 2012-08-19
> **VinDSL said:**
> w00t!  Xserver 1.12.3 git allowed me to start TB successfully.  :)

I hear ya on the "too white" TB interface, so I played around with it a little.

Are you looking for something like this -- or is it too dark?!?!?


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-2.png")[/INDENT]


Personally, I like dark themes with light windows -- an odd combination -- but, that's what I use.

It's a little hard for me to judge what would be acceptable in a TB theme.


**EDIT**

GS is working now, too!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-19-aug-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-aug-2012-3.png")[/INDENT]


Bring on the breakage!  :D

Wow, that's beautiful, *exactly* what I wanted :) Care to share some tips here? Did you do it manually via CSS or used a addon?

Regards,
Effenberg

**EDIT:** It will match my eclipse :P Right now having Dark Juno in one monitor and Thunderbird in the other is a really aggressive contrast...
[ATTACH]222901[/ATTACH]

---

### Post by mc4man on 2012-08-19
In regards to xserver, nvidia, crashes ect.
Will be hopefully fixed shortly now that nvidia was Finally made aware of the issue 2 days ago
(even though it's been ongoing since 1.13 hit proposed or even earlier

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896/comments/6](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896/comments/6)

---

### Post by VinDSL on 2012-08-19
> **effenberg0x0 said:**
> Wow, that's beautiful, *exactly* what I wanted :) Care to share some tips here? Did you do it manually via CSS or used a addon?
Thanks!

Actually, I did that using a shotgun approach (for testing purposes):

[LIST]
[*]Window Theme: [Zukitwo Dark]("http://gnome-look.org/content/show.php/Zukitwo?content=140562")

[*]Icon Theme:  [ACYL 0.9.4]("http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910")

[*]GTK+ Theme:  [Elementary Dark]("http://satya164.deviantart.com/art/elementary-Dark-GTK3-Theme-244257862")
[/LIST]
That's it -- that's all I did. Took less than an hour. Simple pimple, eh what?  :D

And, of course, the theme changes are automatically applied to all GTK+3 windows, menues, et cetera.  GTK+2 items look a little spartan, but it's liveable.

If I had the time, I could probably extrapolate it backwards, e.g. reverse-engineer it, into a TB add-on, but that would be a new learning experience for me.

---

### Post by VinDSL on 2012-08-19
> **mc4man said:**
> In regards to xserver, nvidia, crashes ect.
Will be hopefully fixed shortly now that nvidia was Finally made aware of the issue 2 days ago
(even though it's been ongoing since 1.13 hit proposed or even earlier

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896/comments/6](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896/comments/6)
Good deal!

I was patiently, and happily, awaiting a fix.  I've been running LXDE/Openbox ever since Unity/GS quit working for me (some time ago) and having a good time with it.

Harry33 is the one that spurred me to action.  I read a post, yesterday, where he said the only thing you have to "downgrade" is the xorg-server-core -- and, I'll be darned if it didn't work.

Anyway, yes, you're right.  Soon, it will be a fond memory, I'm sure.

BTW, I'm actually enjoying GS.  That's what I'm using, as I type.  

Go figure...  ;)

---

### Post by effenberg0x0 on 2012-08-19
> **VinDSL said:**
> Good deal!

I was patiently, and happily, awaiting a fix.  I've been running LXDE/Openbox ever since Unity/GS quit working for me (some time ago) and having a good time with it.

Harry33 is the one that spurred me to action.  I read a post, yesterday, where he said the only thing you have to "downgrade" is the xorg-server-core -- and, I'll be darned if it didn't work.

Anyway, yes, you're right.  Soon, it will be a fond memory, I'm sure.

BTW, I'm actually enjoying GS.  That's what I'm using, as I type.  

Go figure...  ;)

After this breakage I have decided to be more careful about xserver+nvidia. I'll keep a working set pinned so it doesn't bork me out of testing all the rest. And then I'll only test xserver updates in secondary installs/partitions, etc.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-19
> **VinDSL said:**
> Thanks!

Actually, I did that using a shotgun approach (for testing purposes):

[LIST]
[*]Window Theme: [Zukitwo Dark]("http://gnome-look.org/content/show.php/Zukitwo?content=140562")

[*]Icon Theme:  [ACYL 0.9.4]("http://pobtott.deviantart.com/art/Any-Color-You-Like-175624910")

[*]GTK+ Theme:  [Elementary Dark]("http://satya164.deviantart.com/art/elementary-Dark-GTK3-Theme-244257862")
[/LIST]
That's it -- that's all I did. Took less than an hour. Simple pimple, eh what?  :D

And, of course, the theme changes are automatically applied to all GTK+3 windows, menues, et cetera.  GTK+2 items look a little spartan, but it's liveable.

If I had the time, I could probably extrapolate it backwards, e.g. reverse-engineer it, into a TB add-on, but that would be a new learning experience for me.

Hey, I can save you some time in investigating how theming works in TB. I have just installed "Disable Add-on Compatibility Checks 1.3". It's not a smart thing to do but I had to in order to test "TT DeepDark" AddOn. Look at the results:
[ATTACH]222906[/ATTACH]

It's almost there, I just have to find a way to fix the messages pane. 

TT DeepDark is a .jar, same method used in Eclipse. Once you open the .jar in Archive Manager you have a .css inside each directory:
[ATTACH]222908[/ATTACH]

Regards,
Effenberg

---

### Post by VinDSL on 2012-08-19
> **effenberg0x0 said:**
> After this breakage I have decided to be more careful about xserver+nvidia. I'll keep a working set pinned so it doesn't bork me out of testing all the rest. And then I'll only test xserver updates in secondary installs/partitions, etc.
Sounds like a prudent path.  Very good!

As for myself, I cannot stand it when "things just work."  My only concern is whether or not I have the tools (and wherewithal) necessary to fix problems.  Actually, I've made a career of it. And, it's put a lot of bread on our table, over the years.

You do a great job of articulating problems and fixes.  You're analytical and driven -- and I admire that in you.

Actually, I admire a lot of ppl in these forums.  That's why I hang around here so much.

I hope the X crashes go on forever...  LoL!  :D

---

### Post by effenberg0x0 on 2012-08-19
> **VinDSL said:**
> Sounds like a prudent path.  Very good!

As for myself, I cannot stand it when "things just work."  My only concern is whether or not I have the tools (and wherewithal) necessary to fix problems.  Actually, I've made a career of it. And, it's put a lot of bread on our table, over the years.

You do a great job of articulating problems and fixes.  You're analytical and driven -- and I admire that in you.

Actually, I admire a lot of ppl in these forums.  That's why I hang around here so much.

I hope the X crashes go on forever...  LoL!  :D
> **VinDSL said:**
> 
I hope the X crashes go on forever...  LoL!  :D

LOL :)  

Thank you for the kind words, it means a lot to me.

I think most of us here share the same thrill, which is why Ubuntu+1 is such an amazing community... For me it has always been about the challenge: Trying to understand why something broke and finding a way to work around it is how I got started with PCs, electronics, etc. When I was a kid I had no PC so I used to sneak into my school lab (they had some PC-XT machines) with screwdrivers and open their PCs until they caught me. Later when I got my own PC (a 286 with MS-DOS), I had no Modem, no BBS, no Internet, no Books, no Magazines and no friends with PCs to talk about it. I used to spend days and nights in debug.com trying to understand anything and using MS-EDIT to try to write BASIC scripts. Then I found a [dusty 70's book]("http://www.amazon.com/Algorithms-Structures-Prentice-Hall-Automatic-Computation/dp/0130224189") at a friends house that looked amazing, but it was in English (I was 11-years old, I couldn't read or write in English back then, I barely can now lol). So that was a challenge too lol... Later, when I managed to read it, I found out the examples were in Modula-2 language (I had no compiler for it, so I just read it over and over, but couldn't write or test anything). 

Many here at Ubuntu+1 told me similar stories, they have this same spirit... I definitely share your admiration for the people here. 

However, in recent cycles, with the growth in Ubuntu share and market awareness and all the changes, like the thing about making the dev release usable at all times, the challenge of getting more people into testing and, more importantly, making testing more relevant/better, I changed my point of view about things and goals. My main concern right now is how I can actively help increase Ubuntu market share in PCs. So, yes, I think I'm becoming more prudent. Or maybe just getting old :) 

Regards,
Effenberg

---

### Post by xeizo on 2012-08-20
I wonder if Linus Torvalds little hate performance against Nvidia have unconsciously affected Linux-developers in a negative way, such as it becoming easier to just neglect if things run with Nvidia or not instead of just making them run ...

Mabe not, but it was bad karma anyway.

I think it doesn't really matter how bad of a company Nvidia is as long as the infamous Nvidia-blob provides the absolutely best Linux experience. Especially when it comes to gaming, which is necessary if the Linux desktop is ever to get widespread acceptance.

---

### Post by ronacc on 2012-08-20
A few cycles back there was a very anti Nvidia bias around Ubuntu  which is really sad . True they haven't open sourced their driver , but they have kept their blob up to date in a very timely fashion and expended a good bit of effort to support Linux . I think it is a great mistake that a few hardcore idealists insist on causing the rest of us grief .

---

### Post by caryb on 2012-08-24
So am I the only one with this problem still???

Cary

---

### Post by effenberg0x0 on 2012-08-24
> **caryb said:**
> So am I the only one with this problem still???

Cary

Hi Cary, 

Did you read the other posts in this thread and probably about 90% of the latest threads here at Ubuntu+1?

We had a problem in which the combination of the latest xserver to nvidia proprietary driver breaks both Unity and Gnome-Shell. There are also mentions here and in many other distro boards about it. Many users also report problems with T-bird and Firefix. You'll find plenty of examples if you google for it. Like this: [http://www.nvnews.net/vbulletin/showthread.php?t=188017](http://www.nvnews.net/vbulletin/showthread.php?t=188017)

You're not the only one.

Regards,
EFfenberg

---

### Post by Stinger on 2012-08-24
> **effenberg0x0 said:**
>  Many users also report problems with T-bird and Firefix.
Firefix ? Are the Ubuntu developers considering yet another fork ? :biggrin:
Sorry couldn't help myself ;)

---

### Post by effenberg0x0 on 2012-08-24
> **Stinger said:**
> Firefix ? Are the Ubuntu developers considering yet another fork ? :biggrin:
Sorry couldn't help myself ;)

Lol, I'm not even gonna correct the typo, I love it, should be adopted as a product name for sure.

Regards,
Effenberg

---

### Post by caryb on 2012-08-24
> **effenberg0x0 said:**
> Hi Cary, 

Did you read the other posts in this thread and probably about 90% of the latest threads here at Ubuntu+1?

We had a problem in which the combination of the latest xserver to nvidia proprietary driver breaks both Unity and Gnome-Shell. There are also mentions here and in many other distro boards about it. Many users also report problems with T-bird and Firefix. You'll find plenty of examples if you google for it. Like this: [http://www.nvnews.net/vbulletin/showthread.php?t=188017](http://www.nvnews.net/vbulletin/showthread.php?t=188017)

You're not the only one.

Regards,
EFfenberg


Ok after RTFM I created a xorg.conf & added 

Section "Module"
    Disable "glx"
EndSection

Now have Nvidia driver with FF & T-Bird. Thanks EFfenberg :)

Cary

---

### Post by paul_in_london on 2012-08-24
> **caryb said:**
> Ok after RTFM I created a xorg.conf & added 

Section "Module"
    Disable "glx"
EndSection

Now have Nvidia driver with FF & T-Bird. Thanks EFfenberg :)

Cary

Aha! Thanks! I hadn't realised that this work-around for the problems with nvidia-current/xserver 1.13 is mentioned here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1037896)

Apparently it's "expected to be fixed in the next [nvidia-current] 304 release after 304.37".

I've stayed with the 1.13 xserver from xorg-edgers waiting for a fix so it's nice to be able to use FF again. :)

Mostly I use gnome classic (no effects) so it was just FF that was causing me problems. No major issues apart from that.

---

### Post by xeizo on 2012-08-25
> **caryb said:**
> Ok after RTFM I created a xorg.conf & added 

Section "Module"
    Disable "glx"
EndSection

Now have Nvidia driver with FF & T-Bird. Thanks EFfenberg :)

Cary

That would seems nice, except it grants you Mozilla alright, but then you can't play any games instead. I don't put in a 3D-card in a box not expecting to use 3D at all, to me it's still totally broken. Let's hope for 304.37+ ...

I locked X to 1.12, so 3D works, but that seems to cause a whole bunch of other problems. One is practically required to move to 1.13 by now ...

---

### Post by Harry33 on 2012-08-25
> **xeizo said:**
> 
...
I locked X to 1.12, so 3D works, but that seems to cause a whole bunch of other problems. One is practically required to move to 1.13 by now ...

What issues do you have with xserver_1.12 and nvidia-current_304.37 then?
I am using exactly those and I do not have any issues with them.

---

### Post by xeizo on 2012-08-25
> **Harry33 said:**
> What issues do you have with xserver_1.12 and nvidia-current_304.37 then?
I am using exactly those and I do not have any issues with them.

Actually it's 304.32-ubuntu6 in the repos, 304.37 is missing right now. For one, I can't file automatic bug reports because keeping a to old X. There's is lots of bugs right now, mostly filesystem related but who knows what kind of chain reaction using an old X causes. Mozilla and gaming works though.

---

### Post by Sworddragon on 2012-08-25
Instead of using XServer 1.11.4 I tried to use the old version from 12.*. I have installed xserver-common 2:1.12.99.902-0ubuntu1, xserver-xorg-core 2:1.12.99.902-0ubuntu1 and nvidia-current 304.32-0ubuntu3. After a restart of the XServer it still crashes if I'm starting Firefox. Which versions of which packages have I to install to get a working XServer 1.12.*?

---

### Post by kyleabaker on 2012-08-25
I installed nvidia-current last night and have noticed that as soon as I enter my password and proceed into a Unity session, my x server appears to crash.

I'm able to successfully login to a classic Gnome session though. Any idea how I can resolve this for Unity? Previously nouveau was crashing regularly and performance was not even close to ideal, so I'd like to stick with the proprietary drivers, but am wondering if something may not be configured correctly.

Thanks!

---

### Post by clivej on 2012-08-25
I am have the same issue.  Ive dropped back to Nouveau for the time being.

Nvidia current is being held back on my system for some reason 

```
sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable or
                           xorg-video-abi-12 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Is this the same on your system kyleabaker?

---

### Post by paul_in_london on 2012-08-25
See my post here (and that thread in general):

[http://ubuntuforums.org/showthread.php?t=2042429&page=4](http://ubuntuforums.org/showthread.php?t=2042429&page=4)

I don't use Unity at all and haven't tested with G-S (I'm on gnome classic), but if you're not bothered about 3D effects try the work-around of disabling glx in xorg.conf.

HTH.

---

### Post by cariboo on 2012-08-25
Merged two threads on the same subject

---

### Post by mc4man on 2012-08-25
> **Sworddragon said:**
> Instead of using XServer 1.11.4 I tried to use the old version from 12.*. I have installed xserver-common 2:1.12.99.902-0ubuntu1, xserver-xorg-core 2:1.12.99.902-0ubuntu1 and nvidia-current 304.32-0ubuntu3. After a restart of the XServer it still crashes if I'm starting Firefox. Which versions of which packages have I to install to get a working XServer 1.12.*?
Take this with care.. 
When I was bothering to downgrade xserver & kept nvidia I used this source's packages with no issue
[https://launchpad.net/ubuntu/quantal/amd64/xserver-xorg-core/2:1.12.1.902-1ubuntu1](https://launchpad.net/ubuntu/quantal/amd64/xserver-xorg-core/2:1.12.1.902-1ubuntu1)

At this point because I can use nouveau I no longer am holding X back & have no inclination to test a revert now (new install that had some hoop jumping to get going without login nonsense

---

### Post by Harry33 on 2012-08-26
I am using xserver_1.12 (1.12.3)+git20120709 and nvidia-current_304.37 (xorg-edgers PPA)
I always use only the release vesions of firefox and thunderbird.
Just upgraded today firefox to 15.0+build1 (official QQ repos) and that works fine.

However, I tried the 15.0~b5 version of TB.
And noticed it will immediately crash, cannot do anything with it.
So, I downgraded it back to the release version 14.0+build1.
That one works perfectly.

---

### Post by VinDSL on 2012-08-26
> **Harry33 said:**
> However, I tried the 15.0~b5 version of TB.
And noticed it will immediately crash, cannot do anything with it.
So, I downgraded it back to the release version 14.0+build1.
That one works perfectly.
Interesting!

TB is working fine here...


[INDENT][[IMG]http://vindsl.com/images/Screenshot from 2012-08-26 06:27:03(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot from 2012-08-26 06:27:03.png")[/INDENT]


Is this the same version you're running, i.e. trying to run?!?!?

If so (from reading your post) the only difference is, I'm running a xserver 1.13 install with a xserver 1.12 xserver-xorg-core.

Actually, everything is working great, right now...

---

### Post by Sworddragon on 2012-08-26
> **mc4man said:**
> Take this with care.. 
When I was bothering to downgrade xserver & kept nvidia I used this source's packages with no issue
[https://launchpad.net/ubuntu/quantal/amd64/xserver-xorg-core/2:1.12.1.902-1ubuntu1](https://launchpad.net/ubuntu/quantal/amd64/xserver-xorg-core/2:1.12.1.902-1ubuntu1)

I had even to install an older version of xserver-xorg-input-evdev to solve a dependency problem but it is now working fine.

---

### Post by Harry33 on 2012-08-26
> **VinDSL said:**
> Interesting!

TB is working fine here...
...
Is this the same version you're running, i.e. trying to run?!?!?

If so (from reading your post) the only difference is, I'm running a xserver 1.13 install with a xserver 1.12 xserver-xorg-core.

Actually, everything is working great, right now...

Yes I tried to run the latest TB there is in QQ repos (15.0~b5+build1-0ubuntu1).
It crashed already reading the IMAP server. :p
14.0+build1-0ubuntu2 is fine.

---

### Post by VinDSL on 2012-08-26
> **Harry33 said:**
> Yes I tried to run the latest TB there is in QQ repos (15.0~b5+build1-0ubuntu1).
It crashed already reading the IMAP server. :p
Hrm...

I'm at a loss, to understand why my setup is working.  I almost *feel* cheated.  LoL!  :D

There are 1000 ways To do an experiment wrong. I guess I accidentally stumbled on something right.

Oh, well, hopefully there will be more crashes coming down the pike...

---

### Post by VinDSL on 2012-08-27
Just wondering...

What's in your X Config file?

Here's mine:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.37  (buildd@actinium)  Mon Aug 13 18:38:27 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "IgnoreABI" "true"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    Option         "DPI" "96 x 96"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option         "GLXVBlank" "on"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by dino99 on 2012-08-27
with nouveau


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nouveau"
        Option "GLXVBlank" "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

x does not crash, but get garbage if plymouth-label & plymouth-theme are installed.

---

### Post by fluteflute on 2012-08-27
New version of the NVIDIA driver: [http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

"Fixed a bug that caused pre-release versions of X.Org xserver 1.13 to crash when certain GLX operations were performed, such as when starting Firefox."

---

### Post by paul_in_london on 2012-08-27
> **fluteflute said:**
> New version of the NVIDIA driver: [http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html](http://www.nvidia.com/object/linux-display-amd64-304.43-driver.html)

"Fixed a bug that caused pre-release versions of X.Org xserver 1.13 to crash when certain GLX operations were performed, such as when starting Firefox."

Thanks. Prefer to use debs though, so will wait for it to hit xorg-edgers.

---

### Post by kyleabaker on 2012-08-27
> **paul_in_london said:**
> Thanks. Prefer to use debs though, so will wait for it to hit xorg-edgers.

Agreed. However, I'm less interested in getting Firefox to run and more interested in getting Unity to run. Hoping to see some positive feedback soon! :popcorn:

---

### Post by Harry33 on 2012-08-27
> **VinDSL said:**
> Just wondering...

What's in your X Config file?

Here's mine:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.37  (buildd@actinium)  Mon Aug 13 18:38:27 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "IgnoreABI" "true"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    Option         "DPI" "96 x 96"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"Fixes include a GLX crash fix on X.Org Server 1.13, VDPAU hanging on YouTube, problems with [[COLOR=#234865][COLOR=#234865 !important][FONT=inherit !important][COLOR=#234865 !important][FONT=inherit !important]GNOME[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTE2OTM#") Settings Daemon and the display configuration, RandR updates for NVIDIA Settings, and a display palette bug.
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option         "GLXVBlank" "on"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I use xserver-xorg-input-evdev driver, so I do not need any input sections describing mouse nor keyboard. Also the "inputdevice" lines may be deleted from the server layout section.

---

### Post by Harry33 on 2012-08-27
> **paul_in_london said:**
> thanks. Prefer to use debs though, so will wait for it to hit xorg-edgers.
 
+1 :p

---

### Post by paul_in_london on 2012-08-27
> **kyleabaker said:**
> Agreed. However, I'm less interested in getting Firefox to run and more interested in getting Unity to run. Hoping to see some positive feedback soon! :popcorn:

I'm using:

```
paul@quantal-64:~$ X -version

X.Org X Server 1.12.99.905 (1.13.0 RC 5)
Release Date: 2012-08-21
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-23-generic x86_64 Ubuntu
Current Operating System: Linux quantal-64 3.6.0-030600rc3-generic #201208221735 SMP Wed Aug 22 21:36:32 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.6.0-030600rc3-generic root=UUID=c16f4cbf-43d3-45d7-b41e-a8ca3b339513 ro
Build Date: 26 August 2012  03:49:50PM
xorg-server 2:1.12.99.905-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
paul@quantal-64:~$ 
```

I don't even have unity installed, but FF works for me with this xorg.conf:

```
paul@quantal-64:~$ cat /etc/X11/xorg.conf
#
# Module section added by Paul 25/08/2012
# (to be able to use FF during xorg 1.13/nvidia mess)
#
[B][COLOR="Red"]Section "Module"
Disable "glx"
EndSection[/COLOR][/B]
#
Section "DRI"
Mode 0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection
Section "ServerFlags"
     Option "blank time" "0"
     Option "standby time" "0"
     Option "suspend time" "0"
     Option "off time" "0"
     Option "dpms" "false"
     Option "IgnoreABI" "True"
EndSection
paul@quantal-64:~$
```

Have you tried unity with glx disabled?

---

### Post by VinDSL on 2012-08-27
> **Harry33 said:**
> I use xserver-xorg-input-evdev driver, so I do not need any input sections describing mouse nor keyboard. Also the "inputdevice" lines may be deleted from the server layout section.
Heh!  Thanks, Harry!  Dino must be doing the same.

I just found that out the hard way -- the **hard-lock** way, actually. No input devices were recognized, once I hit Plymouth...

I tested Dino's X config.  All I did was replace the indentifiers, and it blew up my cobbled together system.

Been dancing on the keyboard for the past hour.  LoL!  :D

Anyway, I got it to boot into LXDE/Openbox now.  I'll hack it up, and see if I can get Unity/GS working again.

Looks like a permanent fix is upon us, but I appreciate the temporary breakage, all the same.

This is fun!

---

### Post by VinDSL on 2012-08-27
> **paul_in_london said:**
> Have you tried unity with glx disabled?
Right on cue, Paul.  Thanks!

I'm still fluffing around in LXDE.

I'll give that glx hack a whirl, and see what happens...

---

### Post by kyleabaker on 2012-08-27
> **paul_in_london said:**
> Have you tried unity with glx disabled?

I've not tried it yet. I've been working in Gnome Classic for a little while now and am reminiscing on Ubuntu of yesteryear, haha. I'm just planning to wait for a proper fix before I switch sessions back to Unity, but if I get curious enough I'll give your suggestion a try. :D

---

### Post by VinDSL on 2012-08-27
Here's one for you...


[INDENT][IMG]http://vindsl.com/images/2-xorg.confs-wtf.png[/IMG][/INDENT]


Never seen two xorg.confs in the same folder before!

How is that even possible -- two different files/different timestamps/same name?!?!?!?

Seriously?  Maybe that's part of the problem... :)

---

### Post by VinDSL on 2012-08-27
> **kyleabaker said:**
> I've not tried it yet.[...]
Okay, I tried it.

Running under xserver 1.13/nVidia 304.37, Unity boots, but it's featureless - no panel - no launcher, et cetera. 

GS doesn't boot at all.  At Plymouth, I get an error dialogue saying Gnome cannot be loaded.

Anyway, I tried all the usual tricks, and nothing seemed to work.

So, I'm back to my original hack - xserver 1.13/nVidia 304.37 install with a xserver 1.12 core.  Unity and GS both work on this oddball setup.

As an aside, it looks like "the fix" will only work with xserver 1.12.  Time will tell...

---

### Post by kyleabaker on 2012-08-27
> **VinDSL said:**
> Here's one for you...


[INDENT][IMG]http://vindsl.com/images/2-xorg.confs-wtf.png[/IMG][/INDENT]


Never seen two xorg.confs in the same folder before!

How is that even possible -- two different files/different timestamps/same name?!?!?!?

Seriously?  Maybe that's part of the problem... :)

One of the files has a space before the ".conf" extension. Not sure how that would have happened though.

---

### Post by kyleabaker on 2012-08-27
> **VinDSL said:**
> Okay, I tried it.

Running under xserver 1.13/nVidia 304.37, Unity boots, but it's featureless - no panel - no launcher, et cetera.

Thanks for the update. I guess I'll have to continue to be patient for Unity/nVidia to play nice together, haha.

---

### Post by VinDSL on 2012-08-27
> **kyleabaker said:**
> One of the files has a space before the ".conf" extension. Not sure how that would have happened though.
Oops!

Time for me to get new reading glasses...  :D

---

### Post by kyleabaker on 2012-08-27
I just tried logging into Unity after todays updates and it seems to be working fine so far. I'm using nvidia-current installed from edgers/ppa ftw.

---

### Post by Harry33 on 2012-08-28
> **kyleabaker said:**
> I just tried logging into Unity after todays updates and it seems to be working fine so far. I'm using nvidia-current installed from edgers/ppa ftw.

So you are using the newest certified nvidia-current_304.43, which does not break xserver_1.13 rc5 (1.12.99.905). The latter is in QQ official repos.

---

### Post by Harry33 on 2012-08-28
> **VinDSL said:**
> Interesting!

TB is working fine here...
...
Is this the same version you're running, i.e. trying to run?!?!?

If so (from reading your post) the only difference is, I'm running a xserver 1.13 install with a xserver 1.12 xserver-xorg-core.

Actually, everything is working great, right now...

Rigth now I am running the newest upstream stable release (15.0 build1)
and that one works fine. ):P

---

### Post by VinDSL on 2012-08-28
> **Harry33 said:**
> Rigth now I am running the newest upstream stable release (15.0 build1)
and that one works fine. ):P
Yes, nVidia-current 304.43 has washed away the rain!

I think it's a keeper...  ;)

---

### Post by Wise Ferret on 2012-08-28
All good now with the new driver :)

---

