---
title: "Runes of magic, visual C++ error"
date: 2009-12-14
forum: Wine
---

### Post by Denieru on 2009-12-14
Hi!

I've downloaded and installed Runes Of Magic using Wine 1.33, but when I'm launching the game I get this error:

[IMG]http://data.fuskbugg.se/skalman01/visualfel.png[/IMG]

I followed the instructions on WineHQ and used
```
sh winetricks vcrun2005
```
but it will still not work.

Anyone know what to do? If so, then please post! :)

Thanks in advance, 
Denieru

---

### Post by beastrace91 on 2009-12-14
So the game installed properly? I see you've been to the [AppDB page](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16051) for the game, did you use "multiple file downloads" to install the game as it suggests?

Regards,
~Jeff

---

### Post by Denieru on 2009-12-14
> **beastrace91 said:**
> So the game installed properly? I see you've been to the [AppDB page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16051") for the game, did you use "multiple file downloads" to install the game as it suggests?

Regards,
~Jeff
Yeah, the game installs without problems.

I did not use "multiple file downloads" yesterday when I tried, but today I uninstalled the game and reinstalled it with "multiple file downloads", but the problem still exists.

Thanks,
Denieru

EDIT: Tried to install and launch it via PlayOnLinux, same problem, well not exactly the same, when I'm launching it via the launcher it just crashes.

---

### Post by Denieru on 2009-12-16
Tried running it through terminal, here's the message I'm getting:

```
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50608.0 / 8.0.50727.762
fixme:actctx:parse_manifest_buffer failed to parse manifest L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\denieru\\.PlayOnLinux\\wineprefix\\RunesOfMagic\\drive_c\\Program Files\\Runes of Magic\\client.exe" failed, status c0000142

```

---

