---
title: "Apparmor &amp; qbittorrent"
date: 2023-04-02
forum: Security
---

### Post by yann20 on 2023-04-02
Hi everyone,
I just created an Apparmor profile for Qbittorrent.
Problem, when I launch it, I now have this error message:

[HTML]QtSingleCoreApplication: listen on local socket failed, QLocalServer::listen: Permission denied
dbus[176899]: The last reference on a connection was dropped without closing the connection. This is a bug in an application. See dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.
  D-Bus not built with -rdynamic so unable to print a backtrace
Abandon (core dumped)[/HTML]

Here is my configuration file :

[HTML]# Last Modified: Sun Apr  2 16:11:00 2023
abi <abi/3.0>,

include <tunables/global>

/usr/bin/qbittorrent {
  include <abstractions/base>
  include <abstractions/dbus-session>
  include <abstractions/evince>
  include <abstractions/gnome>
  include <abstractions/nameservice>
  include <abstractions/openssl>

  network netlink dgram,

  dbus send bus=session path=/org/freedesktop/DBus interface=org.freedesktop.DBus member=Hello peer=(label=unconfined),

  /etc/gai.conf r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /home/*/Documents/Scripts/ipfilter/ipfilter.dat r,
  /proc/sys/kernel/random/boot_id r,
  /run/dbus/system_bus_socket rw,
  /run/systemd/resolve/stub-resolv.conf r,
  /usr/bin/qbittorrent mr,
  /var/lib/flatpak/exports/share/icons/hicolor/icon-theme.cache r,
  /var/lib/flatpak/exports/share/icons/hicolor/index.theme r,
  owner /home/*/.config/ibus/bus/c30cf36e462f42069d1fcb48a126bad8-unix-0 r,
  owner /home/*/.config/qBittorrent/#52822024 rw,
  owner /home/*/.config/qBittorrent/#52822528 rw,
  owner /home/*/.config/qBittorrent/.vmfEZz/ rw,
  owner /home/*/.config/qBittorrent/.vmfEZz/s rw,
  owner /home/*/.config/qBittorrent/categories.json r,
  owner /home/*/.config/qBittorrent/ipc-socket w,
  owner /home/*/.config/qBittorrent/lockfile rwk,
  owner /home/*/.config/qBittorrent/qBittorrent-data.conf r,
  owner /home/*/.config/qBittorrent/qBittorrent.conf rw,
  owner /home/*/.config/qBittorrent/qBittorrent_new.conf rwl,
  owner /home/*/.config/qBittorrent/qBittorrent_new.conf.lock rwk,
  owner /home/*/.config/qBittorrent/rss/feeds.json r,
  owner /home/*/.config/qBittorrent/rss/storage.lock w,
  owner /home/*/.config/qBittorrent/watched_folders.json r,
  owner /home/*/.config/user-dirs.dirs r,
  owner /home/*/.config/qBittorrent/qBittorrent.conf rw,
  owner /home/*/.local/share/qBittorrent/BT_backup/ r,
  owner /home/*/.local/share/qBittorrent/BT_backup/#52822041 rw,
  owner /home/*/.local/share/qBittorrent/BT_backup/#52822152 rw,
  owner /home/*/.local/share/qBittorrent/BT_backup/6c4a7b695a578b2d96e8f00a532c8e82d40347b8.fastresume rw,
  owner /home/*/.local/share/qBittorrent/BT_backup/6c4a7b695a578b2d96e8f00a532c8e82d40347b8.fastresume.AREMkQ rwl,
  owner /home/*/.local/share/qBittorrent/BT_backup/6c4a7b695a578b2d96e8f00a532c8e82d40347b8.torrent r,
  owner /home/*/.local/share/qBittorrent/BT_backup/9a2b0b5789697a40cfae69d7ed1eae1c9209f277.fastresume rw,
  owner /home/*/.local/share/qBittorrent/BT_backup/9a2b0b5789697a40cfae69d7ed1eae1c9209f277.fastresume.NjBXyQ rwl,
  owner /home/*/.local/share/qBittorrent/BT_backup/9a2b0b5789697a40cfae69d7ed1eae1c9209f277.torrent r,
  owner /home/*/.local/share/qBittorrent/GeoDB/dbip-country-lite.mmdb r,
  owner /home/*/.local/share/qBittorrent/logs/ r,
  owner /home/*/.local/share/qBittorrent/logs/qbittorrent.log w,
  owner /home/*/.local/share/qBittorrent/rss/articles/storage.lock w,
  owner /proc/*/cmdline r,
  owner /proc/*/comm r,
  owner /run/user/1000/ICEauthority r,
  owner /run/user/1000/at-spi/bus_0 rw,
  owner /run/user/1000/bus rw,
  owner /run/user/1000/gdm/Xauthority r,

}[/HTML]

What should I do? 
Thanks to you!

---

### Post by #&amp;thj^% on 2023-04-02
May I ask what version of qbittorrent? and desktop used?
```
apt policy qbittorrent && echo $DESKTOP_SESSION

```
Details will matter here

---

### Post by yann20 on 2023-04-02
[HTML]apt policy qbittorrent && echo $DESKTOP_SESSION
qbittorrent:
  Installé : 4.4.1-2
  Candidat : 4.4.1-2
 Table de version :
 *** 4.4.1-2 500
        500 http://fr.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status[/HTML]

---

### Post by #&amp;thj^% on 2023-04-03
Take a look at mine, been using this one for awhile now:
```
#  AppArmor profile for qBittorrent
# ---------------------------------------------
# Author: Nibaldo Gonzalez <nibgonz@gmail.com>
# Last change: July 15, 2019

# NOTE:
#  - This profile is more restrictive than the one provided
#    in <abstractions/ubuntu-bittorrent-clients>.
#  - This profile is only tested on Ubuntu 18.04 & 16.04 with KDE Plasma 5.

# Requirements:
#    apparmor.d/tunables/confidential
#    apparmor.d/abstractions/networkmanager-strict
#    apparmor.d/abstractions/udisk-strict
#    apparmor.d/abstractions/flatpak-snap
#    apparmor.d/abstractions/general-security
#    apparmor.d/abstractions/confidential-deny
#    apparmor.d/abstractions/open-browser
#    apparmor.d/abstractions/open-email
#    apparmor.d/abstractions/open-some-applications
#    apparmor.d/abstractions/kde-user

include <tunables/global>
include <tunables/confidential>

#  - Important: Check & change the torrents directory
#    according to qBittorrent configuration.
#  - By default, there is only write access to the torrent directory.

# Torrents directory. Modify according to qBittorrent configuration.
@{TORRENTS_DIR} = @{HOME}/Descargas/Torrents

profile qbittorrent /usr/bin/qbittorrent {
	include <abstractions/base>
	include <abstractions/nameservice>
	include <abstractions/fonts>
	include <abstractions/dbus-session>
	include <abstractions/X>
	include <abstractions/freedesktop.org>
	include <abstractions/xdg-desktop>

	include <abstractions/networkmanager-strict>
	include <abstractions/udisk-strict>
	include <abstractions/wayland>
	include <abstractions/flatpak-snap>

	# Blocks binaries, precompiled libraries, etc.
	include <abstractions/general-security>

	# Block full access to sensitive data, as passwords and keys.
	# Includes /boot/**, /var/log/** & /etc/apparmor.d/** directories. View in: tunables/confidential.
	include <abstractions/confidential-deny>

	# Needed to open links (only for some Web browsers/e-mail clients).
	include <abstractions/open-browser>
	include <abstractions/open-email>

	# Required to open downloaded files.
	include <abstractions/open-some-applications>

	network netlink dgram,

	## include <abstractions/dbus-strict>
	# NOTE: The application does not start with bus=system
	dbus (send)
		bus=*
		path=/org/freedesktop/DBus
		interface=org.freedesktop.DBus
		member={Hello,AddMatch,RemoveMatch,GetNameOwner,NameHasOwner,StartServiceByName}
		peer=(name=org.freedesktop.DBus),
	# member={Hello,AddMatch,RemoveMatch,GetNameOwner}
	# peer=(name=org.freedesktop.DBus label=unconfined)
	dbus (receive)
		bus=system
		path=/org/freedesktop/NetworkManager
		interface=org.freedesktop.NetworkManager
		member=PropertiesChanged,

	# Access to Home
	owner @{TORRENTS_DIR}/{,**} rw,                  # Just read/write in the Torrents directory
	owner @{HOME}/**.[tT][oO][rR][rR][eE][nN][tT] r, # Only read .torrent files
	owner @{HOME}/{,[^.]**/} r,                      # Only read directories
	deny @{HOME}/{,**/}.directory r,

	# qBittorrent configuration
	owner @{HOME}/.config/qBittorrent/{,**} rwk,
	owner @{HOME}/.config/qBittorrentrc* rwk,
	owner @{HOME}/.local/share/data/qBittorrent/{,**} rwk,
	owner @{HOME}/.local/share/data/ rw,
	owner @{HOME}/.cache/qBittorrent/{,**} rw,

	# Local configuration
	include <abstractions/kde-user>
	owner @{HOME}/.config/kio* r,
	owner @{HOME}/.config/kdebugrc rw,
	owner @{HOME}/.config/kde.org/libphonon.conf r,
	owner @{HOME}/.kde/share/config/{kde,kio}* r,
	owner @{HOME}/.kde/share/config/ktinfowidgetpluginrc rw,
	owner @{HOME}/.kde/share/config/kcookiejarrc r,
	owner @{HOME}/.kde/share/config/breezerc r,
	owner @{HOME}/.kde/share/config/ktimezonedrc r,
	owner @{HOME}/.kde/share/config/*.new rwk,
	owner @{HOME}/.local/share/qt_temp.* rwk,
	owner @{HOME}/.local/share/kservices5/{,**} r,
	owner @{HOME}/.cache/mesa_shader_cache/** rw,

	link @{HOME}/.config/qBittorrentrc* -> "/home/*/.config/#[0-9]*",
	link @{HOME}/.config/qBittorrent/*  -> "/home/*/.config/qBittorrent/#[0-9]*",
	link @{HOME}/.config/qBittorrent/**/* -> "/home/*/.config/qBittorrent/**/#[0-9]*",
	link @{HOME}/.config/qBittorrent/qBittorrent.conf -> "/home/*/.config/qBittorrent/qBittorrent_new.conf",

	#link @{HOME}/.local/share/data/qBittorrent/BT_backup/* -> "/home/*/.local/share/data/qBittorrent/BT_backup/#[0-9]*",
	link @{HOME}/.local/share/data/qBittorrent/*  -> "/home/*/.local/share/data/qBittorrent/#[0-9]*",
	link @{HOME}/.local/share/data/qBittorrent/**/* -> "/home/*/.local/share/data/qBittorrent/**/#[0-9]*",

	deny /{media,mnt,srv,net}/** rwklmx,  # Block access to mounted drives & other directories

	# Binaries
	/usr/bin/qbittorrent r,
	/usr/bin/kdeinit{4,5} ixr,
	/usr/bin/{gnome,gvfs,xdg}-open ixr,
	/usr/bin/kde-open{,5} ixr,
	/usr/bin/kdialog ixr,

	# Libraries
	/usr/lib{,64,/@{multiarch}}/qt5/plugins/{,**/} r,
	/usr/lib{,64,/@{multiarch}}/qt5/plugins/**.so mr,
	#/usr/lib{,64,/@{multiarch}}/libQt5*.so{,.[0-9]*} m,

	/usr/share/color-schemes/{,**} r,
	/usr/share/GeoIP/{,*} r,
	/usr/share/knotifications5/{,*} r,
	/usr/share/kservices5/{,**/,**.protocol} r,
	/usr/share/plasma/{,**} r,
	/usr/share/qt5/{,**} r,
	/usr/share/sounds/{,**} r,
	/usr/share/mime/ r,
	/usr/share/templates/ r,
	/usr/share/hwdata/pnp.ids r,
	/usr/share/drirc.d/{,**} r,

	/etc/xdg/{,**} r,
	/etc/machine-id r,
	/etc/pulse/client.conf r,
	/etc/ssl/openssl.cnf r,
	/etc/udev/udev.conf r,
	deny /etc/fstab r,

	/dev/**/ r,
	/dev/tty r,
	owner /{dev,run,var/run}/shm/pulse-shm-* rwk,

	/sys/**/ r,
	/sys/devices/**/uevent r,
	/sys/devices/pci[0-9]*/**/{busnum,config,revision} r,
	/sys/devices/pci[0-9]*/**/{,subsystem_}{device,vendor} r,
	/sys/devices/pci[0-9]*/**/id{Product,Vendor} r,
	owner @{PROC}/@{pid}/mounts r,
	@{PROC}/sys/kernel/random/boot_id r,
	@{PROC}/sys/kernel/core_pattern r, # investigate
	#owner @{PROC}/@{pid}/mountinfo r, # investigate

	# Temporal files & sockets
	owner /tmp/xauth-[0-9]* r,
	owner /tmp/*-qBitto* rwk,
	owner /tmp/qt_temp.* rwk,
	owner /tmp/qtsingleapp-qBitto-* rwk,
	owner /tmp/[0-9]*/ rw,
	owner /tmp/.[a-zA-Z0-9]*/{,*} rw,
	owner /{,var/}tmp/{,.}qBitto** rwk,
	owner /var/tmp/kdecache-*/{,*} rwk,
	owner /run/user/[0-9]*/ksocket-*/{,qBitto*} rwk,
	owner /run/user/[0-9]*/kioclient*-socket rwk,
	owner /run/user/[0-9]*/qBitto*-socket rwk,
	owner /run/user/[0-9]*/#[0-9]* rwk,

	link /run/user/[0-9]*/qBittorrent*.slave-socket -> "/run/user/[0-9]*/#[0-9]*",
	link /tmp/.qBittorrent/* -> "/tmp/.qBittorrent/#[0-9]*",

	owner /run/user/[0-9]*/bus rwk,
	/{,var/}run/dbus/system_bus_socket rw,

	signal (send) set=(term) peer=unconfined,
}

