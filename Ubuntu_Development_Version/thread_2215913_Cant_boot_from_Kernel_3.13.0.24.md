---
title: "Cant boot from Kernel 3.13.0.24"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2014-04-09
After installing 14.04 Beta 2 when I running the update I saw these 

```
Installing new version of config file /etc/xdg/autostart/indicator-sound.desktop ...
Setting up unity-control-center (14.04.3+14.04.20140407-0ubuntu1) ...
Setting up glib-networking-common (2.40.0-1) ...
Setting up glib-networking-services (2.40.0-1) ...
Setting up glib-networking:amd64 (2.40.0-1) ...
Setting up libplymouth2:amd64 (0.8.8-0ubuntu16) ...
Setting up plymouth (0.8.8-0ubuntu16) ...
Installing new version of config file /etc/init/plymouth-upstart-bridge.conf ...
update-initramfs: deferring update (trigger activated)
Setting up bash-completion (1:2.1-4) ...
Installing new version of config file /etc/profile.d/bash_completion.sh ...
Setting up python-apt-common (0.9.3.5) ...
Setting up python3-apt (0.9.3.5) ...
Setting up zenity-common (3.8.0-1ubuntu1) ...
Setting up zenity (3.8.0-1ubuntu1) ...
Setting up im-config (0.24-1ubuntu4) ...
Installing new version of config file /etc/X11/Xsession.d/70im-config_launch ...
Setting up iso-codes (3.52-1) ...
Setting up libapparmor1:amd64 (2.8.95~2430-0ubuntu5) ...
Setting up dbus (1.6.18-0ubuntu4) ...
Setting up language-selector-common (0.126) ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-hk.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-mo.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-sg.conf ...
Installing new version of config file /etc/fonts/conf.avail/69-language-selector-zh-cn.conf ...
Setting up language-selector-gnome (0.126) ...
Setting up libcurl3-gnutls:amd64 (7.35.0-1ubuntu2) ...
Setting up libparted0debian1:amd64 (2.3-18) ...
Setting up deja-dup (30.0-0ubuntu4) ...
Setting up fonts-droid (1:4.3-3ubuntu1) ...
Setting up libmessaging-menu0 (13.10.1+14.04.20140408-0ubuntu1) ...
Setting up libpackagekit-glib2-16:amd64 (0.8.12-1ubuntu5) ...
Setting up libbamf3-2:amd64 (0.5.1+14.04.20140408-0ubuntu1) ...
Setting up bamfdaemon (0.5.1+14.04.20140408-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libbluetooth3:amd64 (4.101-0ubuntu11) ...
Setting up libclutter-1.0-0:amd64 (1.16.4-0ubuntu2) ...
Setting up libcolumbus1-common (1.1.0+14.04.20140325.3-0ubuntu1) ...
Setting up libcolumbus1:amd64 (1.1.0+14.04.20140325.3-0ubuntu1) ...
Setting up libcurl3:amd64 (7.35.0-1ubuntu2) ...
Setting up libgl1-mesa-dri:amd64 (10.1.0-4ubuntu2) ...
Setting up libwayland-server0:amd64 (1.4.0-1ubuntu1) ...
Setting up libgbm1:amd64 (10.1.0-4ubuntu2) ...
Setting up gconf2-common (3.2.6-0ubuntu2) ...
Installing new version of config file /etc/X11/Xsession.d/70gconfd_path-on-session ...
Setting up libgconf-2-4:amd64 (3.2.6-0ubuntu2) ...
Setting up dbus-x11 (1.6.18-0ubuntu4) ...
Setting up libglibmm-2.4-1c2a:amd64 (2.39.93-0ubuntu1) ...
Setting up libgoa-1.0-common (3.10.3-0ubuntu1) ...
Setting up libgoa-1.0-0b:amd64 (3.10.3-0ubuntu1) ...
Setting up libgutenprint2 (5.2.10~pre2-0ubuntu2) ...
Setting up libharfbuzz0b:amd64 (0.9.27-1) ...
Setting up libharfbuzz-icu0:amd64 (0.9.27-1) ...
Setting up libhud2:amd64 (13.10.1+14.04.20140402-0ubuntu1) ...
Setting up libido3-0.1-0:amd64 (13.10.0+14.04.20140407-0ubuntu1) ...
Setting up libindicator3-7 (12.10.2+14.04.20140402-0ubuntu1) ...
Setting up libopenvg1-mesa:amd64 (10.1.0-4ubuntu2) ...
Setting up libpulsedsp:amd64 (1:4.0-0ubuntu11) ...
Setting up libqt5core5a:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5dbus5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5gui5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5widgets5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5opengl5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5printsupport5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5network5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5sql5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5sql5-sqlite:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5xml5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5test5:amd64 (5.2.1+dfsg-1ubuntu11) ...
Setting up libqt5positioning5:amd64 (5.2.1-1ubuntu1) ...
Setting up libqt5qml5:amd64 (5.2.1-3ubuntu13) ...
Setting up libqt5quick5:amd64 (5.2.1-3ubuntu13) ...
Setting up libqtwebkit4:amd64 (2.3.2-0ubuntu6) ...
Setting up fonts-opensymbol (2:102.6+LibO4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-style-human (1:4.2.3~rc3-0ubuntu1) ...
Setting up uno-libs3 (4.2.3~rc3-0ubuntu1) ...
Setting up ure (4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-common (1:4.2.3~rc3-0ubuntu1) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up libthumbnailer0:amd64 (1.1+14.04.20140401.1-0ubuntu1) ...
Setting up libunity-gtk2-parser0:amd64 (0.0.0+14.04.20140403-0ubuntu1) ...
Setting up libunity-gtk3-parser0:amd64 (0.0.0+14.04.20140403-0ubuntu1) ...
Setting up libwbclient0:amd64 (2:4.1.6+dfsg-1ubuntu2) ...
Setting up libxatracker2:amd64 (10.1.0-4ubuntu2) ...
Setting up qtdeclarative5-localstorage-plugin:amd64 (5.2.1-3ubuntu13) ...
Setting up qtdeclarative5-qtquick2-plugin:amd64 (5.2.1-3ubuntu13) ...
Setting up qtdeclarative5-window-plugin:amd64 (5.2.1-3ubuntu13) ...
Setting up ubuntu-ui-toolkit-theme (0.1.46+14.04.20140404.1.is.0.1.46+14.04.20140404-0ubuntu1) ...
Setting up qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 (0.1.46+14.04.20140404.1.is.0.1.46+14.04.20140404-0ubuntu1) ...
Setting up samba-libs:amd64 (2:4.1.6+dfsg-1ubuntu2) ...
Setting up libsmbclient:amd64 (2:4.1.6+dfsg-1ubuntu2) ...
Setting up samba-common (2:4.1.6+dfsg-1ubuntu2) ...
Replacing config file /etc/samba/smb.conf with new version
Setting up smbclient (2:4.1.6+dfsg-1ubuntu2) ...
Setting up python-samba (2:4.1.6+dfsg-1ubuntu2) ...
Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2) ...
Setting up usbutils (1:007-2ubuntu1) ...
Setting up ubuntu-drivers-common (1:0.2.91.2) ...
Setting up unity-gtk-module-common (0.0.0+14.04.20140403-0ubuntu1) ...
Setting up unity-gtk2-module:amd64 (0.0.0+14.04.20140403-0ubuntu1) ...
Setting up unity-gtk3-module:amd64 (0.0.0+14.04.20140403-0ubuntu1) ...
Setting up libbrlapi0.6:amd64 (5.0-2ubuntu2) ...
Setting up libgsettings-qt1:amd64 (0.1+14.04.20140408-0ubuntu1) ...
Setting up python-sip (4.15.5-1build1) ...
Setting up python-qt4 (4.10.4+dfsg-1build1) ...
Setting up python-qt4-dbus (4.10.4+dfsg-1build1) ...
Setting up python-openssl (0.13-2ubuntu6) ...
Setting up python-ubuntu-sso-client (13.10-0ubuntu6) ...
Setting up ubuntu-sso-client (13.10-0ubuntu6) ...
Setting up ubuntu-sso-client-qt (13.10-0ubuntu6) ...
Setting up apt-utils (0.9.15.4ubuntu5) ...
Setting up ifupdown (0.7.47.2ubuntu4) ...
Setting up isc-dhcp-common (4.2.4-7ubuntu12) ...
Setting up isc-dhcp-client (4.2.4-7ubuntu12) ...
Installing new version of config file /etc/apparmor.d/sbin.dhclient ...
Setting up ubuntu-minimal (1.324) ...
Setting up libapparmor-perl (2.8.95~2430-0ubuntu5) ...
Setting up apparmor (2.8.95~2430-0ubuntu5) ...
Installing new version of config file /etc/apparmor.d/abstractions/base ...
 * Starting AppArmor profiles                                                   Warning from profile /sbin/dhclient (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /sbin/dhclient (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Warning from profile /usr/lib/NetworkManager/nm-dhcp-client.action (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /usr/lib/NetworkManager/nm-dhcp-client.action (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Warning from profile /usr/lib/connman/scripts/dhclient-script (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /usr/lib/connman/scripts/dhclient-script (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/sbin/cups-browsed (/etc/apparmor.d/usr.sbin.cups-browsed) ptrace rules not enforced
Warning from profile /usr/sbin/cups-browsed (/etc/apparmor.d/usr.sbin.cups-browsed) signal rules not enforced
Warning from profile /usr/lib/cups/backend/cups-pdf (/etc/apparmor.d/usr.sbin.cupsd) ptrace rules not enforced
Warning from profile /usr/lib/cups/backend/cups-pdf (/etc/apparmor.d/usr.sbin.cupsd) signal rules not enforced
Warning from profile /usr/sbin/cupsd (/etc/apparmor.d/usr.sbin.cupsd) ptrace rules not enforced
Warning from profile /usr/sbin/cupsd (/etc/apparmor.d/usr.sbin.cupsd) signal rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Warning from profile /usr/sbin/tcpdump (/etc/apparmor.d/usr.sbin.tcpdump) ptrace rules not enforced
Warning from profile /usr/sbin/tcpdump (/etc/apparmor.d/usr.sbin.tcpdump) signal rules not enforced
Warning from profile /usr/bin/evince (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile /usr/bin/evince-previewer (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince-previewer (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile /usr/bin/evince-thumbnailer (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince-thumbnailer (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Warning from profile /sbin/dhclient (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /sbin/dhclient (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Warning from profile /usr/lib/NetworkManager/nm-dhcp-client.action (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /usr/lib/NetworkManager/nm-dhcp-client.action (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Warning from profile /usr/lib/connman/scripts/dhclient-script (/etc/apparmor.d/sbin.dhclient) ptrace rules not enforced
Warning from profile /usr/lib/connman/scripts/dhclient-script (/etc/apparmor.d/sbin.dhclient) signal rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/sbin/cups-browsed (/etc/apparmor.d/usr.sbin.cups-browsed) ptrace rules not enforced
Warning from profile /usr/sbin/cups-browsed (/etc/apparmor.d/usr.sbin.cups-browsed) signal rules not enforced
Warning from profile /usr/lib/cups/backend/cups-pdf (/etc/apparmor.d/usr.sbin.cupsd) ptrace rules not enforced
Warning from profile /usr/lib/cups/backend/cups-pdf (/etc/apparmor.d/usr.sbin.cupsd) signal rules not enforced
Warning from profile /usr/sbin/cupsd (/etc/apparmor.d/usr.sbin.cupsd) ptrace rules not enforced
Warning from profile /usr/sbin/cupsd (/etc/apparmor.d/usr.sbin.cupsd) signal rules not enforced
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Warning from profile /usr/sbin/tcpdump (/etc/apparmor.d/usr.sbin.tcpdump) ptrace rules not enforced
Warning from profile /usr/sbin/tcpdump (/etc/apparmor.d/usr.sbin.tcpdump) signal rules not enforced
Warning from profile /usr/bin/evince (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile /usr/bin/evince-previewer (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince-previewer (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile /usr/bin/evince-thumbnailer (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile /usr/bin/evince-thumbnailer (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.bin.evince) signal rules not enforced
                                                                         [ OK ]
Setting up apt-transport-https (0.9.15.4ubuntu5) ...
Setting up command-not-found-data (0.3ubuntu12) ...
Setting up python3-commandnotfound (0.3ubuntu12) ...
Setting up command-not-found (0.3ubuntu12) ...
Setting up geoip-database (20140313-1) ...
Setting up krb5-locales (1.12+dfsg-2ubuntu3) ...
Setting up openssh-client (1:6.6p1-2) ...
Setting up openssl (1.0.1f-1ubuntu2) ...
Setting up parted (2.3-18) ...
Setting up python-apt (0.9.3.5) ...
Setting up ubuntu-standard (1.324) ...
Setting up libmission-control-plugins0 (1:5.16.1-1ubuntu3) ...
Setting up telepathy-mission-control-5 (1:5.16.1-1ubuntu3) ...
Installing new version of config file /etc/apparmor.d/usr.lib.telepathy ...
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/mission-control-5 (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-* (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile pxgsettings (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile sanitized_helper (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) ptrace rules not enforced
Warning from profile /usr/lib/telepathy/telepathy-ofono (/etc/apparmor.d/usr.lib.telepathy) signal rules not enforced
Setting up empathy-common (3.8.6-0ubuntu9) ...
Setting up empathy (3.8.6-0ubuntu9) ...
Setting up mcp-account-manager-uoa (3.8.6-0ubuntu9) ...
Setting up account-plugin-salut (3.8.6-0ubuntu9) ...
Setting up nautilus-sendto-empathy (3.8.6-0ubuntu9) ...
Setting up account-plugin-aim (3.8.6-0ubuntu9) ...
Setting up account-plugin-jabber (3.8.6-0ubuntu9) ...
Setting up account-plugin-yahoo (3.8.6-0ubuntu9) ...
Setting up libaccount-plugin-generic-oauth (0.11+14.04.20140325-0ubuntu1) ...
Setting up account-plugin-facebook (0.11+14.04.20140325-0ubuntu1) ...
Setting up account-plugin-flickr (0.11+14.04.20140325-0ubuntu1) ...
Setting up libaccount-plugin-google (0.11+14.04.20140325-0ubuntu1) ...
Setting up account-plugin-google (0.11+14.04.20140325-0ubuntu1) ...
Setting up account-plugin-twitter (0.11+14.04.20140325-0ubuntu1) ...
Setting up account-plugin-windows-live (0.11+14.04.20140325-0ubuntu1) ...
Setting up acpid (1:2.0.21-1ubuntu2) ...
Installing new version of config file /etc/acpi/powerbtn.sh ...
acpid start/running, process 19972
Setting up libwhoopsie-preferences0 (0.11) ...
Setting up whoopsie-preferences (0.11) ...
Setting up activity-log-manager (0.9.7-0ubuntu13) ...
Setting up activity-log-manager-control-center (0.9.7-0ubuntu13) ...
Setting up grub-common (2.02~beta2-8) ...
Installing new version of config file /etc/grub.d/05_debian_theme ...
Setting up grub2-common (2.02~beta2-8) ...
Setting up grub-pc-bin (2.02~beta2-8) ...
Setting up grub-pc (2.02~beta2-8) ...
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-19-generic
Found initrd image: /boot/initrd.img-3.13.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up python3-problem-report (2.14.1-0ubuntu1) ...
Setting up python3-apport (2.14.1-0ubuntu1) ...
Setting up apport (2.14.1-0ubuntu1) ...
apport start/running
Setting up apport-gtk (2.14.1-0ubuntu1) ...
Setting up bluez (4.101-0ubuntu11) ...
bluetooth start/running, process 21057
Setting up bluez-alsa:amd64 (4.101-0ubuntu11) ...
Setting up bluez-cups (4.101-0ubuntu11) ...
Setting up bluez-gstreamer (4.101-0ubuntu11) ...
Setting up compiz-core (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up libcompizconfig0 (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up libdecoration0 (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up compiz-plugins-default (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up cpp (4:4.8.2-1ubuntu6) ...
Setting up deja-dup-backend-gvfs (30.0-0ubuntu4) ...
Setting up gcc (4:4.8.2-1ubuntu6) ...
Setting up gedit-common (3.10.4-0ubuntu4) ...
Setting up gedit (3.10.4-0ubuntu4) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode
Setting up gir1.2-goa-1.0 (3.10.3-0ubuntu1) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu17) ...
Setting up gir1.2-messagingmenu-1.0 (13.10.1+14.04.20140408-0ubuntu1) ...
Setting up gir1.2-packagekitglib-1.0 (0.8.12-1ubuntu5) ...
Setting up libtotem-plparser18 (3.10.2-0ubuntu1) ...
Setting up librhythmbox-core8 (3.0.2-0ubuntu1) ...
Setting up rhythmbox-data (3.0.2-0ubuntu1) ...
Setting up gir1.2-rb-3.0 (3.0.2-0ubuntu1) ...
Setting up rhythmbox (3.0.2-0ubuntu1) ...
Setting up rhythmbox-plugin-magnatune (3.0.2-0ubuntu1) ...
Setting up rhythmbox-plugins (3.0.2-0ubuntu1) ...
Setting up rhythmbox-plugin-cdrecorder (3.0.2-0ubuntu1) ...
Setting up rhythmbox-plugin-zeitgeist (3.0.2-0ubuntu1) ...
Setting up rhythmbox-mozilla (3.0.2-0ubuntu1) ...
Setting up libtotem0 (3.10.1-1ubuntu4) ...
Setting up totem-common (3.10.1-1ubuntu4) ...
Setting up totem (3.10.1-1ubuntu4) ...
Setting up totem-mozilla (3.10.1-1ubuntu4) ...
Setting up gir1.2-totem-plparser-1.0 (3.10.2-0ubuntu1) ...
Setting up gir1.2-totem-1.0 (3.10.1-1ubuntu4) ...
Setting up totem-plugins (3.10.1-1ubuntu4) ...
Setting up python3-brlapi (5.0-2ubuntu2) ...
Setting up gnome-orca (3.10.3-0ubuntu1) ...
Setting up gnome-video-effects (0.4.1-0ubuntu1) ...
Setting up hud (13.10.1+14.04.20140402-0ubuntu1) ...
Setting up ibus-gtk:amd64 (1.5.5-1ubuntu3) ...
Setting up ibus-gtk3:amd64 (1.5.5-1ubuntu3) ...
Setting up indicator-application (12.10.1+14.04.20140407-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/indicator-application.desktop ...
Setting up indicator-appmenu (13.01.0+14.04.20140404-0ubuntu1) ...
Setting up indicator-messages (13.10.1+14.04.20140408-0ubuntu1) ...
Setting up indicator-session (12.10.5+14.04.20140403-0ubuntu1) ...
Setting up kerneloops-daemon (0.12+git20090217-3ubuntu8) ...
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match kerneloops Default-Stop values (1)
Setting up landscape-client-ui-install (14.01-0ubuntu3) ...
Setting up libclutter-1.0-common (1.16.4-0ubuntu2) ...
Setting up libgexiv2-2 (0.10.0-0ubuntu2) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1) ...
Setting up libgupnp-1.0-4 (0.20.10-1ubuntu1) ...
Setting up unity-greeter (14.04.9-0ubuntu1) ...
Setting up unity-services (7.2.0+14.04.20140404-0ubuntu1) ...
Setting up libunity-core-6.0-9 (7.2.0+14.04.20140404-0ubuntu1) ...
Setting up ubuntu-mono (14.04+14.04.20140402-0ubuntu1) ...
Setting up light-themes (14.04+14.04.20140402-0ubuntu1) ...
Setting up linux-firmware (1.127) ...
Setting up linux-libc-dev:amd64 (3.13.0-23.45) ...
Setting up python3-cairo (1.10.0+dfsg-3ubuntu2) ...
Setting up onboard (1.0.0-0ubuntu4) ...
Setting up onboard-data (1.0.0-0ubuntu4) ...
Setting up printer-driver-gutenprint (5.2.10~pre2-0ubuntu2) ...
Setting up pulseaudio-utils (1:4.0-0ubuntu11) ...
Setting up pulseaudio-module-x11 (1:4.0-0ubuntu11) ...
Setting up python-commandnotfound (0.3ubuntu12) ...
Setting up python-cups (1.9.66-0ubuntu2) ...
Setting up python-ibus (1.5.5-1ubuntu3) ...
Setting up python-lxml (3.3.3-1) ...
Setting up python-pam (0.4.2-13.1ubuntu3) ...
Setting up python-smbc (1.0.14.1-0ubuntu2) ...
Setting up python3-lxml (3.3.3-1) ...
Setting up python3-markupsafe (0.18-1build2) ...
Setting up unattended-upgrades (0.82.1ubuntu2) ...
Setting up python3-software-properties (0.92.35) ...
Setting up software-properties-common (0.92.35) ...
Setting up software-properties-gtk (0.92.35) ...
Setting up qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets (0.23+14.04.20140407.1-0ubuntu1) ...
Setting up shotwell-common (0.18.0-0ubuntu4) ...
Setting up shotwell (0.18.0-0ubuntu4) ...
Setting up ssh-askpass-gnome (1:6.6p1-2) ...
Setting up ubuntu-artwork (1:14.04+14.04.20140402-0ubuntu1) ...
Setting up ubuntu-docs (14.04.3) ...
Setting up unity-scope-calculator (0.1+14.04.20140328-0ubuntu1) ...
Setting up unity-scope-devhelp (0.1+14.04.20140328-0ubuntu1) ...
Setting up unity-scope-texdoc (0.1+14.04.20140328-0ubuntu1) ...
Setting up usb-creator-common (0.2.56) ...
Setting up usb-creator-gtk (0.2.56) ...
Setting up xserver-xorg-video-sis (1:0.10.7-0ubuntu6) ...
Setting up brltty (5.0-2ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Setting up mobile-broadband-provider-info (20140317-1) ...
Setting up pulseaudio-module-bluetooth (1:4.0-0ubuntu11) ...
Setting up sessioninstaller (0.20+bzr141-0ubuntu4) ...
Setting up usb-modeswitch-data (20140327-1) ...
Setting up usb-modeswitch (2.1.1+repack0-1ubuntu1) ...
Installing new version of config file /etc/usb_modeswitch.conf ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up plymouth-label (0.8.8-0ubuntu16) ...
Setting up lightdm (1.10.0-0ubuntu1) ...
Installing new version of config file /etc/apparmor.d/abstractions/lightdm ...
Setting up plymouth-theme-ubuntu-text (0.8.8-0ubuntu16) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth-theme-ubuntu-logo (0.8.8-0ubuntu16) ...
update-initramfs: deferring update (trigger activated)
Setting up gconf-service-backend (3.2.6-0ubuntu2) ...
Setting up libnss3-nssdb (2:3.15.4-1ubuntu7) ...
Setting up libnss3:amd64 (2:3.15.4-1ubuntu7) ...
Setting up python3-distupgrade (1:0.220) ...
Setting up python3-update-manager (1:0.196.10) ...
Setting up ubuntu-release-upgrader-core (1:0.220) ...
Installing new version of config file /etc/update-manager/release-upgrades ...
Setting up update-manager-core (1:0.196.10) ...
Setting up perl-modules (5.18.2-2ubuntu1) ...
Setting up unity-webapps-service (2.5.0~+14.04.20140324-0ubuntu1) ...
Setting up libunity-webapps0 (2.5.0~+14.04.20140324-0ubuntu1) ...
Setting up gconf-service (3.2.6-0ubuntu2) ...
Setting up gconf2 (3.2.6-0ubuntu2) ...
Setting up libreoffice-core (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-base-core (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-calc (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-gtk (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-gnome (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-draw (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-impress (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-writer (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-pdfimport (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-math (1:4.2.3~rc3-0ubuntu1) ...
Setting up python3-uno (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-ogltrans (1:4.2.3~rc3-0ubuntu1) ...
Setting up ubuntu-release-upgrader-gtk (1:0.220) ...
Setting up update-manager (1:0.196.10) ...
Setting up compiz-gnome (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up compiz (1:0.9.11+14.04.20140408-0ubuntu1) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:4.2.3~rc3-0ubuntu1) ...
Setting up libreoffice-presentation-minimizer (1:4.2.3~rc3-0ubuntu1) ...
Setting up unity (7.2.0+14.04.20140404-0ubuntu1) ...
Setting up ubuntu-desktop (1.324) ...
Setting up unity-webapps-common (2.4.17+14.04.20140403-0ubuntu1) ...
Setting up perl (5.18.2-2ubuntu1) ...
Setting up lintian (2.5.22ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu3) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-19-generic
Processing triggers for libreoffice-common (1:4.2.3~rc3-0ubuntu1) ...
```

