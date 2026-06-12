---
title: "AppArmor Java Google Chrome FireFox profile question"
date: 2012-09-30
forum: Security
---

### Post by WhiteHatGuy on 2012-09-30
Hi everyone

Today I finally was able to install last version of Java in Lubuntu

I play online poker at partypoker. For linux, I need to run the poker room from my internet browser and I need to have Java Oracle 7 installed. Now, everything works fine and I am able to login to the poker room if I dont use an apparmor profile.

But here is the thing and the catch, at party poker is always full of cheaters, could be hackers, crackers, blackhats, thiefs from all around the world, and cybercriminals. And cause their games are completely RIGGED. This is a fact, and no wonder since you are playing with real money. So this attract this kind of low life no moral values people, who are capable of stealing money from their own mother.

That been said. I need to use apparmor profiles for firefox and google chrome, and Java in order to protect my self from these crooks, bulgars and thiefs.

I am using the default Lubuntu firefox apparmor profile and I use Hungry Man Google Chrome and java apparmor profile.

The problem is that all these profiles are so restricted that my poker room wont load in any of them if I enable apparmor web browsers profiles.

The poker room needs the java plugin in order to run.

I am wondering what do I need to change in the profiles in order to make them work? What line? The profiles are Lubuntu default firefox, insanitybit hungry man Google Chrome and Java profile.

Do I have to put a W at the end to enable write at some line of code? :lolflag: I am so freaking noob when it comes to create profiles.


Also Hungry Man I tried to load your Google Chrome apparmor profile at kernel with command:

cat /etc/apparmor.d/profile.name | sudo apparmor_parser -a


But I get an error:


Warning from stdin (line 1): apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
AppArmor parser error, in stdin line 58: Found unexpected character: '&#65533;'










