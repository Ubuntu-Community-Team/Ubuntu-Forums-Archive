---
title: "program won't run"
date: 2010-05-16
forum: Wine
---

### Post by Mzwo on 2010-05-16
hi,

I managed to install the update manager my satnav needs (which, obviously, is windows only), but no luck running it. The icon's appeared on the desktop, it has been made executable, but clicking it will just have me waiting for a wee while I'm being told the programm is being started - and then nothing. at all.

terminal says:

```
mzwo@mzwo-laptop:~$ env WINEPREFIX="/home/mzwo/.wine" wine "C:\Program Files\Becker\Content Manager 2\cm2.exe" 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Becker\\Content Manager 2\\cm2.exe" failed, status c0000005

```

help appreciated.

Matt

10.04, wine installed from repositories.

---

### Post by Mzwo on 2010-05-17
hi,

solved! 

see [http://forum.winehq.org/viewtopic.php?p=43624#43624]("http://forum.winehq.org/viewtopic.php?p=43624#43624")

thanks,
Matt

---

