---
title: "Steam in wine using winetricks exiting after connecting."
date: 2010-12-13
forum: Wine
---

### Post by Duffadash on 2010-12-13
I have installed steam using wine and winetricks, using the howto found here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=58335](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=58335)
Yet, every time I start steam everything works fine until the "conencting" screen appears, which stays on the screen for a few seconds, before steam closes.
I've tried installing steam using winetricks, vanilla wine and playonlinux, but the same thing always happens.
I use Ubuntu 10.10

This is what the terminal writes when i run Steam.
```
duffadash@Artemis:~$ wine 'C:/program files/steam/steam'
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 2, 0x32d334, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 3, 0x32d338, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 4, 0x32d33c, 4) stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
CellID: CSDS returned 172 servers.
CellID: Connecting to 194.124.229.16:27031. . .
CellID: Connect to 194.124.229.16:27031 took 55 MS
CellID: Nothing beat our old best time of 41 MS
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 2, 0x32d804, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 3, 0x32d808, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 4, 0x32d80c, 4) stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x4af12c0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x425bfc8)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 2, 0x32d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 3, 0x32d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 4, 0x32d814, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 2, 0x32d2e4, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 3, 0x32d2e8, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 4, 0x32d2ec, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 2, 0x32d94c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 3, 0x32d950, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 4, 0x32d954, 4) stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
duffadash@Artemis:~$ 

```

---

### Post by divide_by_zero on 2011-01-09
I am having a very similar problem. I use Debian sid ("squeeze"? I don't know, hate those stupid names). My wine version is wine-1.1.42, installed from the Debian packages provided at winehq.

It seems Steam installed correctly. I used the same instructions from the OP. The login window shows up, it seems everything is fine, but then the window disappears, and I only get these messages in the terminal:

```
nlw@spirit:~$ wine C:\\Arquivos\ de\ Programas\\Steam\\Steam.exe
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 20/02/2011, dlt (d/m/y): 16/10/2011
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 2, 0x33d33c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 3, 0x33d340, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 4, 0x33d344, 4) stub
CellID: CSDS returned 174 servers.
CellID: Connecting to 79.141.165.4:27031. . .
CellID: Connect to 79.141.165.4:27031 took 252 MS
CellID: Nothing beat our old best time of 140 MS
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 2, 0x33d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 3, 0x33d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 4, 0x33d814, 4) stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1bebd0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x43bbfc8)
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 2, 0x33d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 3, 0x33d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 4, 0x33d814, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 2, 0x33d2e4, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 3, 0x33d2e8, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 4, 0x33d2ec, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 2, 0x33d94c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 3, 0x33d950, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 4, 0x33d954, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 2, 0x33d51c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 3, 0x33d520, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 4, 0x33d524, 4) stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
nlw@spirit:~$ fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 20/02/2011, dlt (d/m/y): 16/10/2011

nlw@spirit:~$ 

```

Any ideas?

---

