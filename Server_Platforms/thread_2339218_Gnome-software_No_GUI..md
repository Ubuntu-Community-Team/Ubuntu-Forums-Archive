---
title: "Gnome-software: No GUI."
date: 2016-10-05
forum: Server Platforms
---

### Post by TheMiz on 2016-10-05
gnome-software starts and shows up in the task manager, but there is no GUI.  

Have you found a solution?

---

### Post by Bucky Ball on 2016-10-06
Try Synaptic Package Manager. 

```
sudo apt install synaptic
```

There are issues with the *-software apps. I use none of them so know little about it but f you do a bit of research you will find out more about that. They will be fixed eventually I guess but for the moment Synaptic works fine.

---

### Post by TheMiz on 2016-10-06
Bucky,
Thank you for moving this thread for me. I have synaptic working on my system without trouble. What bothers me is that I have a nearly identical system that will open the gnome-software GUI without trouble. But on this system gnome-software runs, but never displays a GUI.


here is my system information:
```

Operating system    Ubuntu Linux 16.04
Kernel and CPU    Linux 4.4.0-38-generic on x86_64
Processor information    Intel(R) Celeron(R) CPU  N2930  @ 1.83GHz, 4 cores

```


I installed ubuntu server edition on this system and then installed LXDE. It is a headless server that I only access via SSH or VNC. I'm not very smart so I like to use the Desktop environment, plus using a terminal on a VNC desktop allows me to save my workflow if my connection is interrupted. My other system is set up the same way with ubuntu server edition installed, LXDE, headless with VNC/SSH to administer.


the output from running gnome-software with the verbose flag is super long, and I don't know how to interpret it. Here it is:
```
~$ gnome-software --verbose
(gnome-software:11083): Gs-DEBUG: compatible-project: GNOME
(gnome-software:11083): Gs-DEBUG: compatible-project: KDE
(gnome-software:11083): Gs-DEBUG: compatible-project: XFCE
(gnome-software:11083): As-DEBUG: run GsPlugin::setup
(gnome-software:11083): Gs-DEBUG: searching for plugins in /usr/lib/gs-plugins-9
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_menu-spec-categories.so: menu-spec-categories
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_apt.so: apt
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_epiphany.so: epiphany
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_dummy.so: dummy
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_hardcoded-blacklist.so: hardcoded-blacklist
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_hardcoded-featured.so: hardcoded-featured
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_appstream.so: appstream
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_icons.so: icons
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_dpkg.so: dpkg
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_provenance.so: provenance
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_moduleset.so: moduleset
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_menu-spec-refine.so: menu-spec-refine
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_ubuntu-reviews.so: ubuntu-reviews
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_fwupd.so: fwupd
(gnome-software:11083): Gs-DEBUG: opened plugin /usr/lib/gs-plugins-9/libgs_plugin_snappy.so: snappy
(gnome-software:11083): Gs-DEBUG: apt [0.0] to be ordered after appstream [0.0] so promoting to [1.0]
(gnome-software:11083): Gs-DEBUG: epiphany [0.0] to be ordered after appstream [0.0] so promoting to [1.0]
(gnome-software:11083): Gs-DEBUG: hardcoded-blacklist [0.0] to be ordered after appstream [0.0] so promoting to [1.0]
(gnome-software:11083): Gs-DEBUG: appstream [0.0] to be ordered after menu-spec-categories [0.0] so promoting to [1.0]
(gnome-software:11083): Gs-DEBUG: apt [1.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: epiphany [1.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: hardcoded-blacklist [1.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: icons [0.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: icons [2.0] to be ordered after epiphany [2.0] so promoting to [3.0]
(gnome-software:11083): Gs-DEBUG: provenance [0.0] to be ordered after apt [2.0] so promoting to [3.0]
(gnome-software:11083): Gs-DEBUG: cannot find plugin 'packagekit-refine'
(gnome-software:11083): Gs-DEBUG: moduleset [0.0] to be ordered after menu-spec-categories [0.0] so promoting to [1.0]
(gnome-software:11083): Gs-DEBUG: cannot find plugin 'packagekit-refine'
(gnome-software:11083): Gs-DEBUG: moduleset [1.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: cannot find plugin 'packagekit-refine'
(gnome-software:11083): Gs-DEBUG: menu-spec-refine [0.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: cannot find plugin 'packagekit-refine'
(gnome-software:11083): Gs-DEBUG: ubuntu-reviews [0.0] to be ordered after appstream [1.0] so promoting to [2.0]
(gnome-software:11083): Gs-DEBUG: cannot find plugin 'packagekit-refine'
(gnome-software:11083): As-DEBUG: run GsPlugin::dummy(gs_plugin_initialize)
(gnome-software:11083): GsPlugin-DEBUG: disabling 'dummy' as not in self test
(gnome-software:11083): As-DEBUG: run GsPlugin::dpkg(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::fwupd(gs_plugin_initialize)
(gnome-software:11083): GsPlugin-DEBUG: fwupd configuration not found, disabling plugin.
(gnome-software:11083): As-DEBUG: run GsPlugin::snappy(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::appstream(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::apt(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::epiphany(gs_plugin_initialize)
(gnome-software:11083): GsPlugin-DEBUG: disabling 'epiphany' as epiphany does not exist
(gnome-software:11083): As-DEBUG: run GsPlugin::moduleset(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::ubuntu-reviews(gs_plugin_initialize)
(gnome-software:11083): As-DEBUG: run GsPlugin::provenance(gs_plugin_initialize)
(gnome-software:11083): Gs-DEBUG: loading install queue from ~/.local/share/gnome-software/install-queue
(gnome-software:11083): Gs-DEBUG: adding pending app virtualbox.desktop
(gnome-software:11083): As-DEBUG: run GsPlugin::snappy(gs_plugin_refine)
(gnome-software:11083): As-DEBUG: run GsPlugin::appstream(gs_plugin_refine)
(gnome-software:11083): As-DEBUG: run appstream::startup
(gnome-software:11083): As-DEBUG: run AsStore:load
(gnome-software:11083): As-DEBUG: run AsStore:load{per-user}
(gnome-software:11083): As-DEBUG: run AsStore:load{per-system}
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/usr/share/appdata}

```
continued...

