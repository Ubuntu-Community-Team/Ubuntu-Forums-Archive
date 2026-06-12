---
title: "graphics no longer working after yesterdays update - desktop VM"
date: 2024-03-22
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-03-22
I have a 24.04 desktop VM running as a quest on my main Debian server. After updating it late yesterday, the graphics have stopped working. They work fine until after login, and they also work fine during shutdown. If I recall correctly, the grpahics also worked fine after the first re-boot after the update,because I remember seeing the new 24.04 background wallpaper. SSH into the VM works fine, which is how I am able to tell it to restart. Just wondering if others have experienced similar? A syslog segment from the last re-boot:

```
2024-03-22T08:54:07.506551-07:00 desk-nn gnome-shell[980]: Running GNOME Shell (using mutter 45.3) as a Wayland display server
2024-03-22T08:54:07.587010-07:00 desk-nn gnome-shell[980]: Made thread 'KMS thread' realtime scheduled
2024-03-22T08:54:07.730059-07:00 desk-nn gnome-shell[980]: Added device '/dev/dri/card0' (bochs-drm) using atomic mode setting.
2024-03-22T08:54:07.731582-07:00 desk-nn gnome-shell[980]: Failed to initialize accelerated iGPU/dGPU framebuffer sharing: Not hardware accelerated
2024-03-22T08:54:07.731686-07:00 desk-nn gnome-shell[980]: Created gbm renderer for '/dev/dri/card0'
2024-03-22T08:54:07.731800-07:00 desk-nn gnome-shell[980]: Boot VGA GPU /dev/dri/card0 selected as primary
2024-03-22T08:54:07.820837-07:00 desk-nn gnome-shell[980]: Disabling DMA buffer screen sharing (not hardware accelerated)
2024-03-22T08:54:07.827376-07:00 desk-nn /usr/libexec/gdm-wayland-session[953]: dbus-daemon[953]: [session uid=120 pid=953] Activating service name='org.a11y.Bus' requested by ':1.4' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:07.848640-07:00 desk-nn gnome-shell[980]: Using public X11 display :1024, (using :1025 for managed services)
2024-03-22T08:54:07.848791-07:00 desk-nn gnome-shell[980]: Using Wayland display name 'wayland-0'
2024-03-22T08:54:07.943784-07:00 desk-nn /usr/libexec/gdm-wayland-session[1061]: dbus-daemon[1061]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:07.948085-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.361837-07:00 desk-nn gnome-shell[980]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
2024-03-22T08:54:08.361930-07:00 desk-nn gnome-shell[980]: Will monitor session c1
2024-03-22T08:54:08.364824-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.405671-07:00 desk-nn /usr/libexec/gdm-wayland-session[953]: dbus-daemon[953]: [session uid=120 pid=953] Activating service name='org.gnome.Shell.Screencast' requested by ':1.3' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.436025-07:00 desk-nn /usr/libexec/gdm-wayland-session[953]: dbus-daemon[953]: [session uid=120 pid=953] Activating service name='org.freedesktop.impl.portal.PermissionStore' requested by ':1.3' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.489508-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.489861-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.497357-07:00 desk-nn /usr/libexec/gdm-wayland-session[953]: dbus-daemon[953]: [session uid=120 pid=953] Activating service name='org.gnome.Shell.Notifications' requested by ':1.3' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:08.501548-07:00 desk-nn gnome-shell[980]: Extension ding@rastersoft.com already installed in /usr/share/gnome-shell/extensions/ding@rastersoft.com. /usr/share/gnome-shell/extensions/ding@rastersoft.com will not be loaded
2024-03-22T08:54:08.501638-07:00 desk-nn gnome-shell[980]: Extension tiling-assistant@ubuntu.com already installed in /usr/share/gnome-shell/extensions/tiling-assistant@ubuntu.com. /usr/share/gnome-shell/extensions/tiling-assistant@ubuntu.com will not be loaded
2024-03-22T08:54:08.501785-07:00 desk-nn gnome-shell[980]: Extension ubuntu-appindicators@ubuntu.com already installed in /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com. /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com will not be loaded
2024-03-22T08:54:08.501910-07:00 desk-nn gnome-shell[980]: Extension ubuntu-dock@ubuntu.com already installed in /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com. /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com will not be loaded
2024-03-22T08:54:08.558353-07:00 desk-nn gnome-shell[980]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
2024-03-22T08:54:08.664871-07:00 desk-nn gnome-shell[980]: Failed to open sliced image: The resource at “/org/gnome/shell/theme/process-working-dark.svg” does not exist
2024-03-22T08:54:08.714852-07:00 desk-nn gnome-shell[980]: Failed to query file info on '/var/lib/gdm3/.local/share/icc/.goutputstream-NPEPK2': Error when getting information for file “/var/lib/gdm3/.local/share/icc/.goutputstream-NPEPK2”: No such file or directory
2024-03-22T08:54:08.804928-07:00 desk-nn gnome-shell[980]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
2024-03-22T08:54:08.805047-07:00 desk-nn gnome-shell[980]: ibus_bus_call_async: assertion 'ibus_bus_is_connected (bus)' failed
2024-03-22T08:54:08.871625-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:09.070386-07:00 desk-nn dbus-daemon[648]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.38' (uid=120 pid=980 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:09.081210-07:00 desk-nn gnome-shell[980]: Failed to open sliced image: The resource at “/org/gnome/shell/theme/process-working-dark.svg” does not exist
2024-03-22T08:54:09.094197-07:00 desk-nn gnome-shell[980]: Registering session with GDM
2024-03-22T08:54:09.343858-07:00 desk-nn gnome-shell[980]: Gio.IOErrorEnum: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available#012#012Stack trace:#012  asyncCallback@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:114:23#012  @resource:///org/gnome/shell/ui/init.js:21:20#012
2024-03-22T08:54:10.854809-07:00 desk-nn gnome-shell[980]: Gio.IOErrorEnum: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available#012#012Stack trace:#012  asyncCallback@resource:///org/gnome/gjs/modules/core/overrides/Gio.js:114:23#012  @resource:///org/gnome/shell/ui/init.js:21:20#012
2024-03-22T08:54:16.314361-07:00 desk-nn gnome-shell[1727]: Running GNOME Shell (using mutter 45.3) as a Wayland display server
2024-03-22T08:54:16.345697-07:00 desk-nn gnome-shell[1727]: pci id for fd 12: 1234:1111, driver (null)
2024-03-22T08:54:16.345847-07:00 desk-nn gnome-shell[1727]: MESA-LOADER: failed to open bochs-drm: /usr/lib/dri/bochs-drm_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri)
2024-03-22T08:54:16.358372-07:00 desk-nn gnome-shell[1727]: Made thread 'KMS thread' realtime scheduled
2024-03-22T08:54:16.403827-07:00 desk-nn gnome-shell[1727]: Added device '/dev/dri/card0' (bochs-drm) using atomic mode setting.
2024-03-22T08:54:16.404732-07:00 desk-nn gnome-shell[1727]: Failed to initialize accelerated iGPU/dGPU framebuffer sharing: Not hardware accelerated
2024-03-22T08:54:16.404831-07:00 desk-nn gnome-shell[1727]: Created gbm renderer for '/dev/dri/card0'
2024-03-22T08:54:16.404929-07:00 desk-nn gnome-shell[1727]: Boot VGA GPU /dev/dri/card0 selected as primary
2024-03-22T08:54:16.642152-07:00 desk-nn gnome-shell[1727]: Disabling DMA buffer screen sharing (not hardware accelerated)
2024-03-22T08:54:16.652157-07:00 desk-nn gnome-shell[1727]: Using public X11 display :0, (using :1 for managed services)
2024-03-22T08:54:16.652432-07:00 desk-nn gnome-shell[1727]: Using Wayland display name 'wayland-0'
2024-03-22T08:54:16.716654-07:00 desk-nn at-spi-dbus-bus.desktop[1743]: dbus-daemon[1743]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.128142-07:00 desk-nn gnome-shell[1727]: Unset XDG_SESSION_ID, getCurrentSessionProxy() called outside a user session. Asking logind directly.
2024-03-22T08:54:17.128251-07:00 desk-nn gnome-shell[1727]: Will monitor session 2
2024-03-22T08:54:17.161614-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating service name='org.gnome.Shell.Screencast' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.188678-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating service name='org.gnome.Shell.CalendarServer' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.210932-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution-source-registry.service' requested by ':1.38' (uid=1000 pid=1845 comm="/usr/libexec/gnome-shell-calendar-server" label="unconfined")
2024-03-22T08:54:17.292249-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating service name='org.gnome.Shell.Notifications' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.333723-07:00 desk-nn gnome-shell[1727]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
2024-03-22T08:54:17.439254-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.559384-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar8' unit='evolution-calendar-factory.service' requested by ':1.38' (uid=1000 pid=1845 comm="/usr/libexec/gnome-shell-calendar-server" label="unconfined")
2024-03-22T08:54:17.618382-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.669610-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.687139-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.708744-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:17.908098-07:00 desk-nn gnome-shell[1727]: Failed to open sliced image: The resource at “/org/gnome/shell/theme/process-working-dark.svg” does not exist
2024-03-22T08:54:17.965838-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='ca.desrt.dconf' unit='dconf.service' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:18.162491-07:00 desk-nn gnome-shell[1727]: Failed to import DBusMenu, quicklists are not available: Error: Requiring Dbusmenu, version none: Typelib file for namespace 'Dbusmenu' (any version) not found
2024-03-22T08:54:18.162697-07:00 desk-nn gnome-shell[1727]: message repeated 2 times: [ Failed to import DBusMenu, quicklists are not available: Error: Requiring Dbusmenu, version none: Typelib file for namespace 'Dbusmenu' (any version) not found]
2024-03-22T08:54:18.184262-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating service name='org.freedesktop.FileManager1' requested by ':1.33' (uid=1000 pid=1727 comm="/usr/bin/gnome-shell" label="unconfined")
2024-03-22T08:54:18.282727-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
2024-03-22T08:54:18.282787-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
2024-03-22T08:54:18.282839-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
2024-03-22T08:54:18.282865-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
2024-03-22T08:54:18.282890-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
2024-03-22T08:54:18.282921-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
2024-03-22T08:54:18.282946-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
2024-03-22T08:54:18.282971-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
2024-03-22T08:54:18.282995-07:00 desk-nn gnome-shell[1727]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
2024-03-22T08:54:18.413148-07:00 desk-nn gnome-shell[1727]: JS ERROR: TypeError: this._prepareStartupAnimation() is undefined#012_loadBackground/signalId</id<@resource:///org/gnome/shell/ui/layout.js:693:26#012@resource:///org/gnome/shell/ui/init.js:21:20
2024-03-22T08:54:18.604828-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Cannot allocate memory
2024-03-22T08:54:18.604941-07:00 desk-nn gnome-shell[1727]: Failed to post KMS update: drmModeAtomicCommit: Cannot allocate memory
2024-03-22T08:54:18.819894-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Cannot allocate memory
2024-03-22T08:54:18.824924-07:00 desk-nn gnome-shell[1727]: GNOME Shell started at Fri Mar 22 2024 08:54:17 GMT-0700 (Pacific Daylight Time)
2024-03-22T08:54:18.825012-07:00 desk-nn gnome-shell[1727]: Registering session with GDM
2024-03-22T08:54:18.827488-07:00 desk-nn gnome-shell[980]: Connection to xwayland lost
2024-03-22T08:54:18.829327-07:00 desk-nn gnome-shell[980]: Xwayland terminated, exiting since it was mandatory
2024-03-22T08:54:18.829409-07:00 desk-nn gnome-shell[980]: JS ERROR: Gio.IOErrorEnum: Xwayland exited unexpectedly#012@resource:///org/gnome/shell/ui/init.js:21:20
2024-03-22T08:54:18.829463-07:00 desk-nn gnome-shell[980]: Execution of main.js threw exception: Module resource:///org/gnome/shell/ui/init.js threw an exception
2024-03-22T08:54:18.860694-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Cannot allocate memory
2024-03-22T08:54:18.868033-07:00 desk-nn gnome-shell[1727]: Launching DING process
2024-03-22T08:54:18.923246-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:18.990991-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:19.010407-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:19.122942-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:19.248063-07:00 desk-nn dbus-daemon[1523]: [session uid=1000 pid=1523] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.88' (uid=1000 pid=2309 comm="gjs /usr/share/gnome-shell/extensions/ding@rasters" label="unconfined")
2024-03-22T08:54:19.268873-07:00 desk-nn gnome-shell[1727]: DING: Detected async api for thumbnails
2024-03-22T08:54:19.454582-07:00 desk-nn gnome-shell[1727]: DING: DBus interface for Switcheroo control (net.hadess.SwitcherooControl) is now available.
2024-03-22T08:54:19.456183-07:00 desk-nn gnome-shell[1727]: DING: DBus interface for Gvfs daemon (org.gtk.vfs.Metadata) is now available.
2024-03-22T08:54:19.491610-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:19.491786-07:00 desk-nn gnome-shell[1727]: DING: ** Message: 08:54:19.467: Connecting to org.freedesktop.Tracker3.Miner.Files
2024-03-22T08:54:19.507407-07:00 desk-nn gnome-shell[1727]: Received notification for window. 0 notifications remaining.
2024-03-22T08:54:19.524740-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
2024-03-22T08:54:19.567197-07:00 desk-nn gnome-shell[1727]: message repeated 2 times: [ Page flip failed: drmModeAtomicCommit: Invalid argument]
2024-03-22T08:54:19.638624-07:00 desk-nn gnome-shell[1727]: DING: DBus interface for Nautilus (org.gnome.Nautilus.FileOperations2) is now available.
2024-03-22T08:54:19.640458-07:00 desk-nn gnome-shell[1727]: DING: DBus interface for Nautilus (org.freedesktop.FileManager1) is now available.
2024-03-22T08:54:19.713345-07:00 desk-nn gnome-shell[1727]: DING: GNOME nautilus 46.beta
2024-03-22T08:54:37.877413-07:00 desk-nn gnome-shell[1727]: Page flip failed: drmModeAtomicCommit: Invalid argument
```

