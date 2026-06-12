---
title: "WoW under Wine"
date: 2011-04-16
forum: Wine
---

### Post by claythearc on 2011-04-16
i tried to run WoW under wine, the installer worked fine, patched all through the game (with the exception of the non-critical updates), I tried to run Launcher.exe after patching, it works fine to run the launcher - but the intro movie started and i pressed escape to skip, it gave me and error so i tried again.. after the 5th & 6th tries.. it errors out, konsole output is attached below - the first little bit is where i tried to install vc 2005 in hopes it would fix. but it keeps erroring out, any suggestions?

```

clay@clay-Inspiron-1520:~$ $ winetricks vcrun2005sp1
$: command not found
clay@clay-Inspiron-1520:~$ winetricks vcrun2005sp1
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x135930, filter=0xc9e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x78e8b4): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x78e87c): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x126c58,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
Executing w_do_call vcrun2005
Executing load_vcrun2005
Executing mkdir -p /home/clay/.cache/winetricks/vcrun2005
Downloading http://download.microsoft.com/download/6/B/B/6BB661D6-A8AE-4819-B79F-236472F6070C/vcredist_x86.exe to /home/clay/.cache/winetricks/vcrun2005
--2011-04-16 11:39:40--  http://download.microsoft.com/download/6/B/B/6BB661D6-A8AE-4819-B79F-236472F6070C/vcredist_x86.exe
Resolving download.microsoft.com... 65.55.87.103, 65.55.87.111
Connecting to download.microsoft.com|65.55.87.103|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2745256 (2.6M) [application/octet-stream]
Saving to: `vcredist_x86.exe'

100%[==============================================================================================================>] 2,745,256   1.77M/s   in 1.5s    

