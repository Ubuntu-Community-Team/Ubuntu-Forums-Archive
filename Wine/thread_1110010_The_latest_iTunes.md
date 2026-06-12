---
title: "The latest iTunes"
date: 2009-03-29
forum: Wine
---

### Post by HNKS on 2009-03-29
Hey guys, im quite new with linux and wine but got quite a few programs to run via wine such as office 2007. Im having trouble getting the installation of iTunes to work however. I find the exe via terminal and wine the exe file but it says its getting ready to install but then the installation window disappears.

This is what terminal says, no idea what it means. 
Desktop$ wine iTunesSetup.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:sfc:SFC_3 0
err:ole:create_server class {000c101c-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0x4
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0xa1c6b8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x000003f7,(nil),0x0006,0x00000000,0x14e6a8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
hnks@HNKS:~/Desktop$ fixme:advapi:DeregisterEventSource (0xcafe4242) stub

Any help would be appreciated. Thanks

---

### Post by cogadh on 2009-03-29
iTunes doesn't really work in wine, you'd be much better off finding a native app to do what you want.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

---