```


# Last Modified: Fri Sep 28 23:38:48 2012
#include <tunables/global>

/opt/google/chrome/chrome {
capability sys_ptrace,

network inet stream,
network inet tcp,
network inet6 stream,
network inet6 tcp,

deny /anon_hugepage//deleted r,

/bin/readlink rCx,
/bin/which rCx,
/dev/ r,
/dev/dri/card* rw,
/dev/null rw,
/dev/ptmx rw,
/dev/random r,
/dev/snd/controlC* rw,
/dev/snd/pcm* rw,
/dev/snd/timer r,
/dev/tty rw,
/dev/urandom r,
/dev/video* r,
/etc/fonts/** r,
/etc/fstab r,
/etc/gai.conf r,
/etc/group r,
/etc/host.conf r,
/etc/hosts mr,
/etc/ld.so.cache mr,
/etc/locale.alias r,
/etc/localtime r,
/etc/lsb-release r,
/etc/mtab r,
/etc/nss_mdns.conf r,
/etc/nsswitch.conf r,
/etc/opt/chrome/policies/managed/ r,
/etc/opt/chrome/policies/managed/*.json r,
/etc/opt/chrome/policies/recommended/ r,
/etc/opt/chrome/policies/recommended/*.json r,
/etc/passwd mr,
/etc/protocols r,
/etc/pulse/client.conf r,
/etc/python*/sitecustomize.py r,
/etc/resolvconf/run/resolv.conf r,
/etc/samba/lmhosts r,
/etc/services r,
/etc/udev/udev.conf r,
/home/*/.Xauthority r,
owner /home/*/.cache/dconf/user mrw,
/home/*/.config/dconf/user r,
/home/*/.config/google-chrome/ r,
owner /home/*/.config/google-chrome/*.txt rw,
owner /home/*/.config/google-chrome/.com.* rw,
owner &#8220;/home/*/.config/google-chrome/Certificate Revocation Lists&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Consent To Send Stats&#8221; rw,
/home/*/.config/google-chrome/Default/ r,
owner /home/*/.config/google-chrome/Default/* rw,
owner /home/*/.config/google-chrome/Default/*.bak rw,
owner /home/*/.config/google-chrome/Default/*.txt rw,
owner &#8220;/home/*/.config/google-chrome/Default/Application Cache/&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Application Cache/Index&#8221; mrwk,
owner &#8220;/home/*/.config/google-chrome/Default/Application Cache/Index-journal&#8221; mrw,
owner &#8220;/home/*/.config/google-chrome/Default/Archived History&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Archived History-journal&#8221; rw,
owner /home/*/.config/google-chrome/Default/Bookmarks rw,
owner /home/*/.config/google-chrome/Default/Cookies rwk,
owner /home/*/.config/google-chrome/Default/Cookies-journal rw,
owner &#8220;/home/*/.config/google-chrome/Default/Current Session&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Current Tabs&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension Cookies&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Extension Cookies-journal&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/&#8221; r,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/*.dbtmp&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/*.log&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/*.sst&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/CURRENT&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/LOCK&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Extension State/MANIFEST-*&#8221; rw,
/home/*/.config/google-chrome/Default/Extensions/ r,
owner /home/*/.config/google-chrome/Default/Extensions/** rw,
owner /home/*/.config/google-chrome/Default/Extensions/*/*/*/*.so mrw,
owner /home/*/.config/google-chrome/Default/Favicons rwk,
owner /home/*/.config/google-chrome/Default/Favicons-journal rw,
owner &#8220;/home/*/.config/google-chrome/Default/File System/*/*/.usage&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/File System/Origins/LOCK&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/File System/Origins/MANIFEST-*&#8221; rw,
owner /home/*/.config/google-chrome/Default/History* rwk,
owner /home/*/.config/google-chrome/Default/IndexedDB/ r,
owner /home/*/.config/google-chrome/Default/IndexedDB/*.leveldb/ mrw,
owner /home/*/.config/google-chrome/Default/IndexedDB/*/LOCK rw,
owner &#8220;/home/*/.config/google-chrome/Default/Last Session&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Last Tabs&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Local Storage/&#8221; r,
owner &#8220;/home/*/.config/google-chrome/Default/Local Storage/*&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Login Data&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Login Data-journal&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Managed Mode Settings&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Network Action Predictor&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Network Action Predictor-journal&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/*&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/CacheWritableAdobeRoot/AssetCache/&#8221; r,
owner &#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/CacheWritableAdobeRoot/AssetCache/**&#8221; mrw,
&#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/WritableRoot/#SharedObjects/&#8221; r,
&#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/WritableRoot/#SharedObjects/**&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Pepper Data/Shockwave Flash/WritableRoot/macromedia.com/support/flashplayer/sys/**&#8221; rw,
owner /home/*/.config/google-chrome/Default/Preferences rw,
owner /home/*/.config/google-chrome/Default/QuotaManager rwk,
owner /home/*/.config/google-chrome/Default/QuotaManager-journal rw,
owner /home/*/.config/google-chrome/Default/Shortcuts rwk,
owner /home/*/.config/google-chrome/Default/Shortcuts-journal rw,
&#8220;/home/*/.config/google-chrome/Default/Sync Data/&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Data/SyncData.sqlite3&#8243; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Data/SyncData.sqlite3-journal&#8221; rw,
&#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/&#8221; r,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/*.dbtmp&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/*.log&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/*.sst&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/CURRENT&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/LOCK&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Sync Extension Settings/*/MANIFEST-*&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Top Sites&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Top Sites-journal&#8221; rw,
owner /home/*/.config/google-chrome/Default/TransportSecurity rw,
owner &#8220;/home/*/.config/google-chrome/Default/User StyleSheets/*.css&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Visited Links&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Default/Web Data&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Default/Web Data-journal&#8221; rw,
owner /home/*/.config/google-chrome/Default/databases/ rw,
owner /home/*/.config/google-chrome/Default/databases/*.com*/* rwk,
owner /home/*/.config/google-chrome/Default/databases/*.db rwk,
owner /home/*/.config/google-chrome/Default/databases/*.db-journal rwk,
owner /home/*/.config/google-chrome/Default/databases/chrome-extension*/* rwk,
owner /home/*/.config/google-chrome/Dictionaries/*.bdic rw,
owner &#8220;/home/*/.config/google-chrome/Local State&#8221; rw,
/home/*/.config/google-chrome/PepperFlash/ r,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Bloom&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Bloom Filter 2&#8243; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Bloom_new&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Cookies&#8221; rwk,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Cookies-journal&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Csd Whitelist&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Csd Whitelist_new&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Download&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Download Whitelist&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Download Whitelist_new&#8221; rw,
owner &#8220;/home/*/.config/google-chrome/Safe Browsing Download_new&#8221; rw,
owner /home/*/.config/google-chrome/SingletonCookie rw,
owner /home/*/.config/google-chrome/SingletonLock rw,
owner /home/*/.config/google-chrome/SingletonSocket rw,
owner /home/*/.config/google-chrome/Temp/scoped_dir_*/CRX_INSTALL/ r,
owner /home/*/.config/google-chrome/Temp/scoped_dir_*/CRX_INSTALL/*.png rw,
owner /home/*/.config/google-chrome/Temp/scoped_dir_*/CRX_INSTALL/_locales/ rw,
/home/*/.gtk-bookmarks r,
/home/*/.java/deployment/deployment.properties rwk,
/home/*/.local/share/icons/ r,
/home/*/.local/share/icons/*/*/apps/ r,
/home/*/.local/share/mime/* mr,
/home/*/.local/share/recently-used.xbel rw,
/home/*/.local/share/recently-used.xbel.* rw,
/home/*/.pki/nssdb/cert9.db rwk,
/home/*/.pki/nssdb/key4.db rwk,
/home/*/.pki/nssdb/pkcs11.txt rw,
/home/*/.pulse-cookie rwk,
/home/*/.pulse/ r,
/home/*/.thumbnails/normal/* r,
/home/*/Downloads/ r,
/home/*/Downloads/** rw,
/home/*/Pictures/ r,
/home/*/Pictures/** rw,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libbz2.so.* mr,
/lib/x86_64-linux-gnu/libc-*.so mr,
/lib/x86_64-linux-gnu/libcom_err.so.* mr,
/lib/x86_64-linux-gnu/libdbus-*.so.* mr,
/lib/x86_64-linux-gnu/libdl-*.so mr,
/lib/x86_64-linux-gnu/libexpat.so.* mr,
/lib/x86_64-linux-gnu/libgcc_s.so.* mr,
/lib/x86_64-linux-gnu/libgcrypt.so.* mr,
/lib/x86_64-linux-gnu/libglib-*.so.* mr,
/lib/x86_64-linux-gnu/libgpg-error.so.* mr,
/lib/x86_64-linux-gnu/libkeyutils.so.* mr,
/lib/x86_64-linux-gnu/libm-*.so mr,
/lib/x86_64-linux-gnu/libnsl-*.so mr,
/lib/x86_64-linux-gnu/libnss_dns-*.so mr,
/lib/x86_64-linux-gnu/libnss_files-*.so mr,
/lib/x86_64-linux-gnu/libpci.so.* mr,
/lib/x86_64-linux-gnu/libpcre.so.* mr,
/lib/x86_64-linux-gnu/libpng*.so.* mr,
/lib/x86_64-linux-gnu/libpthread-*.so mr,
/lib/x86_64-linux-gnu/libresolv-*.so mr,
/lib/x86_64-linux-gnu/librt-*.so mr,
/lib/x86_64-linux-gnu/libselinux.so.* mr,
/lib/x86_64-linux-gnu/libtinfo.so.* mr,
/lib/x86_64-linux-gnu/libudev.so.* mr,
/lib/x86_64-linux-gnu/libwrap.so.* mr,
/lib/x86_64-linux-gnu/libz.so.* mr,
/opt/google/chrome/*.png r,
/opt/google/chrome/PepperFlash/libpepflashplayer.so mr,
/opt/google/chrome/chrome mrix,
/opt/google/chrome/chrome-sandbox mrPx,
/opt/google/chrome/chrome.pak r,
/opt/google/chrome/default_apps/ r,
/opt/google/chrome/default_apps/*.json rw,
/opt/google/chrome/extensions/ rw,
/opt/google/chrome/google-chrome rix,
/opt/google/chrome/libffmpegsumo.so mr,
/opt/google/chrome/libpdf.so mr,
/opt/google/chrome/libppGoogleNaClPluginChrome.so mr,
/opt/google/chrome/locales/en-US.pak r,
/opt/google/chrome/nacl_helper_bootstrap Px,
/opt/google/chrome/nacl_irt_x86_64.nexe r,
/opt/google/chrome/resources.pak r,
/opt/google/chrome/theme_resources_*_percent.pak r,
/opt/google/chrome/ui_resources_*_percent.pak r,
/proc/*/mounts r,
/run/shm/ r,
/run/shm/.com.google.Chrome.* rw,
/run/shm/pulse-shm-* rw,
/selinux/ r,
/sys/bus/pci/devices/ r,
/sys/devices/*/*/resource r,
/sys/devices/pci*/*/*/class r,
/sys/devices/pci*/*/*/device r,
/sys/devices/pci*/*/*/irq r,
/sys/devices/pci*/*/*/resource r,
/sys/devices/pci*/*/*/vendor r,
/sys/devices/pci*/*:*/class r,
/sys/devices/pci*/*:*/device r,
/sys/devices/pci*/*:*/irq r,
/sys/devices/pci*/*:*/vendor r,
/sys/devices/system/cpu/ r,
/sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_*_freq r,
/sys/devices/system/cpu/online r,
/tmp/ r,
/tmp/** rw,
owner /tmp/chrome/** mrwk,
/usr/bin/dirname rCx,
/usr/bin/lsb_release rCx,
/usr/bin/xdg-open rCx,
/usr/bin/xdg-settings rCx,
/usr/include/python*/pyconfig.h r,
/usr/lib/gtk-*/*/menuproxies/libappmenu.so mr,
/usr/lib/jvm/java-*-oracle/jre/bin/java mrPx,
/usr/lib/jvm/java-*-oracle/jre/lib/** mr,
/usr/lib/libdee-*.so.* mr,
/usr/lib/libicudata.so.* mr,
/usr/lib/libicui18n.so.* mr,
/usr/lib/libicuuc.so.* mr,
/usr/lib/liboverlay-scrollbar*.so.* mr,
/usr/lib/libunity.so.* mr,
/usr/lib/locale/** mr,
/usr/lib/mozilla/plugins/ r,
/usr/lib/x86_64-linux-gnu/*/*/*modules/*.so mr,
/usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_conf_pulse.so mr,
/usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so mr,
/usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_rate_speexrate.so mr,
/usr/lib/x86_64-linux-gnu/dri/libdricore.so mr,
/usr/lib/x86_64-linux-gnu/dri/libgallium.so mr,
/usr/lib/x86_64-linux-gnu/dri/libglsl.so mr,
/usr/lib/x86_64-linux-gnu/dri/r*_dri.so mr,
/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so mr,
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules mr,
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache mr,
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-*/*/loaders.cache mr,
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-*/*/loaders/libpixbufloader-png.so mr,
/usr/lib/x86_64-linux-gnu/gdk-pixbuf-*/*/loaders/libpixbufloader-svg.so mr,
/usr/lib/x86_64-linux-gnu/gio/modules/ r,
/usr/lib/x86_64-linux-gnu/gio/modules/giomodule.cache mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgiognutls.so mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgiolibproxy.so mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgioremote-volume-monitor.so mr,
/usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so mr,
/usr/lib/x86_64-linux-gnu/gtk-*/*/engines/libmurrine.so mr,
/usr/lib/x86_64-linux-gnu/gtk-*/*/gtk.immodules mr,
/usr/lib/x86_64-linux-gnu/gtk-*/modules/libcanberra-gtk-module.so mr,
/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/printbackends/libprintbackend-cups.so mr,
/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/printbackends/libprintbackend-file.so mr,
/usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so mr,
/usr/lib/x86_64-linux-gnu/libFLAC.so.* mr,
/usr/lib/x86_64-linux-gnu/libLLVM-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libX11-xcb.so.* mr,
/usr/lib/x86_64-linux-gnu/libX11.so.* mr,
/usr/lib/x86_64-linux-gnu/libXau.so.* mr,
/usr/lib/x86_64-linux-gnu/libXcomposite.so.* mr,
/usr/lib/x86_64-linux-gnu/libXcursor.so.* mr,
/usr/lib/x86_64-linux-gnu/libXdamage.so.* mr,
/usr/lib/x86_64-linux-gnu/libXdmcp.so.* mr,
/usr/lib/x86_64-linux-gnu/libXext.so.* mr,
/usr/lib/x86_64-linux-gnu/libXfixes.so.* mr,
/usr/lib/x86_64-linux-gnu/libXi.so.* mr,
/usr/lib/x86_64-linux-gnu/libXinerama.so.* mr,
/usr/lib/x86_64-linux-gnu/libXrandr.so.* mr,
/usr/lib/x86_64-linux-gnu/libXrender.so.* mr,
/usr/lib/x86_64-linux-gnu/libXss.so.* mr,
/usr/lib/x86_64-linux-gnu/libXxf86vm.so.* mr,
/usr/lib/x86_64-linux-gnu/libasound.so.* mr,
/usr/lib/x86_64-linux-gnu/libasyncns.so.* mr,
/usr/lib/x86_64-linux-gnu/libatk-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libavahi-client.so.* mr,
/usr/lib/x86_64-linux-gnu/libavahi-common.so.* mr,
/usr/lib/x86_64-linux-gnu/libcairo.so.* mr,
/usr/lib/x86_64-linux-gnu/libcanberra-*/libcanberra-alsa.so r,
/usr/lib/x86_64-linux-gnu/libcanberra-*/libcanberra-pulse.so r,
/usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.* mr,
/usr/lib/x86_64-linux-gnu/libcanberra.so.* mr,
/usr/lib/x86_64-linux-gnu/libcroco-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libcups.so.* mr,
/usr/lib/x86_64-linux-gnu/libdbus-glib-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libdbusmenu-glib.so.* mr,
/usr/lib/x86_64-linux-gnu/libdbusmenu-gtk.so.* mr,
/usr/lib/x86_64-linux-gnu/libdrm.so.* mr,
/usr/lib/x86_64-linux-gnu/libffi.so.* mr,
/usr/lib/x86_64-linux-gnu/libfontconfig.so.* mr,
/usr/lib/x86_64-linux-gnu/libfreetype.so.* mr,
/usr/lib/x86_64-linux-gnu/libgconf-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgdk-x11-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgdk_pixbuf-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgee.so.* mr,
/usr/lib/x86_64-linux-gnu/libgio-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libglapi.so.* mr,
/usr/lib/x86_64-linux-gnu/libgmodule-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgnome-keyring.so.* mr,
/usr/lib/x86_64-linux-gnu/libgnutls.so.* mr,
/usr/lib/x86_64-linux-gnu/libgobject-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgssapi_krb*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgthread-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgtk-x*-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libibus-*.*.so.* mr,
/usr/lib/x86_64-linux-gnu/libjson.so.* mr,
/usr/lib/x86_64-linux-gnu/libk5crypto.so.* mr,
/usr/lib/x86_64-linux-gnu/libkrb5.so.* mr,
/usr/lib/x86_64-linux-gnu/libkrb5support.so.* mr,
/usr/lib/x86_64-linux-gnu/libltdl.so.* mr,
/usr/lib/x86_64-linux-gnu/libnspr*.so mr,
/usr/lib/x86_64-linux-gnu/libnss*.so mr,
/usr/lib/x86_64-linux-gnu/libogg.so.* mr,
/usr/lib/x86_64-linux-gnu/libp*-kit.so.* mr,
/usr/lib/x86_64-linux-gnu/libpango-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libpangocairo-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libpangoft*-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libpixman-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libplc*.so mr,
/usr/lib/x86_64-linux-gnu/libplds*.so mr,
/usr/lib/x86_64-linux-gnu/libpulse.so.* mr,
/usr/lib/x86_64-linux-gnu/libpulsecommon-*.so mr,
/usr/lib/x86_64-linux-gnu/librsvg-2.*o.* mr,
/usr/lib/x86_64-linux-gnu/libsmime*.so mr,
/usr/lib/x86_64-linux-gnu/libsndfile.so.* mr,
/usr/lib/x86_64-linux-gnu/libspeexdsp.so.* mr,
/usr/lib/x86_64-linux-gnu/libsqlite*.so.* mr,
/usr/lib/x86_64-linux-gnu/libstdc*.so.* mr,
/usr/lib/x86_64-linux-gnu/libtasn1.so.* mr,
/usr/lib/x86_64-linux-gnu/libtdb.so.* mr,
/usr/lib/x86_64-linux-gnu/libvorbis.so.* mr,
/usr/lib/x86_64-linux-gnu/libvorbisenc.so.* mr,
/usr/lib/x86_64-linux-gnu/libvorbisfile.so.* mr,
/usr/lib/x86_64-linux-gnu/libxcb-glx.so.* mr,
/usr/lib/x86_64-linux-gnu/libxcb-render.so.* mr,
/usr/lib/x86_64-linux-gnu/libxcb-shm.so.* mr,
/usr/lib/x86_64-linux-gnu/libxcb.so.* mr,
/usr/lib/x86_64-linux-gnu/libxml2.so.* mr,
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.* mr,
/usr/lib/x86_64-linux-gnu/nss/libfreebl*.so mr,
/usr/lib/x86_64-linux-gnu/nss/libnssckbi.so mr,
/usr/lib/x86_64-linux-gnu/nss/libsoftokn*.so mr,
/usr/lib/x86_64-linux-gnu/pango/*/module-files.d/ r,
/usr/lib/x86_64-linux-gnu/pango/*/module-files.d/libpango*.*.modules mr,
/usr/local/lib/python*/dist-packages/ r,
/usr/local/share/icons/ r,
/usr/local/share/icons/hicolor/*/apps/ r,
/usr/local/share/icons/hicolor/*/apps/*chrome.png r,
/usr/local/share/icons/hicolor/scalable/apps/ r,
/usr/share/** r,
/var/cache/*/*.cache-* mr,
/var/cache/nscd/group r,
/var/cache/nscd/passwd r,
/var/lib/dbus/machine-id r,
/var/tmp/ r,
owner /var/tmp/** w,
/var/tmp/** r,
/{,var/}run/.nscd_socket rw,
/{,var/}run/mdnsd rw,
/{,var/}run/nscd/socket rw,
/{,var/}run/resolvconf/resolv.conf r,
/{,var/}run/utmp r,
owner @{HOME}/.cache/** mrw,
owner @{HOME}/.config/** mrw,
@{PROC}/ r,
@{PROC}/*/auxv r,
@{PROC}/*/coredump_filter rw,
@{PROC}/*/maps r,
@{PROC}/[0-9]*/cmdline r,
@{PROC}/[0-9]*/fd/ r,
@{PROC}/[0-9]*/io r,
@{PROC}/[0-9]*/oom_score_adj w,
@{PROC}/[0-9]*/stat r,
@{PROC}/[0-9]*/statm r,
@{PROC}/[0-9]*/status r,
@{PROC}/[0-9]*/task/ r,
@{PROC}/[0-9]*/task/*/stat r,
@{PROC}/cpuinfo r,
@{PROC}/filesystems r,
@{PROC}/meminfo r,
@{PROC}/sys/kernel/shmmax r,
profile /bin/mkdir {

/bin/mkdir r,
/etc/ld.so.cache r,
/lib/x86_64-linux-gnu/ld*.so mr,
/lib/x86_64-linux-gnu/libc*.so mr,
/lib/x86_64-linux-gnu/libdl*.so mr,
/lib/x86_64-linux-gnu/libselinux.so* mr,
/proc/filesystems r,
/usr/lib/locale/locale-archive r,

}

profile /bin/readlink {

/bin/readlink r,
/etc/ld.so.cache r,
/lib/x86_64-linux-gnu/ld*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,
/usr/lib/locale/locale-archive r,

}

profile /bin/which {

/bin/dash r,
/bin/which r,
/dev/null rw,
/etc/ld.so.cache r,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,

}

profile /usr/bin/dirname {

/etc/ld.so.cache r,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,
/usr/bin/dirname r,
/usr/lib/locale/locale-archive r,

}

profile /usr/bin/lsb_release {
/dev/null rw,
/etc/ld.so.cache mr,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,
/lib/x86_64-linux-gnu/libcrypto.so.* mr,
/lib/x86_64-linux-gnu/libdl-*.so mr,
/lib/x86_64-linux-gnu/libgcc_s.so.* mr,
/lib/x86_64-linux-gnu/libm-*.so mr,
/lib/x86_64-linux-gnu/libpthread-*.so mr,
/lib/x86_64-linux-gnu/libssl.so.* mr,
/lib/x86_64-linux-gnu/libutil-*.so mr,
/lib/x86_64-linux-gnu/libz.so.* mr,
/proc/meminfo r,
/usr/bin/python* r,
/usr/include/python2.7/pyconfig.h r,
/usr/lib/python*/UserDict.py r,
/usr/lib/python*/UserDict.pyc r,
/usr/lib/python*/_abcoll.py r,
/usr/lib/python*/_abcoll.pyc r,
/usr/lib/python*/abc.py r,
/usr/lib/python*/abc.pyc r,
/usr/lib/python*/genericpath.py r,
/usr/lib/python*/genericpath.pyc r,
/usr/lib/python*/linecache.py r,
/usr/lib/python*/linecache.pyc r,
/usr/lib/python*/os.py r,
/usr/lib/python*/os.pyc r,
/usr/lib/python*/posixpath.py r,
/usr/lib/python*/posixpath.pyc r,
/usr/lib/python*/site.py r,
/usr/lib/python*/site.pyc r,
/usr/lib/python*/stat.py r,
/usr/lib/python*/stat.pyc r,
/usr/lib/python*/types.py r,
/usr/lib/python*/types.pyc r,
/usr/lib/python*/warnings.py r,
/usr/lib/python*/warnings.pyc r,
/usr/lib/python2.7/_weakrefset.py r,
/usr/lib/python2.7/_weakrefset.pyc r,
/usr/lib/python2.7/config/Makefile r,
/usr/lib/python2.7/copy_reg.py r,
/usr/lib/python2.7/copy_reg.pyc r,
/usr/lib/python2.7/re.py r,
/usr/lib/python2.7/re.pyc r,
/usr/lib/python2.7/sre_compile.py r,
/usr/lib/python2.7/sre_compile.pyc r,
/usr/lib/python2.7/sre_constants.py r,
/usr/lib/python2.7/sre_constants.pyc r,
/usr/lib/python2.7/sre_parse.py r,
/usr/lib/python2.7/sre_parse.pyc r,
/usr/lib/python2.7/sysconfig.py r,
/usr/lib/python2.7/sysconfig.pyc r,
/usr/lib/python2.7/traceback.py r,
/usr/lib/python2.7/traceback.pyc r,

}

profile /usr/bin/xdg-open {

/bin/dash r,
/etc/ld.so.cache mr,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,

}

profile /usr/bin/xdg-settings {

/bin/dash r,
/bin/grep rix,
/bin/mkdir rix,
/bin/readlink rix,
/bin/sed rix,
/bin/touch rix,
/bin/which rix,
/dev/null rw,
/etc/gnome/defaults.list r,
/etc/ld.so.cache mr,
/etc/locale.alias r,
/home/*/.local/share/applications/ rw,
/home/*/.local/share/applications/mimeapps.list r,
/lib/x86_64-linux-gnu/ld-*.so mr,
/lib/x86_64-linux-gnu/libc-*.so mr,
/lib/x86_64-linux-gnu/libdbus-*.so.* mr,
/lib/x86_64-linux-gnu/libdl-*.so mr,
/lib/x86_64-linux-gnu/libglib-*.so.* mr,
/lib/x86_64-linux-gnu/libm-*.so mr,
/lib/x86_64-linux-gnu/libpcre.so.* mr,
/lib/x86_64-linux-gnu/libpthread-*.so mr,
/lib/x86_64-linux-gnu/libresolv-*.so mr,
/lib/x86_64-linux-gnu/librt-*.so mr,
/lib/x86_64-linux-gnu/libselinux.so.* mr,
/lib/x86_64-linux-gnu/libz.so.* mr,
/proc/*/maps r,
/proc/filesystems r,
/usr/bin/basename rix,
/usr/bin/cut rix,
/usr/bin/dirname rix,
/usr/bin/gawk rix,
/usr/bin/gconftool-2 rix,
/usr/bin/xdg-mime rix,
/usr/bin/xdg-settings r,
/usr/lib/libsigsegv.so.* mr,
/usr/lib/locale/** r,
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules mr,
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache mr,
/usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.* mr,
/usr/lib/x86_64-linux-gnu/libffi.so.* mr,
/usr/lib/x86_64-linux-gnu/libgconf-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgio-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgmodule-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgobject-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libgthread-*.so.* mr,
/usr/lib/x86_64-linux-gnu/libxml*.so.* mr,
/usr/local/share/applications/google-chrome.desktop r,

}
}

```