Should I do something or will they get fixed when the next updates arrive ?

---

### Post by ventrical on 2014-04-09
This concerns me:

```

grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..

```

I would try using synaptic and see if that helps rectify or report more information.

---

### Post by linuxyogi on 2014-04-13
The above issue is still there but since its not causing any major problem I am leaving it for some time.

Facing another issue now. Today when I installed the updates I saw kernel 3.13.0.24 getting downloaded. After I rebooted I found that installed version is still stuck at 3.13.0-23-generic. 

Then I did ```
sudo apt-get dist-upgrade
``` which installed 3.13.0.24 again which probably means it didnt got installed previously.

Then I did ```
sudo update-grub
``` and rebooted but found that its still stuck at 3.13.0-23.

Next I did a manual install by ```
sudo apt-get install linux-image-3.13.0.24 
```.

Finally the kernel got installed.

I am worried about that fact that I something important may not get installed buy the usual update (gui) and I will using an insecure system without even realizing it.

---

### Post by linuxyogi on 2014-04-13
Big problem !!!

As I said manually installing the kernel worked but now when I boot Ubuntu I get very low resolution by default.

After getting the grub screen by pressing the shift key I found that the default (top) entry is for the "low latency" kernel.

I selected the regular 3.13.0.24 but it gave me an error and ended up in CLI.

