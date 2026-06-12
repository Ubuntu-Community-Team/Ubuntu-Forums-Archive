---
title: "Just wondering..."
date: 2011-01-02
forum: The Cafe
---

### Post by markbabc on 2011-01-02
What do you all get when you run pstree?

I dont run Ubuntu anymore but i recently saw someones pstree output from ubuntu and there was alot in it... so do you all want to post your output of your pstree on a normal day? lol this could even be a competition, whomever has the smallest wins :P

---

### Post by earthpigg on 2011-01-02
```
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;2*[{bonobo-activat}]
     &#9500;&#9472;clock-applet&#9472;&#9472;&#9472;{clock-applet}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-da}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;2*[dbus-launch]
     &#9500;&#9472;ddclient
     &#9500;&#9472;dropbox&#9472;&#9516;&#9472;firefox
     &#9474;         &#9492;&#9472;12*[{dropbox}]
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;run-mozilla.sh&#9472;&#9472;&#9472;firefox-bin&#9472;&#9516;&#9472;plugin-containe&#9472;&#9472;&#9472;{plugin-conta+
     &#9474;                                        &#9492;&#9472;16*[{firefox-bin}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm-binary&#9472;&#9516;&#9472;gdm-simple-slav&#9472;&#9516;&#9472;Xorg
     &#9474;            &#9474;                 &#9500;&#9472;gdm-session-wor&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;applet.+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;at-spi-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;avant-w+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;fusion-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gdu-not+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;mono&#9472;&#9472;&#9472;+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nautilu+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nm-appl+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;polkit-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;python&#9472;+++
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9474;        +++
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;ssh-age+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;update-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9492;&#9472;2*[{gno+
     &#9474;            &#9474;                 &#9474;                 &#9492;&#9472;{gdm-session-wo}
     &#9474;            &#9474;                 &#9492;&#9472;{gdm-simple-sla}
     &#9474;            &#9492;&#9472;{gdm-binary}
     &#9500;&#9472;gdm-user-switch&#9472;&#9472;&#9472;{gdm-user-switc}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;2*[{gnome-keyring-}]
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;3*[{gnome-terminal}]
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-http&#9472;&#9472;&#9472;{gvfsd-http}
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;indicator-apple&#9472;&#9472;&#9472;{indicator-appl}
     &#9500;&#9472;indicator-appli
     &#9500;&#9472;indicator-messa
     &#9500;&#9472;indicator-sound
     &#9500;&#9472;modem-manager
     &#9500;&#9472;multiload-apple&#9472;&#9472;&#9472;{multiload-appl}
     &#9500;&#9472;nmbd
     &#9500;&#9472;notification-ar&#9472;&#9472;&#9472;{notification-a}
     &#9500;&#9472;notify-osd&#9472;&#9472;&#9472;{notify-osd}
     &#9500;&#9472;ntpd
     &#9500;&#9472;pidgin&#9472;&#9472;&#9472;2*[{pidgin}]
     &#9500;&#9472;polkitd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper&#9472;&#9472;&#9472;{gconf-helper}
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;rhythmbox&#9472;&#9472;&#9472;10*[{rhythmbox}]
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;smbd&#9472;&#9472;&#9472;smbd
     &#9500;&#9472;sshd
     &#9500;&#9472;system-service-
     &#9500;&#9472;transmission&#9472;&#9472;&#9472;4*[{transmission}]
     &#9500;&#9472;ubuntu-sso-logi
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;{udisks-daemon}
     &#9500;&#9472;upowerd
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;2*[winbindd]
     &#9500;&#9472;wnck-applet&#9472;&#9472;&#9472;{wnck-applet}
     &#9492;&#9472;wpa_supplicant

```

---

### Post by Skara Brae on 2011-01-02
Sorry for the n00b question, but what is pstree?

"pstree is a Unix command that shows the running processes as a tree."
*from Wikipedia*

Ah :)

This is what I get:

