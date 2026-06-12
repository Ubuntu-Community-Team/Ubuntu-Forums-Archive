---
title: "libwayland0 updates itself - why?"
date: 2013-03-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-07
Not having Weston installed on this PC , why does libwayland0 upgrade itself when i am not even using it ?? or am I?

 Is this a Mir depend? If so then please merge this thread with the other Mir discussion.

Thankyou.

---

### Post by zika on 2013-03-07
> **ventrical said:**
> Not having Weston installed on this PC , why does libwayland0 upgrade itself when i am not even using it ?? or am I?

 Is this a Mir depend? If so then please merge this thread with the other Mir discussion.

Thankyou.
This what happens if I simulate purge of libwayland0, it seems as if I took the very fist brick in a wall called Ubuntu...
```
:~$ sudo apt-get purge libwayland0 -s[sudo] password for zika: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  audacious-plugins-data gir1.2-gtop-2.0 gstreamer1.0-alsa gstreamer1.0-nice
  gstreamer1.0-plugins-base-apps guile-2.0-libs im-config libaudclient2
  libbinio1ldbl libboost-program-options1.49.0 libbs2b0 libcue1
  libfarstream-0.2-2 libfluidsynth1 libgc1c3 libguess1 libmowgli2
  libsofia-sip-ua-glib3 libsofia-sip-ua0 libtelepathy-farstream3
  oneconf-common python-oneconf python-pywapi python3-oneconf
  python3-piston-mini-client python3-xdg telepathy-rakia
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  account-plugin-empathy* account-plugin-facebook* account-plugin-flickr*
  account-plugin-google* account-plugin-identica* account-plugin-twitter*
  account-plugin-windows-live* activity-log-manager-control-center* aisleriot*
  alacarte* apport-gtk* apturl* audacious* audacious-plugins* bamfdaemon*
  baobab* brasero* brasero-cdrkit* caribou* compiz* compiz-gnome* dconf-tools*
  deja-dup* deja-dup-backend-gvfs* deja-dup-backend-ubuntuone* empathy* eog*
  evince* evolution-data-server* file-roller* gcalctool* gconf-editor* gcr*
  gdm* gedit* gir1.2-appindicator3-0.1* gir1.2-caribou-1.0*
  gir1.2-clutter-1.0* gir1.2-cogl-1.0* gir1.2-coglpango-1.0* gir1.2-gcr-3*
  gir1.2-gdata-0.0* gir1.2-gkbd-3.0* gir1.2-gnomebluetooth-1.0*
  gir1.2-gnomedesktop-3.0* gir1.2-goa-1.0* gir1.2-gtk-3.0*
  gir1.2-gtksource-3.0* gir1.2-mutter-3.0* gir1.2-nmgtk-1.0*
  gir1.2-panelapplet-4.0* gir1.2-peas-1.0* gir1.2-rb-3.0* gir1.2-totem-1.0*
  gir1.2-ubuntuoneui-3.0* gir1.2-vte-2.90* gir1.2-webkit-3.0* gir1.2-wnck-3.0*
  gkbd-capplet* gnome-applets* gnome-bluetooth* gnome-calculator*
  gnome-contacts* gnome-control-center* gnome-control-center-signon*
  gnome-control-center-unity* gnome-disk-utility* gnome-font-viewer*
  gnome-icon-theme* gnome-icon-theme-full* gnome-icon-theme-symbolic*
  gnome-keyring* gnome-mahjongg* gnome-media* gnome-mines*
  gnome-online-accounts* gnome-orca* gnome-panel* gnome-power-manager*
  gnome-screensaver* gnome-screenshot* gnome-session* gnome-session-bin*
  gnome-session-canberra* gnome-session-fallback* gnome-settings-daemon*
  gnome-shell* gnome-shell-extensions* gnome-sudoku* gnome-system-log*
  gnome-system-monitor* gnome-terminal* gnome-themes-standard*
  gnome-tweak-tool* gnome-user-guide* gnome-user-share* gnomine*
  gstreamer1.0-clutter* gtk3-engines-unico* gucharmap* gvfs-backends* gwibber*
  gwibber-service-facebook* gwibber-service-identica* gwibber-service-twitter*
  hud* humanity-icon-theme* ibus* ibus-gtk3* ibus-pinyin* ibus-table*
  indicator-applet-complete* indicator-application* indicator-appmenu*
  indicator-datetime* indicator-messages* indicator-power* indicator-printers*
  indicator-session* indicator-sound* indicator-sync* indicator-weather*
  landscape-client-ui-install* language-selector-gnome*
  libaccount-plugin-1.0-0* libappindicator3-1* libaudcore1* libbamf3-1*
  libbrasero-media3-1* libcanberra-gtk3-0* libcanberra-gtk3-module*
  libcaribou0* libclutter-1.0-0* libclutter-gst-2.0-0* libclutter-gtk-1.0-0*
  libcogl-pango12* libcogl12* libcolord-gtk1* libebackend-1.2-6*
  libebook-1.2-14* libebook-contacts-1.2-0* libecal-1.2-15*
  libedata-book-1.2-17* libedata-cal-1.2-20* libedataserver-1.2-17*
  libegl1-mesa* libegl1-mesa-drivers* libevdocument3-4* libevview3-3*
  libfolks-eds25* libgail-3-0* libgcr-3-1* libgdata13* libgnome-bluetooth11*
  libgnome-desktop-3-4* libgnome-desktop-3-7* libgnome-media-profiles-3.0-0*
  libgnomekbd8* libgoa-1.0-0* libgrip0* libgtk-3-0* libgtk-3-bin*
  libgtkmm-3.0-1* libgtksourceview-3.0-0* libgtkspell-3-0*
  libgucharmap-2-90-7* libgweather-3-1* libgweather-3-3* libgwibber-gtk3*
  libido3-0.1-0* libindicator3-7* libmirserver0* libmutter0a*
  libnautilus-extension1a* libnm-gtk0* libpanel-applet-4-0* libpeas-1.0-0*
  librhythmbox-core6* libsyncdaemon-1.0-1* libtimezonemap1* libtotem0*
  libubuntuoneui-3.0-1* libunity-core-6.0-5* libunity-misc4*
  libunity-webapps0* libvte-2.90-9* libwayland0* libwebkitgtk-3.0-0*
  libwnck-3-0* libyelp0* light-themes* lightdm-remote-session-freerdp*
  lightdm-remote-session-uccsconfigure* mcp-account-manager-uoa* metacity*
  mir* mousetweaks* mutter* nautilus* nautilus-sendto*
  nautilus-sendto-empathy* nautilus-share* network-manager-gnome*
  network-manager-pptp-gnome* notification-daemon* notify-osd* onboard*
  oneconf* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3*
  pavucontrol* policykit-1-gnome* python-aptdaemon.gtk3widgets*
  python-ubuntu-sso-client* python-ubuntuone-control-panel*
  python3-aptdaemon.gtk3widgets* remmina* remmina-plugin-rdp*
  remmina-plugin-vnc* rhythmbox* rhythmbox-mozilla*
  rhythmbox-plugin-cdrecorder* rhythmbox-plugin-magnatune*
  rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone*
  seahorse* sessioninstaller* shotwell* simple-scan* software-center*
  software-properties-gtk* stormcloud* synaptic* system-config-printer-gnome*
  telepathy-indicator* thunderbird-gnome-support* totem* totem-mozilla*
  totem-plugins* transmission-gtk* ubuntu-artwork* ubuntu-desktop*
  ubuntu-docs* ubuntu-mono* ubuntu-release-upgrader-gtk* ubuntu-sso-client*
  ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-gnome*
  ubuntuone-control-panel* ubuntuone-control-panel-qt* unity*
  unity-asset-pool* unity-greeter* unity-lens-photos* unity-scope-gdrive*
  unity-scope-musicstores* unity-services* unity-tweak-tool*
  unity-webapps-common* unity-webapps-service* update-manager*
  update-notifier* usb-creator-gtk* vino* xdg-user-dirs-gtk* xdiagnose*
  xul-ext-unity* xul-ext-websites-integration* yelp* zenity*
0 upgraded, 0 newly installed, 273 to remove and 0 not upgraded.
Purg account-plugin-empathy [3.7.90-0ubuntu1~raring2]
Purg gwibber-service-facebook [3.6.0-0ubuntu2]
Purg account-plugin-facebook [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-flickr [0.10bzr13.02.27-0ubuntu1]
Purg unity-scope-gdrive [0.8daily12.12.05-0ubuntu1]
Purg account-plugin-google [0.10bzr13.02.27-0ubuntu1]
Purg gwibber-service-identica [3.6.0-0ubuntu2]
Purg account-plugin-identica [0.10bzr13.02.27-0ubuntu1]
Purg gwibber-service-twitter [3.6.0-0ubuntu2]
Purg account-plugin-twitter [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-windows-live [0.10bzr13.02.27-0ubuntu1]
Purg activity-log-manager-control-center [0.9.4-0ubuntu6.1]
Purg aisleriot [1:3.4.1+really3.2.3.2-0ubuntu3]
Purg alacarte [3.7.90-0ubuntu1~raring1]
Purg apport-gtk [2.9-0ubuntu2]
Purg nautilus-share [0.7.3-1ubuntu3]
Purg apturl [0.5.1ubuntu6]
Purg audacious [3.3.4-1]
Purg audacious-plugins [3.3.4-1]
Purg unity-tweak-tool [0.0.3-0~85~raring1]
Purg ubuntu-desktop [1.295]
Purg lightdm-remote-session-uccsconfigure [1.1-0ubuntu2]
Purg unity [6.12.0daily13.03.06.1bzr3194pkg0raring0]
Purg indicator-appmenu [13.01.0daily13.02.20-0ubuntu1]
Purg hud [13.04.0daily13.02.20-0ubuntu2]
Purg libbamf3-1 [0.4.0daily13.02.06bzr523pkg0raring0]
Purg bamfdaemon [0.4.0daily13.02.06bzr523pkg0raring0]
Purg baobab [3.7.90-0ubuntu1~raring1]
Purg brasero [3.6.1-0ubuntu2]
Purg brasero-cdrkit [3.6.1-0ubuntu2]
Purg gnome-shell-extensions [3.7.91~git20130305.dda35127-0ubuntu1~13.04~ricotz0]
Purg gnome-shell [3.7.91+git20130306.3b1e5368-0ubuntu1~13.04~ricotz0]
Purg caribou [0.4.8-0ubuntu1~raring2]
Purg compiz [1:0.9.9~daily13.03.06bzr3633pkg0raring0]
Purg compiz-gnome [1:0.9.9~daily13.03.06bzr3633pkg0raring0]
Purg gdm [3.7.90-0ubuntu1~raring2]
Purg dconf-tools [0.15.3-0ubuntu1]
Purg deja-dup-backend-ubuntuone [25.5-0ubuntu1]
Purg deja-dup-backend-gvfs [25.5-0ubuntu1]
Purg deja-dup [25.5-0ubuntu1]
Purg mcp-account-manager-uoa [3.7.90-0ubuntu1~raring2]
Purg nautilus-sendto-empathy [3.7.90-0ubuntu1~raring2]
Purg empathy [3.7.90-0ubuntu1~raring2]
Purg eog [3.7.4-0ubuntu1~raring2]
Purg evince [3.7.90-0ubuntu1~raring1]
Purg gnome-contacts [3.7.90-0ubuntu1~raring3]
Purg libfolks-eds25 [0.9.1-0ubuntu1~raring1]
Purg evolution-data-server [3.7.90-0ubuntu1~raring3]
Purg file-roller [3.7.90-0ubuntu1~raring1]
Purg gcalctool [1:3.7.90-0ubuntu1]
Purg gconf-editor [3.0.1-1ubuntu2]
Purg seahorse [3.7.5-0ubuntu1~raring1]
Purg ubuntuone-control-panel-qt [4.1.91-0ubuntu1]
Purg ubuntu-sso-client-qt [4.1.91-0ubuntu1]
Purg ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg ubuntuone-client-gnome [4.1.91-0ubuntu1]
Purg gir1.2-ubuntuoneui-3.0 [4.1.2-0ubuntu1]
Purg libubuntuoneui-3.0-1 [4.1.2-0ubuntu1]
Purg libsyncdaemon-1.0-1 [4.1.91-0ubuntu1]
Purg ubuntuone-client [4.1.91-0ubuntu1]
Purg software-center [5.5.5-0ubuntu1]
Purg oneconf [0.3.3]
Purg ubuntu-sso-client [4.1.91-0ubuntu1]
Purg python-ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg python-ubuntu-sso-client [4.1.91-0ubuntu1]
Purg gnome-keyring [3.7.5-0ubuntu1~raring1]
Purg gcr [3.7.5-0ubuntu1~raring1]
Purg gedit [3.7.5-0ubuntu1~raring1]
Purg gir1.2-appindicator3-0.1 [12.10.1daily13.02.15-0ubuntu1]
Purg gir1.2-caribou-1.0 [0.4.8-0ubuntu1~raring2]
Purg gir1.2-mutter-3.0 [3.7.91+git20130306.df8ad83c-0ubuntu1~13.04~ricotz0]
Purg gir1.2-clutter-1.0 [1.13.7+git20130224.5c2931a2-0ubuntu1~13.04~ricotz0]
Purg gir1.2-coglpango-1.0 [1.13.4-0ubuntu1]
Purg gir1.2-cogl-1.0 [1.13.4-0ubuntu1]
Purg gir1.2-gcr-3 [3.7.5-0ubuntu1~raring1]
Purg unity-lens-photos [0.9daily12.12.05bzr124pkg0raring0]
Purg gir1.2-gdata-0.0 [0.13.3~git20130216.0fd7b768-0ubuntu1~raring0]
Purg gir1.2-gkbd-3.0 [3.6.0-0ubuntu1]
Purg gnome-user-share [3.0.4-0ubuntu1]
Purg gnome-bluetooth [3.6.1-0ubuntu2]
Purg gir1.2-gnomebluetooth-1.0 [3.6.1-0ubuntu2]
Purg gnome-tweak-tool [3.7.4-0ubuntu1~raring1]
Purg gir1.2-gnomedesktop-3.0 [3.7.90-0ubuntu1~raring1]
Purg gir1.2-goa-1.0 [3.6.2-1]
Purg stormcloud [1.1-0~6~raring1]
Purg rhythmbox-plugin-magnatune [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg rhythmbox-plugins [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg rhythmbox-plugin-zeitgeist [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg rhythmbox-mozilla [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg rhythmbox-plugin-cdrecorder [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg unity-scope-musicstores [6.8.1daily13.03.04bzr132pkg0raring0]
Purg rhythmbox-ubuntuone [4.1.91-0ubuntu1]
Purg rhythmbox [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg gir1.2-rb-3.0 [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg totem-plugins [3.7.0~git20130226.64cfed80-0ubuntu1~13.04~ricotz0]
Purg gir1.2-totem-1.0 [3.7.0~git20130226.64cfed80-0ubuntu1~13.04~ricotz0]
Purg gir1.2-peas-1.0 [1.7.0-0ubuntu1~raring1]
Purg gir1.2-gtksource-3.0 [3.7.90-0ubuntu1~raring1]
Purg gnome-applets [3.5.92-0ubuntu1]
Purg gir1.2-panelapplet-4.0 [1:3.6.2-0ubuntu3]
Purg xdiagnose [3.4.3]
Purg usb-creator-gtk [0.2.46.1]
Purg ubuntu-release-upgrader-gtk [1:0.192.5] [update-notifier:amd64 update-manager:amd64 ]
Purg update-manager [1:0.184] [update-notifier:amd64 ]
Purg update-notifier [0.131]
Purg software-properties-gtk [0.92.14.1]
Purg sessioninstaller [0.20+bzr134-0ubuntu4]
Purg language-selector-gnome [0.106]
Purg python3-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg landscape-client-ui-install [12.12-0ubuntu3]
Purg python-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg onboard [0.99.0~alpha1~tr1190-0ubuntu1]
Purg gwibber [3.6.0-0ubuntu2]
Purg gnome-sudoku [1:3.7.4-0ubuntu1]
Purg gnome-orca [3.7.91-0ubuntu1]
Purg gir1.2-wnck-3.0 [3.4.5-0ubuntu1]
Purg gir1.2-webkit-3.0 [1.10.2-0ubuntu1]
Purg gir1.2-vte-2.90 [1:0.34.2-0ubuntu2]
Purg gir1.2-nmgtk-1.0 [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg gir1.2-gtk-3.0 [3.7.13+git20130306.ca2368db-0ubuntu1~13.04~ricotz2]
Purg gnome-control-center-unity [1.2daily13.02.15bzr15pkg0raring0]
Purg gnome-control-center-signon [0.1.2bzr12.12.05-0ubuntu2~raring1]
Purg indicator-power [12.10.6daily13.01.25-0ubuntu1]
Purg indicator-datetime [12.10.3daily13.03.06-0ubuntu1]
Purg gnome-control-center [1:3.7.90-0ubuntu1~raring4]
Purg gkbd-capplet [3.6.0-0ubuntu1]
Purg gnome-calculator [1:3.7.90-0ubuntu1]
Purg gnome-disk-utility [3.7.2-0ubuntu1~raring1]
Purg gnome-font-viewer [3.7.5-0ubuntu1]
Purg unity-asset-pool [0.8.24daily12.12.05bzr65pkg0raring0]
Purg totem-mozilla [3.7.0~git20130226.64cfed80-0ubuntu1~13.04~ricotz0]
Purg totem [3.7.0~git20130226.64cfed80-0ubuntu1~13.04~ricotz0]
Purg gnome-session-fallback [3.7.90-0ubuntu1~raring2]
Purg gnome-panel [1:3.6.2-0ubuntu3]
Purg gnome-icon-theme-symbolic [3.7.5-0ubuntu1~raring0]
Purg indicator-weather [12.07.30-0ubuntu2]
Purg ubuntu-artwork [1:13.04daily13.03.05-0ubuntu1]
Purg light-themes [13.04daily13.03.05-0ubuntu1]
Purg ubuntu-mono [13.04daily13.03.05-0ubuntu1]
Purg system-config-printer-gnome [1.3.11+20120807-0ubuntu14]
Purg simple-scan [3.6.0-2]
Purg network-manager-gnome [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg metacity [1:2.34.13-0ubuntu1]
Purg ibus-table [1.5.0.is.1.4.99.1-1ubuntu1]
Purg ibus-pinyin [1.4.0-1build1]
Purg ibus [1.4.2-0ubuntu1]
Purg humanity-icon-theme [0.6.1]
Purg gnome-screensaver [3.6.1-0ubuntu3]
Purg gnome-icon-theme [3.7.4-0ubuntu1~raring1] [gnome-icon-theme-full:amd64 ]
Purg gnome-icon-theme-full [3.7.4-0ubuntu1~raring1]
Purg gnome-mahjongg [1:3.7.90-0ubuntu1]
Purg gnome-media [3.4.0-1ubuntu1]
Purg gnomine [1:3.7.5-0ubuntu1]
Purg gnome-mines [1:3.7.5-0ubuntu1]
Purg gnome-online-accounts [3.6.2-1]
Purg gnome-power-manager [3.6.0-1]
Purg gnome-screenshot [3.7.5-0ubuntu1~raring1]
Purg gnome-session [3.7.90-0ubuntu1~raring2]
Purg gnome-session-bin [3.7.90-0ubuntu1~raring2]
Purg gnome-session-canberra [0.30-0ubuntu1]
Purg unity-greeter [13.04.1-0ubuntu2]
Purg indicator-session [12.10.5daily13.03.06-0ubuntu1]
Purg gnome-settings-daemon [3.7.90-0ubuntu1~raring1]
Purg gnome-system-log [3.6.1-0ubuntu1]
Purg gnome-system-monitor [3.7.90-0ubuntu1]
Purg gnome-terminal [3.7.2-0ubuntu1~raring1]
Purg mutter [3.7.91+git20130306.df8ad83c-0ubuntu1~13.04~ricotz0]
Purg gnome-themes-standard [3.7.91+git20130305.d9d75ae7-0ubuntu1~13.04~ricotz0]
Purg gnome-user-guide [3.6.2-0ubuntu1]
Purg gstreamer1.0-clutter [2.1.0~git20130131.dc2d3c0a-0ubuntu1~13.04~ricotz0]
Purg gtk3-engines-unico [1.0.3daily12.12.12-0ubuntu1]
Purg gucharmap [1:3.6.1-0ubuntu1]
Purg gvfs-backends [1.15.4-0ubuntu1]
Purg ibus-gtk3 [1.4.2-0ubuntu1]
Purg indicator-applet-complete [12.10.2daily13.03.01-0ubuntu1]
Purg indicator-application [12.10.1daily13.01.25-0ubuntu1]
Purg indicator-messages [12.10.6daily13.02.13-0ubuntu1]
Purg indicator-printers [0.1.7+bzr64pkg0raring1]
Purg indicator-sound [12.10.2daily13.02.25-0ubuntu1]
Purg indicator-sync [12.10.5daily13.01.25-0ubuntu1]
Purg libaccount-plugin-1.0-0 [0.1.2bzr12.12.05-0ubuntu2~raring1]
Purg vino [3.7.90-0ubuntu1~raring1]
Purg transmission-gtk [2.77-0ubuntu1]
Purg remmina-plugin-vnc [1.0.0-4ubuntu1]
Purg remmina-plugin-rdp [1.0.0-4ubuntu1]
Purg remmina [1.0.0-4ubuntu1]
Purg libbrasero-media3-1 [3.6.1-0ubuntu2]
Purg libappindicator3-1 [12.10.1daily13.02.15-0ubuntu1]
Purg libaudcore1 [3.3.4-1]
Purg libmutter0a [3.7.91+git20130306.df8ad83c-0ubuntu1~13.04~ricotz0]
Purg pavucontrol [1.0-1]
Purg notification-daemon [0.7.6-1]
Purg libcanberra-gtk3-module [0.30-0ubuntu1]
Purg libcanberra-gtk3-0 [0.30-0ubuntu1]
Purg libcaribou0 [0.4.8-0ubuntu1~raring2]
Purg libclutter-gst-2.0-0 [2.1.0~git20130131.dc2d3c0a-0ubuntu1~13.04~ricotz0]
Purg libtotem0 [3.7.0~git20130226.64cfed80-0ubuntu1~13.04~ricotz0]
Purg libclutter-gtk-1.0-0 [1.4.2-0ubuntu2]
Purg libclutter-1.0-0 [1.13.7+git20130224.5c2931a2-0ubuntu1~13.04~ricotz0]
Purg libcogl-pango12 [1.13.4-0ubuntu1]
Purg libcogl12 [1.13.4-0ubuntu1]
Purg libcolord-gtk1 [0.1.24-0ubuntu1]
Purg thunderbird-gnome-support [17.0.3+build1-0ubuntu1]
Purg nautilus-sendto [3.6.1-0ubuntu1]
Purg libebook-1.2-14 [3.7.90-0ubuntu1~raring3]
Purg libedata-book-1.2-17 [3.7.90-0ubuntu1~raring3]
Purg libedata-cal-1.2-20 [3.7.90-0ubuntu1~raring3]
Purg libebackend-1.2-6 [3.7.90-0ubuntu1~raring3]
Purg libebook-contacts-1.2-0 [3.7.90-0ubuntu1~raring3]
Purg libecal-1.2-15 [3.7.90-0ubuntu1~raring3]
Purg libedataserver-1.2-17 [3.7.90-0ubuntu1~raring3]
Purg mir [0.0.2+bzr467raring1]
Purg libmirserver0 [0.0.2+bzr467raring1]
Purg libegl1-mesa-drivers [9.2.0~git20130301.58bd926d-0ubuntu0sarvatt]
Purg libegl1-mesa [9.2.0~git20130301.58bd926d-0ubuntu0sarvatt]
Purg libevview3-3 [3.7.90-0ubuntu1~raring1]
Purg libevdocument3-4 [3.7.90-0ubuntu1~raring1]
Purg nautilus [1:3.7.90-0ubuntu1~raring2]
Purg librhythmbox-core6 [2.98+git20130301.f3df3036-0ubuntu1~13.04~ricotz0]
Purg ubuntu-docs [12.10.3]
Purg yelp [3.7.4-0ubuntu1~raring1]
Purg libyelp0 [3.7.4-0ubuntu1~raring1]
Purg lightdm-remote-session-freerdp [1.0-0ubuntu2]
Purg zenity [3.7.2-0ubuntu1~raring1]
Purg shotwell [0.13.1-0ubuntu3]
Purg libgdata13 [0.13.3~git20130216.0fd7b768-0ubuntu1~raring0]
Purg libgoa-1.0-0 [3.6.2-1]
Purg libwebkitgtk-3.0-0 [1.10.2-0ubuntu1]
Purg libgail-3-0 [3.7.13+git20130306.ca2368db-0ubuntu1~13.04~ricotz2]
Purg libgcr-3-1 [3.7.5-0ubuntu1~raring1]
Purg libgnome-bluetooth11 [3.6.1-0ubuntu2]
Purg libgnome-desktop-3-4 [3.7.2-0ubuntu1~raring4]
Purg libgnome-desktop-3-7 [3.7.90-0ubuntu1~raring1]
Purg libgnome-media-profiles-3.0-0 [3.0.0-1ubuntu1]
Purg libgnomekbd8 [3.6.0-0ubuntu1]
Purg libgrip0 [0.3.6daily13.02.26-0ubuntu1]
Purg libgweather-3-1 [3.7.2-0ubuntu1~raring1]
Purg libunity-core-6.0-5 [6.12.0daily13.03.06.1bzr3194pkg0raring0]
Purg unity-services [6.12.0daily13.03.06.1bzr3194pkg0raring0]
Purg libunity-misc4 [4.0.5daily13.02.26bzr36pkg0raring0]
Purg libgtk-3-bin [3.7.13+git20130306.ca2368db-0ubuntu1~13.04~ricotz2]
Purg libgweather-3-3 [3.7.90-0ubuntu1~raring1]
Purg libnautilus-extension1a [1:3.7.90-0ubuntu1~raring2]
Purg libgtksourceview-3.0-0 [3.7.90-0ubuntu1~raring1]
Purg libpeas-1.0-0 [1.7.0-0ubuntu1~raring1]
Purg synaptic [0.80~exp1]
Purg libpanel-applet-4-0 [1:3.6.2-0ubuntu3]
Purg xdg-user-dirs-gtk [0.10-0ubuntu1]
Purg unity-webapps-common [2.4.13-0ubuntu1]
Purg xul-ext-unity [2.4.4bzr13.01.29-0ubuntu1]
Purg xul-ext-websites-integration [2.3.5.1-0ubuntu1]
Purg unity-webapps-service [2.4.4~daily13.03.06-0ubuntu1] [libunity-webapps0:amd64 ]
Purg libunity-webapps0 [2.4.4~daily13.03.06-0ubuntu1]
Purg telepathy-indicator [0.3.1daily13.03.01-0ubuntu1]
Purg libnm-gtk0 [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg policykit-1-gnome [0.105-1ubuntu4]
Purg overlay-scrollbar-gtk3 [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar:amd64 ]
Purg overlay-scrollbar [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar-gtk2:amd64 ]
Purg overlay-scrollbar-gtk2 [0.2.16+r359daily13.02.06-0ubuntu1]
Purg notify-osd [0.9.35daily12.11.28-0ubuntu1]
Purg network-manager-pptp-gnome [0.9.6.0-0ubuntu2]
Purg mousetweaks [3.6.0-0ubuntu2]
Purg libwnck-3-0 [3.4.5-0ubuntu1]
Purg libvte-2.90-9 [1:0.34.2-0ubuntu2]
Purg libtimezonemap1 [0.3.2build1]
Purg libindicator3-7 [12.10.2daily13.02.25-0ubuntu1]
Purg libido3-0.1-0 [12.10.3daily13.03.01-0ubuntu1]
Purg libgwibber-gtk3 [3.6.0-0ubuntu2]
Purg libgucharmap-2-90-7 [1:3.6.1-0ubuntu1]
Purg libgtkspell-3-0 [3.0.0~hg20110814-1build1]
Purg libgtkmm-3.0-1 [3.6.0-0ubuntu1]
Purg libgtk-3-0 [3.7.13+git20130306.ca2368db-0ubuntu1~13.04~ricotz2]
Purg libwayland0 [1.0.5-0ubuntu1]
```

