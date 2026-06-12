---
title: "Help: Game tries to load from a CD."
date: 2010-09-26
forum: Wine
---

### Post by bullet311 on 2010-09-26
I recently downloaded Swat 4 (legally)(yes, swat4 its a good game) and am trying to use wine to play it. I left everything at defaults hoping it would work. (yeah right)  The install went completely fine and smooth. But whenever I choose the option either autorun.exe or swat4.exe it gives me this.. 

"No Cd-Rom/Dvd-Rom found!"

Somehow I need to change the path, because I have all the game files necessary loaded into the same folder. I'm unfamiliar with Wine. 

Any help? Thanks.

EDIT: 

```
wine Swat4.exe
``````
err:module:import_dll Library ALAudio.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:import_dll Library SwatAIAwareness.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:import_dll Library AICommon.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:import_dll Library Core.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:import_dll Library Engine.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:import_dll Library Window.dll (which is needed by L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sierra\\SWAT 4\\Swat4.exe" failed, status c0000135

```

All those dll libraries are located in Swat4/Content/System
So its just loading it from the wrong place. How to redirect it idk.

---