I am now using 3.13.0-23-generic.

---

### Post by zika on 2014-04-14
I did not read log thoroughly and thoughtfully but just pointing a finger in the dark: did You install linux-headers for 3.13.0.24?

---

### Post by grahammechanical on 2014-04-14
I have noticed that some things get installed twice, especially kernels. I sometimes see, when using the terminal for updating, that sometimes packages are down loaded but not installed.

It is my guess that sometimes the repository does not have all the dependencies available. So, what the repository has available gets downloaded but not installed until the next day when the missing dependency packages are available and are then download and the whole group are then installed. 

It helps keep me sane to imagine logical reasons for mysteries.

Regards.

---

### Post by linuxyogi on 2014-04-14
Installed the kernel and headers by

```
sudo apt-get install linux-image-3.13.0.24 linux-headers-3.13.0-24-generic  
```

Again by default boots to low latency kernel in low resolution and booting from 3.13.0-24-generic gives me this

```
Gave up waiting for root device. Common problems :
-Boot Args (cat /proc/cmdline)
-Check root delay =(did the system wait long enough?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/desk/by-uuid/1dbe2bf2-e657-4dd8-bb48-21e0dbyc95c5 does not exist.

Busybox u.1.21.1
Ubuntu 1:1:21.0.1ubuntu1
builtinshell (ash)
Enter help for a list of built in commands

(inintramfs)
```

