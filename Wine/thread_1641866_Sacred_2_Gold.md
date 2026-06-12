---
title: "Sacred 2 Gold"
date: 2010-12-09
forum: Wine
---

### Post by Vepar on 2010-12-09
I've been trying to get the game to run, but no luck... In [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19127") it says that it works. I installed it from a directory with all 3 DVD's in it, and it installed fine, but doesn't want to run... 

I'm running it with Windows XP settings. Wine version 1.2, and Sacred is updated to the latest version 2.65.1, but it won't run...

I get this in terminal:

```
Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
err:module:import_dll Library s2logic.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2editor.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2editor.dll") not found
err:module:import_dll Library s2editor.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
err:module:import_dll Library s2logic.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logicai.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logicai.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logicai.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
err:module:import_dll Library s2logic.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logicai.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logicai.dll") not found
err:module:import_dll Library s2logicai.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
err:module:import_dll Library PhysXLoader.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\NxCharacter.dll") not found
err:module:import_dll Library NxCharacter.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
err:module:import_dll Library PhysXLoader.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\APEX_release.dll") not found
err:module:import_dll Library APEX_release.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\orcSystem.dll") not found
err:module:import_dll Library orcSystem.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2core.dll") not found
err:module:import_dll Library s2core.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2logic.dll") not found
err:module:import_dll Library s2logic.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\s2render.dll") not found
err:module:import_dll Library s2render.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\MemMgr.dll") not found
err:module:import_dll Library MemMgr.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\stlport.5.0.dll") not found
err:module:import_dll Library stlport.5.0.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Deep Silver\\Sacred 2 Gold\\system\\sacred2.exe" failed, status c0000135
```I want to mess around with it since it doesn't work on my Windows 7 (or works poorly).

Anyone have any ideas on what i should do?

EDIT: Sorry forgot to add:

I'm using Ubuntu 10.04

System specs:
AMD 3000+ 64 bit @2.2GHz
1.5 GB RAM
GeForce 9600 GT