2011-04-16 11:39:42 (1.77 MB/s) - `vcredist_x86.exe' saved [2745256/2745256]

Using native,builtin override for following DLLs: msvcr80
Executing winetricks_early_wine regedit C:\windows\Temp\_vcrun2005\override-dll.reg
Executing wine vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\users\\clay\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\users\\clay\\Temp\\IXP001.TMP\\" 00000000
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"Microsoft.VC80.ATL,type=\"win32\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"Microsoft.VC80.CRT,type=\"win32\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"Microsoft.VC80.MFC,type=\"win32\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"Microsoft.VC80.MFCLOC,type=\"win32\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"Microsoft.VC80.OpenMP,type=\"win32\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"policy.8.0.Microsoft.VC80.ATL,type=\"win32-policy\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"policy.8.0.Microsoft.VC80.CRT,type=\"win32-policy\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"policy.8.0.Microsoft.VC80.MFC,type=\"win32-policy\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"policy.8.0.Microsoft.VC80.MFCLOC,type=\"win32-policy\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:sxs:cache_QueryAssemblyInfo 0x410448, 0x00000002, L"policy.8.0.Microsoft.VC80.OpenMP,type=\"win32-policy\",version=\"8.0.50727.4053\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f9b8
fixme:msi:ITERATE_RemoveExistingProducts remove L"0"
clay@clay-Inspiron-1520:~$ cd /home
clay@clay-Inspiron-1520:/home$ cd ./clay
clay@clay-Inspiron-1520:~$ ls
Asking Alexandria Full Discography     jagex_runescape_preferences2.dat  Pictures          vmware
CLIPINF                                jagex_runescape_preferences.dat   Public            VMWare Workstation 7.1.4 Build 385536
Desktop                                kdenlive                          RIFT Game         Windows 7 AIO - x32x64 [Activated]
Documents                              Millionaires Collection           Templates         WoW-4.0.0-WOW-enUS-Installer.exe
Downloads                              Music                             tersus-workspace
God² - Are You Being Saved? [DUBSTEP]  PHP Bot                           Videos
clay@clay-Inspiron-1520:~$ cd "./.wine/
> ls
> ^C
clay@clay-Inspiron-1520:~$ cd "./.wine/"
clay@clay-Inspiron-1520:~/.wine$ ls
dosdevices  drive_c  reg11830000.tmp  system.reg  userdef.reg  user.reg  winetricks.log
clay@clay-Inspiron-1520:~/.wine$ cd ./drive_c
clay@clay-Inspiron-1520:~/.wine/drive_c$ ls
Program Files  users  windows
clay@clay-Inspiron-1520:~/.wine/drive_c$ cd ./P*
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files$ ls
Apple Software Update  Bonjour  Common Files  Internet Explorer  iPod  iTunes  Magic Workstation  QuickTime  World of Warcraft
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files$ cd ./Wo*
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ ls
Battle.net.dll        Data             Errors     Launcher.exe                 msvcr80.dll  unicows.dll   Wow.exe   WTF
Blizzard Updater.exe  dbghelp.dll      ijl15.dll  Logs                         Patch.html   Updates       WoW.mfil
Cache                 divxdecoder.dll  Interface  Microsoft.VC80.CRT.manifest  Repair.exe   WowError.exe  WoW.tfil
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ kate Config.wtf
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/clay/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kate(15294)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15294)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
^Z
[1]+  Stopped                 kate Config.wtf
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ cd ./WTF
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ ls
Launcher.WTF  RunOnce-Installer.wtf  RunOnce.wtf
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ kate RunOnce.wtf
kate(15437)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15437)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/clay/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
[1]+  Killed                  kate Config.wtf  (wd: ~/.wine/drive_c/Program Files/World of Warcraft)
(wd now: ~/.wine/drive_c/Program Files/World of Warcraft/WTF)
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ kate Launcher.wtf
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/clay/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kate(15440)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15440)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ ls
Launcher.WTF  RunOnce-Installer.wtf  RunOnce.wtf
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ kate Launcher.WTF
kate(15445)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15445)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/clay/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ ls
Launcher.WTF  RunOnce-Installer.wtf  RunOnce.wtf
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ kate RunOnce-Installer.wtf
kate(15534)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15534)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/clay/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kate(15534)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(15534)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/clay/.local/share/mime/magic"
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft/WTF$ cd ..
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ ls
Battle.net.dll        Data             Errors     Launcher.exe                 msvcr80.dll  unicows.dll   Wow.exe   WTF
Blizzard Updater.exe  dbghelp.dll      ijl15.dll  Logs                         Patch.html   Updates       WoW.mfil
Cache                 divxdecoder.dll  Interface  Microsoft.VC80.CRT.manifest  Repair.exe   WowError.exe  WoW.tfil
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ wine ./Wow.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x1359d8, filter=0xc9e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x78e8b4): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x78e87c): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x126c58,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:process:GetLogicalProcessorInformation (0x32f640,0x32fc40): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:process:GetLogicalProcessorInformation (0x148bfac,0x148c5ac): stub
fixme:process:GetLogicalProcessorInformation (0x148bfd8,0x148c5d8): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x32f468,0x32fa68): stub
fixme:process:GetLogicalProcessorInformation (0x32f468,0x32fa68): stub
fixme:process:GetLogicalProcessorInformation (0x158e390,0x158e990): stub
archive Data\enUS\base-enUS.MPQ opened
Unable to read archive hash/block table: "Data/Cache/SoundCache-3.MPQ"
archive Data/Cache/SoundCache-3.MPQ opened for writing
Unable to read archive hash/block table: "Data/Cache/SoundCache-2.MPQ"
archive Data/Cache/SoundCache-2.MPQ opened for writing
Unable to read archive hash/block table: "Data/Cache/SoundCache-1.MPQ"
archive Data/Cache/SoundCache-1.MPQ opened for writing
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/enUS/patch-enUS-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/enUS/patch-enUS-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/enUS/patch-enUS-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/enUS/patch-enUS-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/enUS/patch-enUS-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/enUS/patch-enUS-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data\art.MPQ opened
archive Data\world.MPQ opened
archive Data\sound.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f120,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5e8,0x00000000), stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x32f198,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f05c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a1590,0x1a1490): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a1590,0x1a1490): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f86c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f184,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f048,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1fc,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation (0x198e390,0x198e990): stub
fixme:process:GetLogicalProcessorInformation (0x198e390,0x198e990): stub
err:d3d:loadNumberedArrays >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading numbered arrays @ state.c / 4308
fixme:dbghelp:i386_stack_walk new PC=7bc9fff4 different from Eip=7b86a155
clay@clay-Inspiron-1520:~/.wine/drive_c/Program Files/World of Warcraft$ 



```

---

### Post by cwwilson721 on 2011-04-16
You have searched this forum and read:
[LIST]
[*][This sticky on how to ask for help]("http://ubuntuforums.org/showthread.php?t=885111")
[*][This post on HOWTO Run WoW on wine]("http://ubuntuforums.org/showthread.php?t=579378&highlight=howto+wow")
[/LIST]
Right?

Because, if you did, you would know what we need: Hardware (Video), wine version, etc...

And when you have your information, why not search the forum one more time for "WoW+<Videochip name>". (Because it's been asked and answered MANY times)

---