```

(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/gucharmap.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-pdfdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/org.gnome.DiskUtility.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-tiffdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-dvidocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/gnome-power-statistics.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-comicsdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/org.gnome.Screenshot.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-djvudocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/galculator.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-psdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-xpsdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/usr/share/applications}
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/mimeinfo.cache
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/nm-applet.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/signon-ui.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/users.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-info-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/vim.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gucharmap.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-screenlock.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/xscreensaver-properties.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/defaults.list
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-screen-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/galculator.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-logout.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-user-share-webdav.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/synaptic.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-datetime-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-userpasswd.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-display-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-mplayer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/update-accounts.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gcr-prompter.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gpicview.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/python3.5.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-universal-access-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxsession-edit.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-disk-image-mounter.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-keyboard-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-wacom-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-network-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/pcmanfm.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-credentials-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/nm-connection-editor.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/firefox.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/leafpad.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/notification-daemon.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-software-local-file.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-region-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-disk-image-writer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-user-share-properties.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-color-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-control-center.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-mouse-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxmusic.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evolution-data-server-uoa.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/im-config.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/python2.7.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evince-previewer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/pcmanfm-desktop-pref.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/xarchiver.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxrandr.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/alsamixergui.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-user-accounts-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-userinfo.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/yelp.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxappearance.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-sound-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gksu.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/time.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/system-config-printer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/bluetooth-sendto.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/openjdk-8-policytool.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxtask.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-usermount.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/deluge.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-x-www-browser.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/credentials-preferences.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/openjdk-8-java.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/obconf.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gkbd-keyboard-display.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/screensavers
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/ibus-setup.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxterminal.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-appearance-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evince.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/byobu.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gcr-viewer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/network.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-power-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/shares.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.Software.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-bluetooth-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-x-terminal-emulator.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxinput.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/mimeinfo.cache: /usr/share/applications/mimeinfo.cache has an unrecognised extension
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/nm-applet.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/signon-ui.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-info-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: gucharmap.desktop
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-screenlock.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/defaults.list: /usr/share/applications/defaults.list has an unrecognised extension
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-screen-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: galculator.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-logout.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-user-share-webdav.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-datetime-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-display-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/update-accounts.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gcr-prompter.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/python3.5.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-universal-access-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-disk-image-mounter.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-keyboard-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-wacom-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-network-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-credentials-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/notification-daemon.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-software-local-file.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-region-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-disk-image-writer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-color-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-mouse-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/evolution-data-server-uoa.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/python2.7.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/evince-previewer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-user-accounts-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-sound-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gksu.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/system-config-printer.desktop: Has category X-GNOME-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/bluetooth-sendto.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-x-www-browser.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/openjdk-8-java.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gkbd-keyboard-display.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-appearance-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: evince.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gcr-viewer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-power-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/shares.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-bluetooth-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-x-terminal-emulator.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/var/lib/menu-xdg/applications}
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/menu-xdg/applications/menu-xdg
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/usr/share/appdata}
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/gucharmap.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-pdfdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/org.gnome.DiskUtility.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-tiffdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-dvidocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/gnome-power-statistics.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-comicsdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/org.gnome.Screenshot.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-djvudocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/galculator.appdata.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-psdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/appdata/evince-xpsdocument.metainfo.xml
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: gucharmap.desktop
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-pdfocument
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: evince.desktop
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-tiffdocument
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-dvidocument
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-comicsdocument
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-djvudocument
(gnome-software:11083): As-DEBUG: merging duplicate appdata:appdata entries: galculator.desktop
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-psdocument
(gnome-software:11083): As-DEBUG: merging duplicate metainfo:metainfo entries: evince-xpsdocument
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/usr/share/applications}
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/mimeinfo.cache
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/nm-applet.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/signon-ui.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/users.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-info-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/vim.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gucharmap.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-screenlock.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/xscreensaver-properties.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/defaults.list
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-screen-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/galculator.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-logout.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-user-share-webdav.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/synaptic.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-datetime-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-userpasswd.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-display-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-mplayer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/update-accounts.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gcr-prompter.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gpicview.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/python3.5.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-universal-access-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxsession-edit.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-disk-image-mounter.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-keyboard-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-wacom-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-network-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/pcmanfm.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-credentials-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/nm-connection-editor.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/firefox.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/leafpad.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/notification-daemon.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-software-local-file.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-region-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-disk-image-writer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gnome-user-share-properties.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-color-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-control-center.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-mouse-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxmusic.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evolution-data-server-uoa.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/im-config.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/python2.7.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evince-previewer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/pcmanfm-desktop-pref.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/xarchiver.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxrandr.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/alsamixergui.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-user-accounts-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-userinfo.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/yelp.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxappearance.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-sound-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gksu.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/time.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/system-config-printer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/bluetooth-sendto.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/openjdk-8-policytool.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxtask.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/redhat-usermount.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/deluge.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-x-www-browser.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/credentials-preferences.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/openjdk-8-java.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/obconf.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gkbd-keyboard-display.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/screensavers
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/ibus-setup.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxterminal.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-appearance-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/evince.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/byobu.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/gcr-viewer.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/network.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-power-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/shares.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/org.gnome.Software.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/unity-bluetooth-panel.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxde-x-terminal-emulator.desktop
(gnome-software:11083): As-DEBUG: adding existing file: /usr/share/applications/lxinput.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/mimeinfo.cache: /usr/share/applications/mimeinfo.cache has an unrecognised extension
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/nm-applet.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/signon-ui.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/users.desktop as users.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-info-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/vim.desktop as vim.desktop already exists
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: gucharmap.desktop
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-screenlock.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/xscreensaver-properties.desktop as xscreensaver-properties.desktop already exists
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/defaults.list: /usr/share/applications/defaults.list has an unrecognised extension
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-screen-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: galculator.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-logout.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-user-share-webdav.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/synaptic.desktop as synaptic.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-datetime-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/redhat-userpasswd.desktop as redhat-userpasswd.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-display-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/gnome-mplayer.desktop as gnome-mplayer.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/update-accounts.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gcr-prompter.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/gpicview.desktop as gpicview.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/python3.5.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-universal-access-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxsession-edit.desktop as lxsession-edit.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-disk-image-mounter.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-keyboard-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-wacom-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-network-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/pcmanfm.desktop as pcmanfm.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-credentials-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/nm-connection-editor.desktop as nm-connection-editor.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/firefox.desktop as firefox.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/leafpad.desktop as leafpad.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/notification-daemon.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-software-local-file.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-region-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gnome-disk-image-writer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/gnome-user-share-properties.desktop as gnome-user-share-properties.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-color-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/unity-control-center.desktop as unity-control-center.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-mouse-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxmusic.desktop as lxmusic.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/evolution-data-server-uoa.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/im-config.desktop as im-config.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/python2.7.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/evince-previewer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/pcmanfm-desktop-pref.desktop as pcmanfm-desktop-pref.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/xarchiver.desktop as xarchiver.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxrandr.desktop as lxrandr.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/alsamixergui.desktop as alsamixergui.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-user-accounts-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/redhat-userinfo.desktop as redhat-userinfo.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/yelp.desktop as yelp.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxappearance.desktop as lxappearance.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-sound-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gksu.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/time.desktop as time.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/system-config-printer.desktop: Has category X-GNOME-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/bluetooth-sendto.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/openjdk-8-policytool.desktop as openjdk-8-policytool.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxtask.desktop as lxtask.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/redhat-usermount.desktop as redhat-usermount.desktop already exists

```

