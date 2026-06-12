---
title: "Install a package on Ubuntu-Emulator"
date: 2015-04-20
forum: Ubuntu Phone and Tablet
---

### Post by enricobe on 2015-04-20
Hello,
I'm not sure that this is the right section, but I think it is.

I'm testing Ubuntu Touch on my PC via ubuntu-emulator. It works fine but I can't install [PodBird]("https://uappexplorer.com/app/com.mikeasoft.podbird"). This app don't appear if I search on Ubuntu's App Store and I really can't find how to install it on the emulator. 

I can't use the "Installation Instruction" [Here]("http://nik90.com/podbird-v0-6-call-for-testing/") because it says "Device offline"

Anyone has suggestions?

---

### Post by michael-sheldon on 2015-04-20
We don't currently build fat click packages for Podbird (i.e. packages that include both arm and x86 binaries), and because the emulator is x86 based and the podbird packages in the store are only arm based they don't show up. However we've just created an experimental PPA for using Podbird directly on the desktop which you can try out here: [https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa](https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa) 

Hope that helps :)

---

### Post by enricobe on 2015-04-20
> **michael-sheldon said:**
> We don't currently build fat click packages for Podbird (i.e. packages that include both arm and x86 binaries), and because the emulator is x86 based and the podbird packages in the store are only arm based they don't show up. However we've just created an experimental PPA for using Podbird directly on the desktop which you can try out here: [https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa](https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa) 

Hope that helps :)
Thank you very much for your explanation Michael! :) I'll try to install Podbird on my Desktop asap ;)

---

### Post by enricobe on 2015-04-21
> **michael-sheldon said:**
> We don't currently build fat click packages for Podbird (i.e. packages that include both arm and x86 binaries), and because the emulator is x86 based and the podbird packages in the store are only arm based they don't show up. However we've just created an experimental PPA for using Podbird directly on the desktop which you can try out here: [https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa](https://launchpad.net/~podbird-devs/+archive/ubuntu/ppa) 

Hope that helps :)

Hi again Michael. 
I've installed Podbrid with your PPA, but it didn't work.
Here the dependecies (I have Xubuntu 15.04) :
```

enrico@enrico-linux:~$ sudo apt-get install podbird
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti saranno inoltre installati:
  hud libboost-log1.55.0 libboost-program-options1.55.0 libcolumbus1
  libcolumbus1-common libdbusmenu-qt5 libgflags2 libgoogle-glog0
  libgsettings-qt1 libhud2 libpocketsphinx1 libqgsttools-p1 libqt5feedback5
  libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5organizer5 libsphinxbase1
  libubuntu-download-manager-client0 libubuntu-download-manager-common0
  libudm-common0 libudm-priv-common0 libunity-action-qt1 libunityvoice1
  libunwind8 qml-module-qtfeedback qml-module-qtgraphicaleffects
  qml-module-qtmultimedia qml-module-qtquick-layouts
  qml-module-qtquick-window2 qml-module-qtquick2 qmlscene
  qtdeclarative5-gsettings1.0 qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-download-manager0.1
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en suru-icon-theme
  ubuntu-download-manager ubuntu-mobile-icons ubuntu-ui-toolkit-theme
  unity-voice-service
I seguenti pacchetti NUOVI saranno installati:
  hud libboost-log1.55.0 libboost-program-options1.55.0 libcolumbus1
  libcolumbus1-common libdbusmenu-qt5 libgflags2 libgoogle-glog0
  libgsettings-qt1 libhud2 libpocketsphinx1 libqgsttools-p1 libqt5feedback5
  libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediaquick-p5
  libqt5multimediawidgets5 libqt5organizer5 libsphinxbase1
  libubuntu-download-manager-client0 libubuntu-download-manager-common0
  libudm-common0 libudm-priv-common0 libunity-action-qt1 libunityvoice1
  libunwind8 podbird qml-module-qtfeedback qml-module-qtgraphicaleffects
  qml-module-qtmultimedia qml-module-qtquick-layouts
  qml-module-qtquick-window2 qml-module-qtquick2 qmlscene
  qtdeclarative5-gsettings1.0 qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-download-manager0.1
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en suru-icon-theme
  ubuntu-download-manager ubuntu-mobile-icons ubuntu-ui-toolkit-theme
  unity-voice-service
0 aggiornati, 47 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 44,4 MB di archivi.
Dopo quest'operazione, verranno occupati 95,8 MB di spazio su disco.

```

As it is an experimental PPA this could be useful 

 The command "podbird" doesn't exists, but I've found that "qmlscene $@ /usr/share/podbird/qml/podbird/podbird.qml" should be the right command. 

