---
title: "CQG Trader Installation Problem"
date: 2009-06-03
forum: Wine
---

### Post by zhangmaster12 on 2009-06-03
Hello everybody. Im trying to install CQG trader on Ubuntu Netbook Remix. Its a trading program. 

When I first tried to install, a window popped up saying that I need to install .NET framework. So, following the manual install directions on WineHq, I successfully installed .NET 2.0

After that, when trying to install CQG.msi, a command promp window that says msiexec.exe would pop up, and after that,  nothing would happen. I thought maybe it was taking a long time to load, waited half and hour and still nothing happened. 

Then I tried installing through the terminal so I could see the actual error message and post it here so maybe someone can help.

qin@qin-laptop:~/Documents$ wine msiexec /i cqg..msi
err:msi:copy_package_to_temp failed to copy package L"cqg..msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"cqg..msi"
qin@qin-laptop:~/Documents$ wine msiexec /i Cqg.msi
fixme:advapi:LookupAccountNameW (null) L"qin" (nil) 0x32f87c (nil) 0x32f880 0x32f874 - stub
fixme:advapi:LookupAccountNameW (null) L"qin" 0x12b128 0x32f87c 0x12bd98 0x32f880 0x32f874 - stub
qin@qin-laptop:~/Documents$ fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
Debug: --------RunSetup STARTED-------
Debug: args[0] = C:\ 
Debug: Installation was started manually
Debug: ProcesId = C:\ 
Warning: Can't parse ProcesId comand line argument!
Exception: System.FormatException: Input string was not in a correct format.
   at System.Number.StringToNumber(String str, NumberStyles options, NumberBuffer& number, NumberFormatInfo info, Boolean parseDecimal)
   at System.Number.ParseInt32(String s, NumberStyles style, NumberFormatInfo info)
   at CQGTAndAutoUpgradeInstallation.RunSetup.Main(String[] args)
Debug: ---- Comand line format is:
Debug: ---- CQGTAndAutoUpgradeInstallation.exe ProcesId TARGETDIR
Debug: ---- 
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub


Thanks guys. Help would be highly appreciated. Hopefully this means I'm doing something wrong, not its impossible to install CQG trader. Vmware isn't an option either, because I'm running on a 900A without an upgraded SSD.

---

### Post by zhangmaster12 on 2009-06-04
Anyone? Oh well, bump I guess.

---