```
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activat}
     &#9500;&#9472;clock-applet
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-da}]
     &#9500;&#9472;couchdb&#9472;&#9472;&#9472;couchdb&#9472;&#9472;&#9472;beam&#9472;&#9472;&#9472;heart
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;2*[dbus-launch]
     &#9500;&#9472;desktopcouch-se&#9472;&#9472;&#9472;desktopcouch-se
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data}]
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-exch}
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;run-mozilla.sh&#9472;&#9472;&#9472;firefox-bin&#9472;&#9516;&#9472;npviewer.bin
     &#9474;                                        &#9492;&#9472;16*[{firefox-bin}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm-binary&#9472;&#9516;&#9472;gdm-simple-slav&#9472;&#9516;&#9472;Xorg
     &#9474;            &#9474;                 &#9500;&#9472;gdm-session-wor&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;bluetoo+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;compiz&#9472;+++
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;evoluti+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gdu-not+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nautilu+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nm-appl+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;polkit-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;python
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;ssh-age+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;update-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9492;&#9472;{gnome-+
     &#9474;            &#9474;                 &#9474;                 &#9492;&#9472;{gdm-session-wo}
     &#9474;            &#9474;                 &#9492;&#9472;{gdm-simple-sla}
     &#9474;            &#9492;&#9472;{gdm-binary}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;2*[{gnome-keyring-}]
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;2*[{gnome-terminal}]
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-computer
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9516;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-inpu
     &#9474;      &#9474;             &#9492;&#9472;6*[hald-addon-stor]
     &#9474;      &#9492;&#9472;{hald}
     &#9500;&#9472;modem-manager
     &#9500;&#9472;notification-ar
     &#9500;&#9472;notify-osd
     &#9500;&#9472;polkitd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;2*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;{udisks-daemon}
     &#9500;&#9472;upowerd
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;wnck-applet&#9472;&#9472;&#9472;{wnck-applet}
     &#9492;&#9472;wpa_supplicant

```

---

### Post by Skara Brae on 2011-01-02
> **markbabc said:**
> I dont run Ubuntu anymore
What do you run then, if I may be so curious?

---

### Post by sandyd on 2011-01-02
```
init-+-NetworkManager-+-dhcpcd
     |                `-2*[{NetworkManager}]
     |-acpid
     |-6*[agetty]
     |-akonadi_control-+-7*[akonadi_agent_l---{akonadi_agent_}]
     |                 |-akonadi_maildis
     |                 |-2*[akonadi_nepomuk---{akonadi_nepomu}]
     |                 |-akonadiserver---18*[{akonadiserver}]
     |                 `-4*[{akonadi_contro}]
     |-amarok---19*[{amarok}]
     |-avahi-daemon---avahi-daemon
     |-avahi-dnsconfd
     |-console-kit-dae---64*[{console-kit-da}]
     |-crond
     |-cupsd
     |-3*[dbus-daemon]
     |-2*[dbus-launch]
     |-dropbox---14*[{dropbox}]
     |-gconfd-2
     |-gvfs-gphoto2-vo
     |-gvfsd
     |-kaccess
     |-kactivitymanage
     |-kded4---3*[{kded4}]
     |-kdeinit4-+-firefox-+-plugin-containe---{plugin-contain}
     |          |         `-16*[{firefox}]
     |          |-kio_file
     |          |-kio_http
     |          |-kio_http_cache_
     |          |-kio_trash---2*[{kio_trash}]
     |          |-klauncher
     |          |-kmess
     |          |-konqueror
     |          |-ksmserver-+-kwin---2*[{kwin}]
     |          |           `-{ksmserver}
     |          `-transmission-qt---2*[{transmission-q}]
     |-kdesud
     |-kdm-+-X
     |     `-kdm---startkde---kwrapper4
     |-kget---2*[{kget}]
     |-kglobalaccel
     |-klipper
     |-kmix---{kmix}
     |-knotify4---6*[{knotify4}]
     |-konsole-+-bash---sudo---emerge---sandbox---ebuild.sh---ebuild.sh---emake---make---mak+
     |         |-bash---pstree
     |         `-{konsole}
     |-kopete---4*[{kopete}]
     |-korgac
     |-krunner---6*[{krunner}]
     |-kuiserver
     |-kwalletd
     |-kwalletmanager
     |-modem-manager
     |-mysqld---9*[{mysqld}]
     |-nepomukserver-+-nepomukservices-+-virtuoso-t---4*[{virtuoso-t}]
     |               |                 `-12*[{nepomukservice}]
     |               |-2*[nepomukservices---{nepomukservice}]
     |               |-nepomukservices---2*[{nepomukservice}]
     |               |-nepomukservices
     |               `-{nepomukserver}
     |-plasma-desktop-+-ksysguardd
     |                `-2*[{plasma-desktop}]
     |-polkit-kde-auth---{polkit-kde-aut}
     |-polkitd---{polkitd}
     |-preload
     |-psad
     |-psadwatchd
     |-pulseaudio---{pulseaudio}
     |-soffice.bin---7*[{soffice.bin}]
     |-start_kdeinit
     |-strigidaemon---5*[{strigidaemon}]
     |-syslog-ng---syslog-ng
     |-udevd---2*[udevd]
     |-udisks-daemon-+-udisks-daemon
     |               `-2*[{udisks-daemon}]
     |-upowerd---{upowerd}
     `-wpa_supplicant

```