Starting PodBird from the menu it does nothing. When I start that command from the terminal I get:
```

enrico@enrico-linux:~$ qmlscene $@ /usr/share/podbird/qml/podbird/podbird.qml
file:///usr/share/podbird/qml/podbird/podbird.qml:26 module "QtQuick.LocalStorage" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:23 module "Ubuntu.Connectivity" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:24 module "Qt.labs.settings" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:21 module "UserMetrics" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:26 module "QtQuick.LocalStorage" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:23 module "Ubuntu.Connectivity" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:24 module "Qt.labs.settings" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:21 module "UserMetrics" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:26 module "QtQuick.LocalStorage" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:23 module "Ubuntu.Connectivity" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:24 module "Qt.labs.settings" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:21 module "UserMetrics" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:26 module "QtQuick.LocalStorage" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:23 module "Ubuntu.Connectivity" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:24 module "Qt.labs.settings" is not installed
file:///usr/share/podbird/qml/podbird/podbird.qml:21 module "UserMetrics" is not installed
enrico@enrico-linux:~$

```

So i've installed all the missin dependencies

```

sudo apt-get install libusermetrics*
sudo apt-get install qml-module-qtquick-localstorage
sudo apt-get install qml-module-qt-labs-settings
sudo apt-get install qml-module-ubuntu-connectivity


```


