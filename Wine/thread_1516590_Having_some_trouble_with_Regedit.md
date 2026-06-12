---
title: "Having some trouble with Regedit"
date: 2010-06-23
forum: Wine
---

### Post by Vendettaseve on 2010-06-23
Having some troubles with Regedit. Im trying to fix up a couple of registry lines to get Dungeon Keeper 2 to work properly, primarily the mouse. Edit. I am using Ubuntu 10.04 and I also have Winetricks installed.

[Wine App DB link with instructions]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3696&iTestingId=50272")

And it asks me to add a new key MouseWarpOverride that does not exhist, also a great deal of the folders it lists keys in. 

I have tried creating several but it does not allow me to change the names.

[Wine Useful Keys Index]("http://wiki.winehq.org/UsefulRegistryKeys")

Thanks in advance.

---

### Post by asdfoo on 2010-06-24
hey

since using regedit is tiresome, this has been integrated into winetricks

try typing:
winetricks mwo=force
or:
winetricks mwo=disabled
or the default:
winetricks mwo=enabled

if you don't have winetricks, you can download it:
wget kegel.com/wine/winetricks
then:
sh winetricks mwo=force

etc

---

### Post by Vendettaseve on 2010-06-24
> **asdfoo said:**
> hey

since using regedit is tiresome, this has been integrated into winetricks

try typing:
winetricks mwo=force
or:
winetricks mwo=disabled
or the default:
winetricks mwo=enabled

if you don't have winetricks, you can download it:
wget kegel.com/wine/winetricks
then:
sh winetricks mwo=force

etc

Well that was easy. Thanks :D

---

### Post by Vendettaseve on 2010-06-24
Turns out, I tried all 3 of thoes commands and the mouse still jumps back to the middle of my screen uncontrollably :(

---

### Post by asdfoo on 2010-06-24
are you using the latest version of wine? 1.2-rc4?

---

### Post by Vendettaseve on 2010-06-24
> **asdfoo said:**
> are you using the latest version of wine? 1.2-rc4?

Im using 1.2-rc1 cant seem to get it to update to RC4

---

### Post by asdfoo on 2010-06-24
well, according to the appdb it should be set to disabled

# so:
winetricks mwo=disabled
# then, incase wine needs to be restarted, type:
wineserver -k

---

### Post by Vendettaseve on 2010-06-24
> **asdfoo said:**
> well, according to the appdb it should be set to disabled

# so:
winetricks mwo=disabled
# then, incase wine needs to be restarted, type:
wineserver -k

Tried this, did not work :(

I should also note, seemed to do something once as I could move my ubuntu mouse around freely and see it on screen during cutscenes but once the main game menu opened up it was the same old story of warping mouse.

If you want a copy of the game its listed as abandonware now and is free for public use. Should you want to test it or just give it a play its a wicked good game.

[Dungeon Keeper 2]("http://digiex.net/downloads/download-center-2-0/games-downloads/159-dungeon-keeper-2-full-version-1-7-a.html")

---

### Post by asdfoo on 2010-06-28
> **Vendettaseve said:**
> Tried this, did not work :(

I should also note, seemed to do something once as I could move my ubuntu mouse around freely and see it on screen during cutscenes but once the main game menu opened up it was the same old story of warping mouse.

If you want a copy of the game its listed as abandonware now and is free for public use. Should you want to test it or just give it a play its a wicked good game.

[Dungeon Keeper 2]("http://digiex.net/downloads/download-center-2-0/games-downloads/159-dungeon-keeper-2-full-version-1-7-a.html")

I'd try it myself but the video card in my linux desktop died.  The only other things I can suggest is maybe posting on the AppDB page for this program to see if anyone responds or you could try the WineHQ forum at [http://forum.winehq.org](http://forum.winehq.org)

---

### Post by Vendettaseve on 2010-06-30
> **asdfoo said:**
> I'd try it myself but the video card in my linux desktop died.  The only other things I can suggest is maybe posting on the AppDB page for this program to see if anyone responds or you could try the WineHQ forum at [http://forum.winehq.org](http://forum.winehq.org)

Sorry to hear about your graphics card, Hope you gave it a proper funeral, 10 gun salute etc etc.

As for Appdb, no ones interested in helping lol, posted the problem on the site there after I posted on the forums here and have yet to get a response. :(

---

### Post by Vendettaseve on 2010-07-07
Seems wine just updated to rc6 now, gave me a little hope when it fixed the issue of my ubuntu mouse showing through into the game window but the mouse still warps no matter what I set the MWO key to :(

Can anyone help? this is very frustrating.

Edit: It would appear that the ubuntu mouse dissapearing thing was just a fluke, its still there when I run the game again after the first time where it appeared to have been fixed.

---