```
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/deluge.desktop as deluge.desktop already exists
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-x-www-browser.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/credentials-preferences.desktop as credentials-preferences.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/openjdk-8-java.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/obconf.desktop as obconf.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gkbd-keyboard-display.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/ibus-setup.desktop as ibus-setup.desktop already exists
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxterminal.desktop as lxterminal.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-appearance-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: merging duplicate desktop:appdata entries: evince.desktop
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/byobu.desktop as byobu.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/gcr-viewer.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/network.desktop as network.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-power-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/shares.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/org.gnome.Software.desktop as org.gnome.Software.desktop already exists
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/unity-bluetooth-panel.desktop: Has category X-Unity-Settings-Panel
(gnome-software:11083): As-DEBUG: Ignoring /usr/share/applications/lxde-x-terminal-emulator.desktop: NoDisplay=true
(gnome-software:11083): As-DEBUG: not parsing /usr/share/applications/lxinput.desktop as lxinput.desktop already exists
(gnome-software:11083): As-DEBUG: run AsStore:load-installed{/var/lib/menu-xdg/applications}
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/menu-xdg/applications/menu-xdg
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: removing desktop entry: org.gnome.Software.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: vim.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: firefox.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: nm-connection-editor.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_restricted_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_universe_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: removing desktop entry: xarchiver.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxmusic.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: obconf.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxsession-edit.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxtask.desktop
(gnome-software:11083): As-DEBUG: removing appdata entry: galculator.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: xscreensaver-properties.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: gnome-mplayer.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: leafpad.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxrandr.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: deluge.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: pcmanfm-desktop-pref.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: pcmanfm.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: redhat-userpasswd.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: redhat-usermount.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: redhat-userinfo.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxterminal.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: users.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: time.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: network.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: plan.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxappearance.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: lxinput.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: synaptic.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: flcheckers.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: flblocks.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: flsudoku.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_universe_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: chromium-browser.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: firefox.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-math.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-draw.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-base.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: eog.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: display-im6.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-writer.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.FileRoller.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-calc.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-startcenter.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: display-im6.q16.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-impress.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: thunderbird.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: CMake.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.taquin.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: virt-manager.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: chromium-browser.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gufw.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: lshw-gtk.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: owncloud.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Maps.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: mscore.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: abiword.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: ubuntu-mate-welcome.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: ubuntu-mate-software.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: light-locker-settings.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: htop.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: ubiquity-kdeui.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: boinc-manager.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: mplayer.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: evolution.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Contacts.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: evolution-bogofilter
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: evolution-spamassassin
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Documents.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Books.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: ccsm.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: removing appdata entry: gucharmap.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gnome-system-monitor.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gnome-system-monitor-kde.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: vino-preferences.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.font-viewer.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: vim.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Nautilus.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: xdiagnose.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: ubiquity.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: upstart-monitor.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: eog.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-keyboard-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-appearance-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-datetime-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-universal-access-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-bluetooth-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-network-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-sound-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-region-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-wacom-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-mouse-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-user-accounts-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: unity-color-panel.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-base.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.FileRoller.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: thunderbird.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: ibus-setup.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Calendar.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: im-config.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gnome-sudoku.desktop
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-tiffdocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-xpsdocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-dvidocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-pdfocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-djvudocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-psdocument
(gnome-software:11083): As-DEBUG: removing metainfo entry: evince-comicsdocument
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: nm-connection-editor.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gvim.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: gnome-user-share-properties.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-impress.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: org.gnome.Software.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: credentials-preferences.desktop
(gnome-software:11083): As-DEBUG: removing appdata entry: gnome-power-statistics.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: display-im6.q16.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: gnome-session-properties.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: firefox.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-calc.desktop
(gnome-software:11083): As-DEBUG: removing appdata entry: evince.desktop
(gnome-software:11083): As-DEBUG: removing appdata entry: org.gnome.Screenshot.desktop
(gnome-software:11083): As-DEBUG: removing appdata entry: org.gnome.DiskUtility.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-startcenter.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-math.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-draw.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: display-im6.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: libreoffice-writer.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: software-properties-gnome.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: software-properties-drivers.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: software-properties-gtk.desktop
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: language-selector.desktop
(gnome-software:11083): As-DEBUG: removing desktop entry: yelp.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_multiverse_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: merging duplicate appstream:appstream entries: virtualbox.desktop
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: run AsStore:app-info{/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz}
(gnome-software:11083): As-DEBUG: run AsStore:store-from-file
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_restricted_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_restricted_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_universe_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_universe_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_main_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial_multiverse_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_xenial-security_multiverse_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: adding existing file: /var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz
(gnome-software:11083): As-DEBUG: removing openjdk-8-policytool.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing thunar-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce4-settings-editor.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce-ui-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce4-mime-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce-display-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce-keyboard-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: removing xfce4-accessibility-settings.desktop as vetoed
(gnome-software:11083): As-DEBUG: run AsStore:match-addons
(gnome-software:11083): As-DEBUG: Emitting ::changed() [store-load]
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-multiverse provides 49 apps (3%)
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-updates-main provides 44 apps (2%)
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-main provides 60 apps (3%)
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-updates-multiverse provides 1 apps (0%)
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-universe provides 1649 apps (91%)
(gnome-software:11083): GsPlugin-DEBUG: origin ubuntu-xenial-updates-universe provides 2 apps (0%)
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to software-properties-gtk.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to software-properties-gnome.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to software-properties-drivers.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to display-im6.q16.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to display-im6.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-writer.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to ubiquity.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-calc.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to language-selector.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to vino-preferences.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to gnome-system-monitor.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to gnome-system-monitor-kde.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to org.gnome.Software.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-draw.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-math.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to upstart-monitor.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to thunderbird.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-keyboard-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-region-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-network-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-sound-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-datetime-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-universal-access-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-mouse-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-wacom-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-user-accounts-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-appearance-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-bluetooth-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to unity-color-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to gnome-sudoku.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to vim.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to org.gnome.font-viewer.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-startcenter.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to firefox.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to gvim.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to org.gnome.FileRoller.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-base.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to nm-connection-editor.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to org.gnome.Nautilus.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to eog.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to xdiagnose.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to org.gnome.Calendar.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to gnome-session-properties.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-main' to libreoffice-impress.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-multiverse' to virtualbox.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-universe' to scribus.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-updates-universe' to flightgear.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gucharmap.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-system-log.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to orca.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to usb-creator-gtk.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to fcitx-configtool.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to fcitx.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to deja-dup.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gprompter.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to xchat-gnome.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to system-config-printer.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to file-roller.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-mines.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gparted.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.baobab.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to ibus-setup.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to sol.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to transmission-gtk.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to system-config-kickstart.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to im-config.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to remmina.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-tiffdocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-xpsdocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-dvidocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-pdfocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-djvudocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-psdocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince-comicsdocument
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to webbrowser-app.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to debian-uxterm.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to debian-xterm.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-user-share-properties.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.Devhelp.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-terminal.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to simple-scan.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-mahjongg.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to seahorse.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to unity-credentials-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to credentials-preferences.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to inkscape.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.gedit.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-power-statistics.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to onboard-settings.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to onboard.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.Totem.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to fcitx-qimpanel-configtool.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to evince.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.Screenshot.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.DiskUtility.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to rhythmbox.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to update-manager.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to transmission-qt.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to shotwell.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to nvidia-settings.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to org.gnome.Cheese.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to emacs24.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to emacs24-term.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to yelp.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to gnome-calculator.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to unity-activity-log-manager-panel.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-main' to activity-log-manager.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to nvpy.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to jajuk.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to sandboxgamemaker.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to sauerbraten.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to openlugaru.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to hannah-foo2zjs.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to openmw.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to wolf4sdl.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to qcomicbook.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to pq.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to sabnzbdplus.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to mess.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to exult.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to seaview.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to openmw-cs.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to idjc.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake-armagon.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake-dissolution.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to assaultcube.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to rott.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to dropbox.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to cytadela.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to gnome-video-arcade.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to caja-dropbox.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to mythtv.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to zekr.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to fbzx.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to vcmilauncher.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to vcmiclient.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to residualvm.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to series60-remote.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to gfaim.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to mythtv-setup.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to redeclipse.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to mame.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to hijra-applet.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to arb.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to matlab.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to frogatto.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake3.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake3-team-arena.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to opentyrian.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to zangband.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake2-reckoning.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake2-groundzero.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to quake2.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to devede_ng.desktop
(gnome-software:11083): GsPlugin-DEBUG: Adding keyword 'ubuntu-xenial-multiverse' to GENtle.desktop
(gnome-software:11083): As-DEBUG: run appstream::refine
(gnome-software:11083): As-DEBUG: run GsPlugin::apt(gs_plugin_refine)
```

---

### Post by Bucky Ball on 2016-10-06
*Thread moved to **Server Platforms**.*

And again, sorry. Now you've provided more details it is a very different ball game. As you are actually running two servers you've got a better chance of support here. Good luck.

(Your issue is very different to that first thread me thinks ... ;))

---