---

### Post by ventrical on 2013-03-07
Thats a real stunner!!

Now you're scaring me ! :)lol

'Wayland is a protocol for a compositor to talk to its clients as well
as a C library implementation of that protocol. The compositor can be
a standalone display server running on Linux kernel modesetting and
evdev input devices, an X application, or a wayland client
itself. The clients can be traditional applications, X servers
(rootless or fullscreen) or other display servers.

This is an experimental library package, neither ABI or API are fixed
right now. As a consequence, generated dependencies are made as
strict as possible. It should only be used by mesa and weston for
the time being.'

Thats the info from synaptic.  That thing is threaded in there like a worm, How did it get this far?

---

### Post by zika on 2013-03-07
You've made me try weston and I'm writing this from Chromium in Weston... ;)

---

### Post by grahammechanical on 2013-03-07
libwayland0 is not on my 12.04 that I am at present using to burn an ISO image. I intend to put in a 12.10 and a 13.04 fresh install to test the MIR PPA on. I will let you know if libwayland0 is on 12.10 and 13.04 or if the MIR PPA brings it in.

---

### Post by ventrical on 2013-03-07
> **grahammechanical said:**
> libwayland0 is not on my 12.04 that I am at present using to burn an ISO image. I intend to put in a 12.10 and a 13.04 fresh install to test the MIR PPA on. I will let you know if libwayland0 is on 12.10 and 13.04 or if the MIR PPA brings it in.

