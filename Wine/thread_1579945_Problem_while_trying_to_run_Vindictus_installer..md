---
title: "Problem while trying to run Vindictus installer."
date: 2010-09-22
forum: Wine
---

### Post by Cymon on 2010-09-22
Hi, I was trying to run the Vindictus install in the terminal but I get this error: 

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil) 

Does anyone know what this is?

---

### Post by AllRadioisDead on 2010-09-22
Vindictus uses hackshield, even if you manage to install it, it won't work. Might as well give up.

---

### Post by HKJGN on 2010-11-11
actually, i got it to install and when i run it in Wine i get this return:

> fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x127e28, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x76e9c8): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x76e958): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x76e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x127fb0,(nil)): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:ras:RasEnumEntriesW ((nil),(null),0x13b740,0x32dab0,0x13b42c),stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:ver:RtlGetProductInfo (5,1,3,0,0x32d618): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32c488,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c488,0x00000000), stub!

If anyone knows what thats saying, let me know.

---

