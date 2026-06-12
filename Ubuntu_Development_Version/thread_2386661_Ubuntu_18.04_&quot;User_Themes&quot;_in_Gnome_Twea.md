---
title: "Ubuntu 18.04 &quot;User Themes&quot; in Gnome Tweak Tool MISSING"
date: 2018-03-08
forum: Ubuntu Development Version
---

### Post by violetdsobieski on 2018-03-08
In Ubuntu 18.04 there was the option to enable "User Themes" in Gnome Tweak Tool, enabling us to select a theme we want to use so we are not forced to use the standard grey and orange Gnome Shell Theme. After some updates to Ubuntu 18.04 this feature has been removed. Please put it back so people can choose a theme they want to use and not be forced to use the "one and only" theme Ubuntu comes with for Gnome 3. Stop taking features away from us, either keep it the same or give us more or new features :).

---

### Post by mc4man on 2018-03-08
don't use gnome-shell but I'd guess what you want is an extension so in that case install it.
Maybe - [https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

---

### Post by jbicha on 2018-03-09
The *gnome-shell-extensions* package includes the User Themes extension. It is not installed by default (although Ubuntu GNOME before 17.10 did.)

That package also provides the GNOME Classic mode (but you need to reboot after installing new sessions). Maybe the package should be split up a bit more so that the package names are more obvious what they do.

---

### Post by gregster on 2018-03-19
> **jbicha said:**
> The *gnome-shell-extensions* package includes the User Themes extension. It is not installed by default (although Ubuntu GNOME before 17.10 did.)

That package also provides the GNOME Classic mode (but you need to reboot after installing new sessions). Maybe the package should be split up a bit more so that the package names are more obvious what they do.

While 17.10 builds of gnome-shell-extensions included the user-theme extension current builds for 18.04 (bionic) do NOT. 

Head over [here]("https://packages.ubuntu.com/bionic/all/gnome-shell-extensions/filelist") and note that user-theme is NOT there.

---

### Post by Frogs Hair on 2018-03-19
I installed the extension successfully from the extensions website posted above.

---

### Post by jbicha on 2018-03-19
Thanks grester. This issue will be fixed in tomorrow's updates.

---

### Post by gregster on 2018-03-20
> **jbicha said:**
> Thanks grester. This issue will be fixed in tomorrow's updates.

Dude! That was awesome. Thanks very much.

---

