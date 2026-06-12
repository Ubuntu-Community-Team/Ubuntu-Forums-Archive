---
title: "[SOLVED] Lord of the rings issue (unresolved)"
date: 2008-12-16
forum: Wine
---

### Post by zer0theher0 on 2008-12-16
ALRIGHT. So the walk through went smoothly. I decided to just go with the text based installer so it'd show me the errors I am having.
I run lotrolauncher.script and it goes through the boot up text welcome launcher script dialog blah blah blah.
Then it hits the part asking DO YOU WANT TO UPDATE y/N?: I hit Y
and it actually starts updating which is very very good seeing as it was saying it was already updated and no more were available before.
then as it starts updating it displays this:

```


Do you want to check for updates (y/N)? y
Checking for updates...
Connecting to patch.lotro.com:80
Checking files...files to patch: 0 bytes to download: 0
Patching files:
Connecting to patch.lotro.com:80
Checking files...files to patch: 0 bytes to download: 0
Patching files:
Connecting to patch.lotro.com:80
checking data...fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Turbine\\The Lord of the Rings Online\\TTEPatchClient.dll") not found
Failed to check data: Module not found(0x8007007e)
```

now i thought i had heard of that msvrc80.dll file before so i looked in winetricks and there it is under vcrun2005 so i figured hey i must have missed it when i installed it or something. So i click the box to install it and here is the output craziness that ensues:

```


Executing wine /home/happi/.winetrickscache/vcrun2005/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"happi" (nil) 0x33f77c (nil) 0x33f780 0x33f774 - stub
fixme:advapi:LookupAccountNameW (null) L"happi" 0x130208 0x33f77c 0x13f928 0x33f780 0x33f774 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e1ff698 0x7e1ff67c (nil) (nil)
Note: command 'wine /home/happi/.winetrickscache/vcrun2005/vcredist_x86.exe' returned status 194.
```  Aborting.

now what the hell that means i havn't the foggiest.

i'm so close! please help!
original post by pandayanyan common lets help the guy out please.

---

### Post by ajackson on 2008-12-17
People have been trying to help him out, in the thread he originally posted this in. Which leads to the question, why start another thread with the same problem in it?

---

