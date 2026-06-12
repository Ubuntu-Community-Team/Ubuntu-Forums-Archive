---
title: "Wolfenstein, wine 1.1.28"
date: 2009-08-30
forum: Wine
---

### Post by 8Kuula on 2009-08-30
H!

Did play whole Wolfenstein thru and now playing it again from start with increased difficulty, and planing to get all gold/intel/tomes this time too.
Finished Warehouse mission, and now it crashes with this error (terminal buffer full of that first error line).

```

bunbun@deimos:~/.wine/drive_d/Wolfenstein/SP# env WINEDEBUG=fixme-all wine ./Wolf2.exe
...
err:d3d:IWineD3DDeviceImpl_SetTexture Current stage overflows textures array (stage 256)
wine: Unhandled page fault on read access to 0x00000000 at address 0xb2cd42a (thread 0009), starting debugger...

```

Did try with clean ~/.wine directory too, except d3dx9_36.dll file put in ../windows/system32 (could not get it even run without it).
No luck.

Did reinstall whole game.
No luck.

Ubuntu 9.04 64bit, wine v1.1.28, nvidia v185.18.36

Any ideas? :)

I start to think game dont like player to go 100+ times in same map looking for items :P

---

### Post by 8Kuula on 2009-09-03
Looks like it is not wine related problem, game is buggy.

[www.wolfenstein.com/board/viewtopic.php?f=18&t=1398](www.wolfenstein.com/board/viewtopic.php?f=18&t=1398)

---