---

### Post by cariboo on 2011-01-02
Here's mine:

```
pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bamfdaemon
     &#9500;&#9472;chromium-browse&#9472;&#9516;&#9472;chromium-browse
     &#9474;                 &#9500;&#9472;chromium-browse&#9472;&#9472;&#9472;{chromium-brows}
     &#9474;                 &#9492;&#9472;33*[{chromium-brows}]
     &#9500;&#9472;chromium-browse&#9472;&#9472;&#9472;3*[chromium-browse&#9472;&#9472;&#9472;{chromium-brows}]
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;64*[{console-kit-da}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;3*[dbus-daemon]
     &#9500;&#9472;2*[dbus-launch]
     &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;{dconf-service}
     &#9500;&#9472;dcopserver
     &#9500;&#9472;file-roller&#9472;&#9472;&#9472;{file-roller}
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm-binary&#9472;&#9516;&#9472;gdm-simple-slav&#9472;&#9516;&#9472;Xorg
     &#9474;            &#9474;                 &#9500;&#9472;gdm-session-wor&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;applet.py
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;bluetooth-apple&#9472;&#9472;&#9472;{bluetooth-appl}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;compiz&#9472;&#9516;&#9472;sh&#9472;&#9472;&#9472;gtk-window-deco&#9472;&#9472;&#9472;{gtk-window-dec}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9474;        &#9492;&#9472;{compiz}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;docky&#9472;&#9516;&#9472;python
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9474;       &#9492;&#9472;10*[{docky}]
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gdu-notificatio
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-power-man&#9472;&#9472;&#9472;{gnome-power-ma}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gwibber-service&#9472;&#9516;&#9472;2*[gwibber-service]
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9474;                 &#9492;&#9472;4*[{gwibber-servic}]
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;indicator-weath&#9472;&#9472;&#9472;{indicator-weat}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nm-applet&#9472;&#9472;&#9472;{nm-applet}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;polkit-gnome-au&#9472;&#9472;&#9472;{polkit-gnome-a}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;seahorse-agent&#9472;&#9472;&#9472;{seahorse-agent}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;update-notifier&#9472;&#9472;&#9472;{update-notifie}
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9492;&#9472;2*[{gnome-session}]
     &#9474;            &#9474;                 &#9474;                 &#9492;&#9472;{gdm-session-wo}
     &#9474;            &#9474;                 &#9492;&#9472;{gdm-simple-sla}
     &#9474;            &#9492;&#9472;{gdm-binary}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;3*[{gnome-keyring-}]
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;2*[{gnome-terminal}]
     &#9500;&#9472;gsd-locate-poin
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-http&#9472;&#9472;&#9472;{gvfsd-http}
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hddtemp
     &#9500;&#9472;indicator-appli
     &#9500;&#9472;indicator-datet
     &#9500;&#9472;indicator-me-se&#9472;&#9472;&#9472;{indicator-me-s}
     &#9500;&#9472;indicator-messa
     &#9500;&#9472;indicator-sessi&#9472;&#9472;&#9472;{indicator-sess}
     &#9500;&#9472;indicator-sound&#9472;&#9472;&#9472;{indicator-soun}
     &#9500;&#9472;irqbalance
     &#9500;&#9472;kded
     &#9500;&#9472;kdeinit&#9472;&#9516;&#9472;kio_file
     &#9474;         &#9492;&#9472;klauncher
     &#9500;&#9472;knotify
     &#9500;&#9472;modem-manager
     &#9500;&#9472;notify-osd&#9472;&#9472;&#9472;{notify-osd}
     &#9500;&#9472;polkitd&#9472;&#9472;&#9472;{polkitd}
     &#9500;&#9472;portmap
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper&#9472;&#9472;&#9472;{gconf-helper}
     &#9474;            &#9492;&#9472;3*[{pulseaudio}]
     &#9500;&#9472;qbittorrent&#9472;&#9472;&#9472;7*[{qbittorrent}]
     &#9500;&#9472;quanta
     &#9500;&#9472;rpc.statd
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;2*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;sshd
     &#9500;&#9472;system-service-
     &#9500;&#9472;ubuntu-sso-logi
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;2*[{udisks-daemon}]
     &#9500;&#9472;unity-panel-ser&#9472;&#9472;&#9472;{unity-panel-se}
     &#9500;&#9472;upowerd&#9472;&#9472;&#9472;{upowerd}
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;uptimed
     &#9500;&#9472;vmware-usbarbit
     &#9500;&#9472;wpa_supplicant
     &#9492;&#9472;zeitgeist-daemo&#9472;&#9516;&#9472;cat
                       &#9500;&#9472;zeitgeist-datah
                       &#9492;&#9472;{zeitgeist-daem}
```