---

### Post by zika on 2014-04-14
> **linuxyogi said:**
> Installed the kernel and headers by```
sudo apt-get install linux-image-3.13.0.24 linux-headers-3.13.0-24-generic  
```I think You're missing third part (common headers file: linux-headers-3.13.0-24) but I might be wrong...
Which kernel is given as default in Grub? There are lowlatency and generic kernels installed?

---

### Post by linuxyogi on 2014-04-14
> **zika said:**
> I think You're missing third part (common headers file: linux-headers-3.13.0-24) but I might be wrong...
Which kernel is given as default in Grub? There are lowlatency and generic kernels installed?

The 3.13.0.24 low latency kernel is becoming the default. 

```
$ dpkg --list | grep linux-image
ii  linux-image-3.13.0-19-generic                         3.13.0-19.40                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-23-generic                         3.13.0-23.45                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.46                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-lowlatency                      3.13.0-24.46                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-19-generic                   3.13.0-19.40                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-23-generic                   3.13.0-23.45                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP


```

```
$ sudo apt-get install linux-headers-3.13.0-24
[sudo] password for techy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.13.0-24 is already the newest version.
linux-headers-3.13.0-24 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by linuxyogi on 2014-04-14
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    4675944 of the same hard drive for core.img. core.img is at this location 
    and looks in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    58,593,279    58,591,232 Data partition (Linux)
/dev/sda2      58,593,280   304,769,023   246,175,744 Data partition (Linux)
/dev/sda3     304,769,024   312,580,095     7,811,072 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5   ext4       
/dev/sda2        aa5bb58e-b5ee-4bec-9bb3-9585f47a791f   ext4       
/dev/sda3        3f986fc2-3411-4fcf-88b7-a0f8c9c7d814   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
else
  search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    else
      search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    fi
    linux    /boot/vmlinuz-3.13.0-24-lowlatency root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-lowlatency-advanced-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-24-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-24-lowlatency root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-lowlatency-recovery-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-24-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-24-lowlatency root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-23-generic-advanced-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-23-generic ...'
        linux    /boot/vmlinuz-3.13.0-23-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-23-generic-recovery-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-23-generic ...'
        linux    /boot/vmlinuz-3.13.0-23-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-19-generic-advanced-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-19-generic ...'
        linux    /boot/vmlinuz-3.13.0-19-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-19-generic-recovery-1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        else
          search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
        fi
        echo    'Loading Linux 3.13.0-19-generic ...'
        linux    /boot/vmlinuz-3.13.0-19-generic root=UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    else
      search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    else
      search --no-floppy --fs-uuid --set=root 1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=1dbe2bf2-e657-4dd8-bb4d-21e0dbfca5c5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=aa5bb58e-b5ee-4bec-9bb3-9585f47a791f /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=3f986fc2-3411-4fcf-88b7-a0f8c9c7d814 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-qsmU9gXo/Tmp_Log: No such file or directory


```

---

### Post by linuxyogi on 2014-04-17
Did a clean install again this time from the final 14.04 release iso. No problems whatsoever.

```
$ uname -a
Linux bond007 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


```

---