Thats exactly where I was going with this. Thanks!! The honours are yours.

---

### Post by ventrical on 2013-03-07
> **zika said:**
> You've made me try weston and I'm writing this from Chromium in Weston... ;)


Ahhrrrrggg.. alrightee then. Just gotta try weston now. :)

---

### Post by Cheesemill on 2013-03-07
libwayland0 is a dependency of libgtk-3-0

I can't remember exactly when this happened but I recall having it on my system for quite some time now.
```
rob@raring:~$ apt-cache showpkg libwayland0
Package: libwayland0
Versions: 
1.0.5-0ubuntu1 (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages
                  MD5: 4dbd6bb3be80bfda96839d773add232a
 Description Language: en
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
                  MD5: 4dbd6bb3be80bfda96839d773add232a

1.0.0+git20121025.1f521a4f-0ubuntu0ricotz (/var/lib/apt/lists/ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_raring_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages
                  MD5: 4dbd6bb3be80bfda96839d773add232a
 Description Language: en
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
                  MD5: 4dbd6bb3be80bfda96839d773add232a


Reverse Depends: 
  libwayland0:i386,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libwayland0:i386,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  weston,libwayland0
  libwayland-dev,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libwayland0-dbg,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libegl1-mesa-drivers,libwayland0 1.0.2
  libegl1-mesa,libwayland0 1.0.2
  libegl1-mesa-drivers,libwayland0 1.0.2
  libegl1-mesa,libwayland0 1.0.2
  libwayland0:i386,libwayland0 1.0.5-0ubuntu1
  libwayland0:i386,libwayland0 1.0.5-0ubuntu1
  weston,libwayland0 1.0.2
  libwayland0-dbg,libwayland0 1.0.5-0ubuntu1
  libwayland-dev,libwayland0 1.0.5-0ubuntu1
  libgtk-3-0,libwayland0 1.0.2
  libegl1-mesa-drivers,libwayland0
  libegl1-mesa,libwayland0
Dependencies: 
1.0.5-0ubuntu1 - libc6 (2 2.14) libffi6 (2 3.0.4) multiarch-support (0 (null)) libwayland0:i386 (3 1.0.5-0ubuntu1) libwayland0:i386 (6 1.0.5-0ubuntu1) 
1.0.0+git20121025.1f521a4f-0ubuntu0ricotz - libc6 (2 2.14) libffi6 (2 3.0.4) multiarch-support (0 (null)) libwayland0:i386 (3 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz) libwayland0:i386 (6 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz) 
Provides: 
1.0.5-0ubuntu1 - 
1.0.0+git20121025.1f521a4f-0ubuntu0ricotz - 
Reverse Provides: 
rob@raring:~$ 


```