---

### Post by Doug S on 2024-03-22
after a brand new re-install with the same result, I submitted [a bug report]("https://bugs.launchpad.net/ubuntu/+bug/2058785") and entered a FAIL in the testing tracker for todays ISO.

---

### Post by galatians2 on 2024-03-22
I installed using the latest daily 24.04 ISO about 2 weeks ago. After updating packages today Gnome no longer starts on boot. I'm left on the boot job startup list and the last entry is "ucsi_acpi USBC000:00: ucsi_handle_connector_change: ACK failed (-110)

---

### Post by MAFoElffen on 2024-03-22
Let me upgrade one of my Gnome based VMs to check... BRB.
```

mafoelffen@noble00:~$ apt list --upgradable
Listing... Done
adwaita-icon-theme/noble,noble 46~rc-1 all [upgradable from: 41.0-1ubuntu1]
cloud-init/noble,noble 24.1.2-0ubuntu1 all [upgradable from: 24.1.1-0ubuntu1]
coreutils/noble 9.4-2ubuntu4 amd64 [upgradable from: 9.4-2ubuntu2]
debianutils/noble 5.17 amd64 [upgradable from: 5.16]
duplicity/noble 2.1.4-3ubuntu1 amd64 [upgradable from: 2.1.4-2ubuntu1]
efibootmgr/noble 18-1build1 amd64 [upgradable from: 18-1]
fonts-ubuntu/noble,noble 0.869+git20240321-0ubuntu1 all [upgradable from: 0.869-0ubuntu1]
gnome-remote-desktop/noble 45.1-1build1 amd64 [upgradable from: 45.1-1]
gnome-shell-extension-ubuntu-dock/noble,noble 89ubuntu3 all [upgradable from: 89ubuntu2]
gnome-user-docs/noble,noble 46.0-1ubuntu1 all [upgradable from: 45.1-2ubuntu2]
grub-common/noble 2.12-1ubuntu4 amd64 [upgradable from: 2.12~rc1-12ubuntu4]
grub2-common/noble 2.12-1ubuntu4 amd64 [upgradable from: 2.12~rc1-12ubuntu4]
language-pack-en/noble,noble 1:24.04+20240316 all [upgradable from: 1:24.04+20240309]
libtss2-esys-3.0.2-0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-sys1/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-cmd0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-device0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-libtpms0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-mssim0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-spi-helper0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
libtss2-tcti-swtpm0/noble 4.0.1-7ubuntu1 amd64 [upgradable from: 4.0.1-3ubuntu1]
linux-firmware/noble 20240318.git3b128b60-0ubuntu1 amd64 [upgradable from: 20240202.git36777504-0ubuntu1]
orca/noble,noble 46.0-1ubuntu1 all [upgradable from: 46~beta-1ubuntu1]
python3-markupsafe/noble 2.1.5-1build1 amd64 [upgradable from: 2.1.5-1]
thunderbird-gnome-support/noble 1:115.8.0+build1-0ubuntu1 amd64 [upgradable from: 1:115.6.1+build1-0ubuntu1]
thunderbird-locale-en-gb/noble,noble 1:115.8.1+build1+snap2 all [upgradable from: 1:115.6.1+build1-0ubuntu1]
thunderbird-locale-en-us/noble,noble 1:115.8.1+build1+snap2 all [upgradable from: 1:115.6.1+build1-0ubuntu1]
thunderbird-locale-en/noble,noble 1:115.8.1+build1+snap2 amd64 [upgradable from: 1:115.6.1+build1-0ubuntu1]
thunderbird-locale-zh-hant/noble,noble 1:115.8.1+build1+snap2 amd64 [upgradable from: 1:115.6.1+build1-0ubuntu1]
thunderbird/noble 1:115.8.1+build1+snap2 amd64 [upgradable from: 1:115.6.1+build1-0ubuntu1]
ubuntu-desktop-minimal/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-desktop/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-minimal/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-standard/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-wallpapers-mantic/noble,noble 24.04.2 all [upgradable from: 23.10.4]
ubuntu-wallpapers/noble,noble 24.04.2 all [upgradable from: 23.10.4]
x11-utils/noble 7.7+6 amd64 [upgradable from: 7.7+5build2]

```
After the upgrade, on reboot, it would not shutdown all the way on it's own. Forced a power off...

