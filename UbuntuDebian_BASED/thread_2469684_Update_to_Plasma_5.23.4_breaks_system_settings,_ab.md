---
title: "Update to Plasma 5.23.4 breaks system settings, about system etc."
date: 2021-12-06
forum: Ubuntu/Debian BASED
---

### Post by timgood on 2021-12-06
Using latest KDE Neon (based on Kubuntu) and the latest update to Plasma 5.23.4 this afternoon has broken system settings etc. Launching from CLI gives me these errors:

```
Using fontconfig file: "/home/timg/.config/fontconfig/fonts.conf"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_plymouth.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_kwinrules.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: Two plugins with the same interface (QObject) were registered in the KPluginFactory KCMSddmFactory. This might be due to a missing Q_OBJECT macro in one of the registered classes
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_autostart.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: Two plugins with the same interface (QObject) were registered in the KPluginFactory SearchConfigModuleFactory. This might be due to a missing Q_OBJECT macro in one of the registered classes
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_users.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: Two plugins with the same interface (QObject) were registered in the KPluginFactory KcmComponentChooserFactory. This might be due to a missing Q_OBJECT macro in one of the registered classes
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_kaccounts.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_firewall.so"
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_about-distro.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_kscreen.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_nightcolor.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_pulseaudio.so"
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: "Could not load plugin from "
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_bluetooth.so"
kf.coreaddons: KPluginFactory could not load the plugin "/usr/lib/x86_64-linux-gnu/qt5/plugins/kcms/kcm_bolt.so"
Could not create scene graph context for backend 'opengl' - check that plugins are installed correctly in /usr/lib/x86_64-linux-gnu/qt5/plugins
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/private/RefreshableScrollView.qml:175:13: QML Binding: Not restoring previous value because restoreMode has not been set.
This behavior is deprecated.
You have to import QtQml 2.15 after any QtQuick imports and set
the restoreMode of the binding to fix this warning.
In Qt < 6.0 the default is Binding.RestoreBinding.
In Qt >= 6.0 the default is Binding.RestoreBindingOrValue.

file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/BasicListItem.qml:261:18: QML QQuickItem*: Binding loop detected for property "implicitWidth"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/private/RefreshableScrollView.qml:175:13: QML Binding: Not restoring previous value because restoreMode has not been set.
This behavior is deprecated.
You have to import QtQml 2.15 after any QtQuick imports and set
the restoreMode of the binding to fix this warning.
In Qt < 6.0 the default is Binding.RestoreBinding.
In Qt >= 6.0 the default is Binding.RestoreBindingOrValue.

file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/private/RefreshableScrollView.qml:175:13: QML Binding: Not restoring previous value because restoreMode has not been set.
This behavior is deprecated.
You have to import QtQml 2.15 after any QtQuick imports and set
the restoreMode of the binding to fix this warning.
In Qt < 6.0 the default is Binding.RestoreBinding.
In Qt >= 6.0 the default is Binding.RestoreBindingOrValue.

file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/BasicListItem.qml:261:18: QML QQuickItem*: Binding loop detected for property "implicitWidth"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/BasicListItem.qml:261:18: QML QQuickItem*: Binding loop detected for property "implicitWidth"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/BasicListItem.qml:261:18: QML QQuickItem*: Binding loop detected for property "implicitWidth"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/BasicListItem.qml:261:18: QML QQuickItem*: Binding loop detected for property "implicitWidth"
file:///usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/kirigami.2/private/RefreshableScrollView.qml:175:13: QML Binding: Not restoring previous value because restoreMode has not been set.
This behavior is deprecated.
You have to import QtQml 2.15 after any QtQuick imports and set
the restoreMode of the binding to fix this warning.
In Qt < 6.0 the default is Binding.RestoreBinding.
In Qt >= 6.0 the default is Binding.RestoreBindingOrValue.

QQmlEngine::setContextForObject(): Object already has a QQmlContext
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = systemsettings5 path = /usr/bin pid = 5246
KCrash: Arguments: /usr/bin/systemsettings5 
KCrash: Attempting to start /usr/lib/x86_64-linux-gnu/libexec/drkonqi

[1]+  Stopped                 systemsettings5

```

Any ideas? I can get into systemsettings by searching for 'autostart' for example and then I can access that screen and go back to main screen.

---

### Post by slickymaster on 2021-12-06
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by #&amp;thj^% on 2021-12-06
Seems your not alone: [https://forum.kde.org/viewtopic.php?f=289&t=173435](https://forum.kde.org/viewtopic.php?f=289&t=173435)

One user reported they used:
```
plasma-open-settings
```
In a konsole. (As a temporary work-around)

---

### Post by timgood on 2021-12-07
This morning's updates fixed the issue - qml-module issues apparently.

---

