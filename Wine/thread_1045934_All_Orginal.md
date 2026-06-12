---
title: "All Orginal"
date: 2009-01-20
forum: Wine
---

### Post by LinLux451 on 2009-01-20
I'm a hardcure ubuntu user for about 10 months now, all hardy, and single boot. I've found workarounds for many things including iPods, File sharing, FLASH!, but I really need UBU help right now. I have an old windows POS lying around for one purpose, and one purpose only. To run
King's School's Cessna "Cleared for takeoff" private pilot course. If I can get this program to run on Wine, I get a new power mac. I have tried everything, I'm not a great wine guy  but I try, and any help would greatly be appreciated.

Output on Wine when using shortcut on terminal
```

tom@LAPTOP:~$ wine '/home/tom/Desktop/Private Pilot.desktop' 
wine: could not load L"Z:\\home\\tom\\Desktop\\Private Pilot.desktop": Bad EXE format for 
```

Code of program launcher
```

env WINEPREFIX="/home/tom/.wine" "wine C:\windows\command\start.exe" C:\CessnaMM\PPilotCD\ppHome.tbk C:\windows\ASYM\RUNTIME\TB50RUN.EXE C:\CessnaMM\PPilotCD\ppHome.tbk
```

this is the only installed program on wine. I'm running a Hardy box with Mobile Centrino, and 512 RAM. The latter really prevents me from virtual boxing it. and please, please, please oh please, don't let me resort to dual booting. Thanks in advance from a frustrated linux user

-Tom

---

### Post by cogadh on 2009-01-21
I'm assuming that just clicking on the shortcut did not work. You don't use the shortcut in the terminal, if you are going to use the terminal, you need to run the actual executable, like "wine foo.exe". In this case, it appears that you are running what might be a Toolbook application, which might be problematic. I'm not sure if this will actually work, but doing this in the terminal might be more productive:
```
cd .wine/drive_c/CessnaMM/PPilotCD
wine start ppHome.tbk
```

---