"sudo apt-get install qml-module-ubuntu-connectivity" has installed all these packages (200MB!)
```

I seguenti pacchetti saranno inoltre installati:
  account-plugin-tools account-plugin-ubuntuone accountsservice-ubuntu-schemas
  accountsservice-ubuntu-touch-schemas address-book-service apparmor-easyprof
  apparmor-easyprof-ubuntu click click-apparmor dbus-property-service
  dconf-cli evolution-data-server evolution-data-server-online-accounts
  folks-common gir1.2-accounts-1.0 gir1.2-click-0.4 gir1.2-gee-0.8
  gir1.2-json-1.0 gir1.2-signon-1.0 history-service indicator-bluetooth
  indicator-network indicator-power libaccounts-glib0 libaccounts-qt5-1
  libandroid-properties1 libboost-locale1.55.0 libboost-regex1.55.0
  libcapnp-0.4.0 libconnectivity-qt1 libcontent-hub0 libdbus-cpp4
  libebackend-1.2-7 libebook-1.2-14 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libfolks-eds25 libfolks25 libgdata-common libgdata19
  libgeocode-glib0 libgoa-1.0-0b libgoa-1.0-common libgweather-3-6
  libgweather-common libhardware2 libhistoryservice0 libhybris
  libhybris-common1 libhybris-utils libjsoncpp0 liblttng-ust-ctl2
  liblttng-ust0 libmedia1 libmediascanner-2.0-3 libmirplatform6 libmirserver30
  libmission-control-plugins0 libnet-cpp1 liboauth0 libofono-qt1
  libonline-accounts-client1 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libpay2 libpgm-5.1-0 libphonenumber6 libpoppler-qt5-1
  libprocess-cpp2 libqmenumodel0 libqofono-qt5-0 libqt5concurrent5
  libqt5contacts5 libqt5keychain0 libqt5location5 libqt5location5-plugins
  libqt5positioning5 libqt5positioning5-plugins libqt5quickparticles5
  libqt5script5 libqt5sensors5 libqt5systeminfo5 libqt5versit5
  libqt5versitorganizer5 libqt5websockets5 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsodium13
  libsystemsettings1 libtelepathy-qt5-0 libthumbnailer0 libtimezonemap-data
  libtimezonemap1 libtrust-store1 libu1db-qt5-3 libubuntu-app-launch2
  libubuntu-application-api2 libubuntu-location-service2
  libubuntu-platform-hardware-api2 libubuntuoneauth-2.0-0 libunity-api0
  libunity-scopes3 liburcu2 libwhoopsie-preferences0 libzeitgeist-2.0-0
  libzmq3 libzmqpp3 mediascanner2.0 mir-platform-graphics-mesa1 ofono
  packagekit-tools pay-service powerd python-zeitgeist python3-apparmor
  python3-apparmor-click python3-click python3-debian python3-gnupg
  python3-libapparmor qmenumodel-qml qml-module-qt-labs-folderlistmodel
  qml-module-qt-websockets qml-module-qtlocation qml-module-qtorganizer
  qml-module-qtpositioning qml-module-qtquick-particles2
  qml-module-qtquick-xmllistmodel qml-module-qtsensors qml-module-qtsysteminfo
  qml-module-ubuntu-onlineaccounts qml-module-ubuntu-onlineaccounts-client
  qtcontact5-galera qtdeclarative5-accounts-plugin
  qtdeclarative5-folderlistmodel-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-ofono0.2 qtdeclarative5-online-accounts-client0.1
  qtdeclarative5-particles-plugin qtdeclarative5-poppler1.0
  qtdeclarative5-qtmir-plugin qtdeclarative5-qtorganizer-plugin
  qtdeclarative5-systeminfo-plugin qtdeclarative5-u1db1.0
  qtdeclarative5-ubuntu-content1 qtdeclarative5-ubuntu-mediascanner0.1
  qtdeclarative5-ubuntu-push-plugin qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-syncmonitor0.1
  qtdeclarative5-ubuntu-telephony-phonenumber0.1
  qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-web-plugin qtdeclarative5-ubuntu-web-plugin-assets
  qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-usermetrics0.1 qtdeclarative5-window-plugin
  qtdeclarative5-xmllistmodel-plugin qtmir-desktop session-migration
  signon-plugin-oauth2 signon-plugin-password signon-ui signon-ui-service
  signon-ui-x11 signond system-image-common system-image-dbus
  telepathy-mission-control-5 telepathy-ofono telephony-service
  thumbnailer-common thumbnailer-service tone-generator ubuntu-app-launch
  ubuntu-app-launch-tools ubuntu-application-api2-test ubuntu-html5-container
  ubuntu-html5-ui-toolkit ubuntu-keyboard-data ubuntu-sdk-libs ubuntu-sounds
  ubuntu-system-settings ubuntu-system-settings-online-accounts
  ubuntu-touch-sounds ubuntuone-client-data ubuntuone-credentials-common
  unity-asset-pool unity-plugin-scopes unity-schemas unity-scope-click
  unity-scope-click-departmentsdb unity-scope-mediascanner2 unity-scope-scopes
  unity-webapps-qml unity8 unity8-common unity8-private urfkill
  whoopsie-preferences zeitgeist zeitgeist-core zeitgeist-datahub
Pacchetti suggeriti:
  click-reviewers-tools evolution evolution-data-server-dbg
  unity-system-compositor content-hub telepathy-haze
I seguenti pacchetti NUOVI saranno installati:
  account-plugin-tools account-plugin-ubuntuone accountsservice-ubuntu-schemas
  accountsservice-ubuntu-touch-schemas address-book-service apparmor-easyprof
  apparmor-easyprof-ubuntu click click-apparmor dbus-property-service
  dconf-cli evolution-data-server evolution-data-server-online-accounts
  folks-common gir1.2-accounts-1.0 gir1.2-click-0.4 gir1.2-gee-0.8
  gir1.2-json-1.0 gir1.2-signon-1.0 history-service indicator-bluetooth
  indicator-network indicator-power libaccounts-glib0 libaccounts-qt5-1
  libandroid-properties1 libboost-locale1.55.0 libboost-regex1.55.0
  libcapnp-0.4.0 libconnectivity-qt1 libcontent-hub0 libdbus-cpp4
  libebackend-1.2-7 libebook-1.2-14 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libfolks-eds25 libfolks25 libgdata-common libgdata19
  libgeocode-glib0 libgoa-1.0-0b libgoa-1.0-common libgweather-3-6
  libgweather-common libhardware2 libhistoryservice0 libhybris
  libhybris-common1 libhybris-utils libjsoncpp0 liblttng-ust-ctl2
  liblttng-ust0 libmedia1 libmediascanner-2.0-3 libmirplatform6 libmirserver30
  libmission-control-plugins0 libnet-cpp1 liboauth0 libofono-qt1
  libonline-accounts-client1 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libpay2 libpgm-5.1-0 libphonenumber6 libpoppler-qt5-1
  libprocess-cpp2 libqmenumodel0 libqofono-qt5-0 libqt5concurrent5
  libqt5contacts5 libqt5keychain0 libqt5location5 libqt5location5-plugins
  libqt5positioning5 libqt5positioning5-plugins libqt5quickparticles5
  libqt5script5 libqt5sensors5 libqt5systeminfo5 libqt5versit5
  libqt5versitorganizer5 libqt5websockets5 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libsodium13
  libsystemsettings1 libtelepathy-qt5-0 libthumbnailer0 libtimezonemap-data
  libtimezonemap1 libtrust-store1 libu1db-qt5-3 libubuntu-app-launch2
  libubuntu-application-api2 libubuntu-location-service2
  libubuntu-platform-hardware-api2 libubuntuoneauth-2.0-0 libunity-api0
  libunity-scopes3 liburcu2 libwhoopsie-preferences0 libzeitgeist-2.0-0
  libzmq3 libzmqpp3 mediascanner2.0 mir-platform-graphics-mesa1 ofono
  packagekit-tools pay-service powerd python-zeitgeist python3-apparmor
  python3-apparmor-click python3-click python3-debian python3-gnupg
  python3-libapparmor qmenumodel-qml qml-module-qt-labs-folderlistmodel
  qml-module-qt-websockets qml-module-qtlocation qml-module-qtorganizer
  qml-module-qtpositioning qml-module-qtquick-particles2
  qml-module-qtquick-xmllistmodel qml-module-qtsensors qml-module-qtsysteminfo
  qml-module-ubuntu-connectivity qml-module-ubuntu-onlineaccounts
  qml-module-ubuntu-onlineaccounts-client qtcontact5-galera
  qtdeclarative5-accounts-plugin qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-ofono0.2
  qtdeclarative5-online-accounts-client0.1 qtdeclarative5-particles-plugin
  qtdeclarative5-poppler1.0 qtdeclarative5-qtmir-plugin
  qtdeclarative5-qtorganizer-plugin qtdeclarative5-systeminfo-plugin
  qtdeclarative5-u1db1.0 qtdeclarative5-ubuntu-content1
  qtdeclarative5-ubuntu-mediascanner0.1 qtdeclarative5-ubuntu-push-plugin
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-syncmonitor0.1
  qtdeclarative5-ubuntu-telephony-phonenumber0.1
  qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-web-plugin qtdeclarative5-ubuntu-web-plugin-assets
  qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-usermetrics0.1 qtdeclarative5-window-plugin
  qtdeclarative5-xmllistmodel-plugin qtmir-desktop session-migration
  signon-plugin-oauth2 signon-plugin-password signon-ui signon-ui-service
  signon-ui-x11 signond system-image-common system-image-dbus
  telepathy-mission-control-5 telepathy-ofono telephony-service
  thumbnailer-common thumbnailer-service tone-generator ubuntu-app-launch
  ubuntu-app-launch-tools ubuntu-application-api2-test ubuntu-html5-container
  ubuntu-html5-ui-toolkit ubuntu-keyboard-data ubuntu-sdk-libs ubuntu-sounds
  ubuntu-system-settings ubuntu-system-settings-online-accounts
  ubuntu-touch-sounds ubuntuone-client-data ubuntuone-credentials-common
  unity-asset-pool unity-plugin-scopes unity-schemas unity-scope-click
  unity-scope-click-departmentsdb unity-scope-mediascanner2 unity-scope-scopes
  unity-webapps-qml unity8 unity8-common unity8-private urfkill
  whoopsie-preferences zeitgeist zeitgeist-core zeitgeist-datahub
0 aggiornati, 210 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 73,4 MB/73,5 MB di archivi.
Dopo quest'operazione, verranno occupati 217 MB di spazio su disco.

```

