---
title: "Party poker, poker office - blank windows"
date: 2010-05-26
forum: Wine
---

### Post by jaansson on 2010-05-26
Hello

I just managed to isntall party poker after creating a new wineprefix. Only problem is that when I start up the client, the windows are blank/white. I can't see the login or tables list. I can see the frame of the site though, so it seem like I just can't see the interactive parts. On my first start-up it said something like there was a javascript fail or something and I could chose yes or no. I pressed yes. Never got the window after that. And when I exit the program, a pop-up window comes up (just as it's supposed to) and shows me a piece of advertisement for a tournament. And I CAN click that link! Usually, these kind of picture link things doesn't work for me in wine, but this one actually does. So it feels like I'm half way there.

Here comes some info:

Wine version: 1.2rc-1

Terminal output:

```
danne@danne-laptop:~$ env WINEPREFIX="/home/danne/.wine-two" wine C:\\Program\ Files\\PartyGaming\\PartyGaming.exe -P=PartyPoker
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:wbemprox:wbem_locator_ConnectServer 0x12bb70, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32f44c)
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:GetOldestEventLogRecord (0xcafe4242,0x32dcc4) stub
fixme:advapi:GetNumberOfEventLogRecords (0xcafe4242,0x32dcc0) stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x0000000a,0xffffffff,0x158eb28,0x00002800,0x32dcc8,0x32dcb8) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Application Error"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000019,0x5edd80,0xa504f0): stub
err:eventlog:ReportEventW L"pprekop.exe"
err:eventlog:ReportEventW L"4.2.0.172"
err:eventlog:ReportEventW L"ole32.dll"
err:eventlog:ReportEventW L"5.1.2600.2182"
err:eventlog:ReportEventW L"10017bed"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:05 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:05 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:05 GMT")
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:GetOldestEventLogRecord (0xcafe4242,0x32e408) stub
fixme:advapi:GetNumberOfEventLogRecords (0xcafe4242,0x32e404) stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x0000000a,0xffffffff,0x1590f40,0x00002800,0x32e40c,0x32e3fc) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
The file was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x4198 options=0x00000014)
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x4204 options=0x00000014)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (0): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (1252): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (0): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (1252): STUB
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xb810 options=0x00000014)
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:11 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:11 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Fri, 27-May-2011 01:25:11 GMT")
The file 'data' was opened
The file 'data' was opened
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 1
fixme:wininet:INET_QueryOption Stub for 66
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:INET_QueryOption Stub for 66
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:msimtf:DllGetClassObject ({50d5107a-d278-4871-8989-f4ceaaf59cfc} {00000001-0000-0000-c000-000000000046} 0x32cdc4)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {50d5107a-d278-4871-8989-f4ceaaf59cfc} could be created for context 0x401
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_SERVER (10): STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:msxml:xmlcf_QueryInterface interface {342d1ea0-ae25-11d1-89c5-006008c3fbfc} not implemented
fixme:msxml:httprequest_QueryInterface Unsupported interface {bb1a2ae1-a4f9-11cf-8f20-00805f2cd064}
fixme:msxml:httprequest_QueryInterface Unsupported interface {cb5bdc81-93c1-11cf-8f20-00805f2cd064}
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:InternetLockRequestFile STUB
err:wininet:NETCON_secure_connect SSL_connect failed: 12055
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:InternetLockRequestFile STUB
The file 'data' was opened
The file 'data' was opened
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=www1.partypoker.com length=19
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:wininet:InternetCanonicalizeUrlW Unhandled flags 0x04000000
err:wininet:NETCON_secure_connect SSL_connect failed: 12055
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xd434 options=0x00000014)
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xd4b8 options=0x00000014)
fixme:jscript:JScript_SetScriptState unimplemented state 3
fixme:jscript:JScript_SetScriptState unimplemented state 3
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:jscript:JScript_SetScriptState unimplemented state 3
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:jscript:JScript_SetScriptState unimplemented state 3

```

Wine configuration:

OS version - Windows XP

Library overrides: Jscript - builtin, native
                   msi - builtin, native
                   msiexec.exe - builtin, native

Sound settings: standard - ALSA, full, 44100, 16

Graphics settings: standard

Registry edits: none


Other Wine applications: winetricks - 7zip, adobeair, corefonts, dotnet20, flash, fontfix, gdiplus, ie6, jet40, msi2, msscript, msxml6, pdh, shockwave, vbrun6, vcrun2005, vjrun, allfonts, allcodecs.


Might have missed one or two, but that's the ones that I remember. Is there a way to see what I have installed? Should also say that I've got the same problem with Poker Office. For some weird reason when I click the poker office desktop icon it starts and gets blank. When I copy the target of the shortcut to the terminal, it just gives me

```
danne@danne-laptop:~$ env WINEPREFIX="/home/danne/.wine-two" wine C:\\Program\ Files\\PokerOffice\\PokerOffice.exe \ \"C:\\Program\ Files\\PokerOffice\"
fixme:msg:pack_message msg 138 (WM_CTLCOLORSTATIC) not supported yet
err:win:DefWindowProcW called for other process window 0x10050

```

and then nothing more happens.

[[IMG]http://img263.imageshack.us/img263/8903/skrmbildm.th.png[/IMG]](http://img263.imageshack.us/i/skrmbildm.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by jaansson on 2010-05-27
That Jscript fail thing that I mentioned, here is what that window says:

```
An error has occurred in the script on this page.

Line: 979
Char: 5
Error: Automation server can't create object.
Code: 0
URL: http://pam.iivt.com/content/articles/real/en_US/167056.html

Do you want to continue running scripts on this page?

Yes/No
```

I pressed yes.

Btw, I can see the login. Thought that was the one that came up in the start, but when I clicked the log in button, I got a pop up to login, and it actually worked! But everything else is still blank.

---

### Post by asdfoo on 2010-05-28
hell of a lot of overrides and nonstandard stuff you have installed there

what happens if you just winetricks gecko and then try to use it? (make sure you're using the latest version of wine)

---

### Post by jaansson on 2010-05-28
Thanks for the tip! Didn't work though. Yes, I thought it was quite a lot stuff installed there as well, so I created a new wineprefix just for party poker, where I first installed IE6. Didn't really work. The program tried to start but couldn't connect I then installed vcrun2003 and vcrun6. That made the program start up, just like the first wineprefix. And gecko didn't really seem to make too much of a difference.

Anyway, here is what I got after gecko:

```
danne@danne-laptop:~$ env WINEPREFIX="/home/danne/.wine-party" wine C:\\Program\ Files\\PartyGaming\\PartyGaming.exe -P=PartyPoker
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:wbemprox:wbem_locator_ConnectServer 0x12c5b8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32f44c)
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:GetOldestEventLogRecord (0xcafe4242,0x32dcc4) stub
fixme:advapi:GetNumberOfEventLogRecords (0xcafe4242,0x32dcc0) stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x0000000a,0xffffffff,0x158eb28,0x00002800,0x32dcc8,0x32dcb8) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Application Error"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000019,0x5edd80,0xa50610): stub
err:eventlog:ReportEventW L"pprekop.exe"
err:eventlog:ReportEventW L"4.2.0.172"
err:eventlog:ReportEventW L"ole32.dll"
err:eventlog:ReportEventW L"5.1.2600.2182"
err:eventlog:ReportEventW L"10017bed"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:GetOldestEventLogRecord (0xcafe4242,0x32e408) stub
fixme:advapi:GetNumberOfEventLogRecords (0xcafe4242,0x32e404) stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x0000000a,0xffffffff,0x1590f40,0x00002800,0x32e40c,0x32e3fc) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:09 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:09 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:09 GMT")
The file was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
The file 'data' was opened
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x3a74 options=0x00000014)
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x3ae0 options=0x00000014)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (0): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (1252): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (0): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (1252): STUB
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xb0ec options=0x00000014)
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:13 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:13 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"Expires=Sat, 28-May-2011 10:10:13 GMT")
The file 'data' was opened
The file 'data' was opened
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:INET_QueryOption Stub for 66
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 1
fixme:wininet:INET_QueryOption Stub for 66
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=4 host=earlyexperience.partyaccount.com length=32
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:msimtf:DllGetClassObject ({50d5107a-d278-4871-8989-f4ceaaf59cfc} {00000001-0000-0000-c000-000000000046} 0x32cdc4)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {50d5107a-d278-4871-8989-f4ceaaf59cfc} could be created for context 0x401
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_SERVER (10): STUB
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:msxml:xmlcf_QueryInterface interface {342d1ea0-ae25-11d1-89c5-006008c3fbfc} not implemented
fixme:msxml:httprequest_QueryInterface Unsupported interface {bb1a2ae1-a4f9-11cf-8f20-00805f2cd064}
fixme:msxml:httprequest_QueryInterface Unsupported interface {cb5bdc81-93c1-11cf-8f20-00805f2cd064}
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:wininet:NETCON_secure_connect SSL_connect failed: 12055
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:CreateUrlCacheEntryW dwReserved 0x000021b0
fixme:wininet:InternetLockRequestFile STUB
The file 'data' was opened
The file 'data' was opened
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=www1.partypoker.com length=19
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
err:wininet:NETCON_secure_connect SSL_connect failed: 12055
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:wininet:InternetCanonicalizeUrlW Unhandled flags 0x04000000
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=pam.iivt.com length=12
fixme:wininet:InternetSetOptionW INTERNET_OPTION_COOKIES_3RD_PARTY; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_REQUEST_PRIORITY (-1): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CODEPAGE (65001): STUB
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xb074 options=0x00000014)
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0xb0cc options=0x00000014)
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:HTTPREQ_QueryOption Semi-STUB INTERNET_OPTION_SECURITY_FLAGS: 0
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x36b4 options=0x00000014)
fixme:listview:LISTVIEW_PrintClient Partial Stub: (hdc=0x3738 options=0x00000014)
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
wine: Unhandled page fault on read access to 0x0102f710 at address 0x102f710 (thread 0024), starting debugger...
```

---

### Post by jaansson on 2010-05-28
It said in the log something about ole32.dll. So I installed dcom98. Then it wanted to download the files that is supposed to be shown in the client as .html files, instead of showing them straight in it. Is it any way to make them show inside party poker from there?

---

### Post by jaansson on 2010-05-28
msxml3 seemed to have made the trick. Still some blank windows with promotions and stuff, but the options and all that are at least working now. It's blinking quite a lot though, but that's just like everything else in wine I guess.


Edit: A bit too quick there, it doesn't show the names of the tables. I can join the tables, but I don't know which one I get in to. So it's just half way to working.

---