Thanks guys for any help on this. ):P

---

### Post by Hungry Man on 2012-09-30
Hey, about my Chrome profile it look slike there's a character there that shouldn't be or isn't recognized (both in this case). Try deleting and rewriting just the first few lines by hand. When copy/pasting from my blog the characters must have gotten screwed up. It's a wordpress issue and I can't really solve it unfortunately.

What I would suggest is that you set the profiles to complain mode, use the poker site for a minute, and then use 'aa-logprof' (in the terminal, no quotes) to see what they need access to. You can then just allow what's necessary.

---

### Post by WhiteHatGuy on 2012-10-02
> **Hungry Man said:**
> Hey, about my Chrome profile it look slike there's a character there that shouldn't be or isn't recognized (both in this case). Try deleting and rewriting just the first few lines by hand. When copy/pasting from my blog the characters must have gotten screwed up. It's a wordpress issue and I can't really solve it unfortunately.

What I would suggest is that you set the profiles to complain mode, use the poker site for a minute, and then use 'aa-logprof' (in the terminal, no quotes) to see what they need access to. You can then just allow what's necessary.







Ok, I try yesterday but I was not able to figure out this one.:mad:




Ok I put the profile in complain mode,then I enter the poker room for a minute, then I put aa-logprof in the terminal, I get somemthing like, reading logs, and profiles in /etc/apparmor.d/ has been updated.

