---
title: "wine-gecko"
date: 2009-04-30
forum: Wine
---

### Post by risingsun on 2009-04-30
Hi, I'm running wine 1-1-20 and trying to install Wow. However I'm having issues with the HTML rendering. When getting to the EULA it says it couldn't activate gecko or somesuch.

Anyhow, I had gecko 0.1.0 I believe from the repositories but [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko) indicated I needed the later version. I followed the instructions tbu it still didn't work and I noticed the error message:

err:mshtml:install_from_unix_file Could not get dos file name of "/usr/bin/../lib/../share/wine/gecko/wine_gecko-0.9.1.cab"

Does anyone have any ideas of how to fix this? 

Also, is this a valid file? I still have holdovers from windows about any and every unknown file being dangerous but since it was from the wine project on sourceforge I assumed it would be ok and associated with the winehq though I could be mistaken. Can anyone set my mind at ease?

Many thanks :)

---

### Post by asdfoo on 2009-04-30
> **risingsun said:**
> Hi, I'm running wine 1-1-20 and trying to install Wow. However I'm having issues with the HTML rendering. When getting to the EULA it says it couldn't activate gecko or somesuch.

Anyhow, I had gecko 0.1.0 I believe from the repositories but [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko) indicated I needed the later version. I followed the instructions tbu it still didn't work and I noticed the error message:

err:mshtml:install_from_unix_file Could not get dos file name of "/usr/bin/../lib/../share/wine/gecko/wine_gecko-0.9.1.cab"

Does anyone have any ideas of how to fix this? 

Also, is this a valid file? I still have holdovers from windows about any and every unknown file being dangerous but since it was from the wine project on sourceforge I assumed it would be ok and associated with the winehq though I could be mistaken. Can anyone set my mind at ease?

Many thanks :)

gecko is used for rendering html content, the first time it's needed you get a download prompt and it fetches it for you.

If you want to install it manually, do:

wget [www.kegel.com/wine/winetricks](www.kegel.com/wine/winetricks)
sh winetricks gecko

---

### Post by YokoZar on 2009-05-01
Oops, I never ported the Wine-gecko 0.9.1 package from Intrepid to Jaunty.  I'm doing that now.  (all the package does is allow you to install gecko from your hard disk rather than having to download it from the internet when wine prompts you)

---

### Post by risingsun on 2009-05-01
Aye, I managed to get it working in the end by just editing the wine geckourl registry entry to point at the wine_gecko-0.9.1 file I got from the wine project at sourceforge (as linked in the wiki entry I linked to above) and it installed fine. All fixed now so many thanks. :)

---