X tries to start... Cursor is an "X", never comes up to the desktop...

---

### Post by MAFoElffen on 2024-03-22
Ubuntu Noble's default is Wayland.

Toggled over to tty4.
```

sudo killall gdm3

```
Bounced back to the Graphical login... 

Entered User... On password screen, selected the gear icon and selected "Ubuntu on Xorg". Entered password...

Success. Went to Desktop.

Xorg is working. Wayland is broken.

---

### Post by MAFoElffen on 2024-03-22
Later... I got a crash report notification asking me if I wanted to report it. On "show me more", it said it was from gnome-session, and then said it was on packages that said it was installed from the last update, then said I was running old-outdated versions of those packages.

These same packages that are being held back as phased update:
```

The following packages have been kept back:
  adwaita-icon-theme duplicity efibootmgr gnome-remote-desktop grub-common
  grub2-common liblouisutdml-bin libtss2-esys-3.0.2-0 libtss2-sys1
  libtss2-tcti-cmd0 libtss2-tcti-device0 libtss2-tcti-libtpms0
  libtss2-tcti-mssim0 libtss2-tcti-spi-helper0 libtss2-tcti-swtpm0 thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb
  thunderbird-locale-en-us thunderbird-locale-zh-hant wireless-tools x11-utils
The following packages will be upgraded:
  coreutils
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

```
The libxxx packages there are not related to this. those are for Braille transcription, and TPM 2.0 services.

