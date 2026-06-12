---
title: "Getting Runes of Magic to run"
date: 2009-11-10
forum: Wine
---

### Post by DanielJackins on 2009-11-10
Hello, I'm trying to get Runes of Magic to run but I get the following error messages when I try to run it:

```
desiree@desiree-desktop:~/.wine/drive_c/Program Files/Runes of Magic$ wine Runes\ of\ Magic.exe -game -opengl
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
desiree@desiree-desktop:~/.wine/drive_c/Program Files/Runes of Magic$ err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Runes of Magic\\xerces-c_2_8.dll") not found
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"C:\\Program Files\\Runes of Magic\\Client.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Runes of Magic\\Client.exe" failed, status c0000135

```

I am running version 1.1.32 of wine on Ubuntu 9.10 64-bit.

Any help? Thanks

---

### Post by coldReactive on 2009-11-10
Did you try uninstalling, then reinstalling?

Oh, and don't update via the updater, it won't work (even though you HAVE to update to play.) You'll eventually not be able to start ROM.

---

### Post by DanielJackins on 2009-11-10
How do I update then?

---

### Post by coldReactive on 2009-11-10
> **DanielJackins said:**
> How do I update then?

You don't, because the only way to update is through the updater.

---

### Post by omgitsmit on 2009-11-18
I've had a tutorial on getting RoM running on Ubuntu for awhile now, just recently reposted a how-to for those who are having the "No EULA / Login" display issue, a quick registry hack will get you up and running in no time! :)

[http://timashley.me/node/265](http://timashley.me/node/265)

---

