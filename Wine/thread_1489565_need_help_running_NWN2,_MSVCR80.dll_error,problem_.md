---
title: "need help running NWN2, MSVCR80.dll error,problem installing vcrun2005sp1"
date: 2010-05-21
forum: Wine
---

### Post by Bad_Andy on 2010-05-21
I'm hitting a wall when trying to play NWN2 under wine 1.1.44 using ubuntu 10.04 LTS

when I try to run nwn2.exe it hangs, the terminal output says ""MSVCR80.dll" failed to initialize"

full output is here:

```
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50608.0
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Atari\\Neverwinter Nights 2\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
fixme:actctx:parse_assembly_elem wrong version for assembly manifest: 8.0.50727.762 / 8.0.50608.0
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Atari\\Neverwinter Nights 2\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Atari\\Neverwinter Nights 2\\nwn2.exe" failed, status c0000142

```

I have tried to fix this by renaming my wine folder to create a clean prefix and reinstalling the necessary files using winetricks to run nwn2. vcrun2005, d3dx9, dotnet20 and vcrun2005trial all seem to install correctly. When I try to install vcrun2005sp1 I get the following error...terminal output is too long to copy here but I believe this is the relevant part:

```
ixme:advapi:LookupAccountNameW (null) L"leecarey" (nil) 0x33e860 (nil) 0x33e864 0x33e858 - stub 
fixme:advapi:LookupAccountNameW (null) L"leecarey" 0x23ee750 0x33e860 0x23ef040 0x33e864 0x33e858 - stub 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
fixme:msi:MsiGetMode unimplemented run mode: 0 
fixme:msi:ACTION_ValidateProductID partial stub: template L"77718<````=````=````=````=`````>@@@@@" key L"JWFMGDGVMWKPVD39RX6PW2GQY" 
err:module:import_dll Library sqdedev.DLL (which is needed by L"C:\\users\\leecarey\\Temp\\msicbeb.tmp") not found 
err:msi:ACTION_CallDllFunction failed to load dll L"C:\\users\\leecarey\\Temp\\msicbeb.tmp" (126) 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet 
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 357 ignored L"MsiAssembly" table values 
fixme:msi:ITERATE_RemoveODBCDataSource Use ODBCSourceAttribute table 
fixme:odbc:SQLConfigDataSourceW (nil) 6 L"Microsoft Access Driver (*.mdb)" L"DSN=Xtreme Sample Database 2005" 
fixme:odbc:SQLConfigDataSourceW L"DSN=Xtreme Sample Database 2005" 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
err:cabinet:FDICopy PFDI_OPEN returned zero for C:\windows\Installer\_138_RTL_x86_enu_ATL_MFC_Include.cab. 
err:msi:extract_cabinet FDICopy failed 
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"_138_RTL_x86_enu_ATL_MFC_Include.cab" 
err:msi:ITERATE_Actions Execution halted, action L"InstallFiles" returned 1603 
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603 
------------------------------------------------------ 
Note: command 'wine VS80sp1-KB971090-X86-INTL.exe' returned status 69. Aborting. 
------------------------------------------------------ 
```

not sure what else to do at this point, any help is greatly appreciated, thanks.

---

### Post by cogadh on 2010-05-21
First off, don't use the QUOTE tags when posting terminal output, use the CODE tags, it will eliminate that annoying smiley problem and keeps it formatted properly (which is really unformatted).

I think where you went wrong was installing vcrun2005trial, that wasn't necessary at all. You should only need to install dotnet20, vcrun2005, vcrun2005sp1 and dx9 to get the game running. According to Wine's AppDB, there are also a few specific settings you may need to configure (listed at the bottom of the page):
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118)

---

### Post by Bad_Andy on 2010-05-21
quotes fixed, thanks

I agree that vcrun2005trial may be causing a problem, the thing I'm stuck on is that winetricks requires you to install vcrun2005trial in order to install sp1, if you try to install sp1 without trial it refuses.

I am using all the .dll overrides and have tried the registry edits noted there, although the latter aren't necessary as they seem to only be related to the "your video has less than 128 MB of texture memory" bug.

---

### Post by Bad_Andy on 2010-05-23
got it working now by creating a new wine prefix and resinstalling the game. Also, it seems vcrun2005sp1 and therefore vcrun2005trial are not needed and I think the trial may be what caused the problem

I still have a minor bug where I'm unable to change the resolution ingame to anything but 960x600, if anyone has ideas about how to fix that let me know,.

---

### Post by dino99 on 2010-05-23
update your system, 1.2rc1 is out :P

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

[http://appdb.winehq.org/appview.php?iAppId=4118](http://appdb.winehq.org/appview.php?iAppId=4118)

---

