---
title: "Warsow: no antialiasing ?"
date: 2008-05-09
forum: Ubuntu Gamers Arena
---

### Post by TheExplorer on 2008-05-09
Hello,

I've got some kind of a problem. Well, it's just annoying...

My specs are:
AMD64 3200+, 2G RAM, NVidia 7600GT 256 MB
Ubuntu Hardy 8.04 LTS (final, not beta version)
Kernel 2.6.24.17 (hardy-proposed)
NVidia driver: 162.12 (from the official site)

I've changed the appropriate antialiasing and filtering from 'nvidia-settings', but' when playing Warsow it seems that antialiasing is not applied.

Is there a fix for that somewhere?

Thank you.

---

### Post by U83RMENSCH on 2008-05-23
As I recall, i didnt have AA on it either, in both ubuntu and windows, and im running an ATI card, so its possible its not even an option. however, i dont honestly remember.

That aside, I'd recommend Nexuiz instead. Similar game play, but much much more fun ( in my opinion )

nexuiz download at filefront.com: [http://files.filefront.com/nexuiz+223zip/;9011963;/fileinfo.html](http://files.filefront.com/nexuiz+223zip/;9011963;/fileinfo.html)

---

### Post by Jamieson630 on 2008-12-28
In my limited experience, the antialiasing override from nvidia-settings only takes effect if the game tries to enable antialiasing AT ALL.

In Half Life 2, if I set the in-game antialiasing setting to "None", it doesn't matter what the nvidia-settings override is; I will get no antialiasing. As soon as I set the in-game antialiasing setting to something other than "None", I get the antialiasing from the nvidia-settings override.

For games that do not provide an in-game option to enable antialiasing (such as UT2004), I have not discovered a way to force antialiasing.

All my tests so far have included Wine in the mix. I don't know if that has any effect on the AA behavior. A quick search to see if you can force Wine to enable multisampling didn't yield anything worthwhile.

Ubuntu 8.10 (Linux-x86_64)
nVidia driver 177.80
Wine 1.1.11-184-gb15ba76 (current git)

---

