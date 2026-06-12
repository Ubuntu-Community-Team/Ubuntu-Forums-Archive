---
title: "Getting Just Cause 2 to work on Ubuntu/Linux"
date: 2011-03-19
forum: Wine
---

### Post by smallfryfury on 2011-03-19
I have been searching for a way to get Just Cause 2 working with Linux. I  could not get it to work with wine, but I only know the basics.

Wine AppDB says the game needs DirectX10. But that was a year ago. Wine doesn't have a work around / substitute for that?

I have the latest Ubuntu and Wine versions. Also, I deleted these to get a clean slate.
    /home/(usr)/.wine/
    /home/(usr)/.winetrickscache/
    /home/(usr)/.cache/winetricks/

I can provide more info on my computer, but this problem isn't specific  to me. Any help getting this game to work would be excellent. It is a  very unique and fun looking game.

*EDIT:
I got this terminal output after trying it with a clean wine slate.

:~$ wine "/home/(usr)/Desktop/Steam/steamapps/common/just cause 2 demo/JustCause2.exe"
fixme:actctx : p a r s e_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by  L"Z:\\home\\justinw\\Desktop\\Steam\\steamapps\\common\\just cause 2  demo\\JustCause2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for  L"Z:\\home\\justinw\\Desktop\\Steam\\steamapps\\common\\just cause 2  demo\\JustCause2.exe" failed, status c0000135

*EDIT:
After downloading msvcp80.dll and placing in C:\Program Files\Steam\steamapps\common\just cause 2 demo\  I got this.

:~$ wine "C:\Program Files\Steam\steamapps\common\just cause 2 demo\JustCause2.exe"
fixme:actctx: p a r s e_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:msvcrt:_controlfp_s ((nil) 65536 196608 ) semi-stub
fixme:msvcr90:__clean_type_info_names_internal (0x7c49e210) stub

*EDIT:
I am not sure why actctx cannot find the Microsoft.VC80.CRT manifest. 
This is the file /home/(usr)/.wine/dosdevices/c:/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.762_none_10b2f55f9bffb8f8/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6b128700.manifest

I think actctx just needs pointed to this location, but I have no clue how to do that.

---

### Post by smallfryfury on 2011-03-22
P.S. I am not necessarily looking for the whole answer. Bits and pieces, hints, even insincere pep talks are happily accepted.

---

### Post by cogadh on 2011-03-22
The test results on Wine's Application Database might be old, but they are still valid. JC2 will not work in Wine (yet). Wine's support for DirectX 10 is [currently nonexistent]("http://www.winehq.org/status/directx") and without that, the game will never work (EDIT - assuming that it actually does require DX10 and cannot work with DX9).

On a side note, you did make one error in your attempts to get the game running. Simply copying msvcp80.dll into the game's install directory is not enough. That DLL is part of the Visual C++ Runtime and you need to actually install the runtime in Wine for it to be properly used. The best way to do that is using [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by smallfryfury on 2011-03-23
Thank you for answering. JC2 does not support DX9. It looks like wine might have one more developer.

---

