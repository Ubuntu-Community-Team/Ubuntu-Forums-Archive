---
title: "Stealthbot on to Battle.net using Wine"
date: 2009-07-13
forum: Wine
---

### Post by dontt0uchme on 2009-07-13
Hello,
I'm sorry I'm really not good with computers.  I have a mac and am trying to use wine to get a stealthbot working on Battle.net (warcraft3 - frozen throne, online).  I went through wine to install it, but now I'm getting an error, everytime I try to start it up I get this:

wine: created the configuration directory '/Users/jackwhipper/.wine'
Could not load Mozilla. HTML rendering will be disabled.
err:process:__wine_kernel_init boot event wait timed out
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (Apple-DRI)
  Minor opcode of failed request:  2 ()
  Value in failed request:  0x600294
  Serial number of failed request:  3063
  Current serial number in output stream:  3063
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\windows\\system32\\vbalTreeView6.ocx") not found
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\windows\\system32\\ssubtmr6.dll") not found
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe" failed, status c0000135
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe" failed, status c0000135
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\StealthBot\\StealthBot v2.6R3.exe" failed, status c0000135

Can anyone help me?
I would really appreciate it :)

Thank you,
Jack

---

### Post by doas777 on 2009-07-13
I know nothing of what you atr trying to do, but it looks like you need the VB6 runtime files.
Get a copy of  MSVBVM60.DLL and drop it in your application dir. you may have to add an application profile and a dll override in your wineconfig.
[http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)

---

### Post by Gosujii-sama on 2009-12-20
Hate to drag up a old topic if this is an old topic. I installed the MSVBVM60.DLL requiered for stealthboth to start the launcher however its also missing MSVBVM60.DBG which I can't seem to find a download for anywhere. Without this file its erroring out giving a msg that it cant find said dll like so:

```

err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "DLL\\MSVBVM60.dbg" ("")
  1 0x660d0956 in msvbvm60 (+0xd0956) (0x0032f09c)
  2 0x660cddaf in msvbvm60 (+0xcddaf) (0x0014d3a8)
  3 0x00000000 (0x00000000)

```

any ideas?

---