---

### Post by themusicalduck on 2011-01-02
Here we go -

```
init-+-NetworkManager
     |-acpid
     |-atd
     |-avahi-daemon---avahi-daemon
     |-bonobo-activati---2*[{bonobo-activat}]
     |-chromium-browse-+-chromium-browse
     |                 |-chromium-browse---9*[chromium-browse---2*[{chromium-brows}]]
     |                 |-chromium-browse---2*[{chromium-brows}]
     |                 |-chromium-browse---{chromium-brows}
     |                 `-26*[{chromium-brows}]
     |-clock-applet---{clock-applet}
     |-console-kit-dae---63*[{console-kit-da}]
     |-cron
     |-cupsd
     |-2*[dbus-daemon]
     |-dbus-launch
     |-ddclient
     |-dropbox---14*[{dropbox}]
     |-gconfd-2
     |-gdm-binary-+-gdm-simple-slav-+-Xorg
     |            |                 |-gdm-session-wor-+-gnome-session-+-.ConkyWizardLau---conky---5*[{conky}]
     |            |                 |                 |               |-applet.py
     |            |                 |                 |               |-at-spi-registry---{at-spi-registr}
     |            |                 |                 |               |-compiz-+-sh---gtk-window-deco---{gtk-window-dec}
     |            |                 |                 |               |        `-{compiz}
     |            |                 |                 |               |-docky-+-3*[python]
     |            |                 |                 |               |       |-python---{python}
     |            |                 |                 |               |       `-12*[{docky}]
     |            |                 |                 |               |-gdu-notificatio
     |            |                 |                 |               |-glippy---5*[{glippy}]
     |            |                 |                 |               |-gnome-do---gnome-do---6*[{gnome-do}]
     |            |                 |                 |               |-gnome-panel---{gnome-panel}
     |            |                 |                 |               |-gnome-power-man---{gnome-power-ma}
     |            |                 |                 |               |-gnome-user-shar---{gnome-user-sha}
     |            |                 |                 |               |-nautilus---3*[{nautilus}]
     |            |                 |                 |               |-nm-applet---{nm-applet}
     |            |                 |                 |               |-polkit-gnome-au
     |            |                 |                 |               |-ssh-agent
     |            |                 |                 |               |-synapse
     |            |                 |                 |               |-tracker-miner-f
     |            |                 |                 |               |-tracker-status-
     |            |                 |                 |               |-tracker-store
     |            |                 |                 |               |-update-notifier---{update-notifie}
     |            |                 |                 |               `-2*[{gnome-session}]
     |            |                 |                 `-{gdm-session-wo}
     |            |                 `-{gdm-simple-sla}
     |            `-{gdm-binary}
     |-6*[getty]
     |-gnome-keyring-d---3*[{gnome-keyring-}]
     |-gnome-screensav
     |-gnome-settings----{gnome-settings}
     |-gnome-terminal-+-bash---pstree
     |                |-gnome-pty-helpe
     |                `-2*[{gnome-terminal}]
     |-gvfs-afc-volume---{gvfs-afc-volum}
     |-gvfs-fuse-daemo---3*[{gvfs-fuse-daem}]
     |-gvfs-gdu-volume
     |-gvfs-gphoto2-vo
     |-gvfsd
     |-gvfsd-burn
     |-gvfsd-metadata
     |-gvfsd-trash
     |-2*[indicator-apple---{indicator-appl}]
     |-indicator-appli
     |-indicator-me-se---{indicator-me-s}
     |-indicator-messa
     |-indicator-sessi---{indicator-sess}
     |-indicator-sound
     |-modem-manager
     |-mount.ntfs-3g
     |-multiload-apple---{multiload-appl}
     |-nmbd
     |-notification-ar---{notification-a}
     |-notify-osd---{notify-osd}
     |-polkitd
     |-pulseaudio-+-gconf-helper---{gconf-helper}
     |            `-4*[{pulseaudio}]
     |-rsyslogd---2*[{rsyslogd}]
     |-rtkit-daemon---2*[{rtkit-daemon}]
     |-smbd---smbd
     |-sshd
     |-system-service-
     |-ubuntu-sso-logi
     |-udevd---2*[udevd]
     |-udisks-daemon-+-udisks-daemon
     |               `-{udisks-daemon}
     |-upowerd
     |-upstart-udev-br
     |-winbindd---3*[winbindd]
     |-wnck-applet---{wnck-applet}
     |-wpa_supplicant
     `-zeitgeist-daemo-+-cat
                       |-zeitgeist-datah
                       `-{zeitgeist-daem}
```

