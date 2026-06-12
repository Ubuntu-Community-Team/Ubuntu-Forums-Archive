---
title: "Should apparmor-profile be reloaded if firefox is updated?"
date: 2011-12-16
forum: Security
---

### Post by newhere_m on 2011-12-16
My main question here is whether I will have to disable existing enforced apparmor-profile for firefox when I update to a recent version of firefox, or will the current profile keep working for the updated version? Also should I reinstall no-script and adblock-plus after updating firefox?

A related doubt is this; please tell me if I have done anything wrong here: Just after installing Ubuntu 10.04 LTS-2, even before I set the network connection, I opened firefox (obviously browsing was not possible) and loaded apparmor profile for firefox in enforce mode. When network connection was established, I was prompted for security updates which I did and this contained a newer apparmor profile for firefox. I assume this updated profile got active by the update manager itself by replacing the older profile. Is that correct or will I have to set this new profile in enforce mode myself?

---

### Post by OpSecShellshock on 2011-12-16
Not sure about the Apparmor bit, but the Firefox extensions and their settings will be carried over when the version is upgraded, provided that they are compatible. Compatibility will be tested automatically the first time you run the new version.

---

### Post by jerome1232 on 2011-12-16
After I run upgrades in a terminal, the apparmor profiles get reloaded. I *believe *that would mean you do not have to manually reload the profiles.

---

### Post by FuturePilot on 2011-12-17
> **jerome1232 said:**
> After I run upgrades in a terminal, the apparmor profiles get reloaded. I *believe *that would mean you do not have to manually reload the profiles.

This is correct. As part of the postinst script for Firefox, it reloads apparmor.

---

