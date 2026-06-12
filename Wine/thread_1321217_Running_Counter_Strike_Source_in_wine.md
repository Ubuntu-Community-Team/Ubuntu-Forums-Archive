---
title: "Running Counter Strike Source in wine"
date: 2009-11-09
forum: Wine
---

### Post by ownsuall on 2009-11-09
The menu and the game look like ****. I can't see anything really the textures are just extremely messed up.
I'm running steam through a ntfs partition and installed it in windows and it works good in windows steam not so much. This is what the menu looks like(not my picture) [http://img249.imageshack.us/i/screenshotvn2.png/](http://img249.imageshack.us/i/screenshotvn2.png/)
If I can give any more info just ask =p
Wine verison is: 1.1.31
Graphics card is: Ati Mobility radeon X600
Driver verison: No idea how to find this out =(
Full hardware specs: [http://support.gateway.com/s/Mobile/Q106/Shadow/1008833sp2.shtml](http://support.gateway.com/s/Mobile/Q106/Shadow/1008833sp2.shtml)

Fixed: Ive tried running CS:S(Counter Strike Source) in wine under Xp and Vista but it didn't work =(
By: downgrading to wine 1.0.1

---

### Post by beastrace91 on 2009-11-09
Wine version, graphics card, and driver version?

Also regarding the fonts take a look into [winetricks](http://wiki.winehq.org/winetricks).

Regards,
~Jeff

---

### Post by chousho on 2009-11-11
I'm not completely certain (as I only found this thread due to searching for my graphics card: x600xt), but I think it might be due to using the open source drivers for your graphics card.

I too have an ATI x600 and have not been even able to play the older Half Life mods under the free drivers. As far as I remember, fglrx would require a downgrade of your X server in order to use.

Can anybody clarify or correct for further information? I, too would like to be able to run Steam/WoW/etc. on my system.

---

### Post by beastrace91 on 2009-11-11
You are correct in saying that you cannot do much 3D with the default drivers with ATI and the ones ATI provides for Linux honestly aren't much better. Try upgrading your Wine version to 1.1.32 (its the latest) and giving it a go - along with installing some drivers for your graphics card. But do not expect any decent results/FPS with the ATI card on Linux.

Regards,
~Jeff

---

