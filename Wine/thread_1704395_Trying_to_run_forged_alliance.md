---
title: "Trying to run forged alliance"
date: 2011-03-10
forum: Wine
---

### Post by ELD on 2011-03-10
Upon trying to run supreme commander forged alliance i get this:
> 
liam@liamspc:~$ wine '/home/liam/.wine/dosdevices/c:/Program Files/THQ/Gas Powered Games/Supreme Commander - Forged Alliance/bin/ForgedAlliance.exe' 
err:module:import_dll Library X3DAudio1_2.dll (which is needed by L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander - Forged Alliance\\bin\\ForgedAlliance.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\THQ\\Gas Powered Games\\Supreme Commander - Forged Alliance\\bin\\ForgedAlliance.exe" failed, status c0000135


No idea what it means.

---

### Post by cogadh on 2011-03-10
It means you probably need to change directories to the game's install directory, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/THQ/Gas\ Powered\ Games/Supreme\ Commander\ -\ Forged\ Alliance/bin
wine ForgedAlliance.exe
```

However, if that still doesn't work, you might want to check out the AppDB page for the game, it has some additional "how-to" info on it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9728)

---