And then it started. It's a huge half-giga podcast player :D
I'm just kidding, I can guess that all these packages are already installed in Ubuntu Touch. The thing that seems strange is that not all dependencies are found from "apt-get install", but I needed to install it manually. Is this normal?


EDIT: Nice crash after using PodBird for half an hour :)
```
enrico@enrico-linux:~$ qmlscene $@ /usr/share/podbird/qml/podbird/podbird.qml
QQmlComponent: Created graphical object was not placed in the graphics scene.
qml: [LOG]: Detecting first time run by user. Starting welcome wizard.
qml: [LOG]: Checking for new episodes
qml: [LOG]: Skipped autodownloading of new episodes...
qml: [LOG]: Online connectivity: true
qml: [LOG]: User settings (maxEpisodeDownload): -1
QXcbWindow: Unhandled client message: "_GTK_LOAD_ICONTHEMES"
qml: [LOG]: Welcome tour complete
QQmlComponent: Created graphical object was not placed in the graphics scene.
QQmlComponent: Created graphical object was not placed in the graphics scene.

(process:12047): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
qml: [LOG]: Checking for new episodes
qml: [LOG]: Finished checking for new episodes..
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: Unable to assign [undefined] to QString
file:///usr/share/podbird/qml/podbird/ui/WhatsNewTab.qml:481: Unable to assign [undefined] to QString
qml: [LOG]: Checking for new episodes
qml: [LOG]: Finished checking for new episodes..
qml: [LOG]: Checking for new episodes
qml: [LOG]: Checking for new episodes
qml: [LOG]: Finished checking for new episodes..
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: Unable to assign [undefined] to QString
qml: [LOG]: Podcast User metric incremented
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: Unable to assign [undefined] to QString
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: TypeError: Cannot read property 'downloadedfile' of undefined
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: Unable to assign [undefined] to QString
file:///usr/share/podbird/qml/podbird/ui/EpisodesPage.qml:530: TypeError: Cannot read property 'downloadedfile' of undefined
qml: [LOG]: Podcast User metric incremented
qml: [LOG]: Download cancelled
Errore di segmentazione (core dump creato)


```

---

