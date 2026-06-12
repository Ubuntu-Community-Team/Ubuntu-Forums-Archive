---
title: "Left 4 Dead Crash, wine 1.1.30"
date: 2009-09-30
forum: Wine
---

### Post by 8Kuula on 2009-09-30
H!

here is crash output.
```

bunbun@deimos:~/.wine/drive_d/Steam/steamapps/common/left 4 dead# env WINEDEBUG=fixme-all wine ./left4dead.exe -novid -sw -noborder          
Unable to remove d:\steam\steamapps\common\left 4 dead\left4dead\addonlist.txt!
err:module:import_dll Library MSVCP80.dll (which is needed by L"D:\\Steam\\steamapps\\common\\left 4 dead\\bin\\NovintHFX_0.5.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"D:\\Steam\\steamapps\\common\\left 4 dead\\bin\\NovintHFX_0.5.dll") not found
FS: Specified two path IDs (//mod/cfg/config.cfg, MOD).
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
0[494d6550]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
bunbun@deimos:~/.wine/drive_d/Steam/steamapps/common/left 4 dead# 

```

Crashes allways when connecting to server, loading goes all the way and after that it crash, back to desktop, not even wine error window. Solo game works ok, only net game crashes.

I have tried so far:
 - default ~/.wine directory + winetricks allfonts (had d3dx9 too on other times, it in or out did not help)
 - added MSVCP80.dll and MSVCR80.dll to L4D bin directory, import_dll Library errors did drop, crashes still.

I have not played L4D for while now. Again did start when new content came (crash course) so all i can say it did work before :)

Setup: ubuntu 9.04 64bit, wine 1.1.30

More info:
Seeems that, on server where is no motd, dont crash. On server where is, crash.
Just by chance i managed to get one server were not motd, after playing little, all seemed to work until i did press "h" key (pops up motd) did crash.

---

### Post by blattengel on 2009-10-02
This happens to me too.  I load the crash course map, see the motd, and it crashes.  All other maps work, even custom ones.

I've noticed a mini dump is put into:
"Steam/steamapps/common/left 4 dead"

Attached is the latest of 5 minidumps.

I'll see if Visual Studio can make anything of the mini dump files when I get a chance.  I don't know how to do it with gcc, anyone know of a good guide?

I'm guessing a quick fix would be to somehow disable the motd, thus avoiding the crash.

---

### Post by blattengel on 2009-10-02
Never mind!  The below doesn't work.  I was using single player mode for testing...

---------------

All right, disabling the motd circumvents the crash for me.

To do so, set the variable "motdfile" to a string that isn't a filename inside the left4dead directory.

I set mine to "a".

A few ways you can set the variable:
[LIST=1]
[*]Every time you start the game, open the console and type "motdfile "a"" without outer quotes.
[*]When launching left 4 dead, add the argument: +motdfile "a"
[*]Add said variable to this file: Steam/steamapps/common/left 4 dead/left4dead/cfg/config.cfg
[/LIST]

Odd how the game crashes when the motd is viewed in the new 'Crash Course' map.  Very odd...

---

### Post by blattengel on 2009-10-02
Alright.  I think I finally have it.  In this file:
Steam/steamapps/common/left 4 dead/left4dead/resource/UI/motd.res

Make all the "visible" and "enabled" values "0" instead of "1".

This seems to skip the motd whenever you join a server.  I wouldn't recommend viewing the motd manually, I did it once and it crashed the game again.

---

### Post by 8Kuula on 2009-10-03
> **blattengel said:**
> Alright.  I think I finally have it.  In this file:
Steam/steamapps/common/left 4 dead/left4dead/resource/UI/motd.res

Make all the "visible" and "enabled" values "0" instead of "1".

This seems to skip the motd whenever you join a server.  I wouldn't recommend viewing the motd manually, I did it once and it crashed the game again.

Hmm, dont work for me :( Four places find from motd.res file where to chance.

Same output than before.

No Mercy, Dead Air and Crash Course, friends-only game, best available dedicated. Eatch did crash in same place. After loading bar was finished and game should start.

But thanks for trying :)

---

### Post by 8Kuula on 2009-10-03
Hmm, for me that motd.res trick wont disable motd when i join in server. I did downgrade wine to 1.1.27 (is platinum in winehq) and game worked. And motd did show when i did join in server, motd.res modification is still active.

So for me downgrading wine to 1.1.27 worked :)

On other note seems something else wrong with 1.1.30 too since when i did launch supreme commander forged alliance all i did got was black screen, sound i did hear only so game starts but with black screen.
So did decide to downgrade wine, now just need remember not to update it when update-notifier says until 1.1.31...

---

### Post by blattengel on 2009-10-03
> **8Kuula said:**
> Hmm, for me that motd.res trick wont disable motd when i join in server. I did downgrade wine to 1.1.27 (is platinum in winehq) and game worked. And motd did show when i did join in server, motd.res modification is still active.

Yes you are right.  It didn't work for me either.  I thought it did, I guess the servers I joined didn't have a motd display on joining.  Bummer that didn't work.

Thanks for the tip about wine 1.1.27.  I'll have to downgrade to that.

---

### Post by asdfoo on 2009-10-04
... don't run Wine as root

---

### Post by blattengel on 2009-10-04
I just filled out a bug report here:
[http://bugs.winehq.org/show_bug.cgi?id=20257](http://bugs.winehq.org/show_bug.cgi?id=20257)

Here are the most recent test results for Left 4 Dead on winehq:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=45107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=45107)

---

### Post by BigKab on 2010-02-15
Can't believe this is still an issue.

---

### Post by Abolish666 on 2010-03-21
> **8Kuula said:**
> Hmm, for me that motd.res trick wont disable motd when i join in server. I did downgrade wine to 1.1.27 (is platinum in winehq) and game worked. And motd did show when i did join in server, motd.res modification is still active.

So for me downgrading wine to 1.1.27 worked :)

On other note seems something else wrong with 1.1.30 too since when i did launch supreme commander forged alliance all i did got was black screen, sound i did hear only so game starts but with black screen.
So did decide to downgrade wine, now just need remember not to update it when update-notifier says until 1.1.31...

Where can  i get 1.1.27??

---

### Post by 8Kuula on 2010-03-22
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Thou seems to work with v1.1.41 (newest at this time).

---

### Post by BigKab on 2010-03-28
Yes, 1.1.41 fixes this issue. Too bad I picked up another problem concerning textures with this version.

---

