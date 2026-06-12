---
title: "[SOLVED] Need help running WoW from windows using wine"
date: 2008-12-21
forum: Wine
---

### Post by Scytes on 2008-12-21
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library DivxDecoder.dll (which is needed by L"Z:\\mnt\\windows\\Program Files\\Worldofwarcraft\\Wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\mnt\\windows\\Program Files\\Worldofwarcraft\\Wow.exe" failed, status c0000135

---

### Post by Scytes on 2008-12-21
Whenever I got through the z:\mnt\windows and go to WoW's program filed and then try wow.exe I get this error 


fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library DivxDecoder.dll (which is needed by L"Z:\\host\\Program Files\\Worldofwarcraft 2\\Wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\host\\Program Files\\Worldofwarcraft 2\\Wow.exe" failed, status c0000135




can anyone tell me what it means?

---

### Post by pmooney78 on 2008-12-28
I'm not sure I'm reading this correctly, but it seems to me that you're trying to run WoW by browsing to the location on your Windows hard drive and executing it ... that you've installed it under Windows, rebooted into Ubuntu, and then try to run it?

If this is correct, then what you actually need to do is to install the program "under Wine." That is, you should boot into Ubuntu and use Wine to run the WoW installer.

Hope this helps.

---