---

### Post by markbabc on 2011-01-02
> **Skara Brae said:**
> What do you run then, if I may be so curious?

Arch Linux. if you wana see my pstree i will post it if you want. I just wanted to know the kind of processes that ubuntu runs default.

---

### Post by andymorton on 2011-01-02
```
andy@oscar:~$ pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;{NetworkManager}
     &#9500;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bluetoothd
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activat}
     &#9500;&#9472;chrome&#9472;&#9516;&#9472;chrome
     &#9474;        &#9500;&#9472;chrome&#9472;&#9472;&#9472;{chrome}
     &#9474;        &#9500;&#9472;chrome&#9472;&#9472;&#9472;11*[{chrome}]
     &#9474;        &#9492;&#9472;23*[{chrome}]
     &#9500;&#9472;chrome&#9472;&#9472;&#9472;4*[chrome&#9472;&#9472;&#9472;{chrome}]
     &#9500;&#9472;clock-applet
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-da}]
     &#9500;&#9472;couchdb&#9472;&#9472;&#9472;couchdb&#9472;&#9472;&#9472;beam.smp&#9472;&#9516;&#9472;couchjs&#9472;&#9472;&#9472;{couchjs}
     &#9474;                              &#9500;&#9472;heart
     &#9474;                              &#9492;&#9472;6*[{beam.smp}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;desktopcouch-se&#9472;&#9472;&#9472;desktopcouch-se
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm-binary&#9472;&#9516;&#9472;gdm-simple-slav&#9472;&#9516;&#9472;Xorg
     &#9474;            &#9474;                 &#9500;&#9472;gdm-session-wor&#9472;&#9516;&#9472;gnome-session&#9472;&#9516;&#9472;avant-w+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;bluetoo+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;compiz&#9472;+++
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;evoluti+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gdu-not+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gnome-p+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;gwibber+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nautilu+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;nm-appl+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;polkit-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;python
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;ssh-age+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9500;&#9472;update-+
     &#9474;            &#9474;                 &#9474;                 &#9474;               &#9492;&#9472;{gnome-+
     &#9474;            &#9474;                 &#9474;                 &#9492;&#9472;{gdm-session-wo}
     &#9474;            &#9474;                 &#9492;&#9472;{gdm-simple-sla}
     &#9474;            &#9492;&#9472;{gdm-binary}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;3*[{gnome-keyring-}]
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9516;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-cpuf
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-inpu
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-leds
     &#9474;      &#9474;             &#9492;&#9472;hald-addon-rfki
     &#9474;      &#9492;&#9472;{hald}
     &#9500;&#9472;indicator-apple&#9472;&#9472;&#9472;{indicator-appl}
     &#9500;&#9472;indicator-apple
     &#9500;&#9472;indicator-appli
     &#9500;&#9472;indicator-me-se
     &#9500;&#9472;indicator-messa
     &#9500;&#9472;indicator-sessi
     &#9500;&#9472;indicator-sound
     &#9500;&#9472;modem-manager
     &#9500;&#9472;notification-ar
     &#9500;&#9472;notify-osd
     &#9500;&#9472;polkitd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;2*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;syndaemon
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;{udisks-daemon}
     &#9500;&#9472;upowerd
     &#9500;&#9472;upstart-udev-br
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9500;&#9472;wnck-applet
     &#9492;&#9472;wpa_supplicant
andy@oscar:~$ 

```

---

### Post by earthpigg on 2011-01-02
> **markbabc said:**
> Arch Linux. if you wana see my pstree i will post it if you want. I just wanted to know the kind of processes that ubuntu runs default.

im curious, please share.

---