# kate: syntax AppArmor Security Profile; replace-tabs off; remove-trailing-spaces mod;
# vim:  syntax=apparmor
```
I'm not the original author, but some the code is mine:
```
sudo aa-status
apparmor module is loaded.
37 profiles are loaded.
35 profiles are in enforce mode.
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince//sanitized_helper
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ntpd
   /{,usr/}sbin/dhclient
   firejail-default
   ippusbxd
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   libvirtd
   libvirtd//qemu_bridge_helper
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   rsyslogd
   swtpm
   tcpdump
   virt-aa-helper
2 profiles are in complain mode.
   libreoffice-oosplash
   libreoffice-soffice
0 profiles are in kill mode.
0 profiles are in unconfined mode.
17 processes have profiles defined.
17 processes are in enforce mode.
   /usr/sbin/cups-browsed (5534) 
   /usr/sbin/cupsd (5397) 
   /usr/sbin/ntpd (38751) 
   /usr/lib/firefox/firefox (28621) firejail-default
   /usr/lib/firefox/firefox (28811) firejail-default
   /usr/lib/firefox/firefox (28863) firejail-default
   /usr/lib/firefox/firefox (28965) firejail-default
   /usr/lib/firefox/firefox (29110) firejail-default
   /usr/lib/firefox/firefox (29119) firejail-default
   /usr/lib/firefox/firefox (29167) firejail-default
   /usr/lib/firefox/firefox (32579) firejail-default
   /usr/lib/firefox/firefox (88895) firejail-default
   /usr/lib/firefox/firefox (150958) firejail-default
   /usr/lib/firefox/firefox (151706) firejail-default
   /usr/lib/firefox/firefox (157872) firejail-default
   /usr/local/bin/qbittorrent (177449) firejail-default//&unconfined
   /usr/sbin/rsyslogd (2497) rsyslogd
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.
0 processes are in kill mode.

```
```
/etc/apparmor.d branch: (HEAD) 
>> ls
abi                    usr.bin.man
abstractions          **_[COLOR="#FF0000"] usr.bin.qbittorrent[/COLOR]_**
disable                usr.bin.swtpm
firejail-default       usr.bin.tcpdump
force-complain         usr.lib.libreoffice.program.oosplash
libvirt                usr.lib.libreoffice.program.senddoc
lightdm-guest-session  usr.lib.libreoffice.program.soffice.bin
local                  usr.lib.libreoffice.program.xpdfimport
lsb_release            usr.lib.libvirt.virt-aa-helper
nvidia_modprobe        usr.lib.snapd.snap-confine.real
rsyslog.d              usr.sbin.cups-browsed
samba                  usr.sbin.cupsd
sbin.dhclient          usr.sbin.ippusbxd
tunables               usr.sbin.libvirtd
usr.bin.evince         usr.sbin.ntpd
usr.bin.firefox        usr.sbin.rsyslogd
```

---