(So it should run the game since it's within the games system requirements)

If you need some additional information, just say what you need, this is all i can think of right now...

---

### Post by Vepar on 2010-12-09
Ok, so i downloaded msvcp80.dll and Physicsloader.dll from the net and put them in wine windows folder just to see what i'll get, and now i get this:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
wine: Call from 0x7b836a42 to unimplemented function msvcr80.dll._set_purecall_handler, aborting
wine: Unimplemented function msvcr80.dll._set_purecall_handler called at address 0x7b836a42 (thread 0009), starting debugger...
Unhandled exception: unimplemented function msvcr80.dll._set_purecall_handler called in 32-bit code (0x7b836a42).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b836a42 ESP:00bffa10 EBP:00bffa74 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b826749 EBX:7b883ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:006b2b74
Stack dump:
0x00bffa10:  00bffa94 00000008 0000003c 80000100
0x00bffa20:  00000001 00000000 7b836a42 00000002
0x00bffa30:  7ecb1d84 7ecb3444 00bffa58 f74b33e1
0x00bffa40:  00110000 00000000 0018abe0 7b883ff4
0x00bffa50:  0018abe0 0000003d 00bffa88 7b84f025
0x00bffa60:  00110000 00000000 7b8369fa 00000000
Backtrace:
=>0 0x7b836a42 in kernel32 (+0x26a42) (0x00bffa74)
  1 0x7ecb1d28 in msvcr80 (+0x11d27) (0x00bffaa4)
  2 0x7ecaf935 in msvcr80 (+0xf934) (0x00bffe00)
  3 0x005f548a in sacred2 (+0x1f5489) (0x00bffe90)
  4 0x7b855c8c call_process_entry+0xb() in kernel32 (0x00bffea8)
  5 0x7b857ebb in kernel32 (+0x47eba) (0x00bffee8)
  6 0x7bc710c0 call_thread_func+0xb() in ntdll (0x00bffef8)
  7 0x7bc71290 call_thread_entry_point+0x6f() in ntdll (0x00bfffc8)
  8 0x7bc4c19a in ntdll (+0x3c199) (0x00bfffe8)
0x7b836a42: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (131 modules)
PE      230000-  23f000    Deferred        memmgr
PE      240000-  2e2000    Deferred        stlport.5.0
PE      2f0000-  303000    Deferred        zlib1
PE      310000-  31a000    Deferred        libsigc-2.0.17
PE      320000-  32e000    Deferred        inputwrap
PE      330000-  3cb000    Deferred        tincat3
PE      3d0000-  3ef000    Deferred        nxcharacter
PE      3f0000-  3ff000    Deferred        physxloader
PE      400000-  6ff000    Export          sacred2
PE      c00000-  fa9000    Deferred        d3dx9_36
PE      fb0000- 109f000    Deferred        s2editor
PE     10a0000- 1212000    Deferred        s2core
PE     1220000- 1714000    Deferred        s2render
PE     1720000- 1783000    Deferred        nxcooking
PE     1790000- 1824000    Deferred        apex_release
PE     1830000- 1c02000    Deferred        s2logic
PE     1c10000- 1e0c000    Deferred        s2logicai
PE     26d0000- 26ea000    Deferred        rld
PE    10000000-106a8000    Deferred        orcsystem
PE    50000000-500a5000    Deferred        granny2
ELF    7b800000-7b972000    Export          kernel32<elf>
  \-PE    7b810000-7b972000    \               kernel32
ELF    7bc00000-7bcb9000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    7c420000-7c4a5000    Deferred        msvcp80
ELF    7da17000-7da1c000    Deferred        libgpg-error.so.0
ELF    7da1c000-7da25000    Deferred        librt.so.1
ELF    7da25000-7da5e000    Deferred        libdbus-1.so.3
ELF    7da5e000-7dad1000    Deferred        libgcrypt.so.11
ELF    7dad1000-7dae2000    Deferred        libtasn1.so.3
ELF    7dae2000-7dae6000    Deferred        libkeyutils.so.1
ELF    7dae6000-7daee000    Deferred        libkrb5support.so.0
ELF    7daee000-7db12000    Deferred        libk5crypto.so.3
ELF    7db12000-7dbc3000    Deferred        libkrb5.so.3
ELF    7dbc3000-7dbd4000    Deferred        libavahi-client.so.3
ELF    7dbd4000-7dbe0000    Deferred        libavahi-common.so.3
ELF    7dbe0000-7dc7b000    Deferred        libgnutls.so.26
ELF    7dc7b000-7dcaa000    Deferred        libgssapi_krb5.so.2
ELF    7dcaa000-7dcf1000    Deferred        libcups.so.2
ELF    7dd69000-7dd7d000    Deferred        xinput1_3<elf>
  \-PE    7dd70000-7dd7d000    \               xinput1_3
ELF    7dd7d000-7ddb1000    Deferred        uxtheme<elf>
  \-PE    7dd80000-7ddb1000    \               uxtheme
ELF    7ddb1000-7ddbb000    Deferred        libxcursor.so.1
ELF    7ddbb000-7ddc1000    Deferred        libxfixes.so.3
ELF    7ddc1000-7ddc5000    Deferred        libxcomposite.so.1
ELF    7ddc5000-7ddcd000    Deferred        libxrandr.so.2
ELF    7ddcd000-7ddd7000    Deferred        libxrender.so.1
ELF    7ddd7000-7dddd000    Deferred        libxxf86vm.so.1
ELF    7dddd000-7dde1000    Deferred        libxinerama.so.1
ELF    7dde1000-7dde7000    Deferred        libxdmcp.so.6
ELF    7dde7000-7ddeb000    Deferred        libxau.so.6
ELF    7ddeb000-7de05000    Deferred        libxcb.so.1
ELF    7de05000-7de0a000    Deferred        libuuid.so.1
ELF    7de0a000-7df27000    Deferred        libx11.so.6
ELF    7df27000-7df37000    Deferred        libxext.so.6
ELF    7df37000-7df50000    Deferred        libice.so.6
ELF    7df50000-7dff3000    Deferred        winex11<elf>
  \-PE    7df60000-7dff3000    \               winex11
ELF    7e043000-7e06a000    Deferred        libexpat.so.1
ELF    7e06a000-7e09a000    Deferred        libfontconfig.so.1
ELF    7e09a000-7e0af000    Deferred        libz.so.1
ELF    7e0af000-7e125000    Deferred        libfreetype.so.6
ELF    7e125000-7e129000    Deferred        libcom_err.so.2
ELF    7e129000-7e13d000    Deferred        xinput1_1<elf>
  \-PE    7e130000-7e13d000    \               xinput1_1
ELF    7e13f000-7e153000    Deferred        lz32<elf>
  \-PE    7e140000-7e153000    \               lz32
ELF    7e153000-7e1b9000    Deferred        gdiplus<elf>
  \-PE    7e160000-7e1b9000    \               gdiplus
ELF    7e1b9000-7e2f1000    Deferred        wined3d<elf>
  \-PE    7e1c0000-7e2f1000    \               wined3d
ELF    7e2f1000-7e325000    Deferred        d3d9<elf>
  \-PE    7e300000-7e325000    \               d3d9
ELF    7e325000-7e339000    Deferred        libresolv.so.2
ELF    7e33a000-7e353000    Deferred        version<elf>
  \-PE    7e340000-7e353000    \               version
ELF    7e353000-7e374000    Deferred        iphlpapi<elf>
  \-PE    7e360000-7e374000    \               iphlpapi
ELF    7e374000-7e3a1000    Deferred        ws2_32<elf>
  \-PE    7e380000-7e3a1000    \               ws2_32
ELF    7e3a1000-7e3bc000    Deferred        wsock32<elf>
  \-PE    7e3b0000-7e3bc000    \               wsock32
ELF    7e3bc000-7e3f4000    Deferred        winspool<elf>
  \-PE    7e3c0000-7e3f4000    \               winspool
ELF    7e3f4000-7e4ab000    Deferred        comdlg32<elf>
  \-PE    7e400000-7e4ab000    \               comdlg32
ELF    7e4ab000-7e50d000    Deferred        shlwapi<elf>
  \-PE    7e4c0000-7e50d000    \               shlwapi
ELF    7e50d000-7e6e5000    Deferred        shell32<elf>
  \-PE    7e520000-7e6e5000    \               shell32
ELF    7e6e5000-7e7ce000    Deferred        oleaut32<elf>
  \-PE    7e700000-7e7ce000    \               oleaut32
ELF    7e7ce000-7e842000    Deferred        rpcrt4<elf>
  \-PE    7e7e0000-7e842000    \               rpcrt4
ELF    7e842000-7e942000    Deferred        ole32<elf>
  \-PE    7e860000-7e942000    \               ole32
ELF    7e942000-7e97b000    Deferred        dinput<elf>
  \-PE    7e950000-7e97b000    \               dinput
ELF    7e97b000-7e996000    Deferred        dinput8<elf>
  \-PE    7e980000-7e996000    \               dinput8
ELF    7e996000-7e9b8000    Deferred        imm32<elf>
  \-PE    7e9a0000-7e9b8000    \               imm32
ELF    7e9b8000-7eaa3000    Deferred        comctl32<elf>
  \-PE    7e9c0000-7eaa3000    \               comctl32
ELF    7eaa3000-7eb34000    Deferred        winmm<elf>
  \-PE    7eab0000-7eb34000    \               winmm
ELF    7eb34000-7ec65000    Deferred        user32<elf>
  \-PE    7eb50000-7ec65000    \               user32
ELF    7ec65000-7ec97000    Deferred        msvcr90<elf>
  \-PE    7ec70000-7ec97000    \               msvcr90
ELF    7ec97000-7ecc6000    Export          msvcr80<elf>
  \-PE    7eca0000-7ecc6000    \               msvcr80
ELF    7ecc6000-7ed21000    Deferred        advapi32<elf>
  \-PE    7ecd0000-7ed21000    \               advapi32
ELF    7ed21000-7edac000    Deferred        gdi32<elf>
  \-PE    7ed30000-7edac000    \               gdi32
ELF    7edac000-7ee2e000    Deferred        msvcrt<elf>
  \-PE    7edc0000-7ee2e000    \               msvcrt
ELF    7ef8b000-7ef97000    Deferred        libnss_files.so.2
ELF    7ef97000-7efa1000    Deferred        libnss_nis.so.2
ELF    7efa1000-7efb8000    Deferred        libnsl.so.1
ELF    7efb8000-7efc0000    Deferred        libnss_compat.so.2
ELF    7efc0000-7efe6000    Deferred        libm.so.6
ELF    7efe6000-7efef000    Deferred        libsm.so.6
ELF    f7434000-f7438000    Deferred        libdl.so.2
ELF    f7438000-f7592000    Deferred        libc.so.6
ELF    f7593000-f75ac000    Deferred        libpthread.so.0
ELF    f75c6000-f7706000    Export          libwine.so.1
ELF    f7708000-f7726000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Deep Silver\Sacred 2 Gold\system\sacred2.exe
    0000001a    0
    00000019    0
    00000009    0 <==
0000000e services.exe
    00000016    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
0000001b explorer.exe
    0000001c    0
Backtrace:
=>0 0x7b836a42 in kernel32 (+0x26a42) (0x00bffa74)
  1 0x7ecb1d28 in msvcr80 (+0x11d27) (0x00bffaa4)
  2 0x7ecaf935 in msvcr80 (+0xf934) (0x00bffe00)
  3 0x005f548a in sacred2 (+0x1f5489) (0x00bffe90)
  4 0x7b855c8c call_process_entry+0xb() in kernel32 (0x00bffea8)
  5 0x7b857ebb in kernel32 (+0x47eba) (0x00bffee8)
  6 0x7bc710c0 call_thread_func+0xb() in ntdll (0x00bffef8)
  7 0x7bc71290 call_thread_entry_point+0x6f() in ntdll (0x00bfffc8)
  8 0x7bc4c19a in ntdll (+0x3c199) (0x00bfffe8)
wine: Call from 0x7b836a42 to unimplemented function msvcr80.dll._set_purecall_handler, aborting
wine: Call from 0x7b836a42 to unimplemented function msvcr80.dll._set_purecall_handler, aborting
```

Help please? :D

---

### Post by Vepar on 2010-12-09
Ok, i installed winetricks and installed all the necesary dll's, the game runs now but very slowly and has no sound (override for openal32 is not working)...

---

### Post by Vepar on 2010-12-10
Still couldn't fix audio and performance issues... Anyone?

---