### Post by markbabc on 2011-01-02
> **earthpigg said:**
> im curious, please share.
```

init&#9472;&#9516;&#9472;6*[agetty]
     &#9500;&#9472;chromium&#9472;&#9472;&#9472;2*[chromium&#9472;&#9472;&#9472;{chromium}]
     &#9500;&#9472;ck-launch-sessi&#9472;&#9472;&#9472;startx&#9472;&#9472;&#9472;xinit&#9472;&#9516;&#9472;X
     &#9474;                                  &#9492;&#9472;dwm&#9472;&#9516;&#9472;chromium&#9472;&#9516;&#9472;chromium
     &#9474;                                        &#9474;          &#9500;&#9472;chromium&#9472;&#9472;&#9472;4*[{chromium}]
     &#9474;                                        &#9474;          &#9492;&#9472;19*[{chromium}]
     &#9474;                                        &#9500;&#9472;sh&#9472;&#9472;&#9472;dropbox&#9472;&#9472;&#9472;14*[{dropbox}]
     &#9474;                                        &#9500;&#9472;sh&#9472;&#9472;&#9472;sleep
     &#9474;                                        &#9492;&#9472;urxvt&#9472;&#9472;&#9472;zsh&#9472;&#9472;&#9472;pstree
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;64*[{console-kit-da}]
     &#9500;&#9472;crond
     &#9500;&#9472;3*[dbus-daemon]
     &#9500;&#9472;2*[dbus-launch]
     &#9500;&#9472;dhcpcd
     &#9500;&#9472;polkitd&#9472;&#9472;&#9472;{polkitd}
     &#9500;&#9472;sshd
     &#9500;&#9472;syslog-ng&#9472;&#9472;&#9472;syslog-ng
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9492;&#9472;wicd&#9472;&#9516;&#9472;dhcpcd
            &#9492;&#9472;wicd-monitor

```
normally i also have irssi running so that would add another urxvt-zsh-irssi

---

### Post by piquat on 2011-01-03
Wow!  That's like... nothing compared to mine/most.  I had heard this about Arch, nice to actually see it.

Thanks!

---

### Post by markbabc on 2011-01-03
> **piquat said:**
> Wow!  That's like... nothing compared to mine/most.  I had heard this about Arch, nice to actually see it.

Thanks!

lol you have to remember that im not running a DE (desktop environment) like gnome, kde, xfce, ect, ect. im only running a WM (windows manager) called DWM

---

### Post by Skara Brae on 2011-01-05
> **markbabc said:**
> Arch Linux. if you wana see my pstree i will post it if you want. I just wanted to know the kind of processes that ubuntu runs default.
Noooooo, I am barely more than a n00b, it would (and does) not mean much to me. I was only being curious.

So, am I correct in assuming that the smaller the "tree" is, the faster Linux runs?

---

### Post by TeoBigusGeekus on 2011-01-05
On arch.
```
init&#9472;&#9516;&#9472;5*[agetty]
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;64*[{console-kit-da}]
     &#9500;&#9472;crond
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dhcpcd
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;hald&#9472;&#9516;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;      &#9474;             &#9500;&#9472;hald-addon-inpu
     &#9474;      &#9474;             &#9492;&#9472;hald-addon-stor
     &#9474;      &#9492;&#9472;{hald}
     &#9500;&#9472;login&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;xinit&#9472;&#9516;&#9472;X
     &#9474;                      &#9492;&#9472;ck-launch-sessi&#9472;&#9516;&#9472;numlockx
     &#9474;                                        &#9500;&#9472;openbox&#9472;&#9516;&#9472;opera&#9472;&#9516;&#9472;operapluginclea
     &#9474;                                        &#9474;         &#9474;       &#9500;&#9472;operapluginwrap
     &#9474;                                        &#9474;         &#9474;       &#9492;&#9472;6*[{opera}]
     &#9474;                                        &#9474;         &#9500;&#9472;sh&#9472;&#9472;&#9472;conky&#9472;&#9472;&#9472;5*[{conky}]
     &#9474;                                        &#9474;         &#9500;&#9472;sh&#9472;&#9472;&#9472;xterm&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                                        &#9474;         &#9492;&#9472;xterm&#9472;&#9472;&#9472;rtorrent
     &#9474;                                        &#9492;&#9472;xscreensaver
     &#9500;&#9472;polkitd&#9472;&#9472;&#9472;{polkitd}
     &#9500;&#9472;syslog-ng&#9472;&#9472;&#9472;syslog-ng
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9492;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
                     &#9492;&#9472;2*[{udisks-daemon}]
```

---

