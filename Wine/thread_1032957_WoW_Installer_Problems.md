---
title: "WoW Installer Problems"
date: 2009-01-06
forum: Wine
---

### Post by Roflmewafflez on 2009-01-06
When trying to Install World Of Warcraft Wrath of the Lich King on my Ubuntu 8.10 (gnome) it will run the installer in the begining then when it gets to the end user license agreement the accept button is supposed to activate when you scroll to the bottom of the agreement and the button never ends up activating

Does anyone know what could be causing this?

---

### Post by Ajd on 2009-01-12
I'm having the same issue. Friendly bump.

---

### Post by Martin Wolflux on 2009-01-14
I had a similar problem, but I fixed it by using the Downloader while logged in as root.

There seems to be problems when installing WotLK from a DVD (which I have not been able to fix).

---

### Post by Bios Element on 2009-01-14
Already been fixed. Go get the WoW Downloader off the site and the button works. Oh, and don't run a program as root like that. >.>

---

### Post by hikaricore on 2009-01-14
Actually the best solution was to copy the files to your drive as root.
Then run them as a normal user...

Many if not all copies of the Wotlk dvd had very strange file permissions that caused problems with installation.

---

### Post by Valok on 2009-01-14
If memory serves me, I believe this is a WINE bug that was fixed with later versions.  So maybe double check to make sure you have the latest version of WINE and see if that helps.

---

### Post by Bios Element on 2009-01-14
> **Valok said:**
> If memory serves me, I believe this is a WINE bug that was fixed with later versions.  So maybe double check to make sure you have the latest version of WINE and see if that helps.

Just checked and the wotlk CD does not work for me. The downloader has a different version. Since Bliz "kinda/sorta" supports Linux i suspect they made a minor patch to get it to work under Wine.

---

### Post by Valok on 2009-01-14
Ahh that makes sense, I installed the game off of the online installer with no problems at all. Maybe give that a try and see how it turns out.

---