So far so good.



But then I have absolutely no idea what to do. Whats the next step. I mean the profile has been modified automatically and I should use it now?
Or do I have to go to the logs folder to see what rulez has been denied. And then make the right changes in the apparmor profile.

I am kinda lost on this one.

---

### Post by Hungry Man on 2012-10-02
If you can enforce the profile and it works then all is well and you can just leave it like that.

---

### Post by WhiteHatGuy on 2012-10-02
> **Hungry Man said:**
> If you can enforce the profile and it works then all is well and you can just leave it like that.


OOOOhhhhhh ok now I get it.




Regarding your profile look the error I get when I use aa-logprof in the terminal:




Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

/etc/apparmor.d/GoogleChromeHungry contains syntax errors. Line [owner “/home/*/.config/google-chrome/Certificate Revocation Lists” rw,]


Aparently there is something wrong with line 58, It must be my computer or something I did, damn it. I am going to write it by hand and see what happends.


Thanks

---

### Post by Hungry Man on 2012-10-02
Delete the quotes and rewrite them in manually. It's a wordpress issue.

You can just do a find and replace. Copy the quotes from the broken line and then put that in the 'find' box. In the replace just type an actual quote from the keyboard.

---

### Post by WhiteHatGuy on 2012-10-03
> **Hungry Man said:**
> Delete the quotes and rewrite them in manually. It's a wordpress issue.

You can just do a find and replace. Copy the quotes from the broken line and then put that in the 'find' box. In the replace just type an actual quote from the keyboard.





WoW, yep it was the quotes, I was able to fix it. Thanks.

But unfourntanly. When I enforce the profile. I cant start Google Chrome. If I click the shortcut on my desktop of google chrome, does not open and nothing happends.

The same thing happen if I use Chronomatic KodiacZiller profile for google chrome.

:mad::mad::(:(:confused::confused:

---

### Post by Hungry Man on 2012-10-03
Now that you've managed to get it enforced and we've fixed that quotation issue perhaps aa-logprof will give new results?

Could you also post the output of aa-status? Might help me - thanks.

---

### Post by rookcifer on 2012-10-03
> **WhiteHatGuy said:**
> The same thing happen if I use Chronomatic KodiacZiller profile for google chrome.


Calm down.  Hungry and I will walk you through this.

I have written a complete guide on AA profiles for Google Chrome.  It's on [my blog]("http://rookcifer.blogspot.com/2012/09/securing-google-chrome-in-ubuntu-1204.html").  It will include the following profiles:

usr.lib.totem.totem-plugin
browser-openjdk

As well as profiles for every part of Chrome:
google-chrome (the shell script)
nacl_bootstrap_helper
chrome-sandbox
chrome (the main binary)

If you install these as directed on my blog, you should be able to use Chrome without issue.

---

### Post by WhiteHatGuy on 2012-10-03
> **Hungry Man said:**
> Now that you've managed to get it enforced and we've fixed that quotation issue perhaps aa-logprof will give new results?

Could you also post the output of aa-status? Might help me - thanks.




My output is:

apparmor module is loaded.
25 profiles are loaded.
25 profiles are in enforce mode.
   /opt/google/chrome/chrome
   /opt/google/chrome/chrome///bin/mkdir
   /opt/google/chrome/chrome///bin/readlink
   /opt/google/chrome/chrome///bin/which
   /opt/google/chrome/chrome///usr/bin/dirname
   /opt/google/chrome/chrome///usr/bin/lsb_release
   /opt/google/chrome/chrome///usr/bin/xdg-open
   /opt/google/chrome/chrome///usr/bin/xdg-settings
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//launchpad_integration
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//launchpad_integration
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (822) 
   /usr/bin/freshclam (1396) 
   /usr/sbin/cupsd (548) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.




OMG WOW DUDE, this is getting real geek  LOL.  I never did stuff like this on windows.

I put your profile on complain mode,  then I open Google Chrome and I went to the poker room and login, after a minute, I close google chrome. Then I put aa-logprof. And now it gives me the option to allow or denied rules. The ones that got my atention are java ones. I put allow to all of them cause I dont know wich ones are a threath or a danger. Plus I need to see if I am able ti fix the thing about google chrome not open when I put profile in enforce mode.




Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.
Complain-mode changes:

Profile:  /opt/google/chrome/chrome
Path:     /etc/timezone
Mode:     r
Severity: unknown


 [1 - /etc/timezone]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/CacheUpgrade.properties
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/CacheUpgrade.properties 
 [2 - /home/*/.java/deployment/CacheUpgrade.properties]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/CacheUpgrade.properties r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/38/
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/38/ 
 [2 - /home/*/.java/deployment/cache/6.0/38/]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/38/ r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5 
 [2 - /home/*/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5 r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5.idx
Mode:     rk
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5.idx 
 [2 - /home/*/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5.idx]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/38/651cc4a6-5553a7e5.idx rk to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/48/
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/48/ 
 [2 - /home/*/.java/deployment/cache/6.0/48/]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/48/ r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/5/
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/5/ 
 [2 - /home/*/.java/deployment/cache/6.0/5/]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/5/ r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/57/
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/57/ 
 [2 - /home/*/.java/deployment/cache/6.0/57/]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/57/ r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/57/581f60b9-7ee22016
Mode:     r
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/57/581f60b9-7ee22016 
 [2 - /home/*/.java/deployment/cache/6.0/57/581f60b9-7ee22016]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/57/581f60b9-7ee22016 r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/deployment/cache/6.0/57/581f60b9-7ee22016.idx
Mode:     rk
Severity: 4

  1 - /home/alex/.java/deployment/cache/6.0/57/581f60b9-7ee22016.idx 
 [2 - /home/*/.java/deployment/cache/6.0/57/581f60b9-7ee22016.idx]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/*/.java/deployment/cache/6.0/57/581f60b9-7ee22016.idx rk to profile.

Profile:  /opt/google/chrome/chrome
Path:     /home/alex/.java/fonts/1.7.0_07/fcinfo-1-alex-desktop-Ubuntu-12.04-en.properties
Mode:     r
Severity: 4

  1 - /home/alex/.java/fonts/1.7.0_07/fcinfo-1-alex-desktop-Ubuntu-12.04-en.properties 
  2 - /home/*/.java/fonts/1.7.0_07/fcinfo-1-alex-desktop-Ubuntu-12.04-en.properties 
 [3 - /home/alex/.java/fonts/**]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /home/alex/.java/fonts/** r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /lib/i386-linux-gnu/libc-2.15.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-gnome-terminal> 
  9 - #include <abstractions/ubuntu-konsole> 
  10 - /lib/i386-linux-gnu/libc-2.15.so 
 [11 - /lib/i386-linux-gnu/libc-*.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /lib/i386-linux-gnu/libc-*.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /lib/i386-linux-gnu/libgcc_s.so.1
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-gnome-terminal> 
  9 - #include <abstractions/ubuntu-konsole> 
  10 - /lib/i386-linux-gnu/libgcc_s.so.1 
 [11 - /lib/i386-linux-gnu/libgcc_s.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /lib/i386-linux-gnu/libgcc_s.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /lib/i386-linux-gnu/libpthread-2.15.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-gnome-terminal> 
  9 - #include <abstractions/ubuntu-konsole> 
  10 - /lib/i386-linux-gnu/libpthread-2.15.so 
 [11 - /lib/i386-linux-gnu/libpthread-*.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /lib/i386-linux-gnu/libpthread-*.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /lib/i386-linux-gnu/librt-2.15.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-gnome-terminal> 
  9 - #include <abstractions/ubuntu-konsole> 
  10 - /lib/i386-linux-gnu/librt-2.15.so 
 [11 - /lib/i386-linux-gnu/librt-*.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /lib/i386-linux-gnu/librt-*.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
 [11 - /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/gio/modules/
Mode:     r
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
 [11 - /usr/lib/i386-linux-gnu/gio/modules/]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/gio/modules/ r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/gio/modules/giomodule.cache
Mode:     r
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
 [11 - /usr/lib/i386-linux-gnu/gio/modules/giomodule.cache]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/gio/modules/giomodule.cache r to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
 [11 - /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
 [11 - /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libX11.so.6.3.0 
 [12 - /usr/lib/i386-linux-gnu/libX11.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libX11.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2 
 [12 - /usr/lib/i386-linux-gnu/libXcursor.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libXcursor.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libXext.so.6.4.0 
 [12 - /usr/lib/i386-linux-gnu/libXext.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libXext.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0 
 [12 - /usr/lib/i386-linux-gnu/libXfixes.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libXfixes.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libXrender.so.1.3.0 
 [12 - /usr/lib/i386-linux-gnu/libXrender.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libXrender.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libXss.so.1.0.0
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libXss.so.1.0.0 
 [12 - /usr/lib/i386-linux-gnu/libXss.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libXss.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libcroco-0.6.so.3.0.1
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libcroco-0.6.so.3.0.1 
 [12 - /usr/lib/i386-linux-gnu/libcroco-0.6.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libcroco-0.6.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/librsvg-2.so.2.36.1
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/librsvg-2.so.2.36.1 
 [12 - /usr/lib/i386-linux-gnu/librsvg-2.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/librsvg-2.so.* mr to profile.

Profile:  /opt/google/chrome/chrome
Path:     /usr/lib/i386-linux-gnu/libxml2.so.2.7.8
Mode:     mr
Severity: unknown


  1 - #include <abstractions/base> 
  2 - #include <abstractions/evince> 
  3 - #include <abstractions/gnome> 
  4 - #include <abstractions/kde> 
  5 - #include <abstractions/ubuntu-browsers.d/firefox> 
  6 - #include <abstractions/ubuntu-browsers.d/kde> 
  7 - #include <abstractions/ubuntu-browsers.d/mailto> 
  8 - #include <abstractions/ubuntu-browsers.d/plugins-common> 
  9 - #include <abstractions/ubuntu-gnome-terminal> 
  10 - #include <abstractions/ubuntu-konsole> 
  11 - /usr/lib/i386-linux-gnu/libxml2.so.2.7.8 
 [12 - /usr/lib/i386-linux-gnu/libxml2.so.*]

[(A)llow] / (D)eny / (G)lob / Glob w/(E)xt / (N)ew / Abo(r)t / (F)inish / (O)pts
Adding /usr/lib/i386-linux-gnu/libxml2.so.* mr to profile.

Profile:        /opt/google/chrome/chrome
Network Family: inet
Socket Type:    dgram

 [1 - #include <abstractions/nameservice>]
  2 - network inet dgram 

[(A)llow] / (D)eny / Audi(t) / Abo(r)t / (F)inish
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/Immunix/AppArmor.pm line 4092.
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/Immunix/AppArmor.pm line 4102.
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/Immunix/AppArmor.pm line 4092.
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/Immunix/AppArmor.pm line 4102.
Adding #include <abstractions/nameservice> to profile.
Deleted 14 previous matching profile entries.

= Changed Local Profiles =

The following local profiles were changed.  Would you like to save them?

 [1 - /opt/google/chrome/chrome]

(S)ave Changes / [(V)iew Changes] / Abo(r)t
Writing updated profile for /opt/google/chrome/chrome.

Can't write new AppArmor profile /etc/apparmor.d/GoogleChromeHungry: Permission denied

---

### Post by Hungry Man on 2012-10-03
You need to run aa-logprof as sudo (so 'sudo aa-logprof) or you won't be able to commit the changes.

home/*/.java/deployment/cache/** rm,

You can put that rule in there.

Are you on 32bit Ubuntu? That would explain the issues. My rules are for 64bit so I gave access to 64bit libraries. You're on 32bit so you need to give access to 32bit libraries.

---

### Post by WhiteHatGuy on 2012-10-03
> **Hungry Man said:**
> You need to run aa-logprof as sudo (so 'sudo aa-logprof) or you won't be able to commit the changes.

home/*/.java/deployment/cache/** rm,

You can put that rule in there.

Are you on 32bit Ubuntu? That would explain the issues. My rules are for 64bit so I gave access to 64bit libraries. You're on 32bit so you need to give access to 32bit libraries.







Yep, that explain the hole thing,I am using 32 bit. Hungry, your profile thats only for Java 7 oracle is also only for 64 bit or it would work also for 32 bit?

I am able to put your Java 7 oracle profile in enforce mode. But I cant login to the poker room, it blocks java plugin I think. So I try to put it in complain mode and then use sudo aa-logprof.

And this is my output:

Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

But does not give me the options for allow or denied rules, I mean, nothing happends.

I am trying to use, Chronomatic KodiacZiller firefox profile, and your hungry Java 7 oracle profile.

I also tried to include line:

home/*/.java/deployment/cache/** rm,


in your Java 7 Oracle profile, but it wont do the trick, I still cant login to the poker room, it blocks java.

---

### Post by Hungry Man on 2012-10-03
64bit or 32bit Java should not make much difference they store their libraries in the same area and I gave full read/mmap access to that directory.

Chrome uses shared libraries. On 32bit it'll use the 32bit libs on 64bit it uses 64bit libs. That's the issue.

Not sure why the Java profile isn't working.

---

### Post by rookcifer on 2012-10-04
> **WhiteHatGuy said:**
> I am trying to use, Chronomatic KodiacZiller firefox profile, and your hungry Java 7 oracle profile.


You should probably use either Hungry's profiles or mine.  You shouldn't mix them.

The main difference in our profiles is Hungry defines each shared library separately.  I tried doing this at first as well, but found out that Chrome needs access to so many .so's that it is much easier (and probably just as secure) to use the base abstraction to cover it.  In your case, it would have been best to use the base abstraction since HM wrote his profile for 64 bit.  I suggest you start over from scratch (build your own) or use my profile which uses the abstraction to cover those libs.

---

### Post by 0011235813 on 2012-10-05
Do you mind if I just but in a little, and say that while configuring apparmor is all nice and great, I'm not convinced it is a suitable measure for the OP.

OP claimed that they should try and use apparmor to protect themselves from cheating crooks.

Hon, apparmor is designed to protect programs such as browsers and printing utilities from zero day exploitations using sandboxing. That has nothing to do with a crook hacking the server. 

I suggest you don't play the game if you're in doubt of their security.

But carry on debugging apparmor :) I never got my Chrome profile working. Maybe you'll have more luck.

---

### Post by WhiteHatGuy on 2012-10-05
> **rookcifer said:**
> You should probably use either Hungry's profiles or mine.  You shouldn't mix them.

The main difference in our profiles is Hungry defines each shared library separately.  I tried doing this at first as well, but found out that Chrome needs access to so many .so's that it is much easier (and probably just as secure) to use the base abstraction to cover it.  In your case, it would have been best to use the base abstraction since HM wrote his profile for 64 bit.  I suggest you start over from scratch (build your own) or use my profile which uses the abstraction to cover those libs.





Hi, thanks for the links and tutorials, very very helpfull

The reason I mixed profiles is because in your site sais for firefox profile:

This profile will only work for OpenJDK (and IcedTea) and *not* Oracle's Java.  OpenJDK comes with Ubuntu, so if you are using the defaults, then you will be fine here. 

This only works with OpenJDK-7.  If you use v. 6 for some odd reason, then you will need to replace all the 7's in the profile. 

Thats why I was trying to use Hungry Man profile cause I was using Java Oracle 7, and your profile is not build for it.


But its ok, I am going to use OpenJDK 7 (and IcedTea), so I can use your profiles.

But I have one question, wich version has to be the IcedTea?

Thing is that with Lubuntu, I install OpenJDK 7, so far so good, but when I install IcedTea from repositories. Automatically install OpenJDK 6 and IcedTea 6. I think version 7 hasent been release so far. I am not shure.

Can you tell me please how and what order to install things, so your profiles for firefox works good with no holes or leaks or vulnerabilities?





I also tried your Google Chrome profile, you say is for 32 bits, thats great, but it happends the same behavior that Hungry Man profile. When I click or shortcut or tried to open google chrome, nothing happens and wont open.



LOL I been study all the things you guys has been telling me here. I am still learning):P

---

### Post by WhiteHatGuy on 2012-10-05
> **0011235813 said:**
> Do you mind if I just but in a little, and say that while configuring apparmor is all nice and great, I'm not convinced it is a suitable measure for the OP.

OP claimed that they should try and use apparmor to protect themselves from cheating crooks.

Hon, apparmor is designed to protect programs such as browsers and printing utilities from zero day exploitations using sandboxing. That has nothing to do with a crook hacking the server. 

I suggest you don't play the game if you're in doubt of their security.

But carry on debugging apparmor :) I never got my Chrome profile working. Maybe you'll have more luck.










Sorry for grammar, spelling errors. English is not my native language.

Of course, sandboxing the poker room makes a huge diference, the same thing using a VPN that changes your IP and encrypt your connection. Ive been fighting against Party Poker crooks (Ruth Parasol etc), 10 years of my life now. Their games are Rigged.
What means this is no matter how good you are at poker, if they decide to play you unfairly. You have not a chance. Is like playing poker with someone who can see your cards.

Their system works like a lottery, who gives winning hands to the hot IP addresses. If the system checks your IP address and other factors, like if you are depositing money to their poker room, and decide to give you winnings. No matter how bad you play, you will win session after session. But they let you win a little bit or some for some time, so you get hooked up, then they stop give you winnings, so you go and make another deposit of $20, that is the minimum. And so on. On the other hand if system checks your IP, checks if you are not making deposits to the poker room and other factors and decide to fuc* you up, and say, hey this guy is not making any deposits for ten years straight now. Its not bringing any money to our poker room, ok then, lets rigged the deck for him. And they provide you with a rigged game.

So what happends is that when you sand box the poker room in a low privileges enviroment, for example with comodo CIS, (untrusted level), the random number generator, or the poker room, starts to give you, winning hands. But does not end there. Thats where hacking time beggings. They start to use inject code, global hooks, rootkits, etc etc etc. At they always get away with it, sometimes takes minutes, sometime hours, rarely days or weeks, to crack the thing. Depends on how tight your security is, and like they say on the chat to his hacking criminal thiefs friends, YOU DO THE CRACKING, I take care of the rest. For example EmsisoftAntiMalware, has my poker room clasified as malware, if I scan my computer with windows, and party poker its installed, Emsisoft gives you the warning and make a complete removal of the poker room. The hole thing is completely full of malware. So they can cheat their customers. Who blindly trust them.

Same applies if you use VPN when you connect to the poker room. No matter how bad you play you are probably are going to win pot after pot, session after session.
But like I said, hacking time beggings. When you use a vpn, they have no other choice to disconnect you. And the disconnection I think it happends from their side. So they dont need to hack your machine in order to disconnect you.

Is like if your ISP want you to disconnect your internet connection, there is nothing you can do. You can make your OS a bullet proof against hackers, that if your ISP decide to disconect you, is the end of story. 

I test this for over 10 years now on windows. And now I decide to make the same thing but in linux, and see what happends. Is my little experiment.

I am pretty shure that some one with high knowledge of linux security stuff, will bring to these crooks, extremely hard times and nightmares.

But I am no pro on linux security. Just learning

---

### Post by 0011235813 on 2012-10-06
> **WhiteHatGuy said:**
> Sorry for grammar, spelling errors. English is not my native language.

Of course, sandboxing the poker room makes a huge diference, the same thing using a VPN that changes your IP and encrypt your connection. Ive been fighting against Party Poker crooks (Ruth Parasol etc), 10 years of my life now. Their games are Rigged.
What means this is no matter how good you are at poker, if they decide to play you unfairly. You have not a chance. Is like playing poker with someone who can see your cards.

Their system works like a lottery, who gives winning hands to the hot IP addresses. If the system checks your IP address and other factors, like if you are depositing money to their poker room, and decide to give you winnings. No matter how bad you play, you will win session after session. But they let you win a little bit or some for some time, so you get hooked up, then they stop give you winnings, so you go and make another deposit of $20, that is the minimum. And so on. On the other hand if system checks your IP, checks if you are not making deposits to the poker room and other factors and decide to fuc* you up, and say, hey this guy is not making any deposits for ten years straight now. Its not bringing any money to our poker room, ok then, lets rigged the deck for him. And they provide you with a rigged game.

So what happends is that when you sand box the poker room in a low privileges enviroment, for example with comodo CIS, (untrusted level), the random number generator, or the poker room, starts to give you, winning hands. But does not end there. Thats where hacking time beggings. They start to use inject code, global hooks, rootkits, etc etc etc. At they always get away with it, sometimes takes minutes, sometime hours, rarely days or weeks, to crack the thing. Depends on how tight your security is, and like they say on the chat to his hacking criminal thiefs friends, YOU DO THE CRACKING, I take care of the rest. For example EmsisoftAntiMalware, has my poker room clasified as malware, if I scan my computer with windows, and party poker its installed, Emsisoft gives you the warning and make a complete removal of the poker room. The hole thing is completely full of malware. So they can cheat their customers. Who blindly trust them.

Same applies if you use VPN when you connect to the poker room. No matter how bad you play you are probably are going to win pot after pot, session after session.
But like I said, hacking time beggings. When you use a vpn, they have no other choice to disconnect you. And the disconnection I think it happends from their side. So they dont need to hack your machine in order to disconnect you.

Is like if your ISP want you to disconnect your internet connection, there is nothing you can do. You can make your OS a bullet proof against hackers, that if your ISP decide to disconect you, is the end of story. 

I test this for over 10 years now on windows. And now I decide to make the same thing but in linux, and see what happends. Is my little experiment.

I am pretty shure that some one with high knowledge of linux security stuff, will bring to these crooks, extremely hard times and nightmares.

But I am no pro on linux security. Just learning
That sounds like a very dodgy company you're describing there. I really wouldn't waste your time with such a shoddy company, there must be better poker companies out there.

In any case, what platform you are accessing the service on (Be it Linux, Windows, OSX whatever) is irrelevant if the company discriminates based on IP address (this is what you're trying to say I assume?). You're better off with a proxy or VPN service, based on what you've told me (as opposed to apparmor).

Anyway, I'm not a native English speaker either. I'm curious as to what you're native language happens to be? Hope I don't sound rude saying that.

---

### Post by WhiteHatGuy on 2012-10-06
> **0011235813 said:**
> That sounds like a very dodgy company you're describing there. I really wouldn't waste your time with such a shoddy company, there must be better poker companies out there.

In any case, what platform you are accessing the service on (Be it Linux, Windows, OSX whatever) is irrelevant if the company discriminates based on IP address (this is what you're trying to say I assume?). You're better off with a proxy or VPN service, based on what you've told me (as opposed to apparmor).

Anyway, I'm not a native English speaker either. I'm curious as to what you're native language happens to be? Hope I don't sound rude saying that.



Yep, the VPN totally do the trick, but they can tell when you use it. For example a long time ago, I use two VPNs at same time. And they had hard times, because they where able to disconect me from one, but the other one was still there. And they get really mad, they put on chat ffs, or hh or !!, or its again that bullshi* of tts. That was describing I was using 2 VPNs, thats why the 2 letters ff. They got really mad when I was doing that. But somehow they figure it out how to crack it, at the end, it just take them several weeks. If I was able to not get disconnected from VPN, it would work like a charm, because the system send you wins at a ridiculios amounts of times.

But like I said I think the disconnection happends from their side, cause when they disconnect me, only the poker room lose internet connection, but if I surf the internet in my browser everything works fine. I think that it does not matter how tight my security system is. They had the power to disconnect me from the poker room, from where they are cheating. I dont think there is to much I can do about it. Again I could be wrong. I am no security expert. But I know the hole site is a scam.


My native language is spanish

---

