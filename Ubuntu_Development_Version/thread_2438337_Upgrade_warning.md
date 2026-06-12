---
title: "Upgrade warning"
date: 2020-03-10
forum: Ubuntu Development Version
---

### Post by P-I H on 2020-03-10
There is a really big partial upgrade waiting. Looked at it, thought it was OK and tried it. However it gave errors and didn't finish. The system doesn't boot. Perhaps it will require a new installation.

---

### Post by CelticWarrior on 2020-03-10
Those partial upgrades should be avoided indeed. Almost always it's a symptom of an APT problem.

In those situations (had only two, I think, in many years) I did it in terminal with the usual apt-get update and apt-get dist-upgrade.

You may not need to reinstall if it's a problem with the desktop not loading. In TTY use the usual commands to update and it should fix it.

---

### Post by Frogs Hair on 2020-03-10
Partial upgrades occur during the development release cycle and can be more frequent if proposed/developer repositories are enabled.  Packages may be uploaded that depend on other packages not yet uploaded  hence you get a partial upgrade notice. It is not recommended to use the development release as your daily driver. 

  [https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by P-I H on 2020-03-10
Thanks, but not a problem to reinstall on this computer, as it is used as a test system.
The system hangs long before loading of the desktop. I will try tomorrow to boot in recovery mode and upgrade.
The boot record on sda is OK and the grub menu is OK. I'm able to boot to W10 and also to fedora 31.

---

### Post by P-I H on 2020-03-10
I upgraded my main computer's 20.04 installation and this went OK. After the upgrade "Dash to panel" worked OK, but "Dash to panel" settings doesn't work.
Because of this I'm a little curious about the upgrade to gnome 3.36. I had perhaps set "Developer Options" on my test system to check if there were any updates and forgot to remove that setting.

---

### Post by P-I H on 2020-03-11
Reinstalled, which took less than an hour with my customizations. Only one problem, settings of the extensions Dash to panel, Alternatetab, Desktop icons and Openweather don't work.

---