I'm thinking it was one of these updates that did apply:
```

gnome-shell-extension-ubuntu-dock/noble,noble 89ubuntu3 all [upgradable from: 89ubuntu2]
ubuntu-desktop-minimal/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-desktop/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-minimal/noble 1.536build1 amd64 [upgradable from: 1.536]
ubuntu-standard/noble 1.536build1 amd64 [upgradable from: 1.536]

```

---

### Post by Doug S on 2024-03-23
It turns out that my "graphics no longer working" title might be incorrect. It seems my VNC desktop screen is merely frozen, dark but frozen. Because I see a cursor, also frozen, in the screen. 

Anyway, via SSH, I applied todays updates and now re-boot via "sudo shutdown -r now" has the VNC session hung with a spinning wheel type thingy.

Grrr... Being a server person, I don't even use desktop other than to compile and publish the desktop help portion of help.ubuntu.com.

EDIT: The VM did eventually re-boot, after I do not know how many minutes.

EDIT 2: I am also seeing this:

```
N: Ignoring file 'ubuntu.sources.curtin.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

---

### Post by corradoventu on 2024-03-23
I also see the message about 'ubuntu.sources.curtin.old' with every apt update, I would like to open a bug but against which package?

[https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058811](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058811)

---

### Post by galatians2 on 2024-03-23
Ok my problem was self inflicted. I had installed packages `fuse` & `libfuse2` which force uninstalled `fuse3` and a bunch of other packages needed by the system. Once I reverted that everything worked again.

---

### Post by Doug S on 2024-03-23
I have started again, with a new install from the iso of 2024.03.23. Same issue. Launchpad is currently broken. Here is my pending latest bug report entry:

[INDENT]After a fresh install (from the 2024.03.23 ISO in this case) everything is fine if I don't change the screen resolution from the default of 1024X768. Issues start once I change the display to 1680X1050, but seems to recover after an idle time screen blank/lock cycle. It seems I get into trouble because I normally operate with "Blank Screen Delay" set to never.

Workaround: Set "Blank Screen Delay" to 1 minute and screen lock off; After re-boot wait for the 1 minute with a messed up screen; Move the mouse or type a key, then the screen is fine.[/INDENT]

---

### Post by perockwell on 2024-03-23
Yesterday's update also broke my VM. I'm running a Noble arm64 VM under VMware Fusion 13.5 on an Apple Silicon Mac. When using the vmwgfx (VMware SVGA 3d) driver and enabling 3D support for the VM, the entire GNOME/Wayland graphical environment becomes unusable. The display doesn't refresh properly. As I move the mouse pointer, blocks of the display automatically refresh. This sounds like the "messed up screen" that Doug S. is seeing.

I didn't have to resort to going back to X11. Staying with Wayland and disabling 3D support allows the VM to work properly.

This is a major regression from Mantic, which works fine with the same VM configuraiton. I can't tell if this is GNOME 46 or Mesa related, but to me this is a showstopper for Noble.

---

### Post by perockwell on 2024-03-23
I just started fresh and reinstalled my VM from today's daily arm64 Desktop ISO. Things are working for me again as well. 
Keeping fingers crossed.

---

### Post by MAFoElffen on 2024-03-23
I updated the same VM that Wayland was broken yesterday. Libc6 packages where updated today (so the Glibc libraries...)

Wayland works and the Ubuntu Desktop came up for me in Wayland. Must have been a chicken-before-the-egg progression order of phased updates problem. LOL.

All good here. (Now.)

---

### Post by Doug S on 2024-03-24
Thanks to all that chimed in on this thread. If I understand correctly, while others had issues that may or may not have been the same, most are now resolved. Interesting. My issue remains and is annoying, but at least I have a work around, and actually I only really need SSH access to the VM to be able to do what is needed for help.ubuntu.com update publications.

---

### Post by hwertz10 on 2024-03-25
Amusingly I had to do the opposite on my VirtualBox VM.  With vmsvga driver and 3D acceleration off, everything works fine in Ubuntu 22.04, upon upgrade to 24.04 it seems that Wayland sessions fire up but Xorg ones crash back to login prompt (and, if you only have an Xorg login manager like lightdm, with no gdm3 for Wayland usage, I assume you'd get no graphical login either.)   But if turn 3D acceleration on in VirtualBox display settings, no problem, 24.04 goes right to the desktop environment I'd selected.

I assume this is some problem with vmsvga driver in particular, after it worked on that VM, I had a couple old Core 2 Duos I threw Ubuntu 22.04 onto and I had them upgrade to 24.04, it works fine on them.

I decided to throw Steam on one.  Why not?  It does have a 250GB HDD for some games; no I did not find some old games and attempt to run them; the Gallium drivers are amazing and something as old as a Sandy Bridge played even some low-requirement DX11 games at a playable framerate; but, the GPU in this is even older, slower, and less featureful than that for 3D, I used GPUs like this "back in the day", even for some retrogaming type purpose the 3D performance of them was not considered good even 15-20 years ago when they were new.  But the 2D and video scaling on these GPUs is perfectly serviceable.  I ran remote steam play off my desktop, it said it was getting 58FPS and sub 10ms pings.  The laptop was like a $2000 system when it was new, so it has a very nice 1080 screen, nice keyboard, very nice speakers, nice chassis (other than being heavy).  The power use is brutal though, it has a hardware MPEG-2 decoder but really, who uses MPEG-2?  The dual core CPU is a tad faster than a Celeron N and is just fast enough to decode 1080 H.264/H.265 video but it's sucking down like 30-50W doing it.  Under light load the battery will last like 3+ hours, but it gets about like 30-40 minutes tops browsing playing videos, etc.  It's so big and thick the fan blows hot air off some direction and the chassis and keyboard do not even warm up, so just run it plugged in.  I'm donating it to a friend of mine, who has a nice gaming laptop they've cracked the screen on.

---

### Post by stephen-c1udulq on 2024-04-21
Same thing here - moved from a Nvidia to new 7000 series AMD card recently and was interested to try Wayland. Have been running 22.04 but Wayland wasn't working for me on that. So I upgraded to 24.04 today and see that Wayland crashes back to gdm with some cryptic messages like  "Connection to xwayland lost" and nothing else in the logs looking like an error.

Is there a way to get a log from the core wayland process to see what is going on?

---

### Post by Doug S on 2024-04-22
My issue was fixed with some recent updates. I set the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/2058785") to "Fix Released".

---