---

### Post by ventrical on 2013-03-07
> **zika said:**
> You've made me try weston and I'm writing this from Chromium in Weston... ;)


Writing to you through FF using weston compositor. I tried it through tty1 first and it locked up  but works through terminal on ubuntu-desktop.

Funny looking thing. :)

Edit:

It has big issues with Xorg current.

---

### Post by zika on 2013-03-07
> **ventrical said:**
> Writing to you through FF using weston compositor. I tried it through tty1 first and it locked up  but works through terminal on ubuntu-desktop.

Funny looking thing. :)

Edit:

It has big issues with Xorg current.
It is nicer to start it through startx(xinit)... That way You can see how fast it is, much of the stuff works...
I've looked into site that is in Your signature and I woud suggest to have```
sudo -i gedit /etc/apt/sources.list
```changed into```
gksu gedit /etc/apt/sources.list
```or at least```
sudo -H gedit /etc/apt/sources.list
```since usage od sudo for GUI is proven to be source of possible trouble... ;)

---

### Post by ventrical on 2013-03-07
> **zika said:**
> It is nicer to start it through startx(xinit)... That way You can see how fast it is, much of the stuff works...
I've looked into site that is in Your signature and I woud suggest to have```
sudo -i gedit /etc/apt/sources.list
```changed into```
gksu gedit /etc/apt/sources.list
```or at least```
sudo -H gedit /etc/apt/sources.list
```since usage od sudo for GUI is proven to be source of possible trouble... ;)

Done.

Thanks for the good pointers. ;)

---

### Post by ventrical on 2013-03-07
> **Cheesemill said:**
> libwayland0 is a dependency of libgtk-3-0

I can't remember exactly when this happened but I recall having it on my system for quite some time now.
```
rob@raring:~$ apt-cache showpkg libwayland0
Package: libwayland0
Versions: 
1.0.5-0ubuntu1 (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages
                  MD5: 4dbd6bb3be80bfda96839d773add232a
 Description Language: en
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
                  MD5: 4dbd6bb3be80bfda96839d773add232a

1.0.0+git20121025.1f521a4f-0ubuntu0ricotz (/var/lib/apt/lists/ppa.launchpad.net_xorg-edgers_ppa_ubuntu_dists_raring_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages
                  MD5: 4dbd6bb3be80bfda96839d773add232a
 Description Language: en
                 File: /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
                  MD5: 4dbd6bb3be80bfda96839d773add232a


Reverse Depends: 
  libwayland0:i386,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libwayland0:i386,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  weston,libwayland0
  libwayland-dev,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libwayland0-dbg,libwayland0 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz
  libegl1-mesa-drivers,libwayland0 1.0.2
  libegl1-mesa,libwayland0 1.0.2
  libegl1-mesa-drivers,libwayland0 1.0.2
  libegl1-mesa,libwayland0 1.0.2
  libwayland0:i386,libwayland0 1.0.5-0ubuntu1
  libwayland0:i386,libwayland0 1.0.5-0ubuntu1
  weston,libwayland0 1.0.2
  libwayland0-dbg,libwayland0 1.0.5-0ubuntu1
  libwayland-dev,libwayland0 1.0.5-0ubuntu1
  libgtk-3-0,libwayland0 1.0.2
  libegl1-mesa-drivers,libwayland0
  libegl1-mesa,libwayland0
Dependencies: 
1.0.5-0ubuntu1 - libc6 (2 2.14) libffi6 (2 3.0.4) multiarch-support (0 (null)) libwayland0:i386 (3 1.0.5-0ubuntu1) libwayland0:i386 (6 1.0.5-0ubuntu1) 
1.0.0+git20121025.1f521a4f-0ubuntu0ricotz - libc6 (2 2.14) libffi6 (2 3.0.4) multiarch-support (0 (null)) libwayland0:i386 (3 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz) libwayland0:i386 (6 1.0.0+git20121025.1f521a4f-0ubuntu0ricotz) 
Provides: 
1.0.5-0ubuntu1 - 
1.0.0+git20121025.1f521a4f-0ubuntu0ricotz - 
Reverse Provides: 
rob@raring:~$ 


```

Yes .. I have it on Quantal non Mir, non Weston .

---

### Post by grahammechanical on 2013-03-07
Just install 12.10 but could not find libwayland0 using Synaptic. Did not try the apt-cache showpkg until after I put in the MIR ppa. I see this

> Reverse Depends: 
  libegl1-mesa-drivers,libwayland0
  libegl1-mesa,libwayland0
  libegl1-mesa-drivers,libwayland0
  libegl1-mesa,libwayland0
  libwayland0:i386,libwayland0 0.95.0-0ubuntu1
  libwayland0:i386,libwayland0 0.95.0-0ubuntu1
  weston,libwayland0
  libwayland0-dbg,libwayland0 0.95.0-0ubuntu1
  libwayland-dev,libwayland0 0.95.0-0ubuntu1
  libegl1-mesa-drivers,libwayland0
  libegl1-mesa,libwayland0
Dependencies: 
0.95.0-0ubuntu1 - libc6 (2 2.14) libffi6 (2 3.0.4) multiarch-support (0 (null)) libwayland0:i386 (3 0.95.0-0ubuntu1) libwayland0:i386 (6 0.95.0-0ubuntu1) 
Provides: 
0.95.0-0ubuntu1 -

Now I have to work out what to do with this MIR ppa. I did fine this which I think is interesting.

> However, Wayland support could be added either by providing a  Wayland-specific frontend implementation for our display server or by  providing a client-side implementation of libwayland that ultimately  talks to Mir.

> **Roadmap**

 The full roadmap can be seen in the [client-1303-mir-converged]("https://blueprints.launchpad.net/ubuntu/+spec/client-1303-mir-converged") blueprint. Key milestones are: 

 
**May 2013**

 Finish  the first step towards integrating Unity Next with Mir and provide  enough facility to start iterating the actual shell development,  providing developers with a solid platform and designers with means for  rapid prototyping. 
 
**October 2013**

 Unity  Next & Mir window management are completely integrated with the  rest of the system to support an Ubuntu Phone product. For the  desktop/laptop form-factor, we want to fully replace X in user sessions  and provide a legacy mode that allows to run legacy X clients against an  on-demand rootless X server. A cascade of display servers/shells is  implemented, with the session-level instances talking to a global system  compositor instance, providing a flicker-free, tightly integrated and  beautiful UX. 
 
**April 2014**

 Complete  convergence across the form factors is achieved, with Mir serving as  the carrier across form factors, powering a seamless transition between  different use-cases and devices.

[https://wiki.ubuntu.com/MirSpec](https://wiki.ubuntu.com/MirSpec)

So, it looks like some of us will be kept amused for a while.

Update. Install Raring and this time I did not need any F6 options like I did a week ago and I ran apt-cache showpkg libwayland0 and the librarie is present even without the MIR ppa being activated. Isn't this fun!  :)

---

### Post by ventrical on 2013-03-07
@grahammechanical

A solid peice of research, as usual.

Thanks.

---

### Post by cole.mickens on 2013-03-07
> **zika said:**
> You've made me try weston and I'm writing this from Chromium in Weston... ;)

WHAT? Since when does Chromium support Wayland? I had *no* idea. Very exciting!

Also, it's almost surely because of this: [http://www.phoronix.com/scan.php?page=news_item&px=MTI3MDY](http://www.phoronix.com/scan.php?page=news_item&px=MTI3MDY)

Originally GTK+ was not going to ship in 13.04 with Wayland support. Since something else needs libwayland0 anyway, it was decided to include GTK with the Wayland backend enabled (during compilation, available at runtime if you want to run GTK apps in Wayland [assuming there isn't other Xlib crap]).

So anyway, that's probably why it is linked to all those (presumably GTK) apps.

edit: It seems I've missed a few posts, sorry, didn't see "Page 2". Also, yes, this is due to libgtk3 as I implied. This should NOT be the case in 12.10. Is libwayland0 even in 12.10? You probably got it from a ppa (xorg-edgers?)

edit2: No offense, but this really doesn't have anything to do with Mir yet. Wayland is a protocol, so if Mir wanted to implement it, it would likely pull libwayland0 as a dependency, but that's an issue for... a year or more from now when Mir is actually halfway usable. Then it could be extended in a few ways to support Wayland and thus Wayland-compatible-Mir-incompatible-apps (which is likely to be many, anything that doesn't use GTK/Qt, assuming that Canonical really manages to push Mir in that (and/or) get it merged upstream). At least, this is my understanding.

---

### Post by alphacrucis2 on 2013-03-08
I have it with the normal raring repos, no edgers ppa. The weston package is available but not installed here. According to synaptic the origin repo for libwayland0 is raring/main. Weston appears to be in universe.

---

### Post by cole.mickens on 2013-03-08
> **alphacrucis2 said:**
> I have it with the normal raring repos, no edgers ppa. The weston package is available but not installed here. According to synaptic the origin repo for libwayland0 is raring/main. Weston appears to be in universe.

> This should **NOT** be the case in **12.10**. Is libwayland0 even in 12.10? You probably got it from a ppa (xorg-edgers?)

I was referring to whoever is on Quantal and has libwayland0.

---

### Post by serdotlinecho on 2013-03-08
Hell!

```
~&#10095; sudo apt-get purge libwayland0 -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libept1.4.12 libgc1c3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  docbook-xml librarian0 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp libxml2-utils
The following packages will be REMOVED:
  account-plugin-aim* account-plugin-facebook* account-plugin-flickr* account-plugin-google*
  account-plugin-identica* account-plugin-jabber* account-plugin-salut* account-plugin-twitter*
  account-plugin-windows-live* account-plugin-yahoo* activity-log-manager-control-center* aisleriot*
  apport-gtk* apturl* bamfdaemon* baobab* brasero-cdrkit* compiz* compiz-gnome* dconf-tools* empathy* eog*
  evince* evolution-data-server* file-roller* gcalctool* gcr* geary* gedit* gir1.2-appindicator3-0.1*
  gir1.2-gdata-0.0* gir1.2-gnomebluetooth-1.0* gir1.2-goa-1.0* gir1.2-gtk-3.0* gir1.2-gtksource-3.0*
  gir1.2-peas-1.0* gir1.2-rb-3.0* gir1.2-totem-1.0* gir1.2-vte-2.90* gir1.2-webkit-3.0* gir1.2-wnck-3.0*
  gkbd-capplet* gnome-bluetooth* gnome-calculator* gnome-contacts* gnome-control-center*
  gnome-control-center-signon* gnome-control-center-unity* gnome-disk-utility* gnome-font-viewer*
  gnome-icon-theme* gnome-icon-theme-symbolic* gnome-keyring* gnome-mahjongg* gnome-mines* gnome-orca*
  gnome-power-manager* gnome-screensaver* gnome-screenshot* gnome-session* gnome-session-bin*
  gnome-session-canberra* gnome-settings-daemon* gnome-sudoku* gnome-system-log* gnome-system-monitor*
  gnome-terminal* gnome-user-guide* gnome-user-share* gnomine* gstreamer1.0-clutter* gtk3-engines-unico*
  gucharmap* gvfs-backends* hud* humanity-icon-theme* ibus* ibus-gtk3* ibus-pinyin* ibus-table*
  indicator-application* indicator-appmenu* indicator-bluetooth* indicator-datetime* indicator-messages*
  indicator-power* indicator-printers* indicator-session* indicator-sound* indicator-sync*
  landscape-client-ui-install* language-selector-gnome* libaccount-plugin-1.0-0* libappindicator3-1*
  libbamf3-1* libbrasero-media3-1* libcanberra-gtk3-0* libcanberra-gtk3-module* libclutter-1.0-0*
  libclutter-gst-2.0-0* libclutter-gtk-1.0-0* libcogl-pango0* libcogl-pango12* libcogl11* libcogl12*
  libebackend-1.2-5* libebook-1.2-14* libecal-1.2-15* libedata-book-1.2-15* libedata-cal-1.2-18*
  libedataserver-1.2-17* libegl1-mesa* libegl1-mesa-drivers* libevdocument3-4* libevview3-3* libfolks-eds25*
  libgail-3-0* libgcr-3-1* libgdata13* libgnome-bluetooth11* libgnome-control-center1* libgnome-desktop-3-4*
  libgnomekbd8* libgoa-1.0-0* libgrip0* libgtk-3-0* libgtk-3-bin* libgtkmm-3.0-1* libgtksourceview-3.0-0*
  libgtkspell-3-0* libgucharmap-2-90-7* libgweather-3-1* libido3-0.1-0* libindicator3-7*
  libnautilus-extension1a* libnm-gtk0* libpeas-1.0-0* librhythmbox-core6* libsyncdaemon-1.0-1* libtimezonemap1*
  libtotem0* libunique-3.0-0* libunity-core-6.0-5* libunity-misc4* libunity-webapps0* libvte-2.90-9*
  libwayland0* libwebkitgtk-3.0-0* libwnck-3-0* libyelp0* light-themes* lightdm-remote-session-freerdp*
  lightdm-remote-session-uccsconfigure* mcp-account-manager-uoa* mousetweaks* nautilus* nautilus-sendto*
  nautilus-sendto-empathy* nautilus-share* network-manager-gnome* network-manager-pptp-gnome* notify-osd*
  onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* policykit-1-gnome*
  python-aptdaemon.gtk3widgets* python-ubuntu-sso-client* python-ubuntuone-control-panel*
  python3-aptdaemon.gtk3widgets* seahorse* sessioninstaller* shotwell* simple-scan* software-properties-gtk*
  system-config-printer-gnome* telepathy-indicator* totem* totem-mozilla* totem-plugins* transmission-gtk*
  ubuntu-artwork* ubuntu-docs* ubuntu-mono* ubuntu-release-upgrader-gtk* ubuntu-sso-client*
  ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-gnome* ubuntuone-control-panel*
  ubuntuone-control-panel-qt* unity* unity-asset-pool* unity-greeter* unity-lens-photos* unity-scope-gdocs*
  unity-scope-gdrive* unity-services* unity-webapps-common* unity-webapps-facebookmessenger*
  unity-webapps-googleplus* unity-webapps-launchpad* unity-webapps-service* unity-webapps-youtube*
  update-manager* update-notifier* usb-creator-gtk* vino* webaccounts-extension-common* xdg-user-dirs-gtk*
  xdiagnose* xul-ext-unity* xul-ext-webaccounts* xul-ext-websites-integration* yelp* zenity*
The following NEW packages will be installed:
  docbook-xml librarian0 rarian-compat sgml-data
0 upgraded, 4 newly installed, 217 to remove and 0 not upgraded.
Purg account-plugin-aim [3.6.3-0ubuntu4]
Purg account-plugin-facebook [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-flickr [0.10bzr13.02.27-0ubuntu1]
Purg unity-scope-gdocs [0.8daily12.12.05-0ubuntu1]
Purg unity-scope-gdrive [0.8daily12.12.05-0ubuntu1]
Purg account-plugin-google [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-identica [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-jabber [3.6.3-0ubuntu4]
Purg account-plugin-salut [3.6.3-0ubuntu4]
Purg account-plugin-twitter [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-windows-live [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-yahoo [3.6.3-0ubuntu4]
Purg activity-log-manager-control-center [0.9.4-0ubuntu6.1]
Purg aisleriot [1:3.4.1+really3.2.3.2-0ubuntu3]
Purg apport-gtk [2.9.1-0ubuntu1]
Purg nautilus-share [0.7.3-1ubuntu3]
Purg apturl [0.5.1ubuntu6]
Purg lightdm-remote-session-uccsconfigure [1.1-0ubuntu2]
Purg unity [6.12.0daily13.03.07-0ubuntu1]
Purg indicator-appmenu [13.01.0daily13.02.20-0ubuntu1]
Purg hud [13.04.0daily13.02.20-0ubuntu2]
Purg libbamf3-1 [0.4.0daily13.03.07-0ubuntu1]
Purg bamfdaemon [0.4.0daily13.03.07-0ubuntu1]
Purg baobab [3.6.4-0ubuntu1]
Purg brasero-cdrkit [3.6.1-0ubuntu2]
Purg compiz [1:0.9.9~daily13.03.06-0ubuntu1]
Purg compiz-gnome [1:0.9.9~daily13.03.06-0ubuntu1]
Purg dconf-tools [0.15.3-0ubuntu1]
Purg nautilus-sendto-empathy [3.6.3-0ubuntu4]
Purg mcp-account-manager-uoa [3.6.3-0ubuntu4]
Purg empathy [3.6.3-0ubuntu4]
Purg eog [3.6.2-0ubuntu1]
Purg evince [3.6.1-1ubuntu3]
Purg gnome-contacts [3.6.2-0ubuntu1]
Purg libfolks-eds25 [0.8.0-1]
Purg evolution-data-server [3.6.2-0ubuntu1]
Purg file-roller [3.6.3-1ubuntu3]
Purg gcalctool [1:3.7.90-0ubuntu1]
Purg seahorse [3.6.3-0ubuntu1]
Purg ubuntuone-control-panel-qt [4.1.91-0ubuntu1]
Purg ubuntu-sso-client-qt [4.1.91-0ubuntu1]
Purg ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg ubuntuone-client-gnome [4.1.91-0ubuntu1]
Purg libsyncdaemon-1.0-1 [4.1.91-0ubuntu1]
Purg ubuntuone-client [4.1.91-0ubuntu1]
Purg ubuntu-sso-client [4.1.91-0ubuntu1]
Purg python-ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg python-ubuntu-sso-client [4.1.91-0ubuntu1]
Purg gnome-keyring [3.6.3-0ubuntu1]
Purg gcr [3.6.2-0ubuntu1]
Purg geary [0.2.2-0ubuntu1]
Purg gedit [3.6.2-0ubuntu1]
Purg gir1.2-appindicator3-0.1 [12.10.1daily13.02.15-0ubuntu1]
Purg unity-lens-photos [0.9daily12.12.05-0ubuntu1]
Purg gir1.2-gdata-0.0 [0.13.2-2svn1]
Purg indicator-bluetooth [0.0.6daily13.02.19-0ubuntu1]
Purg gnome-user-share [3.0.4-0ubuntu1]
Purg gnome-bluetooth [3.6.1-0ubuntu2]
Purg gir1.2-gnomebluetooth-1.0 [3.6.1-0ubuntu2]
Purg gir1.2-goa-1.0 [3.6.2-1]
Purg xdiagnose [3.4.3]
Purg usb-creator-gtk [0.2.46.1]
Purg ubuntu-release-upgrader-gtk [1:0.192.5] [update-manager:i386 update-notifier:i386 ]
Purg update-manager [1:0.184] [update-notifier:i386 ]
Purg update-notifier [0.131]
Purg totem-plugins [3.6.3-0ubuntu3]
Purg software-properties-gtk [0.92.14.1]
Purg sessioninstaller [0.20+bzr134-0ubuntu4]
Purg language-selector-gnome [0.106]
Purg python3-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg landscape-client-ui-install [12.12-0ubuntu3]
Purg python-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg onboard [0.99.0~alpha1~tr1190-0ubuntu1]
Purg gnome-sudoku [1:3.7.4-0ubuntu1]
Purg gnome-orca [3.7.91-0ubuntu1]
Purg gir1.2-wnck-3.0 [3.4.5-0ubuntu1]
Purg gir1.2-webkit-3.0 [1.10.2-0ubuntu1]
Purg gir1.2-vte-2.90 [1:0.34.2-0ubuntu2]
Purg gir1.2-totem-1.0 [3.6.3-0ubuntu3]
Purg gir1.2-rb-3.0 [2.98-0ubuntu3]
Purg gir1.2-peas-1.0 [1.6.2-0ubuntu1]
Purg gir1.2-gtksource-3.0 [3.6.3-0ubuntu1]
Purg gir1.2-gtk-3.0 [3.6.4-0ubuntu6]
Purg indicator-power [12.10.6daily13.03.07-0ubuntu1]
Purg indicator-datetime [12.10.3daily13.03.07-0ubuntu1]
Purg gnome-control-center-unity [1.2daily13.02.15-0ubuntu1]
Purg xul-ext-webaccounts [0.4.5-0ubuntu4]
Purg webaccounts-extension-common [0.4.5-0ubuntu4]
Purg gnome-control-center-signon [0.1.2bzr12.12.05-0ubuntu1]
Purg gnome-control-center [1:3.6.3-0ubuntu13]
Purg gkbd-capplet [3.6.0-0ubuntu1]
Purg gnome-calculator [1:3.7.90-0ubuntu1]
Purg gnome-disk-utility [3.6.1-1ubuntu1]
Purg gnome-font-viewer [3.7.5-0ubuntu1]
Purg unity-asset-pool [0.8.24daily12.12.05-0ubuntu1]
Purg ubuntu-artwork [1:13.04daily13.03.05-0ubuntu1]
Purg light-themes [13.04daily13.03.05-0ubuntu1]
Purg ubuntu-mono [13.04daily13.03.05-0ubuntu1]
Purg totem-mozilla [3.6.3-0ubuntu3]
Purg totem [3.6.3-0ubuntu3]
Purg system-config-printer-gnome [1.3.11+20120807-0ubuntu14]
Purg simple-scan [3.6.0-2]
Purg network-manager-gnome [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg ibus-table [1.5.0.is.1.4.99.1-1ubuntu1]
Purg ibus-pinyin [1.4.0-1build1]
Purg ibus [1.4.2-0ubuntu1]
Purg gnome-screensaver [3.6.1-0ubuntu3]
Purg gnome-icon-theme-symbolic [3.6.2-0ubuntu1]
Purg gnome-icon-theme [3.6.2-0ubuntu1] [humanity-icon-theme:i386 ]
Purg humanity-icon-theme [0.6.2]
Purg gnome-mahjongg [1:3.7.90-0ubuntu1]
Purg gnomine [1:3.7.5-0ubuntu1]
Purg gnome-mines [1:3.7.5-0ubuntu1]
Purg gnome-power-manager [3.6.0-1]
Purg gnome-screenshot [3.6.1-0ubuntu1]
Purg gnome-session [3.6.2-0ubuntu3]
Purg gnome-session-bin [3.6.2-0ubuntu3]
Purg gnome-session-canberra [0.30-0ubuntu1]
Purg unity-greeter [13.04.1-0ubuntu2]
Purg indicator-session [12.10.5daily13.03.06-0ubuntu1]
Purg gnome-settings-daemon [3.6.4-0ubuntu6]
Purg gnome-system-log [3.6.1-0ubuntu1]
Purg gnome-system-monitor [3.7.90-0ubuntu1]
Purg gnome-terminal [3.6.1-0ubuntu4]
Purg gnome-user-guide [3.6.2-0ubuntu1]
Purg gstreamer1.0-clutter [2.0.2-0ubuntu1]
Purg gtk3-engines-unico [1.0.3daily12.12.12-0ubuntu1]
Purg gucharmap [1:3.6.1-0ubuntu1]
Purg gvfs-backends [1.15.4-0ubuntu1]
Purg ibus-gtk3 [1.4.2-0ubuntu1]
Purg indicator-application [12.10.1daily13.01.25-0ubuntu1]
Purg indicator-messages [12.10.6daily13.02.13-0ubuntu1]
Purg indicator-printers [0.1.7daily13.03.01-0ubuntu1]
Purg indicator-sound [12.10.2daily13.03.07-0ubuntu1]
Purg indicator-sync [12.10.5daily13.01.25-0ubuntu1]
Purg libaccount-plugin-1.0-0 [0.1.2bzr12.12.05-0ubuntu1]
Purg vino [3.6.2-0ubuntu2]
Purg transmission-gtk [2.77-0ubuntu1]
Purg libbrasero-media3-1 [3.6.1-0ubuntu2]
Purg libappindicator3-1 [12.10.1daily13.02.15-0ubuntu1]
Purg libcanberra-gtk3-module [0.30-0ubuntu1]
Purg libcanberra-gtk3-0 [0.30-0ubuntu1]
Purg libtotem0 [3.6.3-0ubuntu3]
Purg libclutter-gtk-1.0-0 [1.4.2-0ubuntu2]
Purg libclutter-gst-2.0-0 [2.0.2-0ubuntu1]
Purg libclutter-1.0-0 [1.12.2-0ubuntu3]
Purg libcogl-pango0 [1.12.2-0ubuntu1]
Purg libcogl-pango12 [1.13.4-0ubuntu1]
Purg libcogl11 [1.12.2-0ubuntu1]
Purg libcogl12 [1.13.4-0ubuntu1]
Purg libedata-cal-1.2-18 [3.6.2-0ubuntu1]
Purg libedata-book-1.2-15 [3.6.2-0ubuntu1]
Purg libebackend-1.2-5 [3.6.2-0ubuntu1]
Purg nautilus-sendto [3.6.1-0ubuntu1]
Purg libebook-1.2-14 [3.6.2-0ubuntu1]
Purg libecal-1.2-15 [3.6.2-0ubuntu1]
Purg libedataserver-1.2-17 [3.6.2-0ubuntu1]
Purg libegl1-mesa-drivers [9.0.2-0ubuntu1]
Purg libegl1-mesa [9.0.2-0ubuntu1]
Purg libevview3-3 [3.6.1-1ubuntu3]
Purg libevdocument3-4 [3.6.1-1ubuntu3]
Purg nautilus [1:3.6.3-0ubuntu6]
Purg lightdm-remote-session-freerdp [1.0-0ubuntu2]
Purg zenity [3.6.0-0ubuntu1]
Purg ubuntu-docs [12.10.3]
Purg yelp [3.6.2-0ubuntu1]
Purg shotwell [0.13.1-0ubuntu3]
Purg libyelp0 [3.6.2-0ubuntu1]
Purg librhythmbox-core6 [2.98-0ubuntu3]
Purg libgdata13 [0.13.2-2svn1]
Purg libgoa-1.0-0 [3.6.2-1]
Purg libwebkitgtk-3.0-0 [1.10.2-0ubuntu1]
Purg libgail-3-0 [3.6.4-0ubuntu6]
Purg libgcr-3-1 [3.6.2-0ubuntu1]
Purg libgnome-bluetooth11 [3.6.1-0ubuntu2]
Purg libgnome-control-center1 [1:3.6.3-0ubuntu13]
Purg libgnome-desktop-3-4 [3.6.2-0ubuntu8]
Purg libgnomekbd8 [3.6.0-0ubuntu1]
Purg libgrip0 [0.3.6daily13.02.26-0ubuntu1]
Purg xdg-user-dirs-gtk [0.10-0ubuntu1]
Purg unity-webapps-youtube [2.4.10.1]
Purg unity-webapps-launchpad [2.2]
Purg unity-webapps-googleplus [2.2]
Purg unity-webapps-facebookmessenger [2.2]
Purg unity-webapps-common [2.4.13-0ubuntu1]
Purg xul-ext-unity [2.4.4bzr13.01.29-0ubuntu1]
Purg xul-ext-websites-integration [2.3.5.1-0ubuntu1]
Purg unity-webapps-service [2.4.4~daily13.03.06-0ubuntu1] [libunity-webapps0:i386 ]
Purg libunity-webapps0 [2.4.4~daily13.03.06-0ubuntu1]
Purg libunity-core-6.0-5 [6.12.0daily13.03.07-0ubuntu1]
Purg unity-services [6.12.0daily13.03.07-0ubuntu1]
Purg telepathy-indicator [0.3.1daily13.03.01-0ubuntu1]
Purg libnm-gtk0 [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg policykit-1-gnome [0.105-1ubuntu4]
Purg overlay-scrollbar-gtk3 [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar:i386 ]
Purg overlay-scrollbar [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar-gtk2:i386 ]
Purg overlay-scrollbar-gtk2 [0.2.16+r359daily13.02.06-0ubuntu1]
Purg notify-osd [0.9.35daily12.11.28-0ubuntu1]
Purg network-manager-pptp-gnome [0.9.6.0-0ubuntu2]
Purg mousetweaks [3.6.0-0ubuntu2]
Purg libwnck-3-0 [3.4.5-0ubuntu1]
Purg libvte-2.90-9 [1:0.34.2-0ubuntu2]
Purg libunity-misc4 [4.0.5daily13.02.26-0ubuntu1]
Purg libunique-3.0-0 [3.0.2-1build1]
Purg libtimezonemap1 [0.3.2build1]
Purg libpeas-1.0-0 [1.6.2-0ubuntu1]
Purg libnautilus-extension1a [1:3.6.3-0ubuntu6]
Purg libindicator3-7 [12.10.2daily13.02.25-0ubuntu1]
Purg libido3-0.1-0 [12.10.3daily13.03.01-0ubuntu1]
Purg libgweather-3-1 [3.6.2-0ubuntu1]
Purg libgucharmap-2-90-7 [1:3.6.1-0ubuntu1]
Purg libgtkspell-3-0 [3.0.0~hg20110814-1build1]
Purg libgtksourceview-3.0-0 [3.6.3-0ubuntu1]
Purg libgtkmm-3.0-1 [3.6.0-0ubuntu1]
Purg libgtk-3-bin [3.6.4-0ubuntu6]
Purg libgtk-3-0 [3.6.4-0ubuntu6]
Purg libwayland0 [1.0.5-0ubuntu1]
Inst sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Inst docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Inst librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Inst rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Conf sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Conf docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Conf librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Conf rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [i386])
```

---

### Post by zika on 2013-03-08
> **cole.mickens said:**
> I was referring to whoever is on Quantal and has libwayland0.This is: Ubuntu +1 (Raring Ringtail) place... So we have RR not QQ on our machines... ;)

---

### Post by zika on 2013-03-08
> **serdotlinecho said:**
> Hell!

```
~&#10095; sudo apt-get purge libwayland0 -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libept1.4.12 libgc1c3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  docbook-xml librarian0 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp libxml2-utils
The following packages will be REMOVED:
  account-plugin-aim* account-plugin-facebook* account-plugin-flickr* account-plugin-google*
  account-plugin-identica* account-plugin-jabber* account-plugin-salut* account-plugin-twitter*
  account-plugin-windows-live* account-plugin-yahoo* activity-log-manager-control-center* aisleriot*
  apport-gtk* apturl* bamfdaemon* baobab* brasero-cdrkit* compiz* compiz-gnome* dconf-tools* empathy* eog*
  evince* evolution-data-server* file-roller* gcalctool* gcr* geary* gedit* gir1.2-appindicator3-0.1*
  gir1.2-gdata-0.0* gir1.2-gnomebluetooth-1.0* gir1.2-goa-1.0* gir1.2-gtk-3.0* gir1.2-gtksource-3.0*
  gir1.2-peas-1.0* gir1.2-rb-3.0* gir1.2-totem-1.0* gir1.2-vte-2.90* gir1.2-webkit-3.0* gir1.2-wnck-3.0*
  gkbd-capplet* gnome-bluetooth* gnome-calculator* gnome-contacts* gnome-control-center*
  gnome-control-center-signon* gnome-control-center-unity* gnome-disk-utility* gnome-font-viewer*
  gnome-icon-theme* gnome-icon-theme-symbolic* gnome-keyring* gnome-mahjongg* gnome-mines* gnome-orca*
  gnome-power-manager* gnome-screensaver* gnome-screenshot* gnome-session* gnome-session-bin*
  gnome-session-canberra* gnome-settings-daemon* gnome-sudoku* gnome-system-log* gnome-system-monitor*
  gnome-terminal* gnome-user-guide* gnome-user-share* gnomine* gstreamer1.0-clutter* gtk3-engines-unico*
  gucharmap* gvfs-backends* hud* humanity-icon-theme* ibus* ibus-gtk3* ibus-pinyin* ibus-table*
  indicator-application* indicator-appmenu* indicator-bluetooth* indicator-datetime* indicator-messages*
  indicator-power* indicator-printers* indicator-session* indicator-sound* indicator-sync*
  landscape-client-ui-install* language-selector-gnome* libaccount-plugin-1.0-0* libappindicator3-1*
  libbamf3-1* libbrasero-media3-1* libcanberra-gtk3-0* libcanberra-gtk3-module* libclutter-1.0-0*
  libclutter-gst-2.0-0* libclutter-gtk-1.0-0* libcogl-pango0* libcogl-pango12* libcogl11* libcogl12*
  libebackend-1.2-5* libebook-1.2-14* libecal-1.2-15* libedata-book-1.2-15* libedata-cal-1.2-18*
  libedataserver-1.2-17* libegl1-mesa* libegl1-mesa-drivers* libevdocument3-4* libevview3-3* libfolks-eds25*
  libgail-3-0* libgcr-3-1* libgdata13* libgnome-bluetooth11* libgnome-control-center1* libgnome-desktop-3-4*
  libgnomekbd8* libgoa-1.0-0* libgrip0* libgtk-3-0* libgtk-3-bin* libgtkmm-3.0-1* libgtksourceview-3.0-0*
  libgtkspell-3-0* libgucharmap-2-90-7* libgweather-3-1* libido3-0.1-0* libindicator3-7*
  libnautilus-extension1a* libnm-gtk0* libpeas-1.0-0* librhythmbox-core6* libsyncdaemon-1.0-1* libtimezonemap1*
  libtotem0* libunique-3.0-0* libunity-core-6.0-5* libunity-misc4* libunity-webapps0* libvte-2.90-9*
  libwayland0* libwebkitgtk-3.0-0* libwnck-3-0* libyelp0* light-themes* lightdm-remote-session-freerdp*
  lightdm-remote-session-uccsconfigure* mcp-account-manager-uoa* mousetweaks* nautilus* nautilus-sendto*
  nautilus-sendto-empathy* nautilus-share* network-manager-gnome* network-manager-pptp-gnome* notify-osd*
  onboard* overlay-scrollbar* overlay-scrollbar-gtk2* overlay-scrollbar-gtk3* policykit-1-gnome*
  python-aptdaemon.gtk3widgets* python-ubuntu-sso-client* python-ubuntuone-control-panel*
  python3-aptdaemon.gtk3widgets* seahorse* sessioninstaller* shotwell* simple-scan* software-properties-gtk*
  system-config-printer-gnome* telepathy-indicator* totem* totem-mozilla* totem-plugins* transmission-gtk*
  ubuntu-artwork* ubuntu-docs* ubuntu-mono* ubuntu-release-upgrader-gtk* ubuntu-sso-client*
  ubuntu-sso-client-qt* ubuntuone-client* ubuntuone-client-gnome* ubuntuone-control-panel*
  ubuntuone-control-panel-qt* unity* unity-asset-pool* unity-greeter* unity-lens-photos* unity-scope-gdocs*
  unity-scope-gdrive* unity-services* unity-webapps-common* unity-webapps-facebookmessenger*
  unity-webapps-googleplus* unity-webapps-launchpad* unity-webapps-service* unity-webapps-youtube*
  update-manager* update-notifier* usb-creator-gtk* vino* webaccounts-extension-common* xdg-user-dirs-gtk*
  xdiagnose* xul-ext-unity* xul-ext-webaccounts* xul-ext-websites-integration* yelp* zenity*
The following NEW packages will be installed:
  docbook-xml librarian0 rarian-compat sgml-data
0 upgraded, 4 newly installed, 217 to remove and 0 not upgraded.
Purg account-plugin-aim [3.6.3-0ubuntu4]
Purg account-plugin-facebook [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-flickr [0.10bzr13.02.27-0ubuntu1]
Purg unity-scope-gdocs [0.8daily12.12.05-0ubuntu1]
Purg unity-scope-gdrive [0.8daily12.12.05-0ubuntu1]
Purg account-plugin-google [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-identica [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-jabber [3.6.3-0ubuntu4]
Purg account-plugin-salut [3.6.3-0ubuntu4]
Purg account-plugin-twitter [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-windows-live [0.10bzr13.02.27-0ubuntu1]
Purg account-plugin-yahoo [3.6.3-0ubuntu4]
Purg activity-log-manager-control-center [0.9.4-0ubuntu6.1]
Purg aisleriot [1:3.4.1+really3.2.3.2-0ubuntu3]
Purg apport-gtk [2.9.1-0ubuntu1]
Purg nautilus-share [0.7.3-1ubuntu3]
Purg apturl [0.5.1ubuntu6]
Purg lightdm-remote-session-uccsconfigure [1.1-0ubuntu2]
Purg unity [6.12.0daily13.03.07-0ubuntu1]
Purg indicator-appmenu [13.01.0daily13.02.20-0ubuntu1]
Purg hud [13.04.0daily13.02.20-0ubuntu2]
Purg libbamf3-1 [0.4.0daily13.03.07-0ubuntu1]
Purg bamfdaemon [0.4.0daily13.03.07-0ubuntu1]
Purg baobab [3.6.4-0ubuntu1]
Purg brasero-cdrkit [3.6.1-0ubuntu2]
Purg compiz [1:0.9.9~daily13.03.06-0ubuntu1]
Purg compiz-gnome [1:0.9.9~daily13.03.06-0ubuntu1]
Purg dconf-tools [0.15.3-0ubuntu1]
Purg nautilus-sendto-empathy [3.6.3-0ubuntu4]
Purg mcp-account-manager-uoa [3.6.3-0ubuntu4]
Purg empathy [3.6.3-0ubuntu4]
Purg eog [3.6.2-0ubuntu1]
Purg evince [3.6.1-1ubuntu3]
Purg gnome-contacts [3.6.2-0ubuntu1]
Purg libfolks-eds25 [0.8.0-1]
Purg evolution-data-server [3.6.2-0ubuntu1]
Purg file-roller [3.6.3-1ubuntu3]
Purg gcalctool [1:3.7.90-0ubuntu1]
Purg seahorse [3.6.3-0ubuntu1]
Purg ubuntuone-control-panel-qt [4.1.91-0ubuntu1]
Purg ubuntu-sso-client-qt [4.1.91-0ubuntu1]
Purg ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg ubuntuone-client-gnome [4.1.91-0ubuntu1]
Purg libsyncdaemon-1.0-1 [4.1.91-0ubuntu1]
Purg ubuntuone-client [4.1.91-0ubuntu1]
Purg ubuntu-sso-client [4.1.91-0ubuntu1]
Purg python-ubuntuone-control-panel [4.1.91-0ubuntu1]
Purg python-ubuntu-sso-client [4.1.91-0ubuntu1]
Purg gnome-keyring [3.6.3-0ubuntu1]
Purg gcr [3.6.2-0ubuntu1]
Purg geary [0.2.2-0ubuntu1]
Purg gedit [3.6.2-0ubuntu1]
Purg gir1.2-appindicator3-0.1 [12.10.1daily13.02.15-0ubuntu1]
Purg unity-lens-photos [0.9daily12.12.05-0ubuntu1]
Purg gir1.2-gdata-0.0 [0.13.2-2svn1]
Purg indicator-bluetooth [0.0.6daily13.02.19-0ubuntu1]
Purg gnome-user-share [3.0.4-0ubuntu1]
Purg gnome-bluetooth [3.6.1-0ubuntu2]
Purg gir1.2-gnomebluetooth-1.0 [3.6.1-0ubuntu2]
Purg gir1.2-goa-1.0 [3.6.2-1]
Purg xdiagnose [3.4.3]
Purg usb-creator-gtk [0.2.46.1]
Purg ubuntu-release-upgrader-gtk [1:0.192.5] [update-manager:i386 update-notifier:i386 ]
Purg update-manager [1:0.184] [update-notifier:i386 ]
Purg update-notifier [0.131]
Purg totem-plugins [3.6.3-0ubuntu3]
Purg software-properties-gtk [0.92.14.1]
Purg sessioninstaller [0.20+bzr134-0ubuntu4]
Purg language-selector-gnome [0.106]
Purg python3-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg landscape-client-ui-install [12.12-0ubuntu3]
Purg python-aptdaemon.gtk3widgets [0.45+bzr883-0ubuntu1]
Purg onboard [0.99.0~alpha1~tr1190-0ubuntu1]
Purg gnome-sudoku [1:3.7.4-0ubuntu1]
Purg gnome-orca [3.7.91-0ubuntu1]
Purg gir1.2-wnck-3.0 [3.4.5-0ubuntu1]
Purg gir1.2-webkit-3.0 [1.10.2-0ubuntu1]
Purg gir1.2-vte-2.90 [1:0.34.2-0ubuntu2]
Purg gir1.2-totem-1.0 [3.6.3-0ubuntu3]
Purg gir1.2-rb-3.0 [2.98-0ubuntu3]
Purg gir1.2-peas-1.0 [1.6.2-0ubuntu1]
Purg gir1.2-gtksource-3.0 [3.6.3-0ubuntu1]
Purg gir1.2-gtk-3.0 [3.6.4-0ubuntu6]
Purg indicator-power [12.10.6daily13.03.07-0ubuntu1]
Purg indicator-datetime [12.10.3daily13.03.07-0ubuntu1]
Purg gnome-control-center-unity [1.2daily13.02.15-0ubuntu1]
Purg xul-ext-webaccounts [0.4.5-0ubuntu4]
Purg webaccounts-extension-common [0.4.5-0ubuntu4]
Purg gnome-control-center-signon [0.1.2bzr12.12.05-0ubuntu1]
Purg gnome-control-center [1:3.6.3-0ubuntu13]
Purg gkbd-capplet [3.6.0-0ubuntu1]
Purg gnome-calculator [1:3.7.90-0ubuntu1]
Purg gnome-disk-utility [3.6.1-1ubuntu1]
Purg gnome-font-viewer [3.7.5-0ubuntu1]
Purg unity-asset-pool [0.8.24daily12.12.05-0ubuntu1]
Purg ubuntu-artwork [1:13.04daily13.03.05-0ubuntu1]
Purg light-themes [13.04daily13.03.05-0ubuntu1]
Purg ubuntu-mono [13.04daily13.03.05-0ubuntu1]
Purg totem-mozilla [3.6.3-0ubuntu3]
Purg totem [3.6.3-0ubuntu3]
Purg system-config-printer-gnome [1.3.11+20120807-0ubuntu14]
Purg simple-scan [3.6.0-2]
Purg network-manager-gnome [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg ibus-table [1.5.0.is.1.4.99.1-1ubuntu1]
Purg ibus-pinyin [1.4.0-1build1]
Purg ibus [1.4.2-0ubuntu1]
Purg gnome-screensaver [3.6.1-0ubuntu3]
Purg gnome-icon-theme-symbolic [3.6.2-0ubuntu1]
Purg gnome-icon-theme [3.6.2-0ubuntu1] [humanity-icon-theme:i386 ]
Purg humanity-icon-theme [0.6.2]
Purg gnome-mahjongg [1:3.7.90-0ubuntu1]
Purg gnomine [1:3.7.5-0ubuntu1]
Purg gnome-mines [1:3.7.5-0ubuntu1]
Purg gnome-power-manager [3.6.0-1]
Purg gnome-screenshot [3.6.1-0ubuntu1]
Purg gnome-session [3.6.2-0ubuntu3]
Purg gnome-session-bin [3.6.2-0ubuntu3]
Purg gnome-session-canberra [0.30-0ubuntu1]
Purg unity-greeter [13.04.1-0ubuntu2]
Purg indicator-session [12.10.5daily13.03.06-0ubuntu1]
Purg gnome-settings-daemon [3.6.4-0ubuntu6]
Purg gnome-system-log [3.6.1-0ubuntu1]
Purg gnome-system-monitor [3.7.90-0ubuntu1]
Purg gnome-terminal [3.6.1-0ubuntu4]
Purg gnome-user-guide [3.6.2-0ubuntu1]
Purg gstreamer1.0-clutter [2.0.2-0ubuntu1]
Purg gtk3-engines-unico [1.0.3daily12.12.12-0ubuntu1]
Purg gucharmap [1:3.6.1-0ubuntu1]
Purg gvfs-backends [1.15.4-0ubuntu1]
Purg ibus-gtk3 [1.4.2-0ubuntu1]
Purg indicator-application [12.10.1daily13.01.25-0ubuntu1]
Purg indicator-messages [12.10.6daily13.02.13-0ubuntu1]
Purg indicator-printers [0.1.7daily13.03.01-0ubuntu1]
Purg indicator-sound [12.10.2daily13.03.07-0ubuntu1]
Purg indicator-sync [12.10.5daily13.01.25-0ubuntu1]
Purg libaccount-plugin-1.0-0 [0.1.2bzr12.12.05-0ubuntu1]
Purg vino [3.6.2-0ubuntu2]
Purg transmission-gtk [2.77-0ubuntu1]
Purg libbrasero-media3-1 [3.6.1-0ubuntu2]
Purg libappindicator3-1 [12.10.1daily13.02.15-0ubuntu1]
Purg libcanberra-gtk3-module [0.30-0ubuntu1]
Purg libcanberra-gtk3-0 [0.30-0ubuntu1]
Purg libtotem0 [3.6.3-0ubuntu3]
Purg libclutter-gtk-1.0-0 [1.4.2-0ubuntu2]
Purg libclutter-gst-2.0-0 [2.0.2-0ubuntu1]
Purg libclutter-1.0-0 [1.12.2-0ubuntu3]
Purg libcogl-pango0 [1.12.2-0ubuntu1]
Purg libcogl-pango12 [1.13.4-0ubuntu1]
Purg libcogl11 [1.12.2-0ubuntu1]
Purg libcogl12 [1.13.4-0ubuntu1]
Purg libedata-cal-1.2-18 [3.6.2-0ubuntu1]
Purg libedata-book-1.2-15 [3.6.2-0ubuntu1]
Purg libebackend-1.2-5 [3.6.2-0ubuntu1]
Purg nautilus-sendto [3.6.1-0ubuntu1]
Purg libebook-1.2-14 [3.6.2-0ubuntu1]
Purg libecal-1.2-15 [3.6.2-0ubuntu1]
Purg libedataserver-1.2-17 [3.6.2-0ubuntu1]
Purg libegl1-mesa-drivers [9.0.2-0ubuntu1]
Purg libegl1-mesa [9.0.2-0ubuntu1]
Purg libevview3-3 [3.6.1-1ubuntu3]
Purg libevdocument3-4 [3.6.1-1ubuntu3]
Purg nautilus [1:3.6.3-0ubuntu6]
Purg lightdm-remote-session-freerdp [1.0-0ubuntu2]
Purg zenity [3.6.0-0ubuntu1]
Purg ubuntu-docs [12.10.3]
Purg yelp [3.6.2-0ubuntu1]
Purg shotwell [0.13.1-0ubuntu3]
Purg libyelp0 [3.6.2-0ubuntu1]
Purg librhythmbox-core6 [2.98-0ubuntu3]
Purg libgdata13 [0.13.2-2svn1]
Purg libgoa-1.0-0 [3.6.2-1]
Purg libwebkitgtk-3.0-0 [1.10.2-0ubuntu1]
Purg libgail-3-0 [3.6.4-0ubuntu6]
Purg libgcr-3-1 [3.6.2-0ubuntu1]
Purg libgnome-bluetooth11 [3.6.1-0ubuntu2]
Purg libgnome-control-center1 [1:3.6.3-0ubuntu13]
Purg libgnome-desktop-3-4 [3.6.2-0ubuntu8]
Purg libgnomekbd8 [3.6.0-0ubuntu1]
Purg libgrip0 [0.3.6daily13.02.26-0ubuntu1]
Purg xdg-user-dirs-gtk [0.10-0ubuntu1]
Purg unity-webapps-youtube [2.4.10.1]
Purg unity-webapps-launchpad [2.2]
Purg unity-webapps-googleplus [2.2]
Purg unity-webapps-facebookmessenger [2.2]
Purg unity-webapps-common [2.4.13-0ubuntu1]
Purg xul-ext-unity [2.4.4bzr13.01.29-0ubuntu1]
Purg xul-ext-websites-integration [2.3.5.1-0ubuntu1]
Purg unity-webapps-service [2.4.4~daily13.03.06-0ubuntu1] [libunity-webapps0:i386 ]
Purg libunity-webapps0 [2.4.4~daily13.03.06-0ubuntu1]
Purg libunity-core-6.0-5 [6.12.0daily13.03.07-0ubuntu1]
Purg unity-services [6.12.0daily13.03.07-0ubuntu1]
Purg telepathy-indicator [0.3.1daily13.03.01-0ubuntu1]
Purg libnm-gtk0 [0.9.7.995+git201301311844.0376019-0ubuntu3]
Purg policykit-1-gnome [0.105-1ubuntu4]
Purg overlay-scrollbar-gtk3 [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar:i386 ]
Purg overlay-scrollbar [0.2.16+r359daily13.02.06-0ubuntu1] [overlay-scrollbar-gtk2:i386 ]
Purg overlay-scrollbar-gtk2 [0.2.16+r359daily13.02.06-0ubuntu1]
Purg notify-osd [0.9.35daily12.11.28-0ubuntu1]
Purg network-manager-pptp-gnome [0.9.6.0-0ubuntu2]
Purg mousetweaks [3.6.0-0ubuntu2]
Purg libwnck-3-0 [3.4.5-0ubuntu1]
Purg libvte-2.90-9 [1:0.34.2-0ubuntu2]
Purg libunity-misc4 [4.0.5daily13.02.26-0ubuntu1]
Purg libunique-3.0-0 [3.0.2-1build1]
Purg libtimezonemap1 [0.3.2build1]
Purg libpeas-1.0-0 [1.6.2-0ubuntu1]
Purg libnautilus-extension1a [1:3.6.3-0ubuntu6]
Purg libindicator3-7 [12.10.2daily13.02.25-0ubuntu1]
Purg libido3-0.1-0 [12.10.3daily13.03.01-0ubuntu1]
Purg libgweather-3-1 [3.6.2-0ubuntu1]
Purg libgucharmap-2-90-7 [1:3.6.1-0ubuntu1]
Purg libgtkspell-3-0 [3.0.0~hg20110814-1build1]
Purg libgtksourceview-3.0-0 [3.6.3-0ubuntu1]
Purg libgtkmm-3.0-1 [3.6.0-0ubuntu1]
Purg libgtk-3-bin [3.6.4-0ubuntu6]
Purg libgtk-3-0 [3.6.4-0ubuntu6]
Purg libwayland0 [1.0.5-0ubuntu1]
Inst sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Inst docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Inst librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Inst rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Conf sgml-data (2.0.8 Ubuntu:13.04/raring [all])
Conf docbook-xml (4.5-7.1 Ubuntu:13.04/raring [all])
Conf librarian0 (0.8.1-5build1 Ubuntu:13.04/raring [i386])
Conf rarian-compat (0.8.1-5build1 Ubuntu:13.04/raring [i386])
```
[http://ubuntuforums.org/showthread.php?t=2123163&p=12545964#post12545964](http://ubuntuforums.org/showthread.php?t=2123163&p=12545964#post12545964)
Going for another spin...? ;)

---

### Post by cole.mickens on 2013-03-08
Scroll up six+ posts... someone talking about having it on Quantal. (it was just a small sidenote in my original post anyway :P)

I already explained why it's there and why purging it will remove everything.... (or tried to :P)

---

### Post by zika on 2013-03-08
> **cole.mickens said:**
> Scroll up four posts... someone talking about having it on Quantal.

I already explained why it's there and why purging it will remove everything.... (or tried to :P)[img]http://dingo.care2.com/photos/3/3049a.gif[/img]

---

### Post by alphacrucis2 on 2013-03-08
> **cole.mickens said:**
> Scroll up six+ posts... someone talking about having it on Quantal. (it was just a small sidenote in my original post anyway :P)

I already explained why it's there and why purging it will remove everything.... (or tried to :P)

Yeah sorry. I missed that.

---

