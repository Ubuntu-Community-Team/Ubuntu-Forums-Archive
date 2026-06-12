---
title: "sh winetricks msxml4 errors"
date: 2009-12-30
forum: Wine
---

### Post by YarDYar on 2009-12-30
Hi All,

I want to run MathCAD 14 on 9.04 using wine so I can rewrite my calculations in NumPy/SciPy/sage. WineHQ says I need to install msxml4 in order to install it. 

When I run winetricks msxml4, I get the following errors:
```

err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 1 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values

```

I've uninstalled wine a few times (deleting my .local and .config files each time), and tried running the winetricks scripts in different orders, but I always end up with the error: 
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination

Any help/advice would be appreciated.

Yar

---

### Post by YarDYar on 2009-12-31
I tried downloading msxml4.dll from a website and register it using:
regsvr32 c:\windows\system32\msxml4.dll
It didn't work.

Then I downloaded the msmxl4 install exe from microsoft. 
[http://www.microsoft.com/downloads/details.aspx?FamilyId=021E12F5-CB46-43DF-A2B8-185639BA2807&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyId=021E12F5-CB46-43DF-A2B8-185639BA2807&displaylang=en)

When I ran the exe I got the error message:
```

fixme:advapi:LookupAccountNameW (null) L"username" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"username" 0x132810 0x33f87c 0x1320b0 0x33f880 0x33f874 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination

```

---

### Post by k@e on 2010-01-01
I think this is what you want to install: [http://www.microsoft.com/downloads/details.aspx?familyid=3144b72b-b4f2-46da-b4b6-c5d7485f2b42&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=3144b72b-b4f2-46da-b4b6-c5d7485f2b42&displaylang=en)

EDIT: I just tested it and it somehow does not work, although it previously did. They must have updated the installer and now it does not work anymore.

---

### Post by YarDYar on 2010-01-03
I upgraded to Wine 1.1.35, and after a couple of tries msxml4 installed using winetricks with no errors.
Now my MathCAD install gets a bit furthur before getting the same xml parsing error. That's probably specific to my ripped copy of MathCAD 14.

---

