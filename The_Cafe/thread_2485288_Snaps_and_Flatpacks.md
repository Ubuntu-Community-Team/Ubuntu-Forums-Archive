---
title: "Snaps and Flatpacks"
date: 2023-03-25
forum: The Cafe
---

### Post by pantazi on 2023-03-25
I came across this article for those interested in the snap/flatpack debate. I don't know if this has been posted anywhere else on the forums.

[https://9to5linux.com/meet-ubuntu-flatpak-remix-ubuntu-with-flatpak-support-preinstalled](https://9to5linux.com/meet-ubuntu-flatpak-remix-ubuntu-with-flatpak-support-preinstalled)

---

### Post by nimafanniasl on 2023-03-26
Hmm, this is cool, finally no snaps easily (but with a remix)

---

### Post by TenPlus1 on 2023-03-26
I tend to recommend Linux Mint as an Ubuntu Os without snaps, but this is a very good start.

---

### Post by monkeybrain20122 on 2023-03-26
It is very easy to remove snap and set up flatpak anyway. However it would be nice of there is a gui for flatpak apps if I set up the system for new users. The gnome store extension is forever broken (or rather gnome store is forever broken ) and I heard that it would be removed.
Found [this]("https://github.com/vinifmor/bauh#installation"), will test it out.

---

### Post by TenPlus1 on 2023-03-27
You could always use FlatSeal for a graphical way to handle flatpak's ( [https://itsfoss.com/flatseal/](https://itsfoss.com/flatseal/) )

---

### Post by monkeybrain20122 on 2023-03-27
> **TenPlus1 said:**
> You could always use FlatSeal for a graphical way to handle flatpak's ( [https://itsfoss.com/flatseal/](https://itsfoss.com/flatseal/) )

Flatseal is for controlling access by flatpak apps, it is not an app store.

---

### Post by donald187 on 2023-03-27
> **monkeybrain20122 said:**
> Flatseal is for controlling access by flatpak apps, it is not an app store.

Doesn't installing the gnome software plugin automatically install a deb version of gnome software which handles Flatpaks?

[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

---

### Post by monkeybrain20122 on 2023-03-30
> **donald187 said:**
> Doesn't installing the gnome software plugin automatically install a deb version of gnome software which handles Flatpaks?

[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

It is broken for 22.04.

---

### Post by donald187 on 2023-03-30
> **monkeybrain20122 said:**
> It is broken for 22.04.
Sorry.  Didn't equate "extension" with "plugin". :)

---

### Post by Dennis N on 2023-03-30
> **monkeybrain20122 said:**
> It  is broken for 22.04.

It (gnome-software-plugin-flatpak) should work. Check **flatpak history**. My Ubuntu 22.04 did these (and a few more) today automatically in the background. A popup notification also indicated how many applications were updated. 

```
dmn@Tyana-vm:~$ flatpak history | tail
Mar 30 13:36:32	deploy update	com.mattjakeman.ExtensionManager	stable	system	flathub
Mar 30 13:36:32	deploy update	com.github.tchx84.Flatseal	stable	system	flathub
Mar 30 13:36:33	deploy update	org.gnome.Platform	42	system	flathub
Mar 30 13:36:35	deploy update	org.freedesktop.Platform	22.08	system	flathub
Mar 30 13:36:35	deploy update	org.kde.Platform.Locale	5.15-22.08	system	flathub
Mar 30 13:36:35	deploy update	org.kde.PlatformTheme.QGnomePlatform	5.15-22.08	system	flathub
Mar 30 13:36:37	deploy update	org.kde.Platform	5.15-22.08	system	flathub
Mar 30 13:36:37	deploy update	org.ksnip.ksnip	stable	system	flathub
Mar 30 13:36:37	deploy update	org.mozilla.firefox.Locale	stable	system	flathub
Mar 30 13:36:38	deploy update	org.mozilla.firefox	stable	system	flathub

```

---

