---
title: "After applying security patches from Ubuntu, VirtualBox hangs whole Ubuntu box when s"
date: 2018-01-11
forum: Virtualisation
---

### Post by tmarkwalder on 2018-01-11
After updating the security patches available from Ubuntu, attempting to  start my previously working VMs hangs the whole box.  I have to cold  boot it.  (Security patches for CVE-2017-5715, CVE-2017-5753,  CVE-2017-5754).

1. Launch VirtualBoxManager
2. Pick any of my three VMs
3. Click start
4. Console window for VM appears
5. Everything hangs ... no mouse/keyboard input, cannot ssh in... nothing

uname -a:

Linux wild-dog 4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Everything was fine yesterday before the patches, I've been using the VMs for weeks.

I'm using VirutalBox version   5.0.40_Ubuntu r115130

---

### Post by DuckHook on 2018-01-11
I experienced exactly the same problem. The problem is VB 5.0. You need to update to VB 5.2.

[LIST=1]
[*]Uninstall VB completely (Your VMs should be safe. They aren't touched by an uninstall. But make sure you are backed up as a matter of policy.).
[*]If not already present, add the Oracle PPA: [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)
[*]Then:```
sudo apt update
```
[*]Open Software Centre and install VB 5.2
[/LIST]

---

### Post by AnupamMitra on 2018-01-23
@ DuckHook : I'm also facing the same problem with this Kernel 4.13 for Ubuntu 16.04. In my Virtual Box Windows 7 was the guest. Virtual Box doesn't run anymore but freezes the entire system. However, I seen your above suggestion and uninstalled VB completely. As per your advice I opened Software Centre for VB 5.2. which is not available there. VB 5.0.40-dfsg-0ubuntu1.16.04.2 is available. 

However, beforehand I had downloaded virtualbox-5.2_5.2.6-120293~Ubuntu~xenial_amd64.deb from Oracle site and installed it. But after installation it didn't start the guest OS. Need your further advice.

---

### Post by AnupamMitra on 2018-01-23
@ DuckHook : Now I provide the following results:
```

$ uname -a
Linux anupam-ubuntu 4.13.0-31-generic #34~16.04.1-Ubuntu SMP Fri Jan 19 17:11:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

```

```

$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 94
Model name:            Intel(R) Core(TM) i3-6098P CPU @ 3.60GHz
Stepping:              3
CPU MHz:               3600.000
CPU max MHz:           3600.0000
CPU min MHz:           800.0000
BogoMIPS:              7200.00
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single pti intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp

```

```

$ tail -n 50 /var/log/apt/history.log
Commandline: aptdaemon role='role-upgrade-system' sender=':1.59'
Install: qtdeclarative5-ubuntu-ui-extras0.2:amd64 (0.3+16.04.20170323-0ubuntu1, automatic), python3-distro-info:amd64 (0.14build1, automatic), libgeonames-common:amd64 (0.2+16.04.20170220-0ubuntu1, automatic), liblttng-ust0:amd64 (2.7.1-1, automatic), libboost-program-options1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1, automatic), libgoogle-glog0v5:amd64 (0.3.4-0.1, automatic), indicator-common:amd64 (16.10.0+16.10.20160913-0ubuntu1~16.04, automatic), libaccount-plugin-flickr:amd64 (0.13+16.04.20170314-0ubuntu1, automatic), liblibertine1:amd64 (1.7.1+16.04.20170331-0ubuntu1, automatic), qml-module-qtsysteminfo:amd64 (5.0~git20141206~44f70d99-0ubuntu13~~xenialoverlay2~1, automatic), ubuntu-app-launch:amd64 (0.12+16.04.20170404.2-0ubuntu1, automatic), qtdeclarative5-ubuntu-download-manager0.1:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), libboost-thread1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1, automatic), libudm-common1:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), libubuntu-app-launch4:amd64 (0.12+16.04.20170404.2-0ubuntu1, automatic), libertined:amd64 (1.7.1+16.04.20170331-0ubuntu1, automatic), liburcu4:amd64 (0.9.1-3, automatic), libertine-xmir-tools:amd64 (1.7.1+16.04.20170331-0ubuntu1, automatic), libubuntu-download-manager-client1:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), libaccount-plugin-facebook:amd64 (0.13+16.04.20170314-0ubuntu1, automatic), libcontent-hub0:amd64 (0.3+16.04.20170403-0ubuntu1, automatic), qml-module-qtqml-models2:amd64 (5.6.2-0ubuntu1~~xenialoverlay1~9, automatic), libudm-priv-common1:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), geoclue-2.0:amd64 (2.4.1-1, automatic), libgeoclue-2-0:amd64 (2.4.1-1, automatic), python3-libertine:amd64 (1.7.1+16.04.20170331-0ubuntu1, automatic), libqt5concurrent5:amd64 (5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3, automatic), libqt5x11extras5:amd64 (5.6.2-0ubuntu1~~xenialoverlay1~1, automatic), qtdeclarative5-ubuntu-content1:amd64 (0.3+16.04.20170403-0ubuntu1, automatic), libxcb-xinerama0:amd64 (1.11.1-1ubuntu1, automatic), libubuntumetrics5:amd64 (1.3.2190+16.04.20170327build1~~xenialoverlay1~1, automatic), xmir:amd64 (2:1.18.4-0ubuntu0.7, automatic), libboost-log1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1, automatic), libubuntu-download-manager-common1:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), liblttng-ust-ctl2:amd64 (2.7.1-1, automatic), ubuntu-download-manager:amd64 (1.3+16.04.20161202-0ubuntu1, automatic), dbus-user-session:amd64 (1.10.6-1ubuntu3.3, automatic), libqt5systeminfo5:amd64 (5.0~git20141206~44f70d99-0ubuntu13~~xenialoverlay2~1, automatic), libboost-regex1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1, automatic), qml-module-ubuntu-components-labs:amd64 (1.3.2190+16.04.20170327build1~~xenialoverlay1~1, automatic), libgflags2v5:amd64 (2.1.2-3, automatic)
Upgrade: qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), bluez:amd64 (5.37-0ubuntu5.1, 5.41-0ubuntu1.1), signon-plugin-password:amd64 (8.58+16.04.20151106-0ubuntu1, 8.59+16.04.20160916-0ubuntu1), liboxideqt-qmlplugin:amd64 (1.21.5-0ubuntu0.16.04.1, 1.21.5-0ubuntu0.16.04.1+overlay1), suru-icon-theme:amd64 (14.04+16.04.20171116-0ubuntu1, 16.10+16.04.20161205-0ubuntu1), libhybris:amd64 (0.1.0+git20151016+6d424c9-0ubuntu7, 0.1.0+git20151016+6d424c9-0ubuntu24~xenial1), libqt4-xmlpatterns:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), libqt5svg5:amd64 (5.5.1-2build1, 5.6.2-0ubuntu1~~xenialoverlay1~1), intel-microcode:amd64 (3.20180108.0~ubuntu16.04.2, 3.20180108.0+really20170707ubuntu16.04.1), liboxideqtquick0:amd64 (1.21.5-0ubuntu0.16.04.1, 1.21.5-0ubuntu0.16.04.1+overlay1), qml-module-qtquick-window2:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), qml-module-ubuntu-test:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), libqt5test5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libaccounts-qt5-1:amd64 (1.14+16.04.20151106.1-0ubuntu1, 1.15+16.04.20161104.1-0ubuntu1), libhybris-common1:amd64 (0.1.0+git20151016+6d424c9-0ubuntu7, 0.1.0+git20151016+6d424c9-0ubuntu24~xenial1), liboxideqtcore0:amd64 (1.21.5-0ubuntu0.16.04.1, 1.21.5-0ubuntu0.16.04.1+overlay1), libprotobuf-lite9v5:amd64 (2.6.1-1.3, 2.6.1+16.04.20170317-0ubuntu1), zeitgeist-datahub:amd64 (0.9.16-0ubuntu4, 0.9.16-0ubuntu5~xenial), bluez-cups:amd64 (5.37-0ubuntu5.1, 5.41-0ubuntu1.1), qml-module-qtquick2:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libsignon-qt5-1:amd64 (8.58+16.04.20151106-0ubuntu1, 8.59+16.04.20160916-0ubuntu1), libqt4-declarative:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), qdbus:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), qml-module-qt-labs-folderlistmodel:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libmedia1:amd64 (0.1.0+git20151016+6d424c9-0ubuntu7, 0.1.0+git20151016+6d424c9-0ubuntu24~xenial1), libaccount-plugin-generic-oauth:amd64 (0.12+16.04.20160126-0ubuntu1, 0.13+16.04.20170314-0ubuntu1), libpulsedsp:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), libindicator7:amd64 (12.10.2+16.04.20151208-0ubuntu1, 16.10.0+16.10.20160913-0ubuntu1~16.04), account-plugin-flickr:amd64 (0.12+16.04.20160126-0ubuntu1, 0.13+16.04.20170314-0ubuntu1), signon-plugin-oauth2:amd64 (0.23+16.04.20151209-0ubuntu1, 0.24+16.04.20160818-0ubuntu1), libzmq5:amd64 (4.1.4-7, 4.1.5+git20160811+2fc86bc-0ubuntu0.16.04.1~overlay2), pulseaudio:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), gsettings-ubuntu-schemas:amd64 (0.0.5+16.04.20160307-0ubuntu1, 0.0.7+16.04.20161109-0ubuntu1), gnome-desktop3-data:amd64 (3.18.2-1ubuntu1, 3.18.2-1ubuntu1+overlay4), libqt5multimedia5:amd64 (5.5.1-4ubuntu2, 5.6.2-0ubuntu1~~xenialoverlay1~1), signond:amd64 (8.58+16.04.20151106-0ubuntu1, 8.59+16.04.20160916-0ubuntu1), libqt5organizer5:amd64 (5.0~git20140515~29475884-0ubuntu20, 5.0~git20140515~29475884-0ubuntu23~~xenialoverlay1~1), libsignon-plugins-common1:amd64 (8.58+16.04.20151106-0ubuntu1, 8.59+16.04.20160916-0ubuntu1), libhardware2:amd64 (0.1.0+git20151016+6d424c9-0ubuntu7, 0.1.0+git20151016+6d424c9-0ubuntu24~xenial1), libqt5dbus5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libqt5feedback5:amd64 (5.0~git20130529-0ubuntu13, 5.0~git20130529-0ubuntu15~~xenialoverlay1~1), libqt5sql5-sqlite:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libaccount-plugin-1.0-0:amd64 (0.1.8+16.04.20160201-0ubuntu1, 0.1.9+16.04.20160825-0ubuntu1), qtcore4-l10n:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), qml-module-qtquick-layouts:amd64 (5.5.1-1ubuntu1, 5.6.2-0ubuntu1~~xenialoverlay1~1), libqtcore4:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), libqt5widgets5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), indicator-sound:amd64 (12.10.2+16.04.20160406-0ubuntu1, 12.10.2+16.04.20170328.1-0ubuntu1), indicator-keyboard:amd64 (0.0.0+16.04.20151125-0ubuntu1, 0.0.0+16.04.20170301-0ubuntu1), gstreamer1.0-plugins-bad:amd64 (1.8.3-1ubuntu0.2, 1.8.3-1ubuntu0.3~overlay2), qml-module-qttest:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libindicator3-7:amd64 (12.10.2+16.04.20151208-0ubuntu1, 16.10.0+16.10.20160913-0ubuntu1~16.04), zeitgeist-core:amd64 (0.9.16-0ubuntu4, 0.9.16-0ubuntu5~xenial), qml-module-ubuntu-performancemetrics:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), qmlscene:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), account-plugin-facebook:amd64 (0.12+16.04.20160126-0ubuntu1, 0.13+16.04.20170314-0ubuntu1), gstreamer1.0-plugins-bad-videoparsers:amd64 (1.8.3-1ubuntu0.2, 1.8.3-1ubuntu0.3~overlay2), qml-module-qt-labs-settings:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), qtdeclarative5-test-plugin:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libandroid-properties1:amd64 (0.1.0+git20151016+6d424c9-0ubuntu7, 0.1.0+git20151016+6d424c9-0ubuntu24~xenial1), libqt5xml5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libqt5quicktest5:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), indicator-session:amd64 (12.10.5+16.04.20160412-0ubuntu1, 17.3.20+16.04.20170403-0ubuntu1), libqt5printsupport5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libqt5qml5:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libqtgui4:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), qml-module-ubuntu-web:amd64 (0.23+16.04.20161028-0ubuntu2, 0.23+16.04.20170321-0ubuntu1), gir1.2-gnomedesktop-3.0:amd64 (3.18.2-1ubuntu1, 3.18.2-1ubuntu1+overlay4), gir1.2-signon-1.0:amd64 (1.13+16.04.20151209.1-0ubuntu1, 1.14+16.04.20161117-0ubuntu1), libqt4-script:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), qml-module-qtfeedback:amd64 (5.0~git20130529-0ubuntu13, 5.0~git20130529-0ubuntu15~~xenialoverlay1~1), webapp-container:amd64 (0.23+16.04.20161028-0ubuntu2, 0.23+16.04.20170321-0ubuntu1), libqt5gui5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libgnome-desktop-3-12:amd64 (3.18.2-1ubuntu1, 3.18.2-1ubuntu1+overlay4), libpulse0:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), libpulse0:i386 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), libpulse-mainloop-glib0:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), gstreamer1.0-plugins-bad-faad:amd64 (1.8.3-1ubuntu0.2, 1.8.3-1ubuntu0.3~overlay2), indicator-bluetooth:amd64 (0.0.6+16.04.20160526-0ubuntu1, 0.0.6+16.04.20170322-0ubuntu1), libqt5webkit5:amd64 (5.5.1+dfsg-2ubuntu1, 5.6.1+dfsg-5ubuntu2~~xenialoverlay1~1), libqt4-sql-sqlite:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), oxideqt-codecs-extra:amd64 (1.21.5-0ubuntu0.16.04.1, 1.21.5-0ubuntu0.16.04.1+overlay1), libqtdbus4:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), unity-control-center-signon:amd64 (0.1.8+16.04.20160201-0ubuntu1, 0.1.9+16.04.20160825-0ubuntu1), appmenu-qt5:amd64 (0.3.0+16.04.20170216-0ubuntu1, 0.3.1+16.04.20170216-0ubuntu1), indicator-datetime:amd64 (15.10+16.04.20160406-0ubuntu1, 15.10+16.04.20170322-0ubuntu1), libqt5core5a:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libgsettings-qt1:amd64 (0.1+16.04.20160329-0ubuntu1, 0.1+16.04.20160329-0ubuntu3~~xenialoverlay1~1), ubuntu-mobile-icons:amd64 (14.04+16.04.20171116-0ubuntu1, 16.10+16.04.20161205-0ubuntu1), qml-module-ubuntu-layouts:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), libqt4-sql:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), libaccounts-glib0:amd64 (1.21+16.04.20160222-0ubuntu1, 1.23+16.04.20161104-0ubuntu1), pulseaudio-module-x11:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), light-themes:amd64 (14.04+16.04.20171116-0ubuntu1, 16.10+16.04.20161205-0ubuntu1), libmessaging-menu0:amd64 (13.10.1+15.10.20150505-0ubuntu1, 13.10.1+16.04.20161201-0ubuntu1), bluez-obexd:amd64 (5.37-0ubuntu5.1, 5.41-0ubuntu1.1), libqt5opengl5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), ubuntu-artwork:amd64 (1:14.04+16.04.20171116-0ubuntu1, 1:16.10+16.04.20161205-0ubuntu1), upstart:amd64 (1.13.2-0ubuntu21.1, 1.13.2-0ubuntu21.2), gir1.2-accounts-1.0:amd64 (1.21+16.04.20160222-0ubuntu1, 1.23+16.04.20161104-0ubuntu1), qttranslations5-l10n:amd64 (5.5.1-2build1, 5.6.2-0ubuntu1~~xenialoverlay1~1), qml-module-ubuntu-components:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), pulseaudio-module-bluetooth:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), libsignon-glib1:amd64 (1.13+16.04.20151209.1-0ubuntu1, 1.14+16.04.20161117-0ubuntu1), libzeitgeist-2.0-0:amd64 (0.9.16-0ubuntu4, 0.9.16-0ubuntu5~xenial), libqt4-xml:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), libubuntutoolkit5:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), signon-ui-service:amd64 (0.17+16.04.20151125-0ubuntu1, 0.17+16.04.20170320-0ubuntu1), libqt5network5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), libqt4-dbus:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), webbrowser-app:amd64 (0.23+16.04.20161028-0ubuntu2, 0.23+16.04.20170321-0ubuntu1), libaccount-plugin-google:amd64 (0.12+16.04.20160126-0ubuntu1, 0.13+16.04.20170314-0ubuntu1), libbluetooth3:amd64 (5.37-0ubuntu5.1, 5.41-0ubuntu1.1), libqt5positioning5:amd64 (5.5.1-3ubuntu1, 5.6.2-0ubuntu1~~xenialoverlay2~2), libubuntugestures5:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), libprotobuf9v5:amd64 (2.6.1-1.3, 2.6.1+16.04.20170317-0ubuntu1), account-plugin-google:amd64 (0.12+16.04.20160126-0ubuntu1, 0.13+16.04.20170314-0ubuntu1), pulseaudio-utils:amd64 (1:8.0-0ubuntu3.7, 1:8.0-0ubuntu6~xenial1), ubuntu-ui-toolkit-theme:amd64 (1.3.1918+16.04.20160404-0ubuntu1, 1.3.2190+16.04.20170327build1~~xenialoverlay1~1), indicator-power:amd64 (12.10.6+16.04.20160105-0ubuntu1, 12.10.6+16.04.20170322-0ubuntu1), qtdeclarative5-dev-tools:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), libgeonames0:amd64 (0.2+16.04.20160321-0ubuntu1, 0.2+16.04.20170220-0ubuntu1), libgstreamer-plugins-bad1.0-0:amd64 (1.8.3-1ubuntu0.2, 1.8.3-1ubuntu0.3~overlay2), libqt5quick5:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), ubuntu-mono:amd64 (14.04+16.04.20171116-0ubuntu1, 16.10+16.04.20161205-0ubuntu1), signon-ui:amd64 (0.17+16.04.20151125-0ubuntu1, 0.17+16.04.20170320-0ubuntu1), qtchooser:amd64 (52-gae5eeef-2build1~gcc5.2, 58-gfab25f1-1~xenialoverlay~1), libsignon-extension1:amd64 (8.58+16.04.20151106-0ubuntu1, 8.59+16.04.20160916-0ubuntu1), libmircommon5:amd64 (0.21.0+16.04.20160330-0ubuntu1, 0.22.1+16.04.20160516.2-0ubuntu1), libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), libqt5sql5:amd64 (5.5.1+dfsg-16ubuntu7.5, 5.6.2+dfsg-0ubuntu1~~xenialoverlay5~3), qml-module-qtgraphicaleffects:amd64 (5.5.1-1ubuntu1, 5.6.2-0ubuntu1~~xenialoverlay1~1), signon-ui-x11:amd64 (0.17+16.04.20151125-0ubuntu1, 0.17+16.04.20170320-0ubuntu1), indicator-messages:amd64 (13.10.1+15.10.20150505-0ubuntu1, 13.10.1+16.04.20161201-0ubuntu1), qtdeclarative5-qtquick2-plugin:amd64 (5.5.1-2ubuntu6, 5.6.2-0ubuntu1~~xenialoverlay1~9), liburl-dispatcher1:amd64 (0.1+16.04.20151110-0ubuntu2, 0.1+16.04.20170328-0ubuntu1), unity-webapps-qml:amd64 (0.1+16.04.20160114-0ubuntu1, 0.1+16.04.20160713-0ubuntu1), indicator-printers:amd64 (0.1.7+15.04.20150220-0ubuntu2, 0.1.7+16.04.20170227-0ubuntu1), libqt4-network:amd64 (4:4.8.7+dfsg-5ubuntu2, 4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1)
End-Date: 2018-01-22  23:45:57

Start-Date: 2018-01-23  00:11:47
Commandline: aptdaemon role='role-upgrade-system' sender=':1.59'
Upgrade: openssh-client:amd64 (1:7.2p2-4ubuntu2.2, 1:7.2p2-4ubuntu2.4)
End-Date: 2018-01-23  00:11:50

Start-Date: 2018-01-23  20:26:29
Commandline: aptdaemon role='role-commit-packages' sender=':1.82'
Install: linux-image-extra-4.13.0-31-generic:amd64 (4.13.0-31.34~16.04.1, automatic), linux-headers-4.13.0-31-generic:amd64 (4.13.0-31.34~16.04.1, automatic), linux-headers-4.13.0-31:amd64 (4.13.0-31.34~16.04.1, automatic), linux-image-4.13.0-31-generic:amd64 (4.13.0-31.34~16.04.1, automatic), linux-signed-image-4.13.0-31-generic:amd64 (4.13.0-31.34~16.04.1, automatic)
Upgrade: linux-libc-dev:amd64 (4.4.0-109.132, 4.4.0-112.135), linux-image-generic-hwe-16.04:amd64 (4.13.0.26.46, 4.13.0.31.51), linux-signed-generic-hwe-16.04:amd64 (4.13.0.26.46, 4.13.0.31.51), linux-generic-hwe-16.04:amd64 (4.13.0.26.46, 4.13.0.31.51), linux-signed-image-generic-hwe-16.04:amd64 (4.13.0.26.46, 4.13.0.31.51), linux-headers-generic-hwe-16.04:amd64 (4.13.0.26.46, 4.13.0.31.51)
End-Date: 2018-01-23  20:27:54

Start-Date: 2018-01-23  21:03:51
Commandline: apt-get purge virtualbox*
Requested-By: anupam (1000)
Purge: virtualbox-dkms:amd64 (5.0.40-dfsg-0ubuntu1.16.04.2), virtualbox:amd64 (), virtualbox-qt:amd64 (), virtualbox-5.2:amd64 (5.2.6-120293~Ubuntu~xenial)
End-Date: 2018-01-23  21:04:42

Start-Date: 2018-01-23  21:05:15
Commandline: apt-get purge unity-scope-virtualbox
Requested-By: anupam (1000)
Purge: unity-scope-virtualbox:amd64 (0.1+13.10.20130723-0ubuntu1)
End-Date: 2018-01-23  21:05:17

Start-Date: 2018-01-23  21:15:12
Commandline: apt-get purge virtualbox*
Requested-By: anupam (1000)
Purge: virtualbox-5.2:amd64 (5.2.6-120293~Ubuntu~xenial)
End-Date: 2018-01-23  21:15:52

Start-Date: 2018-01-23  21:18:09
Commandline: apt autoremove
Requested-By: anupam (1000)
Remove: python-six:amd64 (1.10.0-3), linux-headers-4.10.0-28-generic:amd64 (4.10.0-28.32~16.04.2), libgsoap8:amd64 (2.8.28-1), xscreensaver-gl:amd64 (5.34-2ubuntu1), linux-image-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), linux-signed-image-4.10.0-38-generic:amd64 (4.10.0-38.42~16.04.1), python-imaging:amd64 (3.1.2-0ubuntu1.1), containerd:amd64 (0.2.5-0ubuntu1~16.04.1), bridge-utils:amd64 (1.5-9ubuntu1), linux-signed-image-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), linux-image-4.10.0-42-generic:amd64 (4.10.0-42.46~16.04.1), cgroupfs-mount:amd64 (1.2), libjpeg-progs:amd64 (1:9b-1ubuntu1), python-chardet:amd64 (2.3.0-2), linux-signed-image-4.10.0-42-generic:amd64 (4.10.0-42.46~16.04.1), linux-image-4.10.0-28-generic:amd64 (4.10.0-28.32~16.04.2), python-lxml:amd64 (3.5.0-1build1), libvncserver1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1), gir1.2-gnomedesktop-3.0:amd64 (3.18.2-1ubuntu1+overlay4), libllvm4.0:amd64 (1:4.0-1ubuntu1~16.04.2), libllvm4.0:i386 (1:4.0-1ubuntu1~16.04.2), linux-image-extra-4.10.0-38-generic:amd64 (4.10.0-38.42~16.04.1), ubuntu-fan:amd64 (0.12.8~16.04.2), linux-headers-4.10.0-38-generic:amd64 (4.10.0-38.42~16.04.1), xscreensaver-data:amd64 (5.34-2ubuntu1), runc:amd64 (1.0.0~rc2+docker1.13.1-0ubuntu1~16.04.1), xscreensaver-data-extra:amd64 (5.34-2ubuntu1), linux-image-extra-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), python-pkg-resources:amd64 (20.7.0-1), python-html5lib:amd64 (0.999-4), libjpeg9:amd64 (1:9b-1ubuntu1), libgle3:amd64 (3.1.0-7.1), python-bs4:amd64 (4.4.1-1), libsdl1.2debian:amd64 (1.2.15+dfsg1-3), linux-image-extra-4.10.0-42-generic:amd64 (4.10.0-42.46~16.04.1), python-pyatspi:amd64 (2.18.0+dfsg-3), linux-headers-4.10.0-42-generic:amd64 (4.10.0-42.46~16.04.1), gir1.2-gdesktopenums-3.0:amd64 (3.18.1-1ubuntu1), caribou:amd64 (0.4.20-1), python-gconf:amd64 (2.28.1+dfsg-1.1), libsdl-ttf2.0-0:amd64 (2.0.11-3), linux-headers-4.10.0-28:amd64 (4.10.0-28.32~16.04.2), linux-headers-4.10.0-38:amd64 (4.10.0-38.42~16.04.1), linux-headers-4.10.0-40:amd64 (4.10.0-40.44~16.04.1), linux-headers-4.10.0-42:amd64 (4.10.0-42.46~16.04.1), xscreensaver-gl-extra:amd64 (5.34-2ubuntu1), linux-headers-4.10.0-40-generic:amd64 (4.10.0-40.44~16.04.1), gir1.2-gconf-2.0:amd64 (3.2.6-3ubuntu6), linux-image-4.10.0-38-generic:amd64 (4.10.0-38.42~16.04.1), libqt4-opengl:amd64 (4:4.8.7+dfsg-7ubuntu1~xenialoverlay1~1), gnome-backgrounds:amd64 (3.18.0-1), linux-image-extra-4.10.0-28-generic:amd64 (4.10.0-28.32~16.04.2)
End-Date: 2018-01-23  21:19:53

Start-Date: 2018-01-23  21:21:41
Commandline: aptdaemon role='role-install-file' sender=':1.57'
Install: libsdl1.2debian:amd64 (1.2.15+dfsg1-3, automatic)
End-Date: 2018-01-23  21:21:43

Start-Date: 2018-01-23  21:36:06
Commandline: apt autoremove --purge virtualbox*
Requested-By: anupam (1000)
Purge: libsdl1.2debian:amd64 (1.2.15+dfsg1-3), virtualbox-5.2:amd64 (5.2.6-120293~Ubuntu~xenial)
End-Date: 2018-01-23  21:36:49

```

---

### Post by AnupamMitra on 2018-01-25
Ultimately issue could be addressed and VB is installed and it starts guest OS. Thanks.

---

### Post by samio1221 on 2018-02-12
I'm new to ubuntu. I'm sorry, so what exactly is the solution here? Can someone please post an exact solution?
Precise action list or links would be very helpful or at least the sudo commands.
I have tried remove/purging. Then adding ppa, reinstall, update. Same problems.

---

### Post by howefield on 2018-02-12
Thread moved to the "*Virtualisation*" forum.

---

### Post by AnupamMitra on 2018-02-13
I mention below the details how I had settled the problem with the help of Lonnie Best (lonniebest@startport.com). You can try.

sudo sh -c 'echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib" >> /etc/apt/sources.list'

wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add 

sudo apt remove virtualbox

sudo apt update

sudo apt install virtualbox-5.2

---

